---
title: "IDebugPointerField::GetDereferencedField | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerField::GetDereferencedField
helpviewer_keywords: IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f881a7ad6f11b4c916dad8af184d84a434f3e510
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Этот метод возвращает тип объекта, на который указывает этот указатель объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppField`  
 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) описанием типа целевого объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Например, если [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) объекта указывает на целое число, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) целое число типа описывает тип, возвращаемый этим методом.  
  
## <a name="see-also"></a>См. также  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)