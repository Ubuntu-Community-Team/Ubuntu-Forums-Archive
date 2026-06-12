---
title: "WINE offline installation?"
date: 2008-06-23
forum: Wine
---

### Post by taffypride on 2008-06-23
I don't have a working internet connection as I have a dialup USB modem from 3 UK.

How can I get a copy of WINE that I can install offline?  And how do I actually install it once I have it?

---

### Post by btermeli on 2008-06-23
Download wine package from here;

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Copy that to ur desktop with memory stick or cd and type;

cd Desktop

sudo dpkg -i FILENAME.deb

Thats all...

---

### Post by taffypride on 2008-06-23
thank you very much!

:popcorn:
:KS:KS:KS:KS

---

### Post by danuka on 2010-02-09
Hi There!
I'm using Ubuntu 9.10 and i have not any internet connection. But i want to install wine on my PC. How can i do that? Please Help....






> **btermeli said:**
> Download wine package from here;

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Copy that to ur desktop with memory stick or cd and type;

cd Desktop

sudo dpkg -i FILENAME.deb

Thats all...

---

### Post by Soulcage on 2010-02-09
Are you not able to use your dialup connection on ubuntu? I'm using earthlink with my USR5637.

---

### Post by kithusan on 2011-02-27
hi btermeli
               i just randomly  download a file from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) :confused::confused::confused:

              but i want to know which one should i download for ubuntu 10.10 32bit

---

### Post by cogadh on 2011-02-27
This one (its the most recent archived version): wine1.3_1.3.14-0ubuntu1~maverickppa1_i386.deb

However, it will very likely fail to install. That package has lot of dependencies that it will need to install as well and without an internet connection, it won't be able to download and install those dependencies. You could try manually downloading each dependency, but that usually doesn't go very well. You'd be much better off just temporarily getting that machine online to install Wine, then taking it offline.

---

