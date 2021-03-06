---
title: "VSPerfCLREnv | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 629e810bd05fe838e18cc78587921266c351f32d
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Средство VSPerfCLREnv служит для задания переменных среды, необходимых для профилирования приложения .NET Framework. Для этого используется следующий синтаксис:

```
VsPerfCLREnv [/option]
```

Параметр выбирается на основе используемого метода профилирования: выборки, инструментирования или глобального. Отдельный параметр необходим для включения данных уровневого взаимодействия в данные профилирования. Синтаксис каждого параметра описывается в приведенных ниже таблицах.

> [!NOTE]
> После завершения профилирования запустите **VSPerfCLREnv** с параметром **/off** или **/globaloff**, чтобы удалить переменные среды, необходимые для профилирования. Дополнительные сведения см в разделе "Параметры средства VSPerfCLREnv для удаления переменных среды" ниже.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Параметры VSPerfCLREnv для включения данных уровневого взаимодействия

> [!WARNING]
> Сведения о профилировании уровневого взаимодействия можно собирать с помощью любого выпуска Visual Studio. Но данные профилирования уровневого взаимодействия можно просматривать только в Visual Studio Enterprise.

Профилирование уровневого взаимодействия предоставляет дополнительные сведения о запросах ADO.NET в многоуровневых приложениях. Данные собираются только для синхронных вызовов функций. Данные взаимодействия можно добавлять в любой сеанс профилирования с помощью любого из методов профилирования.

Параметры **InteractionOn** и **GlobalInteractionOn** включают сбор данных уровневого взаимодействия. Параметр взаимодействия необходимо устанавливать после задания переменной среды VSPerfCLREnv, которая является обязательной для профилирования приложения.

В следующем примере данные уровневого взаимодействия включаются в сеанс профилирования, использующий метод выборки:

```
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

В следующем примере данные уровневого взаимодействия включаются в сеанс профилирования службы Windows:

```
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp 
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Параметры VSPerfCLREnv для профилирования процессов с инструментированием

В таблице ниже описаны параметры средства VSPerfCLREnv для профилирования с инструментированием.

|Параметр|Описание:|
|------------|-----------------|
|**TraceOn**|Включает профилирование с помощью метода инструментирования. Не включает профилирование выделения памяти или сбор данных о времени существования объектов.|
|**TraceGC**|Включает профилирование выделения памяти с помощью метода инструментирования. Не включает сбор данных о времени существования объектов.|
|**TraceGCLife**|Включает профилирование выделения памяти и сбор данных о времени существования объектов с помощью метода инструментирования.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Параметры VSPerfCLREnv для профилирования процессов с выборкой

В таблице ниже описаны параметры средства VSPerfCLREnv для профилирования с выборкой.

|Параметр|Описание:|
|------------|-----------------|
|**SampleOn**|Включает профилирование с помощью метода выборки. Не включает профилирование выделения памяти или сбор данных о времени существования объектов.|
|**SampleGC**|Включает профилирование выделения памяти с помощью метода выборки. Не включает сбор данных о времени существования объектов.|
|**SampleGCLife**|Включает профилирование выделения памяти с помощью метода выборки. Также включает сбор данных о времени существования объектов.|
|**SampleLineOff**|Отключает сбор данных профилирования на уровне строк кода .NET.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Параметры VSPerfCLREnv для глобального профилирования

Чтобы выполнить профилирование управляемой службы, например веб-приложения ASP.NET, которое запускается не пользователем, а операционной системой, используйте параметры средства VSPerfCLREnv, предназначенные для глобального профилирования. В таблице ниже приведены глобальные версии параметров VSPerfCLREnv. Эти параметры задают соответствующие переменные среды в реестре.

|Параметр|Описание:|
|------------|-----------------|
|**GlobalTraceOn**|Включает глобальное профилирование с помощью метода инструментирования. Не включает сбор событий выделения памяти или данных о времени существования объектов.|
|**GlobalTraceGC**|Включает глобальное профилирование выделения памяти с помощью метода инструментирования. Не включает сбор данных о времени существования объектов.|
|**GlobalTraceGCLife**|Включает глобальное профилирование выделения памяти с помощью метода инструментирования. Также включает сбор данных о времени существования объектов.|
|**GlobalSampleOn**|Включает глобальное профилирование с помощью метода выборки. Не включает сбор событий выделения памяти или данных о времени существования объектов.|
|**GlobalSampleGC**|Включает глобальное профилирование выделения памяти с помощью метода выборки. Не включает сбор данных о времени существования объектов.|
|**GlobalSampleGCLife**|Включает глобальное профилирование выделения памяти с помощью метода выборки. Также включает сбор данных о времени существования объектов.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Параметры VSPerfCLREnv для удаления переменных среды

 После завершения профилирования управляемого приложения можно использовать один из приведенных ниже параметров для удаления переменных среды, которые были добавлены средством VSPerfCLREnv. В таблице ниже представлены параметры удаления обычных и глобальных переменных среды.

|Параметр|Описание:|
|------------|-----------------|
|**Off**|Удаляет переменные среды для обычного профилирования .NET. Этот параметр необходимо использовать, если для задания переменных среды профилировщика используются неглобальные параметры VSPerfClrEnv.|
|**GlobalOff**|Удаляет переменные среды для глобального профилирования .NET. Этот параметр следует использовать, если приложение запускается не профилировщиком, а операционной системой.|

## <a name="remarks"></a>Примечания

Если приложение запускается с помощью обозревателя производительности интегрированной среды разработки, эти параметры не требуются для профилирования управляемых приложений. Обозреватель производительности устанавливает все необходимые параметры среды автоматически.

Если при профилировании не была задана правильная среда, то во время анализа выводится предупреждение, а имена управляемых функций будут разрешаться неверно.

## <a name="see-also"></a>См. также

[Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)