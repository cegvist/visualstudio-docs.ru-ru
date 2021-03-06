---
title: "Задача Warning | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ca4e9906d31468b028f1ad9a39c196bd54e3fb9e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="warning-task"></a>Задача Warning
Регистрирует в журнале предупреждение в процессе сборки на основе вычисленного условного оператора.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи `Warning`.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`Code`|Необязательный параметр `String` .<br /><br /> Код предупреждения для связи с предупреждением.|  
|`File`|Необязательный параметр `String` .<br /><br /> Указывает соответствующий файл (при его наличии). Если файл не указан, используется файл, содержащий задачу Warning.|  
|`HelpKeyword`|Необязательный параметр `String` .<br /><br /> Ключевое слово справки для связи с предупреждением.|  
|`Text`|Необязательный параметр `String` .<br /><br /> Текст предупреждения, регистрируемый в журнале [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], если результат вычисления параметра `Condition` оказывается равным `true`.|  
  
## <a name="remarks"></a>Примечания  
 Задача `Warning` позволяет проектам [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] проверять наличие необходимой конфигурации или необходимого свойства перед переходом к следующему шагу сборки.  
  
 Если параметр `Condition` задачи `Warning` равен `true`, значение параметра `Text` записывается в журнал, а процесс сборки продолжается. Если параметр `Condition` не существует, текст предупреждения записывается в журнал. Дополнительные сведения о ведении журнала см. в разделе [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода проверяет свойства, заданные в командной строке. Если заданные свойства отсутствуют, проект инициирует событие предупреждения и регистрирует в журнале значение параметра `Text` задачи `Warning`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Получение журналов построения](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)