### Install phinx
```$ composer require robmorgan/phinx```

fuel/vendor/binにphinxコマンドができる

```$ fuel/vendor/bin/phinx init```

phinx.ymlができるので、

migrations: '%%PHINX_CONFIG_DIR%%/db/migrations'を
migrations: '%%PHINX_CONFIG_DIR%%/fuel/app/migrations'

```$ phinx create AddSample```

migrationsにxxxxx_add_sample.phpができる

```$ phinx status```

```
Status  [Migration ID]  Started              Finished             Migration Name 
----------------------------------------------------------------------------------
     up  20191118101216  2019-11-18 10:16:45  2019-11-18 10:16:45  AddSample
```

DB別に使いたいので
phinx_db1.yml
phinx_db2.yml

migrations/db1
migrations/db2

```phinx create  -c phinx_db.yml```

```phinx migrate -e environment  -c phinx_db.yml```
