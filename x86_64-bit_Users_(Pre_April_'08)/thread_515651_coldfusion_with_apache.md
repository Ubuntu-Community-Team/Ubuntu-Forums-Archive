---
title: "coldfusion with apache"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by beamo on 2007-08-02
I'm trying to install Coldfusion8 to work with Apache2. Everything installs nicely but when I try to start the Apache server afterwards I get this error message:

* Starting web server (apache2)... apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Syntax error on line 2 of /etc/apache2/httpd.conf: Cannot load /opt/coldfusion8/runtime/lib/wsconfig/1/mod_jrun22 .so into server: /opt/coldfusion8/runtime/lib/wsconfig/1/mod_jrun22 .so: wrong ELF class: ELFCLASS32


Is there any way to get beyond this? I'm running Feisty 64-bit.

---

### Post by bluetracer on 2007-08-02
Well, it's complaining that that particular Cold Fusion module is 32-bit, basically.  Unless there's a 64-bit version of CF, you might be better off going with 32-bit Ubuntu.

If you just want to do development work, a VM might work OK for you.

---

### Post by bluetracer on 2007-08-02
> **bluetracer said:**
> Well, it's complaining that that particular Cold Fusion module is 32-bit, basically.  Unless there's a 64-bit version of CF, you might be better off going with 32-bit Ubuntu.

If you just want to do development work, a VM might work OK for you.

Sorry, just found [this]("http://www.houseoffusion.com/groups/cf-linux/thread.cfm/threadid:1065").  It's all to do with Java.

---

