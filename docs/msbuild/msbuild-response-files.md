---
title: "Файлы ответов MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7520a9f51f0d9420039728a75e84d4ed16583738
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-response-files"></a>Файлы ответов MSBuild
Файлы ответов (RSP) — это текстовые файлы, содержащие параметры командной строки MSBuild.exe. Каждый параметр может находиться в отдельной строке, либо все они могут быть в одной строке. Перед строками примечаний указывается символ **#**. Параметр **@** используется для передачи другого файла ответов в MSBuild.exe.  
  
 Файл автоматического ответа — это специальный файл RSP, который автоматически используется программой MSBuild.exe при сборке проекта. Этот файл MSBuild.rsp должен находится в одном каталоге с программой MSBuild.exe, иначе он не будет обнаружен. Этот файл можно изменять для того, чтобы задать для MSBuild.exe параметры командной строки по умолчанию. Например, если при сборке проекта всегда используется одно и то же средство ведения журнала, можно добавить в файл MSBuild.rsp параметр **/logger**. В этом случае MSBuild.exe будет всегда использовать это средство ведения журнала при сборке проекта.  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)