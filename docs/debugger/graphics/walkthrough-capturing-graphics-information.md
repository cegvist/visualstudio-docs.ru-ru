---
title: "Пошаговое руководство: Запись графических сведений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11213c60eb03626f86b51f896b6edb487c3e3394
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-capturing-graphics-information"></a>Пошаговое руководство. Запись графических сведений
В этом пошаговом руководстве показано, как с помощью диагностики графики [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] вручную захватывать графические данные из приложения Direct3D.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Перенаправление диагностики графики в приложение  
  
-   Захват графической информации  
  
## <a name="capturing-graphics-information"></a>Захват графической информации  
 Чтобы использовать средства диагностики графики, сначала нужно захватить графические данные для него. Чтобы включить захват, используйте команду **Начать диагностику** для перенаправления диагностики графики в приложение при его запуске.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Включение захвата графических данных после загрузки проекта или решения  
  
1.  В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]загрузите файл проекта или решения файла для приложения, из которого нужно захватывать графические данные.  
  
2.  На панели инструментов "Диагностика графики" нажмите кнопку **Начать диагностику**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Включение захвата графических данных без загрузки проекта или решения  
  
1.  В строке меню выберите **Файл**, **Открыть**, **Проект/Решение**. Откроется диалоговое окно **Открыть проект** .  
  
2.  Вместо файла проекта или решения укажите исполняемый файл для приложения, из которого требуется захватывать графические данные, а затем нажмите кнопку **Открыть**.  
  
3.  В строке меню выберите **Отладка**, **Графика**, **Начать диагностику**.  
  
 После запуска приложения – когда оно начало отрисовывать кадры — можно захватывать данные графики.  
  
#### <a name="to-capture-graphics-information"></a>Захват графических данных  
  
-   На панели инструментов "Диагностика графики" нажмите кнопку **Захват** . ![Значок кнопки захвата графики](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     -или-  
  
     Поместив фокус на приложение, нажмите клавишу **PRINT SCREEN**.  
  
 Каждый раз при захвате данных о кадре диагностика графики записывает события Direct3D и связанное состояние и добавляет эти данные в журнал графики. Новый журнал графики создается для каждого сеанса диагностики графики. Сведения о журналах графики см. в разделе [Обзор](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Дальнейшие действия  
 В этом пошаговом руководстве было продемонстрировано, как захватывать графические данные вручную. Далее можно перейти к рассмотрению следующего этапа.  
  
-   Узнайте, как анализировать захваченные графические данные с помощью средств диагностики графики. В разделе [Обзор](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>См. также  
 [Capturing Graphics Information](capturing-graphics-information.md)