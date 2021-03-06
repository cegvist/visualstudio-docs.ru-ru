---
title: "Команда \"Перейти\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 53c45ccf528375bc31b4d61fd6af0193aa295e6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="go-to-command"></a>Команда Go To
Перемещение курсор на указанную строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Аргументы  
 `linenumber`  
 Необязательный. Целое число, задающее номер строки, к которой нужно перейти.  
  
## <a name="remarks"></a>Примечания  
 Нумерация строк начинается с единицы. Если значение `linenumber` меньше единицы, отображается первая строка. Если значение `linenumber` больше номера последней строки, отображается последняя строка.  
  
 Если значение `linenumber` не указано, отображается диалоговое окно **Переход на строку**.  
  
 Эта команда имеет псевдоним GoToLn.  
  
## <a name="example"></a>Пример  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)