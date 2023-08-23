# Description

[![Latest Version on Packagist](https://img.shields.io/packagist/v/proxify/proxify-php-code-style.svg?style=flat-square)](https://packagist.org/packages/proxify/proxify-php-code-style)
[![Total Downloads](https://img.shields.io/packagist/dt/proxify/proxify-php-code-style.svg?style=flat-square)](https://packagist.org/packages/proxify/proxify-php-code-style)

This package is a [Laravel Pint](https://laravel.com/docs/pint) preset for [Proxify](https://proxify.io) projects.

## Installation

You can install the package via composer:

```bash
composer require proxify/proxify-php-code-style --dev
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
These commands will use proxify code style rules by default, which are made on top of laravel preset.
For more details you can check [laravel pint docs](https://laravel.com/docs/pint)
Although it's not recommended, you still can use laravel pint commands directly
as well as custom pint.json config file.

### VSCode setup
Install Laravel pint plugin:
https://marketplace.visualstudio.com/items?itemName=open-southeners.laravel-pint

Add code style config path to `.vscode/settings.json`
```
"laravel-pint.configPath": "vendor/proxify/proxify-php-code-style/pint.json"
```

### PHPStorm setup

Create a new File watcher.

```
// Pint file watcher settings
$ProjectFileDir$/vendor//bin/proxify-cs-fixer
$FileRelativePath$
$FileRelativePath$
$ProjectFileDir$
```
![Watchers config](https://github.com/proxify-ab/proxify-php-code-style/blob/master/assets/file-watchers.jpg?raw=true)

To make phpstorm ctrl+alt+L hotkey work similar to pint configs, adjust code style by setting laravel and update

“Wrapping and Braces“->”Array initializer”->“align key-value pairs”

“Spaces“->”Around operators”->”Concatenation(.)”

![Editor Configs](https://github.com/proxify-ab/proxify-php-code-style/blob/master/assets/editor-configs.jpg?raw=true)

Disable `PHP` in the reformat code setting.
![reformat-code.jpg](https://github.com/proxify-ab/proxify-php-code-style/blob/master/assets/reformat-code.jpg?raw=true)

[Source Article](https://janostlund.com/2023-05-11/php-storm-laravel-pint#:~:text=If%20you%20want%20Laravel%20Pint,in%20code%20formatting%20for%20PHP)

[Laracasts Video](https://laracasts.com/series/phpstorm-for-laravel-developers/episodes/5)

### Github actions job
create a file in `.github/workflows/laravel_checks.yml`
or add the below step to your existing jobs workflow
```yml
  laravel-code-style:
    name: Code Style
    if: github.ref_name != 'master'
    runs-on: "ubuntu-20.04"
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: Cache Composer cache directory
        uses: actions/cache@v2
        with:
          path: ~/.composer/cache/files
          key: ${{ runner.os }}-composer-${{ hashFiles('composer.lock') }}
          restore-keys: ${{ runner.os }}-composer-

      - name: Install PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: "${{ env.php_version }}"
          extensions: "${{ env.php_extensions }}"
          tools: composer:v2.4

      - name: Install dependencies
        run: composer install --no-scripts --no-progress --no-suggest --prefer-dist --optimize-autoloader

      - name: Code style check
        run: |
          sh ./vendor/bin/proxify-cs-checker
```

### Pre-commit testing
install [pre-commit](https://pre-commit.com/#install) on your PC

Add this to your `.pre-commit-config.yaml`
```yaml
repos:
  - repo: local
    hooks:
      - id: laravel-pint
        name: laravel-pint
        entry: ./vendor/bin/proxify-cs-fixer
        language: script
        types: [php]
        pass_filenames: false
```

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

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
