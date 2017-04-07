---
title: "Работа с C++ и Python в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 3/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7dbda92-21bf-4af0-bb34-29b8bf231f32
description: "Процедура и шаги для написания модуля или расширения C++ для Python в Visual Studio"
caps.latest.revision: 1
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
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: 730207e42f42c0cd5d1b78dc558e58267343d186
ms.lasthandoff: 03/27/2017

---

# <a name="creating-a-c-extension-for-python"></a>Создание расширения C++ для Python

Модули, написанные на C++ (или C), обычно используются для расширения возможностей интерпретатора Python, а также для доступа к низкоуровневым возможностям операционной системы. Существует три основных типа модулей:

- Модули акселератора: так как Python — это интерпретируемый язык, для повышения производительности некоторые фрагменты кода могут быть написаны на C++. 
- Модули оболочки: предоставляют существующие интерфейсы C/C++ для кода Python или API, упрощающий работу за счет использования функций языка Python.
- Модули низкоуровневого системного доступа: созданы для доступа к низкоуровневым функциям среды выполнения CPython, операционной системы и базового оборудования. 

В этой статье рассматривается создание модуля расширения C++ для CPython, вычисляющего гиперболический тангенс и вызывающего его из кода Python. Чтобы продемонстрировать разницу в производительности, вы сначала создадите и протестируете подпрограмму в Python.

