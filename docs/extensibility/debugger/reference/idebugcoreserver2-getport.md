---
title: "IDebugCoreServer2::GetPort | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetPort
helpviewer_keywords: IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a51eefc5defb02f1affbbad8822296150186e060
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Извлекает определенный порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidPort`  
 [in] Идентификатор GUID порта должно быть извлечено.  
  
 `ppPort`  
 [out] Возвращает [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) объект, представляющий нужный порт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_PORTSUPPLIER_NO_PORT` , если нет порта с указанным идентификатором.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)