# node.js version管理
```bash
# Confirm node.js version
$ node -v
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

# npm自体のVer上げる
```bash
$ npm install -g npm@latest
```

# npmが壊れたら
globalのnode_modulesを消して、
```bash
$ npm install -g npm@latest
```

# npm list -gでパッケージが見つからずエラー
```bash
npm update -g
```
