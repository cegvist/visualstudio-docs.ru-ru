---
title: "Таблица объектов графики | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb03ab88ca3d1d50b559cef87bfdf045a0a81319
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-object-table"></a>Таблица графических объектов
Таблица графических объектов в компоненте анализа графики Visual Studio помогает разобраться в работе объектов Direct3D, которые поддерживают кадр вашей игры или вашего приложения.  
  
 Таблица объектов выглядит так:  
  
 ![Объекты Direct3D, которые были созданы приложения.](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Основные сведения о таблице графических объектов  
 С помощью таблицы объектов можно анализировать объекты Direct3D, поддерживающие отрисовку определенного кадра. Можно проследить проблему отрисовки до конкретного объекта, анализируя его свойства и данные (с помощью других инструментов диагностики графики можно сузить список объектов, функции которых могут отличаться от ожидаемых). Если вы нашли выявив объект, можно использовать визуализацию, относящиеся к типу, чтобы изучить его — например, можно использовать редактор изображений для просмотра текстур или *визуализатор буфера* для просмотра содержимого буфера.  
  
 Таблица объектов поддерживает операции копирования и вставки, поэтому для анализа ее содержимого можно использовать другое средство, например Microsoft Excel.

 Кроме того, можно использовать **тип** раскрывающемся списке в верхнем левом углу для переключения просмотра объектов типа **буферы**, **шейдеров** или **текстур**, или все эти элементы за один раз.  Кроме того можно использовать поле поиска в правом верхнем углу для поиска определенных строк для всех данных, представленных.  Например, можно выполнить поиск *D32_FLOAT* для поиска всех экземпляров объектов этого формата в списке.
  
### <a name="graphics-object-table-format"></a>Формат таблицы графических объектов  
 Таблица объектов отображает ресурсы и объекты Direct3D, которые поддерживают кадр, связанный с выбранным событие, например, объекты состояния, буферы, шейдеры, текстуры и другие ресурсы. Объекты, которые были созданы в предыдущем кадре, но не используются во время захваченного кадра, не приводятся в таблице объектов. Объекты, которые были уничтожены предыдущими событиями во время захваченного кадра, в последующих событиях опускаются. Объекты, которые не установлены в D3D10Device или D3D11DeviceContext, отображаются серым текстом. Объекты отображаются в виде таблицы.  
  
|Столбец|Описание:|  
|------------|-----------------|  
|**Идентификатор**|Идентификатор объекта.|  
|**Name**|Сведения, относящиеся к приложению и заданные в объекте с помощью функции Direct3D `SetPrivateData`. Обычно служат для предоставления дополнительных идентификационных сведений об объекте.|  
|**Type**|Тип объекта.|  
|**Активный**|Содержит "*" для объекта, который был установлен в D3D10Device или D3D11DeviceContext во время захваченного кадра.<br /><br /> Это соответствует объектам, которые отображаются серым текстом, но с помощью этой записи в столбце можно сортировать таблицу объектов.|  
|**Size**|Размер объекта в байтах.|  
|**Формат**|Формат объекта. Например, формат объекта текстуры или модель шейдера объекта шейдера.|  
|**Ширина**|Ширина объекта текстуры. Не распространяется на другие типы объектов.|  
|**Высота**|Высота объекта текстуры. Не распространяется на другие типы объектов.|  
|**Глубина**|Глубина объекта трехмерной текстуры. Если текстура не является трехмерной, значение равно нулю. Не распространяется на другие типы объектов.|  
|**MIPS**|Количество уровней MIP у объекта текстуры. Не распространяется на другие типы объектов.|  
|**ArraySize**|Число текстур в массиве текстур. Диапазон включает в себя значения от 1 до верхней границы, определенной текущим функциональным уровнем. Для кубической карты это значение в 6 раз больше числа кубических карт в массиве.|  
|**Примеры**|Число мультисэмплингов на пиксель.|  
  
## <a name="graphics-object-viewers"></a>Средства просмотра объектов графики  
 Для просмотра сведений об объекте откройте его, выбрав его имя в таблице объектов. Сведения об объекте отображаются в различных форматах в зависимости от типа объекта. Например, текстуры отображаются с помощью средства просмотра текстур, а состояние устройства, такое как контекст устройства D3D11, отображается в виде форматированного списка. Различные версии Direct3D используют разные объекты, и часто для наиболее важных объектов каждой из версий применяются специальные визуализаторы.  
  
 Здесь показано средство просмотра текстур, в котором отображается содержимое этапа конвейера средства слияния вывода.  
  
 ![Предварительная версия текстуры, отображающая слияние выходных данных](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>Список команд D3D12  
 В Direct3D 12 список команд — это объект, который записывает команды в распределитель команд, чтобы их можно было отправлять в GPU в виде одного запроса. Списки команд обычно выполняют последовательность команд для задания состояния, рисования, очистки и копирования. Они особенно важны, так как являются предпочтительным методом отрисовки в Direct3D 12 и могут повторно использоваться между кадрами для повышения производительности. Сведения о списке команд отображаются в окне нового документа, а информация, связанная с каждым этапом конвейера, отображается на отдельной вкладке.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>Объект состояния конвейера D3D12  
 В Direct3D 12 объект состояния конвейера представляет значительную часть состояния GPU, включая все заданные в данный момент шейдеры и отдельные объекты состояния с фиксированной функциональностью. После создания объект состояния конвейера является неизменяемым — приложение может изменять конфигурацию конвейера только путем привязки другого объекта состояния конвейера. Сведения об объекте состояния конвейера отображаются в окне нового документа, а информация о конфигурации конвейера упорядочивается по уровням иерархии.  
  
### <a name="d3d12-root-signature"></a>Сигнатура корня D3D12  
 В Direct3D 12 сигнатура корня определяет все ресурсы, привязанные к графическому или вычислительному конвейеру, и связывает списки команд с ресурсами, необходимыми шейдерам. Обычно в приложении используется одна сигнатура корня для графики и одна для вычислений. Сведения о сигнатуре корня отображаются в новом окне документа, при этом данные сведения упорядочивается по уровням иерархии.  
  
### <a name="d3d12-resources"></a>Ресурсы D3D12  
 В Direct3D 12 ресурсы представляют собой объекты, предоставляющие данные конвейеру отрисовки; это существенно отличается от ситуации с Direct3D11, где определялось множество отдельных объектов для разных видов и измерений ресурсов. Ресурс Direct3D 12 может содержать данные текстуры, данных вершин, данные шейдеров и многое другое, он даже может представлять целевые объекты отрисовки, такие как буфер глубины. Сведения о ресурсе Direct3D 12 отображаются в новом окне документа. Компонент анализа графики будет использовать соответствующее средство просмотра для содержимого объекта ресурса, если сможет определить его тип. Например, объект ресурса, который содержит данные текстуры, отображаются с использованием средства просмотра текстур, как и объект Texture2D D3D11.  
  
### <a name="device-context-object"></a>Объект контекста устройства  
 В Direct3D 11 и Direct3D 10 объект контекста устройства (**контекст устройства D3D11** или **устройство D3D10**) особенно важен, поскольку он содержит наиболее важную информацию о состоянии, и приводятся ссылки на другой состояние объектов, заданных в настоящее время. Сведения о контексте устройства приводятся в новом окне документа, а каждая категория сведений представлена на отдельной вкладке. Контекст устройства изменяется при выборе нового события в соответствии с текущим состоянием устройства.  
  
### <a name="buffer-object"></a>Объект буфера  
 Данные объекта буфера (буфер D3D11 или буфер D3D10) приводятся в новом окне документа, в котором в таблице представлено содержимое буфера и предоставлен интерфейс для изменения способа его отображения. **Помещать в буфер данные** поддерживает копирование и вставка, чтобы можно было использовать другое средство, например Microsoft Excel, для просмотра ее содержимого. Содержимое буфера интерпретируется согласно значению **формат** со списком, расположенную над **помещать в буфер данные** таблицы. В этом поле можно ввести составной формат данных, который состоит из типов данных, перечисленных ниже в таблице. Например, "float int" выводит список структур, содержащих 32-разрядное значение с плавающей запятой, за которым следует 32-разрядное целое число со знаком. Указанные составные форматы данных добавляются в поле со списком для последующего использования.  
  
 Вы можете включать и выключать **Показать смещения** флажок, чтобы скрыть или отобразить смещение каждого элемента в буфере.  
  
|Тип|Описание:|  
|----------|-----------------|  
|**float**|32-разрядное значение с плавающей запятой.|  
|**float2**|Вектор, содержащий два 32-разрядных значения с плавающей запятой.|  
|**float3**|Вектор, содержащий три 32-разрядных значения с плавающей запятой.|  
|**float4**|Вектор, содержащий четыре 32-разрядных значения с плавающей запятой.|  
|**byte**|8-разрядное целое значение со знаком.|  
|**2-байтовая**|16-разрядное целое значение со знаком.|  
|**4-байтовым**|32-разрядное целое значение со знаком. То же, что **int**.|  
|**8-байтовую**|64-разрядное целое значение со знаком. То же, что **int64**.|  
|**xbyte**|8-разрядное шестнадцатеричное значение.|  
|**x2byte**|16-разрядное шестнадцатеричное значение.|  
|**x4byte**|32-разрядное шестнадцатеричное значение. То же, что **xint**.|  
|**x8byte**|64-разрядное шестнадцатеричное значение. То же, что **xint64**.|  
|**ubyte**|8-разрядное целочисленное значение без знака.|  
|**u2byte**|16-разрядное целочисленное значение без знака.|  
|**u4byte**|32-разрядное целочисленное значение без знака. То же, что **uint**.|  
|**u8byte**|64-разрядное целочисленное значение без знака. То же, что **uint64**.|  
|**половина**|16-разрядное значение с плавающей запятой.|  
|**half2**|Вектор, содержащий два 16-разрядных значения с плавающей запятой.|  
|**half3**|Вектор, содержащий три 16-разрядных значения с плавающей запятой.|  
|**half4**|Вектор, содержащий четыре 16-разрядных значения с плавающей запятой.|  
|**double**|64-разрядное значение с плавающей запятой.|  
|**int**|32-разрядное целое значение со знаком. То же, что **4-байтовым**.|  
|**Int64**|64-разрядное целое значение со знаком. То же, что **размером 8 байт**.|  
|**XINT**|32-разрядное шестнадцатеричное значение. То же, что **x4byte**.|  
|**xint64**|64-разрядное шестнадцатеричное значение. То же, что **x8byte**.|  
|**uint**|32-разрядное целочисленное значение без знака. То же, что **u4byte**.|  
|**UInt64**|64-разрядное целочисленное значение без знака. То же, что **u8byte**.|  
|**bool**|Логическое значение (`true` или `false`). Каждое значение логического типа представлено 32-разрядным значением.|  
  
## <a name="see-also"></a>См. также  
 [Диагностика графики (Отладка графики DirectX)](visual-studio-graphics-diagnostics.md)   
 [Пошаговое руководство. Отсутствие объектов вследствие состояния устройства](walkthrough-missing-objects-due-to-device-state.md)