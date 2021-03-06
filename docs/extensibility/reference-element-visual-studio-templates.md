---
title: "Ссылаться на элемент (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1006e85611044805c0f3bd1e0035595288a5b32d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="reference-element-visual-studio-templates"></a>Элемент Reference (шаблоны Visual Studio)
Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Ссылки на >  
 \<Ссылка >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Указывает сведения о сборке, используемые шаблоном для добавления в проекты ссылки на эту сборку. Должен существовать один `Assembly` элемент в каждом `Reference` элемент.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Ссылки](../extensibility/references-element-visual-studio-templates.md)|Группы ссылок на сборки, которые добавляются в проекты.|  
  
## <a name="remarks"></a>Примечания  
 `Reference` — обязательный дочерний элемент элемента `References`.  
  
 `Reference` И `References` элементы могут использоваться только в VSTEMPLATE-файлах, имеющих `Type` значение атрибута `Item`.  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется `TemplateContent` элемента шаблона элемента. Этот XML-код добавляет ссылки на сборки System.dll и System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)