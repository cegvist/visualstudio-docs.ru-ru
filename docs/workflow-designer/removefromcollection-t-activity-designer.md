---
title: "RemoveFromCollection&lt;T&gt; конструктора | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f097e0d826725d3e3aa899c6137164487cfc5685
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection&lt;T&gt; конструктора действий
**RemoveFromCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.RemoveFromCollection%601> действия.

## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection < T\> действия
 Действие <xref:System.Activities.Statements.RemoveFromCollection%601> удаляет указанный элемент из определенной коллекции.

### <a name="using-the-removefromcollectiont-activity-designer"></a>С помощью RemoveFromCollection\<T > конструктора действий
 **RemoveFromCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав **Элементов** на вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **RemoveFromCollection\<T >** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , везде, где обычно размещаются действия, такие как внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.RemoveFromCollection%601> действия по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из RemoveFromCollection < Int32\>. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **RemoveFromCollection < T\>**  конструктора или в **DisplayName** поле сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\> свойства
 В следующей таблице показаны свойства <xref:System.Activities.Statements.RemoveFromCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.RemoveFromCollection%601>. Значение по умолчанию — RemoveFromCollection < Int32\>.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Да|Элемент для добавления **коллекции\<T >**. Этот элемент относится к типу *T*, который относится к типу *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection < TypeArgument\>.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|
|*TypeArgument*|Да|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Значение, которое указывает, удален ли из коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную в таблицу свойств.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)