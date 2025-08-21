# pecl-build - Build pecl extension for multiple versions php.

## How to use

If you want usage detail, type `--help`.

### Use standalone

```
% git clone https://github.com/berenddeboer/pecl-build.git
% cd pecl-build
% bin/pecl-build <package_name>
```

When standalone, build php version is system default.
If you want to use another php version, you can change `phpize` and `php-config` command by parameter.

```
$ bin/pecl-build <package_naem> -p /path/to/phpize -i /path/to/php-config
```

### Install as phpenv plugins

```
% git clone https://github.com/berenddeboer/pecl-build.git $(phpenv root)/plugins/pecl-build
phpenv pecl <package_name>
```

phpenv plugin follows the php version installed by phpenv.
If you want to build for a specific php version, you can specify a parameter.

```sh
phpenv pecl <package_name> -j <php version>
phpenv pecl <package_name> -a # build all php version by phpenv have.
```

*NOTICE: phpenv plugin versin is now skipped `system` environment build.*

you want specify package version:

```
phpenv pecl <package_name>-<package_version>
```

and when you build `zend_extension`, pass `-z (--zend-extension)` option.
so created `.ini` config set `zend_extension`

### Integrate with php-build

Patch the php-build script to add this:

```sh
# ### install_pecl

# install pecl (requires pecl-build)
install_pecl() {
    local name=$1
    log "Pecl" "Installing: $name"
    echo phpenv pecl $name -j $DEFINITION
    phpenv pecl $name -j $DEFINITION > /dev/null
}
```

You can then add `install_pecl` to build files like 8.3.23:

```
configure_option "--enable-gd"
configure_option "--with-jpeg"
configure_option "--with-zip"
configure_option "--with-mhash"

configure_option -D "--with-xmlrpc"

install_package "https://www.php.net/distributions/php-8.3.23.tar.bz2"
install_xdebug "3.4.5"
enable_builtin_opcache
install_pecl redis
install_pecl apcu
```

## ChangeLog

### v0.2 2025/07/28

Fix pecl url as https is now required.

### v0.1.1 2025/07/28

Update docs.

### v0.1.0 2013/12/06

* Initial Version

AUTHOR:: Daichi Kamemoto <yudoufu@crocos.co.jp>
