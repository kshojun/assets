# Install

```
wget https://files.phpmyadmin.net/phpMyAdmin/4.8.5/phpMyAdmin-4.8.5-all-languages.zip
unzip phpmyadmin.zip
mv phpmyadmin pm
mv pm DOCUMENT_ROOT/
cd DOCUMENT_ROOT
mv config.sample.inc.php config.sample.php 
```

# Setting
```
vi config.sample.php
```

```php
$cfg['Servers'][$i]['controlhost'] = '';
$cfg['Servers'][$i]['controlport'] = '';
$cfg['Servers'][$i]['controluser'] = 'USER';
$cfg['Servers'][$i]['controlpass'] = 'PW';

$cfg['LoginCookieValidity'] = 86400;
$cfg['SendErrorReports'] = 'never';
```

# Session Error
```
Error during session start; please check your PHP and/or webserver log file and configure your PHP installation properly. Also ensure that cookies are enabled in your browser.

session_start(): open(SESSION_FILE, O_RDWR) failed: Permission denied (13)

session_start(): Failed to read session data: files (path: /var/lib/php/session)
```

```
$ sudo chmod 777 -R /var/lib/php/session
```
