# pecl-build - Build pecl extension for multiple versions php.

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
% git clone https://github.com/crocos/pecl-build.git $PHPENV_ROOT/plugins/pecl-build
% phpenv pecl <package_name>
```

phpenv plugin follow php version for phpenv specified.
If you want specify build php version, you can set parameter.

```
% phpenv pecl <package_name> -j <php version>
% phpenv pecl <package_name> -a # build all php version by phpenv have.
```

*NOTICE: phpenv plugin versin is now skipped `system` environment build.*

you want specify package version:

```
% phpenv pecl <package_name>-<package_version>
```

and when you build `zend_extension`, pass `-z (--zend-extension)` option.
so created `.ini` config set `zend_extension`


## ChangeLog

### v0.1.0 2013/12/06

* Initial Version

AUTHOR:: Daichi Kamemoto <yudoufu@crocos.co.jp>

