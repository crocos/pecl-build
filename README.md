# pecl-build - phpenv plugin for installing pecl extensions

## How to use

If you want usage detail, type `--help`.

### Use standalone

```
% git clone https://github.com/crocos/pecl-build.git
% cd pecl-build
% bin/pecl-build <package_name>
```

When standalone, build php version is system default.
If you want use other php version, you can change `phpize` and `php-config` command by parameter.

```
$ bin/pecl-build <package_naem> -p /path/to/phpize -i /path/to/php-config
```

### Use phpenv plugins

```
% git clone https://github.com/crocos/pecl-build.git $(phpenv root)/plugins/pecl-build
% phpenv pecl <package_name>
```

phpenv plugin follow php version for phpenv specified.
If you want specify build php version, you can set parameter.

```
% phpenv pecl <package_name> -j <php version>
% phpenv pecl <package_name> -a # build all php version by phpenv have.
```

*NOTICE: phpenv plugin version is now skipped `system` environment build.*

you want specify package version:

```
% phpenv pecl <package_name>-<package_version>
```

and when you build `zend_extension`, pass `-z (--zend-extension)` option.
so created `.ini` config set `zend_extension`


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

