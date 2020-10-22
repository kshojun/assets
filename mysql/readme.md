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

### MySQL 5.7 Install
```
$ sudo rpm -Uvh http://dev.mysql.com/get/mysql57-community-release-el7-7.noarch.rpm

$ sudo yum install mysql-community-server

$ mysql -V
mysql  Ver 14.14 Distrib 5.7.27, for Linux (x86_64) using  EditLine wrapper

$ sudo systemctl start mysqld
$ sudo systemctl enable mysqld

$ sudo  cat /var/log/mysqld.log | grep password
2020-02-17T13:04:07.911877Z 1 [Note] A temporary password is generated for root@localhost: 4X9E2QbvQW/d

$ mysql_secure_installation
全部y

$ sudo vim /etc/my.cnf
： # 下記2行を末尾に追加
character-set-server=utf8
default_password_lifetime=0
$ sudo systemctl restart mysqld
```

### rootパスワードをリセット
mysqld_safeはなくなった   
```
$ systemctl stop mysqld
$ systemctl set-environment MYSQLD_OPTS="--skip-grant-tables"
$ systemctl start mysqld
```

### Slow query
```
事前に作っておく
$ touch /var/log/slow_query.log
$ chown mysql:root /var/log/slow_query.log # logrotateを考えてroot groupにしておく
$ chmod g+w /var/log/slow_query.log

[mysqld]
slow_query_log='ON'
long_query_time = 2
log_queries_not_using_indexes = 'ON' # インデックス貼ってないクエリを出力。これをONにすると実行時間関係なく出力される
slow_query_log_file = /var/log/slow_query.log

わざと出す
select sleep(3);

-s ソート
at Queryの平均実行時間
c Queryの出現回数
ar Query内で取得/更新した合計レコード行数
t Queryの合計実行時間
$ mysqldumpslow -s t /var/log/slow_query.log
```

### ぶっ壊れたら
```
datadirに行ってIB系ファイルとDBディレクトリを消す
cd /var/lib/mysql
rm ibdata1 ib_logfile0 ib_logfile1
rm -rf [db]
systemctl restart mysqld

データディレクトリごと消す
rm -rf /var/lib/mysql
systemctl start mysqld
cat /var/log/mysqld.log | grep 'temporary password'
ログインできるはず
```

```sql
UPDATE master_an ma
INNER JOIN (
	SELECT
		ma.id
		, mq.code
		, (
			SELECT count(0) FROM master_an inma
			WHERE inma.question_id = ma.question_id
				AND	inma.id <= ma.id
		) num
	FROM master_q mq
	INNER JOIN master_an ma
		ON	ma.question_id = mq.id
) uni
	ON	uni.id = ma.id
SET
	ma.code = concat(uni.code,'-',uni.num)
	, ma.number = uni.num;

ALTER TABLE `master_an`
ADD UNIQUE INDEX (`code`) USING BTREE ,
ADD UNIQUE INDEX (`question_id`, `number`) USING BTREE;
```
