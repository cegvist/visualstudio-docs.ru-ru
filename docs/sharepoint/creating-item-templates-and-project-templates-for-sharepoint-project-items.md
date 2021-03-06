---
title: "Создание элемента шаблоны элементов проекта SharePoint | Документы Microsoft"
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
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7f64abf2327d4e7702020a53c88d0d2c640e0756
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="creating-item-templates-and-project-templates-for-sharepoint-project-items"></a>Создание шаблонов элементов и проектов для элементов проектов SharePoint
  При определении настраиваемого типа элемента проекта SharePoint, можно связать его с шаблоном элемента или шаблон проекта, чтобы другие разработчики могут использовать элемент проекта в Visual Studio. Можно также создать мастер для шаблона.  
  
 Например Visual Studio включает шаблон проекта или шаблона элемента для добавления поля к сайту SharePoint. Можно определить тип элемента проекта SharePoint, представляющий поле, а затем постройте шаблона элемента, который другие разработчики могут использовать для добавления элемента поля в проект SharePoint. Кроме того, можно создать шаблон проекта, чтобы разработчики могли создавать новый проект SharePoint, содержащий элемент поля. В обоих случаях можно также предоставить мастер, который появляется, когда разработчики с помощью этого шаблона. Этот мастер может запрашивать сведения у разработчиков для настройки нового элемента или проекта.  
  
 Шаблоны элементов и проектов представляют собой ZIP-файлы, содержащие файлы, используемые в Visual Studio для создания проекта или элемента проекта. Дополнительные сведения об основах шаблонов элементов и проектов см. в разделе [Создание проекта и шаблонов элементов](/visualstudio/ide/creating-project-and-item-templates).  
  
