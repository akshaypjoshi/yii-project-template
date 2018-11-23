<p align="center">
    <a href="http://www.yiiframework.com/" target="_blank">
        <img src="https://www.yiiframework.com/files/logo/yii.png" width="400" alt="Yii Framework" />
    </a>
    <h1 align="center">Yii Framework Project Template</h1>
    <br>
</p>

[Yii Framework] Project Template is a skeleton application best for
rapidly creating projects.

[Yii Framework]: http://www.yiiframework.com/

The template contains the basic features including user login/logout and a contact page.
It includes all commonly used configurations that would allow you to focus on adding new
features to your application.

[![Latest Stable Version](https://img.shields.io/packagist/v/yiisoft/yii-project-template.svg)](https://packagist.org/packages/yiisoft/yii-project-template)
[![Total Downloads](https://img.shields.io/packagist/dt/yiisoft/yii-project-template.svg)](https://packagist.org/packages/yiisoft/yii-project-template)
[![Build Status](https://travis-ci.org/yiisoft/yii-project-template.svg?branch=master)](https://travis-ci.org/yiisoft/yii-project-template)

DIRECTORY STRUCTURE
-------------------

```
config/             contains application configurations
public/             contains the entry script, published assets and other publicly available files e.g. favicon.ico and robots.txt
runtime/            contains files generated during runtime
vendor/             contains dependent 3rd-party packages
.env
.env.dist
composer.json
docker-compose.yml
```

REQUIREMENTS
------------
 

The minimum requirement by this project template that your Web server supports PHP 7.1.


INSTALLATION
------------

If you do not have [Composer](http://getcomposer.org/), you may install it by following the instructions
at [getcomposer.org](http://getcomposer.org/doc/00-intro.md#installation-nix).

You can then install this project template using the following command:

~~~
$ composer create-project --prefer-dist --stability=dev yiisoft/yii-project-template myapp
$ cd myapp
~~~

> Depending on your host system you might need to give write permissions to `./runtime` and `./public/assets`

### Web application

Choose an asset distribution system, e.g. if you plan to use a web-application base

*a) Asset-packagist & composer-merge-plugin*

    $ composer require "wikimedia/composer-merge-plugin" && \
    composer config repositories.ap '{"type": "composer", "url": "https://asset-packagist.org"}' && \
    composer config extra.merge-plugin.include "vendor/*/*/composer.assets.json"
        
*b) Foxy*

    $ composer require "foxy/foxy:^1.0.0"

Choose application base packages

    $ composer require yiisoft/yii-base-web

> You can find available application bases on [GitHub](https://github.com/yiisoft?utf8=✓&q=yii-base).

Now you should be able to access the application via `http://localhost:8080/`.

### Docker

Clone the repository and create the environment configuration file

    cp .env.dist .env

To run the installation create a bash from the PHP image

    docker-compose run --rm php bash
    
and run the `composer` commands above.
   
Start application stack

    docker-compose up -d
    
Access in your browser via

~~~
http://docker.host:30080
~~~

CONFIGURATION
-------------

### Database

Edit the file `config/db.php` with real data, for example:

```php
return [
    'class' => 'yii\db\Connection',
    'dsn' => 'mysql:host=localhost;dbname=yii2basic',
    'username' => 'root',
    'password' => '1234',
    'charset' => 'utf8',
];
```

**NOTES:**
- Yii won't create the database for you, this has to be done manually before you can access it.
- Check and edit the other files in the `config/` directory to customize your application as required.
- Refer to the README in the `tests` directory for information specific to basic application tests.


TESTING
-------

Tests are located in `tests` directory.

Run directly from Docker image

    docker run -it -v $PWD/yii-project:/app -w /app yiisoftware/yii2-php:7.2-apache bash