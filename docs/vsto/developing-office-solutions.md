---
title: "Разработка решений Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bb3727d95fab03d2485c26f5858e0dbea7fe7543
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="developing-office-solutions"></a>Разработка решений Office
  После разработки проекта с помощью Office Developer Tools в Visual Studio и настройки файлов проекта можно начать реализовывать код и пользовательский интерфейс.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Заинтересованы в разработке решений, расширяющих возможности Office через [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и их можно создавать с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="office-solutions-programming-model"></a>Модель программирования решений Office  
 Объектная модель Office предоставляет широкий набор объектов, которые можно использовать. При программировании решений Office с помощью управляемого кода вы создаете код, который использует типы в основных сборках взаимодействия Office. В решениях, создаваемых с помощью шаблонов проектов Office в Visual Studio, также можно разрабатывать код непосредственно для созданных классов в своем проекте. Для получения дополнительной информации см. [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="programming-different-types-of-office-solutions"></a>Программирование различных типов решений Office  
 Тип создаваемого решения определяет, какие функции можно использовать в проекте. Например, элементы управления Windows Forms и расширенные элементы управления Office (которые называются *элементы управления ведущего приложения*) можно добавлять в настройки на уровне документа путем перетаскивания элементов из **панели элементов** в Visual Studio во время разработки. Однако при разработке надстройки VSTO можно только добавлять эти элементы управления в документы во время выполнения путем написания кода.  
  
 Дополнительные сведения о функциях, характерных для различных типов решений, см. в следующих статьях:  
  
-   [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
-   [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
 Дополнительные сведения о планировании создания решений Office и процедурах создания проектов см. в статье [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)|Описание различных аспектов написания кода в решениях Office.|  
|[Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)|Общие сведения о модели программирования надстроек VSTO и связанных задачах программирования.|  
|[Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)|Общие сведения о модели программирования настроек на уровне документа и связанных задачах программирования.|  
|[Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)|Описание различных способов настройки пользовательского интерфейса приложений Office с помощью надстроек VSTO и настроек на уровне документа.|  
|[Данные в решениях Office](../vsto/data-in-office-solutions.md)|Описание различных способов работы с данными в решениях Office, например, привязки данных к элементам управления и кэширования данных в настройках на уровне документа.|  
|[Влияние функции "Автосохранение" на решения для Office](./how-autosave-impacts-office-solutions.md)|Описывает изменения, которые может потребоваться вносить в решениях Office, когда включена функция автоматического сохранения.|
|[Устранение неполадок при работе с решениями Office](../vsto/troubleshooting-office-solutions.md)|Советы по решению типичных проблем, которые могут происходить при создании решений Office.|  
|[Поддержка потоков в Office](../vsto/threading-support-in-office.md)|Общие сведения о работе с несколькими потоками в решениях Office.|  
|[Специальные возможности в проектах Office](../vsto/accessibility-in-office-projects.md)|Описание специальных возможностей, доступных в решениях Office.|  
  
## <a name="see-also"></a>См. также  
 [Как: создавать и изменять настраиваемые свойства документа](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Как: чтение и запись в свойства документа](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Как: целевой многоязыкового пользовательского интерфейса Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Walkthrough: Creating Your First VSTO Add-in for Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  (Пошаговое руководство. Создание первой надстройки VSTO для Excel)  
 [Пошаговое руководство: Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Пошаговое руководство: Создание первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Пошаговое руководство: Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Пошаговое руководство: Создание первой надстройки VSTO для проекта](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Пошаговое руководство: Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Пошаговое руководство. Создание первой настройки на уровне документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  