---
title: "CA1052: Типы со статическими заполнителями должны быть запечатаны | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d9ce807aca8b28a279a3a423802196e710f63dea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: типы со статическими заполнителями должны быть запечатаны
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип содержит только статические элементы и не объявлен с [запечатанный](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) модификатор.  
  
## <a name="rule-description"></a>Описание правила  
 В этом правиле предполагается, что тип, который содержит только статические члены не предназначено для наследуется, поскольку тип не предоставляет никаких функциональных возможностей, который может быть переопределен в производном типе. Тип, который не предназначен для наследования должны быть помечены `sealed` модификатор, чтобы запретить его использование в качестве базового типа.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, пометить тип как `sealed`. Если вы используете [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 или более поздней версии, лучшим подходом является пометить тип как `static`. Таким образом можно избежать необходимости объявлять закрытый конструктор для предотвращения создания класса.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила только в том случае, если тип должен наследоваться. Отсутствие `sealed` модификатор предполагает, что тип является полезны в качестве базового типа.  
  
## <a name="example-of-a-violation"></a>Пример нарушения  
  
### <a name="description"></a>Описание:  
 В следующем примере показано тип, нарушающий правило.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Исправьте модификатором Static  
  
### <a name="description"></a>Описание:  
 В следующем примере показано, как устранить нарушение этого правила, пометив тип с `static` модификатор.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1053: типы статических владельцев не должны иметь конструкторы](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
