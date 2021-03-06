---
title: "CA2132: Конструкторы по умолчанию должно быть по крайней мере такой критический, как конструкторы по умолчанию базового типа | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 752103825a25c4352ccc21730b8d2b7265f8f41b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: конструкторы по умолчанию должны быть по крайней мере настолько критичными, как и конструкторы базовых типов по умолчанию
|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
> [!NOTE]
>  Это предупреждение применяется только для кода, выполняющего CoreCLR (версия среды CLR, предназначенную для веб-приложений Silverlight).  
  
## <a name="cause"></a>Причина  
 Атрибут прозрачности конструктора по умолчанию производного класса не такой критический, как прозрачность базового класса.  
  
## <a name="rule-description"></a>Описание правила  
 Типы и члены, которые имеют <xref:System.Security.SecurityCriticalAttribute> не может использоваться кодом приложения Silverlight. Критичные в плане безопасности типы и элементы могут использоваться только надежным кодом в среде .NET Framework для библиотеки классов Silverlight. Поскольку открытая или защищенная конструкция в производном классе должна иметь ту же или большую прозрачность, чем ее базовый класс, класс в приложении не может быть производным от класса, помеченного как SecurityCritical.  
  
 Для кода платформы CoreCLR Если базовый тип имеющий открытый или защищенный непрозрачный конструктор затем производный тип должен подчиняться правилам наследования конструктора по умолчанию. Производный тип также должен иметь конструктор по умолчанию, и этот конструктор должен быть по крайней мере критический конструктор по умолчанию базового типа.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение, удалите тип или не являются производными от типа не прозрачный с точки зрения безопасности.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не следует отключать предупреждения из этого правила. Нарушение этого правила с помощью кода приложения приведет к CoreCLR отказывается загрузить тип с <xref:System.TypeLoadException>.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### <a name="comments"></a>Комментарии