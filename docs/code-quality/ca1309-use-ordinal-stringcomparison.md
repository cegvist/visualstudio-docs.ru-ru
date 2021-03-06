---
title: "CA1309: Используйте порядковый параметр StringComparison | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cf913eea3f156595c9b9194b3d8a74e71b848367
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: используйте порядковый параметр StringComparison
|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Не задает операции сравнения строк, лингвистической <xref:System.StringComparison> параметра к **порядковый номер** или **OrdinalIgnoreCase**.  
  
## <a name="rule-description"></a>Описание правила  
 Многие строковые операции, наиболее важные <xref:System.String.Compare%2A?displayProperty=fullName> и <xref:System.String.Equals%2A?displayProperty=fullName> методы, теперь предоставляют перегрузку, которая принимает <xref:System.StringComparison?displayProperty=fullName> значение перечисления в качестве параметра.  
  
 При указании либо **StringComparison.Ordinal** или **StringComparison.OrdinalIgnoreCase**, то строковое сравнение будет лингвистической. То есть функции, характерные для естественного языка игнорируются при принятии решений сравнения. Это означает, что решения основываются на простых байтовых сравнений и игнорировать таблиц регистров или эквивалентности, которые параметризуются языком и региональными параметрами. В результате путем явного задания для параметра либо **StringComparison.Ordinal** или **StringComparison.OrdinalIgnoreCase**, кода часто увеличивается скорость, повышает правильность и становится более надежным.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените метод сравнения строк на перегрузку, которая принимает <xref:System.StringComparison?displayProperty=fullName> перечисления в качестве параметра и указать либо **порядковый номер** или **OrdinalIgnoreCase**. Например, измените `String.Compare(str1, str2)` на `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно отключать предупреждение из этого правила, если библиотека или приложение предназначено для ограниченного круга локальных пользователей или когда следует использовать семантику текущего языка и региональных параметров.  
  
## <a name="see-also"></a>См. также  
 [Предупреждения глобализации](../code-quality/globalization-warnings.md)   
 [CA1307: укажите StringComparison](../code-quality/ca1307-specify-stringcomparison.md)