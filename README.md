## Dependencias - Ubuntu 12 +

## Cofiguração de ambiente

#### Install PHP

##### Comand:

      sudo apt-get install php5
      sudo php5enmod mcrypt
      sudo a2enmod rewrite
      sudo apt-get install curl
      sudp apt-get install php5-curl
      
#### Install Apache

##### Comand:

      sudo apt-get install apache2 libapache2-mod-php5

####  Install Composer

##### Comand:
      
      curl -sS https://getcomposer.org/installer | php
      sudo mv composer.phar /usr/local/bin/composer
      sudo chmod +x /usr/local/bin/composer
      
#### Install Node.js 

##### Comand:
  
      sudo apt-get install python-software-properties
      sudo apt-add-repository ppa:chris-lea/node.js
      sudo apt-get update
      sudo apt-get install nodejs
      node -v

### more..
