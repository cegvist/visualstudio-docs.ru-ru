---
title: "Определения значений локальных переменных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bad0f751f6f772643f38d4f20b2765affd561fb9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="evaluating-locals"></a>Определения значений локальных переменных
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) вызывается, чтобы получить значение local, а также имя локальной переменной и типом. Поскольку значение локального зависит текущее состояние программы, значение локальной переменной необходимо получить из памяти. [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) объект используется для привязки [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объект, представляющий локальной в соответствующее место в памяти, содержащий значение. Это расположение в памяти, представленного [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объекта.  
  
 Эти функциональные возможности получения значение локального инкапсулируются в вспомогательная функция, которая выполняет следующие задачи:  
  
1.  Привязывает `IDebugField` объекта памяти, чтобы получить `IDebugObject` объекта.  
  
2.  Возвращает значение из памяти. Это значение представлено в виде последовательности байтов.  
  
3.  Форматирует значение на основе типа локальной переменной.  
  
4.  Возвращает универсальный объект, содержащий значение локальной переменной. В C# это `object`, и в C++ это `VARIANT`.  
  
## <a name="managed-code"></a>Управляемый код  
 Это представляет собой реализацию функции, которая возвращает значение локального в управляемом коде.  
  
```csharp  
namespace EEMC  
{  
    internal class Field  
    {  
        internal static object GetValue(  
            IDebugBinder binder,  
            IDebugField field,  
            Type t,  
            uint size)  
        {  
            if (t == null || size == 0)  return null;  
  
            IDebugObject debugObject = null;  
            binder.Bind(null, field, out debugObject);  
  
            byte[] buffer = new byte[size];  
            for (int i = 0; i < size; i++)  buffer[i] = 0;  
  
            debugObject.GetValue(buffer, size);   
  
            if (t == typeof(sbyte)) return (sbyte) buffer[0];  
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);  
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);  
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);  
            if (t == typeof(byte))  return buffer[0];  
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);  
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);  
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);  
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);  
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);  
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);  
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);  
            return null;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Неуправляемый код  
 Это представляет собой реализацию функции, которая возвращает значение локального в неуправляемом коде. `FieldGetType`отображается в [начало локальных значений](../../extensibility/debugger/getting-local-values.md).  
  
```cpp  
HRESULT FieldGetPrimitiveValue(  
    in  IDebugBinder* pbinder,  
    in  IDebugField*  pfield,  
    out VARIANT*      pvarValue  
    )  
{  
    if (pvarValue == NULL)  
        return E_INVALIDARG;  
    else  
        *pvarValue = 0;  
  
    if (pfield == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    UINT          valueSize = 0;  
    BYTE*         pvalueBits = NULL;  
    IDebugObject* pobject    = NULL;  
  
    //get the value as bits  
    hr = pbinder->Bind( NULL, pfield, &pobject );  
    if (FAILED(hr))  
        return hr;  
  
    hr = pobject->GetSize( &valueSize );  
    if (FAILED(hr))  
    {  
        pobject->Release();  
        return hr;  
    }  
  
    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));  
    if (!pvalueBits)  
    {  
        pobject->Release();  
        return E_OUTOFMEMORY;  
    }  
  
    hr = pobject->GetValue( pvalueBits, valueSize );  
    pobject->Release();  
    if (FAILED(hr))  
    {  
        free(pvalueBits);  
        return hr;  
    }  
  
    //get the type  
    VARIANT     valueType;  
  
    hr = FieldGetType( pfield, &valueType );  
    if (FAILED(hr))  
    {  
        free(pvalueBits);  
        return hr;  
    }  
  
    //copy a primitive value  
    switch (valueType.vt)  
    {  
    case VT_BSTR:  
        {  
            pvarValue->vt = VT_BSTR;  
            if (valueSize == 0)  
                pvarValue->bstrVal = SysAllocString( OLE("") );  
            else  
                pvarValue->bstrVal =  
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),  
                                           valueSize );  
        }  
  
    case VT_BOOL:  
    case VT_I1:  
    case VT_I2:  
    case VT_I4:  
    case VT_I8:  
    case VT_UI1:  
    case VT_UI2:  
    case VT_UI4:  
    case VT_UI8:  
    case VT_R4:  
    case VT_R8:  
        pvarValue->vt = valueType.vt;  
  
        if (valueSize > 8)  
            valueSize = 8;  
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );  
        break;  
  
    case VT_VOID:  
    case VT_EMPTY:  
        pvarValue->vt = valueType.vt;  
        break;  
  
    default:  
        //not a primitive type  
        VariantClear(&valueType);  
        free(pvalueBits);  
        return E_FAIL;  
    }  
  
    free(pvalueBits);  
    VariantClear(&valueType);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [Получение локальных значений](../../extensibility/debugger/getting-local-values.md)   
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)