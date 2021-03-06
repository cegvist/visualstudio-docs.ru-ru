---
title: "Отладка 64-разрядных приложений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5c3840cc7d43c3e30dda0317674ffb8cd664a262
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debug-64-bit-applications"></a>Отладка 64-разрядных приложений
Существует возможность отладки 64-разрядного приложения, которое выполняется на локальном или удаленном компьютере.  
  
 Сведения об отладке 64-разрядного приложения, которое выполняется на удаленном компьютере, см. в статье [Remote Debugging](../debugger/remote-debugging.md).  
  
 Для отладки 64-разрядных приложений локально в Visual Studio используется 64-разрядная версия рабочего процесса (msvsmon.exe) для выполнения низкоуровневых операций, которые невозможно выполнить в 32-разрядном процессе Visual Studio.  
  
 Отладка в смешанном режиме не поддерживается для 64-разрядных процессов, использующих платформу .NET Framework 3.5 или более раннюю версию.  
  
## <a name="debug-a-64-bit-application"></a>Отладка 64-разрядных приложений  
 Чтобы отладить 64-разрядное приложение, выполните следующее.  
  
1.  Создайте решение Visual Studio, например консольное приложение C#.  
  
2.  С помощью Configuration Manager задайте для конфигурации 64-разрядный режим. Для получения дополнительной информации см. [How to: Configure Projects to Target Platforms](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  На этом этапе запускается 64-разрядная версия удаленного отладчика (msvsmon.exe). Он работает до тех пор, пока открыто решение с 64-разрядной конфигурацией.  
  
4.  Приступите к отладке. Результат должен быть таким же, как и в случае с 32-разрядной конфигурацией. Если возникли ошибки, обратитесь к разделу "Устранение проблем", расположенному ниже.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Устранение проблем при 64-разрядной отладке  
 Появится сообщение об ошибке: «64-разрядная операция отладки занимает больше времени, чем ожидалось.» В этом случае из Visual Studio отправлен запрос к 64-разрядной версии msvsmon.exe, и потребовалось много времени на возвращение результата этого запроса.  
  
 Есть две основных причины этой ошибки.  
  
-   На компьютере установлено программное обеспечение для защиты сети, из-за чего сетевой стек стал ненадежным и стал терять пакеты, идущие через localhost. Попробуйте отключить все программное обеспечение для защиты сети. Если проблема устранена, сообщите поставщику программного обеспечения для защиты сети о том, что его программа мешает трафику localhost.  
  
-   Программа не отвечает на запросы, или возникла проблема с производительностью Visual Studio. Если проблема возникает регулярно, можно собрать дампы Visual Studio (devenv.exe) и рабочего процесса (msvsmon.exe) и отправить их в корпорацию Майкрософт. Сведения о том, как сообщить о проблеме, см. в статье [How to Report a Problem with Visual Studio](../ide/How-to-Report-a-Problem-with-Visual-Studio-2017.md).
  
## <a name="see-also"></a>См. также  
 [64-разрядные приложения](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Настройка программ для 64-разрядных систем](/cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Поддержка 64-разрядных интегрированной среды разработки Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Использование файлов дампа](../debugger/using-dump-files.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)