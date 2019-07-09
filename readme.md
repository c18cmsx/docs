<p align="center">CmsX - Demo</p>

# vytvoření aplikace

## Instalace Laravel

```
composer create-project --prefer-dist laravel/laravel <appname>
```

## Vytvoření gitu

přepnout se do adresáře <dev_app_name>
```
git init
git add .
git commit -m "initial commit"
```

- přidat CMSX
```
composer require "c18cmsx/core 0.0.1"
```
Laravel autentikace
```
php artisan make:auth
```
.env
- APP_NAME
- db connection
- mailtrap

config
- app
    - timezone => Europe/Prague
    - locale => cz
- database
    - charset => utf8
    - collation => utf8_unicode_ci
    - engine => InnoDB
- auth
    - providers/users/model => C18app\Cmsx\Models\User::class    

```
php artisan migrate --seed
#php artisan migrate:fresh --seed
```
vyprázdnit
- public/css/app.css
- public/js/app.css

nainstalovat
```
composer require barryvdh/laravel-debugbar --dev
```

upravit:
- routes/web.php

vypublikovat
```
php artisan vendor:publish --tag=c18app_cmsx
#php artisan vendor:publish --tag=c18app_cmsx --force
```
