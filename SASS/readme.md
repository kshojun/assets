拡張子はscss   

css
```html
.container h1 {
    color: red;
}

.container p {
    color: blue;
}
```

scss
```html
.container {
  h1 {
    color: red;
  }
  p {
    color: blue;
  }
}
```

# Install VSCode Extensions
- Live Sass Compiler
- Beutify css/sass/scss/less

# Using Live Sass Compiler
scss fileをクリックし、Watch Sassをクリックするとmapファイルとcssファイルができあがる
mapファイルはcssファイルとscssファイルの行番号をマッピングさせるためのもの
mapファイルとscssファイルが同じとこにあればdeveloper toolで要素を検証したとき、scssファイルを参照してくれる

# Using Beutify css/sass/scss/less
Shift+Ctrl+Pでbeutifyを選択

# Nesting
```html
a {
    color: #fff;
}

a:hover {
    text-decoration: none;
}
```

```html
a {
    color: #fff;

    &:hover {
        text-decoration: none;
    }
}
```

# Variables
```html
$btn-width: 100px;

.btn {
    width: $btn-width;

    &.btn-large {
        width: $btn-width * 2;
    }

    &.btn-small {
        width: $btn-width / 2;
    }
}
<a href="#" class="btn">A</a>
<a href="#" class="btn btn-large">B</a>
```

```html
$selector: '.btn.btn-large';

/* セレクタの場合は#をつける */
#{$selector} {
    width: 100px;
}
```

# mixin
```html
.box {
    width: 100px;
    margin: 0 auto; /* 真ん中に */
}
img {
    display: block; /* インライン要素なのでblockにしないと効かない */
    margin: 0 auto; /* 真ん中に */    
}
button {
    display: block; /* インライン要素なのでblockにしないと効かない */
    margin: 0 auto; /* 真ん中に */    
}

<div class="container">
    <div class="box">box</div>
    <img src="https://picsum.photos/200/200">
    <button>button</button>
</div>
```

```html
@mixin align-center {
    display: block;
    margin: 0 auto;
}

/* 引数あり */
@mixin align-center2($margin) {
    display: block;
    margin: $margin auto;
}

/* default値 */
@mixin align-center2($margin: 3px) {
    display: block;
    margin: $margin auto;
}

.box {
    width: 100px;
    margin: 0 auto; /* 真ん中に */
}
img {
    @include align-center;
}
button {
    @include align-center2();/* デフォルト値 */
    @include align-center2(10px);
}

<div class="container">
    <div class="box">box</div>
    <img src="https://picsum.photos/200/200">
    <button>button</button>
</div>
```

# extend
```html
.btn {
    background-color: #ccc;
    padding: 5px 10px;
    border-radius: 5px;
    color: #333;
    text-decoration: none;
}

.btn-alert {
    background-color: #fcc;
}
<a href="#" class="btn">button</a>
<a href="#" class="btn btn-alert">button</a> /* 指定が面倒 */
```

```html
.btn {
    background-color: #ccc;
    padding: 5px 10px;
    border-radius: 5px;
    color: #333;
    text-decoration: none;
}

.btn-alert {
    @extend .btn;
    background-color: #fcc;
}
<a href="#" class="btn">button</a>
<a href="#" class="btn-alert">button</a> /* btn-alertだけでいい、ただし#cccで描いたあとに#fccで上書きするので背景色だけ分けたい */
```

```html
/* %はscss専用,cssにはない */
%btn {
    padding: 5px 10px;
    border-radius: 5px;
    color: #333;
    text-decoration: none;
}

.btn-default {
    @extend %btn;
    background-color: #ccc;
}

.btn-alert {
    @extend %btn;
    background-color: #fcc;
}
<a href="#" class="btn-default">button</a>
<a href="#" class="btn-alert">button</a>
```

# 関数
```html
$width: 100px;

.boxNormal {
    width: $width / 3;/* 33.33333...  */
}

.boxCeil {
    width: ceil($width / 3);/* 34px */
}

.boxFloor {
    width: floor($width / 3);/* 33px */
}

.boxRound {
    width: round($width / 3);/* 33px */
}
```

```html
.container {
    width: 800px;
    margin: 0 auto;

    $margin: -20px;
    h1 {
        background-color: #ccc;
        margin-left: $margin;/* 見出しの背景をはみ出させる */
        padding-left: abs($margin);/* 文字はそのまま */
        text-shadow: 1px 1px 1px rgba(#ccc, .3); /* rgba(200,200,200,.3)のように書かなくてもよい */
        color: lighten(black, 50%);/* 50%明るく */
        color: darken(#fcc, 50%);/* 50%暗く */
    }
}

<div class="container">
    <h1>Sass</h1>
    <p>Sass...</p>
</div>
```

```html
@function half($value) {
    @return ceil($value / 2);
}

.box {
    width: half(101px);
}
```

# Comment
```html
h1 {
    // これはcssファイルには表示されない scssのみ使える
    /* これは表示される  */
    /*! compressedにしてもcssファイルに表示される */
}
```

# import
```html
@import url("head.css");/* ファイルの数分ダウンロードしないといけない */
@import "head.scss"; /* こうするとファイルはひとつで済むが、mapファイルやcssファイルができる */
@import "_head.scss"; // cssファイルなどを生成しない
@import "head"; // これでもいい（ファイル名は_head.scssだが）
```

# for
```html
// 5未満まで(1~4)
@for $i from 1 to 5 {
    .level_#{$i} {
        font-size: 2px * $i;
    }
}

// 5以下まで(1~5)
@for $i from 1 through 5 {
    .level_#{$i} {
        font-size: 2px * $i;
    }
}
```

# while
```html
$i: 1;
@while $i < 5 {
    .level_#{$i} {
        font-size: 2px * $i;
    }
    $i: $i + 1;
}
```
