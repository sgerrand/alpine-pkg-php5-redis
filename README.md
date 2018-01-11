# alpine-pkg-php5-redis

[![CircleCI](https://circleci.com/gh/sgerrand/alpine-pkg-php5-redis/tree/master.svg?style=svg)](https://circleci.com/gh/sgerrand/alpine-pkg-php5-redis/tree/master)

This is the [PHP driver for Redis][php-redis] as an Alpine Linux package.

## Releases

See the [releases page](https://github.com/sgerrand/alpine-pkg-php5-redis/releases) for the latest
download links.

## Installing

The current installation method for these packages is to pull them in using
`wget` or `curl` and install the local file with `apk`:

    apk --no-cache add ca-certificates wget
    wget --quiet --output-document=/etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub
    wget https://github.com/sgerrand/alpine-pkg-php5-redis/releases/download/3.1.6-r0/php5-redis-3.1.6-r0.apk
    apk add php5-redis-3.1.6-r0.apk

[php-redis]: https://pecl.php.net/redis
