---
title: "Проверьте приложение отладки с ведением журнала | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 315a5c06a1ecda7976f17e20a299daed5dad65bd
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Проверьте приложение с помощью IntelliTrace с ведением журнала отладки в Visual Studio
Можно использовать [отладка с ведением журнала](../debugger/historical-debugging.md) переход назад и вперед по выполнению приложения и проверять его состояние.  
  
IntelliTrace можно использовать в выпуске Visual Studio Enterprise, но не в выпусках Professional или Community.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Перейдите в коде отладки с ведением журнала  
 Давайте начнем с простой программы, содержащей ошибку. В консольном приложении C# добавьте следующий код:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Предположим, что ожидаемое значение `resultInt` после вызова `AddAll()` — 20 (результат увеличения `testInt` 20 раз). (Также предположим, нельзя увидеть ошибки в `AddInt()`). Но результат будет 44. Как можно найти ошибку без обращения к `AddAll()` 10 раз? Отладка с ведением журнала можно использовать для поиска ошибки проще и быстрее. Это делается так.  
  
1.  В **Сервис > Параметры > IntelliTrace > Общие**, убедитесь, что включено средство IntelliTrace и установите **события IntelliTrace и сведений о вызовах**. Если этот параметр не выбран, область навигации отображаться не будет (как описано ниже).  
  
2.  Установите точку останова на строке `Console.WriteLine(resultInt);`.  
  
3.  Приступите к отладке. Код выполняется до точки останова. В **локальные** окна, можно увидеть, что значение `resultInt` 44.  
  
4.  Откройте **средства диагностики** окна (**Отладка > Показать средства диагностики**). Окно кода должно выглядеть следующим образом.  
  
     ![Окно кода в точке останова](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Рядом с левым полем непосредственно над точкой останова отображается двойная стрелка. Эта область называется внутренней области навигации и используется для отладки с ведением журнала. Щелкните стрелку.  
  
     В окне кода предыдущая строка кода (`int resultInt = AddIterative(testInt);`) выделена розовым цветом. Над окном вы увидите сообщение, информирующее о отладки с ведением журнала.  
  
     Теперь окно кода выглядит следующим образом.  
  
     ![окно кода в режиме журнала отладки](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Теперь можно выполнить пошаговую отладку `AddAll()` метод (**F11**, или **шаг с заходом** кнопки в области навигации. Выполните шаг вперед (**F10**, или **перейти к следующему вызову** во внутренней области навигации. Теперь розовая строка находится на строке `j = AddInt(j);`. **F10** в этом случае выполняет переход к следующей строке кода. Вместо этого осуществляется вызов следующей функции. Отладка с ведением журнала переходит от вызова к вызову и пропускает строки кода, которые не включают вызов функции.  
  
7.  Выполните шаг с заходом в метод `AddInt()`. Вы сразу же увидите ошибку в этом коде.  

## <a name="next-steps"></a>Следующие шаги

Эта процедура лишь краткий обзор функций отладки с ведением журнала.

- Просмотр моментальных снимков во время отладки, в разделе [Просмотр моментальных снимков с помощью IntelliTrace шаг обратной](../debugger/how-to-use-intellitrace-step-back.md).
- Дополнительные сведения о различных параметрах и действиях кнопок в области навигации, в разделе [возможности IntelliTrace](../debugger/intellitrace-features.md).