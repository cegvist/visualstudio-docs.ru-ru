---
title: "Функция SccRunScc | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4ad179325c4f34cd206a3c5e6b0840a69dd46037
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccrunscc-function"></a>Функция SccRunScc
Эта функция вызывает инструментом администрирования системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 nFiles  
 [in] Число файлов, указанных в `lpFileNames` массива.  
  
 lpFileNames  
 [in] Массив имен выбранного файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Средство администрирования source control был успешно вызван.|  
|SCC_I_OPERATIONCANCELED|Операция была отменена.|  
|SCC_E_INITIALIZEFAILED|Не удалось инициализировать систему управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов.|  
|SCC_E_CONNECTIONFAILURE|Не удалось подключиться к системе управления версиями.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция позволяет вызывающему объекту обращаться средство администрирования внешних полный спектр функций системы управления версиями. Если система управления версиями не имеет пользовательского интерфейса, подключаемый модуль системы управления версиями можно реализовать интерфейс для выполнения функций необходимые администрирования.  
  
 Эта функция вызывается с количеством и массив имен файлов для выбранных файлов. Если ее поддерживает средства администрирования, список файлов можно использовать для предварительного выбора файлов в интерфейсе администрирования; в противном случае список можно пропустить.  
  
 Эта функция обычно вызывается, когда пользователь выбирает **запуска \<сервера системы управления версиями >** из **файл** -> **системы управления версиями** меню. Это **запуска** меню можно всегда отключен или даже скрыть параметру реестра. В разделе [как: установить подключаемый модуль системы управления источника](../extensibility/internals/how-to-install-a-source-control-plug-in.md) подробные сведения. Эта функция вызывается только в том случае, если [SccInitialize](../extensibility/sccinitialize-function.md) возвращает `SCC_CAP_RUNSCC` бит функции (см. [флаги возможностей](../extensibility/capability-flags.md) подробные сведения об этом и других возможностей бит).  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Как: установить подключаемый модуль системы управления версиями](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Флаги возможностей](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)