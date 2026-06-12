---
title: "Web Server"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yz85Racer on 2007-10-08
Hey. I'm running AMD-64, and I need a web server, I can't find any for 64-bit :(

---

### Post by Kilz on 2007-10-08
> **Yz85Racer said:**
> Hey. I'm running AMD-64, and I need a web server, I can't find any for 64-bit :(

Apache is in the repos.

---

### Post by Yz85Racer on 2007-10-08
I've downloaded Apache, but where did it download to? I used Adept.

---

### Post by Kilz on 2007-10-08
> **Yz85Racer said:**
> I've downloaded Apache, but where did it download to? I used Adept.

I recommend using the pre configured packages in the repositories rather than downloaded packages that may need to be setup to your system. Open a terminal, type in the following.

```
sudo apt-get install apache2 
```

You may also want to [read and follow this howto]("https://help.ubuntu.com/community/ApacheMySQLPHP") if you want mysql and php.

---

### Post by philipcs on 2007-10-09
I have followed the guide here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to install Apache2

After these steps, i still see port listening to 80

see my netstat -tnl result:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6990            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN
tcp6       0      0 :::5901                 :::*                    LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN

If I install apache (1.3.34), i can see port 80 is listening but PHP5 is not able to work with apache1.3.34 because keep asking me to download php file.

Netstat -tnl result after install apache + apache2:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6990            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN

Please assist.
tcp6       0      0 :::5901                 :::*                    LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN

---

### Post by incidence on 2007-10-09
[http://www.howtoforge.com/perfect_setup_ubuntu704]("http://www.howtoforge.com/perfect_setup_ubuntu704")

---

### Post by Kilz on 2007-10-09
> **philipcs said:**
> I have followed the guide here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to install Apache2

After these steps, i still see port listening to 80

see my netstat -tnl result:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6990            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN
tcp6       0      0 :::5901                 :::*                    LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN

If I install apache (1.3.34), i can see port 80 is listening but PHP5 is not able to work with apache1.3.34 because keep asking me to download php file.

Netstat -tnl result after install apache + apache2:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6990            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN

Please assist.
tcp6       0      0 :::5901                 :::*                    LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN

You need to edit the /etc/apache2/apache2.conf and add these lines

```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```
Then restart apache2, You also only want one instance of Apache installed.

---

