# Laravel Share


Share links exist on almost every page in every project, creating the code for these share links over and over again can be a pain in the ass.
With Laravel Share you can generate these links in just seconds in a way tailored for Laravel.

### Available services

* Facebook
* Twitter
* Linkedin
* WhatsApp
* Reddit
* Telegram

## Installation

You can install the package via composer:

``` bash
composer require michelmelo/laravel-share
```


If you don't use auto-discovery, add the ServiceProvider to the providers array in config/app.php

```php
// config/app.php
'providers' => [
    MichelMelo\Share\Providers\ShareServiceProvider::class,
];
```

And optionally add the facade in config/app.php

```php
// config/app.php
'aliases' => [
    'Share' => MichelMelo\Share\ShareFacade::class,
];
```

Publish the package config & resource files.

```bash
php artisan vendor:publish --provider="MichelMelo\Share\Providers\ShareServiceProvider"
```

> You might need to republish the config file when updating to a newer version of Laravel Share

This will publish the ```laravel-share.php``` config file to your config folder, ```share.js``` in ```public/js/``` and ```laravel-share.php``` in your ```resources/lang/vendor/en/``` folder.

### Fontawesome

Since this package relies on Fontawesome, you will have to require it's css, js & fonts in your app.
You can do that by requesting a embed code [via their website](http://fontawesome.io/get-started/) or by installing it locally in your project.

### Javascript

Load jquery.min.js & share.js by adding the following lines to your template files.

```html
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="{{ asset('js/share.js') }}"></script>
```

## Usage

### Creating one share link

#### Facebook

``` php
Share::page('http://michelmelo.pt')->facebook();
```

#### Twitter

``` php
Share::page('http://michelmelo.pt', 'Your share text can be placed here')->twitter();
```

#### Reddit

``` php
Share::page('http://michelmelo.pt', 'Your share text can be placed here')->reddit();
```

#### Linkedin

``` php
Share::page('http://michelmelo.pt', 'Share title')->linkedin('Extra linkedin summary can be passed here')
```

#### Whatsapp

``` php
Share::page('http://michelmelo.pt')->whatsapp()
```

#### Telegram

``` php
Share::page('http://michelmelo.pt', 'Your share text can be placed here')->telegram();
```

### Sharing the current url

Instead of manually passing an url, you can opt to use the `currentPage` function.

```php
Share::currentPage()->facebook();
```
