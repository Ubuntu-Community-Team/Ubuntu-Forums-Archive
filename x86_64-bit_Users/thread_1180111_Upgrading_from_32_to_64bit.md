---
title: "Upgrading from 32 to 64bit"
date: 2009-06-06
forum: x86 64-bit Users
---

### Post by drew212 on 2009-06-06
What is the easiest way to upgrade from jaunty 32 to 64? Can I do this without losing everything on my current jaunty partition? Is there any way to keep all my software and files?

---

### Post by dcraven on 2009-06-06
I'm pretty sure you will need to do a reinstall with the amd64 disk. If you mounted /home as its own partition, then there is no need to format that, therefore you will not lose your data. You can remount that partition as /home when you reinstall.

I'd suggest you back up your data and files regardless of your situation if you are going to make such a move. Accidentally telling the installer to format everything has been known to happen. You can never be too cautious.

Good luck!
~djc

---

### Post by ProbablyX on 2009-06-06
You could use the Ubuntu installer to remove everything except the /home folders (your user account files).

However even if you were to keep your programs, they'd still be 32bit - so I'd go for installing 64bit ones.
I believe you can make a scheme of what packages you have installed and make apt-get reinstall them once Linux is reinstalled but if you're changing 32 -> 64bit I think a clan install, with keeping your documents and settings would be the best deal.

Maybe someone else knows a better solution? :)

---

### Post by cybrsaylr on 2009-06-06
When I upgraded from 32bit 8.10 to 64bit 9.04 with the 64bit Live CD I made, my entire 'Home Folder' carried over to 64bit with no problem.

---

### Post by hondacodonbk on 2009-06-06
I think you should not do that,because release for 32 bit is different from 64 bit,so its config is so different and,of course,it will bring many unpredicate error if you upgrade from 32 to 64
I think the best way is installition a new 64bit release for your computer
have a good day ^_^

---

### Post by 3Miro on 2009-06-06
Back everything up and do a clean install.

---

### Post by bford16 on 2009-06-06
> **ProbablyX said:**
> You could use the Ubuntu installer to remove everything except the /home folders (your user account files).

However even if you were to keep your programs, they'd still be 32bit - so I'd go for installing 64bit ones.
I believe you can make a scheme of what packages you have installed and make apt-get reinstall them once Linux is reinstalled but if you're changing 32 -> 64bit I think a clan install, with keeping your documents and settings would be the best deal.

Maybe someone else knows a better solution? :)How do you "make a scheme of all your installed software?"

---

### Post by John.Michael.Kane on 2009-06-06
> **bford16 said:**
> How do you "make a scheme of all your installed software?"

The below will create a text file of software you installed sudo is not needed here.
```
dpkg --get-selections > ~/installed-software.log
```

To restore software from backup list
```
sudo dpkg --set-selections < ~/installed-software.log
```

The list should now be imported, and you can use dselect to install.
```
sudo aptitude install dselect
```
Then run.
```
sudo dselect
```

Choose 'i' for installing the software.

Note: The package list is architecture neutral, so the packages the list will installed should be 64-bit packages, however. You should make sure you have any 3rd party repositories that you previously used installed.

---

