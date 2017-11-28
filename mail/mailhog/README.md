Mail Mailhog

Image for the mail catching service [MailHog](https://github.com/mailhog/MailHog) for development purposes.

* Debian Stretched based.
* SMTP server starts on port 1025 (Default)
* HTTP server starts on port 8025 (Default)

* Examples for using with PHP
```
sendmail_path = /usr/sbin/sendmail -S mail:1025
sendmail_path = /usr/local/bin/mhsendmail --smtp-addr=mail:1025
```