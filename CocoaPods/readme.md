```bash
# rubyは既に入ってるので
sudo gem update --system
# 権限ないのでインストールできない（systemのrubyを使ってるため)
sudo gem install cocoapods
# which ruby
/usr/bin/ruby
# which ruby
/usr/bin/gem

# rbenvでrubyを入れてrbenvでrubyを管理する
$ brew install rbenv ruby-build
$ rbenv versions
* system (set by /Users/kshojun/.rbenv/version)

$ rbenv install -l
$ rbenv install 2.6.6
$ rbenv versions
* system (set by /Users/kshojun/.rbenv/version)
  2.6.6
 
# localはアプリごと
$ rbenv global 2.6.6

$ vi .bashrc
[[ -d ~/.rbenv  ]] && \
  export PATH=${HOME}/.rbenv/bin:${PATH} && \
  eval "$(rbenv init -)"
$ source .bashrc
$ which ruby
/Users/kshojun/.rbenv/shims/ruby
$ which gem
/Users/kshojun/.rbenv/shims/gem

$ brew install cocoapods
$ pod -v
$ pod setup
```
