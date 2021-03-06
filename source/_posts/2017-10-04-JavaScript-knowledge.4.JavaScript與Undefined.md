---
title: 克服JS的奇怪部分-JavaScript與Undefined
date: 2017-10-04 00:00:00
tags: [javascript, js]
categories: [javascript]
top:
---
# JavaScript與Undefined
變數創造階段存入記憶體時，會被設定初始值`undefined`，一個JavaScript內建的特殊值，表示這個變數未被設定。
```javascript
var a;
console.log(a);
if (a === undefined) {
  console.log('a is undefined');
} else {
  console.log('a is defined');
}
```
如果沒有`var a;`，而直接呼叫`a`，JavaScript記憶體中找不到`a`這個值。
```javascript
a
// 返回: Uncaught ReferenceError: a is not defined
```
> 遠永不要設定變數值為`undefined`。

## 參考資源 (References)
* [JavaScript 全攻略：克服 JS 的奇怪部分](https://www.udemy.com/javascriptjs/learn/v4/overview)