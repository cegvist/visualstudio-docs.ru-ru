---
title: "Отладка примера кода HTML и CSS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1fc92029910b49692e055f165cdf8b93d13e3a05
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="debug-html-and-css-sample-code"></a>Отладка примера кода HTML и CSS
  
 В этом разделе код — это файл примера для [краткое руководство: отладка HTML и CSS](../debugger/quickstart-debug-html-and-css.md). Ошибки, намеренно допущенные в кратком руководстве, исправлены в этой версии кода.  
  
## <a name="sample-code"></a>Пример кода  
 Следующий код HTML используется в \<текст > тег в кратком руководстве.  
  
```html  
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
         style="display:none">  
    <div class="fixedItem" >  
        <img src="#" data-win-bind="src: flipImg" />  
    </div>  
</div>  
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{  
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
</div>  
```  
  
 В следующем коде CSS показаны добавления, сделанные в файл default.css.  
  
```css  
#fView {  
    background-color:#0094ff;  
    height: 500px;  
    margin: 25px;  
}  
```  
  
 В следующем примере кода показан выполненный код JavaScript в default.js. Ссылки на пространство имен WinJS для данного кода находятся в файле шаблона default.html.  
  
```javascript  
(function () {  
    "use strict";  
  
    var app = WinJS.Application;  
    var activation = Windows.ApplicationModel.Activation;  
  
    var myData = [];  
    for (var x = 0; x < 3; x++) {  
        myData[x] = { flipImg: "/images/logo.png" }  
    };  
  
    var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
    app.onactivated = function (args) {  
        if (args.detail.kind === activation.ActivationKind.launch) {  
            if (args.detail.previousExecutionState !==  
            activation.ApplicationExecutionState.terminated) {  
                // TODO: . . .  
            } else {  
                // TODO: . . .  
            }  
            args.setPromise(WinJS.UI.processAll());  
  
            updateImages();  
        }  
    };  
  
    function updateImages() {  
  
        pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });  
        pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });  
        pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });  
    };  
  
    app.oncheckpoint = function (args) {  
    };  
  
    app.start();  
  
    var publicMembers = {  
        items: pages  
    };  
  
    WinJS.Namespace.define("Data", publicMembers);  
  
})();  
```  
  
## <a name="see-also"></a>См. также  
 [Краткое руководство по отладке HTML и CSS](../debugger/quickstart-debug-html-and-css.md)