---
id: Compilation-Install-PHP-8
title: Install PHP 8 by Compilation
sidebar_position: 1
---

# Install PHP 8 from Source

<div align="left">

<img src="https://img.shields.io/badge/RockyLinux_9.1-Tested-green?style=flat&logo=RockyLinux" alt="Tested Platform" />

<img src="https://img.shields.io/badge/Tested_SW_Ver.-PHP_8.1.2-blue?style=flat" alt="Tested Software Version" />

</div>

:::warning
Compiling requires adequate memory.

If your device has **less than 2GB of RAM**, it is strongly recommended to create a swap partition first.
:::

## Prepare

### 1. Install basic build tools

```bash
dnf groupinstall "Development Tools"
dnf install libxml2-devel libicu-devel sqlite-devel libxslt-devel \
    libpng-devel libjpeg-devel freetype-devel libzip-devel git \
    systemd-devel curl-devel
```

### 2. Download & build Oniguruma
```bash
cd oniguruma
./autogen.sh
./configure --bindir=/usr/sbin/ \
            --sbindir=/usr/sbin/ \
            --libexecdir=/usr/libexec \
            --sysconfdir=/etc/ \
            --localstatedir=/var \
            --libdir=/usr/lib64/ \
            --includedir=/usr/include/ \
            --datarootdir=/usr/share \
            --infodir=/usr/share/info \
            --localedir=/usr/share/locale \
            --mandir=/usr/share/man/ \
            --docdir=/usr/share/doc/onig
make
make install
```

### 3. Add user for PHP-FPM
```bash
adduser www
```

### 4. Download PHP source code

You can download suitable PHP for your application from the offical website:
https://www.php.net/downloads

Example:
```bash
wget https://www.php.net/distributions/php-8.1.2.tar.gz
```
```bash
tar -xzf php-8.1.2.tar.gz
```

### 5. Configure PHP
：：：tip
You can find all available ./configure options in the official docs:
https://www.php.net/manual/en/configure.about.php#configure.options.misc
:::

Below is a recommended FPM-enabled configuration:
```bash
cd php-8.1.2
```
：：：tip
Replace YOUR_WEB_USER with the actual PHP-FPM user (for example: www)
:::

```bash
./configure --prefix=/usr/local/php/ \
            --enable-fpm \
            --with-openssl \
            --enable-bcmath \
            --with-curl \
            --enable-ftp \
            --enable-gd \
            --enable-mbstring \
            --enable-sockets \
            --enable-pcntl \
            --with-zlib \
            --enable-intl \
            --with-fpm-systemd \
            --enable-pdo \
            --enable-xml \
            --with-zip \
            --with-gettext \
            --with-freetype \
            --enable-opcache \
            --enable-shmop \
            --with-fpm-user=YOUR_WEB_USER \
            --with-fpm-group=YOUR_WEB_USER
```
Optional MySQL-related options (adjust paths to your own environment; the example assumes MySQL installed via 'dnf'):
```bash
--enable-mysqlnd \
--with-pdo-mysql=mysqlnd \
--with-mysqli \
--with-mysql-sock=/var/lib/mysql/mysql.sock
```