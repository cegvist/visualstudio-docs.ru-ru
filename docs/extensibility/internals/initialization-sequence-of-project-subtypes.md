---
title: "Последовательность инициализации подтипов проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: db259b7bc5f9935b229f4f6522ae14a4496f0e15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="initialization-sequence-of-project-subtypes"></a>Последовательность инициализации подтипов проекта
Среда создает проект путем вызова реализации базового проекта фабрики <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Построение проекта подтипа начинается, когда среда определяет, что список GUID типа проекта для расширения файла проекта не является пустым. Расширение файла проекта и идентификатор GUID проекта укажите, является ли проект [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] или [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] тип проекта. Например, расширение VBPROJ-файлу и {F184B08F-C81C-45F6-A57F-5ABD9991F28F} идентификации [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проекта.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Инициализация среды подтипов проекта  
 В следующей процедуре подробно последовательность инициализации для системы проектов, упорядоченные по несколько подтипов проекта.  
  
1.  Окружение вызывает базовый проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, и обнаруживает во время проекта анализирует его файл проекта не является тип статистической проекта списка идентификаторов GUID `null`. Проект прекращает напрямую создания своего проекта.  
  
2.  Вызовы проекта `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> службы для создания подтипом проекта, используя реализацию интерфейса среды <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> метод. В этом методе среды делает рекурсивных вызовов функций для реализации методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` и <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> идентификаторы GUID, начиная с подтипом проекта внешней введите методы, пока он проход по списку проекта.  
  
     Ниже описаны шаги инициализации.  
  
    1.  Реализация интерфейса среды <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> вызовы методов "HrCreateInnerProj'' ' метод со следующим объявлением функции:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         Когда эта функция вызывается в первый раз, т. е для подтип внешней проекта параметры `pOuter` и `pOwner` передаются в качестве `null` и функция задает подтип внешней проекта `IUnknown` для `pOuter`.  
  
    2.  Затем среда вызывает `HrCreateInnerProj` функцию с второй GUID типа проекта в списке. Этот идентификатор GUID соответствует второй подтип внутреннего проекта, шаг с заходом сторону базового проекта в последовательности статистической обработки.  
  
    3.  `pOuter` Теперь указывает `IUnknown` подтипа внешней проекта и `HrCreateInnerProj` вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> после вызова реализации метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> метод передать управление `IUnknown` подтипа внешней проекта `pOuter`. Собственный проект (подтипом внутреннего проекта) должен создать его объекта aggregate проекта. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> передать указатель на реализацию метода `IUnknown` внутреннего проекта, который выполняется статистическая обработка. Эти два метода создания объекта статистической обработки и реализации должны следовать правилам COM статистической обработки, чтобы убедиться, что подтипом проекта не попадут удерживающие значение счетчика ссылок на себя.  
  
    4.  `HrCreateInnerProj`вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. В этом методе подтипом проекта выполняет свой код инициализации. Можно например, регистрировать события решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
    5.  `HrCreateInnerProj`вызывается рекурсивно, пока не будет достигнут последний идентификатор GUID (базовый проект) в списке. Для каждого из этих вызовов шаги c-d, повторяются. `pOuter`Указывает подтип внешней проекта `IUnknown` для каждого уровня статистической обработки.  
  
 В следующем примере подробно программный процесс в приблизительное представление <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> метод, как оно реализуется с помощью среды. Код всего лишь пример; он не предназначен для компиляции и проверки всех ошибок был удален для ясности.  
  
## <a name="example"></a>Пример  
  
### <a name="code"></a>Код  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)