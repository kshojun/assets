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
