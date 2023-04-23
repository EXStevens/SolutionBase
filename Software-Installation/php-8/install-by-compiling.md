# Install by Compiling

![Tested Platform](https://img.shields.io/badge/RockyLinux\_9.1-Tested-green?style=flat\&logo=RockyLinux) ![Tested SW Ver.](https://img.shields.io/badge/Tested\_SW\_Ver.-PHP\_8.1.2-blue?style=flat)

{% hint style="warning" %}
**Compiling Needs Memory Space!**

If the memory space of your device is **Lower than 2GB**, you had better Create a Swap.
{% endhint %}

### **Prepare**

1.  Prepare for the Environment

    ```bash
    dnf groupinstall "Development Tools"
    dnf install libxml2-devel libicu-devel sqlite-devel libxslt-devel libpng-devel libjpeg-devel freetype-devel libzip-devel git systemd-devel curl-devel
    ```


2.  Install Oniguruma

    <pre class="language-bash"><code class="lang-bash"><strong>git clone https://github.com/kkos/oniguruma.git
    </strong>cd oniguruma
    ./autogen.sh
    ./configure --bindir=/usr/sbin/ \
            --sbindir=/usr/sbin/ \
            --libexecdir=/usr/libexec \
            --sysconfdir=/etc/ \
            --localstatedir=/var \
            --libdir=/usr/lib64/  \
            --includedir=/usr/include/ \
            --datarootdir=/usr/share \
            --infodir=/usr/share/info \
            --localedir=/usr/share/locale \
            --mandir=/usr/share/man/ \
            --docdir=/usr/share/doc/onig
    make &#x26;&#x26; make install
    </code></pre>


3.  Add user for FPM

    ```bash
    adduser www
    ```


4.  Download the Source [![Downloads](https://img.shields.io/badge/Downloads-blue)](https://www.php.net/downloads) [![OSS-DL](https://img.shields.io/badge/Download\_from\_SRC--OSS-darkblue)](https://src-oss.expcs.net/php-8.2.5.tar.gz)

    wget https://www.php.net/distributions/php-8.1.2.tar.gz
5. Copy the link you need and download and then unzip.

&#x20;tar -xzf php-8.1.2.tar.gz

1.  **Pre-Compile**

    _See all options in_ [![Option](https://img.shields.io/badge/Offical\_Docs-blue)](https://www.php.net/manual/en/configure.about.php#configure.options.misc)

    **Here are the recommanded options(FPM included):**

    ```bash
    cd php-8.1.2
    # Replace UR_WEB_USER into your user for php-fpm
    ./configure --prefix=/usr/local/php/ --enable-fpm --with-openssl --enable-bcmath --with-curl --enable-ftp --enable-gd --enable-mbstring --enable-sockets --enable-pcntl --with-zlib --enable-intl --with-fpm-systemd --enable-pdo --enable-xml --with-zip --with-gettext --with-freetype --enable-opcache --enable-shmop --with-fpm-user=UR_WEB_USER --with-fpm-group=UR_WEB_USER

    ```

    If need to support MySQL, add those options you need. **The Directories and Configs depend on your env.** (MySQL here installed by DNF)

    ```bash
    --enable-mysqlnd --with-pdo-mysql=mysqlnd --with-mysqli --with-mysql-sock=/var/lib/mysql/mysql.sock
    ```
2.  **Compile & Install**

    ```bash
    make && make install
    ```
3.  **Finish Config**

    Copy Config File to the Install Directory

    ```bash
    cp PATH_TO_THE_SRC/php.ini-production /usr/local/php/php.ini
    cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf
    cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf
    ```

    Add Php to systemd as a service(**Recommanded**, make it ez to manage) _About the usage of systemd,Check systemd#BasicUsage_

    1. Edit PID Location

    ```bash
    # Open the File
    vim /usr/local/php/etc/php-fpm.conf

    # Find the part and Change into
    pid = /var/run/php-fpm.pid
    ```

    2. Write the systemd script

    ```bash
    # Create one and edit
    vim /lib/systemd/system/php-fpm.service
    ```

    3. Then, add the content.

    ```conf
    [Unit]
    Description=The PHP FastCGI Process Manager
    After=syslog.target network.target

    [Service]
    Type=forking
    PIDFile=/var/run/php-fpm.pid
    ExecStart=/usr/local/php/sbin/php-fpm
    ExecReload=/bin/kill -USR2 $MAINPID
    PrivateTmp=true

    [Install]
    WantedBy=multi-user.target
    ```

    4. Reload systemd

    ```bash
    systemctl daemon-reload
    ```
4. **Enjoy it!**
