---
title: "Ubunty Jaunty no such file in therminal"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by sunhunter on 2009-05-09
I changed from Ubuntu Studio on ext4 to Ubuntu Jaunty amd64 on ext3 to see if the RT kernel caused problems or ext4.

 I'm installing homebank software, not the homebank that ships with Ubuntu.
So from within terminal:

sudo dpkg -i HomeBank.deb
(note: GDebi can extract the files also correctly.

But then some older libraries have to be installed and so on but something strange is happening.

I go to the folder:

cd /opt/HomeBank
I should be able to start HBSecurity   with ./HBSecurity
But terminal says that the file does not exists.

dir

I see the files. No typing error
if I check with nautilus then I see the files also and can open there the included jpeg and htm files.

I check if the deb files was corrupted or not  cause I got this message on Ubuntu studio This is not the case with Jaunty amd64  so I did google and located which labraries and so on have to be added, but none, read again ..none are able to install wiithing terminal.

Always : no such file or folder.

I was *never* able to get 9.0.4 Jaunty , either as Ubuntu studio or Ubuntu Desktop

Remark: there's a dual boot with windows XP .
XP's eventviewer reported ferquzently that the virtual memory (swap file) was damaged.
chkdsk fixed that but still it a bit weird that both Windows as Ubuntu Jaunty having some sort of problem that might be related to the harddisk.

Has ubuntu a hardisk check application and even some sort of checkdisk for ext3/4?
if it is harddisk related, then there also no reason to test 8.0.4 LTS again.

---

### Post by pixel :-) on 2009-05-09
give me the .deb and the libraries you installed, and where

you can check your ram, with the memory test at boot time. Thats a much thorougher test then the one of the BIOS.

Look first at the ubuntu forum for the program before trying any thing from bellow. If you are a newbe, just buckup and try them the day you decide you want to reinstall

fsck

at boot time, from time to time the sytem uses fsck to check the fille system, the partition must not be mounted. If the partitions are mounted they will be corrupted. This is just a pointer if you do a mistake you are fscked.

A hard disk checker utility, named more or less ***block*** (i forgot the name),again it must be unmounted.

What ever you do start by backing up your data.

---

### Post by sunhunter on 2009-05-09
it's with every .deb file
But in my case, I have to install ```
libstdc++2.10-glibc2.2_2.95.4-27_i386.deb


```I have tried other .deb files and here the same, the deb file can be extracted with GDedit or extracted from within terminal ```
dpkg -i name of deb.dep


``` but if the deb file needs a configuration like ./configure or in this case ./HBSecurity then bash gives the error.

I should always be able to run ./HBSecurity even when there are still missing libraries or whetever.


remark: I can install applications with synaptic or .deb files that install anything, but the the .deb file is used as container format
where ./configure , make, make install are needed then this amlways fails.

ps. I use Ubuntu 9.0.4 amd64

---

### Post by pixel :-) on 2009-05-09
Just tell me exacly what you installed, links to the filles, and to what ever tutorial you are following. If i can't replicate what you are doing i can't help you 

you try to install that [http://homebank.ing.be/EN/index.jsp](http://homebank.ing.be/EN/index.jsp) homebank?

---

### Post by ibuclaw on 2009-05-09
Is this the error message that you are seeing?
```

HBSecGUI: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

```
This is neither an UbuntuStudio/Filesystem problem. This is to do with the architecture of your installed OS.

In this case, you are running a 32Bit executable in a 64Bit environment and it is searching for the file **libX11.so.6** in the directory /usr/lib32, but it doesn't exist.

To resolve, download/install [getlibs]("http://ubuntuforums.org/showthread.php?t=474790"), and run it on the file.

```
sudo getlibs /opt/HomeBank/HBSecurity
```

Regards
Iain

---

### Post by pixel :-) on 2009-05-09
sory tinivol

sunhunter just tell us exacly what you are doing with links to the filles and everything. And don't do anything

getlibs is for later, maybe.

---

### Post by ibuclaw on 2009-05-09
Actually, I've just looked, homebank is available in the repositories...

```
sudo apt-get --purge remove homebank
```
```
sudo apt-get install homebank
```

Then type in
```
homebank
```
To run it... or go to **Applications -> Office -> HomeBank**

Regards
Iain

---

### Post by sunhunter on 2009-05-11
Pixel: yes, ING belgium.

Tinivole: I did not try getlibs yet, getlibs is installed tho.


The Homebank version in the repositories  is not a valid one.
This version can not work with ING.

I follow the instructions located on:

[http://www.linuxontdekt.be/2008/07/06/ing-homebank-op-ubuntu-804-64-bit/](http://www.linuxontdekt.be/2008/07/06/ing-homebank-op-ubuntu-804-64-bit/)

Sorry, not availabe in englisch but, the steps can be follwoed if you look at the linux commands.

I can extract the deb both from within terminal as with the GDedit application of Ubuntu.
Ia32-libs are installed by default.


The step : ./HBSecurity
Fails. It should give the error: [I]“error while loading shared libraries: libtiff.so.3

[/I]But, terminal reports that the file HBSecurity does not exist

dir *.* shows the files tho and nautilus shows them too.
Sudo su : root access same error


Will try getlibs

---

### Post by apparle on 2009-05-11
Are you using command 'sudo ./HBSecurity'

Try using this command 'sudo sh ./HBSecurity'

---

### Post by sunhunter on 2009-05-11
Tinivole:

Thanks alot, Your solution works.

No Apparle,

I use ./HBSecurity

sudo getlibs /opt/HomeBank/HBSecurity
And then I could access ./HBSecurity within terminal.
Great tip Tinvole.

---

