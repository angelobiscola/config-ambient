Update

Apache 2.4

    sudo apt-get install apache2
    
Rewrite Module

    sudo a2enmod rewrite
    sudo systemctl restart apache2
    
Outro
    
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
   
