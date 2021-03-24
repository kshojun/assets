# LEMP用docker-compose.yml
イメージをECR管理にしたいのでimageにECRのレポジトリを書いておく
```yml
version: "3"

services:
  web:
    image: xxxxx.dkr.ecr.ap-northeast-1.amazonaws.com/web:latest
    build: ./docker/web
    restart: always
    ports:
      - 80:80
    depends_on:
      - app
    volumes:
      # config file
      - ./docker/web/default.conf:/etc/nginx/conf.d/default.conf
      # log dir
      - ./docker/logs:/var/log/nginx
      # document root
      - .:/var/www/html
  app:
    image: xxxxx.dkr.ecr.ap-northeast-1.amazonaws.com/app:latest
    build: ./docker/app
    volumes:
      # config file
      - ./docker/app/php.ini:/usr/local/etc/php/php.ini
      # document root
      - .:/var/www/html
    depends_on:
      - db
  db:
    build: ./docker/db
    restart: always
    environment:
      MYSQL_DATABASE: peter
      MYSQL_SERVERNAME: localhost
      MYSQL_USER: user
      MYSQL_PASSWORD: password
      MYSQL_ROOT_PASSWORD: password
      TZ: 'Asia/Tokyo'
    ports:
      - 3306:3306
    volumes:
      # data dir
      - ./docker/db/data:/var/lib/mysql
      # init以下のsql, shを実行してくれる
      - ./docker/db/init:/docker-entrypoint-initdb.d
  swagger-api:
    image: xxxxx.dkr.ecr.ap-northeast-1.amazonaws.com/swagger-api:latest
    build: ./docker/swagger
    ports:
      - 8080:8000
    volumes:
      - ./docker/swagger/api.yml:/api.yml
    command: /api.yml
volumes:
  data: {}
```

# ECRにログイン
```bash
aws ecr get-login-password --region ap-northeast-1 | docker login --username AWS --password-stdin xxxxx.dkr.ecr.ap-northeast-1.amazonaws.com
```

# ビルド
```bash
docker-compose build
```

# ECRへPUSH
```bash
docker-compose push
```
