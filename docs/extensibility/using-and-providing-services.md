---
title: "Использование и предоставляет службы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fbba5070af77e1509ed3b3840a2045ae0f2c12b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-and-providing-services"></a>Использование и предоставления услуг
Служба представляет собой контракт между двумя пакеты VSPackage. Один пакет VSPackage предоставляет определенный набор интерфейсов для другого пакета VSPackage для использования. Например [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предлагает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службы к любой VSPackage его загрузки. Эта служба предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который может использоваться для записи в журнал действий. Дополнительные сведения см. в разделе [как: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
 Пакеты VSPackage могут предложить службы с помощью среды <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейс...  
  
 Visual Studio предлагает важные услуги, например следующие:  
  
|Служба интегрированной среды разработки|Описание:|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Предоставляет доступ к интегрированной среде разработки служб работы с базовую функциональность, пакеты VSPackage и реестра.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет основные управления окнами и связанные с Пользовательским интерфейсом функциональных возможностей в Интегрированной среде разработки, такие как возможность создавать средства и окна документов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Обеспечивает базовые функции, связанные с решением, такие как возможность перечислить проекты, создание новых проектов и отслеживать изменения в проект.|  
  
## <a name="in-this-section"></a>В этом разделе  
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)  
 Представляет элементы важные обновления для Visual Studio.  
  
 [Практическое руководство. Получение службы](../extensibility/how-to-get-a-service.md)  
 Описывает способ запроса (использовать) службы.  
  
 [Практическое руководство. Предоставление службы](../extensibility/how-to-provide-a-service.md)  
 Описывает, как для предоставления службы.  
  
 [Практическое руководство. Предоставление асинхронной службы Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Обсуждается асинхронный обслуживает.  
  
 [Практическое руководство. Устранение неполадок, связанных со службами](../extensibility/how-to-troubleshoot-services.md)  
 Описание общих проблем и представляет их решения.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md)