---
title: "Советы и рекомендации по специальным возможностям для Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4cfc07cb77e1db595d1b381b1097dcfcba0abdab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Советы и рекомендации по специальным возможностям для Visual Studio
> [!TIP]
> Дополнительные сведения о новых специальных возможностях см. в записи блога [Accessibility improvements in Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Улучшения специальных возможностей в Visual Studio 2017 версии 15.3).

Visual Studio имеет встроенные специальные возможности, совместимые со средствами чтения с экрана и другими специальными возможностями. В этом разделе перечислены распространенные сочетания клавиш, позволяющие выполнять задачи с помощью одной клавиатуры, а также приведены сведения об использовании тем с высокой контрастностью для улучшения видимости. В нем также описано, как пользоваться заметками, чтобы получить полезные сведения о коде, и как настроить звуковые подсказки для событий сборки и точек останова.

## <a name="save-your-ide-settings"></a>Сохранение параметров интегрированной среды разработки  
 Вы можете настроить интегрированную среду разработки на своем компьютере, сохранив макет окна, схему назначений клавиш и другие настройки. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Изменение интегрированной среды разработки для просмотра в режиме высокой контрастности
Некоторые люди хуже различают отдельные цвета. Если вы хотите повысить контрастность при написании кода, но не желаете использовать основные темы с высокой контрастностью, мы предлагаем вам новую тему — "Синий (дополнительный контраст)".

  ![Сравните синюю тему и синюю тему с дополнительный контрастностью](media/blue-extra-contrast-theme.png "Определите различия между синей темой и синей темой с дополнительный контрастностью")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Использование заметок для получения ценных сведений о коде

Редактор Visual Studio содержит множество текстовых элементов оформления, позволяющих узнать о характеристиках и возможностях отдельных элементов в строке кода, например лампочек, закладок, волнистых линий, обозначающих ошибки и предупреждения, и т. д. Вы можете использовать набор команд "Показать заметки линий" для поиска этих элементов оформления и перемещения между ними.

  ![Используйте набор команд "Показать заметки линий"](media/show-line-annotations-command-set.png "Показано, как задать набор команд "Показать заметки линий"")

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Доступ к панелям инструментов с помощью сочетаний клавиш
Интегрированная среда разработки Visual Studio включает панели инструментов, как и многие другие окна инструментов. Следующие сочетания клавиш позволяют обращаться к ним.

|Функция|Описание|Сочетание клавиш|  
|-------------|-----------------|---------------------|  
|Панели инструментов IDE|Выбор первой кнопки на панели инструментов "Стандартная".|**ALT**, **CTRL** + **TAB**|  
|Панели инструментов окна инструментов|Перемещение фокуса на панели инструментов в окне инструментов. <br> <br> **ПРИМЕЧАНИЕ**. Это сочетание работает для большинства окон инструментов, но только в том случае, если фокус находится в окне инструментов. Кроме того, необходимо нажать клавишу SHIFT прежде, чем клавишу ALT. В некоторых окнах инструментов, например Team Explorer, клавишу SHIFT необходимо некоторое время удерживать нажатой перед выбором клавиши ALT.|**SHIFT** + **ALT**|
|Панели инструментов|Переход к первому элементу в следующей панели инструментов (когда панель инструментов находится в фокусе)|**CTRL** + **TAB**|

### <a name="other-useful-shortcut-key-combinations"></a>Другие полезные сочетания клавиш  
Далее представлен список некоторых других полезных сочетаний клавиш.

|Функция|Описание|Сочетание клавиш|  
|-------------|-----------------|---------------------|  
|IDE|Включение и выключение режима высокой контрастности <br> <br> **ПРИМЕЧАНИЕ**. Стандартное сочетание клавиш Windows|Левая клавиша **ALT + левая клавиша SHIFT + PRINT SCREEN**|  
|Диалоговое окно|Установка или снятие флажка в диалоговом окне <br> <br> **ПРИМЕЧАНИЕ**. Стандартное сочетание клавиш Windows|**ПРОБЕЛ**|  
|Контекстные меню|Открытие контекстного меню <br> <br> **ПРИМЕЧАНИЕ**. Стандартное сочетание клавиш Windows|**SHIFT** + **F10**|
|Меню|Быстрый доступ к пункту меню с помощью соответствующей клавиши вызова Нажмите клавишу **ALT**, а затем подчеркнутые буквы в меню, чтобы выполнить команду. Например, чтобы открыть диалоговое окно "Открыть проект" в Visual Studio, выберите **ALT** + **F** + **O** + **P**.  <br><br> **ПРИМЕЧАНИЕ**. Стандартное сочетание клавиш Windows|**ALT** + **[буква]**|
|Окно "Панель элементов"|Перемещение между вкладками панели элементов|**CTRL** + **СТРЕЛКА ВВЕРХ**<br /><br /> и<br /><br /> **CTRL** + **СТРЕЛКА ВНИЗ**|  
|Окно "Панель элементов"|Добавление элемента управления из панели элементов в форму или конструктор|**ВВОД**|  
|Страница "Клавиатура", папка "Среда", диалоговое окно "Параметры"|Удаление сочетания клавиш в параметре **Введите сочетание клавиш**|**BACKSPACE**|  

> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.  


## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Задание подсказок для сборок и точек останова с помощью приложения "Звук"
С помощью приложения "Звук" в Windows вы можете назначить звуковой сигнал событиям программы Visual Studio. В частности, вы можете назначить сигнал следующим событиям:

 * Достигнута точка останова
 * Сборка отменена
 * Ошибка сборки
 * Сборка успешно завершена

Ниже описывается порядок действий.

1. В поле **поиска** на компьютере под управлением Windows 10 введите **изменение системных звуков**.

  ![Поле поиска в Windows 10](media/type-here-to-search.png "Введите слово "звуки" в поле поиска на компьютере под управлением Windows 10")

  (Кроме того, если включена Кортана, скажите "Привет, Кортана!" и произнесите "Изменение системных звуков".)

2. Дважды щелкните элемент **Изменение системных звуков**.

  ![Результаты поиска в Windows 10](media/change-system-sounds.png "Дважды щелкните "Изменение системных звуков" в результатах поиска")

3. В диалоговом окне **Звук** выберите вкладку **Звуки**. <br><br>
 Затем в области **Программные события** прокрутите до **Microsoft Visual Studio** и выберите звуки, которые хотите применить к выбранным событиям.

  ![Вкладка "Звуки" приложения "Звук" в Windows 10](media/sound-applet.png "Дважды щелкните "Изменение системных звуков" в результатах поиска")

4. Нажмите кнопку **ОК**.



## <a name="see-also"></a>См. также  
* [Специальные возможности Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
  * [Практическое руководство. Настройка меню и панелей инструментов в Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Специальные возможности корпорации Майкрософт](https://www.microsoft.com/Accessibility)
