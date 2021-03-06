---
title: 前端工程師手冊-CSS
date: 2017-09-18 00:00:00
tags: [css]
categories: [css]
top:
---
# CSS 選取器
## 深入理解
### 基本知識
> [MDN - CSS 選擇器](https://developer.mozilla.org/zh-TW/docs/Glossary/CSS_Selector)
* 基本選擇器
  * 類型選擇器 elementname
  * Class 選擇器 .classname
  * ID 選擇器 #idname
  * 通用選擇器 * ns|* *|*
  * 屬性選擇器 [attr=value]
  * 狀態選擇器 a:active, a:visited
* 複合選擇器
  * 鄰接同層選擇器 A + B
  * 通用同層選擇器 A ~ B
  * 直屬選擇器 A > B
  * 後代選擇器 A B
  * 虛擬元素
  * 虛擬類別

---

|選取器|意義|範例|
|--|--|--|
|全域選取|套用所有元素上|`* {}`|
|類型選取|找出符合的元素|`h1, h2, h3 {}`|
|class|找出符合class的元素|`.note {} p.note {}`|
|id|找出符合id的元素|`#note {}`|
|子元素選取|元素之後的第一層元素|`li > a {}`|
|後代選取|元素之後的任何一層元素|`p a {}`|
|相連手足選取|相鄰的第一個元素|`h1 + p {}`|
|整體手足選取|相鄰的所有元素|`h1 ~ p {}`|
|existence|找出一個特定屬性|`p[class] {}`<br />帶有class屬性的p元素|
|equality|找出一個特定值的特定屬性|`p[class="dog"] {}`<br />帶有class屬性值為dog的p元素|
|space|找出一個特定屬性，其值出現在一串用空格分開的字詞當中|`p[class~="dog"] {}`<br />class屬性是一串空白隔開的字詞清單，而其中一個字是dog的任何p元素|
|space|找出一個特定屬性，其值出現在一串用空格分開的字詞當中|`p[class^="dog"] {}`<br />class屬性值開頭含dog的任何p元素，不是開頭就不會選取，例如`catdog` or `cat dog`就不會選取|
|prefix|找出一個特定屬性，其值得開頭為某一特定字串|`p[attr^"d"] {}`<br />帶有class屬性值為d字母開頭的任何p元素|
|substring|找出一個特定屬性，其值包含了一個特定子字串|`p[attr*"do"] {}`<br />帶有class屬性值包含do的任何p元素|
|suffix|只出一個屬性，其值的結尾是某一特定字串|`p[attr$"g"] {}`<br />帶有class屬性值為g字母結尾的任何p元素|
|`.class-name:not(:last-child) {}`|[詳細教學](https://www.minwt.com/webdesign-dev/css/17780.html)|The :not(selector) selector matches every element that is NOT the specified element/selector.|