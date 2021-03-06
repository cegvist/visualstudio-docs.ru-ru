---
title: "Не удалось присоединиться к процессу | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 15acb250c561cb1c7d414784f355a9239ead53ef
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="unable-to-attach-to-the-process"></a>Не удается присоединиться к процессу
Не удается присоединиться к процессу. Компонент отладчика на сервере получил отказ в доступе при подключении к этому компьютеру.  
  
 Существуют два типичных скрипта, вызывающих эту ошибку:  
  
 **Сценарий 1:** компьютер A работает под управлением Windows XP. Компьютер B работает под управлением Windows Server 2003. Реестр на компьютере B содержит следующее значение DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Пользователь 1 запускает сеанс службы терминалов (сеанс 1) на компьютере B и запускает управляемое приложение из этого сеанса.  
  
 Пользователь 2, являющийся администратором обоих компьютеров, вошел в систему компьютера A. Оттуда он пытается подключиться к приложению, выполняющемуся в сеансе 1 на компьютере B.  
  
 **Сценарий 2.** одного пользователя на двух компьютерах — A и B, в той же рабочей группе, используя одинаковые пароли на обоих компьютерах. Отладчик выполняется на компьютере A и пытается подключиться к управляемому приложению, выполняющемуся на компьютере B. на компьютере A **сетевой доступ: модель совместного доступа и безопасности для локальных учетных записей** значение **гостевой**.  
  
### <a name="to-solve-scenario-1"></a>Решение скрипта 1  
  
-   Запустите отладчик и управляемое приложение под одним и тем же именем учетной записи пользователя и паролем.  
  
### <a name="to-solve-scenario-2"></a>Решение скрипта 2  
  
1.  Из **запустить** меню, выберите **панели управления**.  
  
2.  На панели управления дважды щелкните **Администрирование**.  
  
3.  В окне «Администрирование» дважды щелкните **Локальная политика безопасности**.  
  
4.  В окне «Локальная политика безопасности» выберите **локальные политики**.  
  
5.  В **политики** столбец, дважды щелкните **сетевой доступ: модель совместного доступа и безопасности для локальных учетных записей**.  
  
6.  В **сетевой доступ: модель совместного доступа и безопасности для локальных учетных записей** диалоговом окне измените параметр локальной безопасности для **классический**и нажмите кнопку **ОК**.  
  
    > [!CAUTION]
    >  Изменение модели безопасности на обычную может привести к непредвиденным возможностям доступа к общим файлам и DCOM-компонентам. Если сделать это, удаленный пользователь сможет проходить проверку подлинности под локальной учетной записью пользователя вместо записи "Гость". Если у него такие же, как у вас, имя пользователя и пароль, то он сможет получить доступ к любой папке или объекту DCOM, которые открыты вами для общего доступа. Если используется эта модель безопасности, убедитесь, что все учетные записи пользователей на компьютере обладают надежными паролями или настройте изолированную сеть для отладочных и отлаживаемых компьютеров для предотвращения несанкционированного доступа.  
  
7.  Закройте все окна.  
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)