# php-coverage-ensure

A composer package that provides a PHP CLI script able to clover.xml coverage reports and return non-zero when percent coverage is below specified threshold. Intended for use with automated test/build tools like Travis CI, Circle CI and Jenkins.


## Requirements

* PHP 7.0+
	* php-xdebug extension
	* phpunit, for generating code coverage reports


## Installation

```shell
# In your project:
$ composer require --dev beporter/php-coverage-ensure
```


## Usage

Before calling the script, you must produce a clover coverage report for your project. This can be done with PHPUnit.

```shell
$ vendor/bin/phpunit --coverage-clover tmp/clover.xml
```

Then call the script providing the path to a clover XML coverage report file and an optional minimum acceptable percentage.

```shell
$ vendor/bin/coverage-ensure tmp/clover.xml 80
```


### Advanced Usage

If you want PHPUnit to _always_ generate a clover report, you can also add the following block to your `phpunit.xml` or `phpunit.xml.dist` file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<phpunit
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="https://schema.phpunit.de/6.3/phpunit.xsd"
>
    <!-- ... -->

    <!-- Always generate a clover coverage report. -->
    <logging>
        <log type="coverage-clover" target="tmp/clover.xml"/>
    </logging>

</phpunit>
```

This package also includes a helper script that can determine the location of your clover report file by reading your phpunit config file:

```shell
$ vendor/bin/coverage-ensure `vendor/bin/clover-path-from-phpunit` 80
```


## Contributing


### Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms. [Translations are available](https://www.contributor-covenant.org/translations).


### Reporting Issues

Please use [GitHub Isuses](https://github.com/beporter/php-coverage-ensure/issues) for listing any known defects or issues.


### Development

Please fork this repository, create a new topic branch, and submit a [pull request](https://github.com/beporter/php-coverage-ensure/issues) for your work.


## Credits

This work was originally done as a part of [loadsys/cakephp-shell-scripts](https://github.com/loadsys/CakePHP-Shell-Scripts) and broken out here for greater portability/reuse.


## License

[MIT](LICENSE.md)


## Copyright

Copyright &copy; 2018 Brian Porter
