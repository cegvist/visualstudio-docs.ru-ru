---
title: "Класс VsgDbg | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e1a3810f6f0c2de6bffb2f97c2f1fc446ea3b6d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdbg-class"></a>Класс VsgDbg
Представляет интерфейс для программного управления компонента диагностики графики в приложении.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Участники  
 `VsgDbg` Класс поддерживает следующие члены.  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (конструктор)](vsgdbg-vsgdbg-constructor.md)|Создает экземпляр класса `VsgDbg` класса и при необходимости подготавливает компонент диагностики графики для активного захвата и записи данных графики в приложении.|  
|[VsgDbg::~VsgDbg (деструктор)](vsgdbg-tilde-vsgdbg-destructor.md)|Удаляет экземпляр `VsgDbg` класса.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Добавляет пользовательское сообщение диагностики графики Дисплей (Head).|  
|[BeginCapture](begincapture.md)|Начинается интервал захвата, будут заканчиваться `EndCapture`.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Захватывает оставшуюся часть текущего кадра в файл журнала графики.|  
|[Copy (программный захват)](copy-programmatic-capture.md)|Копирует содержимое активного файла журнала графики (.vsglog) в новый файл.|  
|[EndCapture](endcapture.md)|Завершает интервал захвата, начатый функцией `BeginCapture`.|  
|[Init](init.md)|Подготавливает компонент диагностики графики для активного захвата и записи данных графики в приложении.|  
|[ToggleHUD](togglehud.md)|Переключает наложение HUD диагностики графики, или отключить.|  
|[UnInit](uninit.md)|Финализирует файл журнала графики, закрывает его и освобождает все ресурсы, которые использовались во время активной записи данных графики приложением.|  
  
## <a name="remarks"></a>Примечания  
 `VsgDbg` Класс представляет интерфейс, который можно использовать для управления функциями диагностики графики программными средствами. Можно использовать некоторые возможности, даже в том случае, если вы не активно захвата и записи данных графики; Сюда входят `AddMessage` функции-члена и `ToggleHUD` функции-члена. Другие функции-члены подготовки компонента диагностики графики, чтобы запустить или остановить активный захвата графических данных в приложении, либо должен вызываться во время активного захвата и записи данных графики в файл журнала графики приложения.