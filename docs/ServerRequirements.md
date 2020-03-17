# Server Requirements
The minimum server requirement:
- CPU: `1 vCPU` or higher
- RAM: `2GB` or higher
- HDD: `50GB` or higher

Web-service requirements:
- PHP: 7.2 or higher
- MySQL: 5.7.29 or higher

> see https://laravel.com/docs/6.x#server-requirements for more information

Packages required:
```sh
$ sudo apt-get install -y \
    libxrender1 \
    libfontconfig1 \
    libx11-dev \
    libjpeg62 \
    libxtst6 \
    libssl1.0-dev
```

If you are running a headless server such as `ubuntu-server` you might need to install `Virtual Framebuffer`:`xvfb`:

```sh
# Virtual Framebuffer
$ sudo apt-get install -y xvfb
```

> see https://launchpad.net/ubuntu/bionic/+package/xvfb


### Getting project source code
After you have installed all the required dependencies, now it time to clone the project source code onto your server.

```sh
# Add user to www-data group
$ sudo usermod -a -G www-data $USER

# Set ownership to /var/www/html folder
$ sudo chown -R $USER:www-data /var/www/html

# Change folder mod on bootstrap/ & storage/
$ cd /var/www/html
$ sudo chmod -R 775 bootstrap/ storage/
```


### Setting up domain name
Once everything is completed, now it time to setup domain name for your server.

Transfer `server/etc/apache2/sites-available/angkorgreen.biz.conf` into `/etc/apache2/sites-available/` folder on your server.

Then run the followin command:

```sh
$ sudo a2ensite angkorgreen.biz
```

Then restart `apache2` with the following command:
```sh
$ sudo systemctl restart apache2
```
