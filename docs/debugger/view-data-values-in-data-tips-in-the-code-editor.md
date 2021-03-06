---
title: "Просмотреть значения в подсказках в редакторе кода | Документы Microsoft"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 178bd1768474eaaaf760e2ef4feecfe0e1519bee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Просмотр значений данных в подсказках в редакторе кода
Подсказки данных предоставляют удобный способ просмотра сведений о переменных в программе во время отладки. Подсказки данных работают только в режиме прерывания и только с переменными, которые находятся в пределах текущей области выполнения.
  
### <a name="to-display-a-datatip"></a>Чтобы отобразить подсказку данных  
  
1. Установите точку останова и начните отладку (нажмите клавишу **F5**).

2. Где остановлено в отладчике, поместите указатель мыши поверх любой переменной в текущей области.
  
     Появится подсказка.
  
3.  Подсказка данных исчезнет при перемещении указателя мыши. Чтобы прикрепить подсказку данных, чтобы она оставалась открытой, щелкните **закрепить к исходному коду** значок или щелкните правой кнопкой мыши на переменную, нажмите кнопку **закрепить к исходному коду**.

    ![Закрепление подсказке](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > Подсказки данных всегда вычисляются в контексте того места, где приостановлено выполнение, а не в контексте текущего местоположения курсора. Если в другой функции навести указатель на переменную, имеющую такое же имя, что и переменная в текущем контексте, в качестве значения этой другой переменной отобразится значение переменной, относящейся к текущему контексту.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Открепление подсказки данных и размещение поверх всех окон  
  
-   На закрепленной подсказке щелкните **Открепить от исходного кода** значок.  
  
     Значок прикрепления заменяется на незакрепленный. После этого подсказка данных будет располагаться поверх всех остальных окон. Такая подсказка данных будет закрыта при завершении сеанса отладки.  
  
### <a name="to-repin-a-floating-datatip"></a>Чтобы повторно прикрепить подсказку данных, размещенную поверх всех окон  
  
-   Щелкните значок прикрепления на подсказке.  
  
     Значок прикрепления заменяется на закрепленный. Если подсказка находится вне окна исходного кода, то значок будет отключен, а прикрепление подсказки будет невозможным.  
  
### <a name="to-close-a-datatip"></a>Закрытие подсказки данных  
  
-   Наведите указатель мыши на подсказку, а затем нажмите кнопку **закрыть** значок.  
  
### <a name="to-close-all-datatips"></a>Закрытие всех подсказок данных  
  
-   На **отладки** меню, нажмите кнопку **очистить все подсказки данных**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Закрытие всех подсказок данных для определенного файла  
  
-   На **отладки** меню, нажмите кнопку **очистить все подсказки данных, прикрепленные к** *файл*.  
  
## <a name="expand-and-edit-information"></a>Развернуть и изменить сведения  
 Подсказки данных позволяют развернуть массив, структуру или объект для просмотра его элементов. Можно также изменить значение переменной из Подсказки Данных.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Чтобы развернуть переменную для просмотра ее элементов  
  
-   В подсказке по данным, поместите указатель мыши  **+**  входа, которая предшествует имени переменной.  
  
    Переменная развернется, отобразив свои элементы в виде дерева.

    ![Просмотр подсказке](../debugger/media/dbg-tour-data-tips.gif "просмотра подсказки")
  
    При развертывании переменной можно использовать клавиши со стрелками для перемещения вверх и вниз. Кроме того, можно использовать мышь.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Изменение значения переменной с помощью подсказки данных  
  
1.  Щелкните значение в подсказке. Эта возможность отключена для значений, предназначенных только для чтения.  
  
2.  Введите новое значение и нажмите клавишу "Ввод".  
  
## <a name="making-a-datatip-transparent"></a>Задание прозрачности для подсказки данных  
 Чтобы просмотреть код, закрываемый подсказкой данных, подсказку можно временно сделать прозрачной. Это неприменимо к закрепленным или плавающим подсказкам данных.  
  
#### <a name="to-make-a-datatip-transparent"></a>Прозрачная подсказка данных  
  
-   Нажмите клавишу CTRL в подсказке данных.  
  
     Подсказка будет прозрачной пока удерживается клавиша CTRL.  
  
## <a name="visualize-complex-data-types"></a>Визуализация сложных типов данных  
 Если отображается значок лупы рядом с именем переменной в подсказке по данным, один или несколько [визуализаторы](../debugger/create-custom-visualizers-of-data.md), такие как [строка визуализаторы](../debugger/string-visualizer-dialog-box.md), доступны для переменных этого типа данных. Для отображения сведений в более понятном (обычно графическом) режиме можно использовать визуализатор.
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Просмотр содержимого переменной с помощью визуализатора  
  
-   Щелкните значок лупы ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор") чтобы выбрать визуализатор по умолчанию для типа данных.  
  
     - или -  
  
     Щелкните всплывающую стрелку рядом с визуализатором, чтобы выбрать из всплывающего списка визуализатор для конкретного типа данных.  
  
     Появится визуализатор, содержащий информацию.  
  
## <a name="add-information-to-a-watch-window"></a>Добавление данных в окне контрольных значений  
 Если вы хотите продолжать наблюдение за переменной в виде списка, можно добавить переменную **Контрольные значения** окна из подсказки данных.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Чтобы добавить переменную в окно Контрольное значение  
  
-   Щелкните правой кнопкой мыши окно подсказки и нажмите кнопку **Добавить контрольное значение**.  
  
     Переменная добавляется к **Контрольные значения** окна. При использовании выпуска, который поддерживает несколько **Контрольные значения** windows, переменная будет добавлена к **Контрольное значение 1.**  
  
## <a name="import-and-export-datatips"></a>Импорт и Экспорт подсказок данных  
 подсказки данных можно экспортировать в XML-файл, который можно использовать совместно с коллегами или редактировать с помощью текстового редактора.  
  
#### <a name="to-export-datatips"></a>Экспорт подсказок данных  
  
1.  В меню "Отладка" выберите **Экспорт подсказок данных**.  
  
     **Экспорт подсказок данных** откроется диалоговое окно.  
  
2.  С помощью стандартных действий перейдите в папку, в которой вы хотите сохранить XML-файл, введите имя для файла в **имя файла** , а затем щелкните **ОК**.  
  
#### <a name="to-import-datatips"></a>Импорт подсказок данных  
  
1.  В меню "Отладка" выберите **Импорт подсказок данных**.  
  
     **Импорт подсказок данных** откроется диалоговое окно.  
  
2.  Используйте диалоговое окно, найдите XML-файл, который требуется открыть и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Контрольное значение и окна "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)   
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)   