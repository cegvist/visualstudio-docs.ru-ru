---
title: "Использование списка задач | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 282d9a70470686af71120887ee18bb2b6a899f78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-task-list"></a>Использование списка задач

**Список задач** позволяет отслеживать комментарии к коду, в которых используются токены, такие как `TODO` и `HACK`, или настраиваемые токены, а также управлять ярлыками, с помощью которых можно перейти непосредственно к предварительно заданному месту в коде. Щелкните элемент в списке, чтобы перейти к его расположению в исходном коде.

## <a name="the-task-list-window"></a>Окно "Список задач"

При открытии окно **Список задач** отображается в нижней части окна приложения.

### <a name="to-open-the-task-list"></a>Отображение списка задач

- В меню **Вид** выберите команду **Список задач** (сочетание клавиш: CTRL+\\, T).

    ![Окно "Список задач"](../ide/media/vs2015_task_list.png "vs2015_task_list")

### <a name="to-change-the-sort-order-of-the-list"></a>Изменение порядка сортировки элементов в списке

- Щелкните заголовок любого столбца. Чтобы дополнительно уточнить результаты поиска, нажмите клавишу SHIFT и щелкните заголовок второго столбца.

     Вместо этого также можно выбрать пункт **Порядок сортировки**в меню ярлыков, а затем выбрать заголовок. Чтобы дополнительно уточнить результаты поиска, нажмите клавишу SHIFT и выберите второй заголовок.

### <a name="to-show-or-hide-columns"></a>Отображение или скрытие столбцов

- В контекстном меню выберите пункт **Показать столбцы**. Выберите столбцы, которые требуется отобразить или скрыть.

### <a name="to-change-the-order-of-the-columns"></a>Изменение порядка столбцов

- Перетащите заголовок любого столбца в нужное место.

## <a name="user-tasks"></a>Задачи пользователя

Функция задач пользователя была удалена, начиная с Visual Studio 2015. При открытии решения, которое содержит данные задачи пользователя из Visual Studio 2013 и более ранней версии, данные задач пользователя в файле SUO не будут затронуты, но задачи пользователя не будут отображаться в списке задач.

Если необходимо иметь доступ к данным задач пользователя и изменять их, следует открыть проект в Visual Studio 2013 и скопировать содержимое всех задач пользователя в предпочтительное средство управления проектами (например Team Foundation Server).

## <a name="tokens-and-comments"></a>Токены и комментарии

В окне **Список задач** также отображаются комментарии, представленные в коде, с предшествующим маркером комментария и предопределенным токеном. Например, следующий комментарий C# состоит из трех частей:

- Маркер комментария (`//`)

- Токен, например (`TODO`)

- Сам комментарий (оставшийся текст)

```csharp
// TODO: Load state from previously suspended application
```

Так как `TODO` — это стандартный токен, этот комментарий будет выглядеть как задача `TODO` в списке.

###  <a name="customTokens"></a> Пользовательские маркеры

По умолчанию Visual Studio включает следующие токены: HACK, TODO, UNDONE, NOTE. В этих токенах регистр не учитывается.

Можно также создавать пользовательские токены.

#### <a name="to-create-a-custom-token"></a>Создание пользовательского токена

1. В меню **Сервис** выберите пункт **Параметры**.

2. Откройте папку **Среда** и выберите **Список задач**.

     Отображается страница [Параметры списка задач](../ide/reference/task-list-environment-options-dialog-box.md).

     ![Список задач Visual Studio](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")

3. В категории **Токены** в текстовом поле **Имя** введите имя токена, например "BUG".

4. В раскрывающемся списке **Приоритет** выберите приоритет по умолчанию для нового токена. Нажмите кнопку **Добавить** .

###  <a name="cppComments"></a> Комментарии TODO C++

По умолчанию комментарии TODO C++ отображаются в окне **Список задач** . Это поведение можно изменить.

#### <a name="to-turn-off-c-todo-comments"></a>Отключение комментариев TODO C++

В меню **Сервис** выберите пункты **Параметры** > **Текстовый редактор** > **C/C++** > **Вид** > **Перечислить задачи комментариев** и установите значение "false".

## <a name="shortcuts"></a>Ярлыки

Объект *ярлык* — это закладка в коде, которая отслеживается в **списке задач**; он имеет свой значок, отличный от обычной закладки. Дважды щелкните ярлык в **Списке задач** , чтобы перейти к соответствующему месту в коде.

![Значок ярлыка списка задач Visual Studio](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")

### <a name="to-create-a-shortcut"></a>Создание ярлыка

Чтобы создать ярлык, вставьте указатель в код, где необходимо разместить ярлык. Выберите **Изменить** > **Закладки** > **Добавить ярлык списка задач** или нажмите клавиши **CTRL** + **K**, **CTRL** + **H**.

Для навигации по ярлыкам в коде можно выбрать ярлык в списке, а затем пункт **Следующая задача** или **Предыдущая задача** в контекстном меню.

## <a name="see-also"></a>См. также

[Страница "Список задач", папка "Среда", диалоговое окно "Параметры"](../ide/reference/task-list-environment-options-dialog-box.md)