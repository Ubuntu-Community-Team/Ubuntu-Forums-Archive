---
title: "Xampp"
date: 2008-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Majorflam on 2008-01-20
I installed XAMPP from Apache friends, and after following the install instructions I've discovered that XAMPP is not supported in 64 bit systems.

2 Questions if you would be so kind:

1. How do I uninstall XAMPP?

2. Is there an alternative I can use in 64 bit enviornment?

TIA

---

### Post by Thelasko on 2008-01-22
Sounds like you didn't use the repositories to install Xampp.  I don't mean to scold you.  However, typically program's are not in the repositories for a reason.  To install a program from the repositories simply click on applications>add/remove programs.  There you can sort by the most popular programs for your need.   

As far as removing Xampp?  I can't answer that.

Sorry I couldn't be of more help.

---

### Post by XplOzIOn on 2008-01-22
> **Majorflam said:**
> I installed XAMPP from Apache friends, and after following the install instructions I've discovered that XAMPP is not supported in 64 bit systems.

2 Questions if you would be so kind:

1. How do I uninstall XAMPP?

2. Is there an alternative I can use in 64 bit enviornment?

TIA

Hello there!

To unistall XAMMP do the following command

```
#sudo /opt/lampp/lampp stop
#sudo rm -rf /opt/lampp 
```

EDIT: Added stop command just in case :P

---

### Post by incubus on 2008-01-22
Hello there,

Regarding #2, my suggestion is to simply install the packages you need.  Here's a guide.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I think something in the lines of:
```

$ sudo apt-get install apache2 phpmyadmin mysql-server

```

would do it.

incubus

---

### Post by XplOzIOn on 2008-01-22
> **incubus said:**
> Hello there,

Regarding #2, my suggestion is to simply install the packages you need.  Here's a guide.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I think something in the lines of:
```

$ sudo apt-get install apache2 phpmyadmin mysql-server

```

would do it.

incubus

Dont forget to set password for mysql-server

```
mysqladmin -u root password [COLOR="Red"]YourPasswordHere[/COLOR]
```

---

### Post by drizad on 2008-05-25
Thanks... 

Really helped me on uninstalling XAMPP. At last, I need to remove it as my harddisk is full.

---

