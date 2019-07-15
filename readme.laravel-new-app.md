# Založení nové Laravel aplikace

## Instalace Laravel

```
composer create-project --prefer-dist laravel/laravel <appname>
```
Laravel autentikace (doporučuju vždy)
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

```
php artisan migrate
#php artisan migrate:fresh
```
vyprázdnit
- public/css/app.css
- public/js/app.css

nainstalovat
```
composer require barryvdh/laravel-debugbar --dev
```

## první nasazení

```
git clone <repozitář>
```

```
composer install --no-dev
```

nastavit .env
```
APP_ENV=production
```
