---
title: "Типизированные и нетипизированные наборы данных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: af42a48a311cadba9fc22a487d03492f92ba6469
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="typed-vs-untyped-datasets"></a>Типизированные и нетипизированные наборы данных
Типизированный набор данных представляет собой набор данных, извлекается из базового <xref:System.Data.DataSet> класса и затем использует сведения из **конструктора наборов данных**, который хранится в XSD-файл, чтобы создать новый, строго типизированными класс набора данных. Сведения из схемы (таблицы, столбцы и т. д.) создается и компилируются в этот новый класс набора данных как набор первого класса объектов и свойств. Поскольку типизированный набор данных наследует от базового <xref:System.Data.DataSet> класса, типизированный класс обладает все функциональные возможности <xref:System.Data.DataSet> класса и может использоваться с методами, которые принимает экземпляр <xref:System.Data.DataSet> класса в качестве параметра.  
  
 Нетипизированный набор данных, напротив, не имеет соответствующей встроенной схемы. Как и типизированный набор данных, нетипизированный набор данных содержит таблицы, столбцы и т. д., но те, которые доступны только как коллекции. (Тем не менее, создав вручную таблиц и других элементов данных нетипизированного набора данных, можно экспортировать структуру набора данных в качестве схемы с помощью набора данных <xref:System.Data.DataSet.WriteXmlSchema%2A> метод.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Доступ к данным в типизированных и нетипизированных наборов данных  
 Класс для типизированного набора данных имеет объектную модель, в которой его свойства принимают фактические имена таблиц и столбцов. Например если вы работаете с типизированного набора данных, может ссылаться на столбец с помощью следующего кода:  
  
 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]  
  
 Напротив Если вы работаете с нетипизированного набора данных, эквивалентный код будет:  
  
 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]  
  
 Типизированный доступ не только более удобными для чтения, а также полностью поддерживается технологией IntelliSense в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **редактор кода**. Помимо проще работать, синтаксис для типизированного набора данных обеспечивает тип проверки во время компиляции, значительно уменьшая вероятность возникновения ошибок при присвоении значений членам набора данных. Если изменить имя столбца в вашей <xref:System.Data.DataSet> класса и затем скомпилировать приложение, будет получена ошибка построения. Дважды щелкните ошибку сборки в **список задач**, можно перейти непосредственно к строке или строк кода, ссылающиеся на старое имя столбца. Доступ к таблицам и столбцам в типизированный набор данных также немного быстрее во время выполнения, так как доступ определяется во время компиляции, а не с помощью коллекций во время выполнения.  
  
 Несмотря на то, что типизированных наборов данных имеют много преимуществ, нетипизированный набор данных полезен в различных ситуациях. Самый очевидный случай — когда схема не доступен для набора данных. Это может произойти, например, если приложение взаимодействует с компонентом, который возвращает набор данных, но вы не знаете заранее является ее структуру. Аналогичным образом бывают ситуации, при работе с данными, не имеет статической предопределенной структуры. В этом случае нецелесообразно использовать типизированный набор данных, поскольку необходимо повторно создать класс типизированного набора данных при каждом изменении в структуре данных.  
  
 Как правило очень часто может создавать наборы данных динамически, без необходимости доступной схемы. В этом случае набор данных является просто удобной структурой, в котором можно хранить данные, при условии, что данные могут быть представлены в виде реляционной структуры. В то же время можно воспользоваться преимуществами возможности набора данных, такие как возможность сериализации данных для передачи их в другой процесс или записать в XML-файл.

## <a name="see-also"></a>См. также
[Средства набора данных](../data-tools/dataset-tools-in-visual-studio.md)