---
title: "Упрощенное внедрение | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 183dc4ad9d7ea1a2f6855be050ad8459a3f801ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="simplified-embedding"></a>Упрощенное внедрения
Упрощенная внедрение включена в редакторе, его объекту представления документа имеет родителя (то есть сделаны дочерний) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс реализуется для обработки его окно команд. Упрощенная внедрения редакторы, не могут содержать активные элементы управления. На следующем рисунке показаны объекты, используемые для создания редактора с упрощенной внедрения.  
  
 ![График упрощенного вложенного редактора](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Редактор с упрощенной внедрения  
  
> [!NOTE]
>  Объекты на этом рисунке, только `CYourEditorFactory` объекта, необходимые для создания стандартного редактора файла. При создании пользовательского редактора необходимые для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, так как ваш редактор, скорее всего будет свой собственный закрытый механизм сохраняемости. Для определенных пользователем редакторов тем не менее, это необходимо сделать.  
  
 Все интерфейсы, реализованные создания редактора с упрощенной внедрения находятся в `CYourEditorDocument` объекта. Однако для поддержки нескольких представлений данных документа, разделите интерфейсы на отдельные объекты данных и представления, как указано в следующей таблице.  
  
|Интерфейс|Расположение интерфейса|Использовать|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Просмотр|Обеспечивает подключение родительского окна.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Просмотр|Обработка команд.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Просмотр|Обеспечивает обновление строки состояния.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Просмотр|Включает **элементов** элементов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Данные|Отправлять уведомления при изменении файла.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Данные|Включает функцию Сохранить как для типа файлов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Данные|Обеспечивает сохраняемость документа.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Данные|Позволяет подавления событий изменения файла, например перезагрузить активации.|