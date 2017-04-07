---
title: "Шаблон веб-проекта в Инструментах Python для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401e7725-8be5-4e67-862c-bf0690a529e3
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 2375c0c3b1a692d03d8790e400e3fea606355831
ms.lasthandoff: 03/10/2017

---

# <a name="python-web-project-templates"></a>Шаблоны веб-проектов Python

Инструменты Python для Visual Studio (PTVS) включают поддержку разработки веб-проектов на таких платформах, как Bottle, Django и Flask. Сюда входят шаблоны проектов и средство запуска отладки, которые можно настроить для работы с различными платформами. PTVS не содержит платформы, но их можно установить отдельно, щелкнув проект правой кнопкой мыши и выбрав **Python > Install/upgrade framework... (Установить или обновить платформы...)**.

Каждый шаблон (открывается с помощью команд **Файл > Создать > Проект...**) запускает веб-сервер с использованием случайно выбранного локального порта, открывает браузер по умолчанию при отладке и позволяет публиковать проект в [Microsoft Azure](http://www.azure.com) напрямую. Есть шаблоны для Bottle, Flask и Django. Для других платформ, например Pyramid, можно использовать универсальный шаблон веб-проекта.

![Новые шаблоны веб-проектов](media/template-web-new-project.png)

Каждый шаблон (Bottle, Flask и Django) имеет начальный сайт с несколькими страницами и статическими файлами. Этот код позволяет локально выполнить запуск и отладку сервера (некоторые параметры для этого кода необходимо получить из среды) и развернуть проект в Microsoft Azure (где необходимо указать объект [приложения WSGI](http://www.python.org/dev/peps/pep-3333/)).

При создании проекта из шаблона для конкретной платформы появится диалоговое окно для установки необходимых пакетов с помощью pip. Чтобы при публикации веб-сайта были настроены правильные зависимости, для веб-проектов рекомендуется использовать [виртуальную среду](python-environments.md#virtual-environments).

![Диалоговое окно, с помощью которого можно установить необходимые пакеты для шаблона проекта](media/template-web-requirements-txt-wizard.png)

Выполняя развертывание в службе приложений Microsoft Azure, необходимо выбрать версию Python в качестве [расширения сайта](https://aka.ms/PythonOnAppService) и установить пакеты вручную. Кроме того, поскольку при развертывании из Visual Studio служба приложений Azure **не** устанавливает пакеты из файла `requirements.txt` автоматически, используйте сведения о конфигурации, указанные в статье [Upgrading Python on Azure App Service](https://aka.ms/PythonOnAppService) (Обновление Python в службе приложений Azure).

С другой стороны, облачная служба Microsoft Azure поддерживает файл `requirements.txt`. Дополнительные сведения см. в статье [Azure Cloud Service Projects for Python](template-azure-cloud-service.md) (Проекты облачных служб Azure для Python).

Обзор веб-проектов Python представлен в видео [Visual Studio Python Tutorial 6/6: Building a Website](https://youtu.be/FJx5mutt1uk?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Руководство по Python для Visual Studio, часть 6. Создание веб-сайта) длительностью 3 мин 10 с, размещенном на сайте youtube.com.

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk]

## <a name="debugging"></a>Отладка

При запуске веб-проекта для отладки PTVS локально запускает веб-сервер и открывает в браузере по умолчанию страницу с определенным адресом и портом. Чтобы указать дополнительные параметры, щелкните правой кнопкой мыши проект, выберите **Свойства** и **Web Launcher** (Веб-средство запуска):

  ![Свойства веб-средства запуска для универсального веб-шаблона](media/template-web-launcher-properties.png)

Параметры группы **Отладка**:

- Поля **Search Paths** (Пути поиска), **Script Arguments** (Аргументы сценария), **Interpreter Arguments** (Аргументы интерпретатора) и **Interpreter Path** (Путь к интерпретатору) ничем не отличаются от используемых в режиме [обычной отладки](debugging.md).
- **URL-адрес для запуска** — задает URL-адрес, который будет открыт в браузере. По умолчанию для него используется значение `localhost`.
- **Номер порта** — порт, который будет использоваться, если в URL-адресе не указан порт (PTVS по умолчанию автоматически выбирает порт). Это позволяет переопределить значение по умолчанию переменной среды `SERVER_PORT`, используемое шаблонами для настройки порта, прослушиваемого локальным сервером отладки.

Свойства, указанные в группах **команды запуска сервера** и **команды отладки сервера** (последняя группа находится ниже в окне, показанном на рисунке), определяют, как будет запускаться веб-сервер. Так как для многих платформ требуется использовать сценарий вне текущего проекта, можно настроить сценарий здесь и передать модуль автозагрузки как параметр.

- **Команда** — может содержать сценарий Python (файл `*.py`), имя модуля (как и в `python.exe -m module_name`) или одну строку кода (как и в `python.exe -c "code"`). Значение в раскрывающемся списке указывает, какой из этих типов будет использоваться.
- **Аргументы** — содержимое этого поля передается в командной строке после команды.
- **Среда** — разделенный символом новой строки список пар `NAME=VALUE`, определяющих переменные среды. Эти переменные задаются после всех свойств, которые могут изменить среду, например номер порта или пути поиска, и поэтому могут перезаписать эти значения.

Любое свойство проекта и любую переменную среды можно указать, используя синтаксис MSBuild, например `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` — это относительный путь к файлу запуска, а `{StartupModule}` — импортируемое имя файла запуска. `$(SERVER_HOST)` и `$(SERVER_PORT)` являются обычными переменными среды, автоматически задаваемые свойствами **URL-адрес для запуска** и **Номер порта** или с помощью свойства **Среда**.

> [!Note]
> Значения в группе **команды запуска сервера** используются при выборе команды **Отладка > Start Server (Запуск сервера)** или нажатии клавиш CTR+F5. Значения в группе **команды отладки сервера** используются при выборе команды **Отладка > Start Debug Server (Запустить сервер отладки)** или нажатии клавиши F5.


### <a name="sample-bottle-configuration"></a>Пример конфигурации Bottle

Шаблон веб-проекта Bottle содержит стандартный код, который выполняет необходимую конфигурацию. Импортированное приложение Bottle может не содержать этот код, однако в этом случае следующие параметры запускают приложение с помощью установленного модуля `bottle`:

- Группа **команды запуска сервера**:
    - **Команда**: `bottle` (модуль);
    - **Аргументы**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`.

- Группа **команды отладки сервера**:
    - **Команда**: `bottle` (модуль);
    - **Аргументы**: `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`.

При отладке с помощью PTVS не рекомендуется использовать параметр `--reload`.

### <a name="sample-pyramid-configuration"></a>Пример конфигурации приложения Pyramid

В настоящее время для создания приложений Pyramid лучше всего использовать средство командной строки `pcreate`. После создания приложения его можно импортировать с помощью шаблона [From Existing Python Code](python-projects.md#creating-a-project-from-existing-files) (Из существующего кода Python). Затем настройте параметры в свойствах **универсального веб-проекта**. Эти параметры предполагают, что платформа Pyramid установлена в виртуальной среде в `..\env`.

- Группа **отладки**:
    - **Порт сервера**: 6543 (или заданный в INI-файлах).

- Группа **команды запуска сервера**:
    - Команда: `..\env\scripts\pserve-script.py` (сценарий);
    - Аргументы: `Production.ini`

- Группа **команды отладки сервера**:
    - Команда: `..\env\scripts\pserve-script.py` (сценарий);
    - Аргументы: `Development.ini`

> [!Tip]
> Скорее всего, потребуется настроить **рабочий каталог** для вашего проекта, так как приложения Pyramid обычно находятся на один уровень каталога ниже, чем верхний элемент дерева исходного кода.


### <a name="other-configurations"></a>Другие конфигурации

Если у вас есть параметры для другой платформы, которыми вы хотите поделиться, или вы хотите запросить параметры для такой платформы, откройте обращение в [репозитории GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="publishing-to-azure-app-service"></a>Публикация в службу приложений Azure

Существует два основных способа публикации проекта в службу приложений Azure. Во-первых, развертывание из системы управления версиями можно выполнять так же, как и для других языков программирования, как описано в [документации по Azure](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/). Чтобы выполнить публикацию из Visual Studio напрямую, щелкните правой кнопкой мыши проект и выберите **Опубликовать**:

![Команда публикации в контекстном меню проекта](media/template-web-publish-command.png)

После выбора команды мастер поможет создать веб-узел или импортировать параметры публикации, предварительно просмотреть измененные файлы и выполнить публикацию на удаленном сервере.

При создании сайта в службе приложений необходимо установить Python и все пакеты, от которых зависит работа сайта. Вы можете сначала опубликовать сайт, однако он не будет работать, пока Python не будет настроен.

Чтобы установить Python в службе приложений, мы рекомендуем использовать [расширения сайта](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net). Это оптимизированные и перепакованные копии [официальных выпусков](https://www.python.org) Python для службы приложений Azure.

Расширение сайта можно развернуть на [портале Azure](https://portal.azure.com/) с помощью колонки **Средства разработки > Расширения** для службы приложений, где нужно выбрать **Добавить** и прокрутить список, чтобы найти нужные расширения для Python:

![Добавление расширения сайта на портале Azure](media/template-web-site-extensions.png)

При использовании шаблонов развертывания JSON можно указать расширение сайта как его ресурс:

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

Наконец, можно выполнить вход с помощью [консоли разработки](https://github.com/projectkudu/kudu/wiki/Kudu-console) и установить расширения сайта.

В настоящее время для установки пакетов рекомендуется использовать консоль разработки, после того как вы установили расширения сайта и выполнили pip напрямую. Очень важно указать полный путь к Python. Иначе может быть использован ошибочный путь. Как правило, нет необходимости использовать виртуальную среду. Например:

```
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

При развертывании в службе приложений Azure сайт будет работать в фоновом режиме Microsoft IIS. Чтобы сайт работал со службой IIS, необходимо добавить по крайней мере файл `web.config`. Можно использовать шаблоны для некоторых общих целей развертывания, которые можно добавить, щелкнув правой кнопкой мыши проект и выбрав "Добавить > Создать элемент..." (см. диалоговое окно ниже). Их можно легко изменить для других целей. Сведения о доступных параметрах конфигурации см. в [справочнике по настройке IIS](https://www.iis.net/configreference).

![Шаблоны элементов Azure](media/template-web-azure-items.png)

К доступным элементам относятся:

- Файл Azure web.config (FastCGI): добавляет файл `web.config`, когда приложение предоставляет объект [WSGI](https://wsgi.readthedocs.io/en/latest/) для обработки входящих подключений.
- Файл Azure web.config (HttpPlatformHandler): добавляет файл `web.config`, когда приложение прослушивает сокет для входящих подключений.
- Статические файлы Azure web.config: при наличии одного из вышеперечисленных файлов `web.config` добавьте этот шаблон в подкаталог, чтобы исключить его обработку приложением.
- Файл Azure web.config для удаленной отладки: добавляет необходимые файлы для удаленной отладки через WebSockets.
- Файлы для поддержки веб-роли: содержат сценарии развертывания по умолчанию для веб-ролей облачной службы.
- Файлы для поддержки рабочей роли: содержат сценарии запуска и развертывания по умолчанию для рабочих ролей облачной службы.

Если вы добавили шаблон отладки `web.config` в проект и планируете использовать удаленную отладку Python, необходимо будет опубликовать сайт в конфигурации отладки. Этот параметр не входит в текущую активную конфигурацию решения, и для него всегда по умолчанию используется значение "Выпуск". Чтобы его изменить, откройте вкладку **Параметры** и используйте в мастере публикации поле со списком **Конфигурация** (дополнительные сведения о создании и развертывании веб-приложения Azure см. в [документации по Azure](https://azure.microsoft.com/develop/python/)):

![Изменение конфигурации публикации](media/template-web-publish-config.png)

С помощью команды **Преобразовать в проект облачной службы Microsoft Azure** (см. рисунок ниже) можно добавить проект облачной службы в решение. Этот проект включает параметры развертывания и конфигурации для используемых виртуальных машин и служб. Используйте команду **Опубликовать** в облачном проекте, чтобы выполнить развертывание в облачной службе. С помощью команды **Опубликовать** в проекте Python можно по-прежнему выполнить развертывание на веб-сайтах. Дополнительные сведения см. в статье [Проекты облачных служб Azure для Python](template-azure-cloud-service.md).

![Команда "Преобразовать в проект облачной службы Microsoft Azure"](media/template-web-convert-menu.png)
