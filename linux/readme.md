# timezone変更
```
# date  
Tue Dec 17 10:07:12 UTC 2019  

# strings /etc/localtime  
TZif2  
TZif2  
UTC0  
```
UTCになってる  

JSTに変更  
```ln -sf  /usr/share/zoneinfo/Asia/Tokyo /etc/localtime```  

```
# strings /etc/localtime
TZif2
TZif2
JST-9

# date  
Tue Dec 17 19:11:44 JST 2019
```
JSTになってる

```
# vi /etc/sysconfig/clock
ZONE="UTC"
UTC=true
```
このままでは再起動したらUTCに戻るので、falseにする

あと、crondも再起動しないといけない  
```systemctl restart crond```

# postfix
```
# yum install postfix  
# systemctl start postfix
# systemctl enable postfix
インストール確認  
# postconf  | grep mail_version
# which postfix  
/usr/sbin/sendmail
```

# scp
権限ないファイルを落とす   
```ssh -i ~/xxx.pem w1 "sudo cat /var/log/nginx/xxx_api_access_log" > access_log1```

# SSHの接続アカウント発行
```bash
@client
# PuttyGenで鍵ペアを作る

@server
# ユーザー追加
$ useradd [username]
# sudoになるとき使うパスワード
$ passwd [username] 
# sudo権限与える
$ usermod -G wheel [username]
# group確認
$ groups [username] or id [username]

$ mkdir /home/[username]/.ssh
$ chmod 700 /home/[username]/.ssh
$ chown <ユーザー名> /home/<ユーザー名>/.ssh
$ chgrp <ユーザー名> /home/<ユーザー名>/.ssh
$ cd /home/[username]/.ssh
# 公開鍵を保存
$ cat [public key] > /home/[username]/.ssh/authorized_keys  <-- これはダメ
# puttyGenの文字列をそのままコピーし、authorized_keysに貼り付ける（改行が含まれないように）

$ chmod 600 /home/<ユーザー名>/.ssh/authorized_keys
$ chown <ユーザー名> /home/<ユーザー名>/.ssh/authorized_keys
$ chgrp <ユーザー名> /home/<ユーザー名>/.ssh/authorized_keys
```

# ImageMagick Installation
```bash
$ yum install -y ImageMagick
$ convert -version
Version: ImageMagick 6.9.10-68 Q16 x86_64 2020-04-01 https://imagemagick.org
Copyright: © 1999-2019 ImageMagick Studio LLC
License: https://imagemagick.org/script/license.php
Features: Cipher DPC Modules OpenMP(3.1) 
Delegates (built-in): bzlib cairo fontconfig freetype gslib jng jpeg lcms ltdl lzma openexr pangocairo png ps rsvg tiff wmf x xml zlib
```

# logrotate
```bash
$ yum list installed | grep logrotate

$ vi /etc/logrotate.d/mysql_slow
/var/log/slow_query.log {
    daily
    missingok
    rotate 7
    nocompress
    notifempty
    dateext
    postrotate
      mysql -uroot -pxxxxxx -e 'FLUSH SLOW LOGS'
    endscript
}

# 再起動は不要

# dry-run
$ logrotate -dv /etc/logrotate.d/mysql_slow
reading config file /etc/logrotate.d/mysql_slow
Allocating hash table for state file, size 15360 B

Handling 1 logs

rotating pattern: /var/log/slow_query.log  after 1 days (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/slow_query.log
  log does not need rotating (log has been already rotated)
```
