Update

    sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y dist-upgrade
    
PHP 7

    sudo apt-get install libapache2-mod-php7.0 php7.0-mysql php7.0-curl php7.0-json php-memcached php7.0-dev php7.0-mcrypt php7.0-sqlite3 php7.0-mbstring
  
PHP mais seguro

    sudo nano /etc/php/7.0/apache2/php.ini 

    de  ;cgi.fix_pathinfo=1
    para  cgi.fix_pathinfo=0
   
 Teste
      
      sudo systemctl restart apache2
      sudo nano /var/www/html/info.php

 Copie e cole o código abaixo.
    
    <?php
       phpinfo();
  
    acesse http://localhost/info.php,
    
 Mcrypt
  
    sudo phpenmod mcrypt
    sudo systemctl restart apache2
    
 Dicas
 
  Let's Encrypt Apache
    
    sudo apt-get install software-properties-common
    sudo add-apt-repository ppa:certbot/certbot
    sudo apt-get install python-certbot-apache
    
  Install SSL Certificate

    sudo certbot --apache -d example.com -d www.example.com
    
  Auto Renewal

    sudo crontab -e
    15 3 * * * /usr/bin/certbot renew --quiet
  
