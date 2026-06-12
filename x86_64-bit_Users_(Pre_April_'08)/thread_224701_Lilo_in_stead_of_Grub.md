---
title: "Lilo in stead of Grub"
date: 2006-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Donnieboii on 2006-07-28
Is there a possibility to use lilo instead of grub.. grub takes long to load so i want to try grub... 
does anyone know how to do this??

Thanks,

Donnieboii

---

### Post by rocketman768 on 2006-07-28
What do you mean Grub takes a long time to load? It should take a split second. Make sure that in your bios your boot order is:

CD-ROM
HDD
FLOPPY

My guess would be that your floppy is above the HDD, and checking to see if a floppy is in the drive and bootable can take 5-10 seconds.

---

### Post by Donnieboii on 2006-07-28
No i have floppy disabled cause have no floppy... and its set to 1st cdrom 2nd hdd so i dont think its that... it does the disk loading and than it says: Grub 1.5 or somethin like that than 3 seconds later it says Loading grub please wait and that wil be there for 3 secondes and than I can choose my operating system...

did wasnt before and I dont know what I have done...

Thanks 

Donnieboii

---

### Post by yopnono on 2006-07-28
> **Donnieboii said:**
> No i have floppy disabled cause have no floppy... and its set to 1st cdrom 2nd hdd so i dont think its that... it does the disk loading and than it says: Grub 1.5 or somethin like that than 3 seconds later it says Loading grub please wait and that wil be there for 3 secondes and than I can choose my operating system...

did wasnt before and I dont know what I have done...

Thanks 

Donnieboii
Change this part in your menu.lst. In terminal "sudo gedit /boot/grub/menu.lst"
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3
```
to
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1
```

---

### Post by Donnieboii on 2006-07-30
i tried .. it doesnt work.. and now i've got the problem i sometimes have to reboot 5 or 6 times before grub even works... this is like really annoying... does anyone have a awnser to this??

any help is really appriciated,,,

thanks

Donnieboii

---

### Post by rocketman768 on 2006-08-01
Maybe this is a hardware error.

---

### Post by Donnieboii on 2006-08-01
what kind of hardware error?

---

### Post by drn8 on 2006-08-01
So the question remains, does dapper come with LILO?

If not it should be a simple matter of ```
sudo apt-get install LILO
``` then run the configure script indicated during the install.

[here](http://lwn.net/Articles/89772/) is a nice comparison between GRUB and LILO, note GRUB is still in alpha.

[ here](http://www-128.ibm.com/developerworks/library/l-bootload.html?ca=dgr-lnxw16LILOandGRUB) is another lengthy explanation and comparison of both loaders.

---

### Post by Donnieboii on 2006-08-01
ok thanks.. ill read up on it... but it is possible to do lilo on dapper?

what would you suggest?

thanks 

donnieboii

---

### Post by McMarley on 2006-08-01
I dont know if it is possible to run lilo, but I use grub and its pretty fast, so whats the point of spending 10 minutes or possibly more setting it all up under lilo, while grub isnt TOO slow and you have no idea how long it take with lilo?

---

### Post by Donnieboii on 2006-08-01
my uncle uses lilo and is in my case faste cause for some reason my grub is messed up... but thank you for your help.. im gonna try it...

Thanks..

Donnieboii

---

### Post by drn8 on 2006-08-02
You can use LILO in dapper. LILO uses a static configuration whereas grub actually looks at your disk. it is possible for lilo to run faster on your machine, how much faster is the question. If ```
sudo apt-get install lilo
``` doesnt work you will have to download and compile LILO. 

[Here](http://lilo.go.dyndns.org/) is the lilo home page.
[Here](http://www.tldp.org/HOWTO/LILO.html) is a nice lilo howto from the linux documentation project.
[Here](http://freshmeat.net/redir/lilo/5784/url_tgz/lilo) is a tarball.

---

