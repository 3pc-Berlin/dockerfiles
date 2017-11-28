PHP 7.1 FPM

Image for PHP 7.1 with Fpm, Cli, packages and settings for use with [TYPO3](https://typo3.org).

* Debian Stretched based, PHP Packages from [DEB.SURY.ORG](https://deb.sury.org).

* Installed PHP Packages

    * Apcu
    * Bcmath
    * Curl
    * Gd
    * Json
    * Mbstring
    * Mysqli
    * Zip
    * Xml
  
* PHP settings

```
memory_limit = 256M
upload_max_filesize = 128M
post_max_size = 256M
max_execution_time = 240
max_input_vars = 2500
date.timezone=Europe/Berlin
sendmail_path = /usr/sbin/ssmtp -t
```

* Xdebug

* Additional packages

    * Graphicsmagick