##  <a name="creatingitemtemplates"></a>Создание шаблонов элементов  
 При создании шаблона элемента для элемента проекта SharePoint, существуют некоторые файлы, которые обязательно нужны и дополнительные файлы, которые могут использоваться определенные типы элементов проекта. Пошаговое руководство демонстрирует, как определить тип элемента проекта SharePoint и создание шаблона элемента для него см. в разделе [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 В следующей таблице перечислены файлы, необходимые для создания шаблона элемента для элемента проекта SharePoint.  
  
|Обязательный файл|Описание:|  
|-------------------|-----------------|  
|SPDATA-файл|Это XML-файл, который указывает содержимое и поведение по умолчанию элемента проекта. Этот файл должен содержаться в шаблоне элемента. Дополнительные сведения о содержимом SPDATA-файлов см. в разделе [Справочник по схеме элементов проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|VSTEMPLATE-файл.|Этот файл предоставляет сведения, необходимые для отображения шаблона в Visual Studio **Добавление нового элемента** диалоговое окно и создать элемент проекта из шаблона. Этот файл должен содержаться в шаблоне элемента. Дополнительные сведения см. в разделе [файлы метаданных шаблонов Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Сборка расширения Visual Studio, который реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейса.|Эта сборка определяет поведение во время выполнения элемента проекта. Эта сборка должна включаться в пакет VSIX с шаблоном элемента. Дополнительные сведения см. в разделе [определение типов элементов проектов настраиваемый SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) и [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 В следующей таблице перечислены некоторые из наиболее типичных необязательных файлов, которые могут быть включены в шаблон элемента. Некоторые типы элементов проекта могут требоваться другие файлы, не перечисленные здесь.  
  
|Необязательный файл|Описание:|  
|-------------------|-----------------|  
|Файл Elements.XML|Объект *компонент элемент* файла. Этот файл определяет пользовательский Интерфейс и поведение настройки, созданной элементом проекта. Каждый тип настройки, такие как экземпляры списков, типы содержимого или настраиваемые действия имеет другую схему, определяющую содержимое этого файла. Дополнительные сведения см. в разделе [стандартный блок: функции](http://go.microsoft.com/fwlink/?LinkId=169183) и [схемы компонентов](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|Schema.XML|Файл схемы для определения списков. Дополнительные сведения см. в разделе [стандартный блок: списки и библиотеки документов](http://go.microsoft.com/fwlink/?LinkId=177792) и [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|.WebPart|Объект *определение веб-части* файла. Этот файл содержит параметры свойств для веб-части. Дополнительные сведения см. в разделе [стандартный блок: веб-части](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|.ascx|Файл пользовательского элемента управления ASP.NET. Этот файл определяет пользовательский Интерфейс визуальной веб-части.|  
|.aspx|Файл страницы ASP.NET. Этот файл содержит XML-разметку, которая определяет страницу приложения.|  
|файлы с расширением CS или VB.|Эти файлы кода определяют поведение настроек SharePoint, содержащих модель программирования, доступную на Visual C# или Visual Basic, например страниц приложений, веб-части и рабочие процессы.|  
  
## <a name="creating-project-templates"></a>Создание шаблонов проектов  
 При создании шаблона проекта SharePoint, существуют некоторые файлы, которые всегда имеют обязательные и необязательные файлы, которые могут использоваться определенные типы проектов. Как правило проектов SharePoint включает по крайней мере один элемент проекта SharePoint. Однако это не является обязательным. Например можно определить шаблон проекта SharePoint, который предназначен для использования только для развертывания решений SharePoint, созданных в других проектах.  
  
 Пошаговое руководство демонстрирует, как определить тип элемента проекта SharePoint и создать шаблон проекта для него см. в разделе [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 В следующей таблице перечислены файлы, которые должны быть включены в шаблон проекта SharePoint.  
  
|Обязательный файл|Описание:|  
|-------------------|-----------------|  
|VSTEMPLATE-файл|Этот файл предоставляет сведения, необходимые для отображения шаблона в Visual Studio **новый проект** диалоговое окно и для создания проекта из шаблона. Дополнительные сведения см. в разделе [файлы метаданных шаблонов Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Csproj или VBPROJ-файл|Это файл проекта. Он определяет содержимое и параметры конфигурации проекта.|  
|Package.Package|Этот файл определяет пакет развертывания для проекта. При использовании конструктора пакетов для настройки пакета решения для проекта Visual Studio сохраняет данные о пакете решения в этом файле.<br /><br /> При создании пользовательского шаблона проекта SharePoint, рекомендуется включать минимальное количество необходимого содержимого в файл Package.package, а также настраивать пакет решения с помощью интерфейсов API в <xref:Microsoft.VisualStudio.SharePoint.Packages> пространства имен в расширении, связанные с использованием шаблона проекта. После этого шаблон проекта защищена от возможных изменений в структуру файла Package.package. Пример, демонстрирующий создание файла Package.package с минимально необходимым содержимым см. в разделе [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Если требуется напрямую изменить файл Package.package, вы можете проверить содержимое с помощью схемы в папке % Program Files (x86)%\Microsoft 11.0\Xml\Schemas\PackageModelSchema.xsd Visual Studio.|  
|Package.Template.xml|Этот файл предоставляет основу для файла манифеста решения (manifest.xml) для пакета решения SharePoint (WSP-файл), который создается из проекта. Содержимое можно добавить в этот файл, если вы хотите указать определенное поведение, которое не должно изменяться пользователями типом проекта. Дополнительные сведения см. в разделе [стандартный блок: решений](http://go.microsoft.com/fwlink/?LinkId=169186) и [решения схемы](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> При построении пакета решения из проекта Visual Studio объединяет содержимое пакета и файл манифеста Package.Template.xml файлы в решение. Дополнительные сведения о построении пакетов решений см. в разделе [как: Создание пакета решения SharePoint (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 В следующей таблице перечислены необязательные файлы, которые могут быть включены в шаблон проекта.  
  
|Необязательный файл|Описание:|  
|-------------------|-----------------|  
|элементы проектов SharePoint|Можно включить один или несколько SPDATA-файлы, которые определяют типы элементов проекта SharePoint. Каждого SPDATA-файла должно иметь соответствующее <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> реализации в сборке расширения, включенный в пакет VSIX с помощью шаблона проекта. Дополнительные сведения см. в разделе [Создание шаблонов элементов](#creatingitemtemplates).<br /><br /> Как правило проектов SharePoint включает по крайней мере один элемент проекта SharePoint. Однако это не является обязательным.|  
|*featureName*.feature|Этот файл определяет компонент SharePoint, используемый для группирования нескольких элементов проекта для развертывания. При использовании конструктора возможностей для настройки компонента в проекте Visual Studio сохраняет данные о компоненте в этом файле. Если требуется выполнить группировку элементов проекта в различных компонентах, можно включить несколько Feature-файлов.<br /><br /> При создании пользовательского шаблона проекта SharePoint, рекомендуется включить минимальное необходимое содержимое в Feature-файл, и настраивать компоненты с помощью интерфейсов API в <xref:Microsoft.VisualStudio.SharePoint.Features> пространства имен в расширении, связанные с шаблон проекта. После этого шаблон проекта защищен от будущих изменений в структуру файла компонента. Пример, демонстрирующий создание Feature-файла с минимально необходимым содержимым см. в разделе [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Если требуется напрямую изменить файл с расширением FEATURE, вы можете проверить содержимое с помощью схемы в папке % Program Files (x86)%\Microsoft 11.0\Xml\Schemas\FeatureModelSchema.xsd Visual Studio.|  
|*featureName*. Файл шаблона Template.XML|Этот файл предоставляет основу для файла манифеста компонента (Feature.xml) для каждого компонента, который создается из проекта. Содержимое можно добавить в этот файл, если вы хотите указать определенное поведение, которое не должно изменяться пользователями типом проекта. Дополнительные сведения см. в разделе [стандартный блок: функции](http://go.microsoft.com/fwlink/?LinkId=169183) и [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) файлов.<br /><br /> При построении пакета решения из проекта Visual Studio объединяет содержимое каждой пары *featureName*Feature-файла и *featureName*. Файл шаблона Template.XML файлов в файл манифеста компонента. Дополнительные сведения о построении пакетов решений см. в разделе [как: Создание пакета решения SharePoint (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## <a name="creating-wizards-for-item-templates-and-project-templates"></a>Создание мастеров для шаблонов элементов и проектов  
 После определения типа элемента проекта SharePoint и свяжите его с шаблоном элемента или проекта, можно также создать мастер. Мастер отображает, когда разработчик использует шаблон элемента для добавления элемента проекта SharePoint в проект, или когда разработчик использует шаблон проекта для создания нового проекта, содержащего элемент проекта SharePoint. Мастер можно использовать для сбора информации от разработчиков и для инициализации нового элемента проекта SharePoint.  
  
 Примеры, демонстрирующие создание мастеров для шаблонов элементов и проектов, в разделе [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) и [Пошаговое руководство: Создание сайта Элемент проекта столбца с шаблоном проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>См. также  
 [Определение типов элементов проектов SharePoint, пользовательские](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Создание шаблонов проектов и элементов](/visualstudio/ide/creating-project-and-item-templates)  
  
  