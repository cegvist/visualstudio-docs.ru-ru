---
title: "Обзор и выбор диалоговое окно типа .NET (устаревшая версия) | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3cdc5d3928cd436d86d529e667f99251e1e7cc95
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Диалоговое окно «Обзор и выбор типа .NET» (для прежних версий)
В этом разделе описывается использование **Обзор и Выбор типа .NET** диалоговое окно в конструкторе рабочих процессов прежних версий Windows. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 В **свойства** окна, при выборе свойств, которые принимают тип платформы .NET Framework в связанной сборке, многоточие **[...]**  появится в конце текстового поля свойства. Щелкнув **[...]**  открывает **Обзор и Выбор типа .NET** диалоговое окно. В этом диалоговом окне из представления в виде дерева сборок, на которые есть ссылки, можно выбрать тип. Например, при использовании конструктора действий в **свойства** окно, нажмите кнопку **базовый класс** многоточие **[...]**  для выбора другого базового класса для действия в дереве ссылки на сборки.

 В следующей таблице описаны элементы пользовательского интерфейса (UI) **Обзор и Выбор типа .NET** диалоговое окно.

|Элемент пользовательского интерфейса|Описание:|
|----------------|-----------------|
|**Имя типа:**|Имя выбранного в данный момент типа.|
|**Type**|Левая панель содержит представление в виде дерева сборок, на которые есть ссылки. Правая панель содержит типы, доступные для выделения из сборки, на которую есть ссылка, выбранной в левой панели.|

## <a name="see-also"></a>См. также

- [Использование конструктора действия для прежних версий](../workflow-designer/using-the-legacy-activity-designer.md)