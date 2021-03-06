---
title: "Просматривать библиотеки DLL и исполняемых файлов в отладчике | Документы Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: "36"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 772c252265e15c3c928fbcc47c756ceafd9e1362
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Просмотр библиотеки DLL и исполняемых файлов, с помощью окна "Модули" в отладчике Visual Studio
 
**Модули** окне выводится список библиотек DLL и исполняемых файлов (EXE), используемых программой и отображаются соответствующие данные для каждого. 

> [!NOTE]
>  Эта возможность недоступна при отладке SQL и скриптов. 
  
### <a name="to-display-the-modules-window"></a>Для отображения окна "Модули"  
  
-   В процессе отладки, выберите **Отладка > Windows** и нажмите кнопку **модулей**.  
  
     По умолчанию **модули** окна модули упорядочены в порядке загрузки. При этом можно выбрать сортировку по любому столбцу.  
  
### <a name="to-sort-by-any-column"></a>Выбор сортировки по произвольному столбцу  
  
-   Нажмите кнопку вверху столбца.  
  
     Можно загрузить символы или указать путь к символам из **модули** окна с помощью контекстного меню.  
  
## <a name="loading-symbols"></a>Загрузка символов  
 В **модули** окна, можно видеть, каких модулей загружены символы отладки. Эта информация появляется в **состояние символов** столбца. Если указано состояние **loadingCannot пропускаются найти или открыть файл PDB**, или **загрузка отключена параметром включения/исключения**, можно настроить отладчик на загрузку символов с открытых символов Майкрософт серверы или загрузить символы из каталога символов на компьютере. Дополнительные сведения см. в разделе [укажите символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Загрузка символов вручную  
  
1.  В **модули** окно, щелкните правой кнопкой мыши какой-либо модуль, для которого не загружены символы.  
  
2.  Пункты **загрузить символы из** и нажмите кнопку **серверы символов Microsoft** или **путь к символам**.  
  
#### <a name="to-change-symbol-load-settings"></a>Изменение параметров загрузки символов  
  
1.  В **модули** окно, щелкните правой кнопкой мыши любой модуль.  
  
2.  Нажмите кнопку **символов параметры**.  
  
     Теперь можно изменить параметры загрузки символов, как описано в [укажите расположения символов и поведения при загрузке](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Изменения вступают в силу только после перезапуска сеанса отладки.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Изменение поведения загрузки символов для конкретного модуля  
  
1.  В **модули** окно, щелкните правой кнопкой мыши модуль.  
  
2.  Пункты **параметры автоматической загрузки символов** и нажмите кнопку **всегда загружать вручную** или **по умолчанию**. Изменения вступают в силу только после перезапуска сеанса отладки.  
  
## <a name="see-also"></a>См. также  
 [Прерывание выполнения](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Укажите символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)