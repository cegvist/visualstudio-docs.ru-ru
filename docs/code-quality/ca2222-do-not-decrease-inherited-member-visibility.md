---
title: "CA2222: Не уменьшайте видимость унаследованных членов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac62bc901629e65d5104bede66046711dd879930
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: не уменьшайте видимость унаследованных членов
|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Закрытый метод в незапечатанный тип имеет подпись, идентичный открытый метод, объявленный в базовом типе. Закрытый метод не является последней.  
  
## <a name="rule-description"></a>Описание правила  
 Не следует изменять модификатор доступа для унаследованных членов. Если сделать унаследованный член закрытым, то доступ вызывающих объектов к реализации метода базового класса все равно не будет запрещен. Если сделать член закрытым, а незапечатанный тип, наследуемые типы могут вызывать последнюю открытую реализацию метода в иерархии наследования. Если нужно изменить модификатор доступа, метод должен быть помечен как окончательный, или его тип должны быть запечатаны, чтобы исключить возможность переопределения метода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените доступ к быть отличным от private. Кроме того если она поддерживается язык программирования, можно сделать метод конечный.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий это правило.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]