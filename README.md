# Description

[![Latest Version on Packagist](https://img.shields.io/packagist/v/proxify/proxify-php-code-style.svg?style=flat-square)](https://packagist.org/packages/proxify/proxify-php-code-style)
[![Total Downloads](https://img.shields.io/packagist/dt/proxify/proxify-php-code-style.svg?style=flat-square)](https://packagist.org/packages/proxify/proxify-php-code-style)

This package is a [Laravel Pint](https://laravel.com/docs/pint) preset for [Proxify](https://proxify.io) projects.

## Installation

You can install the package via composer:

```bash
composer require proxify/proxify-php-code-style --dev
```

```bash
pint --config vendor/proxify/proxify-php-code-style/pint.json
```

## Usage
Check for [laravel pint docs](https://laravel.com/docs/pint)

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
$ProjectFileDir$/vendor/bin/pint
$FileRelativePath$
$FileRelativePath$
$ProjectFileDir$
```
![Watchers config]([..%2F..%2FDownloads%2Ffile-watchers.jpg](https://raw.githubusercontent.com/proxify-ab/proxify-php-code-style/master/assets/file-watchers.jpg?token=GHSAT0AAAAAABY6GVP6XAPFDZFGX665GYQAZHDS2GA))

To make phpstorm ctrl+alt+L hotkey work similar to pint configs, adjust code style by setting laravel and update

“Wrapping and Braces“->”Array initializer”->“align key-value pairs”

“Spaces“->”Around operators”->”Concatenation(.)”

![Editor Configs](https://raw.githubusercontent.com/proxify-ab/proxify-php-code-style/master/assets/editor-configs.jpg?token=GHSAT0AAAAAABY6GVP6OJZBQE5EY3NE43NOZHDSY5Q)

Disable `PHP` in the reformat code setting.
![reformat-code.jpg](https://raw.githubusercontent.com/proxify-ab/proxify-php-code-style/master/assets/reformat-code.jpg?token=GHSAT0AAAAAABY6GVP6MWHM2QWIBQXL2BA6ZHDS2WA)

[Source Article](https://janostlund.com/2023-05-11/php-storm-laravel-pint#:~:text=If%20you%20want%20Laravel%20Pint,in%20code%20formatting%20for%20PHP)

[Laracasts Video](https://laracasts.com/series/phpstorm-for-laravel-developers/episodes/5)

### Github actions job
create a file in `.github/workflows/pint.yml`
```yml
name: PHP Linting
on: pull_request
jobs:
  phplint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: "laravel-pint"
        uses: aglipanci/laravel-pint-action@2.0.0
        with:
          preset: laravel
          verboseMode: true
          testMode: true
```

### Pre-commit testing
Add this to your `.pre-commit-config.yaml`
```yaml
repos:
  - repo: local
    hooks:
      - id: laravel-pint
        name: laravel-pint
        entry: ./vendor/bin/pint
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
