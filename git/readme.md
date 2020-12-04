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

# リモートレポジトリ追加
```bash
$ git remote add origin https://github.com/kshojun/tutorial-react.git
$ git remote -v
# 初回のみ
$ git push --set-upstream origin master
# 次回から
$ git push
```

