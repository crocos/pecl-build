# pecl-build - phpenv plugin for installing pecl extensions

## How to use

For usage details, run with `--help`.

### Use standalone

```
% git clone https://github.com/crocos/pecl-build.git
% cd pecl-build
% bin/pecl-build <package_name>
```

When run standalone, the extension is built against the system's default PHP version.
To use a different PHP version, specify the `phpize` and `php-config` binaries with parameters.

```
$ bin/pecl-build <package_name> -p /path/to/phpize -i /path/to/php-config
```

### Use phpenv plugins

```
% git clone https://github.com/crocos/pecl-build.git $(phpenv root)/plugins/pecl-build
% phpenv pecl <package_name>
```

As a phpenv plugin, it builds against the PHP version phpenv has selected.
To build for a specific PHP version, pass a parameter instead.

```
% phpenv pecl <package_name> -j <php version>
% phpenv pecl <package_name> -a # build for every PHP version phpenv has installed.
```

*NOTE: the phpenv plugin skips the `system` environment when building.*

To specify a package version:

```
% phpenv pecl <package_name>-<package_version>
```

When building a `zend_extension`, pass the `-z` (`--zend-extension`) option,
so the generated `.ini` file sets `zend_extension` instead of `extension`.


## ChangeLog

### v0.3.0 2026/08/19

* Use HTTPS for pecl.php.net package downloads
* Fix a crash when downloading a missing/invalid package (404 from pecl.php.net):
  validate the tarball name up front and verify gzip integrity before extracting
* Add the Summary/Usage comment block phpenv's help system requires, so
  `phpenv pecl -h`/`--help` shows real help instead of "Sorry, this command
  isn't documented yet."
* Make `phpenv pecl` (no package given) print the same help text as
  `phpenv pecl -h`, instead of a separate, out-of-sync usage message
* Use `$(phpenv root)` instead of `$PHPENV_ROOT` in the docs

### v0.2.0 2026/02/11

* Fix package downloads and fix typos

### v0.1.0 2013/12/06

* Initial Version

AUTHOR:: Daichi Kamemoto <yudoufu@crocos.co.jp>

