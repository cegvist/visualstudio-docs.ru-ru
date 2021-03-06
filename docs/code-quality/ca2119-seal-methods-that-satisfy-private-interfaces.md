---
title: "CA2119: Запечатайте методы, соответствующие частным интерфейсам | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b61a3e81ff7be1ff868f2dd9ce42dd5cb10522cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: запечатайте методы, соответствующие частным интерфейсам
|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Наследуемый открытый тип предоставляет реализацию переопределяемого метода `internal` (`Friend` в Visual Basic) интерфейса.  
  
## <a name="rule-description"></a>Описание правила  
 Методы интерфейса являются открытыми, которые нельзя изменить путем реализации типа. Внутренний интерфейс создает контракт, который не предназначен для реализации за пределами сборки, определяющий интерфейс. Открытый тип, реализующий метод внутреннего интерфейса с помощью `virtual` (`Overridable` в Visual Basic) модификатор позволяет вызвать метод для переопределения с помощью производного типа, который находится за пределами сборки. Если второй тип в определяющей сборке вызывает метод и ожидает только внутреннего контракта, поведение может быть нарушено, если вместо этого выполняется переопределенный метод во внешней сборке. Это создает уязвимость системы безопасности.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, предотвратить метод переопределение извне с помощью одного из следующих:  
  
-   Сделайте объявляющий тип `sealed` (`NotInheritable` в Visual Basic).  
  
-   Изменить доступность объявляющий тип для `internal` (`Friend` в Visual Basic).  
  
-   Удалите все открытые конструкторы из объявляющего типа.  
  
-   Реализуйте метод без использования `virtual` модификатор.  
  
-   Реализуйте метод явным образом.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила, если после тщательного анализа проблем безопасности не существует, могут быть использованы, если этот метод переопределен за пределами сборки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано типа `BaseImplementation`, который нарушает это правило.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## <a name="example"></a>Пример  
 В следующем примере используется реализация виртуального метода из предыдущего примера.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index)   
 [Интерфейсы](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)