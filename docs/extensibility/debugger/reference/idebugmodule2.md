---
title: "IDebugModule2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2
helpviewer_keywords: IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ffa4044e6490f8de8228541787b7bf8ab80285a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule2"></a>IDebugModule2
Этот интерфейс представляет модуль — то есть исполняемый модуль программы, таких как библиотеки DLL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления модуля и обеспечивает доступ к информации об этом модуле.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) возвращает этот интерфейс. Отправляет DE [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) Диспетчер сеанса отладки (SDM), с помощью интерфейса [события](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) метод.  
  
 Этот интерфейс также могут быть возвращены в [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры (которая возвращается вызовом [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Далее](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) также возвращает этот интерфейс ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) возвращает [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) интерфейс).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugModule2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Возвращает [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , описывающий этот модуль.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|УСТАРЕВШИЕ. НЕ СЛЕДУЕТ ИСПОЛЬЗОВАТЬ. Повторно загружает символы для данного модуля.|  
  
## <a name="remarks"></a>Примечания  
 Сведения о модуле может быть отображено в **модули** окна интегрированной среды разработки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)