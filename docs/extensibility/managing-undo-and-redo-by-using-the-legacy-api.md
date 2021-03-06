---
title: "Управление отмены и возврата с помощью прежних версий API | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c50316b7d5786b1fb3f07255eaf4d875f7f41e5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Управление отмены и повтора, с помощью API прежних версий
Редакторы должен поддерживать операции отмены, позволяющих пользователям отменить их последние изменения, если они изменяют код. Большинство редакторов, реализованных в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] может иметь отмены, предоставляемый автоматически интегрированной среды разработки (IDE).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Как: реализации управления отмены](../extensibility/how-to-implement-undo-management.md)  
 Предоставляет возможность отмены изменений для редакторов с одним или несколькими представлениями.  
  
 [Как: очистить стек отмены](../extensibility/how-to-clear-the-undo-stack.md)  
 Описывает, как очистить стек отмены.  
  
 [Как: использовать связанный откат управления](../extensibility/how-to-use-linked-undo-management.md)  
 Включает управление связанный откат в редактор.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Обеспечивает управление отмены для редактора, который поддерживает несколько представлений.  
  
## <a name="related-sections"></a>Связанные разделы