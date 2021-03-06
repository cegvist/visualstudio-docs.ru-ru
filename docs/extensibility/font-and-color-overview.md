---
title: "Шрифт и цвет Обзор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09597130864ae0c1e79ef7470c58b25dde8a9263
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="font-and-color-overview"></a>Обзор цвет и шрифт
В этом разделе обсуждаются параметры шрифта и цвета текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Он также понятия, категории и отображаемые элементы и описываются как пакеты VSPackage и базового редактора использовать атрибуты текста.  
  
## <a name="the-fonts-and-colors-property-page"></a>Шрифты и цвета Свойства страницы  
 Вы можете управлять атрибуты текста, отображаемого в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) через **шрифты и цвета** страницу свойств. Чтобы найти **шрифты и цвета** свойства страницы на **средства** меню, нажмите кнопку **параметры**. Разверните **среды**, а затем нажмите кнопку **шрифты и цвета**.  
  
## <a name="categories-and-display-items"></a>Категории и отображаемые элементы  
 Шрифты и цвета организованы в **категории** и **отображаемые элементы**.  
  
-   Объект **категории** является контейнером для нескольких логические или функциональные **отображаемые элементы**.  
  
     Список **категории** в **Показать параметры для** поле со списком из **шрифты и цвета** страницу свойств.  
  
-   Объект **отображаемым элементом** — это сущность четко определенный текст, например комментарий, строка или структуре элемента управления, который должен быть цветом при отображении.  
  
 Каждый **отображаемым элементом** однозначно определены в **категории** , которая его содержит. Следовательно, несколько **категории** может иметь **отображаемым элементом** с тем же именем.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Управление VSPackage шрифты и цвета  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Позволяет пакетам VSPackage:  
  
-   Определить шрифт и цвет **категории**.  
  
-   Задание шрифтов и цветов, используемых для представления **отображаемые элементы**.  
  
-   Взаимодействовать с **шрифты и цвета** страницу свойств.  
  
-   Несколько статистических **категории** по группам.  
  
-   Сохранение изменений в параметрах по умолчанию.  
  
 Существует два способа взаимодействия с Выбор шрифта и цвета в пределах [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Одним из способов называется *цветовой подсветки синтаксиса*. Он используется пакетом VSPackage, который настраивает существующую [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактор для реализации языковой службы и создать источник редактора.  
  
     Только один **категории** поддерживает этот механизм, а именно, **текстовый редактор**.  
  
-   Более общие альтернативой поддерживает все остальные **категории** и компоненты пользовательского интерфейса, отличное от этого редактора источника при отображении текста. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Параметры текстового редактора Core  
 Управляемые параметры шрифта и цвета для базового редактора объекта службы языка **EditorCategory текст** в **Показать параметры для** поле со списком из **шрифты и цвета** страницу свойств.  
  
 При работе с редакторами, следует использовать специализированные шрифт и цвет элемента управления механизм, который предоставляет службы языка для управления и расширения **текстовый редактор** параметры. Механизм называется *Цветовая подсветка синтаксиса* и предоставляет:  
  
-   Упрощенный способ управления шрифты и цвета, отображаемые элементы.  
  
     Дополнительные сведения см. в разделах <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Механизм Раскраска четко определенных и оптимизирован.  
  
     Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   Возможности, как использовать встроенные отображаемые элементы из **EditorCategory текст** и расширять их.  
  
     Дополнительные сведения см. в разделе [как: Используйте встроенные цветные элементы](../extensibility/internals/how-to-use-built-in-colorable-items.md) и [цветные элементы пользовательских](../extensibility/internals/custom-colorable-items.md).  
  
-   Автоматическое сохранение текущего состояния обоих встроенных и пользовательских отображение элементов с **текстовый редактор** категории.  
  
 Дополнительные сведения о см. в разделе Цветовая подсветка синтаксиса [цветовую подсветку синтаксиса в языковую службу прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>См. также  
 [Устаревшие интерфейсы в редакторе](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)