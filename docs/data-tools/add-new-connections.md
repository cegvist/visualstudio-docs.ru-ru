---
title: "Добавление новых подключений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: accf99d7a1d230bac64ebd8ebf9c9f1071ad1876
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="add-new-connections"></a>Добавление новых подключений
Проверьте подключение к базе данных или службы и изучить содержимое базы данных и схемы с помощью **обозревателя серверов**, **Cloud Explorer**, или **обозреватель объектов SQL Server**. Функциональные возможности этих окон пересекается в некоторой степени. Ниже перечислены основные различия.  
  
 - обозревателя серверов  
 Устанавливается по умолчанию в Visual Studio. Можно использовать для проверки подключения и просмотра баз данных SQL Server, базы данных которых установлен поставщик ADO.NET и несколько служб Azure. Также показывает низкоуровневые объекты, такие как счетчики производительности системы, журналы событий и очереди сообщений. Если в источнике данных нет поставщика ADO.NET, он не будет отображаться здесь, но его можно по-прежнему использовать из Visual Studio путем подключения программным образом.  
  
 - Cloud Explorer  
 Установите это окно вручную как расширение Visual Studio, выбрав **средства** > **расширения и обновления** > **Online**  >  **Коллекции visual Studio**. Предоставляет специализированные функции для просмотра и подключения к службам Azure.  
  
 - Обозреватель объектов SQL Server  
 Вместе с SQL Server Data Tools и отображается под **представление** меню. Если вы их там нет, перейдите к **программы и компоненты** панели управления найдите Visual Studio и выберите **изменений** для повторного запуска программы установки после установки флажка для SQL Server Data Tools. Используйте **обозреватель объектов SQL Server** для представления базы данных SQL (если они имеют поставщик ADO.NET), создать новые базы данных, изменения схемы, создания хранимых процедур, получить строки подключения, просматривать данные и многое другое. Базы данных SQL, которые не установлен поставщик ADO.NET не будет отображаться здесь, но вы можете подключаться к ним программным способом.  
  
## <a name="add-a-connection-in-server-explorer"></a>Добавить соединение в обозревателе серверов  
 Чтобы создать подключение к базе данных, нажмите кнопку **добавить подключение** значок в **обозревателя серверов**, или щелкните правой кнопкой мыши **обозревателя серверов** на **данных Подключения** , а затем выберите **добавить подключение**. Здесь можно подключиться к базе данных на другом сервере, службы SharePoint или службы Azure.  
  
 ![Значок нового подключения обозревателя сервера](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata значок нового подключения обозревателя сервера")  
  
 Откроется окно **добавить подключение** диалоговое окно. Здесь мы ввели имя экземпляра SQL Server LocalDB.  
  
 ![Добавление нового подключения](../data-tools/media/raddata-add-new-connection-dialog.png "raddata добавить новое диалоговое окно соединения")  
  
## <a name="change-the-provider"></a>Изменить поставщика  
 Если источник данных не требуется, нажмите кнопку **изменений** кнопку, чтобы выбрать новый источник данных и/или новый поставщик данных ADO.NET. Новый поставщик может запрашивать учетные данные, в зависимости от того, как настроить.  
  
 ![Изменить поставщика данных AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png "raddata изменить AD0.NET данных поставщика")  
  
## <a name="test-the-connection"></a>Проверка соединения  
 После выбора источника данных, нажмите кнопку **проверить подключение**. Если не выполнены успешно, необходимо будет Устранение зависимости в документации поставщика.  
  
 ![Проверка соединения](../data-tools/media/raddata-test-connection.png "raddata проверить подключение")  
  
 Если тест выполняется успешно, можно приступать к созданию *источника данных*, — это понятие Visual Studio, на самом деле означает *модели данных* , основанный на базовой базы данных или службы.  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)