---
title: "Практическое руководство. Сопоставление схем и документов Word в Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "сопоставления [разработка решений Office в Visual Studio], схемы XML (документы Word)"
  - "Word [разработка решений Office в Visual Studio], сопоставление схем XML"
  - "схемы XML [разработка решений Office в Visual Studio], сопоставление"
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Практическое руководство. Сопоставление схем и документов Word в Visual Studio
  **Важным** набор сведений в этом разделе, касающиеся Microsoft Word исключительно для использования преимущества и цене и организаций, найдены вне Соединенные Штаты и его территорий или используют или разработки программ, запущенных на продуктов Microsoft Word, которые были лицензированы Майкрософт до января 2010, когда выполненного реализация конкретной функциональности Майкрософт, связанное с пользовательским XML в Microsoft Word.  Данная информация, относящаяся к Microsoft Word, не предназначена для чтения и использования лицами или организациями, расположенными в США или их территориях, которые используют продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г., или разрабатывают программы для этих продуктов; поведение данных продуктов отличается от поведения продуктов, лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Схему XML можно сопоставить с документом, когда документ открыт в Visual Studio.  Здесь используются те же инструменты Microsoft Office Excel, что и при открытии документа за пределами Visual Studio.  Проект Office создает те же объекты вне зависимости от того, происходит ли сопоставление с документом до или после создания решения Word.  
  
### Сопоставление схемы XML и документа Word в Visual Studio  
  
1.  Откройте документ Word или шаблон проекта в Visual Studio.  
  
2.  Откройте документ для перемещения фокуса в конструктор.  
  
3.  В ленте щелкните вкладку **Разработчик**.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается в ленте, то ее следует сначала отобразить.  Дополнительные сведения см. в разделе [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  В группе **XML** нажмите кнопку **Схема**.  
  
     Появится диалоговое окно **Шаблоны и надстройки**.  
  
5.  Перейдите на вкладку **Схема XML**.  
  
6.  Откройте вкладку **Добавить схему**.  
  
     Появится диалоговое окно **Добавить схему**.  
  
7.  Найдите файл схемы, выберите его и нажмите **Открыть**.  
  
     Откроется диалоговое окно **Настройки схемы**.  
  
8.  Укажите псевдоним или нажмите кнопку **OK**, чтобы добавить схему без назначения псевдонима.  
  
9. Нажмите кнопку **ОК**.  
  
     Откроется окно **Структура XML**.  
  
10. Перетащите элементы из окна **Структура XML** в те части документа, где необходимо создать соответствующие элементы управления.  
  
## См. также  
 [Практическое руководство. Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [XML-схемы и данные в настройках на уровне документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  