# frontend 開発トレンド
昔はHTML, CSS, JavaScriptだけでよかったが、  
今はES6, npm, webpack, TypeScript。

# 検索時
keyword **mdn**で検索した方がいい

# 開発に必要なもの
- Chrome
- Git
- VSCode
- Vue.js devtools(Chrome Extension)
- Node.js

# VSCodeに入れるextension
- ビルトインサーバー **Live Server**
- Vue文法 **vetur**
- Vueコードスニペット **Vue VSCode Snippets**
- シンタックスチェック **ESLint, TSLint**
- ファイルアイコンテーマ **Material Icon Theme**
- 色テーマ **Night Owl**

# VSCodeの設定
**Ctrl + Shift + P**で窓を出す  
\>color theと打って、**Preference: color theme**を選択し、**night owl**を選択  
\>file iconと打って、**Preference: file icon theme**を選択し、**material icon theme**を選択

# インストール
htmlファイルに以下の文を追加

開発  
```<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>```

本番  
```<script src="https://cdn.jsdelivr.net/npm/vue"></script>```

# 実行方法
実行したいファイルを右クリックし**Open with Live Server**をクリック

# これだけ知っていればよい
- Vue.jsコア
- Vue Router
- Vuex
- Vue CLI
- Vue devtools

# Vue.jsの特徴
- コンポネント基盤
- MVVMパターン
- Two-way data binding, Virtual DOM

# HTTP通信
axiosを使う

# directive
- v-on
- v-model
- v-for

# Github Pagesに配布
githubのrepositoryを選択し、settingsのgithub pagesにあるsourceのブランチをmasterにすると  
xxx.github.io/repository/ というリンクができるのでこれを公開する。
これを使えば無料でWeb Appをいくらでも公開できる。

# 有用サイト
[MDN Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)  
[Web Fundamentals](https://developers.google.com/web/fundamentals)  
[Vue.js Developers](https://vuejsdevelopers.com/)  
[Vue.js Enterprise Boilerplate](https://github.com/chrisvfritz/vue-enterprise-boilerplate)  
[Vue.js](https://vuejs.org/index.html)  
[Vue CLI](https://cli.vuejs.org/)  
[Vue router](https://router.vuejs.org/)

# Sample Code
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <title>vue.js sample</title>
</head>
<body>
    <div id="app">
        {{ message }}
    </div>
    <script>
        let app = new Vue({
            el: "#app",
            data: {
                message: "abc"
            }
        })
    </script>
</body>
</html>
```
