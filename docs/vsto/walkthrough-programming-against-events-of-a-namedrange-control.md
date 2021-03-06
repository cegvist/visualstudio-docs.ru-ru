---
title: "Пошаговое руководство: Программирование реакции на события элементов управления NamedRange | Документы Microsoft"
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
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a06e8aa544cdaff2e75d8af942f8aea68e7bc960
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-programming-against-events-of-a-namedrange-control"></a>Пошаговое руководство. Программирование реакции на события элементов управления NamedRange
  В этом пошаговом руководстве демонстрируется добавление <xref:Microsoft.Office.Tools.Excel.NamedRange> управления на лист Microsoft Office Excel и программированию его событий с помощью средств разработки Office в Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
-   Добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в лист.  
  
-   Программирование <xref:Microsoft.Office.Tools.Excel.NamedRange> контролировать события.  
  
-   Тестирование проекта.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Создание проекта  
 На этом шаге вы создадите проект книги Excel с помощью Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект книги Excel с именем **Мои события именованного диапазона**. Убедитесь, что **создания документа** выбран. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает новую книгу Excel в конструкторе и добавляет **Мои события именованного диапазона** проекта **обозревателе решений**.  
  
## <a name="adding-text-and-named-ranges-to-the-worksheet"></a>Добавление текста и именованных диапазонов в лист  
 Так как элементы управления ведущего приложения являются расширенными объектами Office, их можно добавить в документ так же, необходимо добавить собственный объект. Например, можно добавить Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> управления на лист, открыв **вставить** меню команду **имя**и выбрав **определение**. Можно также добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> управления, перетащив его из **элементов** на лист.  
  
 На этом шаге вы добавите двух элементов управления именованного диапазона на листе с помощью **элементов**, а затем добавьте текст на рабочий лист.  
  
#### <a name="to-add-a-range-to-your-worksheet"></a>Чтобы добавить диапазон в лист  
  
1.  Убедитесь, что **Мои Events.xlsx диапазона с именем** книга открыта в конструкторе Visual Studio с `Sheet1` отображается.  
  
2.  Из **элементов управления Excel** вкладки панели элементов перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> управления ячейку **A1** в `Sheet1`.  
  
     **Добавление элемента управления NamedRange** откроется диалоговое окно.  
  
3.  Убедитесь, что **$A$ 1** отображается в редактируемом текстовом поле и ячейка **A1** выбран. Если это не так, щелкните ячейку **A1** для ее выделения.  
  
4.  Нажмите кнопку **ОК**.  
  
     Ячейка **A1** становится диапазоном `namedRange1`. Никак не видны на листе, но `namedRange1` отображается в **имя** поле (над листом слева) ячеек **A1** выбран.  
  
5.  Добавьте еще один <xref:Microsoft.Office.Tools.Excel.NamedRange> управления ячейку **B3**.  
  
6.  Убедитесь, что **$B$ 3** отображается в редактируемом текстовом поле и ячейка **B3** выбран. Если это не так, щелкните ячейку **B3** для ее выделения.  
  
7.  Нажмите кнопку **ОК**.  
  
     Ячейка **B3** становится диапазоном `namedRange2`.  
  
#### <a name="to-add-text-to-your-worksheet"></a>Добавление текста на лист  
  
1.  В ячейке **A1**, введите следующий текст:  
  
     **Ниже приводится пример элемента управления NamedRange.**  
  
2.  В ячейке **A3** (слева от `namedRange2`), введите следующий текст:  
  
     **События:**  
  
 В следующих разделах будет написан код, который вставляет текст в `namedRange2` и изменяет свойства `namedRange2` управления в ответ на <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, и <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> события `namedRange1`.  
  
## <a name="adding-code-to-respond-to-the-beforedoubleclick-event"></a>Добавление кода для реакции на событие BeforeDoubleClick  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Вставка текста в Именованный_диапазон2 BeforeDoubleClick события  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1.vb** или **Sheet1.cs** и выберите **Просмотр кода**.  
  
2.  Добавьте код, поэтому `namedRange1_BeforeDoubleClick` обработчик события выглядит следующим образом:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  В C# необходимо добавить обработчики событий для именованного диапазона, как показано в <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> ниже события. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="adding-code-to-respond-to-the-change-event"></a>Добавление кода для реагирования на события изменения  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Вставка текста в Именованный_диапазон2 на события изменения  
  
1.  Добавьте код, поэтому `NamedRange1_Change` обработчик события выглядит следующим образом:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Поскольку дважды щелкните ячейку в диапазоне Excel переводит в режим редактирования, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> событие возникает при перемещении выделения за пределами диапазона, даже если никаких изменений в текст.  
  
## <a name="adding-code-to-respond-to-the-selectionchange-event"></a>Добавление кода для реагирования на события SelectionChange  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Вставка текста в Именованный_диапазон2 в зависимости от события SelectionChange  
  
1.  Добавьте код, поэтому **NamedRange1_SelectionChange** обработчик события выглядит следующим образом:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Так как двойной щелчок ячейки в диапазоне Excel приводит к перемещению в диапазон, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> событие возникает перед <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> событием.  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно протестировать книгу, чтобы убедиться, что текст, описывающий события элемента <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления вставляется в другой именованный диапазон при возникновении события.  
  
#### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Поместите курсор в `namedRange1`и убедитесь, что текст в отношении <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> вставить событие и комментария вставляется в лист.  
  
3.  Дважды щелкните внутри `namedRange1`и убедитесь, что текст в отношении <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> событий добавляется с красным курсивом `namedRange2`.  
  
4.  Щелкните за пределами `namedRange1` и обратите внимание, что событие изменения возникает при выходе из режима редактирования, несмотря на то, что было сделано никаких изменений в текст.  
  
5.  Измените текст в `namedRange1`.  
  
6.  Щелкните за пределами `namedRange1`и убедитесь, что текст в отношении <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> событие вставляется голубым цветом в `namedRange2`.  
  
## <a name="next-steps"></a>Следующие шаги  
 В этом пошаговом руководстве описываются основные принципы Программирование реакции на события <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления. Вот задачу, которая может быть следующей:  
  
-   Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>См. также  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Как: изменение размеров элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Как: Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  