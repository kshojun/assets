# エディタの設定変更
**Ctrl + Shift + p**で窓を出して設定キーワードを検索し、選択すれば設定できる  
例えば、窓に\>breadcrumsと打つと、View: Toggle Breadcrumbsなどが表示されるので、選択すればよい

# Cheatsheet
- **! + Tab** or **! + Enter**でHTML5のテンプレート文が表示される(**html:5 + Enter**でもいい)
- **div#app + Enter**で<div id="app"></div>

# WSL(Windows Subsystem for Linux)をいれる  
1. 管理者モードでPowerShellを起動し下記のコマンドを実行しWSLを有効化   
```C:\Windows\System32> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux```  

2. 再起動後、microsoft storeからubuntuをいれる  

3. ubuntuを起動しsudoできるユーザーを作る  

4. terminalのデフォルトshellをubuntuにする  
**Terminal: Select Default Shell**を選択し、WSL Bashを選択する  

5. nodejs使いたいのでいれる  
```apt-get update```  
```apt-get install nodejs```

# 入れるべきExtensions
1. Material Theme : 環境テーマ
2. Material Icon Theme : ファイル種類をアイコン表示
3. Prettier - Code formatter : コード自動整列
4. Bracket Pair Colorizer : ブロック括弧を色分け
5. indent-rainbow : インデントをレインボー色で鮮やかに
6. Auto Rename Tag : 開くタグと閉じるタグを同時修正
7. CSS Peek
8. HTML CSS SUPORT : CSS内容を自動補完
9. LIVE SERVER

# WSLからVSCodeを起動(WSL使える状態になってる)
```bash
$ cd workspace
$ code .
or
VSCode起動済みの場合はcmdでwsl打つ
```

# wslのsudoパスワードがわからない場合
```bash
# cmd.exe上で以下を実行してルートになればいい
wsl -u root
```
