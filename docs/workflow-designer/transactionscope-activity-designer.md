---
title: "Конструктор действия TransactionScope | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e2b2e5400aa231f51c75ff1bfd364ae34d9c1a7a
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="transactionscope-activity-designer"></a>Конструктор действия TransactionScope
**TransactionScope** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.TransactionScope> действия.

## <a name="the-transactionscope-activity"></a>Действие TransactionScope
 Действие <xref:System.Activities.Statements.TransactionScope> выполняет вложенное действие за одну транзакцию. Транзакция фиксируется, после того как действие <xref:System.Activities.Statements.TransactionScope.Body%2A> и все другие участники транзакции успешно завершаются.

### <a name="using-the-transactionscope-activity-designer"></a>Использование конструктора операций TransactionScope
 **TransactionScope** конструктора действий можно найти в **транзакции** категории **элементов**, который нажав **элементов**  вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **TransactionScope** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.TransactionScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TransactionScope. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **TransactionScope** конструктора или в **DisplayName** поле сетки свойств.

### <a name="the-transactionscope-properties"></a>Свойства TransactionScope
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TransactionScope> и описано их использование в конструкторе. Свойства <xref:System.Activities.Activity.DisplayName%2A> и <xref:System.Activities.Statements.TransactionScope.Body%2A> можно изменить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Но другие свойства следует изменять в таблице свойств.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.TransactionScope>. По умолчанию выбрано значение TransactionScope. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Указывает действие, которое следует выполнить за одну транзакцию. Чтобы добавить <xref:System.Activities.Statements.TransactionScope.Body%2A> действие, перетащите действие из **элементов** в **текст** поле на **TransactionScope** конструктора действий с текстом подсказки «перетащить действие Сюда».|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Да|Задает <xref:System.Transactions.IsolationLevel> для объекта <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Задает интервал времени (в формате 00:00:00, что означает часы:минуты:секунды), в течение которого транзакция должна завершиться. Значение по умолчанию - 1 минута (00:01:00).|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Да|Задает значение, которое указывает, следует ли прерывать рабочий процесс, если прервана транзакция.|

## <a name="see-also"></a>См. также

- [Транзакция](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Подтверждение](../workflow-designer/confirm-activity-designer.md)