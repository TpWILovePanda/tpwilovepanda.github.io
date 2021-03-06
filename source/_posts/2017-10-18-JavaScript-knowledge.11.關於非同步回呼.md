---
title: 克服JS的奇怪部分-關於非同步回呼
date: 2017-10-18 00:00:00
tags: [javascript, js]
categories: [javascript]
top:
---
# 關於非同步回呼
## 非同步是什麼意思
非同步表示在一個時間點不只一個，可能有程式在執行時，開始執行一段程式碼然後又在執行別的程式碼，這些程式碼在JavaScript引擎內是同時在執行的，但之前說過JavaScript是同步的一行一行逐步執行，它不會非同步執行。

## 瀏覽器引擎
瀏覽器本身除了JavaScript引擎還有有其他引擎，在JavaScript引擎外執行別的程式，像是呈現引擎（Rendering Engine），用來渲染網頁呈現於螢幕上，也有其他引擎去回應HTTP的請求，例如：獲取資料，JavaScript引擎可以與其他引擎溝通，改變網頁的樣子也可以請求資料，但這些可能都是非同步執行，呈現引擎、JavaScript引擎和請求在瀏覽器內是非同步的，但不要忘記，JavaScript引擎是一行一行執行是同步的。

## 執行堆
JavaScript執行堆是當執行環境被創造函式被呼叫時，執行程序會往上排堆疊排列，直到上一層處理完畢移出執行堆才會在處理下一層的堆疊。

```javascript
function a() { b(); }
function b() { console.log('Called b!'); }
a();
```

* 執行啟用順序 ↓
  1. 全域執行環境
  1. `a();`
  1. `b();`

* 執行堆疊順序 ↓
  1. `b();`
  1. `a();`
  1. 全域執行環境

## 事件隊列（event queue）
JavaScript引擎內的處理事件的等待列稱為事件隊列（event queue），這裡面都是事件、事件通知等待處理隊列。觀察範例 ↓

```javascript
// 長時間執行的 function 函式
function waitThreeSeconds() {
  var ms = 3000 + new Date().getTime();
  // 延遲 3 秒
  while (new Date() < ms) {}
  console.log('finished function! 完成事件!');
}

// 回應 click 事件的函式
function clickHandler() {
  console.log('click event! 點擊事件!');
}

// 監聽 click 事件
document.addEventListener('click', clickHandler);

waitThreeSeconds();
console.log('finished execution! 完成執行!');
```

例如：螢幕上點擊觸發`click`事件，有個需要回應`click`事件的函式，我們的程式繼續執行，當JavaScript執行堆是空的時候，JavaScript才會注意到事件隊列（event queue）的`click`事件，這表示長時間的函式可以干擾事件，但這也就是JavaScript如何同步處理在瀏覽器別處非同步的事件發生，完成時JavaScript需要知道，JavaScript會持續的檢查事件隊列（event queue）。

## 非同步回呼
非同步回呼在JavaScript是可能的，但非同步的部分是發生在JavaScript引擎外面，例如：渲染引擎或`HTTP Request`。

## 參考資源 (References)
* [JavaScript 全攻略：克服 JS 的奇怪部分](https://www.udemy.com/javascriptjs/learn/v4/overview)