---
title: "Advice about Drupal install"
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by d98rolb on 2008-11-18
Hi!

I have an idea to use Drupal on a more advanced site. I will first build it locally on a desktop Ubuntu 8.10 AMD64. But I'm a beginner of this kind of programs so it would be good with some advices. I have done this so far:

```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin
```

Seems to work well.
[http://localhost/](http://localhost/) in the browser says "It works!" 

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal) says that the repository in Ubuntu is old and it is better to download direct from the Drupal site.
So I downloaded latest Drupal 6.06 and copied it to /var/www/drupal.
And  [http://localhost/drupal](http://localhost/drupal) shows a nice page for installation :)

Now I must create the database with mysql. I have seen that phpmyadmin is popular so I downloaded latest phpmyadmin 3.0.1.1 and copied it to /var/www/phpmyadmin.

Men nu ska jag skapa databasen med mysql.
Jag har sett att phpmyadmin verkar vara populärt så jag tog hem senaste phpmyadmin 3.0.1.1 och lade in det på /var/www/phpmyadmin.

[http://localhost/phpmyadmin](http://localhost/phpmyadmin) show this page:
```
 Error
MySQL said: Documentation
#1045 - Access denied for user 'root'@'localhost' (using password: NO)
Open new phpMyAdmin-window

```

And a link to create a config file. When I click on it I came to phpMyAdmin 3.0.1.1 setup. What is the next step now ?

Regards

---

### Post by cariboo on 2008-11-18
Create a database in mysql you have to use the password you created when you installed it. To make sure you can access mysql, open a Applications--Accessories-->Terminal and type:

```
mysql -u root -p
```

You will be prompted for the password you created. The sesult should look something like this:

```
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1320
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 
```

If you can access mysql from the command line, you should be able to use phpmyadmin to create a database. If I remember correctly during Drupal setup, it will ask you to create a databse in one of the setup steps, so there isn't any need to setup a db before hand.

Jim

---

