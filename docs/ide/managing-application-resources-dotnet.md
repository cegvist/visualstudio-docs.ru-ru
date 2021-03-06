---
title: "Управление ресурсами приложения (.NET) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2006f565edbca8a859cd2c155645e47e083b5528
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="managing-application-resources-net"></a>Управление ресурсами приложения (.NET)

Файлы ресурсов — это файлы, которые являются частью приложения, но не компилируются, например файлы значков или звуковые файлы. Так как они не включаются в процесс компиляции, их можно изменять, не компилируя повторно двоичные файлы. Если вы планируете локализовать приложение, файлы ресурсов следует использовать для всех строк и других ресурсов, которые потребуется изменить при локализации.

Более подробную информацию о ресурсах в классических приложениях .NET см. в разделе [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="working-with-resources"></a>Работа с ресурсами

В проекте управляемого кода откройте окно свойств проекта. Для этого вы можете:

- щелкнуть правой кнопкой мыши узел проекта в **обозревателе решений** и выбрать пункт **Свойства**;
- ввести фразу "свойства проекта" в окне **Быстрый запуск**;
- нажать клавиши **ALT**+**ВВОД** в окне **обозревателя решений**.

Перейдите на вкладку **Ресурсы** . Вы можете добавить файл RESX, если проект его еще не содержит, добавить и удалить различные типы ресурсов, а также изменить существующие ресурсы.

## <a name="resources-in-other-project-types"></a>Ресурсы в других типах проектов

Управление ресурсами в проектах .NET осуществляется не так, как в проектах других типов. Дополнительные сведения о ресурсах:

- приложения универсальной платформы Windows (UWP) — [Ресурсы приложения и система управления ресурсами](/windows/uwp/app-resources/);
- проекты C++ — [Работа с файлами ресурсов](/cpp/windows/working-with-resource-files) и [Практическое руководство. Создание ресурса](/cpp/windows/how-to-create-a-resource).

## <a name="see-also"></a>См. также

[Ресурсы в приложениях для настольных систем (.NET Framework)](/dotnet/framework/resources/index)