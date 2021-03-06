---
title: "DEBUG_REFERENCE_INFO | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_REFERENCE_INFO
helpviewer_keywords: DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5fc8f3517d1a1c0f3ea2d8d5f9f19098fe9c7e49
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
Описывает ссылку.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```csharp  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## <a name="members"></a>Участники  
 dwFields  
 Сочетание флагов из [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) перечисления, которое указывает, какие поля заполнены.  
  
 bstrName  
 Имя пользовательской [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объекта.  
  
 bstrType  
 Ссылочный тип, как отформатированную строку.  
  
 bstrValue  
 Значение ссылки как отформатированную строку  
  
 dwAttrib  
 Сочетание флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисления, которое задает флаги для атрибутов свойства отладки.  
  
 dwRefType  
 Значение из [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) перечисления, которое указывает, является ли тип ссылки строгие или слабые.  
  
 m_pReference  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , указывающий справочные сведения.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается в вызов [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) метод, чтобы быть заполнено. Эта структура также возвращается как часть списка из [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) интерфейс, который в свою очередь, возвращается из вызова [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)