<p align="center">CmsX - Dev</p>

# vytvoření dev pro vývoj package

## Instalace Laravel

```
composer create-project --prefer-dist laravel/laravel <dev_app_name>
```

## Vytvoření gitu

přepnout se do adresáře <dev_app_name>
```
git init
git add .
git commit -m "initial commit"
```

## Klon repozitáře

```
git clone git@github.com:c18cmsx/core.git <repo_name>
```

- přidat do composeru
```
"repositories": [
    {
        "type": "path",
        "url": "../path/to/your/package",
        "options": {
            "symlink": true
        }
    }
]
```
- zavolat
```
composer require "c18cmsx/core @dev"
composer update c18cmsx/core --prefer-source
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
- auth
    - providers/users/model => C18cmsx\Core\Models\User::class    

```
php artisan migrate --seed
#php artisan migrate:fresh --seed
```

nainstalovat
```
composer require barryvdh/laravel-debugbar --dev
```

zakomentovat
- routes/web.php... celé zakomentovat

## Nastavit v PHP Stormu

- Tools/File Watchers/Less

```
File type: Less Style Sheet
Scope: nastavit na cestu <REPO>:src/assets/less/*/*

Program: nastavit na less.cmd
Arguments: $FileName$ ..\..\css\$FileDirName$\$FileNameWithoutExtension$.css --source-map
Output paths to refresh: $FileNameWithoutExtension$.css:$FileNameWithoutExtension$.css.map

Advanced
Auto-save edited files to trigger the watcher: check
Trigger the watcher on external changes: check
ostatní nezaškrtávat
```

- v public vytvořit cestu vendor/c18app/

- spustit WINDOWS konzolu
```
mklink /D <cesta k DEV/public/vendor/c18app/cmsx> <cesta k REPO/src/assets>
```
