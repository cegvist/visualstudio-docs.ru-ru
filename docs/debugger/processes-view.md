---
title: "Представление процессов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.externaltools.spyplus.processesview
helpviewer_keywords: Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d2dc97cbe5c6bc178e4b14c89287a3f1c3794dca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="processes-view"></a>Представление процессов
В представлении процессов дерево всех активных процессов в системе. Отображаются имя идентификатора и модуль процесса. В представлении процессов следует используйте, если вы хотите проанализировать конкретному процессу системы, который обычно соответствует исполняемой программой. Процессы идентифицируются по именам модулей или они обозначены «системные процессы».  
  
 Microsoft Windows поддерживает несколько процессов. Каждый процесс может иметь один или несколько потоков и каждый поток может иметь одно или несколько окон верхнего уровня. Каждое окно верхнего уровня может принадлежать ряд windows. A + символ означает, что уровень свернут. Свернутое представление состоит из одной строке для каждого процесса. Щелкните символ, чтобы расширить уровень +.  
  
 В представлении процессов следует используйте, если вы хотите проанализировать конкретному процессу системы, который обычно соответствует исполняемой программой. Процессы идентифицируются по именам модулей или они обозначены «системные процессы». Чтобы найти процесс, Свернуть дерево и поиска в списке.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-open-the-processes-view"></a>Чтобы открыть представление процессов  
  
1.  Из **Spy** меню, выберите **процессов**.  
  
 ![Spy &#43; &#43; Представление процессов](../debugger/media/spy--_processes.png "Spy ++ _Processes")  
Представление процессов в Spy++  
  
 На рисунке выше показано представление процессов с развернутыми узлами потоков и процессов.  
  
### <a name="in-this-section"></a>В этом разделе  
 [Поиск процесса в представлении процессов](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Описание поиска определенного процесса в представлении процессов.  
  
 [Отображение свойств процесса](../debugger/how-to-display-process-properties.md)  
 Описание для отображения дополнительных сведений о сообщении.  
  
### <a name="related-sections"></a>Связанные разделы  
 [Представления Spy++](../debugger/spy-increment-views.md)  
 Описание представления деревьев Spy ++ окон, сообщений, процессов и потоков.  
  
 [Использование Spy++](../debugger/using-spy-increment.md)  
 Представляет средство Spy ++ и объясняется, как использовать.  
  
 [Диалоговое окно "Поиск процесса"](../debugger/process-search-dialog-box.md)  
 Используется для поиска узла заданного процесса в представлении процессов.  
  
 [Диалоговое окно "Свойства процесса"](../debugger/process-properties-dialog-box.md)  
 Отображение свойств процесса, выбранного в представлении процессов.  
  
 [Справочник по Spy++](../debugger/spy-increment-reference.md)  
 Содержит разделы с описанием каждого Spy ++ меню и диалоговых окон поле.