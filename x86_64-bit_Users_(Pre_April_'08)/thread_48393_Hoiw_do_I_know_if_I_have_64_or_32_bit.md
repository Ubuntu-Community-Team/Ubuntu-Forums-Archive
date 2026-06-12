---
title: "Hoiw do I know if I have 64 or 32 bit?/"
date: 2005-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by young_digital on 2005-07-12
i just installed ubuntu but cant figure out which one i have installed....i heard 32 bit is  less complicated than 64...can y'all tell me how to figure out which one i got??

---

### Post by runenes on 2005-07-12
type:
```
$ uname -a 
```
and eyeball the info to find out.

---

### Post by dave9191 on 2005-07-12
If you type 

uname -m

into a console it will tell you the version of the kernel. And for a 32 bit machine you would see something like ix86. Im guessing that for the 64 bit you would see something like x86-64 or AMD64 or EM64T. 

You should install the right one for your processor. So dont install the 64 bit one if you have a 32 bit machine. 

Dave

---

### Post by young_digital on 2005-07-12
thnx for the info ppl

 # uname -m
i686

so im guessing thats a 32bit i got...so how do i know if my system is a 32bit system???? cus im havin some sound problems..
[http://ubuntuforums.org/showthread.php?p=251567#post251567](http://ubuntuforums.org/showthread.php?p=251567#post251567)
.and am hopin the installation is not a cause of this

---

### Post by drummer on 2005-07-12
[QUOTE=dave9191]You should install the right one for your processor. So dont install the 64 bit one if you have a 32 bit machine.[/QUOTE]
True, but you can install 32 on a 64-bit system if you have it, as 64-bit processors are completely backwards compatable with 32-bit code. The 32-bit Ubuntu is also easier to set up such things like extra media codecs, flash player plugin, and other things that have been ported from 32-bit windows versions. 64-bit Ubuntu will be easier in the future once 64-bit versions of these primarily windows apps emerge (which shouldn't be too long I hope ;) )

EDIT: yes, i686 is the 32-bit version.

---

### Post by dave9191 on 2005-07-12
Well thats something that you should know from when you bough your machine. What processor have you got inside. If you dont know, its something that shows up on the screen when you power up your computer. There is probably a hardware listing tool you can run as well. 

Dave

---

### Post by AllenGG on 2005-07-13
YD :  something's amiss ! 
are you saying that you have or have not a 64bit processor ?
go to >system>administration>device manager  (type in root password)
go to processor, (then) advanced, you'll see which CPU is onboard.

OK , you have a 64 bit CPU or processor
then with "uname" as above:
root@Xxxx:/home/alleng # uname -a
Linux Xxxx 2.6.10-5-amd64-k8 #1 Fri Jun 24 17:08:40 UTC 2005 x86_64 GNU/Linux
root@Xxxx:/home/alleng # uname -m
x86_64

hope that helps.
Allen G

---

### Post by brighton on 2005-07-13
download check.sh  ([www.ati.com](www.ati.com))
and run it

---

