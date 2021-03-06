---
title: "CA2109: Проверьте видимые обработчики событий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 42b4ed61faae66c0a07e171a89a6ac9e4b9157e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: проверьте видимые обработчики событий
|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Обнаружен открытый или защищенный метод обработки событий.  
  
## <a name="rule-description"></a>Описание правила  
 Видимый извне метод обработки событий представляет угрозу безопасности, которая требует проверки.  
  
 Методы обработки событий следует раскрывать только в тех случаях, когда это совершенно необходимо. Обработчик событий, вызывающий метод, предоставленный тип делегата можно добавить к любому событию при условии, что соответствует подписей обработчика и события. События могут возникнуть в любой код и часто вызываются высоконадежным системный код в ответ на действия пользователя, например на нажатие кнопки. Добавление проверки безопасности к методу обработки событий не запрещает код регистрации обработчика событий, который вызывает метод.  
  
 Запрос не может надежно защитить метод, вызываемый обработчик событий. Запросы безопасности помогают защитить код от ненадежных вызывающих объектов путем проверки вызывающих объектов в стеке вызовов. Код, который добавляет обработчик событий к событию не обязательно должен находиться в стеке вызовов, при выполнении методов обработчика событий. Таким образом стек вызовов может только высоконадежным вызывающих объектов при вызове метода обработчика событий. В результате запросы, сделанные методом обработчика события для успешного выполнения. Кроме того запрошенное разрешение может быть подтверждено при вызове метода. По этим причинам риск устранения нарушения данного правила не может оцениваться только после просмотра метод обработки событий. При проверке кода, необходимо учитывайте следующее:  
  
-   Обработчик событий выполняет все операции, которые являются опасными или уязвимыми, например подтверждение разрешений или подавление разрешений неуправляемого кода?  
  
-   Каковы угрозы безопасности в и из кода, так как можно будет использовать в любое время с высокой только доверенные вызывающие объекты в стеке?  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, проверьте метод и рассмотрите следующие возможности:  
  
-   Сделать метод обработки событий неоткрытым?  
  
-   Можно ли переместить все опасные функции за пределы обработчика событий?  
  
-   Если требование безопасности состоит в том, это можно реализовать в других целях?  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила только после тщательного анализа безопасности, чтобы убедиться, что код не представляют угрозу безопасности.  
  
## <a name="example"></a>Пример  
 Ниже приведен метод обработки событий, который может быть неправильно использован вредоносным кодом.  
  
 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 