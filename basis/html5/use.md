# 用法

## 簡化的語法
文檔類型Doctype:

文檔類型的聲明是一個HTML文檔的第一行內容，它告訴瀏覽器這個頁面是使用哪個版本的標記語言編寫的。

比如,HTML 4.01 Transitional 文檔類型的聲明是：
```js
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"

"http://www.w3.org/TR/html4/loose.dtd">
```
XHTML 1.0 Transitional 文檔類型聲明的寫法是：
```js
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"

"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```
而HTML5中，你只需要：
```js
<!doctype html>
```
## 字符編碼
為了驗證或顯示一個HTML文檔，程序必須選擇一種字符編碼。

字符編碼告訴瀏覽器和驗證程序應該使用哪種編碼由比特流轉換為字符。

下面是HTML 4.01指定UTF-8字符編碼的例子：
```js
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
```
在XHTML中：
```js
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
```
而現在使用HTML5,編碼類型的語法非常簡單：
```js
<meta charset="UTF-8">
```
因此，最基本的HTML文檔結構應該是：
```js
<!doctype html>

<html>

<head>

<meta charset="UTF-8">

<title>Example document</title>

</head>

<body>

<p>Hello, World</p>

</body>

</html>
```
## <code>&lt;script&gt;</code>標籤
<code>&lt;script&gt;</code>標籤用來定義一段客戶端腳本，比如JavaScript. 在HTML4里，type屬性是必須的，但在HTML5里不是。

比如在HTML4里，<code>&lt;script&gt;</code>標籤是這樣定義的：
```js
<script type="text/javascript" src="file.js"></script>
```
在HTML5里:
```js
〈script src=”code.js”></script>
```
HTML5為script標籤添加了一個新的可選屬性 “async”, 用來告訴瀏覽器異步加載代碼，所以這段代碼在頁面繼續加載的同時就會被執行。可以像下面這樣使用：
```js
<script src="code.js" async></script>
```
或者：
```js
<script src="code.js" async="async"></script〉
```
## <code>&lt;link&gt;</code>標籤
<code>&lt;link&gt;</code>標籤定義了文檔與外部資源的聯繫，常用來引入CSS文件:
```js
<link rel="stylesheet" type="text/css" href="style.css"/>
```
在HTML5K ,type屬性跟<code>&lt;script&gt;</code>標籤一樣，都不需要。比如：
```js
<link rel="stylesheet" href="style.css">
```
## HTML5的新標籤
HTML5為更好地組織內容和簡化開發，添加了一些非常新奇和實用的標籤，一些比較重要的如下：

<code><code>&lt;header&gt;</code></code>

header 標籤包含網頁的頁面頭部，裡面常常放置頁面包含的LOGO和其它有用的信息，像標語、菜單等等。使用<code>&lt;header&gt;</code>來代替<code>&lt;div id=”header”&gt;</code>

<code>&lt;nav&gt;</code>

這個標籤是用來建立菜單導航的，可以使用<code>&lt;nav&gt;</code> 來代替<code>&lt;div id=”nav”&gt;</code>

<code>&lt;artical&gt;</code>

這個標籤用來定義獨立的內容，像那些博客文章、新聞、或者用戶評論內容。

<code>&lt;section&gt;</code>

<code>&lt;section&gt;</code>用來分割頁面的不同部分。

一個 section是一組內容，一般sections可以嵌套在在header之前，footer之後。如果需要，它還可以包含任意數量的特殊標記。

<code>&lt;aside&gt;</code>

這個標籤指定一個存放與頁面內容無關的元素，可以用來定義邊欄或者其它任何我們能想到的與頁面正文內容無關的內容。

<code>&lt;figure&gt;</code>

<code>&lt;figure&gt;</code>標籤用來註解插畫、圖表、照片和代碼列表等等的。在<code>&lt;figure&gt;</code>標籤裡的<code>&lt;figcaption&gt;</code>標籤定義標題。

<code>&lt;footer&gt;</code>

這個標籤用來定義代替在頁面底部的部分，常常用來包含像作者、版權信息、使用政策鏈接、隱私條件等信息。在<code>&lt;footer&gt;</code>裡的聯繫信息應該使用<code>&lt;address&gt;</code>標籤。

## 修改過的標籤
<code>&lt;a&gt;</code>

在HTML5里，<code>&lt;a&gt;</code>標籤允許在一行元素內包含多行元素，比如：
```js
<a href="news.html">

<h3>Iceland’s Grimsvotn volcano erupting</h3>

<p>The eruption had begun at the Grimsvotn volcano.</p>

<p>Read more</p>

</a>
```
而在HTML 4.01里，〈a>標籤只能包裝超鏈接或者錨點,但是在HTML5里，<code>&lt;a&gt;</code>標籤通常是一個超鏈接，但是如果沒有指定 href 屬性，它只是一個放超級鏈接的地方

<code>&lt;b&gt;</code>

<code>&lt;b&gt;</code>標籤是用來指定一段文本為粗體，而在HTML5里，使用這標籤設定文本為粗體不再表達任何重要性。

<code>&lt;hr&gt;</code>

在HTML5里，<code>&lt;hr&gt;</code>標籤顯示一條水平線，並且在內容上標記了一個改動，而在HTML4.01里，它僅僅只顯示一個水平線。

<code>&lt;i&gt;</code>

<code>&lt;i&gt;</code>標籤在HTML5里不再唯一指定文字的斜體樣式（雖然它可以是斜體的）。它現在代表文字是變化的語音或心情，或者與普通文本不同。

刪除的標籤
除了新加入的標籤和修改的標籤，也有一些標籤HTML5不再支持，這些是：

<code>&lt;frame&gt;</code>,<code>&lt;frameset&gt;</code>和<code>&lt;noframes&gt;</code>: 這些標籤從HTML5中被移除了。

<code>&lt;font&gt;</code>：這個標籤曾經用來定義字體樣式、字體大小和顏色。

<code>&lt;s&gt;</code>和<code>&lt;strike&gt;</code>：這兩個標籤曾經用來定義帶刪除線的文本，現在用<code>&lt;del&gt;</code>標籤來代替。

<code>&lt;u&gt;</code>: 曾經用來定義帶下劃線的文本。

<code>&lt;center&gt;</code>：之前用來讓文字和內容居中。

<code>&lt;big&gt;</code>: 之前用來讓字體大一些。

<code>&lt;applet&gt;</code>： 以前用來定義一段嵌入的網頁小應用程序。HTML5建議使用<code>&lt;object&gt;</code>標籤來代替。

<code>&lt;acronym&gt;</code>： 這標籤在HTML 4.01里曾經用來定義首字母縮寫詞。如果一個縮寫詞是一個單詞，那麼它可以被讀出來，像NATO,NASA,ASAP,GUI。