#### You can do so with:

#####

    sudo su
    add-apt-repository ppa:ondrej/php
    apt-get update
    apt-get install php7.0 php5.6 php5.6-mysql php-gettext php5.6-mbstring php-xdebug libapache2-mod-php5.6 libapache2-mod-php7.0 php5.6-curl php5.6-gd php5.6-mcrypt php5.6-xml php5.6-xmlrpc
 

#### To switch from php 5.6 to php 7.0 you need to do two things:

##### For php in web apps
        sudo a2dismod php5.6 && sudo a2enmod php7.0 && sudo service apache2 restart
##### For php-cli in the command line
        sudo ln -sfn /usr/bin/php7.0 /etc/alternatives/php

##### Or from php7.0 to php5.6:

##### For php in web apps
       sudo a2dismod php7.0 && sudo a2enmod php5.6 && sudo service apache2 restart
##### For php-cli in the command line
        sudo ln -sfn /usr/bin/php5.6 /etc/alternatives/php
