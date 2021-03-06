---
title: "Ловушки выделения и выделения памяти времени выполнения C | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b123e0e03f33f54e6d4fe82313c9a017e3baafff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Ловушки выделения и выделения памяти CRT
Очень важное условие для функций-ловушек выделения — то, что они не должны явно обрабатывать блоки `_CRT_BLOCK` (выделения памяти, сделанные внутри библиотеки CRT ее функциями) при любом вызове функций CRT, выделяющих внутреннюю память. Блоки `_CRT_BLOCK` можно исключить из обработки путем добавления в начало функции-ловушки выделения следующего кода:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Если ловушка обрабатывает блоки `_CRT_BLOCK`, то любая вызываемая в ней функция CRT может привести к выполнению в программе бесконечного цикла. Например, `printf` осуществляет внутреннее выделение. Если код ловушки вызывает `printf`, то полученный выделение приведет к ловушки вызываться снова, где будет вызван **printf** еще раз, и так далее до переполнения стека. Если нужен отчет об операциях выделения `_CRT_BLOCK`, есть способ обойти это ограничение — для форматирования и вывода использовать функции Windows API вместо функций CRT. Поскольку функции Windows API не используют кучу библиотеки CRT, они не могут привести к выполнению в приложении бесконечного цикла.  
  
 Если посмотреть на исходные файлы библиотеки времени выполнения, вы увидите, что функция-ловушка выделения по умолчанию **CrtDefaultAllocHook** (возвращающая просто значение **TRUE**), находится в отдельном файле свои собственные, DBGHOOK. C. Если необходимо, чтобы ловушка выделения памяти для вызова даже для выделений, сделанных код запуска времени выполнения, который выполняется до установки приложения **основной** функции, можно заменить эту функцию по умолчанию своим собственным вместо с помощью [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
