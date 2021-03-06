---
title: "CA2201: Не вызывайте зарезервированные типы исключений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11e00594c1cf279fb6b07791bb48f2222cc9c79b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: не вызывайте зарезервированные типы исключений
|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Метод создает тип исключения, слишком общими, или, зарезервированные для среды выполнения.  
  
## <a name="rule-description"></a>Описание правила  
 Указанные ниже типы исключений имеют слишком общий характер для предоставляет достаточно сведений для пользователя:  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 Указанные ниже типы исключений являются зарезервированными и должно выдаваться только средой CLR:  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Не создавайте общих исключений**  
  
 Если вы вызываете исключения общего типа, таких как <xref:System.Exception> или <xref:System.SystemException> в библиотеке или платформе, вынуждает объекты-получатели перехватывать все исключения, включая неизвестные исключения, которые они не известны способы их обработки.  
  
 Вместо этого исключение более производный тип, который уже существует в структуре, или создать собственный тип, производный от <xref:System.Exception>.  
  
 **Создание конкретных исключений**  
  
 В следующей таблице показаны параметры и исключения, которые могут вызывать при проверке параметров, включая значение параметра в метод доступа set свойства:  
  
|Описание параметра|Исключение|  
|---------------------------|---------------|  
|`null`ссылка|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Вне диапазона допустимых значений (таких как индекс для коллекции или списка)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Недопустимый `enum` значение|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Содержит формат, который не соответствует спецификациям параметров метода (например, строка формата для `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|  
|В противном случае значение недопустимо|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Когда операция недопустима для текущего состояния объекта throw<xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Исключение при выполнении операции на объекте, который был удален<xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Когда операция не поддерживается (например, в переопределенном **методы Stream.Write** в поток открыт для чтения) throw<xref:System.NotSupportedException?displayProperty=fullName>  
  
 Исключение при преобразовании приведет к переполнению, (например, в явной перегрузке оператора приведения)<xref:System.OverflowException?displayProperty=fullName>  
  
 В других случаях рекомендуется создать свой собственный тип, производный от <xref:System.Exception> и создает исключение, которое.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените тип вызванного исключения для определенного типа, который не является одним из зарезервированных типов.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1031: не перехватывайте типы общих исключений](../code-quality/ca1031-do-not-catch-general-exception-types.md)