---
title: "Элемент ProjectItem (шаблоны проектов Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ca5143a3e5eaff488fee89b643a40adb60473bd8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Элемент ProjectItem (шаблоны проектов Visual Studio)
Указывает файл, который включен в шаблоне проекта.  
  
> [!NOTE]
>  `ProjectItem` Элемент принимает различные атрибуты в зависимости от того, является ли шаблон для проекта или элемента. В этом разделе объясняется `ProjectItem` элемент для шаблонов проектов. Объяснение `ProjectItem` для шаблонов элементов, см. в разделе [элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<ProjectItem >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`TargetFileName`|Необязательный атрибут.<br /><br /> Указывает имя и путь к элементу проекта при создании проекта из шаблона. Этот атрибут полезен для создания структуры каталогов отличается от структуры каталогов в ZIP-файле шаблона или при использовании замены параметров для создания имени элемента.|  
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, содержит ли элемент значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию — `false`.|  
|`OpenInEditor`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, следует ли открывать элемент в соответствующем редакторе или в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] при создании проекта из шаблона.<br /><br /> `OpenInWebBrowser` И `OpenInHelpBrowser` пропущены атрибуты в элемент с `OpenInEditor` значение `true`.<br /><br /> Значение по умолчанию — `false`.|  
|`OpenInWebBrowser`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, следует ли открывать элемент веб-браузера при создании проекта из шаблона.<br /><br /> Только HTML-файлы и текстовые файлы, которые являются локальными в проект можно открыть в веб-браузере. Не удается открыть внешние URL-адреса с помощью этого атрибута.<br /><br /> Значение по умолчанию — `false`.|  
|`OpenInHelpBrowser`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, следует ли открывать элемент в средстве просмотра справки при создании проекта из шаблона.<br /><br /> В средстве просмотра справки можно открыть только HTML-файлы и текстовые файлы, являющиеся локальными для проекта. Не удается открыть внешние URL-адреса с помощью этого атрибута.<br /><br /> Значение по умолчанию — `false`.|  
|`OpenOrder`|Необязательный атрибут.<br /><br /> Указывает числовое значение, представляющее порядок, в том, что элементы будут открыты в соответствующих редакторах. Все значения должны быть кратными 10. Элементы, которые выше `OpenOrder` сначала открытых значения.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Проект](../extensibility/project-element-visual-studio-templates.md)|Указывает, файлов или каталогов, добавляемых в проект.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Объект `string` , представляющий имя или путь к файлу в ZIP-файле шаблона.  
  
## <a name="remarks"></a>Примечания  
 `ProjectItem`Необязательный дочерний `Project`.  
  
 `TargetFileName` Атрибут может использоваться для создания структуры каталогов отличается от структуры каталогов в ZIP-файле шаблона. Например если файл `MyFile.vb` в корне ZIP-файле шаблона, но требуется файл помещается в каталог с именем `CustomFiles` во всех проектах, созданных из шаблона, используется следующий XML-код:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName` Атрибут также может использоваться для переименования файлов, содержащих международных символов в именах. Например ZIP-файл шаблона не может содержать имена файлов с символами Юникода, поэтому необходимо переименовать файл, прежде чем могут быть сжаты в ZIP-файл. `TargetFileName` Атрибут может использоваться для задания имени файла к имени исходного файла Юникода.  
  
 `TargetFileName` Атрибут также может использоваться для переименования файлов с параметрами. Следующая процедура объясняет, как переименовать файл `MyFile.vb`, который существует в корневом каталоге ZIP-файле шаблона к имени файла, на основе имени проекта.  
  
### <a name="to-rename-files-with-parameters"></a>Для переименования файлов с параметрами  
  
1.  Используйте следующий XML-код в файле .vstemplate.  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Откройте файл проекта (VBPROJ-файлу для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] проекта) в текстовом редакторе или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Найдите строку в файле проекта, похожее на следующий XML-код:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Замените строку кода следующий код XML:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     При создании проекта на основе этого шаблона, имя файла будет основываться на имени, введенного пользователем в **новый проект** диалоговое окно с всех небезопасных символов и пробелов. Дополнительные сведения см. в разделе [параметров шаблона](../ide/template-parameters.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)