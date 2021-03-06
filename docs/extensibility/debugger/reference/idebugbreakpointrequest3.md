---
title: "IDebugBreakpointRequest3 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointRequest3
helpviewer_keywords: IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: acccf830983239f81ba5c896c848ec13007c5d6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Этот интерфейс представляет сведения, необходимые для создания и привязки точки останова любого типа. Он является расширением [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Диспетчер сеансов отладки (SDM) обычно реализует этот интерфейс.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Модуль отладки (DE) обращается к этот интерфейс путем вызова [QueryInterface](/cpp/atl/queryinterface) в интерфейсе IDebugBreakpointRequest2 принимаются в вызове к [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` интерфейс предоставляет следующий метод.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Возвращает сведения о точках останова запроса, описывающее этот запрос точки останова.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс используется для предоставления дополнительных сведений для DE через [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры. Эта дополнительная информация включает идентификатор поставщика DE (в виде идентификатора GUID), имя точки трассировки и имя ограничения точки останова.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)