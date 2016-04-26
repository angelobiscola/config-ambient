#### Reset Password MYSQL

##### Linux:

     sudo /etc/init.d/mysqld stop
     sudo /etc/init.d/mysqld_safe --skip-grant-tables
     sudo /usr/local/mysql/bin/mysql -u root

    v5.4-
     UPDATE mysql.user SET Password=PASSWORD('NewPassword') WHERE User='root';

    v5.5+
     UPDATE mysql.user SET authentication_string=PASSWORD('NewPassword') WHERE User='root';
     UPDATE mysql.user SET password_expired='N' WHERE User='root';
    
     FLUSH PRIVILEGES;
     \q

     sudo /etc/init.d/mysqld start

#### Mac

##### Comand:

      sudo /usr/local/mysql/support-files/mysql.server stop
      sudo /usr/local/mysql/bin/mysqld_safe --skip-grant-tables
      sudo /usr/local/mysql/bin/mysql -u root

     v5.4-
      UPDATE mysql.user SET Password=PASSWORD('NewPassword') WHERE User='root';

     v5.5+
      UPDATE mysql.user SET authentication_string=PASSWORD('NewPassword') WHERE User='root';
      UPDATE mysql.user SET password_expired='N' WHERE User='root';
      
      FLUSH PRIVILEGES;
       \q
      
      sudo /usr/local/mysql/support-files/mysql.server star





