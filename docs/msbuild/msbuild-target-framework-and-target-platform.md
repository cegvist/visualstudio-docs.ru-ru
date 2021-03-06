---
title: "MSBuild: целевая рабочая среда и целевая платформа | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e175a534cb35333b1f57c188c62a781f2fd68627
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild: целевая рабочая среда и целевая платформа
Проект может быть создан для выполнения в *требуемой версии .NET Framework*, которая является конкретной версией платформы .NET Framework, и на *целевой платформе*, которая является конкретной программной архитектурой.  Например, можно настроить приложение для выполнения в .NET Framework 2.0 на 32-разрядной платформе, которая совместима с семейством процессоров 802x86 ("x86"). Сочетание требуемой версии .NET Framework и целевой платформы называется *целевым контекстом*.  
  
## <a name="target-framework-and-profile"></a>Целевая платформа и профиль  
 Целевая платформа — это конкретная версия [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], для выполнения на которой создан проект. Спецификация целевой платформы является необходимым условием, поскольку она позволяет использовать возможности компилятора и ссылки на сборки, предназначенные исключительно для этой версии платформы.  
  
 В настоящее время доступны следующие версии платформы .NET Framework.  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (входит в состав Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (входит в состав [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (входит в состав [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (входит в состав [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.1  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.2  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7.1  
  
 Версии платформы .NET Framework отличаются друг от друга в списке сборок, доступном для использования в справочных целях. Например, приложения WPF можно создавать, только если проект предназначен для платформы .NET Framework версии 3.0 или выше.  
  
 Целевая версия .NET Framework указывается в свойстве `TargetFrameworkVersion` в файле проекта. Целевую версию .NET Framework для проекта можно изменить с помощью страниц свойств проекта в интегрированной среде разработки Visual Studio. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Доступными значениями для `TargetFrameworkVersion` являются `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v.4.6.1`, `v4.6.2`, `4.7` и `4.7.1`.  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 *Целевой профиль* — это подмножество целевой платформы. Например, профиль клиента .NET Framework 4 не содержит ссылок на сборки MSBuild.  
  
 Целевой профиль указывается в свойстве `TargetFrameworkProfile` в файле проекта. Целевой профиль можно изменить с помощью элемента управления целевой платформы на страницах свойств проекта в интегрированной среде разработки. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Целевая платформа  
 *Платформа* — это сочетание оборудования и программного обеспечения, которое определяет конкретную среду выполнения. Например, примененная к объекту директива  
  
-   `x86` обозначает 32-разрядную операционную систему Windows, работающую с процессором Intel 80x86 или эквивалентным.  
  
-   `Xbox` обозначает платформу Microsoft Xbox 360.  
  
 *Целевая платформа* — это конкретная платформа, для выполнения на которой создан проект. Целевая платформа указывается в свойстве сборки `Platform` в файле проекта. Целевую платформу можно изменить с помощью страниц свойств проекта или **диспетчера конфигураций** в интегрированной среде разработки.  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 *Целевая конфигурация* — это подмножество целевой платформы. Например, конфигурация `x86``Debug` не поддерживает большинство видов оптимизации кода. Целевая конфигурация указывается в свойстве сборки `Configuration` в файле проекта. Целевую конфигурацию можно изменить с помощью страниц свойств проекта или **диспетчера конфигураций**.  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)