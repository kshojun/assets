### パスワードチェック無効
```bash
[mysqld]
validate-password=OFF 
```

### rootパスワード変更
```
$ mysqladmin password [newpassword] -u root -p
Enter password:
```

### IPアドレス許可
```
grant all privileges on *.* to root@"172.%.%.%" identified by 'xxxxxxx' with grant option;
flush privileges;
```

### firewall
```bash
$ sudo firewall-cmd --add-service=mysql --zone=public --permanent
$ sudo firewall-cmd --add-source=172.x.x.x --zone=public --permanent
$ sudo firewall-cmd --reload
```

### Inbound Rule編集
```
MySQL/Aurora   172.x.x.x/32      other_server
```
