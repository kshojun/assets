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
