---
title: "CA1062: Проверьте аргументы открытых методов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f3661a9475935dbe92dfd55f566170ce46d69f84
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: проверьте аргументы открытых методов

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Видимый извне метод разыменовывает одного из его аргументов ссылки без проверки, является ли этот аргумент `null` (`Nothing` в Visual Basic).

## <a name="rule-description"></a>Описание правила

Все ссылочные аргументы, передаваемые внешним видимым методам должны проверяться на `null`. При необходимости, создавать <xref:System.ArgumentNullException> когда аргумент является `null`.

Если метод может вызываться из неизвестного сборки, поскольку он объявлен как открытый или защищенный, следует проверить все параметры метода. Метод предназначен для вызывать только известные сборок, следует сделать метод внутренней и применить <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> атрибут к сборке, содержащего метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение данного правила, проверьте каждый ссылочный аргумент для `null`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно подавить предупреждение из этого правила, если вы уверены, что со снятой ссылкой параметр был проверен другим вызовом метода в функции.

## <a name="example"></a>Пример

В следующем примере показано метод, который нарушает правила и метод, соответствующий этому правилу.

 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Пример

Конструкторы копирования, заполняющие поля или свойства, которые являются ссылочными объектами, также могут нарушать правило CA1062. Нарушение возникает, если копируемый объект, который передается в конструктор копии может быть `null` (`Nothing` в Visual Basic). Чтобы устранить нарушение, используйте статический (Shared в Visual Basic) метод для проверки того, что копируемый объект не равен null.

В следующем `Person` пример класса `other` объект, передаваемый `Person` конструктор копии может быть `null`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Пример

В следующем примере пересмотра `Person` примере `other` объект, передаваемый в конструктор копирования сначала проверяется на равенство null в `PassThroughNonNull` метод.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}

```