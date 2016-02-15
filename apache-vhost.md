APP por Vhost apache

        <VirtualHost *:80>
            ServerName app
            ServerAdmin admin@admin.com
            DocumentRoot /var/www/html/app/public
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined

            <Directory /var/www/html/gda.app/public>
                <IfModule mod_rewrite.c>
                    Options -MultiViews
                    RewriteEngine On
                    RewriteCond %{REQUEST_FILENAME} !-f
                    RewriteRule ^ index.php [L]
                </IfModule>
            </Directory>
        </VirtualHost>
