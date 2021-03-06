---
title: "Параметры страниц свойств для веб-проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e58541c5ab0c7a38773740343349880aa5297e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="property-pages-settings-for-web-projects"></a>Параметры страниц свойств для веб-проектов
Можно изменить значения свойств для конфигурации отладки веб-сайта в **страницы свойств** диалоговое окно, как описано в [конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md). В следующих таблицах показано, где можно найти параметры, связанные с отладчиком **страницы свойств** диалоговое окно.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Папка "Свойства конфигурации" (категория "Параметры запуска")  
  
|**Параметр**|**Описание**|  
|-----------------|---------------------|  
|**Действие при запуске**|Заголовок, группирующий параметры запуска приложения.|  
|**Использовать текущую страницу**|Задает текущую страницу в качестве начальной точки для отладки.|  
|**Указанная страница:**|Задает веб-страницу с которой должна начинаться отладка.|  
|**Запуск внешней программы:**|Задает команду для запуска отлаживаемой программы.|  
|**Аргументы командной строки:**|Описывает аргументы для заданной выше команды.|  
|**Рабочий каталог:**|Задает рабочий каталог для отлаживаемой программы. В [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] рабочий каталог — это каталог, откуда запускается приложение, по умолчанию — "\bin\debug".|  
|**Начальный URL-адрес**|Задает местоположение отлаживаемого веб-приложения.|  
|**Не открывать страницу. Дождаться запроса из внешнего приложения**|Устанавливает, что надо дождаться запроса из внешнего приложения. В этом варианте не производится запуск браузера Internet Explorer или другого приложения. Просто производится подготовка к отладке при вызове приложением.|  
|**Сервер**|Заголовок, группирующий параметры, связанные с используемым сервером.|  
|**Использовать веб-сервер по умолчанию**|Устанавливает, что надо использовать веб-сервер по умолчанию.|  
|**Использовать другой сервер**|Позволяет ввести базовый URL-адрес для использования в качестве сервера.|  
|**Отладчики**|Заголовок, группирующий параметры, связанные с типом отладки, который необходимо выполнить.|  
|**Отладка ASP.NET**|Включается отладка серверных страниц, написанных для платформы разработки [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Необходимо указать URL-адрес в **начальный URL-адрес**.|  
|**Отладка машинного кода**|Разрешает отлаживать вызовы машинного (неуправляемого) кода Win32 из управляемого приложения.|  
|**Отладка SQL Server**|Разрешает отладку объектов базы данных SQL Server.|  
|**Отладка Silverlight**|Обеспечивает отладку компонентов Silverlight.|  
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)