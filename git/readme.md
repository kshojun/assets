# git hooks
git pushしたらshell(post-receive)実行してソース最新にする  
なお.gitの下にあるファイルなのでgit管理下には入らない

```
vi .git/hooks/post-receive  
chmod +x post-receive
```
shellは
```
#!/bin/sh

cd /home/project
git --git-dir=.git pull
```
# commit rule
- フェーズごとにコミットする
- コミット内容を構造的に
https://udacity.github.io/git-styleguide/
