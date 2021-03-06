---
title: "Общие сведения о развертывании - Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e05bf361515b45f3ebc7683fa0c83ec6116d9419
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="deployment-overview-in-visual-studio"></a>Общие сведения о развертывании в Visual Studio

Развертывание приложения, службы или компонента — это механизм их распространения для установки на других компьютерах, устройствах, серверах и в облаке. В Visual Studio можно выбрать соответствующий подход в зависимости от требуемого типа развертывания. (Такие как развертывание командной строки и NuGet другими средствами развертывания, не описанные здесь поддерживают множество типов приложений.)

Учебники по пошаговые инструкции в разделе.

### <a name="deploy-to-local-folder"></a>Развернуть локальную папку

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, и **.NET Core**: средство публикации для развертывания на локальный папка. Параметры, доступные зависят от типа приложения. В обозревателе решений щелкните правой кнопкой мыши проект и выберите команду **публикации**, а затем выберите **папки**. Дополнительные сведения см. в разделе [развернуть локальную папку](quickstart-deploy-to-local-folder.md).

    ![Выберите опубликовать](../deployment/media/quickstart-publish.png)

- **Среда выполнения Visual C++**: вы можете развернуть среду выполнения Visual C++ с помощью локальное развертывание или статическое связывание. Дополнительные сведения см. в разделе [развертывание собственного приложения для настольных компьютеров (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

### <a name="publish-to-web-or-deploy-to-network-share"></a>Публикация в Интернете или развернуть на сетевом ресурсе

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, и **.NET Core**: можно использовать средство публикации для развертывания веб-сайт через FTP или веб-развертывания. Дополнительные сведения см. в разделе [развертывание на веб-сайт](quickstart-deploy-to-a-web-site.md).

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**. В средство публикации выберите параметр требуется и выполните шаги настройки.

    ![Выберите IIS, FTP и т. д.](../deployment/media/quickstart-publish-iis-ftp.png)

    Можно также развернуть приложений ASP.NET и служб в ряд других способов. Дополнительные сведения см. в разделе [ASP.NET развертывание веб-приложений и служб](http://www.asp.net/aspnet/overview/deployment).

- **Среда выполнения Visual C++**: вы можете развернуть среду выполнения Visual C++ с использованием центрального развертывания. Дополнительные сведения см. в разделе [развертывание собственного приложения для настольных компьютеров (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Рабочий стол Windows** можно опубликовать классическое приложение Windows на веб-сервере или в сетевой общей папке, с помощью развертывания ClickOnce. Затем пользователи смогут устанавливать приложение одним щелчком. Дополнительные сведения см. в разделе [развертывание классического приложения с помощью ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) и [развернуть собственное приложение с помощью ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

### <a name="publish-to-azure"></a>Публикация в Azure

- **ASP.NET, ASP.NET Core, Python, Node.js и .NET Core** веб-приложения: можно использовать средство публикации для быстрого развертывания приложений в службе приложений Azure или к виртуальной машине Azure. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**. В диалоговом окне «публикация» выберите **службу приложений Microsoft Azure** или **виртуальные машины Microsoft Azure**, а затем выполните действия по настройке.

    ![Выберите службы приложений Azure](../deployment/media/quickstart-publish-azure.png "выберите службы приложений Azure")

    Чтобы опубликовать к виртуальной машине Azure, прокрутите вправо и выберите **виртуальные машины Microsoft Azure**.

    Краткие сведения см. в разделе [опубликовать в Azure](quickstart-deploy-to-azure.md). Кроме того, в разделе [публикация приложений ASP.NET Core для Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Развертывания с помощью Git см. в разделе [непрерывного развертывания ASP.NET Core в Azure с помощью Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Если вы еще нет учетной записи Azure, вы можете [регистрации здесь](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

- Другие **служб Azure**: см. конкретный [службы Azure](/azure/#pivot=products) документации для разных вариантов развертывания, поддерживаемый Visual Studio.

### <a name="publish-to-microsoft-store"></a>Публикация в Microsoft Store

Из Visual Studio можно создать пакеты приложения для развертывания в Microsoft Store.

- **UWP**: можно упаковать приложение и развернуть ее с помощью пунктов меню. Дополнительные сведения см. в разделе [упаковать приложение UWP, с помощью Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Создание пакета приложения](../deployment/media/feature-tour-create-app-package.jpg)

- **Рабочий стол Windows**: можно развернуть в Microsoft Store с помощью моста Desktop начиная с версии 15.4 2017 г. Visual Studio. Чтобы сделать это, начните с создания проекта упаковки приложения Windows. Дополнительные сведения см. в разделе [пакета классического приложения для магазина Microsoft (рабочий стол мост)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Мост рабочего стола](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>Создание пакета установщика (клиент Windows)

- Установщик MSI-based WiX можно создать с помощью [2017 г. расширение WiX набора средств Visual Studio](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) из Flexera программного обеспечения, могут быть использованы с Visual Studio 2017 г. (Community Edition не поддерживается). Обратите внимание, что InstallShield Limited Edition больше не входят в состав Visual Studio не поддерживается в Visual Studio 2017 г.; Уточните [программного обеспечения Flexera](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) о будущих доступности.

- Если вы хотите создать проект установки (vdproj), установите [проекты установщика Visual Studio 2017 г. расширение](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Можно установить необходимые компоненты для настольных приложений путем настройки универсального установщика, также называемого загрузчиком. Дополнительные сведения см. в разделе [необходимые условия для развертывания приложения](../deployment/application-deployment-prerequisites.md).

### <a name="deploy-to-test-lab"></a>Развертывание в тестовой лаборатории

Можно включить более сложную разработку и тестирование путем развертывания приложений в виртуальных средах. Дополнительные сведения см. в разделе [тестов в лабораторной среде](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

### <a name="devops-deployment"></a>DevOps развертывания

В среде рабочей группы Visual Studio Team Services (VSTS) можно использовать для обеспечения непрерывного развертывания приложения. Дополнительные сведения см. в разделе [сборок и выпусков](/vsts/build-release/index) и [развертыванию в Azure](/vsts/deploy-azure/index).

### <a name="deployment-for-other-app-types"></a>Развертывание для других типов приложений

| Тип приложения | Сценарий развертывания | Ссылка |
| --- | --- | --- |
| **Приложения Office** | Можно опубликовать надстройку для Office в Visual Studio. | [Развертывание и публикация надстройки Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Службы WCF или OData**  | Другие приложения могут использовать службы WCF RIA, развертываемые на веб-сервере. | [Разработка и развертывание служб данных WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch не поддерживается в Visual Studio 2017 г., но по-прежнему могут развертываться из Visual Studio 2015 и более ранних версий. | [Развертывание приложений LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

