## To install PHP stack

### Install apache2

1) To install apache2 use command : `brew install httpd`
2) Start and end apache2 `brew services start httpd` | `brew services stop httpd`
3) Default port will be `8080` if you need to change to `80`, if needed to be changed 
`nano /usr/local/etc/httpd/httpd.conf`
 then find `#ServerName www.example.com:8080` and update it with `ServerName localhost`
Then restart `brew services restart httpd`
4) Default working directory is `/usr/local/var/www`, if needed to be changed update it and restart
5) Find `#LoadModule rewrite_module lib/httpd/modules/mod_rewrite.so` and uncomment it
6) Apache log files are `/usr/local/var/log/httpd/error_log` && `/usr/local/var/log/httpd/access_log`
7) Now `http://localhost` is working but if you tried PHP code will be shown as plain text.

### Install PHP
1) First add PHP `brew tap shivammathur/php` 
2) Based on the version required `brew install shivammathur/php/php@7.4` 
3) If needed to install multiple PHP versions `brew install shivammathur/php/php@8.1`
4) Now unlink the not required version `brew unlink php@8.1`
5) Link the required version `brew link php@7.4`

### Configure PHP in apache2 to process PHP code
1) Go to file `nano /usr/local/etc/httpd/httpd.conf` and add `LoadModule php7_module /usr/local/lib/httpd/modules/libphp7.so`
 or if php 8 `LoadModule php_module /usr/local/opt/php@8.0/lib/httpd/modules/libphp.so`
2) Then find 
    ```
    <IfModule dir_module$>
        DirectoryIndex index.php index.html
    </IfModule>
    ```
    and replace with 
    ```
    <FilesMatch .php$>
    	SetHandler application/x-httpd-php
    </FilesMatch>

    <IfModule dir_module$>
        DirectoryIndex index.php index.html
    </IfModule>
    ```
3) Restart `brew services restart httpd`
4) Test configurations `sudo apachectl configtest`

### Required extensions
1) Install imagemagick `brew install pkg-config imagemagick` 
2) Compile it `pecl install imagick`
3) Try `php -m` should be found there

