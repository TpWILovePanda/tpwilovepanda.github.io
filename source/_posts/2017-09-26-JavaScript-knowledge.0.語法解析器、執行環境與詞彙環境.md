---
title: 克服JS的奇怪部分-語法解析器、執行環境與詞彙環境
date: 2017-09-26 00:00:00
tags: [javascript, js]
categories: [javascript]
top:
---
## 語法解析器
我們所撰寫的 JavaScript 是經過**語法解析器**轉換成電腦可閱讀的語言，而**語法解析器**是由其他工程師所撰寫，它（語法解析器）會去逐字閱讀撰寫語法 **f-u-n-c-t-i-o-n**，它就會知道這是函式，後面會需要加上空格，接著是函式名稱，這就是**語法解析器**。

## 執行環境
幫助管理正在執行的程式，也包括其他工程師開發環境時撰寫好用來驗證與執行你的程式代碼的程式。

## 詞彙環境
這代表程式碼在程式中實際的所在位置，它被寫在哪裡？它的周遭環境是什麼？  
```javascript
// 例如：一個函數裡面有變數，這個變數在詞彙環境上，實際程式碼的位置就是在函數的裡面。
function hello() {
  var a = 'hello world!';
}
```

## 參考資源 (References)
* [JavaScript 全攻略：克服 JS 的奇怪部分](https://www.udemy.com/javascriptjs/learn/v4/overview)