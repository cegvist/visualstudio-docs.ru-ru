---
title: "Как: использовать поиск в конструкторе рабочих процессов | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0ab8fe2ca639dd4660dfbabc8c5497f4ab0b3487
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Как использовать поиск в конструкторе рабочих процессов
Чтобы упростить создание более сложных рабочих процессов большего размера, в конструкторе рабочих процессов можно использовать функцию поиска для поиска элементов по ключевым словам. Обратите внимание, что конструктор не поддерживает замену. Поиск может найти следующее в конструкторе:  
  
## <a name="quick-find"></a>Быстрый поиск  
 Быстрый поиск может найти следующее в конструкторе:  
  
-   Свойства объектов <xref:System.Activities.Activity>, объектов <xref:System.Activities.Statements.FlowNode>, объектов <xref:System.Activities.Statements.State>, объектов, переходов и других пользовательских элементов управления потоками.  
  
-   Переменные  
  
-   Аргументы  
  
-   Выражения  
  
#### <a name="using-quick-find"></a>Использование быстрого поиска  
  
1.  Откройте конструктор рабочих процессов, нажмите клавишу **Ctrl + F**, или выберите **изменить**, **поиск и замена**, **быстрый поиск**.  
  
2.  Введите условие поиска в **найти** текстовое поле и нажмите кнопку **Найти далее**.  
  
3.  Условие поиска будет расположено в текущем рабочем процессе. На следующем снимке экрана показано отображаемое имя действия, расположенное в конструкторе.  
  
     ![Результаты поиска в конструкторе рабочих процессов](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>Поиск в файлах  
 Поиск в файлах может находить строки в файлах рабочего процесса, включая файлы XAML.  
  
#### <a name="using-find-in-files"></a>Использование поиска в файлах  
  
1.  В Visual Studio нажмите клавишу **Ctrl + Shift + F**, или выберите **изменить**, **поиск и замена**, **поиск в файлах**  
  
2.  Введите условие поиска в **найти** текстовое поле и нажмите кнопку **найти все**  
  
3.  Результат поиска будет отображаться в [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] **результат поиска** представления. Если дважды щелкнуть элемент в результатах, произойдет переход к действию, содержащему искомый элемент в конструкторе рабочих процессов.