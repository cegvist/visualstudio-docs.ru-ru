---
title: "IPropertyProxyEESide::CreateReplacementObject | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 958b34ea15fdbfda4c98979fec3ce7210183d921
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Создает копию объекта данных для оценки выражений (EE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, содержащий данные для копирования.  
  
 `dataOut`  
 [out] Возвращает новый `IEEDataStorage` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод получает [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, представляющий массив байтов. Это входящего объекта данных обычно не реализуют EE. Тем не менее, возвращаемый этим методом объект всегда реализуется EE, которая позволяет реализовать EE `IEEDataStorage` интерфейс требуемого любой класс.  
  
 Обратите внимание, что данные предоставляются во входящем `IEEDataStorage` объект должен иметь те же данные в исходящий `IEEDataStorage` объекта.  
  
## <a name="see-also"></a>См. также  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)