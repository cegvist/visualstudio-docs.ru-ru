---
title: "Как: Создание пользовательской функции правил проверки и пакетов для решений SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: efc9cc2988125621212698576deeca1247e26a58
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Практическое руководство. Создание пользовательских правил проверки компонентов и пакетов для решений SharePoint
  Можно создать пользовательские правила проверки для проверки пакета решения, созданные Visual Studio. Полную проверку можно выполнить весь компонент или пакета, выбрав **проверки** в контекстном меню пакета или компонента в **PackagingExplorer**. Частичная проверка выполняется при добавлении нового проекта SharePonit или функции в проект, чтобы определить, пакета или компонента будет находиться в недопустимом состоянии.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Чтобы создать настраиваемое правило проверки пакета  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Создайте класс, который реализует один из следующих интерфейсов:  
  
    -   Чтобы создать правило проверки пакета, реализуйте <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> интерфейса.  
  
    -   Чтобы создать правило проверки компонента, реализуйте <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> интерфейса.  
  
4.  Добавить <xref:System.ComponentModel.Composition.ExportAttribute> к классу. Этот атрибут позволяет Visual Studio находить и загружать пользовательское правило проверки. Передайте <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> или <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> тип в конструктор атрибута.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как создать пользовательское правило проверки компонента.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Чтобы развернуть расширение, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение упаковки и развертывания проектов SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  