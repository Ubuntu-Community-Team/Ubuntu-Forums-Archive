---
title: "Going from 32bit to 64bit, worth it?"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by whitehornmatt on 2006-01-15
I have been using Ubuntu as my main os for a while now and recently upgraded to a 64bit machine but am still using 32-bit ubuntu. 
I have had second thoughts because of the fact I do a bit of multimedia stuff and need to be able to play WMV's and Real stuff. 
I also need to be able to compile my modem's kernel module so I was wondering if Breezy 64-bit has the same gcc version problem as the 32 bit one, becuase if it does I have to download gcc before I can go on the internet to use apt (so i need to know all the packages that I need)
I am upgrading to 64-bit because I want it to be faster, and for a better chance of getting Direct Rendering on my VIA Unichrome (k8m800) working.
I don't mind doing alot of stuff on the command line if I need to, because I have had to do it alot in the past. 
The live CD works fine (Infact it started about as quick as my old computer started the 32 bit off the hd) except for it using the vesa driver.

So basically my question is, how hard is it to get the multimedia codecs I need working on 64bit Ubuntu? And what are the files I need to download for gcc?

---

### Post by stuporglue on 2006-01-15
gcc would need "build-essential", if  my spelling is correct. If it's not, it's something close to that.

---

### Post by Mr_Grieves on 2006-01-15
The fact that there is no flash support would keep me from converting..

I'm sorry but I don't know anything about video codecs..
Reading here: [http://ubuntuforums.org/showthread.php?t=75278](http://ubuntuforums.org/showthread.php?t=75278)
It says that WMV9 does not work in Ubuntu 64.

---

### Post by whitehornmatt on 2006-01-15
[QUOTE=stuporglue]gcc would need "build-essential", if  my spelling is correct. If it's not, it's something close to that.[/QUOTE]
I actually need to know what packages that I need to get to install gcc-3.4 manually, because I have to get them before upgrading, because I can't get them using apt until I have the modem working. 

Also I don't really need flash as I try to aviod sites with flash.

---

### Post by whitehornmatt on 2006-01-15
I just had a quick look in the repos and found that all the stuff i needed was in one folder. I will backup and install a bit later tonight and hopefully it will go as to plan. And if it isn't good I might go back to the 32bit one.

---

### Post by Gowator on 2006-01-15
[QUOTE=whitehornmatt]I actually need to know what packages that I need to get to install gcc-3.4 manually, because I have to get them before upgrading, because I can't get them using apt until I have the modem working. 

Also I don't really need flash as I try to aviod sites with flash.[/QUOTE]


Me too but then sometimes I *need* to.  This and the MM support is the main reason Im still running 32 bit.

---

### Post by Damburger on 2006-01-19
I'm running 64 bit and thinking of switching back because of all the hassle.

I can't get DVDs to play at all and Quake 4 doesn't work. Yes, its fine running openoffice for all the serious stuff, but I want to be able to use it as my main OS and be able to wipe windows. I don't feel I can do with with the amd64 ubuntu.

---

