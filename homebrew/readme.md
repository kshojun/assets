# Installation
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
brew -v
```

# nodebrew (node.vs version管理)
```bash
brew install nodebrew
nodebrew -v
```

# Install latest node.js
```bash
mkdir -p ~/.nodebrew/src
nodebrew install-binary latest
nodebrew list
nodebrew use v15.3.0
node -v
npm -v
```

# nodebrew ver指定してインストール
```bash
nodebrew ls-remote
nodebrew install vxx.xx.xx
nodebrew list
nodebrew use vxx.xx.xx
node -v
npm -v
```

# .bash_profileにPATHを通す
```
if [ -f ~/.bashrc ] ; then
. ~/.bashrc
fi
export PATH=$PATH:$HOME/.nodebrew/current/bin
```
