---
title: "Конструктор действия Confirm | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1350bd57b2792140a6e54e7d4252899d2498bb93
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="confirm-activity-designer"></a>Конструктор действия Confirm
**Подтверждение** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Confirm> действия.

## <a name="the-confirm-activity"></a>Действие Confirm
 Действие <xref:System.Activities.Statements.Confirm> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>. Если действие <xref:System.Activities.Statements.Confirm> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Confirm.Target%2A>.

 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.

### <a name="using-the-confirm-activity-designer"></a>Использование конструктора действия Confirm
 **Подтверждение** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **элементов**вкладка на левой стороне [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **Подтверждение** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.Confirm>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно Confirm. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **Подтверждение** конструктора действий или в **DisplayName** поле сетки свойств.

### <a name="the-confirm-properties"></a>Свойства Confirm
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Confirm> и описано их использование в конструкторе. Свойство <xref:System.Activities.Activity.DisplayName%2A> может быть изменено в таблице свойств или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], однако свойство <xref:System.Activities.Statements.Confirm.Target%2A> можно изменить только в таблице свойств.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.CancellationScope>. По умолчанию используется Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)