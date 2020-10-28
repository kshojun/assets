# structure
## html4
![html4](https://github.com/kshojun/docs/blob/master/images/html4.png)
## html5
![html5](https://github.com/kshojun/docs/blob/master/images/html5.png)

```html
<!DOCTYPE html> <- html5以降はhtmlだけでいい
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
  </body>
</html>
```

# レンダリングエンジン
|browser|rendering engine|
|---|---|
|Chrome|Blink| <- Webkitから派生
|Edge|Webkit|
|Firefox|Gecko|
|Safari|Webkit|

# 表示可能イメージ形式
- jpeg : 写真
- png : イラスト、ロゴ。透明色の利用
- gif : アニメーション
- svg : ベクター形式（拡大しても劣化しない）

# グローバル属性
どんなタグにも入れられる
- id
- class
- lang : htmlタグに使うことが多い
- title
- style
- dir : 文字表記の方向 アラビア語などはrtl（右から）
- tabindex : タブキーで操作するときの順序指定(1～)
- accesskey : AでALT + Aでフォーカス
- hidden
- translate : 翻訳させるか否か(no/yes) 効かないブラウザもある
- spellcheck : スペルチェックするか
- contenteditable : 編集可能にするか(true/false)
- contextmenu : 右クリックメニュー指定
- draggable : ドラック可能か
- dropzone : ドロップされるとどうなるか

# 列挙型
決まったものしか入れられない translateなど

# 論理型
属性があれば有効 hidden

# Form Input Type
- text
- password
- search
- email
- url
- tel
- number
- range
- checkbox
- radio
- submit
- reset
- button
- image
- file
- color
- date
- month
- week
- time
- datetime-local
- hidden

# label
```html
<label><input type="checkbox">aaa</label> <- クリック領域が広がる
<label><input type="radio">aaa</label> <- クリック領域が広がる
```

# Tags in Head
```html
<meta charset="utf-8">
<meta name="description" content=""> <- 紹介文、250文字くらい ページトップにあればいい
<meta name="keyword"> <- 今や不要
<meta http-equiv="X-UA-Compatible" content="IE=edge"> <- 過去のIEの互換モード対応
<meta name="viewport" content="width=device-width,initial-scale=1"> <- スマホでみたとき
<meta name="robots" content="noindex,follow"> <- 検索ロボット用 nofollow無視してくれ followみてもいいよ
```

# Social Share時の情報
```html
facebook
<meta property="og:url" content="">
<meta property="og:title" content="">
<meta property="og:type" content="">
<meta property="og:description" content="">
<meta property="og:image" content="">
<meta property="og:locale" content="">

twitter
<meta property="twitter:card" content="">
<meta property="twitter:site" content="">
```

# URLが複数ある場合の正規化
```html
<link rel="canonical" href="">
```

# CSS
```html
<link rel="stylesheet" href="">
```

# JavaScript
```html
<script src=""></script>
```

# RSS Feed
```html
<link rel="alternate" type="application/rss+xml" title="" href="">
```

# 複数ページの前後
```html
<link rel="prev" href="">
<link rel="next" href="">
```

# スマホで自動番号の自動リンク
```html
<meta name="format-detection" content="telephone=no"> <- 電話番号リンク
<meta name="" content="">
```
