---
title: "События в проектах Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 31d7e8483865ed03830376012e780bac87fdda07
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="events-in-office-projects"></a>События в проектах Office
  Каждый шаблон проекта Office автоматически создает несколько обработчиков событий. Обработчики событий для настроек на уровне документа несколько отличаются от обработчиков событий для надстроек VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="document-level-projects"></a>Проекты уровня документа  
 Visual Studio предоставляет сформированный код для новых или существующих документов или листов в настройках на уровне документа. Этот код создает два различных события: **Startup** и **Shutdown**.  
  
### <a name="startup-event"></a>Startup - событие  
 Событие **Startup** возникает для каждого ведущего элемента (документа, книги или листа) после запуска документа и всех кодов инициализации в сборке. Это самая последняя операция, запускаемая в конструкторе класса, в котором выполняется ваш код. Дополнительные сведения о ведущих элементах см. в разделе [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 При создании проекта на уровне документа Visual Studio создает обработчики событий для события **Startup** в созданных файлах кода:  
  
-   Для проектов Microsoft Office Word обработчик событий имеет имя `ThisDocument_Startup`.  
  
-   Для проектов Microsoft Office Excel обработчики событий имеют следующие имена:  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### <a name="shutdown-event"></a>Shutdown - событие  
 Событие **Shutdown** возникает для каждого ведущего элемента (документа или листа), когда домен приложения, в который загружен ваш код, готов к выгрузке. Это самая последняя операция, которая должна быть вызвана в классе при выгрузке.  
  
 При создании проекта на уровне документа Visual Studio создает обработчики событий для события **Shutdown** в созданных файлах кода:  
  
-   Для проектов Microsoft Office Word обработчик событий имеет имя `ThisDocument_Shutdown`.  
  
-   Для проектов Microsoft Office Excel обработчики событий имеют следующие имена:  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  Не удаляйте программным образом элементы управления во время работы обработчика событий **Shutdown** документа. Если возникает событие **Shutdown** , элементы пользовательского интерфейса документа становятся недоступными. Если элементы управления необходимо удалить до закрытия приложения, добавьте свой код в другой обработчик событий, например, **BeforeClose** или **BeforeSave**.  
  
### <a name="event-handler-method-declarations"></a>Объявления метода обработчика событий  
 В каждое объявление метода обработчика событий передаются одни и те же аргументы: *sender* и *e*. В Excel аргумент *sender* ссылается на лист, например, `Sheet1` или `Sheet2`. В Microsoft Word аргумент *sender* ссылается на документ. Аргумент *e* ссылается на стандартные аргументы для события, которые не используются в этом случае.  
  
 В следующем примере кода показаны обработчики событий по умолчанию в проектах на уровне документа для Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]  
  
 В следующем примере кода показаны обработчики событий по умолчанию в проектах на уровне документа для Excel.  
  
> [!NOTE]  
>  В следующем примере кода показаны обработчики событий в классе `Sheet1` . Имена обработчиков событий в других классах ведущих элементов соответствуют имени класса. Например, в классе `Sheet2` обработчик событий **Startup** имеет имя `Sheet2_Startup`. В классе `ThisWorkbook` обработчик событий **Startup** имеет имя `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]  
  
### <a name="order-of-events-in-document-level-excel-projects"></a>Порядок событий в проектах на уровне документа Excel  
 Обработчики **Startup** событий в проектах Excel вызываются в следующем порядке:  
  
1.  `ThisWorkbook_Startup`.  
  
2.  `Sheet1_Startup`.  
  
3.  `Sheet2_Startup`.  
  
4.  `Sheet3_Startup`.  
  
5.  Другие листы по порядку.  
  
 Обработчики событий **Shutdown** в решении книги вызываются в следующем порядке:  
  
1.  `ThisWorkbook_Shutdown`.  
  
2.  `Sheet1_Shutdown`.  
  
3.  `Sheet2_Shutdown`.  
  
4.  `Sheet3_Shutdown`.  
  
5.  Другие листы по порядку.  
  
 Порядок определяется при компиляции проекта. Если пользователь изменяет порядок листов во время выполнения, это не приводит к изменению порядка, в котором появляются события при очередном открытии или закрытии книги.  
  
## <a name="vsto-add-in-projects"></a>Проекты надстроек VSTO  
 Visual Studio предоставляет сформированный код в надстройках VSTO. Этот код создает два различных события: <xref:Microsoft.Office.Tools.AddInBase.Startup> и <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### <a name="startup-event"></a>Startup - событие  
 Событие <xref:Microsoft.Office.Tools.AddIn.Startup> возникает после загрузки надстройки VSTO и запуска всего кода инициализации в сборке. Это событие обрабатывается методом `ThisAddIn_Startup` в файле сформированного кода.  
  
 Код в обработчике событий `ThisAddIn_Startup` — это первый код пользователя, подлежащий выполнению, если надстройка VSTO не переопределяет метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . В этом случае обработчик событий `ThisAddIn_Startup` вызывается после <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 Не добавляйте код в `ThisAdd-In_Startup` обработчик событий, если для кода требуется Открытие документа. Добавьте код в событие, которое создает приложение Office, когда пользователь создает или открывает документ. Для получения дополнительной информации см. [Обращение к документу при запуске приложения Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Дополнительные сведения о последовательности запуска надстроек VSTO см. в разделе [надстроек VSTO архитектура](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="shutdown-event"></a>Shutdown - событие  
 Событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> возникает, когда домен приложения, в котором загружен ваш код, готов к выгрузке. Это событие обрабатывается методом `ThisAddIn_Shutdown` в файле сформированного кода. Этот обработчик событий — последний код пользователя, выполняемый при выгрузке надстройки VSTO.  
  
#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Событие завершения работы в надстройках VSTO для Outlook  
 Событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> возникает только в том случае, когда пользователь отключает надстройку VSTO с помощью диалогового окна надстроек COM в Outlook. Оно не возникает при завершении работы Outlook. Если у вас есть код, который должен выполняться при завершении работы Outlook, обработайте одно из следующих событий:  
  
-   Событие <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> объекта <xref:Microsoft.Office.Interop.Outlook.Application> .  
  
-   Событие <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> объекта <xref:Microsoft.Office.Interop.Outlook.Explorer> .  
  
> [!NOTE]  
>  Чтобы Outlook принудительно создавал событие <xref:Microsoft.Office.Tools.AddInBase.Shutdown> при выходе, можно изменить реестр. Однако, если администратор отменяет эту настройку, любой код, добавленный в метод `ThisAddIn_Shutdown` , больше не будет выполняться при завершении работы Outlook. Дополнительные сведения см. в разделе [Изменения при завершении работы для Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## <a name="see-also"></a>См. также  
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  