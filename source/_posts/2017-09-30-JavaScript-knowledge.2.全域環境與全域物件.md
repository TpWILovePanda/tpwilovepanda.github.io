---
title: 克服JS的奇怪部分-全域環境與全域物件
date: 2017-09-30 00:00:00
tags: [javascript, js]
categories: [javascript]
top:
---
# 全域環境與全域物件
全域代表可以在任何地方取用，JavaScript全域執行環境創造兩個事情，創造「全域物件」，還有一個特殊的變數「`this`」，當執行JavaScript時，永遠會有「全域物件」，瀏覽器全域物件是`Window`，但在NodeJS「全域物件」就不是`Window`，每個視窗都有自己的執行環境與全域物件，全域等級中這兩者相同「全域物件」＝「`this`」。「全域物件」`Window`，特殊變數「`this`」。
```javascript
Window {...}
// 返回: Window {...}

this
// 返回: Window {...}
```

當說全域就表示不再函式裡，程式碼或變數不再函式裡時就是在全域，觀察Window「全域物件」會看到a變數與b函式。
```javascript
var a = "Hello World!"
function b () {}
Window {...}
// 返回:
// Window {
//   ...
//   a: "Hello World!"
//   ...
//   b: function b() {}
//   ...
// }

> a
// 返回: "Hello World!"
> Window.a
// 返回: "Hello World!"
```

## 參考資源 (References)
* [JavaScript 全攻略：克服 JS 的奇怪部分](https://www.udemy.com/javascriptjs/learn/v4/overview)