---
title: "Форматирование кода в Инструментах Python для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0f1631-360b-45d4-a0cb-01c3c10d25f2
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: c1d7a19438b796c5666daecef33052e43d1f720f
ms.lasthandoff: 03/10/2017

---

# <a name="formatting-python-code"></a>Форматирование кода Python

Форматирование кода в Инструментах Python для Visual Studio (PTVS) версии 2.0 и более поздних версий позволяет быстро переформатировать код в соответствии c предварительно настроенными параметрами форматирования.

- Чтобы форматировать выделенный фрагмент, выберите **Правка > Дополнительно > Форматирование выделения** или нажмите клавиши Ctrl+E, F.
- Чтобы форматировать весь файл, выберите **Правка > Дополнительно > Форматирование документа** или нажмите клавиши Ctrl+E, D.

Параметры форматирования задаются в меню **Средства > Параметры > Текстовый редактор > Python > Форматирование** и на соответствующих вложенных вкладках. По умолчанию здесь настроено надмножество правил из [руководства по стилю PEP 8](http://www.python.org/dev/peps/pep-0008/). Вкладка **Общие** определяет, когда применяется форматирование. Остальные три вложенные страницы описаны в следующих разделах.

Также PTVS предлагает в меню **Правка > Дополнительно** полезную команду [Fill Comment Paragraph](#fill-comment-paragraph) (Заполнение параграфа комментария).

## <a name="spacing"></a>Интервал

Элементы управления в разделе **Интервал** определяют, нужно ли вставлять и (или) удалять пробелы в различных языковых конструкциях. Каждый параметр имеет три возможных значения.

- Флажок установлен: пробелы всегда применяются.
- Флажок снят: пробелы всегда удаляются.
- Неопределенное состояние: сохраняется установленное форматирование.

В следующих таблицах приведены примеры для различных параметров.

| Параметр определения класса | Помечено | Флажок снят |
| --- | --- | --- | 
| Вставлять пробел между именем и списком базовых классов в объявлении класса | `class X (object): pass` | `class X(object): pass` | 
| Вставлять пробел между скобками в списке баз | `class X( object ): pass` | `class X(object): pass` |
| Вставлять пробел между пустыми скобками в списке баз | `class X( ): pass` | `class X(): pass` |

<br/>

| Параметр определения функций | Помечено | Флажок снят |
| --- | --- | --- |
| Вставлять пробел между именем и списком аргументов в объявлении функции | `def X (): pass` | `def X(): pass` | 
| Вставлять пробел между скобками в списке аргументов | `def X( a, b ): pass` | `def X(a, b): pass` |
| Вставлять пробел между пустыми скобками в списке аргументов | `def X( ): pass` | `def X(): pass` |
| Вставлять пробелы вокруг символа "=" для значений аргументов по умолчанию | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| Вставлять пробел до и после операторов аннотации вывода | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Параметр операторов | Помечено | Флажок снят |
| --- | --- | --- |
| Вставлять пробелы вокруг бинарных операторов | `a + b` | `a+b` |
| Вставлять пробелы вокруг операторов присваивания | `a = b` | `a=b` |

<br/>

| Параметр интервалов для выражений | Помечено | Флажок снят |
| --- | --- | --- |
| Вставлять пробел между именем функции и списком аргументов при вызове функции | `X ()` | `X()` |
| Вставлять пробел между скобками с пустым списком аргументов | `X( )` | `X()` |
| Вставлять пробел между скобками со списком аргументов | `X( a, b )` | `X(a, b)` |
| Вставлять пробел между скобками выражения | `( a )` | `(a)` |
| Добавлять пробел между пустыми скобками кортежа | `( )` | `()` |
| Добавлять пробел между скобками кортежа | `( a, b )` | `(a, b)` |
| Вставлять пробел между пустыми квадратными скобками | `[ ]` | `[]` |
| Вставлять пробелы между квадратными скобками списков | `[ a, b ]` | `[a, b]` |
| Вставлять пробел перед открывающейся квадратной скобкой | `x [i]` | `x[i]` |
| Вставлять пробел между квадратными скобками | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Операторы

Раздел **Операторы** управляет автоматическим изменением некоторых операторов в более привычные для Python форматы.

| Параметр | До форматирования | После форматирования |
| --- | --- | --- |
| Перенос импортированных модулей на новую строку | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Удаление лишних символов точки с запятой | `x = 42;` | `x = 42` |
| Размещение нескольких операторов на несколько строк | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |


## <a name="wrapping"></a>Перенос по словам

**Перенос по словам** позволяет задать параметр **Maximum comment width** (Максимальная длина комментария) (по умолчанию имеет значение 80), и тогда при установленном параметре **Wrap comments that are too wide** (Переносить слишком длинные комментарии) PTVS будет переформатировать комментарии так, чтобы не нарушать это ограничение.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```



## <a name="fill-comment-paragraph-command"></a>Команда "Заполнение параграфа комментария"

Команда **Правка > Дополнительно > Заполнение параграфа комментария** (вызывается клавишами Ctrl+E,Ctrl+P) изменяет форматирование текста комментария, объединяя короткие строки и разбивая слишком длинные.

Например:

```python
# foo 
# bar
# baz
```

изменяется на:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

изменяется на:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```