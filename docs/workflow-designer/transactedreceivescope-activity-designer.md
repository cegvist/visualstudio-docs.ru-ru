---
title: "Конструктор действия TransactedReceiveScope | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 76dfb7002c200f0dc920c4c3aae20b1d97faa6e2
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="transactedreceivescope-activity-designer"></a>Конструктор действия TransactedReceiveScope
**TransactedReceiveScope** конструктор используется для создания и настройки <xref:System.ServiceModel.Activities.TransactedReceiveScope> действия.

## <a name="the-transactedreceivescope-activity"></a>Действие TransactedReceiveScope
 Действие <xref:System.ServiceModel.Activities.TransactedReceiveScope> позволяет передать транзакцию в состав транзакций сервера, созданных рабочим процессом или диспетчером.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Использование конструктора операций TransactedReceiveScope
 **TransactedReceiveScope** конструктора действий можно найти в **обмен сообщениями** категории **элементов**, который нажав **элементов**  на вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **TransactedReceiveScope** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , где обычно размещаются действия. При этом создается <xref:System.ServiceModel.Activities.TransactedReceiveScope> действия по умолчанию **DisplayName** для TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **TransactedReceiveScope** конструктора или в **DisplayName** поле сетки свойств.

 **TransactedReceiveScope** конструктор содержит **запроса** и **текст** поля. Они используются для настройки свойства <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, задающего действие <xref:System.ServiceModel.Activities.Receive> и свойство <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, которое задает другое действие <xref:System.Activities.Activity>. Свойство <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> создает транзакцию. Затем транзакция определяется как внешняя для области <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, так что любое действие в области выполняется внутри данной транзакции.

### <a name="the-transactedreceivescope-properties"></a>Свойства TransactedReceiveScope
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.TransactedReceiveScope> и описано их использование в конструкторе. Данное свойство <xref:System.Activities.Activity.DisplayName%2A> может быть изменено в таблице свойств или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], однако другие свойства можно изменить только в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Значение по умолчанию - TransactedReceiveScope.<br /><br /> Для имени <xref:System.Activities.Activity.DisplayName%2A> нет жестких требований, однако лучше всего использовать отображаемое имя.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Да|Удаляет <xref:System.ServiceModel.Activities.Receive> действия в **запроса** блок в области конструктора операций.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Удаляет <xref:System.Activities.Activity> в **текст** блок в области конструктора операций.|

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)