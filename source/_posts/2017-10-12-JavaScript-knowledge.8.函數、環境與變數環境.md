---
title: 克服JS的奇怪部分-函數、環境與變數環境
date: 2017-10-12 00:00:00
tags: [javascript, js]
categories: [javascript]
top:
---
# 函數、環境與變數環境
變數環境是描述創造變數的位置，還有記憶體中與其他變數的關係，每當呼叫函式就會得到函式自己的執行環境。
```javascript
function b() {
  var myVar; // myVar它的變數環境就b()
  console.log(myVar); // 返回: undefined
}
function a() {
  var myVar = 2; // myVar它的變數環境就a()
  console.log(myVar); // 返回: 2
  b();
}
var myVar = 1; // myVar它的變數環境就是全域物件，也就是瀏覽器的Window
console.log(myVar); // 返回: 1
a();
``` 
上面範例三個`myVar`被宣告了三次，都待在自己的執行環境裡且不會互相引響。

## 參考資源 (References)
* [JavaScript 全攻略：克服 JS 的奇怪部分](https://www.udemy.com/javascriptjs/learn/v4/overview)