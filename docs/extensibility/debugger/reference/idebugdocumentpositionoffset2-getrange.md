---
title: "IDebugDocumentPositionOffset2::GetRange | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09b415e01b6c768f471bdf9ad2e595d1a910d582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Получает текущую позицию в документе диапазон.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwBegOffset`  
 [in, out] Смещение для начальную позицию диапазона. Установите этот параметр в значение null, если эта информация не требуется.  
  
 `pdwEndOffset`  
 [in, out] Смещение для конечную позицию диапазона. Установите этот параметр в значение null, если эта информация не требуется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Диапазон, указанный в документе должности точку останова используется подсистема отладки (DE) для поиска вперед для инструкции, которая фактически участвует кода. Рассмотрим следующий пример кода:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Строка 5 вносит без кода для отлаживаемой программы. Отладчик, который задает точку останова в строке 5 DE поиска в прямом направлении отведенного для первой строки, содержащей код, отладчик будет указать диапазон, включающий дополнительный кандидат строки, где может правильно разместить точки останова. DE будет затем осуществлять поиск вперед по те строки, пока его найти строку, которая могла бы принять точки останова.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)