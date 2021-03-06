---
title: "CA1506: Избегайте чрезмерного соединения классов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d5303e147ae001d887784aa401d456d23485c453
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: избегайте чрезмерного соединения классов
|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Категория|Microsoft.Maintainability|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Тип или метод работает совместно с другими типами.  
  
## <a name="rule-description"></a>Описание правила  
 Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.  
  
 Типы и методы с высокой степенью взаимозависимости классов могут затруднить поддержку. Рекомендуется использовать типы и методы, которые низкой степенью соединения и высокой связности.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Для устранения нарушения данного правила, попробуйте изменить тип или метод, чтобы уменьшить количество типов, к которым она связана.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Исключите это предупреждение, когда тип или метод считается обслуживаемым несмотря на большое количество зависимостей от других типов.  
  
## <a name="see-also"></a>См. также  
 [Предупреждения удобства обслуживания](../code-quality/maintainability-warnings.md)   
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)