---
title: "-Build (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8eba6684167e4b60f02512e9b0fc1c7dc514a614
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
Выполняет сборку решения с использованием заданного файла конфигурации решения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>Аргументы  
 `SolutionName`  
 Обязательно. Полный путь и имя для файла решения.  
  
 `SolnConfigName`  
 Обязательно. Имя конфигурации решения, которая будет применяться для сборки решения, указанного в `SolutionName`.  
  
 /project `ProjName`  
 Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.  
  
 /projectconfig `ProjConfigName`  
 Необязательный. Имя конфигурации сборки проекта, которая применяется при сборке указанного `/project`.  
  
## <a name="remarks"></a>Примечания  
 Этот параметр выполняет те же функции, что и команда меню **Собрать решение** в интегрированной среде разработки (IDE).  
  
 Строки с пробелами заключаются в двойные кавычки.  
  
 Сводные данные для сборок, включая ошибки, могут отображаться в окне **команд** или в любом файле журнала, указанном с помощью параметра `/out`.  
  
 Эта команда выполняет сборку только тех проектов, которые изменились с момента последней сборки. Чтобы выполнить сборку всех проектов в решении, используйте [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).  
  
## <a name="example"></a>Пример  
 В этом примере выполняется сборка проекта `CSharpConsoleApp` с использованием конфигурации проекта `Debug` в пределах конфигурация решения `Debug` для `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>См. также  
 [Building and Cleaning Projects and Solutions in Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)  (Построение и очистка проектов и решений в Visual Studio)  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)