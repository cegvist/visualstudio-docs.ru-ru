---
title: "Задача GenerateBootstrapper | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3feb529b76b9de8c70b87954e928a75158361f6b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="generatebootstrapper-task"></a>Задача GenerateBootstrapper
Задача обеспечивает автоматическое обнаружение, скачивание и установку приложения и необходимых для него компонентов. Она служит единым установщиком, объединяющим отдельные установщики для всех компонентов, образующих приложение.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `GenerateBootstrapper` .  
  
-   `ApplicationFile`  
  
     Необязательный параметр `String` .  
  
     Указывает файл, который будет использоваться начальным загрузчиком для запуска установки приложения после установки всех необходимых компонентов. Если не задан ни один из параметров `BootstrapperItems` и `ApplicationFile`, произойдет ошибка сборки.  
  
-   `ApplicationName`  
  
     Необязательный параметр `String` .  
  
     Указывает имя приложения, которое будет установлено загрузчиком. Это имя будет отображаться в пользовательском интерфейсе загрузчика во время установки.  
  
-   `ApplicationRequiresElevation`  
  
     Необязательный параметр `Boolean` .  
  
     Если `true`, компонент выполняется с повышенным уровнем разрешений при установке на целевом компьютере.  
  
-   `ApplicationUrl`  
  
     Необязательный параметр `String` .  
  
     Задает расположение установщика приложения в Интернете.  
  
-   `BootstrapperComponentFiles`  
  
     Необязательный выходной параметр `String[]`.  
  
     Задает расположение сборки для файлов пакета загрузчика.  
  
-   `BootstrapperItems`  
  
     Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .  
  
     Задает продукты, встраиваемые в загрузчик. Элементы, передаваемые в этот параметр, должны иметь следующий синтаксис:  
  
    ```xml  
    <BootstrapperItem  
        Include="ProductCode">  
        <ProductName>  
            ProductName  
        </ProductName>  
    </BootstrapperItem>  
    ```  
  
     Атрибут `Include` представляет имя необходимого компонента, который должен быть установлен. Метаданные элемента `ProductName` указывать не обязательно. Они будут использоваться обработчиком сборки ядром в качестве понятного имени в случае, если найти пакет не удастся. Эти элементы не являются обязательными входными параметрами [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], если не задан параметр `ApplicationFile`. Следует указать по одному элементу на каждый необходимый компонент, который должен быть установлен для приложения.  
  
     Если не задан ни один из параметров `BootstrapperItems` и `ApplicationFile`, произойдет ошибка сборки.  
  
-   `BootstrapperKeyFile`  
  
     Необязательный выходной параметр `String`.  
  
     Задает расположение сборки для программы setup.exe.  
  
-   `ComponentsLocation`  
  
     Необязательный параметр `String` .  
  
     Задает расположение, в котором начальный загрузчик будет искать необходимые компоненты для установки. Этот параметр может иметь следующие значения.  
  
    -   `HomeSite`: указывает, что необходимый компонент размещается у поставщика компонентов.  
  
    -   `Relative`: указывает, что необходимый компонент располагается в том же месте, что и приложение.  
  
    -   `Absolute`: указывает, что все компоненты располагаются по единому URL-адресу. Это значение следует использовать в связке со входным параметром `ComponentsUrl`.  
  
     Если параметр `ComponentsLocation` не задан, по умолчанию используется значение `HomeSite`.  
  
-   `ComponentsUrl`  
  
     Необязательный параметр `String` .  
  
     Задает URL-адрес, по которому располагаются необходимые компоненты для установки.  
  
-   `CopyComponents`  
  
     Необязательный параметр `Boolean` .  
  
     Если этот параметр равен `true`, загрузчик копирует все выходные файлы в место, задаваемое параметром `OutputPath`. Все значения параметра `BootstrapperComponentFiles` должны основываться на этом пути. Если этот параметр равен `false`, файлы не копируются и значения `BootstrapperComponentFiles` основываются на значении параметра `Path`.  По умолчанию этот параметр имеет значение `true`.  
  
-   `Culture`  
  
     Необязательный параметр `String` .  
  
     Задает язык и региональные параметры, которые следует использовать для пользовательского интерфейса загрузчика и необходимых компонентов установки. Если заданные язык и региональные параметры недоступны, задача использует значение параметра `FallbackCulture`.  
  
-   `FallbackCulture`  
  
     Необязательный параметр `String` .  
  
     Задает дополнительные язык и региональные параметры, которые следует использовать для пользовательского интерфейса загрузчика и необходимых компонентов установки.  
  
-   `OutputPath`  
  
     Необязательный параметр `String` .  
  
     Задает расположение, в которое следует копировать файл setup.exe и все файлы пакетов.  
  
-   `Path`  
  
     Необязательный параметр `String` .  
  
     Задает расположение всех имеющихся необходимых пакетов.  
  
-   `SupportUrl`  
  
     Необязательный параметр `String` .  
  
     Задает URL-адрес, который следует отобразить при сбое установки загрузчика.  
  
-   `Validate`  
  
     Необязательный параметр `Boolean` .  
  
     Если этот параметр равен `true`, загрузчик производит проверку XSD для заданных входных элементов загрузчика. По умолчанию этот параметр имеет значение `false`.  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере используется задача `GenerateBootstrapper` для установки приложения, требующего установки [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] в качестве необходимого компонента.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">  
            <ProductName>Microsoft .NET Framework 2.0</ProductName>  
        </BootstrapperFile>  
    </ItemGroup>  
  
    <Target Name="BuildBootstrapper">  
        <GenerateBootstrapper  
            ApplicationFile="WindowsApplication1.application"  
            ApplicationName="WindowsApplication1"  
            ApplicationUrl="http://mycomputer"  
            BootstrapperItems="@(BootstrapperFile)"  
            OutputPath="C:\output" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)