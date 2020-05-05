### MISCONF Redis is configured to save RDB snapshots... error

vi /etc/redis.conf   
```
stop-writes-on-bgsave-error no
```
redis-cli shutdown NOSAVE   
redis-server --protected-mode no   

または   
redis-cliで   
```config set stop-writes-on-bgsave-error no```
と打つ。ただし、永久措置ではない。

### DENIED Redis is running in protected mode because protected mode is enabled... ERROR
 
vi /etc/redis.conf
```
protected-mode no
```
redis-cli shutdown NOSAVE   
redis-server --protected-mode no   

### IPアドレス許可
```
inbound rule編集
6379      172.x.x.x/32      other_server

$ sudo firewall-cmd --add-port=6379/tcp --zone=public --permanent
$ sudo firewall-cmd --reload

$ vi /etc/redis.conf
bind 172.x.x.x
protected-mode no

$ redis-cli shutdown NOSAVE

$ redis-server --protected-mode no &

$ redis-cli -h 172.x.x.x  これでOK
```
