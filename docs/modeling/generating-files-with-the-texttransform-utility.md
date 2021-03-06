---
title: "Создание файлов с помощью служебной программы TextTransform | Документы Microsoft"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: b7816e11c431f17336955f2037d288641b6c3ad5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="generating-files-with-the-texttransform-utility"></a>Создание файлов с помощью служебной программы TextTransform
TextTransform.exe является средством командной строки, которое можно использовать для преобразования текстового шаблона. При вызове TextTransform.exe указываются имя файла текстового шаблона как аргумент. TextTransform.exe вызывает обработчик преобразования текста и обрабатывает текстового шаблона. TextTransform.exe обычно вызывается из скриптов. Тем не менее это не обычно не требуется, поскольку выполняется преобразование текста в Visual Studio или в процессе построения.  
  
> [!NOTE]
>  Если вы хотите выполнить преобразование текста в рамках процесса построения, рассмотрите возможность использования задачи преобразования текста MSBuild. Дополнительные сведения см. в разделе [создание кода в процессе сборки](../modeling/code-generation-in-a-build-process.md). В компьютере, на котором [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] установлен, можно также написать приложение или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширение, которое можно преобразования текстовых шаблонов. Дополнительные сведения см. в разделе [обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe находится в следующем каталоге:  
  
 **\Program файлы (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**  

для выпуска Professional или

 **\Program файлы (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**
 
 для выпуска Enterprise edition.

В предыдущих версиях Visual Studio этот файл находится в следующем расположении:

**Файлы (x86) \Program \Common Files\Microsoft Shared\TextTemplating\{версии}**

где {version} зависит от установленной предыдущей версии.

## <a name="syntax"></a>Синтаксис  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Параметры  
  
|**Аргумент**|**Описание**|  
|------------------|---------------------|  
|`templateName`|Определяет имя файла шаблона, который требуется преобразовать.|  
  
|**Параметр**|**Описание**|  
|----------------|---------------------|  
|**-out** \<filename>|Файл, в который записывается выходные данные преобразования.|  
|**-r** \<assembly>|Сборка, используемая для компиляции и выполнения шаблона текста.|  
|**-u** \<пространство имен >|Пространство имен, которое используется для компиляции шаблона.|  
|**-I** \<includedirectory >|Каталог, содержащий текстовые шаблоны, включенные в указанный текстовый шаблон.|  
|**-P** \<referencepath>|Указывает каталог поиска для сборок, указанных в текстовом шаблоне или с помощью **- r** параметр.<br /><br /> Например чтобы включить сборки, используемые для Visual Studio API, используйте<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Имя, полное имя типа и сборка процессора директив, который может использоваться для обработки пользовательских директивы в текстовом шаблоне.|  
|**-a** [processorName]![directiveName]!\<parameterName>!\<parameterValue>|Укажите значение параметра для процессора директив. Если указать только имя параметра и значение параметра будет доступен для всех процессоров директив. При указании процессора директив параметр доступен только для указанного процессора. При указании имени директивы, то параметр будет доступен только при обработке указанной директивы.<br /><br /> Для доступа к значения параметров из процессора директив или текстовый шаблон, используйте <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>. В текстовом шаблоне включают `hostspecific` в директиве шаблона и вызвать сообщение на `this.Host`. Пример:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Всегда введите "!" помечает, даже если не указан необязательный процессора и имен директивы. Пример:<br /><br /> `-a !!param!value`|  
|**-h**|Предоставляет справку.|  
  
## <a name="related-topics"></a>См. также  
  
|Задача|Раздел|  
|----------|-----------|  
|Создание файлов в решении [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|  
|Запись шаблонов узла текста, который позволяет вызывать текстовые шаблоны из собственного приложения.|[Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)|
