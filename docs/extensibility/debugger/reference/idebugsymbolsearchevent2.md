---
title: "IDebugSymbolSearchEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a931768dd13f2ced30f329b54c1fe6eb9333eb9c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Этот интерфейс-отправляется подсистема отладки (DE), чтобы указать, отладочные символы для модуля отлаживаемый были загружены.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для отчетов, что были загружены символы для модуля. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE создает и отправляет этот объект события сообщить, что были загружены символы для модуля. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 `IDebugSymbolSearchEvent2` Интерфейс предоставляет следующий метод.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Извлекает сведения о результатах поиска символов.|  
  
## <a name="remarks"></a>Примечания  
 Это событие отправляется, даже если не удалось загрузить символы. Вызов `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` позволяет обработчику это событие, чтобы определить, имеет ли модуль фактически символы.  
  
 Visual Studio обычно использует это событие для обновления состояния загруженные символы в **модули** окна.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)