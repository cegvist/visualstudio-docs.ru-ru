---
title: "Функция SccBackgroundGet | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b63a7e8c9a6b2a4f2539cd6a8426ba9df365ab76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccbackgroundget-function"></a>Функция SccBackgroundGet
Эта функция извлекает из системы управления версиями каждого из указанных файлов без вмешательства пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nFiles  
 [in] Число файлов, указанных в `lpFileNames` массива.  
  
 lpFileNames  
 [in, out] Массив имен файлов, которые требуется получить.  
  
> [!NOTE]
>  Имена должны быть полным локальные имена файлов.  
  
 dwFlags  
 [in] Команда флаги (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Уникальное значение, связанное с данной операцией.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Операция успешно завершена.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Получение фона уже выполняется (подключаемый модуль системы управления версиями должна возвращать это только в том случае, если он не поддерживает одновременное пакетных операций).|  
|SCC_I_OPERATIONCANCELED|Операция отменена до завершения.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция всегда вызывается в потоке, отличном от того, в который загружен подключаемый модуль системы управления версиями. Эта функция не должен вернуть до завершения; Тем не менее он может вызываться несколько раз с несколькими списками файлов, для всех одновременно.  
  
 Использование `dwFlags` аргумент совпадает со значением [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)