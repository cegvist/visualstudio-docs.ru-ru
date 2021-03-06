---
title: "Как: использование точек останова в XSLT | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c86877781b86d34e8e8e68ec71f711b42f7042b7
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Как: использование точек останова в XSLT

Точки останова можно задать в таблице стилей XSLT или в исходном XML-документе. Если задать точку останова на теге, то при выполнении точка останова переходит к следующему оператору, у которого есть сведения исходной строки.

Дополнительные сведения см. в разделе [основы отладки: точки останова](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Установите точку останова в таблице стилей

Точки останова можно задать на открывающих тегах, закрывающих тегах и текстовых узлах таблицы стилей XSLT. Точки останова можно также задать в коде блока скрипта.  
  
### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Задание точки останова в таблице стилей
  
1.  Откройте таблицу стилей в редакторе XML.  
  
2.  Установите курсор в положение точки останова, щелкните правой кнопкой мыши, укажите **останова**и нажмите кнопку **вставить точку останова**.  
  
3.  Нажмите кнопку обзора (**...** ) на **ввода** окна свойств документа.  
  
4.  Выберите исходный XML-документ и нажмите кнопку **откройте**.  
  
     Таким образом задается файл исходного документа, используемого в XSLT-преобразовании.  
  
5.  Нажмите кнопку **Отладка XSL** на панели инструментов редактора XML.  

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Установите точку останова в исходном XML-документа

В исходном XML-документе точки останова можно задать на элементах, атрибутах, узле пространства имен, комментариях, инструкции по обработке и текстовых узлах исходного XML-документа. Невозможно задать точку останова на узле документа или на узле пространства имен, который наследуется от родительского элемента.  

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Задание точки останова в исходном XML-документе 

1.  Откройте XML-документ в XML-редакторе.  
  
2.  Установите курсор в положение точки останова, щелкните правой кнопкой мыши, укажите **останова**и нажмите кнопку **вставить точку останова**.  
  
3.  Нажмите кнопку обзора (**...** ) на **таблицы стилей** окна свойств документа.  
  
4.  Выберите исходный XML-документ и нажмите кнопку **откройте**.  
  
     Таким образом задается файл исходного документа, используемого в XSLT-преобразовании.  
  
5.  Нажмите кнопку **Отладка XSL** на панели инструментов редактора XML.  
 
## <a name="see-also"></a>См. также

[Пошаговое руководство: отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)