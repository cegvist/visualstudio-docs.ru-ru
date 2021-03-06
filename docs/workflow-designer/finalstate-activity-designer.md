---
title: "Конструктор FinalState Activity | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5b9b8cc1fc0bdb390e1bf32a6a8f262b435a157
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="finalstate-activity-designer"></a>Конструктор FinalState Activity
Конструктор <xref:System.Activities.Core.Presentation.FinalState> используется для создания <xref:System.Activities.Statements.State>, которое завершает экземпляр конечного автомата.

## <a name="using-the-finalstate-activity-designer"></a>Использование конструктора действий FinalState
 **FinalState** конструктор используется для создания <xref:System.Activities.Statements.State> , предварительно настраиваемого как завершающее состояние конечного автомата. Объект <xref:System.Activities.Statements.State> , созданного при помощи <xref:System.Activities.Core.Presentation.FinalState> конструктора действий его <xref:System.Activities.Statements.State.IsFinal%2A> свойство **true**, не имеет <xref:System.Activities.Statements.State.Exit%2A> действия и не имеет переходов, исходящие из него. Для использования <xref:System.Activities.Core.Presentation.FinalState> конструктора действий, чтобы добавить <xref:System.Activities.Statements.State> действия, предварительно настроенного как завершающее состояние конечного автомата, перетащите **FinalState** конструктора действий из **конечного автомата**раздел **элементов** и перетащите его в конструкторе рабочих процессов. Конструктор действий <xref:System.Activities.Core.Presentation.FinalState> можно перетащить в <xref:System.Activities.Statements.StateMachine> и переходы, добавленные позже. Переход также можно создать при помещении конструктора действий <xref:System.Activities.Core.Presentation.FinalState> на поверхность. Дополнительные сведения о создании переходы см. в разделе [перехода](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Свойства действия состояния в конструкторе рабочих процессов
 В следующей таблице приведены свойства, которые можно задать с помощью конструктора <xref:System.Activities.Core.Presentation.FinalState>, и описано их использование в конструкторе. Некоторые из этих свойств можно изменить в таблице свойств, а некоторые из них ― в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.State> в заголовке. Значение по умолчанию — **состояние**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Statements.State.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Statements.State.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Указывает действие, которое выполняется при переходе в это состояние. Это значение может быть задано путем перетаскивания действия из **элементов** и помещения его в <xref:System.Activities.Statements.State.Entry%2A> состояния.|

## <a name="see-also"></a>См. также

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Состояние](../workflow-designer/state-activity-designer.md)
- [Переход](../workflow-designer/transition-activity-designer.md)