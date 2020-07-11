# jsにデータを渡すとき、json_encodeはphp側ではなく、js側でやる。php側でやると&quot;が混ざる
```javascript
var a = JSON.parse('<?php echo json_encode($something, JSON_UNESCAPED_UNICODE); ?>');
```
# メールアドレスチェック  
```php
private static function checkEmail($email) {
    switch ($email) {
        case !filter_var($email, FILTER_VALIDATE_EMAIL):
        case !preg_match("/^([a-zA-Z0-9])+([a-zA-Z0-9\._-])*@([a-zA-Z0-9_-])+([a-zA-Z0-9\._-]+)+$/", $email):
            return false;
        default:
            return true;
    }
}
```

# アップロードさせるファイルサイズ指定

upload_max_filesize = default 2M   
post_max_size = default 8M   
upload_max_filesizeだけ大きくしてもpost_max_sizeに引っかかってうまくいかない   
両方のパラメータをあげる必要がある。   
upload_max_filesize < post_max_size

# PHPDOC
```$ composer require --dev phpdocumentor/phpdocumentor```

```$ phpdoc run -d /コード -t /出力先```

composerで入らないので、

```$ cd vendor/bin```

```$ wget http://phpdoc.org/phpDocumentor.phar```

308エラーになる場合は、ブラウザからDLしてWinSCPでコピーして使う

```mv phpDocumentor.phar /media/sf_xxxx/fuel/vendor/bin```

vendor/binを環境変数で実行可能にしておく

phpDocumentor.pharで実行できる

# PHP7.4
```bash
$ yum install -y https://rpms.remirepo.net/enterprise/remi-release-7.rpm
$ yum install -y --enablerepo=remi-php74 php which
$ php -v
PHP 7.4.8 (cli) (built: Jul  9 2020 08:57:23) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
```
