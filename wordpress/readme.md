# wp-login.php, /wp-adminをベーシック認証かける
```bash
$ yum install -y httpd-tools

$ htpasswd -c /etc/nginx/.htpasswd [username]
New password: password
Re-type new password: password
Adding password for user username
```

# themeをインストール
zipファイルを解凍して、/var/wp/wp-content/themesに入れる
