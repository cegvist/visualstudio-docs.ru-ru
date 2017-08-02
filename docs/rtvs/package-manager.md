---
title: "Диспетчер пакетов в инструментах R для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93accb9a-1ef8-4806-baa4-02477c2d7ef0
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: a0bc08a5b4e38651e8d62629778e3ab1647e1bcb
ms.contentlocale: ru-ru
ms.lasthandoff: 05/12/2017

---


# <a name="package-manager"></a>Диспетчер пакетов

Диспетчер пакетов в инструментах R для Visual Studio (RTVS) — это пользовательский интерфейс для управления пакетами R. Чтобы открыть его, выберите **Инструменты R > Окна > Пакеты** или нажмите клавиши CTRL + 7.

В диспетчере пакетов имеется три вкладки, как описано ниже. На всех вкладках отображаются списки соответствующих пакетов (слева) и определенные сведения о выбранном пакете (справа), включая версию пакета, описание, сведения о лицензии, расположении установки пакета, а также ссылки на другие важные сведения. С помощью поля поиска в правом верхнем углу можно сортировать список.

> [!Tip]
> Текст в поле поиска сохраняется при переключении между вкладками.

- **Доступные** — список пакетов для установки. Если пакет уже установлен, кнопка **Установить** справа изменится на **Удалить**.

    ![Вкладка доступных пакетов в диспетчере пакетов в инструментах R для Visual Studio](~/rtvs/media/package-manager-available.png)

- **Установленные** — список всех установленных и загруженных пакетов. Зеленая точка рядом с пакетом указывает на то, что пакет загружен в сеанс R. Чтобы удалить пакет, воспользуйтесь красным значком X слева или кнопкой **Удалить** справа. Синяя стрелка вверх справа от установленного пакета указывает на то, что доступна новая версия этого пакета.

    ![Вкладка установленных пакетов в диспетчере пакетов в инструментах R для Visual Studio](~/rtvs/media/package-manager-installed.png)

- На вкладке **Загруженные** отображаются только те пакеты, которые загружены в сеанс R, поэтому для всех таких пакетов отображаются зеленые точки. Здесь можно также удалить и обновить пакеты.

    ![Вкладка загруженных пакетов в диспетчере пакетов в инструментах R для Visual Studio](~/rtvs/media/package-manager-loaded.png)

## <a name="package-locations"></a>Расположения пакетов

Пакеты устанавливаются в следующие расположения.

- Основные пакеты, которые входят в состав RTVS, устанавливаются в каталог `C:\Program Files\Microsoft\R Client\R_SERVER\library`
- Дополнительные пакеты устанавливаются в каталог `%userprofile%\Documents\R\win-library\3.3`
