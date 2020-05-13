# Založení nové Laravel aplikace

## Instalace Laravel 7.x

minimální verze PHP >= 7.2.5

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

nainstalovat
```
composer require barryvdh/laravel-debugbar --dev
```

- routes\web.php

přidat
```
Route::redirect('/home', '/');
```
odstranit
```
Route::get('/home', 'HomeController@index')->name('home');
```

- odstranit soubor ```app\Http\Controllers\HomeController.php```

- odstranit soubor ```resources\views\home.blade.php```

- v souboru ```resources\views\welcome.blade.php```změnit obsah na:

```
@extends('layouts.app')
@section('content')
@endsection
```

## vývoj

### přidání less (/webpack.mix.js)

```
mix.js('resources/js/app.js', 'public/js')
    .sass('resources/sass/app.scss', 'public/css/assets/app-scss.css')
    .less('resources/less/app.less', 'public/css/assets/app-less.css')
    .sourceMaps(true, 'source-map')
    .combine([
        'public/css/assets/app-scss.css',
        'public/css/assets/app-less.css'
    ], 'public/css/app.css')
    .version();
```

``` 
asset('...') => mix('...')
```

```
npm run watch
```

### přidání fontawesome.com

```
composer require components/font-awesome
```

- do webpack.mix.js přidat do .combine
```
'vendor/components/font-awesome/css/all.css'
```

- do webpack.mix.js přidat
```
.copyDirectory('vendor/components/font-awesome/webfonts', 'public/webfonts')
```

## první nasazení

```
git clone <repozitář>
```

```
composer install --no-dev
```

```
php -r "file_exists('.env') || copy('.env.example', '.env');
```

```
php artisan key:generate --ansi
```

nastavit .env
```
APP_ENV=production
```
