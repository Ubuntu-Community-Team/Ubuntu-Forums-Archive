---
title: "How to install Nvidia drivers in Ubuntu Manually"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by awww on 2008-08-23
Hi well Iam very new to Ubuntu and linux. I have google how to do it but when i do the steps i get permission errors.Also when I do this [http://www.ubuntugeek.com/how-to-install-nvidia-drivers-in-ubuntu-feisty-or-later-versions.html](http://www.ubuntugeek.com/how-to-install-nvidia-drivers-in-ubuntu-feisty-or-later-versions.html) my video card is not even detected any more.I know how to reset the drivers and everything I just need to know how to install them manually maybe that will work because iam tryin to use ubuntu eye candys.Because it says I need Nvdia accelerated graphics drivers for those to work. But every time I install them my screen want even come on meaning they are the wrong drivers and its not. My screen because I tryed to different screens same thing thats why i wanna know how to install them manually.

---

### Post by LateNiteTV on 2008-08-23
do the following:
```
sudo passwd root
```
this will allow you to access the root account.
then do:
```
su
```
you will now be the superuser and you wont get permission errors.

---

### Post by awww on 2008-08-23
OK now could i get step by step on how to do it im just learning my way around linux

---

### Post by LateNiteTV on 2008-08-23
what files are you trying to install?

---

### Post by awww on 2008-08-23
NVIDIA-Linux-x86_64-177.13-pkg2.run

---

### Post by LateNiteTV on 2008-08-23
try this as root:
```
sh NVIDIA-Linux-x86_64-177.13-pkg2.run
```

---

### Post by xen-uno on 2008-08-23
It doesn't get better than this ...

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by littletinman on 2008-08-23
This is what i had to do on my 64 bit laptop running ubuntu with an NVIDIA card. I installed envy, then let it install the driver automatically. Worked like a charm. Saved hours and hours. 


sudo apt-get envy


I think that should do it. or just look in the package manager.

---

### Post by awww on 2008-08-23
i keep getting cant open file the file is on the desktop and envy want work i keep gettin error there to

---

### Post by kjohansen on 2008-08-24
you should be able to go System->Administration->Hardware drivers and then it should list the proprietary driver.

this worked fine for my nvidia card.

---

### Post by IamNehalem on 2008-08-24
> **kjohansen said:**
> you should be able to go System->Administration->Hardware drivers and then it should list the proprietary driver.

this worked fine for my nvidia card.

As for me! I have Nvidia 9000 series

---

### Post by nbayiha on 2008-08-24
Did you try to follow this thread ?

[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver) 
If not try it , maybe that will solve your problem.

---

