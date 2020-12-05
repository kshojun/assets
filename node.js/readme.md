# Restful API作る
```
$ npm init
$ npm install express
```

# nodemon
- ソースコード変更時、いちいちnode xxx.jsを実行しなくて済む

# 本番環境
- node.jsを80番で動かすこともできるが、推奨されてない
- node.jsをpm2でサービス化してnginxのリバースプロキシで動かす
- pm2のクラスターモード使うとロードバランスもできる

# package.jsonの例
```js
{
  "name": "sample",
  "version": "1.0.0",
  "scripts": {
    "client": "cd client && npm start",
    "server": "nodemon server.js",
    # \"で挟んだやつを同時に実行し、一方が失敗した場合は他のやつも殺す
    "dev": "concurrently --kill-others-on-fail \"npm client\" \"npm server\""
  },  
  "dependencies": {
    "body-parser": "^1.18.3",
    "express": "^4.16.4",
  },
  "devDependencies": {
    "mocha": "^3.4.2"
  }
}
```

# version指定方法
- major.minor.patch
- 1.0.0: 1.0.0そのもの
- >1.0.0: 1.0.0より大きい
- >=1.0.0: 1.0.0以上
- 1.0.1 - 1.2.0: 1.0.1以上1.2.0以下
- 1.1.x: >=1.1.0 and <1.2.0
- 1.X: >=1.0.0 and <2.0.0
- *: any version
- ~1.1.1: >=1.1.1 and <1.2.0
- ~1.1: >=1.1.0 and <1.2.0
- ~1: >=1.1.0 and <2.0.0
- ^1.1.1: >=1.1.1 and <2.0.0
- ^0.1.1: >=0.1.1 and <0.2.0
