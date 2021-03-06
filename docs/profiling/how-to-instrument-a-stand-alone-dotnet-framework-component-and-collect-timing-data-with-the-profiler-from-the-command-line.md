---
title: "Практическое руководство. Инструментирование автономного компонента .NET Framework и сбор данных о времени с помощью профилировщика из командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Практическое руководство. Инструментирование автономного компонента .NET Framework и сбор данных о времени с помощью профилировщика из командной строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описывается использование средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с интерфейсом командной строки для инструментирования таких компонентов .NET Framework, как EXE\- и DLL\-файлы, а также для сбора подробных данных о времени.  
  
> [!NOTE]
>  Функции усиленной безопасности в Windows 8 и Windows Server 2012 требуют значительных изменений в способе сбора данных профилировщиком Visual Studio на этих платформах.  Для Приложений Магазина Windows также требуются новые методы сбора.  См. раздел [Профилирование приложений для Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Программы командной строки средств профилирования расположены в подкаталоге \\Team Tools\\Performance Tools каталога установки [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  На 64\-разрядных компьютерах доступны 64\-разрядные и 32\-разрядные версии средств.  Для использования программ командной строки профилировщика необходимо добавить путь к этим программам в переменную среды PATH окна Командная строка или указать этот путь при вызове команды.  Для получения дополнительной информации см. [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Добавление данных об уровневом взаимодействии в сеанс профилирования требует определенных процедур со средствами профилирования командной строки.  См. раздел [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Для сбора подробных данных об использовании времени, предоставляемых компонентом .NET Framework, с помощью метода инструментирования используются программа [VSInstr.exe](../profiling/vsinstr.md), позволяющая создать инструментированную версию компонента, и программа [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md), с помощью которой можно инициализировать переменные среды, используемые для профилирования.  Затем запустите профилировщик.  
  
 При выполнении инструментированного компонента данные о времени автоматически сохраняются в файл данных.  В ходе сеанса профилирования можно приостанавливать и возобновлять сбор данных.  
  
 Для завершения сеанса профилирования нужно закрыть целевое приложение, а затем явным образом завершить работу профилировщика.  В большинстве случаев рекомендуется удалять в конце сеанса значения переменных среды, используемые для профилирования.  
  
## Запуск сеанса профилирования  
  
#### Процедура запуска профилирования с помощью метода инструментирования  
  
1.  Откройте окно командной строки.  При необходимости добавьте каталог средств профилирования в переменную среды PATH.  Этот путь не добавляется при установке.  
  
2.  Для создания инструментированной версии целевого приложения воспользуйтесь программой **VSInstr**.  
  
3.  Инициализируйте переменные среды, используемые для профилирования .NET Framework.  Type:  
  
     **VSPerfClrEnv \/traceon**  
  
4.  Запустите профилировщик.  Type:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   Параметр [\/start](../profiling/start.md)**:trace** обеспечивает инициализацию профилировщика.  
  
    -   Параметр [\/output](../profiling/output.md)**:**`OutputFile` является обязательным при использовании параметра **\/start**.  Параметр `OutputFile` задает имя и расположение файла с данными профилирования \(VSP\-файла\).  
  
     С параметром **\/start:trace** можно использовать любые из следующих параметров.  
  
    |Команда|Описание|  
    |-------------|--------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Задает домен и имя пользователя учетной записи, которая является владельцем профилируемого процесса.  Этот параметр является обязательным только в том случае, если процесс выполняется от имени пользователя, отличного от пользователя, который выполнил вход в систему.  Имя владельца процесса отображается в столбце "Имя пользователя" на вкладке "Процессы" диспетчера задач Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Включает профилирование процессов в других сеансах.  Этот параметр является обязательным, если приложение ASP.NET выполняется в рамках другого сеанса.  Идентификатор сеанса отображается в столбце "Код сеанса" на вкладке "Процессы" диспетчера задач Windows.  Для **\/crosssession** может быть задано сокращение **\/CS**.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Запускает профилировщик с приостановленным сбором данных.  Для возобновления профилирования используйте параметр [\/globalon](../profiling/globalon-and-globaloff.md).|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Собирает данные счетчика производительности процессора, заданного параметром `Config`.  Показатели счетчиков добавляются к данным, собранным для каждого события профилирования.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Задает счетчик производительности Windows, данные которого следует собирать в процессе профилирования.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Используйте только с **\/wincounter**.  Задает интервал времени \(в миллисекундах\) между событиями сбора данных счетчика производительности Windows.  Значение по умолчанию — 500 мс.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Задает событие трассировки событий Windows, данные которого следует собирать в процессе профилирования.  События трассировки событий Windows собираются в отдельный ETL\-файл.|  
  
5.  Запустите целевое приложение из окна командной строки.  
  
## Управление сбором данных  
 Когда выполняется целевое приложение, можно управлять сбором данных путем запуска и остановки записи данных в файл данных профилировщика с помощью параметров **VSPerfCmd.exe**.  Управление сбором данных позволяет собирать данные на различных этапах выполнения программы, например, при запуске или завершении работы приложения.  
  
#### Запуск и остановка сбора данных  
  
-   Следующие пары параметров используются для запуска и остановки сбора данных.  Задайте каждый параметр в отдельной строке командной строки.  Запуск и приостановка сбора данных могут выполняться неоднократно.  
  
    |Команда|Описание|  
    |-------------|--------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Запускает \(**\/globalon**\) или останавливает \(**\/globaloff**\) сбор данных для всех процессов.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Запускает \(**\/processon**\) или останавливает \(**\/processoff**\) сбор данных для процесса с указанным идентификатором процесса \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Запускает \(**\/threadon**\) или останавливает \(**\/threadoff**\) сбор данных для потока с указанным идентификатором потока \(`TID`\).|  
  
## Завершение сеанса профилирования  
 Чтобы завершить сеанс профилирования, закройте приложение, в котором выполняется инструментированный компонент.  Чтобы завершить работу профилировщика и закрыть файл данных профилирования, вызовите команду **VSPerfCmd** [\/shutdown](../profiling/shutdown.md).  Команда **VSPerfClrEnv \/off** удаляет значения переменных среды, используемые для профилирования.  
  
#### Завершение сеанса профилирования  
  
1.  Закройте целевое приложение.  
  
2.  Завершите работу профилировщика.  Type:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Необязательно.\) Удалите переменные среды, используемые для профилирования.  Type:  
  
     **VSPerfClrEnv \/off**  
  
## См. также  
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Представление данных метода инструментирования](../profiling/instrumentation-method-data-views.md)