---
title: "&lt;friendlyName&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 446a64c402ed9eb70b933b8c32f86426277564c5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `friendlyName` пространства имен `vstov4` хранит имя, которое отображается в списке установленных программ.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `friendlyName` находится в пространстве имен `vstov4` . Значение отображается в списке программ, установленных на компьютере, и в диалоговом окне "Надстройки COM VSTO" приложений Microsoft Office.  
  
 У элемента `friendlyName` нет атрибутов и дочерних элементов.  
  
## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO  
  
### <a name="description"></a>Описание:  
 В приведенном ниже примере кода показан элемент `friendlyName` в решении на уровне приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>См. также  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  