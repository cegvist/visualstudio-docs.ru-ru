---
title: "IDebugMessageEvent2::GetMessage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2cb6db61048765ec577a0d14ff4079f78e013219
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2018
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Возвращает сообщение для отображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pMessageType`  
 [out] Возвращает значение из [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) перечисление, описывающее тип сообщения.  
  
 `pbstrMessage`  
 [out] Возвращает сообщение.  
  
 `pdwType`  
 [out] Возвращает тип сообщения, используя соглашения о Win32 `MessageBox` функции. В разделе [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) функция подробные сведения.  
  
 `pbstrHelpFileName`  
 [in, out] Возвращает имя файла справки. Может быть значение null (C++) или пустое значение (C#), если отсутствует файл справки.  
  
 `pdwHelpId`  
 [in, out] Возвращает идентификатор справки. Может быть 0, если нет справки, на которое имеется связанное с этим сообщением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)