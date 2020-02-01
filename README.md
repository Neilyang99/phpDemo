# phpDemo
use Laravel framework

Version:
apache: 2.4.41
php: 7.2.26
laravel: 6.13.1
laravel-admin: 1.7.9

install Step by step

1.install Laravel
    1.1 run: composer global require "laravel/installer"
    1.2 run: laravel new management
        note: management is a project name

2.install Laravel-admin 
    2.1 run: composer require encore/laravel-admin
    2.2 run: php artisan vendor:publish --provider="Encore\Admin\AdminServiceProvider"
    2.3 create DB schema: laravel
        note: utf8
    2.4 run: php artisan admin:install

3.setting apache vhost
    3.1 \xampp\apache\conf\extra的httpd-vhosts.conf : 
        ```
        <VirtualHost *:8080>
            DocumentRoot "F:\project\demo\management\public"
            ServerName localhost
            <Directory "F:\project\demo\management\public">
                AllowOverride ALL
                Require all granted
                Order Deny,Allow
                Allow from all
            </Directory> 
        </VirtualHost>
        ```
    3.2 restart apache
    3.3 url = http://localhost:8080/admin

4.add the path of upload folder: config/filesystems.php
    ```
    'admin' => [
            'driver'     => 'local',
            'root'       => public_path('upload'),
            'visibility' => 'public',
            'url' => env('APP_URL').'/public/upload/',
        ],
    ```
5.setting locale and Timezone: config/app
    5.1 'timezone' => 'Asia/Taipei',
    5.2 'locale' => 'zh-TW',
    5.3 clear cache:
        php artisan cache:clear
        php artisan view:clear
        php artisan config:cache
6.


