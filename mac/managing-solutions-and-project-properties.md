---
title: "Управление свойствами проекта и решения | Документы Майкрософт"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: eac94a70cdfac556fce6e04188ab24c5102eab25
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="managing-project-and-solution-properties"></a>Управление свойствами проекта и решения

## <a name="project-options"></a>Параметры проекта

Параметры проекта задаются для каждого проекта и влияют на его запись, сборку и выполнение. Они отличаются от настроек Visual Studio для Mac (которые задают пользовательские параметры) и параметров решения (которые задают параметры для всего решения). Параметры проекта хранятся в файле проекта (CSPROJ), чтобы другие разработчики могли собирать и запускать проект правильно. Наличие параметров для конкретного проекта позволяет нескольким разработчикам работать с одним документом без нарушения форматирования файла.

Чтобы открыть параметры проекта в Visual Studio для Mac, дважды щелкните имя проекта или щелкните правой кнопкой мыши и выберите элемент **Параметры**:

 ![Параметр в контекстном меню](media/projects-and-solutions-image2.png)

Для изменения доступны параметры для сборки, запуска и настройки исходного кода, а также параметры управления версиями.

Параметры проекта упорядочены по пяти разным категориям:

* **Общие**— позволяет задать сведения о проекте, такие как имя, описание и пространство имен по умолчанию, а также расположение проекта.
* **Сборка** — позволяет разработчикам задать или изменить профили PCL для переносимых библиотек классов. Она также позволяет задать пользовательские команды, конфигурации и параметры компилятора. Кроме того, здесь можно указать выходной путь и имя сборки.
* **Запуск** — позволяет создавать пользовательские конфигурации запуска отдельно для каждого проекта.
* **Исходный код** — позволяет управлять форматированием многих разных типов файлов и соглашений об именовании. Здесь также можно задать политики именования и стили заголовков по умолчанию.
* **Управление версиями** — позволяет изменить стиль сообщения фиксации при использовании управления версиями для проекта.

Каждый проект может содержать отдельные параметры, зависящие от платформы. Например, проект Xamarin.Android, аналогичный показанному на следующем рисунке, будет иметь параметры, связанные со сборкой Android, например параметры компоновщика, и приложением, например разрешения:

 ![Параметры проекта Android](media/projects-and-solutions-image5.png)

Xamarin.iOS содержит параметры, связанные с подписыванием пакета, например требуемый профиль подготовки:

 ![Параметры проекта iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Параметры решения 

Параметры решения аналогичны параметрам проекта, только распространяются на все решение. Они позволяют указать сведения об авторе, параметры сборки, стили форматирования кода, настроить управление версиями, а также назначить запускаемый проект в решении.  Диалоговое окно параметров решения можно открыть с помощью элемента меню **Проект > Параметры решения**, пункта контекстного меню **Параметры** на панели решения, а также дважды щелкнув решение на панели решения:

 ![Параметры решения](media/projects-and-solutions-image7.png)
