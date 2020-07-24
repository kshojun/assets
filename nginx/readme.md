# wwwあり⇒wwwなしにリダイレクト(ドメイン正規化)
```
# Aレコードで0.0.0.0のグローバルIPアドレスにexample.comのドメイン名が紐付けられている
example.com IN A 0.0.0.0 
# CNAMEレコードでwww.example.comのドメイン名にexample.comのドメイン名が紐付けられている
example.com IN CNAME www.example.com 
```

```
server {
    listen       80;
    server_name  www.xxxxx.jp;
    return       301 http://xxxxx.jp$request_uri;
    ...
}

server {
    listen       80;
    server_name  xxxxx.jp;
    ...
}
```
nginx再起動

# wwwとwwwなしどっちもアクセスさせる(SEO的に不利かも)
```
example.com IN A 0.0.0.0 
www.example.com IN A 0.0.0.0
```

```
server {
    listen       80;
    server_name  .xxxxx.jp; # www.xxx.jp xxx.jp;でもいい
}
```
nginx再起動

# 413 Request Entity Too Large
設定ファイルに
```nginx
server {
  client_max_body_size 100M;
  ...
}
```
を追加

# BASIC認証
APACHEじゃないので、htpasswdが使えないので入れる
```
$ sudo yum install httpd-tools
```

```
$ sudo htpasswd -c /etc/nginx/.htpasswd username
New password: password
Re-type new password: password
Adding password for user username
```

```
$ vi /etc/nginx/conf.d/xxx.conf
location / {
  auth_basic "Restricted"; 
  auth_basic_user_file /etc/nginx/.htpasswd;
}
```

```
sudo systemctl restart nginx
```

# IP制限
```nginx
# ALB経由の場合も実IPを取得
set_real_ip_from 0.0.0.0/0;
real_ip_header X-Forwarded-For;
real_ip_recursive on;

allow 223.XXX.XXX.XXX;
deny all;
```
