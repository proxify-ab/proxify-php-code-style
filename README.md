# Description

[![Latest Version on Packagist](https://img.shields.io/packagist/v/proxify/proxify-php-code-style.svg?style=flat-square)](https://packagist.org/packages/proxify/proxify-php-code-style)
[![Total Downloads](https://img.shields.io/packagist/dt/proxify/proxify-php-code-style.svg?style=flat-square)](https://packagist.org/packages/proxify/proxify-php-code-style)
![GitHub Actions](https://github.com/proxify/proxify-php-code-style/actions/workflows/main.yml/badge.svg)

This is where your description should go. Try and limit it to a paragraph or two, and maybe throw in a mention of what PSRs you support to avoid any confusion with users and contributors.

## Installation

You can install the package via composer:

```bash
composer require proxify/proxify-php-code-style
```

## Usage

### Command line
```php
// checks new and modified files if they follow coding standar
sh vendor/bin/proxify-cs-checker
// fixes all project php files
php vendor/bin/proxify-cs-fixer
// fixes selected path files
php vendor/bin/proxify-cs-fixer app/Models
// fixes selected files
php vendor/bin/proxify-cs-fixer app/Models/User.php app/Models/Developer.php
```

### VSCode setup
Install Laravel pint plugin:
https://marketplace.visualstudio.com/items?itemName=open-southeners.laravel-pint

Add code style config path to `.vscode/settings.json`
```
"laravel-pint.configPath": "vendor/proxify/proxify-php-code-style/pint.json"
```

### PHPStorm setup

Create a new File watcher.
<img width="985" alt="image" src="https://github.com/proxify-ab/proxify-php-code-style/assets/9916806/d28cb170-6305-4ecb-9eda-9ccd49f71fb5">


```
// Pint file watcher settings
$ProjectFileDir$/vendor/bin/proxify-cs-fixer
$FileRelativePath$
$FileRelativePath$
$ProjectFileDir$
```

Disable `PHP` in the reformat code setting.
<img width="987" alt="image" src="https://github.com/proxify-ab/proxify-php-code-style/assets/9916806/b02b59be-9aaf-4c43-bf0b-d5f0d3fac9ca">

### Testing

```bash
composer test
```

### Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email chadidi97@gmail.com instead of using the issue tracker.

## Credits

-   [Abdellah Chadidi](https://github.com/chadidi)
-   [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
