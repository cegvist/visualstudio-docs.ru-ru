---
title: "Элементы модели проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c5f230da41efa8dd2fa522a5f86ae1402991b2cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-a-project-model"></a>Элементы модели проекта
Интерфейсы и реализации всех проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] совместно использовать базовую структуру: модель проекта для данного типа проекта. В модели проекта, являющийся VSPackage, вы разрабатываете, создаются объекты, соответствующие проектные решения и работает совместно с глобальной функции интегрированной среды разработки. Несмотря на то, что вы можете управлять сохраняется как элемент проекта, например, вы не управляете уведомление о том, что файл должен быть сохранен. Когда пользователь помещает фокус на элемент, открытие проекта и выбирает **Сохранить** на **файл** меню [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] меню линейчатые, тип кода проекта необходимо перехватить команды в интегрированной среде разработки, сохранять файл и отправьте уведомление в Интегрированной среде разработки, файл больше не изменяется.  
  
 VSPackage взаимодействует с интегрированной средой разработки через службы, предоставляющие доступ к интерфейсам интегрированной среды разработки. Например посредством определенных служб монитора и маршрута команд и предоставить сведения о контексте для выбора, сделанного в проект. Все глобальные функции интегрированной среды разработки, необходимые для вашего VSPackage, предоставляемый службами. Дополнительные сведения о службах см. в разделе [как: доступ к службе](../../extensibility/how-to-get-a-service.md).  
  
 Другие соображения относительно реализации:  
  
-   Модель отдельный проект может содержать более одного типа проекта.  
  
-   Типы проектов и фабрики помощника проекта зарегистрированы независимо друг от друга с идентификаторами GUID.  
  
-   Каждый проект должен иметь файл шаблона или мастера, чтобы инициализировать новый файл проекта, когда пользователь создает новый проект через [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса. Например [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] шаблоны инициализации, что со временем стать vсproj-файлы.  
  
 Интерфейсы, службы и объекты, составляющие реализации типичного проекта на следующем рисунке. Вспомогательный объект приложения HierUtil7, можно использовать для создания базовых объектов и других программирования стандартный. Дополнительные сведения о вспомогательных приложений HierUtil7 см. в разделе [не в сборке: с помощью HierUtil7 проекта классов для реализации типа проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![График Visual Studio проект модели](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
модель проекта  
  
 Дополнительные сведения об интерфейсах и служб, перечисленных в предыдущей диаграмме и другие необязательные интерфейсы, не включенных в диаграмму, см. в разделе [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md).  
  
 Проекты может поддерживать команд и поэтому должны реализовывать интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для участия в маршрутизации команд через контекст команды GUID.  
  
## <a name="see-also"></a>См. также  
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Не в сборке: использование HierUtil7 проекта классов для реализации тип проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)   
 [Создание экземпляров проекта с помощью фабрик проекта](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Как: доступ к службе](../../extensibility/how-to-get-a-service.md)   
 [Создание типов проектов](../../extensibility/internals/creating-project-types.md)