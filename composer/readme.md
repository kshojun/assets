# Tips 1  
```bash
$ composer install

Updating dependencies (including require-dev)
                                                                                           
  [ErrorException]                                                                         
  "continue" targeting switch is equivalent to "break". Did you mean to use "continue 2"?  
                                                                                          

update [--prefer-source] [--prefer-dist] [--dry-run] [--dev] [--no-dev] [--lock] [--no-custom-installers] [--no-autoloader] [--no-scripts] [--no-progress] [--no-suggest] [--with-dependencies] [-v|vv|vvv|--verbose] [-o|--optimize-autoloader] [-a|--classmap-authoritative] [--apcu-autoloader] [--ignore-platform-reqs] [--prefer-stable] [--prefer-lowest] [-i|--interactive] [--root-reqs] [--] [<packages>]...
```

```composer self-update```  
versionをあげて再度やってみる

### メモリ不足の場合
```bash
sudo /bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
sudo /sbin/mkswap /var/swap.1
sudo /sbin/swapon /var/swap.1
```


