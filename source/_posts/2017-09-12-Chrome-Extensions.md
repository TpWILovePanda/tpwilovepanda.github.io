---
title: Chrome Extensions-入門
date: 2017-09-12 00:00:00
tags: [chrome, extensions, introduction]
categories: [chrome]
top:
---

# Chrome Extensions 入門

簡單介紹，如何使用 **Chrome 擴充功能** 設計開起新的分頁時，顯示自己喜愛的圖片。
先來到 [Extensionizr](https://extensionizr.com/) 網站，可幫助創建自己的 Chrome Extensions 基礎！

1. 選擇 **Browser action**，因為要設計開啟新分頁時顯示漂亮圖片，而開啟新分頁屬於 Browser 部分。
1. 選擇 **Background.html**，漂亮圖片需要 html 撰寫 `<img src="..." alt="..." srcset="...">`
1. 選擇 **Blank options.html**，點選擴充工具 Chrome Extensions 時，彈出自訂義選單，這邊我們簡單設計簡介內容。
1. Content scripts 是什麼意思呢？大家可能有聽過 AdBlock，它使用的就是 Content scripts，使用者瀏覽特定頁面時，將 JavsScript 或 css 塞入並且修改頁面顯示內容，讓廣告不會出現，但此次不需要。
1. 選擇 **Add jQuery 2.0.0**，加入 jQuery 讓開發更方便
1. 其他此次尚未需要，如果有興趣，相關內容可以看文章最後的 [Extensionizr.com](http://extensionizr.com/) 簡易中文翻譯。
1. **Download it!**

![Chrome-Extensions 選擇時的配置](https://scontent.ftpe1-1.fna.fbcdn.net/v/t31.0-8/23509162_10208212761356259_4022435121810048611_o.jpg?oh=81d576f26a651abd36576ef8bee28122&oe=5A654AD1 "Chrome-Extensions 選擇時的配置")

上圖為 [Extensionizr](https://extensionizr.com/) 網站選擇時的配置。

完成下載後，打開資料夾會看到此架構

```
├── _locales - 本地端語言設定位置
├── css - 使用到的 CSS 放置位置
├── icons - 圖示放置位置
├── js - 使用到的 JavaScript 放置位置
├── src - 背景、瀏覽器觸發、設定、覆寫之頁面的 HTML 放置位置
└── manidest.json - 它就如同 Chrome 擴充功能的描述簡介
```

## **manifest.json**

```json
{
  // 擴充功能名稱
  "name": "CHANGE THIS : Extension boilerplate",
  // 擴充功能版本
  "version": "0.0.1",
  "manifest_version": 2,
  // 擴充功能簡介描述
  "description": "This extension was created with the awesome extensionizr.com",
  "homepage_url": "http://extensionizr.com",
  // 擴充功能縮圖位置
  "icons": {
    "16": "icons/icon16.png",
    "48": "icons/icon48.png",
    "128": "icons/icon128.png"
  },
  // 預設本地端語言
  "default_locale": "en",
  // 背景執行程式位置
  "background": {
    "page": "src/bg/background.html",
    "persistent": false
  },
  // 彈跳選單內容位置
  "options_page": "src/options/index.html",
  // 瀏覽器執行描述位置
  "browser_action": {
    "default_icon": "icons/icon19.png",
    "default_title": "browser action demo",
    "default_popup": "src/browser_action/browser_action.html"
  },
  // 覆寫內容位置
  "chrome_url_overrides": {
    "newtab": "src/override/override.html"
  }
}
```

將更新 **manifest.json** 以下內容，完成以後就可以存檔。

1. `name: <擴充套件名子>`
1. `description: <描述>`

## 開啟開發人員工具 **安裝擴充套件**

1. 開啟 **Chrome** 右上角 **自訂及管理 > 更多工具 > 擴充功能**，進入之後勾選 **開發人員模式**
1. 點選 **載入未封裝功能** 尋找此專案資料夾並按確定。

![Chrome 開啟開發人員工具 安裝擴充套件 範例畫面](https://scontent.ftpe1-1.fna.fbcdn.net/v/t1.0-9/23517997_10208212761276257_7069548037352052842_n.jpg?oh=8190e9f8d165e8b8cfe9122aa1d8bd87&oe=5AAD538E)

## **src/override**

### 創建 **main.js** 於 src/override，開始寫程式囉。

```js
// 初始化取得福利 API 資料
function initLoad() {
    var data = [];
    let xhr = new XMLHttpRequest();
    xhr.open('GET', 'http://gank.io/api/data/%E7%A6%8F%E5%88%A9/100/1');
    xhr.onreadystatechange = () => {
        if (xhr.readyState === 4) {
            data = JSON.parse(xhr.responseText);
            getRandomArray(data, 0, 100, 10);
        }
    };
    xhr.send();
}

// 取得亂數
function getRandom(minNum, maxNum) { // 取得 minNum(最小值) ~ maxNum(最大值) 之間的亂數
    return Math.floor(Math.random() * (maxNum - minNum + 1)) + minNum;
}

// 隨機產生不重覆的n個數字
function getRandomArray(data, minNum, maxNum, n) {
    let rdmArray = [n]; // 儲存產生的陣列
    for (let i = 0; i < n; i++) {
        let rdm = 0; // 暫存的亂數
        let exist;
        do {
            exist = false; // 此亂數是否已存在
            rdm = getRandom(minNum, maxNum); // 取得亂數
            // 檢查亂數是否存在於陣列中，若存在則繼續回圈
            if (rdmArray.indexOf(rdm) != -1) exist = true;
        } while (exist); // 產生沒出現過的亂數時離開迴圈
        rdmArray[i] = rdm;
    }
    let imgsArray = rdmArray;
    creatCardLayout(data, imgsArray);
}

// 建立卡片框架
function creatCardLayout(data, array) {
    let element = '';
    for (let index = 0; index < array.length; index++) {
        element +=
            `<div class="card">
                <img class="card-img" src="${data.results[array[index]].url}" alt="Card image">
            </div>`;
    }
    $('.card-columns').html(element);
}

initLoad();
```

### **overraid.html**

完成 **main.js** 之後，我們要把畫面顯示出來創建 **overraid.html**。

```html
<!DOCTYPE html>
<html lang="zh-TW">
  <head>
    <!-- Required meta tags -->
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />

    <title>Beauty Tab</title>

    <!-- Bootstrap CSS -->
    <link
      rel="stylesheet"
      href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/css/bootstrap.min.css"
      integrity="sha384-/Y6pD6FV/Vv2HJnA6t+vslU6fwYXjCFtcEpHbNJ0lyAFsXTsjBbfaDjzALeQsN6M"
      crossorigin="anonymous"
    />
  </head>

  <body>
    <div class="container">
      <h1 class="text-center">Beauty Tab</h1>
      <div class="card-columns"></div>
    </div>

    <!-- PS: js 禁止用 CDN 方式，但 CSS 可以 -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="/js/jquery-3.2.1.slim.min.js"></script>
    <script src="/js/popper.min.js"></script>
    <script src="/js/bootstrap.min.js"></script>
    <script src="main.js"></script>
  </body>
</html>
```

恭喜，已經完成初步的 Chrome Extension 開發。

### 後續步驟如下

1. 將開發好的專案壓縮成 zip 檔案。
1. 接著，開啟[Chrome 線上應用程式商店](https://chrome.google.com/webstore/category/extensions?hl=zh-TW)。
1. 進入[開發人員資訊主頁](https://chrome.google.com/webstore/developer/dashboard?hl=zh-TW)
1. 選擇**新增商品**並上傳，這樣就完成囉。
1. 如要驗證你的帳戶並發佈商品，需支付一次性的開發人員註冊費 US\$5.00。

Chrome Extension 開發完成。
![Chrome Extension 範例截圖](https://scontent.ftpe1-1.fna.fbcdn.net/v/t31.0-8/23467223_10208212761396260_135096862158608237_o.jpg?oh=ba190ecf7a7027d585013afce044ed3d&oe=5A9454DB)

---

# [Extensionizr](https://extensionizr.com/) 網站簡易中文翻譯

## Name your extension - 選擇你的擴充功能

1. Hidden extension
   - 如果您不想要擴充功能的任何可視化表示，請使用此選項。 當您只想使用注入腳本時。
1. Page action
   - 使用頁面操作將圖標放在地址欄中。 頁面操作表示可以在當前頁面上執行的操作，但不適用於所有頁面。
1. Browser action
   - 使用瀏覽器操作將圖標放在 Google Chrome 主工具欄中的地址欄右側。 除了圖標之外，瀏覽器操作還可以具有工具提示，徽章和彈出窗口。

## Fine tuning - 微調

1. Extension type （如上 1.）
1. Background page
   - Background.html
     - 後台頁面是在擴展過程中運行的 HTML 頁面。 它在您的擴展的生命週期中存在，並且一次只有一個實例是活動的。
   - Background.js
     - 在常見的情況下，後台頁面不需要任何 HTML 標記。 這些背景頁面可以單獨使用 JavaScript 文件實現
   - Presistent
     - 取消選擇“持久”將背景頁面轉到事件頁面。 活動頁面只有在需要時加載。 當事件頁面沒有積極地做某事時，它被卸載，釋放內存和其他系統資源。
   - No background
1. Options page - 選項頁
   - Black options.html
     - 要允許用戶自定義擴展的行為，您可能希望提供一個選項頁面。 如果您這樣做，則會從擴展管理頁面 chrome：// extensions 提供一個鏈接。 單擊選項鍊接將打開指向您的選項頁面的新選項卡。
   - “Fancy settings” options
     - 適用於 Chrome 擴展程序的花式，Chrome 瀏覽器相似設置。 功能包括搜索，標籤，組等
   - No options page
     - 沒有選項頁
1. Override - 覆蓋
   - Override new tab
     - 覆蓋當用戶創建新的選項卡或窗口時顯示的頁面。 您還可以通過輸入 chrome：// newtab 的 URL 訪問此頁面。
   - Override bookmarks
     - 覆蓋當用戶從“工具”菜單中選擇“書籤管理器”菜單項時顯示的頁面。 您還可以通過輸入網址 chrome：//書籤來訪問此頁面。
   - Override history
     - 用戶從“工具”菜單中選擇“歷史記錄”菜單項時顯示的覆蓋頁面。 您還可以通過輸入 chrome：//歷史記錄訪問此頁面。
   - No Override
1. Content scriipts - 內容腳本
   - Inject css
     - 注入網頁的 CSS 文件。 使用 inject.css 自定義網頁樣式。
   - Inject js
     - 在網頁上下文中運行的 JavaScript 文件。 通過使用標準的文檔對像模型（DOM），他們可以讀取瀏覽器訪問的網頁的詳細信息，或者對它們進行更改。
1. Misc addons - 雜項插件
   - Add omnibox support
     - omnibox API 允許您使用 Google Chrome 的地址欄（也稱為多功能框）註冊關鍵字。
   - Add jQuery 2.0.0
     - 將 jQuery 添加到您的擴展名
   - Add Angular.js 1.0.6
     - 將 AngularJS 添加到您的擴展名

## URL permissions - URL 權限

- Separated by ";" (https://*/* ; http://google.com/*)
  - 網址權限是一種匹配模式集，可讓您的擴展訪問一個或多個主機。

## Permissions - 權限

1. Bookmarks
   - 使用 chrome.bookmarks 模塊創建，整理和以其他方式操作書籤。 另請參閱覆蓋頁面，您可以使用它們來創建自定義書籤管理器頁面。
1. Chrome://favicon
   - 如果擴展名使用“chrome：// favicon / url”機制顯示頁面的圖標，則必需。 例如“chrome：// favicon / http：//www.google.com/” (http://www.google.com/%E2%80%9D)
1. Clipboard read access
   - 如果擴展名使用 document.execCommand（'paste'），則必需。
1. Clipboard write access
   - 表示應用程序或擴展名使用 document.execCommand（'copy'）或 document.execCommand（'cut'）。
1. Content Settings
   - 內容設置允許您根據每個站點而不是全局自定義 Chrome 的行為。
1. Context menus
   - 上下文菜單模塊允許您將項目添加到 Google Chrome 的上下文菜單。
1. Cookies
   - 訪問指定域的 Cookie。
1. FileBrowserHandler
   - 使用 chrome.fileBrowserHandler 模塊來擴展 Chrome 操作系統文件瀏覽器。 例如，您可以使用此 API 來使用戶將文件上傳到您的網站。重要信息：此 API 僅適用於 Chrome 操作系統
1. Text to speech
   - 使用 chrome.tts 模塊播放合成的文本到語音（TTS）。 另請參見相關的 ttsEngine 模塊，它允許擴展來實現語音引擎。
1. Text to speech engine
   - 使用 chrome.ttsEngine 模塊來實現使用擴展名的文本到語音（TTS）引擎。
1. History
   - 使用 chrome.history 模塊與瀏覽器的訪問頁面記錄進行交互。 您可以在瀏覽器的歷史記錄中添加，刪除和查詢網址。 要用您自己的版本覆蓋歷史頁面，請參閱覆蓋頁面。
1. Idle
   - 使用 chrome.idle API
1. Management
   - chrome.management 模塊提供了管理已安裝並正在運行的擴展程序/應用程序列表的方法。 它對於覆蓋內置的新標籤頁的擴展特別有用。
1. Notifications
   - 使用桌面通知通知用戶發生了重要的事情。 通知顯示在瀏覽器窗口之外。
1. Tabs
   - 使用 chrome.tabs 模塊與瀏覽器的標籤系統進行交互。 您可以使用此模塊在瀏覽器中創建，修改和重新排列選項卡。
1. Geolocation
   - 允許擴展程序使用建議的 HTML5 地理位置 API，而不會提示用戶獲得許可。
