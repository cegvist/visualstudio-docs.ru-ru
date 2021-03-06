---
title: "Ca1027: следует Помечать перечисления атрибутом FlagsAttribute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9c80b90e1b1fe0ba89717a175666a68c3812665c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: следует помечать перечисления атрибутом FlagsAttribute
|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Значения открытого перечисления являются степенями двух или являются комбинацией других значений, которые определены в перечислении, и <xref:System.FlagsAttribute?displayProperty=fullName> атрибут не задан. Во избежание ложных положительных результатов, данное правило сообщает о нарушениях для перечислений с непрерывными значениями.  
  
## <a name="rule-description"></a>Описание правила  
 Перечисление является типом значения, которое определяет набор связанных именованных констант. Применить <xref:System.FlagsAttribute> к перечислению, когда его именованные константы могут быть объединены осмысленным образом. Например рассмотрим перечисление дней недели в приложении, которое отслеживает какой день ресурсы доступны. Если доступность каждого ресурса кодируется с помощью перечисления с <xref:System.FlagsAttribute> могут быть представлены присутствует любое сочетание дней. При отсутствии атрибута может быть представлен только один день недели.  
  
 Для полей, которые хранятся комбинируемые перечисления отдельные значения перечислений обрабатываются как группы битов в поле. Поэтому такие поля иногда называются *битовые поля*. Для объединения значений перечисления для хранения в битовом поле, используйте условные логические операторы. Чтобы протестировать битовое поле, чтобы определить наличие конкретного значения перечисления, используйте логические операторы. Для битового поля для хранения и извлечения правильно комбинируемых значений перечисления каждого значения, определенные в перечислении должен быть возведения в квадрат. Если это не так, логические операторы не смогут извлечь значения отдельных перечисления, которые хранятся в поле.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте <xref:System.FlagsAttribute> к перечислению.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила, если не хотите, чтобы быть комбинируемых значений перечисления.  
  
## <a name="example"></a>Пример  
 В следующем примере `DaysEnumNeedsFlags` является перечислением, отвечающий требованиям по использованию <xref:System.FlagsAttribute>, но не имеет. `ColorEnumShouldNotHaveFlag` Перечисление не имеет значения, которые представляют собой степени двух, но неправильно указывает <xref:System.FlagsAttribute>. Это нарушает правило [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).  
  
 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.FlagsAttribute?displayProperty=fullName>