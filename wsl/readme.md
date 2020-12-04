# root
```bash
$ wsl -u root
```

# パッケージのアップデート
```bash
$ apt-get -y update
$ apt-get -y upgrade
$ apt-get -y dist-upgrade
$ apt-get autoremove
```

# nodejsをインストール
```bash
$ curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
$ apt-get install -y nodejs
```

# パスを変更
```bash
$ vi ~/.profile
# 最後尾にPATH="$HOME/bin:$HOME/.local/bin:$PATH" を追記
$ source ~/.profile
$ node -v
$ npm -v
```
