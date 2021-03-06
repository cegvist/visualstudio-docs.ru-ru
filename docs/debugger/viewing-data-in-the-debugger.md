---
title: "Создание настраиваемых представлений данных в отладчике | Документы Microsoft"
ms.custom: 
ms.date: 06/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e8f008ba3cde911ed5c21f281d30fda2a77bf824
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Создание настраиваемых представлений данных в отладчике Visual Studio
В отладчике [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предусмотрены разнообразные средства для проверки и изменения состояния программы. Большинство этих средств функционируют только в режиме приостановки.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Создание настраиваемых представлений данных в окнах переменных и подсказки данных
 Многие [окна отладчика](../debugger/debugger-windows.md), такие как **видимые** и **Контрольные значения** windows, позволяют просматривать значения переменных при отладке. Можно настроить внешний вид собственных типов и управляемых объектов в окнах переменных отладчика и [подсказки данных](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Это может быть полезно отображать типы, созданные в пользовательских приложениях. Дополнительные сведения см. в разделе [Создание настраиваемых представлений собственных объектов](../debugger/create-custom-views-of-native-objects.md) и [создавать пользовательские представления управляемых объектов](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Создание пользовательских визуализаторов  
 Визуализаторы позволяют просмотреть содержимое объекта или переменной более удобным образом. В отладчике Visual Studio визуализатор ссылается на различные окна, которые можно открыть с помощью значка лупы ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор"). Например, можно использовать HTML-визуализатор для просмотра HTML-строки в том виде, в каком она была бы показана в браузере. Можно получить доступ к визуализаторам из подсказок, окна **Контрольное значение** , окна **Видимые** , окна **Локальные** или диалогового окна **Быстрая проверка** . Дополнительные сведения см. в разделе [создания пользовательских визуализаторов](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>См. также  
 [Основы отладки](../debugger/debugger-basics.md)   
 [Командное окно](../ide/reference/command-window.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)