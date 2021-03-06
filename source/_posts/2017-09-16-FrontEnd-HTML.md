---
title: 前端工程師手冊-HTML
date: 2017-09-16 00:00:00
tags: [html]
categories: [html]
top:
---
# HTML 元素
屬性為元素做說明，元素整理。  
`<p lang="en-us">Paragraph in English</p>` 範例中，屬性名是lang，屬性值是us-us，表示此元素裡所使用的語言。
> [HTML5 標籤速查圖表](https://www.w3schools.com/tags/default.asp)

## DOCTYPES
```html
<!-- HTML 5 -->
<!DOCTYPES html>
<!-- HTML 4.01 Transitional -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<!-- HTML 4.01 Strict -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<!-- Transitional XHTML1.0-->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<!-- Strict XHTML1.0 -->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<!-- XML Declaration -->
<?xml version="1.0" ?>
```

## `meta` 頁面相關資訊
* description
  * 通常被搜尋引擎利用來了解頁面內容，最多155字元。
  * `<meta name="description" content="網頁簡介" />`
* keywords
  * 使用者用來搜尋此網頁的字詞清單，但對搜尋引擎索引網站已經沒任何意義！
  * `<meta name="keywords" content="關鍵字1, 關鍵字2, 關鍵字3" />`
* robots
  * 此屬性標明了搜尋引擎是否應該將此頁面加到它們的搜尋結果中。如果不應該加入，可以使用noindex值，如果要搜尋引擎加入此頁，但不加入此頁連結的其他頁面，使用nofollow值。
  * `<meta name="robots" content="nofollow" />`
* author
  * 標明網頁作者
  * `<meta name="author" content="作者名稱" />`
* pragma
  * 此屬性避免瀏覽器儲存快取頁面。
  * `<meta name="pragma" content="no-cache" />`
* expires
  * 因為瀏覽器會快取頁面，可以使用expires標明頁面何時過期（告訴之後不應該在快取），格式一定要相同。
  * `<meta name="expires" content="Fri, 04 Apr 2014 23:59:59 GMT" />`

## `body`
`body`元素內的東西都會顯示於瀏覽器中。

## `head`
`head`元素包含該頁面得些關資訊。

## `title`
`title`元素會出現在瀏覽器頂端的標題列。
```html
<html>
  <head>
    <title>This is Title</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

## `h1 h2 h3 h4 h5 h6` 標題
HTML的標題分為六階段，且注意每頁`<h1>`只會有一個！這關係到SEO部分。
```html
<h1>Level 1 Heading</h1>
<h2>Level 2 Heading</h2>
<h3>Level 3 Heading</h3>
<h4>Level 4 Heading</h4>
<h5>Level 5 Heading</h5>
<h6>Level 6 Heading</h6>
```

## `p` 段落
瀏覽器會使用新的一行來顯示段落，並與之前的保留一小段距離。
```html
<p>《魔戒》（英語：The Lord of the Rings，又名《指環王》）是一部由英國牛津大學教授、語言學家J·R·R·托爾金創作的史詩奇幻文學作品。</p>
<p>這個故事原是托爾金早年創作的兒童幻想小說《哈比人歷險記》（1937年）之續篇，但隨著故事的發展逐漸變得恢弘龐大。</p>
```

## `b` 粗體 <b>text</b>
讓字體呈現粗體，但使用`<b>`元素並不代表有任何而外得意義。
```html
<b>text</b>
```

## `i` 斜體 <i>text</i>
讓字體呈現斜體，使用`<i>`元素代表一段與其他內容不同方式說明的文字。
```html
<i>text</i>
```

## `sup` 上標 4<sup>th</sup>
```html
4<sup>th</sup>
```

## `sub`下標 CO<sub>2</sub>
```html
CO<sub>2</sub>
```

## `br` 斷行
```html
<p>《魔戒》（英語：The Lord of the Rings，又名《指環王》）<br>是一部由英國牛津大學教授、語言學家J·R·R·托爾金創作的史詩奇幻文學作品。</p>
```

## `hr` 水平線
水平線。`<hr />`與`<br />`屬於空元素(empty elements)，通常會有一個空白和一個斜線。有些前端工程師會忽略此寫法，但此習慣會是好事。

## `em blockquote`語法標示
語法標示如：`<em> <blockquote>`...等等，使用語法標示並不只有改變外觀，還有更精確地描述網頁內容，螢幕閱讀器與搜尋引擎可以使用這份額外的資訊。

## `strong, em` 加強與強調
`<strong>`代表其內容有很強烈的重要性。
`<em>`代表文句中稍微有文意轉折的強調字眼。
```html
<p>如果你能<strong>征服</strong>你的<em>恐懼</em>，代表你可以戰勝死亡。</p>
```

## `blockquote` 引述
比較長，整個段落篇幅的引述。`<blockquote>`可以使用cite屬性來加入URL標明引述來源。
```html
<blockquote cite="https://zh.wikipedia.org/wiki/%E5%92%96%E5%95%A1%E8%B1%86">
  <p>咖啡豆是咖啡屬植物的種子，咖啡屬植物的果實大小類似櫻桃，咖啡豆即為其中的核果。將咖啡豆烘焙加工後再磨碎成咖啡粉，即可烹製咖啡。</p>
</blockquote>
```

## `q` 引述
比較短的引述。`<q>`可以使用cite屬性來加入URL標明引述來源。
```html
<p>魔戒小說中曾提到：<q cite="https://zh.wikiquote.org/zh-tw/%E9%AD%94%E6%88%92">把手握緊，裡面什麼也沒有；把手放開，你得到的是一切。</q></p>
```

## `abbr` 縮寫和縮略字
縮寫，cite可以註明全名。
```html
<p>連結網路需要通過<abbr title="網路伺服器">伺服器</dfn>，它是隨時連線的電腦。</p>
```

## `cite` 註解和定義
標示註解的來源，cite不應該用在人名上。
```html
<p><cite>咖啡豆是咖啡屬植物的種子，咖啡屬植物的果實大小類似櫻桃，咖啡豆即為其中的核果。將咖啡豆烘焙加工後再磨碎成咖啡粉，即可烹製咖啡。</cite>引述來自維基百科</p>
```

## `dfn`
第一次解釋新的術語時使用，術語：專業行話或學術概念。
```html
<p>連結網路需要通過<dfn>網路伺服器</dfn>，它是隨時連線的電腦。</p>
```

## `addres` 作者細節
用來表示網頁作者的聯絡方式的特定用途。**微格式 [hCcard](https://zh.wikipedia.org/wiki/HCard) 用來在原始碼中加入實體住址。**
```html
<addres>
  <p><a href="mailto:author@exmaple.org">author@exmaple.org</a></p>
  <p>台北市忠孝東路153巷19號</p>
</addres>
```

## `ins del s` 內容的更動
`<ins>`顯示被插入文件的內容。  
`<del>`顯示被刪除的文字。  
`<s>`標示不再正確顯示或相關（但不應該被刪除）內容。
```html
<p>《魔戒》<del>戒魔</del>（英語：The Lord of the Rings，<s>又名《指環王》</s>）是一部由英國牛津大學教授、語言學家J·R·R·托爾金創作的史詩奇幻文學作品。<ins>這個故事原是托爾金早年創作的兒童幻想小說《哈比人歷險記》（1937年）之續篇，但隨著故事的發展逐漸變得恢弘龐大。</ins></p>
```
<p>《魔戒》<del>戒魔</del>（英語：The Lord of the Rings，<s>又名《指環王》</s>）是一部由英國牛津大學教授、語言學家J·R·R·托爾金創作的史詩奇幻文學作品。<ins>這個故事原是托爾金早年創作的兒童幻想小說《哈比人歷險記》（1937年）之續篇，但隨著故事的發展逐漸變得恢弘龐大。</ins></p>

## `ol ul li` 編號清單與項目清單
```html
<ol>
  <li>情節大綱
    <ul>
      <li>魔戒同盟</li>
      <li>雙塔殊途</li>
      <li>王者再臨</li>
    </ul>
  </li>
  <li>主要人物
    <ul>
      <li>哈比人</li>
      <li>邁雅</li>
      <li>精靈</li>
      <li>矮人</li>
      <li>樹人</li>
      <li>人類</li>
    </ul>
  </li>
</ol>
```

## `dl dt dd` 定義清單
通常是一系列名詞與定義組成，`<dl>`製作定義清單，`<dt>`名詞，`<dd>`定義。有時會有兩個名詞一種定義或一個名詞両種定義。
```html
<dl>
  <dt>哈比人</dt>
  <dd>哈比人（英語：Hobbits），是J.R.R.托爾金的奇幻小說中出現的一種虛構民族，體型嬌小為其特色，但並非矮人或侏儒。</dd>
  <dt>邁雅</dt>
  <dd>邁雅（Maiar）是J.R.R.托爾金的小說中虛構的世界－「中土」的一個種族。</dd>
  <dt>精靈</dt>
  <dd>J.R.R.托爾金的精靈高而優雅，擁有不凡的美麗。在《魔戒現身》（The Fellowship of the Ring）書中，哈比人佛羅多（Frodo）第一次見到高等精靈葛羅芬戴爾（Glorfindel）時，「彷彿有一道白光射穿葛羅芬戴爾的身形和衣著，就像射穿一道薄紗一樣。」</dd>
</dl>
```

## `a` 連結 & EMAIL連結 & 新視窗連結 & 連結到同網頁德某部分
```html
<!-- 連結 -->
<a href="https://zh.wikipedia.org/wiki/%E9%AD%94%E6%88%92#.E5.93.88.E6.AF.94.E4.BA.BA">魔戒</a>
<!-- 新視窗連結 -->
<a href="https://zh.wikipedia.org/wiki/%E9%A3%A2%E9%A4%93%E9%81%8A%E6%88%B2" target="_blank">飢餓遊戲</a>
<!-- EMAIL連結 -->
<a href="mailto:author@exmaple.org">author@exmaple.org</a>
<!-- 連結到同網頁的某部分 -->
<h1 id="top">EXAMPLE TITLE</h1>
<a href="#example_1">example_1</a>
<a href="#example_2">example_2</a>
<h2 id="example_1"></h2>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptates, molestias illo? Harum quo ipsa quam. Aliquam quia ipsa asperiores excepturi quos distinctio quis quae fuga repellendus, quidem veritatis quo consequatur.</p>
<h2 id="example_2"></h2>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptates, molestias illo? Harum quo ipsa quam. Aliquam quia ipsa asperiores excepturi quos distinctio quis quae fuga repellendus, quidem veritatis quo consequatur.</p>
<p><a href="#top">Top</a></p>
```

## `img` 影像
* src會告訴瀏覽器影像位置。
* alt提供該精確影像敘述替代文字，如果失去影像將顯示此敘述，供應螢幕閱讀軟體與搜尋引擎使用。
* title提供該影像資訊的額外資訊，當滑鼠移動至影像上方會有提示資訊。
* width與height指定影像寬高可以預留正在下載影像的所需空間，width與height建議用CSS取代。

## `figure figcaption`HTML5：圖和圖片說明
`<figure>`放入影像與說明，方便將兩者結合再一起，HTML5新增`<figcaption>`方便讓圖片加入說明。
```html
<figure>
  <img src="https://upload.wikimedia.org/wikipedia/zh/thumb/a/ab/Hunger_games.jpg/250px-Hunger_games.jpg" alt="飢餓遊戲">
  <br />
  <figcaption>「飢餓遊戲」，遊戲參加者有24人，他們要用任何方法殺死對方，剩下的一位參賽者，便是遊戲的優勝者。</figcaption>
</figure>
```

## `table thead tbody tfoot th tr td`表格
可以在`th`元素中使用scope屬性來標明它是欄位或行列的標題。`table thead tbody tfoot`對於螢幕閱讀器使用者很有幫助，可以協助將表格主要內容和第一列與最後一列區分開來。row表示行的標題。col表示欄的標題。
```html
<table>
  <thead>
    <tr>
      <th></th>
      <th scope="col">時間</th>
      <th scope="col">內容</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td scope="row">魔戒首部曲：魔戒現身</td>
      <td>2001</td>
      <td>《魔戒首部曲：魔戒現身》（英語：The Lord of the Rings: The Fellowship of the Ring），是一部於2001年上映的美國與紐西蘭合拍的奇幻史詩電影，由彼得·傑克森執導，為自J·R·R·托爾金的奇幻小說《魔戒》改編的《魔戒電影三部曲》中的第一部。美國新線電影公司出品。</td>
    </tr>
    <tr>
      <td scope="row">魔戒二部曲：雙城奇謀</td>
      <td>2002</td>
      <td>《魔戒二部曲：雙城奇謀》（英語：The Lord of the Rings: The Two Towers），是一部於2002年上映的美國與紐西蘭合拍的奇幻史詩電影，由彼得·傑克森執導，為自J·R·R·托爾金的奇幻小說《魔戒》改編的《魔戒電影三部曲》中的第二部。美國新線電影公司出品。</td>
    </tr>
    <tr>
      <td scope="row">魔戒三部曲：王者再臨</td>
      <td>2003</td>
      <td>《魔戒三部曲：王者再臨》（英語：The Lord of the Rings: The Return of the King），是一部於2003年上映的史詩奇幻電影，由彼得·傑克森執導，此片是根據J·R·R·托爾金的奇幻小說《魔戒》的第二部曲及第三部曲改編而成。本片也是《魔戒電影三部曲》的完結篇。</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td scope="row">魔戒電影</td>
      <td>2001 - 2003</td>
      <td>《《魔戒三部曲：王者再臨》是繼1997年的《鐵達尼號》後，第二部票房突破10億美元的電影，該片也和《鐵達尼號》一樣，共贏得11座奧斯卡金像獎，包括「最佳影片」及「最佳導演」，是奧斯卡有史以來獲得兩位數提名的影片中唯一全數得獎的影片。三部曲的電影成功的讓更多人認識了《魔戒》系列作品。</td>
    </tr>
  </tfoot>
</table>
```

## `form` 表單
action：url。  
method：get or post。  
size：不應該使用在現在的表單上，它被用在舊(以前)的表單指定文字輸入欄位寬度，建議使用CSS取代size。  
autocomplete：規定是否啟用表單的自動完成功能。
`<input type="password">`螢幕顯示隱藏，但不代表密碼是以加密方式傳送。
```html
<form action="http://www.example.com/login.php" method="post" autocomplete="on">
  <p>使用者名稱：<input type="text" name="username" maxlength="30" /></p>
  <p>使用者密碼：<input type="password" name="password" maxlength="30" /></p>
  <input type="submit" value="Submit" />
</form>
```

## `input` 輸入框
### `input type="file"`
上傳時，method屬性必須是post。
```html
<form action="http://www.example.com/upload.php" method="post">
  <p>上傳音樂：</p>
  <input type="file" name="user-song" /><br />
  <input type="submit" name="upload" />
</form>
```

### `input type="image"`
```html
<form action="http://www.example.com/subscribe.php">
  <p>訂閱最新消息：</p>
  <input type="txtx" name="email" />
  <input type="image" src="images/subscribe.jpg" width="100" height="20" />
</form>
```

## `label` 表單控制項貼標籤
兩種用法。
1. 將文字敘述與表單包起來。
1. 獨立於表單之外，使用for來表示屬於哪一個表單控制選項。
for的值配合代表的id，此方法可以用在任何表單控制上。當`<label>`用在勾選框或單選紐上面時，使用者可以點按鈕表單控制項或者標籤來進行選取。
```html
<label>Age: <input type="text" name="age" /></label>
<br />
Gender:
<input id="female" type="radio" name="gender" value="f"><label for="female">Female</label>
<input id="male" type="radio" name="gender" value="m"><label for="male">Male</label>
```

## `fieldest legend`群組表單元素
```html
<fieldest>
  <legend>表單細節</legend>
  <label>Email：<input type="txet" name="email" /></label><br />
  <label>Mobile：<input type="txet" name="mobile" /></label><br />
  <label>Telephone：<input type="txet" name="telephone" /></label>
</fieldest>
```

# HTML5

## HTML5 版面
|Tag|Description|
|--|--|
|`<article>`|Defines an article|
|`<aside>`|Defines content aside from the page content|
|`<bdi>`|Isolates a part of text that might be formatted in a different direction from other text outside it|
|`<details>`|Defines additional details that the user can view or hide|
|`<dialog>`|Defines a dialog box or window|
|`<figcaption>`|Defines a caption for a `<figure>` element|
|`<figure>`|Specifies self-contained content, like illustrations,| diagrams, photos, code listings, etc.
|`<footer>`|Defines a footer for a document or section|
|`<header>`|Specifies a header for a document or section|
|`<main>`|Specifies the main content of a document|
|`<mark>`|Defines marked/highlighted text|
|`<menuitem>`|Defines a command/menu item that the user can invoke from a popup menu|
|`<meter>`|Defines a scalar measurement within a known range (a gauge)|
|`<nav>`|Defines navigation links|
|`<progress>`|Represents the progress of a task|
|`<rp>`|Defines what to show in browsers that do not support ruby annotations|
|`<rt>`|Defines an explanation/pronunciation of characters (for East Asian typography)|
|`<ruby>`|Defines a ruby annotation (for East Asian typography)|
|`<section>`|Defines a section in a document|
|`<summary>`|Defines a visible heading for a `<details>` element|
|`<time>`|Defines a date/time|
|`<wbr>`|Defines a possible line-break|

## `form required` 表單驗證(form validation)
HTML5表單驗證之一就是required，這屬性不需要值，但在HTML4裡面，所有的屬性的需要值。
```html
<form action="http://www.example.com/login.php" method="post" autocomplete="on">
  <p>使用者名稱：<input type="text" name="username" maxlength="30" required="required" /></p>
  <p>使用者密碼：<input type="password" name="password" maxlength="30" required="required" /></p>
  <input type="submit" value="Submit" />
</form>
```

## `input type="date"` 日期輸入
HTML5推出新的表單控制項來標準化某些資料的收集方式。
```html
<input type="date">
```

## `input type="email" type="url"` EMAIL與URL輸入
EMAIL：檢查使用者是否提供正確的EMAIL格式。  
URL：檢查使用者是否提供正確的URL格式。
```html
<!-- EMAIL -->
<input type="email">
<!-- URL -->
<input type="url">
```

## `input type="search"` 搜尋輸入
新型瀏覽器提高優使性，例如十字游標按鈕，輸入資料時用來清除欄位。
```html
<input type="search" placeholder="Keyword">
```

## `video`
HTML5中`<video>`所使用的所有屬性都不需要提供一個值，例如controls、autoplay和loop...等等，這些屬性就像開關一樣，存在就開啟，不存在就關閉。
* preload
  * 告訴瀏覽器頁面載入時要做什麼
  * none：使用者按下播放鍵之前，瀏覽器不該載入視訊。
  * auto：瀏覽器應該在頁面載入的同時下載視訊。
  * metadata：瀏覽器只需要收集大小、第一個影格、播放清單和影片長度之資訊。
* src
  * 視訊的路徑
* poster
  * 視訊下載時顯示的圖像，或者使用者播放之前，顯示的圖像。
* controls
  * 使用瀏覽器提供的播放控制鈕。
* autoplay
  * 自動播放。
* loop
  * 重複播放。
```html
<video src="video/example.mp4"
  poster="images/example.png"
  width="400" height="300"
  preload
  controls
  autoplay
  loop>
  <p>影片內容簡介</p>
</video>
```

## `source` 數個視訊來源
iPad Bug，mp4必須是第一個播放，否則無法播放。
```html
<video poster="images/example.png" width="400" height="300" preload controls loop>
  <source src="video/example.mp4" type='video/mp4;codecs="avcl.42E, mp4a.40.2"' />
  <source src="video/example.webm" type='video/webm;codecs="vp8, vorbis"' />
  <p>影片內容簡介</p>
</video>
```

## `audio` 音訊
* src
  * 音訊的路徑
* preload
  * 告訴瀏覽器頁面載入時要做什麼
  * none：使用者按下播放鍵之前，瀏覽器不該載入音訊。
  * auto：瀏覽器應該在頁面載入的同時下載音訊。
  * metadata：瀏覽器只需要收集大小、第一個音格、播放清單和音訊長度之資訊。
* controls
  * 使用瀏覽器提供的播放控制鈕，如果沒使用將不會顯示，可以用javascript指定自己的控制按鈕。
* autoplay
  * 自動播放。
* loop
  * 重複播放。
* muted
  * 音訊輸出靜音。
```html
<audio src="audio/example.ogg" controls autoplay>
  <p>音訊內容簡介</p>
</audio>
```

### `audio` 多重音訊
```html
<audio controls autoplay>
  <source src="audio/example.ogg" />
  <source src="audio/example.mp3" />
  <p>音訊內容簡介</p>
</audio>
```