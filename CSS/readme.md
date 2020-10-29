# Inline Style
HTML要素に直接CSSを記述。**使うべきでない**が、デバック時は使ったりする。  
```<div style="color:red;">text</div>```  

# 内部参照
styleタグに生で書く。ページ数が増えた時、変更が大変なので**使うべきでない**。  
```html
<head>
<style>
h1 {
  color: green;
}
.b {
  color:blue;
}
</style>
</head>
<body>
<div class="b">text</div>
```

# 外部参照
割と良く使う
```<link rel="stylesheet" type="text/css" href="some.css">```  

# Import Style
```@import url('some.css');```  
styleタグに書くこともできるが、Embedded Style同様、メンテナンスが大変なので  
CSSファイルの中で使うべき。CSSファイルにそのままIncludeする。  

# reset.css
ブラウザのデフォルトCSSを外し、ブラウザ間のスタイルの違いをなくす   
ただ、まっさらになるので<ul>などの・も表示されなくなる   
すべてのタグをカスタマイズしたいときに使う
```css
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

# sanitize.css
reset.cssはやりすぎなので、こちらを使い、こいつの次から自分のCSSを使う
```html
<link href="https://unpkg.com/sanitize.css" rel="stylesheet">
```

# 書き方  
セレクタ { 属性: 値; }  
div { font-size: 10px; }  

# セレクタ適用の優先順位
|element|score|
|---|---|
|*|0|
|type selector|1|
|class selector|10|
|id selector|100|
|inline style|1000|
|!important| - |

点数の高い方が優先される

```html
<style>
* { color:red; }
div { color:blue; }
.classl { color: orange; }
#id1 { color: pink; }
</style>
```  
styleが上記のようになってるとして  
```html
<body><div>test</div></body>
```  
*は0, divは1なのでtestは青になる。

```html
<body><div class="class1" id="id1">test</div></body>
```  
divは1,class1が10,id1が100なのでid1が優先された結果、pinkになる

```html
<body><div class="class1" id="id1" style="color:gray;">test</div></body>
```  
divは1,class1が10,id1が100,inline styleが1000なのでgrayになる

```html
<style>
* { color:red !important; }
div { color:blue; }
.classl { color: orange; }
#id1 { color: pink; }
</style>
```  
とすると、すべての優先順位を無視し!importantした要素が優先される。  
優先順位が同じ場合は後に書かれた方が優先される。

# padding  
paddingは枠の内側の余白  
padding: 10px 20px 30px 40px; 上 右 下 左(上から時計方向)  
padding: 10px 20px 30px; 上 左右 下  
padding: 10px 20px; 上下 左右  
padding: 10px; 上下左右  

```html
<style>
div { width: 100px; height: 100px; padding: 10px 10px 10px 10px; }
</style>
```

# margin  
marginは枠の外側の余白  
margin: 10px 20px 30px 40px; 上 右 下 左(上から時計方向)  
margin: 10px 20px 30px; 上 左右 下  
margin: 10px 20px; 上下 左右  
margin: 10px; 上下左右

padding-left, padding-right, margin-top, margin-bottomのようにひとつの方向に限定もできる  
ただし、padding-top: 20px; padding-bottom: 10px;のようにコード量が増える場合は  
padding: 20px 0 10px;のようにすれば簡潔に書ける  
あと、margin: 0 auto; 上下は0で左右はautoでブロック要素(div)を中央に配置できる

# border  
線が引ける  
border: 10px solid red;  太さ、線の種類、色。方向は上下左右。  
border-top: 10px solid red; 上にのみ線を引く  
```html
<style>
div { width: 100px; height: 100px; border: 10px solid red; }
</style>
```  
上下左右をそれぞれ指定することもできる。  
border-width: 1px 2px 3px 4px;  
border-style: solid double dotted dashed;  
border-color: black red blue orange;  

# box model  
```html
<style>
  div { padding:20px; width:100px; height:100px; border:10px solid red; }
</style>
```  
縦横100pxのボックスを描く場合、上記のように書くとpaddingの分だけボックスがデカくなり、線も太くなる。  
したがって予めpadding分を引いたwidth or heightを使わないといけない。  
