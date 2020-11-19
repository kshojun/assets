# n
```bash
# Installation of n
$ npm install n -g
# Confirm node.js version
$ n --stable
$ n --latest
# Installation of node.js
$ n latest or n stable
# Switch node.js version
$ n
# List of installed node.js
$ n ls
```

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
