---
title: "Как: использовать Навигатор | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a7392ca650ca171b6f9d9090333c0837eb0f627a
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-use-breadcrumb-navigation"></a>Как использовать навигатор

Существует три основных способа изменить набор действий, которые отображаются в конструкторе рабочих процессов Windows:

1.  Щелкните дважды, чтобы перейти к дочернему действию.

2.  Щелкните строку навигатора, чтобы перейти к родительским действиям.

3.  Разверните или сверните действия.

### <a name="using-breadcrumb-navigation"></a>Использование строки навигатора

1.  Дважды щелкните действие [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], чтобы изменить корневую деятельность на ту, которую вы щелкнули. Действие, которое пользователь щелкнул, полностью развертывается от корня, при этом в строке навигатора показываются его предки. Это часто называется переходом вглубь или из действия.

2.  Чтобы перейти к предку текущей коневой деятельности, щелкните действие в строке навигатора.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>Развертывание и свертывание текущего действия

1.  Щелчок шевронов рядом с действием позволит развернуть или свернуть текущее действие.

2.  Когда состояние развернутости изменяется при помощи этой кнопки, новое состояние развернутости сохраняется в XAML.

    > [!WARNING]
    > Не все действия можно сразу развернуть. Существует два вида действия, которые нельзя развернуть на месте: либо предок действия не позволяет развернуть свои дочерние объекты (например, действия в блок-схеме нельзя там же развернуть), либо конструктор операций не допускает развертывания. Хотя ни одно из действий, включенных в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], не работает вышеописанным образом, некоторые настроенные действия могут так себя вести.

### <a name="expanding-all-or-collapsing-all-activities"></a>Развертывание и свертывание всех действий

1.  Используйте **развернуть все** и **Свернуть все** кнопки в пользовательском интерфейсе для развертывания и свертывания действий в текущем корне. Обратите внимание, что «развернуть все» и «свернуть все» - это глобальные состояния. Это означает, что при смене корневого действия при помощи строки навигации, все или свернуть все сохраняется до нажатия кнопки **восстановить**.

2.  После применения всех развернуть или свернуть все, вы можете щелкнуть **восстановить** кнопки, которая появляется, чтобы вернуться к состоянию, которое предшествовало каждому действию.

    > [!WARNING]
    > Если такое действие, например <xref:System.Activities.Statements.Flowchart>, выпадает из режима расширения, то функции, связанные с **развернуть все** и **Свернуть все** кнопки отключена на **блок-схемы**  конструктора. Дополнительные сведения о **блок-схема** конструктора, см. в разделе [блок-схема](../workflow-designer/flowchart-activity-designer.md) раздела.

    > [!WARNING]
    > Развернуть все также обладает особым эффектом **коммутатор** и **TryCatch** конструкторов действий. При нажатии кнопки **развернуть все**, отображаются все варианты коммутатора и все блоки try/catch/finally. Щелкнув **восстановить** или **Свернуть все** возвращает конструкторы в их состояние по умолчанию, в котором можно щелкнуть отдельный вариант/блок, чтобы просмотреть ее содержимое.