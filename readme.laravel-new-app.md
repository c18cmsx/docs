# Založení nové Laravel aplikace

## Instalace Laravel

```
composer create-project --prefer-dist laravel/laravel <appname>
```

```
git init
git add .
git commit -m "initial commit"
```

Laravel autentikace (doporučuju vždy)
```

composer require laravel/ui

php artisan ui vue --auth

npm install && npm run dev
```
.env
- APP_NAME
- db connection
- mailtrap

config
- app
    - timezone => Europe/Prague
    - locale => cz
    
- do app/Providers/AppServiceProvider.php přidat:
```
use Illuminate\Support\Facades\Schema;
...
public function boot()
{
    Schema::defaultStringLength(191);
}
```

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

## vývoj
```
npm run watch
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
