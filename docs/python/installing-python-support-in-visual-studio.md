---
title: "Установка поддержки Python в Visual Studio | Документация Майкрософт"
description: "Подробные инструкции по установке средств Python для Visual Studio (PTVS) в Visual Studio 2017, 2015, 2013, 2012 и 2010, включая параметры и расположения установки."
ms.custom: 
ms.date: 02/15/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 3cc0b6b99dd76a531ed3e99dcac8ae5d438d7e63
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>Установка поддержки Python в Visual Studio под управлением Windows

Чтобы установить поддержку Python для Visual Studio (Инструменты Python для Visual Studio или PTVS), выполните инструкции из раздела, который соответствует вашей версии Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 и более ранние версии](#visual-studio-2013-and-earlier)

Для Visual Studio 2015 и более ранних версий требуется отдельно [установить любой интерпретатор Python](installing-python-interpreters.md) (требуется Python 3.5 или более ранней версии, так как версия 3.6 не поддерживается, и будет выводиться соответствующее сообщение). На этой же странице приводятся инструкции по добавлению существующего интерпретатора Python в Visual Studio 2017.

Чтобы быстро проверить поддержку Python после установки, откройте интерактивное окно Python. Для этого нажмите клавиши Alt + I и введите `2+2`. Если вы не увидите результат `4`, проверьте выполненные действия.

> [!Tip]
> Рабочая нагрузка Python содержит полезное расширение Cookiecutter, которое предоставляет графический пользовательский интерфейс для поиска шаблонов, ввода параметров шаблонов и создания проектов и файлов. Дополнительные сведения см. в статье [Использование расширения Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Сейчас Python не поддерживается в Visual Studio для Mac, однако доступен в Mac и Linux посредством Visual Studio Code. См. [вопросы и ответы](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Загрузите и запустите последнюю версию установщика Visual Studio 2017. Если вы уже установили Visual Studio, запустите установщик Visual Studio и перейдите к шагу 2.

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Установить Visual Studio 2017 Community</a>

    >[!Tip]
    > Выпуск Community предназначен для индивидуальных разработчиков, использования при аудиторном обучении и в научных исследованиях, а также разработки решений с открытым кодом. В других целях установите <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> или <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>.

1. В установщике предлагается список рабочих нагрузок, то есть групп связанных параметров для определенных целей разработки. Для Python выберите рабочую нагрузку **Разработка на Python**.

    ![Рабочая нагрузка разработки Python в установщике Visual Studio](media/installation-python-workload.png)

    Необязательно: если вы занимаетесь обработкой и анализом данных, также рекомендуется установить рабочую нагрузку **Приложения для обработки и анализа данных и аналитические приложения**. Эта рабочая нагрузка включает в себя поддержку Python, а также языков R и F#. Дополнительные сведения см. в разделе [Рабочая нагрузка "Приложения для обработки и анализа данных и аналитические приложения"](../rtvs/data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Рабочие нагрузки для Python и обработки и анализа данных доступны только в Visual Studio2017 версии 15.2 и выше.

1. В правой области установщика при необходимости выберите дополнительные параметры. Чтобы принять параметры по умолчанию, пропустите этот шаг.

    ![Параметры разработки Python в установщике Visual Studio](media/installation-python-options.png)

    | Параметр | Описание: |
    | --- | --- |
    | Дистрибутивы Python | Выберите любое сочетание 32- и 64-разрядных вариантов дистрибутивов Python 2, Python 3, Anaconda2 и Anaconda3, с которыми вы планируете работать. Каждый дистрибутив включает в себя интерпретатор, среду выполнения и библиотеки. В частности, Anaconda — это открытая платформа обработки и анализа данных, которая включает в себя множество предварительно установленных пакетов. (Вы можете в любой момент вернуться в установщик Visual Studio, чтобы добавить или удалить дистрибутивы.)  **Примечание**. Если вы установили дистрибутив без использования установщика Visual Studio, вам не нужно выполнять дополнительные действия. Visual Studio автоматически определяет существующие установки Python. См. дополнительные сведения о [средах Python](managing-python-environments-in-visual-studio.md). |
    | Поддержка шаблонов Cookiecutter | Устанавливает графический пользовательский интерфейс Cookiecutter для поиска шаблонов, ввода их параметров и создания проектов и файлов. См. раздел [Использование расширения Cookiecutter](using-python-cookiecutter-templates.md). |
    | Поддержка веб-приложений Python | Устанавливает средства для разработки веб-приложений, включая поддержку редактирования кода HTML, CSS и JavaScript, а также шаблоны проектов на основе платформ Bottle, Flask и Django. См. статью [Шаблоны веб-проектов Python](python-web-application-project-templates.md). |
    | Поддержка Интернета вещей для Python | Поддерживает разработку для Windows IoT Core с помощью Python. |
    | Встроенные средства разработки Python | Устанавливает компилятор C++ и другие компоненты, необходимые для разработки собственных расширений для Python. См. статью [Создание расширения C++ для Python](working-with-c-cpp-python-in-visual-studio.md). Чтобы обеспечить полную поддержку С++, установите рабочую нагрузку **Разработка классических приложений на C++**. |
    | Основные инструменты облачных служб Azure | Обеспечивает дополнительную поддержку для разработки облачных служб Azure на Python. См. раздел [Проекты облачных служб Azure](python-azure-cloud-service-project-template.md). |

1. После установки в установщике предлагаются команды для изменения, запуска, восстановления и удаления Visual Studio. Если доступны обновления для установленных компонентов Visual Studio, кнопка **Изменить** меняется на **Обновить**. (Команду "Изменить" в этом случае можно выбрать в раскрывающемся меню.) Запускать среду Visual Studio и установщик можно также из меню "Пуск" в Windows. Для этого выполните поиск по запросу "Visual Studio".

    ![Запуск, изменение или удаление Visual Studio посредством установщика](media/installation-vs-launch.png)

|   |   |
|---|---|
| ![значок кинокамеры для видео](../install/media/video-icon.png "Просмотреть видео") | [Просмотрите видео (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567) о поддержке установки Python в Visual Studio.|

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Чтобы запустить установщик Visual Studio, откройте **Панель управления > Программы и компоненты**, затем выберите **Microsoft Visual Studio 2015** и нажмите кнопку **Изменить**.

1. В самом установщике выберите действие **Изменить**.

1. Выберите **Языки программирования > Инструменты Python для Visual Studio** и нажмите **Далее**:

    ![Выбор PTVS в установщике Visual Studio 2015](media/installation-vs2015.png)

1. Когда завершится работа установщика Visual Studio, [установите любой интерпретатор Python на свой выбор](installing-python-interpreters.md). Если интерпретатор уже установлен, но Visual Studio не обнаруживает его автоматически, см. руководство по [определению существующего окружения вручную](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 и более ранние версии

1. Установите версию Инструментов Python для Visual Studio, соответствующую вашей версии Visual Studio.

    - Visual Studio 2013: [PTVS 2.2 для Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). В Visual Studio 2013 этот процесс можно запустить через диалоговое окно **Файл > Новый проект** в Visual Studio.
    - Visual Studio 2012: [PTVS 2.1 для Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 для Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Selecting and installing Python interpreters](installing-python-interpreters.md) (Установка и настройка интерпретаторов Python). Если интерпретатор уже установлен, но Visual Studio не обнаруживает его автоматически, см. руководство по [определению существующего окружения вручную](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).

## <a name="install-locations"></a>Расположения установки

По умолчанию поддержка Python устанавливается для всех пользователей на компьютере.

В Visual Studio 2017 рабочая нагрузка Python устанавливается в каталог `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`, где &lt;VS_edition&gt; может иметь значение Community, Professional или Enterprise.

В Visual Studio 2015 и более ранних версиях используются такие пути установки:

- 32-разрядная версия.
  - Путь: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Расположение пути в реестре: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64-разрядная версия.
  - Путь: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Расположение пути в реестре: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

Здесь:

- &lt;VS_ver&gt; принимает одно из этих значений:
  - 14.0 for Visual Studio 2015
  - 12.0 for Visual Studio 2013
  - 11.0 for Visual Studio 2012
  - 10.0 for Visual Studio 2010
- &lt;PTVS_ver&gt; — это номер версии, например 2.2, 2.1, 2.0, 1.1, 1.5 или 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Пользовательские установки (для версии 1.5 и более ранних)

Средства Python для Visual Studio 1.5 и более ранних версий можно установить только для текущего пользователя. Путь установки будет выглядеть так: `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>` Здесь &lt;VS_ver&gt; и &lt;PTVS_ver&gt; имеют то же значение, которое описано выше.

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
