# Založení nové Laravel aplikace

## Instalace Laravel 8x

minimální verze PHP >= 7.3

```
composer create-project --prefer-dist laravel/laravel <appname>
```

přejít do nově vytvořeného adresáře

```
git init
git add .
git commit -m "initial commit"
```

**Laravel autentikace (doporučuju vždy)**

```
composer require laravel/jetstream
```

- a po té, jednu z následujících možností

```
php artisan jetstream:install livewire
php artisan jetstream:install livewire --teams
php artisan jetstream:install inertia
php artisan jetstream:install inertia --teams
```

- pak spustit příkaz

```
npm install && npm run dev
```

**config**

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

## vývoj

### přidání less (/webpack.mix.js) - vyměnit celý příkaz mix()

```
mix.js('resources/js/app.js', 'public/js')
    .postCss('resources/css/app.css', 'public/css/assets/app.css', [
        require('postcss-import'),
        require('tailwindcss'),
    ])
    .webpackConfig(require('./webpack.config'))
    .sass('resources/css/sass/app.scss', 'public/css/assets/app-scss.css')
    .less('resources/css/less/app.less', 'public/css/assets/app-less.css')
    .sourceMaps(true, 'source-map')
    .combine([
        'public/css/assets/app.css',
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
