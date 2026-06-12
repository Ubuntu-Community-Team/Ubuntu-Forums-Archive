---
title: "wine won't install"
date: 2007-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by firstc624 on 2007-09-06
ok first i am running gutsy so that my be my problem at teh moment.  i am also running Kubuntu.

i can't install wine, i have all repositories enabled.  this is the error i get when i tell it to install

[HTML] firstc624@firstc624-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
firstc624@firstc624-laptop:~$

 [/HTML]

Like i said i think it is that there is no version for the 64bit dev of gutsy, but was hoping someone could help me out if they have it runnning

Thanks in advance

---

### Post by yabbadabbadont on 2007-09-06
There isn't a version for 64-bit at all.  (at least not that last time I looked)  I believe that the only way to get it, is to setup a 32-bit chroot (or something like that).

Edit: Apparently, there are packages for Feisty.  I sit corrected.  :D

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by firstc624 on 2007-09-06
yea i saw that after i posted, i was looking to see if their was a gutsy version and saw the fiesty and older  :-)

guess i will have to wait or compile it, prolly will just wait as i don't know how to compile it  :-(

---

### Post by Kilz on 2007-09-06
> **firstc624 said:**
> yea i saw that after i posted, i was looking to see if their was a gutsy version and saw the fiesty and older  :-)

guess i will have to wait or compile it, prolly will just wait as i don't know how to compile it  :-(

have you tried downloading and installing the feisty package?

---

### Post by DaGGer on 2007-09-07
you have to add something before you can install it

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Follow those directions and it will work

---

### Post by Blindet on 2007-09-07
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

there you go, maybe it provides some help for gutsy also

---

### Post by Kilz on 2007-09-07
> **DaGGer said:**
> you have to add something before you can install it

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Follow those directions and it will work

But there is no section on that page for Gutsy, and thats what the original poster is running.

> **Blindet said:**
> [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

there you go, maybe it provides some help for gutsy also
Compiling wine on a 64bit install is one of the hardest things I have ever tried. It ranks up there with compiling a kernel and firefox. But in the past I have found that some deb files from previous versions work on the next one. Right now I am using the Edgy Nvu package on Feisty. I just had to download it, and double click on it and gdebi installed it.

---

### Post by firstc624 on 2007-09-07
thanks for the ideas everyone.  as kiltz stated i have already been to the winehq downlaod page and i am running gutsy.  

Kilz - i haven't tried using another version i will give it a try and see what happens. know  :-)

EDIT:  I downloaded the Fiesty deb and it worked.  Just thougth i would pass this on.  Thanks again kilz for recommending it.

---

### Post by ubuntu.daemon on 2007-09-08
why didnt you just try svn it from winehq and compile it yourself?

---

### Post by firstc624 on 2007-09-08
> **firstc624 said:**
> guess i will have to wait or compile it, prolly will just wait as i don't know how to compile it  :-(

this is y i didn't  compile it.  :-)

---

