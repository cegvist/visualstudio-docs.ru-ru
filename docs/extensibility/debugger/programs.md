---
title: "Программы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03b4885e653d879e3aaec1d9a68bc9be144cb676
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="programs"></a>Programs
С точки зрения архитектуры отладчик **программы**:  
  
-   Представляет контейнер для группы потоков и набор модулей. Программа имеет не один аналогию в операционной системе Windows.  
  
     Программы — это разновидность подпроцесса. Например при отладке веб-сайта сценария можно рассматривать как программы. Во время запуска сценария в процесс обработки скрипта ядра, независимым от других сценариев, он также имеет свой собственный набор потоков. Отладчик (DE) присоединяет к программе, а не на процесс или поток.  
  
-   Можно определить себя и процесс его выполнение в и может быть присоединен, следует отсоединить от и описать DE, создавший его, если таковые имеются. Программа может выполнять, остановить, продолжить, прерываются.  
  
-   Можно перечислить все потоки. Программа также может предоставить свой собственный поток Дизассемблированный код и можно перечислить все контексты код позиции данного документа.  
  
-   Представленный [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейса, созданные до исполняемой программы или как часть процесса подключения, в зависимости от реализации. При порт перечисляет программы процесса, каждая программа создается в соответствии с соответствующим [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейса, переданного в качестве аргумента для [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Хотя отладчики также создать `IDebugProgram2` интерфейсы для программ, эти представления не создаются в соответствии с узлом программы. `IDebugProgramNode2` Интерфейсы, созданные в Развернутой используются для фактического отладки хотя созданные порт используются только для обнаружения программы, которые выполняются в процессе.  
  
## <a name="see-also"></a>См. также  
 [Процессы](../../extensibility/debugger/processes.md)   
 [Программа узлов](../../extensibility/debugger/program-nodes.md)   
 [Модули](../../extensibility/debugger/modules.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Позиция в документе](../../extensibility/debugger/document-position.md)   
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)