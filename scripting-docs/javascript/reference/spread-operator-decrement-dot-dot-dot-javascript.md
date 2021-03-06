---
title: "Оператор Spread (...) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a07d480360441906c445faa196f6d7771f97d75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="spread-operator--javascript"></a>Оператор расширения (...) (JavaScript)
Позволяет инициализировать части литерала массива из итерируемого выражения (например, другого литерала массива) или развернуть выражение в несколько аргументов (в вызовах функций).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## <a name="parameters"></a>Параметры  
 `iterable`  
 Обязательный. Итерируемый объект.  
  
 `arg0ToN`  
 Необязательно. Один элемент или несколько элементов литерала массива.  
  
 `args`  
 Необязательно. Один аргумент или несколько аргументов для функции.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения об итераторах см. в разделе [итераторы и генераторы](../../javascript/advanced/iterators-and-generators-javascript.md). Дополнительные сведения об использовании оператора расширения в качестве параметра rest см. в разделе [функции](../../javascript/functions-javascript.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода использование оператора расширения сравнивается с использованием метода `concat`.  
  
```JavaScript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать оператор расширения в вызове функции. В этом примере два литерала массивов передаются в функцию с помощью оператора расширения и массивы разворачиваются в несколько аргументов.  
  
```JavaScript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## <a name="example"></a>Пример  
 Операторы расширения позволяют упростить код, который раньше требовал применять метод `apply`.  
  
```JavaScript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
f.apply(this, args);  
// New method  
f(...args);  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)