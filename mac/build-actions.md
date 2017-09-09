---
title: "Действия при сборке"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 347378da197b5c6d22bbd145c2ac8673d53a63bf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/11/2017

---

# <a name="build-actions"></a>Действия при сборке 

Все файлы в проекте Visual Studio для Mac имеют действие при сборке, которое определяет, что происходит с файлом во время сборки. Его можно настроить, щелкнув правой кнопкой мыши любой файл и выбрав **Действие при сборке**, как показано ниже:

![](media/projects-and-solutions-image1.png)

Ниже приведены некоторые распространенные действия при сборке для проектов C#:

* **None** — файл не является частью сборки, он включен в проект лишь для упрощения доступа из интегрированной среды разработки.
* **Compile** — файл будет передан компилятору C# в виде файла кода.
* **EmbeddedResource** — файл будет передан компилятору C# в виде ресурса, внедряемого в сборку. После этого можно использовать пространство имен `System.Reflection` для чтения файл из сборки.
* **Content** — для проектов ASP.NET эти файлы будут включены в состав сайта при его развертывании. Для проектов Xamarin.iOS и Xamarin.Mac они будут находиться в пакете приложений.

Можно выбрать несколько файлов в обозревателе решений, чтобы задать действие при сборке сразу для большого числа файлов.

Кроме того, существуют действия при сборке для конкретных проектов. Например, проекты Xamarin.iOS имеют действие при сборке **BundeledResource**, которое добавляет файл как часть набора приложений. Сведения о действиях при сборке для Xamarin.Android см. в руководстве по [процессу сборки](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions) на сайте developer.xamarin.com.