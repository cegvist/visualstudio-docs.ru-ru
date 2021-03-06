---
title: "Программирование надстроек VSTO | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 58b6d40e2da962587b44e4b73c8331b3fba5590f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="programming-vsto-add-ins"></a>Приступая к программированию надстроек VSTO
  Если приложение Microsoft Office расширяется путем создания надстройки VSTO, код создается непосредственно для класса `ThisAddIn` соответствующего проекта. Этот класс можно использовать для выполнения таких задач, как получение доступа к объектной модели ведущего приложения Microsoft Office, настройка пользовательского интерфейса приложения, а также предоставление объектов созданной надстройки VSTO другим решениям Office.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Создание кода для надстроек VSTO несколько отличается от работы над другими типами проектов в Visual Studio. Многие отличия связаны с тем, каким образом объектные модели Office предоставляются управляемому коду. Для получения дополнительной информации см. [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
 Общие сведения о надстройках VSTO и других типах решений, можно создать с помощью средств разработки Office в Visual Studio см. в разделе [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-thisaddin-class"></a>Использование класса ThisAddIn  
 Создание кода надстройки VSTO начинается в классе `ThisAddIn` . Visual Studio автоматически создает этот класс в файле кода ThisAddIn.vb (для [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) или в файле ThisAddIn.cs (для C#) проекта надстройки VSTO. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически создает экземпляр этого класса при загрузке надстройки VSTO приложением Microsoft Office.  
  
 В классе `ThisAddIn` существует два обработчика событий по умолчанию. Для выполнения кода при загрузке надстройки VSTO следует добавить код в обработчик событий `ThisAddIn_Startup` . Для выполнения кода непосредственно перед выгрузкой надстройки VSTO следует добавить код в обработчик событий `ThisAddIn_Shutdown` . Дополнительные сведения о создании этих обработчиков событий см. в разделе [события в проектах Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  В Outlook обработчик событий `ThisAddIn_Shutdown` не вызывается при каждой выгрузке надстройки VSTO по умолчанию. Дополнительные сведения см. в разделе [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
### <a name="accessing-the-object-model-of-the-host-application"></a>Доступ к объектной модели ведущего приложения  
 Доступ к объектной модели ведущего приложения можно получить с помощью поля `Application` класса `ThisAddIn` . Это поле возвращает объект, представляющий текущий экземпляр ведущего приложения. В приведенной ниже таблице представлены типы возвращаемых значений для поля `Application` в каждом проекте надстройки VSTO.  
  
|Ведущее приложение|Тип возвращаемого значения|  
|----------------------|-----------------------|  
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 В приведенном ниже примере кода показано, как с помощью поля `Application` создать книгу в надстройке VSTO для Microsoft Office Excel. Код в примере должен выполняться из класса `ThisAddIn` .  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Чтобы выполнить это же действие без использования класса `ThisAddIn` , используйте для получения доступа к классу `Globals` объект `ThisAddIn` . Дополнительные сведения о `Globals` см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Дополнительные сведения об объектных моделях конкретных приложений Microsoft Office см. в следующих статьях:  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [Решения InfoPath](../vsto/infopath-solutions.md)  
  
-   [Решения PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Решения проектов](../vsto/project-solutions.md)  
  
-   [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> Обращение к документу при запуске приложения Office  
 Многие приложения [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] и ни одно приложение [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] не открывают какой-либо документ при своем запуске автоматически. Таким образом, не добавляйте код в `ThisAdd-In_Startup` обработчик событий, если для кода требуется Открытие документа. Добавьте код в событие, которое создает приложение Office, когда пользователь создает или открывает документ. В этом случае документ точно будет открыт, прежде чем созданный вами код проведет с ним какие-то операции.  
  
 В приведенном ниже примере код работает с документом Word только в том случае, если пользователь создает новый или открывает существующий документ.  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>Члены класса ThisAddIn, используемые в других задачах  
 В приведенной ниже таблице описаны наиболее распространенные задачи и члены класса `ThisAddIn` , которые можно использовать для выполнения этих задач.  
  
|Задача|Используемый член|  
|----------|-------------------|  
|Выполнение кода для инициализации надстройки VSTO при ее загрузке.|Добавьте код в метод `ThisAddIn_Startup` . Этот метод является обработчиком событий по умолчанию для события <xref:Microsoft.Office.Tools.AddInBase.Startup> . Дополнительные сведения см. в разделе [Events in Office Projects](../vsto/events-in-office-projects.md).|  
|Выполнение кода для очистки используемых надстройкой VSTO ресурсов перед выгрузкой надстройки VSTO.|Добавьте код в метод `ThisAddIn_Shutdown` . Этот метод является обработчиком событий по умолчанию для события <xref:Microsoft.Office.Tools.AddInBase.Shutdown> . Дополнительные сведения см. в разделе [Events in Office Projects](../vsto/events-in-office-projects.md). **Примечание:** в Outlook, по умолчанию `ThisAddIn_Startup` обработчик событий не вызывается при выгрузке надстройки VSTO. Дополнительные сведения см. в разделе [Events in Office Projects](../vsto/events-in-office-projects.md).|  
|Отображение настраиваемой области задач.|Используйте поле `CustomTaskPanes` . Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md).|  
|Предоставление доступа к объектам в надстройке VSTO другим решениям Microsoft Office.|Переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Для получения дополнительной информации см. [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|  
|Настройка функции в системе Microsoft Office путем реализации интерфейса расширяемости.|Переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для возврата экземпляра класса, который реализует интерфейс. Дополнительные сведения см. в разделе [Customizing UI Features By Using Extensibility Interfaces](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Примечание:** для настройки пользовательского интерфейса ленты можно также переопределить <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> метод.|  
  
### <a name="understanding-the-design-of-the-thisaddin-class"></a>Общие сведения о разработке класса ThisAddIn  
 В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], интерфейсом является <xref:Microsoft.Office.Tools.AddIn> . Класс `ThisAddIn` является производным от класса <xref:Microsoft.Office.Tools.AddInBase> . Этот базовый класс перенаправляет все вызовы к членам внутренней реализации интерфейса <xref:Microsoft.Office.Tools.AddIn> в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 В проектах надстройки VSTO для Outlook `ThisAddIn` класс является производным от класса Microsoft.Office.Tools.Outlook.OutlookAddIn в проектах, ориентированных на .NET Framework 3.5, а также из <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> в проектах, ориентированных на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Эти базовые классы предоставляют дополнительные функции для поддержки областей форм. Дополнительные сведения об областях форм см. в разделе [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>Настройка пользовательского интерфейса приложений Microsoft Office  
 Используя надстройку VSTO, можно настроить пользовательский интерфейс для приложений Microsoft Office программными средствами. Например, можно настроить ленту таким образом, чтобы в ней отображалась настраиваемая панель задач, или создать настраиваемую область формы в Outlook. Дополнительные сведения см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
 Visual Studio предоставляет конструкторы и классы, которые можно использовать для создания настраиваемых областей задач, настроек ленты и областей формы Outlook. Такие конструкторы и классы упрощают процесс настройки этих функций. Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md), [конструктор лент](../vsto/ribbon-designer.md), и [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md).  
  
 Если какую-то из этих функций необходимо настроить способом, который не поддерживается классами и конструкторами, можно реализовать эти функции в надстройке VSTO *интерфейса расширяемости* . Дополнительные сведения см. в разделе [Customizing UI Features By Using Extensibility Interfaces](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
 Кроме того, можно изменить пользовательский интерфейс документов Word и книг Excel, создавая ведущие элементы, которые расширяют поведение документов и книг. Это позволяет добавлять управляемые элементы управления в документы и листы. Для получения дополнительной информации см. [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="calling-code-in-vsto-add-ins-from-other-solutions"></a>Вызов кода в надстройках VSTO из других решений  
 Доступ к объектам в надстройке VSTO можно предоставлять другим решениям, включая решения Office. Это полезно, если надстройка VSTO предоставляет службу, доступ к которой нужно предоставить другим решениям. Например, при наличии надстройки для Microsoft Office Excel, которая выполняет вычисление финансовых данных, получаемых от веб-службы, другие решения могут выполнять эти вычисления, вызывая надстройку VSTO для Excel во время выполнения.  
  
 Для получения дополнительной информации см. [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
## <a name="see-also"></a>См. также  
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Пошаговое руководство: Вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  