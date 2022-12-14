# org.freedesktop.Sdk.Extension.php80

This extension adds PHP support to Flatpak.

PHP installs to `/usr/lib/sdk/php80` inside the sandbox.

Example Visual Studio Code Configuration

```json
"php.validate.executablePath": "/usr/lib/sdk/php80/bin/php",
"php.executablePath": "/usr/lib/sdk/php80/bin/php",
```

Includes

* [php](https://php.net/)
* [composer](https://github.com/composer/composer)
* [PHIVE](https://phar.io/)
* [apcu](https://pecl.php.net/package/APCu)
* [xdebug](https://xdebug.org/)

Each Flatpak can have its own custom php configuration files.
e.g. for Visual Studio Code
`~/.var/app/com.visualstudio.code/config/php/8.0/ini/my-custom.ini` or `/var/config/php/8.0/ini/my-custom.ini` from a sandboxed shell.

Global composer installs are limited to the Flatpak they were installed in.

#### Troubleshooting
`/usr/bin/env: ‘php’: No such file or directory`

Run `. /usr/lib/sdk/php80/enable.sh` or add `/usr/lib/sdk/php80/bin` to your $PATH.

#### Modules

```bash
bash-5.0$ php -m
[PHP Modules]
apcu
bcmath
bz2
calendar
Core
ctype
curl
date
dom
exif
FFI
fileinfo
filter
ftp
gd
gettext
hash
iconv
intl
json
ldap
libxml
mbstring
mysqli
mysqlnd
openssl
pcntl
pcre
PDO
pdo_mysql
pdo_pgsql
pdo_sqlite
Phar
posix
pspell
readline
Reflection
session
SimpleXML
sockets
sodium
SPL
sqlite3
standard
sysvmsg
sysvsem
sysvshm
tokenizer
xdebug
xml
xmlreader
xmlwriter
xsl
zip
zlib

[Zend Modules]
Xdebug
```
#### Build
```bash
flatpak-builder --repo repo .build org.freedesktop.Sdk.Extension.php80.json --force-clean
```
