---
title: "Безопасность текстовых шаблонов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5c6b8d64e02562887b2bc438943fdfe7be3b2e1c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="security-of-text-templates"></a>Безопасность текстовых шаблонов
Текстовые шаблоны имеют следующие проблемы безопасности:  
  
-   Текстовые шаблоны уязвимы для произвольного кода.  
  
-   Если механизм, используемый основным приложением для поиска процессора директив, не является безопасным, может быть запущен вредоносный процессор директив.  
  
## <a name="arbitrary-code"></a>Произвольный код  
 При создании шаблона, можно поместить код в \<## > тегов. Это позволяет произвольный код будет запускаться из текстового шаблона.  
  
 Убедитесь, что получение шаблонов из надежных источников. Убедитесь в том предупредить конечных пользователей приложения не должны выполнять шаблоны, которые не исходят из надежных источников.  
  
## <a name="malicious-directive-processor"></a>Вредоносный процессор директив  
 Текстовых шаблонов взаимодействует с узлом преобразования и один или несколько процессоров директив для преобразования текстового шаблона в выходной файл. Дополнительные сведения см. в разделе [процесс преобразования текстового шаблона](../modeling/the-text-template-transformation-process.md).  
  
 Если механизм, используемый основным приложением для поиска процессора директив, не является безопасным, оно выполняется риск выполнения вредоносных процессора директив. Вредоносный процессор директив может предоставить код, который выполняется в `FullTrust` режиме при выполнении шаблона. При создании узлом преобразования шаблона пользовательского текста, необходимо использовать безопасный механизм, таким как реестр, для поиска процессоры директив.