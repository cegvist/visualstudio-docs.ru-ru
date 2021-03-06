---
title: "Советы и рекомендации по улучшению работы Visual Studio | Документы Майкрософт"
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3a48166490cb48870e9e6341b0cba6dfc9f668fc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Советы и рекомендации по улучшению работы Visual Studio

Рекомендации по повышению производительности Visual Studio предназначены для редких ситуаций, когда может возникать нехватка памяти. В таких случаях можно оптимизировать определенные компоненты Visual Studio, которые могут не использоваться. Приведенные ниже советы не следует рассматривать как общие рекомендации.

> [!NOTE]
> Если при работе с продуктом у вас возникают затруднения из-за проблем с памятью, свяжитесь с нами через средство обратной связи.

## <a name="optimize-your-environment"></a>Оптимизация окружения

- **Использование 64-разрядной ОС**

    При переходе с 32-разрядной на 64-разрядную версию Windows вы увеличиваете объем виртуальной памяти, доступной Visual Studio, с 2 до 4 ГБ. Это позволяет Visual Studio обрабатывать значительно большие рабочие нагрузки, даже если это 32-разрядный процесс.

    Дополнительные сведения см. в разделах [Ограничения памяти](https://msdn.microsoft.com/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits) и [Использование /LARGEADDRESSAWARE в 64-разрядной версии Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="configure-solution-and-projects"></a>Настройка решения и проектов

При наличии очень большого решения с множеством проектов можно попытаться осуществить следующие оптимизации:

- **Выгрузка проектов**

    Вы можете вручную выгрузить отдельные редко используемые проекты в обозревателе решений с помощью контекстного меню.

- **Рефакторинг решения**

    Решение можно разделить на несколько файлов меньшего размера с часто используемыми проектами. Такой рефакторинг должен существенно сократить использование памяти для рабочего процесса. Кроме того, более мелкие решения загружаются быстрее.

## <a name="configure-debugging-options"></a>Настройка параметров отладки

Если вы часто сталкиваетесь с нехваткой памяти во время сеансов отладки, можно оптимизировать производительность, внеся одно или несколько изменений в конфигурацию.

- **Включение функции "Только мой код"**

    Простейшая оптимизация заключается в том, чтобы включить функцию **Только мой код**, которая загружает только символы для проекта. Включение этой функции может привести к значительной экономии памяти при отладке управляемых приложений (.NET). Для некоторых типов проектов этот параметр уже включен по умолчанию.

    Чтобы включить функцию **Только мой код**, выберите **Сервис > Параметры > Отладка > Общие** и затем **Включить только мой код**.

- **Указание символов для загрузки**

    При отладке машинного кода для загрузки файлов символов (PDB) требуется большой объем памяти. Вы можете настроить параметры отладочных символов для экономии памяти. Как правило, решение настраивается для загрузки только модулей из проекта.

    Чтобы указать загрузку символов, выберите **Сервис > Параметры > Отладка > Символы**.

    Задайте параметр **Только указанные модули** вместо **Все модули** и затем укажите, какие модули нужно загружать. Во время отладки также можно щелкнуть определенные модули правой кнопкой мыши в окне **Модули**, чтобы явно включить модуль в загрузку символов. (Чтобы открыть окно во время отладки, выберите **Отладка > Окна > Модули**.)

    Дополнительные сведения см. в разделе [Общие сведения о файлах символов](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Отключение средств диагностики**

    Рекомендуется отключить профилирование ЦП после использования. Эта функция может потреблять очень много ресурсов. После включения профилирования ЦП это состояние распространяется и на все последующие сеансы отладки, поэтому его следует отключать явным образом. Вы можете сэкономить ресурсы, отключив средства диагностики при отладке, если некоторые предоставляемые функции вам не нужны.

    Чтобы отключить средства диагностики, запустите сеанс отладки, выберите **Сервис > Параметры > Включить средства диагностики**  и отмените выбор соответствующего параметра.

    Дополнительные сведения см. в статье [Средства профилирования](../profiling/profiling-tools.md).

## <a name="disable-tools-and-extensions"></a>Отключение инструментов и расширений

Для повышения производительности можно отключить некоторые инструменты или расширения.

> [!TIP]
> Часто проблемы производительности можно выявить, отключая расширения по одному и проверяя уровень производительности.

### <a name="managed-language-services-roslyn"></a>Управляемые службы языка (Roslyn)

Сведения о производительности .NET Compiler Platform ("Roslyn") см. в статье [Особенности производительности для крупных решений] (https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Отключение полного анализа решения**

    Visual Studio проводит анализ всего решения, чтобы предоставить более полную информацию об ошибках перед началом сборки. Эта функция полезна для максимально быстрого выявления ошибок. Однако для очень крупных решений она может потреблять значительный объем ресурсов. При возникновении нехватки памяти или аналогичных проблем можно отключить эту функцию, чтобы освободить ресурсы. По умолчанию этот параметр включен для Visual Basic и отключен для C#.

    Чтобы отключить **Полный анализ решения**, выберите **Сервис > Параметры > Текстовый редактор > Visual Basic или C#**. Выберите **Дополнительно** и отмените выбор параметра **Включить полный анализ решения**.

- **Отключение CodeLens**

    Visual Studio выполняет задачу **Найти все ссылки** для каждого метода при его отображении. CodeLens предоставляет такие функции, как встроенное отображение числа ссылок. Эта работа выполняется в отдельном процессе (например, ServiceHub.RoslynCodeAnalysisService32). В очень крупных решениях или системах с небольшим объемом ресурсов эта функция может оказывать значительное негативное влияние на производительность, хотя она и выполняется с низким приоритетом. В случае возникновения высокой загрузки ЦП при выполнении этого процесса или проблем с памятью (например, при загрузке большого решения на компьютере с 4 ГБ памяти) попробуйте отключить эту функцию для высвобождения ресурсов.

    Чтобы отключить CodeLens, выберите **Сервис > Параметры > Текстовый редактор > Все языки > CodeLens** и отмените выбор данной функции.

    Эта функция доступна в Visual Studio Professional и Visual Studio Enterprise.

### <a name="other-tools-and-extensions"></a>Другие инструменты и расширения

- **Отключение расширений**

    Расширения — это дополнительные программные компоненты в Visual Studio, которые предоставляют новые или расширяют имеющиеся функциональные возможности. Расширения часто могут выступать источником проблем с памятью. При возникновении подобных проблем попробуйте отключать расширения по одному за раз, чтобы оценить, как это влияет на сценарий или рабочий процесс.

    Чтобы отключить расширения, перейдите в раздел **Сервис | Расширения и обновления** и отключите нужное расширение.

- **Отключение конструктора XAML**

    Конструктор XAML по умолчанию включен, но потребляет ресурсы только при открытии XAML-файла. Если вы работаете с XAML-файлами, но не хотите использовать функциональные возможности конструктора, отключите его, чтобы освободить память.

    Чтобы отключить конструктор XAML, перейдите в раздел **Сервис > Параметры > Конструктор XAML > Включить конструктор XAML**  и отключите эту функцию.

- **Удаление рабочих нагрузок**

    Если вы не собираетесь использовать определенные рабочие нагрузки, удалите их с помощью установщика Visual Studio. Это позволяет оптимизировать расходы ресурсов при запуске и выполнении за счет пропуска ненужных пакетов и сборок.

## <a name="force-a-garbage-collection"></a>Принудительная сборка мусора

Среда CLR использует систему управления памятью, подразумевающую сборку мусора. В этой системе память иногда используется объектами, которые больше не нужны. Это временное состояние — сборщик мусора освободит эту память, основываясь на своей эвристике производительности и использования ресурсов. Вы можете заставить среду CLR собрать всю неиспользуемую память, используя сочетание клавиш в Visual Studio. Если имеется значительный объем мусора, ожидающего сборки, то принудительная сборка мусора позволяет снизить использование памяти процессом devenv.exe в диспетчере задач. Потребность в этом методе возникает довольно редко. Тем не менее после завершения операции, потребляющей много ресурсов (такой как полная сборка, сеанс отладки или событие открытия решения), он может помочь определить объем памяти, действительно используемый процессом. Так как среда Visual Studio является смешанной (управляемый и машинный код), собственный распределитель и сборщик мусора могут конкурировать за ограниченные ресурсы памяти. В условиях высокого использования памяти это может помочь принудительно запустить сборщик мусора.

Чтобы принудительно запустить сборку мусора, используйте сочетание клавиш: **CTRL+ALT+SHIFT+F12**, **CTRL+ALT+SHIFT+F12** (нажмите два раза).

Если принудительная сборка мусора обеспечивает работоспособность сценария, направьте отчет с помощью средства обратной связи Visual Studio, так как подобное поведение, скорее всего, указывает на ошибку.

Подробное описание сборщика мусора CLR см. в разделе [Основные сведения о сборке мусора](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>См. также

[Интегрированная среда разработки Visual Studio](../ide/visual-studio-ide.md)
