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

#mixin
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
