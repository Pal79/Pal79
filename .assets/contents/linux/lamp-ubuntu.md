
---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---

# Ubuntu - lamp

---

### update packages

```shell
sudo apt update
```

## install Apache

```shell
sudo apt install apache2
```

### show ufw list

```shell
sudo ufw app list
```

### add the 80 port (Apache) to ufw

```shell
sudo ufw allow in "Apache"
```

### show ufw status

```shell
sudo ufw status
```

### if status inactive

```shell
sudo ufw enable
```

### check the apache in browser

```shell
http://your_ip
```

> or

```shell
http://localhost
```

## Install Mysql

```shell
sudo apt install mysql-server
```

### open mysql

```shell
sudo mysql
```

### set root with password

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

### if everything is ok just write 'exit' and push enter

```sql
exit
```

## Install php

```shell
sudo apt install php libapache2-mod-php php-mysql
```

### check php version

```shell
php -v
```

### modify content in dir.conf

```shell
sudo nano /etc/apache2/mods-enabled/dir.conf
```

> this

```shell
<IfModule mod_dir.c>
    DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>
```

> to this

```shell
<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```

### restart apache

```shell
sudo systemctl restart apache2
```

### check apache status

```shell
sudo systemctl status apache2
```

### if you want check php extensions and install

```shell
apt search php- | less
```

```shell
apt show package_name
```

> e.g.

```shell
apt show php-cli
```

> and install

```shell
sudo apt install php-cli
```

> or more packages

```shell
sudo apt install package1 package2 ...
```

## Create virtual host for your website

```shell
sudo mkdir /var/www/your_domain
```

> add privileges for this map

```shell
sudo chown -R $USER:$USER /var/www/your_domain
```

> create your_domain.conf file

```shell
sudo nano /etc/apache2/sites-available/your_domain.conf
```

> write this in file

```shell
<VirtualHost *:80>
    ServerName your_domain
    ServerAlias www.your_domain
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/your_domain
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

> enable the new virtual host

```shell
sudo a2ensite your_domain
```

```shell
sudo a2dissite 000-default
```

```shell
sudo apache2ctl configtest
```

> reload apache

```shell
sudo systemctl reload apache2
```

### create first content

```shell
nano /var/www/your_domain/index.html
```

> write in file

```html
<html>
  <head>
    <title>your_domain website</title>
  </head>
  <body>
    <h1>Hello World!</h1>

    <p>This is the landing page of <strong>your_domain</strong>.</p>
  </body>
</html>
```

> and test the running

```shell
http://server_ip
```

> or

```shell
http://localhost
```

### testing php

> create php file

```shell
nano /var/www/your_domain/info.php
```

> write in file

```php
<?php phpinfo(); ?>
```

> and test

```shell
http://server_ip/info.php
```

> or

```shell
http://localhost/info.php
```

### test mysql

> enter the mysql with root

```shell
sudo mysql -u root -p
```

> and create new database

```sql
CREATE DATABASE example_database;
```

> create new user

```sql
CREATE USER 'example_user'@'%' IDENTIFIED BY 'password';
```

> and give permissons

```sql
GRANT ALL ON example_database.* TO 'example_user'@'%';
```

> exit

```sql
exit
```

> now use the created user

```shell
mysql -u example_user -p
```

> check databases;

```sql
SHOW DATABASES;
```

> add table in the created database

```sql
CREATE TABLE example_database.todo_list (
  item_id INT AUTO_INCREMENT,
  content VARCHAR(255),
  PRIMARY KEY(item_id)
);
```

> and add contents this table

```sql
INSERT INTO example_database.todo_list (content) VALUES ("My first important item");
```

```sql
INSERT INTO example_database.todo_list (content) VALUES ("My second important item");
```

```sql
INSERT INTO example_database.todo_list (content) VALUES ("My third important item");
```

```sql
INSERT INTO example_database.todo_list (content) VALUES ("and this one more thing");
```

> show datas

```sql
SELECT * FROM example_database.todo_list;
```

> and exit

```sql
exit
```

> create test file

```shell
nano /var/www/your_domain/todo_list.php
```

> and write in file

```php
<?php

$user = "example_user";
$password = "password";
$database = "example_database";
$table = "todo_list";

try {
  $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}

?>
```

> and test

```shell
http://server_ip/todo_list.php
```

> or

```shell
http://localhost/todo_list.php
```

---

- [Back to the first page](../../../README.md)
- [Back to the linux](../linux.md)

---