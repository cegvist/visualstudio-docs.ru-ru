---
title: "Как: использование визуализатора дерева WPF | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78806b2ace7872db06ff403bcae28bb6eff21cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Практическое руководство. Использование визуализатора дерева WPF
Визуализатор дерева WPF можно использовать для изучения визуального дерева объекта WPF, а также для просмотра свойств зависимостей WPF для объектов, содержащихся в дереве. Дополнительные сведения о визуальных деревьев см. в разделе [деревьев в WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Дополнительные сведения о свойствах зависимостей см. в разделе [Общие сведения о свойствах зависимостей](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 При открытии визуализатора дерева WPF отобразятся две панели: **визуального дерева** слева и **свойства** *имя***:**  *Тип* на правой панели. Выберите любой объект **визуального дерева** области и **свойства** *имя***:***тип* область автоматически обновляется для отображения свойств этого объекта.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Открытие визуализатора дерева WPF  
  
1.  В подсказке по данным **Контрольные значения** окне **видимые** окна, или **локальные** , рядом с именем объекта WPF щелкните стрелку возле значка лупы.  
  
     Откроется список визуализаторов.  
  
2.  Нажмите кнопку **визуализатора дерева WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Поиск в визуальном дереве  
  
-   В **визуального дерева** области, введите строку для поиска в **поиска** поле.  
  
     Визуализатор дерева WPF немедленно найдет первый объект визуального дерева, соответствующий введенной строке. Для поиска более точных совпадений введите больше символов.  
  
    -   Чтобы перейти к следующему совпадению в визуальном дереве, щелкните **Далее**.  
  
    -   Чтобы вернуться к предыдущему совпадению, нажмите кнопку **Prev**.  
  
    -   Чтобы удалить условия поиска, нажмите кнопку **снимите**.  
  
### <a name="to-search-the-properties-list"></a>Поиск в списке свойств  
  
-   В **свойства** *имя***:***тип* области, введите строку, которую необходимо найти в **фильтрации**поле.  
  
     Визуализатор дерева WPF немедленно найдет свойства, соответствующие введенной строке; после этого появится список тех свойств, которые совпадают с введенной строкой. Для поиска более точных совпадений введите больше символов.  
  
    -   Чтобы удалить условия поиска, нажмите кнопку **снимите**.  
  
### <a name="to-close-the-visualizer"></a>Закрытие визуализатора  
  
-   Нажмите кнопку **закрыть** значок в правом верхнем углу диалогового окна.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательских визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Деревья в WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Общие сведения о свойствах зависимости](/dotnet/framework/wpf/advanced/dependency-properties-overview)