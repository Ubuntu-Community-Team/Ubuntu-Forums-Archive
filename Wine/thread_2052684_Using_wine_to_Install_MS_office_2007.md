---
title: "Using wine to Install MS office 2007"
date: 2012-09-03
forum: Wine
---

### Post by w1nst0nsm1th on 2012-09-03
Hi,

I'm trying to install Office 2007.. It has gold compatibility with my ubuntu (Maverick Meerkat 10.10) so it should be easy.

I've done all the necessary things in winetricks but now I cannot get wine to recognize the mounted ISO. 

I've wone into the 'drives' section of winecfg and it looks like the relevant virtual drive is being detected - however it still asks for the disc to be mounted.

Anyone got a clue as to what I'm doing wrong?

(I successfully used the same process to install office 2003 before)

---

### Post by w1nst0nsm1th on 2012-09-03
Hi,

I'm trying to install Office 2007.. It has gold compatibility with my ubuntu (Maverick Meerkat 10.10) so it should be easy.

I've done all the necessary things in winetricks but now I cannot get wine to recognize the mounted ISO. 

I've gone into the 'drives' section of winecfg and it looks like the relevant virtual drive is being detected - however it still asks for the disc to be mounted.

Anyone got a clue as to what I'm doing wrong?

(I successfully used the same process to install office 2003 before)

---

### Post by SeaHawk22 on 2012-09-03
According to 

[http://www.wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html](http://www.wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html)

"You might need to mount your Office 2007 CD with the option -o unhide. This will avoid having problems with hidden files during installation.

Mount and cd to your disk and start the install.

mount -t iso9660 -o unhide /dev/cdrom /media/cdrom0

tom@tom:~$ cd /media/cdrom0
tom@tom:/media/cdrom0$ wine setup.exe"

---

### Post by robtygart on 2012-09-03
Why don't you use one made for Linux? Open office, Abbi word, liber office.

---

### Post by coffeecat on 2012-09-03
Merged duplicate threads.

---

### Post by kurt18947 on 2012-09-03
> **robtygart said:**
> Why don't you use one made for Linux? Open office, Abbi word, liber office.

Those may not make it if he needs 100% MSO file compatibility or if he needs functions not found in LibreOffice/OpenOffice/Abiword.

---

### Post by oldos2er on 2012-09-03
Moved to Wine.

---