Используемый здесь подход применяется для стандартных модулей CPython, как описано в [документации по Python](https://docs.python.org/e/c-api/). Сравнение этого и других средств описано в разделе [Альтернативные подходы](#alternative-approaches) в конце этой статьи.

## <a name="prerequisites"></a>Предварительные требования

Это пошаговое руководство предназначено для Visual Studio 2017 Preview с рабочими нагрузками **Разработка классических приложений на C++** и **Разработка на Python** с параметрами по умолчанию (например, с Python 3.6 в качестве интерпретатора по умолчанию). В рабочей нагрузке **Разработка на Python** также установите справа флажок **Собственные средства разработки Python**. Это позволит задать большинство описанных здесь параметров. (Этот параметр также автоматически включает рабочую нагрузку C++.)

![Выбор параметра "Собственные средства разработки Python"](media/cpp-install-native.png)

Дополнительные сведения, включая использование других версий Visual Studio, см. в разделе [Установка поддержки Python для Visual Studio](installation.md). Если вы устанавливаете Python отдельно, обязательно выберите параметры **Download debugging symbols** (Скачать отладочные символы) и **Download debug binaries** (Скачать двоичные файлы отладки) в разделе **Дополнительные параметры** установщика. Это гарантирует наличие необходимых отладочных библиотек, если вы решите сделать отладочную сборку.

## <a name="create-the-python-application"></a>Создание приложения Python

1. Создайте новый проект Python в Visual Studio. Для этого выберите команду **Файл > Создать > Проект** в меню, выполните поиск слова "Python", выберите шаблон **Приложение Python**, укажите подходящее имя и расположение, а затем нажмите кнопку **ОК**.

1. В файл `.py` проекта вставьте следующий код, отвечающий за тестирование производительности при вычислении гиперболического тангенса (для упрощения сравнения реализуется без использования математической библиотеки). Вы можете ввести код вручную, чтобы оценить некоторые [функции редактирования Python](code-editing.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 100000
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tanger function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()

        result = fn(DATA)

        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Запустите программу с помощью команды **Отладка > Запуск без отладки** (CTRL+F5), чтобы просмотреть результаты. Вы увидите, что выполнение каждого теста занимает несколько секунд.

## <a name="create-the-core-c-project"></a>Создание основного проекта C++

1. Щелкните правой кнопкой мыши решение в обозревателе решений и выберите **Добавить > Новый проект...**. Решение Visual Studio может содержать вместе проекты Python и C++.

1. Выполните поиск "C++", выберите **Пустой проект**, укажите имя (например, TanhBenchmark) и нажмите кнопку **ОК**. Примечание. Если вы уже установили **Собственные средства разработки Python** вместе с Visual Studio 2017, то можете начать с шаблона **Модуль расширения Python**, в котором основная часть описанных здесь функций уже реализована. Но в этом пошаговом руководстве начало работы с пустого проекта позволяет шаг за шагом продемонстрировать создание модуля расширения.

1. Создайте файл C++ в новом проекте. Для этого щелкните правой кнопкой мыши узел **Исходные файлы** и выберите **Добавить > Новый элемент...**, выберите **Файл C++**, присвойте ему имя (например, `module.cpp`) и нажмите кнопку **ОК**. Этот шаг необходим для включения страниц свойств C++ в следующих шагах.

1. Щелкните правой кнопкой мыши новый проект и выберите **Свойства**, затем в верхней части появившегося диалогового окна **Страницы свойств** задайте для параметра **Конфигурация** значение **Все конфигурации**.

1. Задайте определенные свойства, как описано ниже, а затем нажмите кнопку **Применить** (чтобы кнопка **Применить** появилась, может потребоваться щелкнуть за пределами изменяемого поля).

    | Вкладка | Свойство | Значение | 
    | --- | --- | --- |
    | Общие | Общие > Целевое имя | Задайте здесь значение, которое точно соответствует имени модуля, считываемому Python. |
    | | Общие > Конечное расширение | .pyd |
    | | Значения по умолчанию для проекта > Тип конфигурации | Динамическая библиотека (.dll) |
    | C/C++ > Общие | Дополнительные каталоги включаемых файлов | Добавьте подходящую для вашей установки папку `include` Python, например `c:\Python36\include`. |     
    | C/C++ > Создание кода | Библиотека времени выполнения | Многопоточная DLL (/MD) (см. предупреждение ниже) |
    | C/C++ > Препроцессор | Определения препроцессора | Добавьте `Py_LIMITED_API;` в начало строки. Это ограничивает некоторые функции, которые можно вызывать из Python, и расширяет возможности по переносу кода между разными версиями Python. |
    | Компоновщик > Общие | Дополнительные каталоги библиотек | Добавьте подходящую для вашей установки папку `lib` Python с файлами `.lib`, например `c:\Python36\libs`. (Нужно указать папку `libs`, содержащую файлы `.lib`, а *не* папку `Lib`, содержащую файлы `.py`.) | 

    > [!Tip]
    > Если вы не видите вкладку C/C++, значит в проекте нет файлов, определенных как исходные файлы C и C++. Это может произойти при создании исходного файла без расширения `.c` или `.cpp`. Например, если ранее вы случайно ввели `module.coo` вместо `module.cpp` в диалоговом окне создания элемента, Visual Studio создает файл, но не задает для него тип "Код C/C+", что требуется для активации вкладки свойств C/C++. Это верно и в случае переименования файла с использованием `.cpp`. Чтобы устранить эту проблему, щелкните файл правой кнопкой мыши в обозревателе решений, выберите **Свойства** и задайте для параметра **Тип файла** значение **Код C/C++**.

    > [!Warning]
    > Не устанавливайте для параметра **C/C++ > Создание кода > Библиотека времени выполнения** значение "Многопоточная DLL с возможностью отладки (/MDd)" даже для конфигурации отладки. Нужно выбрать среду выполнения "Многопоточная DLL (/MD)", так как именно с ее помощью создавались двоичные файлы Python не для отладки. Если задать параметр /MDd, при создании конфигурации отладки для библиотеки DLL возникает ошибка *C1189: Py_LIMITED_API несовместим с Py_DEBUG, Py_TRACE_REFS и Py_REF_DEBUG*. Кроме того, если удалить `Py_LIMITED_API` во избежание этой ошибки сборки, Python аварийно завершит работу при попытке импортировать модуль. (Этот сбой возникает в вызове библиотеки DLL `PyModule_Create`, как описано ниже, и сопровождается сообщением *Fatal Python error: PyThreadState_Get: no current thread* (Неустранимая ошибка Python: PyThreadState_Get — нет текущего потока).)
    >
    > Обратите внимание, что параметр /MDd используется для сборки двоичных файлов отладки Python (например, python_d.exe), но его выбор для библиотеки DLL расширения по-прежнему вызывает ошибку сборки с `Py_LIMITED_API`.
   
1. Щелкните проект C++ правой кнопкой мыши и выберите **Сборка**, чтобы протестировать конфигурации (отладочную и окончательную). Обратите внимание, что файлы `.pyd` находятся в папке *solution* в каталоге **Debug** и **Release**, а не в самой папке проекта C++.

1. Добавьте следующий код в главный файл `.cpp` проекта:

    ```cpp
    #include <Windows.h>
    #include <cmath>    

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh(x) {
        return sinh(x) / cosh(x);
    }
    ```

1. Еще раз выполните сборку проекта C++, чтобы убедиться в правильности кода.


## <a name="convert-the-c-project-to-an-extension-for-python"></a>Преобразование проекта C++ в расширение для Python

Чтобы превратить библиотеку DLL на C++ в расширение для Python, нужно изменить экспортированный метод для взаимодействия с типами Python. После этого нужно добавить функцию, экспортирующую модуль, а также определения методов модуля. Общие сведения о приведенном здесь примере см. в [справочном руководстве по API Python/C](https://docs.python.org/3/c-api/index.html) и в особенности в разделе об [объектах модуля](https://docs.python.org/3/c-api/module.html) на сайте python.org. (Не забудьте выбрать свою версию Python в раскрывающемся списке в правом верхнем углу.)

1. В начало файла C++ включите `Python.h`:

    ```cpp
    include <Python.h>
    ```

1. Измените метод `tanh`, чтобы он принимал и возвращал типы Python:

    ```cpp
    PyObject* tanh(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Добавьте структуру, определяющую способ представления функции `tanh` C++ для Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Добавьте структуру, определяющую модуль так, как его считывает Python:

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. Добавьте метод, вызываемый Python при загрузке модуля. Он должен иметь имя `PyInit_<module-name>`, где *&lt;module_name&gt;* точно соответствует свойству **Общие > Конечное имя** проекта C++ (то есть соответствует имени файла `.pyd`, созданного проектом).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Еще раз выполните сборку библиотеки DLL, чтобы проверить код.

## <a name="test-the-code-and-compare-the-results"></a>Тестирование кода и сравнение результатов

Теперь, когда библиотека DLL структурирована как расширение Python, можно ссылаться на нее из проекта Python, импортировать модуль и использовать его методы.

Предоставить Python доступ к библиотеке DLL можно двумя способами. Во-первых, можно добавить ссылку из проекта Python в проект C++ при условии, что они находятся в одном решении Visual Studio:

1. В обозревателе решений щелкните правой кнопкой мыши проект Python и выберите **Ссылки**. В диалоговом окне откройте вкладку **Проекты**, выберите проект **superfastcode** и нажмите кнопку **ОК**.

Во-вторых, можно установить модуль в глобальном окружении Python, сделав его доступным в других проектах Python. Обратите внимание, что при этом обычно требуется обновить базу данных завершения IntelliSense для этого окружения, как и при извлечении модуля из окружения.

1. Если вы используете Visual Studio 2017, запустите установщик Visual Studio, выберите **Изменить**, затем **Отдельные компоненты > Компиляторы, средства сборки и среды выполнения > Набор инструментов Visual C++ 2015.3 версии 140**. Это вызвано тем, что Python (для Windows) сам создан с помощью Visual Studio 2015 (версия 14.0), и поэтому ожидает наличие этих средств при создании расширения одним из описанных здесь способов.

1. Создайте файл с именем `setup.py` в проекте C++. Для этого щелкните проект правой кнопкой мыши, выберите пункт **Добавить > Новые элементы...*, выполните поиск слова "Python", выберите**Файл Python**, назовите его setup.py и нажмите кнопку **ОК**. Когда файл откроется в редакторе, вставьте в него следующий код:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    Документация к этому скрипту приведена в статье о [создании расширений на C и C++](https://docs.python.org/3/extending/building.html) (python.org).

1. Код `setup.py` велит Python создать расширение (с помощью набора инструментов C++ Visual Studio 2015), что происходит в командной строке. Откройте командную строку с повышенными привилегиями, перейдите в папку с проектом C++ (и `setup.py`), а затем введите следующую команду:

    ```bash
    pip install .
    ```

Теперь можно вызвать код `tanh` модуля и сравнить его эффективность с реализацией на языке Python:

1. Добавьте следующие строки в `tanhbenchmark.py`, чтобы вызвать метод `fast_tanh`, экспортированный из библиотеки DLL, и добавить его в результаты тестирования. Если ввести оператор `from s` вручную, вы увидите `superfastcode` в списке завершения, а после ввода `import` вы увидите метод `fast_tanh`.

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Запустите программу Python, и вы увидите, что подпрограмма на C++ выполняется примерно в 15–20 раз быстрее, чем реализация на языке Python.

## <a name="debug-the-c-code"></a>Отладка кода C++

Поддержка Python в Visual Studio включает в себя возможность [совместной отладки кода Python и C++](debugging-mixed-mode.md). Это можно продемонстрировать на следующем примере:

1. Щелкните проект Python правой кнопкой мыши в обозревателе решений, выберите **Свойства**, откройте вкладку **Отладка** и выберите параметр **Отладка > Разрешить отладку машинного кода**.

    > [!Tip]
    > При включении отладки машинного кода окно вывода Python может исчезнуть сразу после завершения программы без обычной паузы с сообщением "Для продолжения нажмите любую клавишу...". Чтобы сделать паузу принудительно, добавьте параметр `-i` в поле **Запуск > Аргументы интерпретатора** на вкладке **Отладка** при включении отладки машинного кода. Это приведет к переходу интерпретатора Python в интерактивный режим по завершении кода, после чего он ожидает нажатия клавиш CTRL+Z и ВВОД для выхода. (Кроме того, если вы не против изменения кода Python, можно добавить в конец программы операторы `import os` и `os.system("pause")`. Это дублирует исходный запрос с паузой.)

1. В коде C++ установите точку останова на первой строке в методе `tanh`, а затем запустите отладчик. Вы увидите, что при вызове этого кода отладчик останавливается:

    ![Остановка на точке останова в коде C++](media/cpp-debugging.png)

1. На этом этапе вы можете пошагово выполнить код C++, проверить переменные и т. д., как описано в разделе [Совместная отладка C++ и Python](debugging-mixed-mode.md).

## <a name="alternative-approaches"></a>Альтернативные подходы 

Существуют и другие средства для создания расширений Python, как описано в следующей таблице. Первый пункт для CPython уже рассмотрен в этой статье.

| Подход | Появление | Представители | Преимущества | Недостатки |
| --- | --- | --- | --- | --- |
| Модули расширений C/C++ для CPython | 1991 | Стандартная библиотека | [Подробная документация и учебники](https://docs.python.org/e/c-api/). Полный контроль. | Компиляция, переносимость, управление ссылками. Хорошее знание C. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Создание привязок сразу для нескольких языков. | Чрезмерные затраты, когда единственной целью является Python. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Отсутствие компиляции, широкая доступность. | Обращение к структурам C и их изменение затруднено и подвержено ошибкам. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Аналогичен Python. Высокая степень зрелости. Высокая производительность. | Компиляция, новый синтаксис и цепочка инструментов. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Простота интеграции, совместимость с PyPy. | Новый, менее зрелый. |
