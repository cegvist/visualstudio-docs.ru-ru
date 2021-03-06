---
title: "Компоненты отладчика | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1137c8c5c6041b41e8cbdc0e13d43b6188bd1b1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-components"></a>Компоненты отладчика
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладчик реализуется как VSPackage и управление сеансом отладки целиком. Сеанс отладки состоит из следующих элементов:  
  
-   **Отладочный пакет:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчик предоставляет один и тот же пользовательский интерфейс независимо от того, что выполняется отладка.  
  
-   **Диспетчер сеансов отладки (SDM):** предоставляет согласованный программный интерфейс для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчика для управления разнообразные отладчики. Она реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Диспетчер процессов отладки (PDM):** управляет для всех выполняющихся экземплярах [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], список всех программ, которые могут быть либо выполняется отладка. Она реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Отладка ядра (DE):** отвечает за мониторинг отлаживаемой программы взаимодействует состояние выполняемой программы SDM и PDM и взаимодействия с вычислитель выражений и поставщика символов для предоставления анализа в режиме реального времени состояние памяти и переменные программы. Она реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (для языков, он поддерживает) и сторонних поставщиков, которые требуется поддерживать собственные время выполнения.  
  
-   **Вычислитель выражений (Эстония):** обеспечивает поддержку динамической оценки переменных и выражений, предоставляемых пользователем при остановке программы в определенной точке. Она реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (для языков, он поддерживает) и сторонних поставщиков, которые требуется поддерживать собственные языки.  
  
-   **Символ поставщика услуг:** также называется обработчик символов, сопоставляет символы отладки программы к запущенному экземпляру программы, чтобы полезные сведения, которые могут быть предоставлены (например, уровне исходного кода отладки и оценки выражений). Она реализуется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (для общеязыковой среды выполнения [среда CLR] символы и базы данных программы [PDB-ФАЙЛ] symbol формат файла), а по сторонних поставщиков, имеющих собственные собственный метод хранения отладочной информации.  
  
 Следующей схеме показана связь между этими элементами отладчика Visual Studio.  
  
 ![Общие сведения о компонентах отладки](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пакет отладки](../../extensibility/debugger/debug-package.md)  
 Обсуждение отладки пакета, который выполняется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] оболочки и обрабатывает все пользовательского интерфейса.  
  
 [Диспетчер отладки процессов](../../extensibility/debugger/process-debug-manager.md)  
 Обзор возможностей PDM, являющийся диспетчер процессов, которые можно отлаживать.  
  
 [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)  
 Определяет SDM, который обеспечивает единое представление сеанса отладки для интегрированной среды разработки. SDM управляет DE.  
  
 [Модуль отладки](../../extensibility/debugger/debug-engine.md)  
 Документирует отладки службы, предоставляемые DE.  
  
 [Рабочие режимы](../../extensibility/debugger/operational-modes.md)  
 Общие сведения о трех режимов, в которых могут работать интегрированной среды разработки: режим конструктора, режим выполнения и режим приостановки выполнения. Также рассматриваются механизмы переходов.  
  
 [Вычислитель выражений](../../extensibility/debugger/expression-evaluator.md)  
 Описание назначения EE во время выполнения.  
  
 [Поставщик символов](../../extensibility/debugger/symbol-provider.md)  
 Описывает, как, в реализации поставщика символ вычисляет переменных и выражений.  
  
 [Визуализатор типов и пользовательское средство просмотра](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Описывает тип визуализатора и пользовательское средство просмотра, и какая роль средство оценки выражений в поддержка.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные принципы отладки архитектуры.  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как DE одновременно работает в пределах кода, документацию и контекстов выражения вычисления. Описание для каждого из трех контекстов, расположения, положение или оценки, относящиеся к нему.  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, например, запустив программу и оценки выражений.  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)