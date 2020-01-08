# 變數

一個網站常常有一個基本的底色，這樣才會一致，那我們就可以把一些顏色定義為變數，在該使用的地方直接使用變數就好了，以後想要改顏色只要改變數即可

```css
$info:#B9CAD4;
$error:red;
$success:#064B74;
.info-area {
  color: $info;
  border: 1px solid $success;
}
```

底線（\_）和連結線（-）的使用可以互換，舉例來說，雖然下面定義的變數名稱是 $bg\_black，但是一樣可以透過 $bg-black 提取：

```css
$bg_black: #333;

.block1 {
  background-color: $bg_black;
}

.block2 {
  background-color: $bg-black;
}
```

## 全域變數（!global）

這些變數只有在它所定義的階層中有效，因此如果想定義的是全域變數，可以使用 $ 將變數定義在最外層，或者是用 !global 標籤來定義全域變數：

```css
$black: '#CCC';

body {
  background-color: $black;
  $width: 100% !global;     // 這個 $width 會變成全域變數
  width: $width;
}
```

## 預設變數（!default）

對某一個變數後方加上 !default 後，如果這個變數有被賦值過，則使用該值，如果沒有被賦值過，則使用預設值：

```css
// SCSS
$gray: #EAEAEA;

$black: #333 !default;      // $black 沒被賦值過，所以會套用預設值
$gray: #CACACA !default;    // $gray 被賦值過，所以不會套用預設值

.block {
  background-color: $black;
  color: $gray;
}
```

編譯後：

```css
/* CSS */
.block {
  background-color: #333;
  color: #EAEAEA;
}
```

