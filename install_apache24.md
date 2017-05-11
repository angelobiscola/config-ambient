Update

    sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y dist-upgrade

Apache 2.4

    sudo apt-get install apache2
    
Rewrite Module

    sudo a2enmod rewrite
    sudo systemctl restart apache2
    
Outros
    
    sudo a2dismod mpm_event
    sudo a2enmod mpm_prefork
    sudo systemctl restart apache2

Vhost
   
   Acesse pasta
    
        /etc/apache2/sites-available
     
   Crie arquivo da site/aplicação
   
        cp 000-default.conf app.conf
    
   Edite
   
    nano app.conf 
    
        DocumentRoot 
          Ex: /var/www/html/tuaaplicacao/public.
        ServerName 
          Ex: teudominio.com.br.
        ServerAlias 
          Ext: www.teudominio.com.br.
      
   Aplique novo host
   
          sudo a2ensite app.conf
          service apache2 reload
   
    Exemplo Vhost
   
       Sem SSL

           <VirtualHost *:80>

            ServerName teuadminio.com.br
            ServerAdmin webmaster@localhost
            ServerAlias www.teuadminio.com.br
            DocumentRoot /var/www/site/

            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined

            </VirtualHost>
            
       Com SSL
       
           <IfModule mod_ssl.c>
                <VirtualHost *:443>

                        ServerName teuadminio.com.br
                        ServerAdmin webmaster@localhost
                        ServerAlias www.teuadminio.com.br
                        DocumentRoot /var/www/site/

                        ErrorLog ${APACHE_LOG_DIR}/error.log
                        CustomLog ${APACHE_LOG_DIR}/access.log combined

                        SSLCertificateFile caminho_certificado fullchain.pem
                        SSLCertificateKeyFile caminho_certificado privkey.pem

                        Include caminho_config options-ssl-apache.conf
                </VirtualHost>
             </IfModule>
    
       Htacess
       
           <IfModule mod_rewrite.c>
                <IfModule mod_negotiation.c>
                Options -MultiViews
            </IfModule>

                RewriteEngine On
                # Redirect Trailing Slashes If Not A Folder...
                RewriteCond %{REQUEST_FILENAME} !-d
                RewriteRule ^(.*)/$ /$1 [L,R=301]


                # Handle Front Controller...

                RewriteCond %{REQUEST_FILENAME} !-d
                RewriteCond %{REQUEST_FILENAME} !-f
                RewriteRule ^ index.php [L]

                # Handle Authorization Header
                RewriteCond %{HTTP:Authorization} .
                RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
            </IfModule>
        
        Forçar acesso por HTTPS
            
            de
                RewriteCond %{REQUEST_FILENAME} !-d
                RewriteCond %{REQUEST_FILENAME} !-f
                RewriteRule ^ index.php [L]
            para
                RewriteCond %{HTTPS} !=on
                RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301] 
        
