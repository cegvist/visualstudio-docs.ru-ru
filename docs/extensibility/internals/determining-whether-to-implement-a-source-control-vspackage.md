---
title: "Определения, следует ли реализовать VSPackage управления источника | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 88281496c2e8350f910feda7934e2b55a494243b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Определения, следует ли реализовать VSPackage исходного элемента управления
В данном разделе описываются варианты подключаемые модули управления версиями и система управления версиями пакетов VSPackage для расширения решений и предоставляет общие рекомендации о выборе пути подходящий интеграции системы управления версиями.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Решение для управления небольшой версиями с ограниченными ресурсами  
 Если ограниченными ресурсами и не может быть burdened с издержками записи пакета управления версиями, можно создать на основе API подключаемых модулей для управления источника подключаемых модулей. Это позволяет работать параллельно с пакетами управления источника и переключении между подключаемые модули управления версиями и пакеты по требованию. Дополнительные сведения см. в разделе [регистрации и выбора](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Решение для управления большими исходными с набором полнофункциональных функций  
 Если требуется реализовать решение для управления версиями, который предоставляет модель управления форматированного источника, адекватно не фиксируется с помощью API подключаемых модулей управления источника пакета управления версиями можно как путь интеграции. Это особенно в том случае, если исходный пакет адаптера управления (который взаимодействует с подключаемые модули управления версиями и предоставляет основные исходные элемент управления пользовательского интерфейса) вместо заменяемое собственными, что можно обрабатывать события элемента управления источника особым образом. Если уже имеется удовлетворительные источник элемента пользовательского интерфейса и хотите сохранить этот процесс в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], вариант пакета системы управления версиями позволяет делать это. Пакет системы управления версиями не является универсальным и предназначен исключительно для использования с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.  
  
 Если необходимо реализовать решение для управления версиями, который обеспечивает гибкость и расширенные контроль над логики управления источника и пользовательского интерфейса, можно указать маршрут интеграции пакета управления. Можно выполнить следующие действия.  
  
1.  Регистрация VSPackage собственной системе управления версиями (см. [регистрации и выбора](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Замените настраиваемого пользовательского интерфейса системы управления версиями по умолчанию пользовательского интерфейса (см. [собственный пользовательский интерфейс](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Укажите глифы для использования и обработки событий глиф в обозревателе решений (в разделе [управления глиф](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Обрабатывать события изменения запроса и сохранения запроса (см. [запроса изменить запрос Сохранить](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>См. также  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)