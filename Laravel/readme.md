# Trying to access array offset on value of type null ERROR
```php
 'message' => 'Trying to access array offset on value of type null',
   'string' => '',
   'code' => 0,
   'file' => '/media/sf_nami_api/vendor/illuminate/support/ServiceProvider.php',
   'line' => 84,
   'trace' => 
```
php7.4から
```php
$a = null;
echo $a[1];
```
でエラーになるようになった
```php
protected function loadViewsFrom($path, $namespace) {
    if (isset($this->app->config['view']['paths']) && is_array($this->app->config['view']['paths'])) {
    // isset($this->app->config['view']['paths'])を追加
        foreach ($this->app->config['view']['paths'] as $viewPath) {
            if (is_dir($appPath = $viewPath.'/vendor/'.$namespace)) {
                $this->app['view']->addNamespace($namespace, $appPath);
            }
        }
    }
    $this->app['view']->addNamespace($namespace, $path);
}
```
