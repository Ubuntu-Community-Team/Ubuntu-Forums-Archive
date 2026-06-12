---
title: "wine - exception EdxGdipException during installation of program"
date: 2014-11-12
forum: Wine
---

### Post by marchello_lippi2 on 2014-11-12
Hi all, 

I got error when tried to install program. 

Application Error 
Exception EdxGdipException in module 
AdminSetup.exe at 000B4612. 
Invalid operation in GDI+ (Code: 1). 

The program is PL/SQL Developer from allroundautomations.com 

Could someone suggest how to solve? 
Thanks ahead. 

P.S.: I'm pretty happy with Oracle SQL Developer for linux, but tech lead said that I should install what other team members use. Hope to use it via wine, because virtual windows machine slows down my computer.

---

### Post by Mark Phelps on 2014-11-13
If you're trying to use version 8 or 9, you should be in good shape -- as indicated in the linked WineHW web page:  [https://appdb.winehq.org/objectManager.php?sClass=application&iId=935]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=935")

But, if you're using version 10, or older than 8, you're wasting your time trying to do this with Wine.

---

