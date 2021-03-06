---
title: "Практическое руководство. Исключение и включение малых функций при инструментировании | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1238e092bf1b088ba9ce377aeaf66b1fa953f1bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Практическое руководство. Исключение и включение малых функций при инструментировании
По умолчанию средства профилирования исключают *малозначимые функции* из инструментирования. Малозначимыми функциями называют малые функции, которые не выполняют вызовы других функций. Исключение таких малозначимых функций позволяет сократить временные затраты инструментирования и повысить скорость профилирования. При исключении малозначимых функций также уменьшается размер файла данных профилирования производительности (VSP) и время, необходимое для анализа. Если малозначимые функции исключаются, время, затрачиваемое на такие функции, учитывается в эксклюзивном и инклюзивном времени их родительских функций. Малые функции можно исключить или включить при инструментировании, как описано в следующей процедуре.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Исключение и включение малых функций при инструментировании  
  
1.  В **обозревателе производительности** выберите **Сеанс производительности**, а затем щелкните его правой кнопкой мыши и выберите **Свойства**.  
  
     Откроется диалоговое окно **Страницы свойств**.  
  
2.  В окне **Страницы свойств** щелкните свойства **Инструментирование**.  
  
3.  Чтобы исключить малые функции из инструментирования, выберите **Исключить малые функции из инструментирования**. Этот параметр используется по умолчанию.  
  
     - или -  
  
     Чтобы включить малые функции в инструментирование, выберите **Включить малые функции в инструментирование**.  
  
4.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Управление сбором данных](../profiling/controlling-data-collection.md)   
 [Свойства сеанса анализа производительности](../profiling/performance-session-properties.md)