---
title: "Just installed x64 and am having a few problems."
date: 2007-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by extracted on 2007-09-10
I downloaded the 64 bit 7.04 live cd and wanted to do a dual boot os, to make this easy I just decided to back up all my files to my other computer. I then removed all the partition data and made a 50gig (out of an 80 gig drive)  ntfs partition for windows. The installation went smooth, I updated windows installed what I needed. My next step was, rebooting with the Ubuntu cd. I tried to install Ubuntu to the hard drive. I told it to just use all the unallocated hard drive space for the install. When it got to copying files it hung at 22%. After about 10 minutes I rebooted the pc, expecting it to just reboot off the live cd, but what I got was "can not load operating system" error. So i figured I would try to reboot again, same thing. ( Just a note: I tried to go back to boot to windows but the boot loader was gone i also tried the windows installation cd  and i kept getting the same can not load operating system error.) in the end I had to boot w/o the hard drive plugged in, and wait tell the boot loader was on screen and then plug the hard drive in   .
Next I went back to install Ubuntu to the hard drive, and it worked perfectly. 

Now the only problems I am really having is I am trying to use this computer for learning programing and other sorts. When ever I try to include a header in a C program the gcc compiler tells me,
gcc -o p1 p1.c
p1.c:1:19: error: stdio.h: No such file or directory
So does Ubuntu not install any of these library by default ?  


Also I can't install source code. I wanted to download a program that wasn't in the online Ubuntu library and when I try to do a sudo ./configure I get this error
 checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

I also tried ./make
 sudo make
make: *** No targets specified and no makefile found.  Stop.


Any help well be much o appreciated.

---

### Post by John.Michael.Kane on 2007-09-10
From the looks of it, You need to install the build package.

This should get you going.
```
sudo aptitude install build-essential
```

And if your making deb's for personal use you may want to install this.
```
sudo aptitude install checkinstall
```

Then you can run sudo checkinstall -D" instead of "sudo make install", it should then install the software while giving synaptic all the needed information to see it, As well as create a .deb.

---

### Post by extracted on 2007-09-10
Thats a Big help,

I only got like 2 more problems that I can see atm.
I am use to fedora 7 and I am use to seeing my source code highlighted like variables green  strings red ext.. ext.. ext..  But I cant seem to duplicate the same results is there some where to configure the default settings for vim to do that.

also Ubuntu installed my sound and I can hear it  But I have to have my speakers As load as possible to hear whats coming out of them ?  I have all the volume settings maxed in Ubuntu as well.

---

### Post by John.Michael.Kane on 2007-09-10
For vim syntax highlighting these may help
[http://ubuntuforums.org/showthread.php?t=413696](http://ubuntuforums.org/showthread.php?t=413696)
[http://www.vim.org/scripts/script.php?script_id=790](http://www.vim.org/scripts/script.php?script_id=790)

Regarding your sound issue what sound card is running on your machine?

---

### Post by extracted on 2007-09-10
Its intergrated in to the Abit Motherboard I think its a Real Teck Ac-97 
5.1

---

### Post by John.Michael.Kane on 2007-09-10
> **extracted said:**
> Its intergrated in to the Abit Motherboard I think its a Real Teck Ac-97 
5.1

Please type the below command in your terminal, and post the output.
```
lspci
```

---

### Post by extracted on 2007-09-10
Actualy I got my sound problem taken care of, Thanks.  But can you mount network Samba shares ?

---

### Post by John.Michael.Kane on 2007-09-10
> **extracted said:**
> Actualy I got my sound problem taken care of, Thanks.  But can you mount network Samba shares ?

Take your pick.
[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605&highlight=mount+network+Samba+shares")
[Howto Easy FuseSMB - access Samba shares from ALL programs. - automatic access to win]("http://ubuntuforums.org/showthread.php?t=525736&highlight=mount+network+Samba+shares")
[Mount samba shares with utf8 encoding using cifs]("http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+network+Samba+shares")
[SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by extracted on 2007-09-10
I read through it but I am trying to mount the samba shares from my other linux box on to this one running Ubuntu.  I am not for sure if i am just missing where it talks about it or what :(

---

### Post by extracted on 2007-09-10
Okay I got the samba thing working. But now if I try to watch a movie via Mplayer I get the error:
error opening/initializing the selected video_out (-vo) device

---

### Post by John.Michael.Kane on 2007-09-10
> **extracted said:**
> Okay I got the samba thing working. But now if I try to watch a movie via Mplayer I get the error:
error opening/initializing the selected video_out (-vo) device

The mplayer error means you have to select the video out.

Open mplayer right click, and click on preferences---->video---->x11 or gl. While there, also select enable direct rendering.

---

### Post by Lonthong on 2007-09-10
> **extracted said:**
> Okay I got the samba thing working. But now if I try to watch a movie via Mplayer I get the error:
**error opening/initializing the selected video_out (-vo) device**

Issue the following command to get a list of available video output drivers:
mplayer -vo help
gedit ~/.mplayer/gui.conf
change the video driver: vo_driver = "x11" (it might be different for you though. I solved it by trial & error based on available drivers above)
and/or to ~/.mplayer/config:  vo = x11

---

### Post by extracted on 2007-09-10
Thanks for all the help, I got every thing working now except one thing.

I can mount samba shares now on my ubuntu installation but I can not seem to get them to auto mount when i reboot I tried adding

//exatron/Other   ~/other   smbfs   credentials=/etc/samba/user,rw,uid=extracted
   0   0
//exatron/TV   ~/TV   smbfs   credentials=/etc/samba/user,rw,uid=extracted   0  
 0
//exatron/Music   ~/Music   smbfs   credentials=/etc/samba/user,rw,uid=extracted
   0   0
//exatron/Movies   ~/Movies   smbfs   credentials=/etc/samba/user,rw,uid=extract
ed   0   0

i also created the /etc/samba/user   file with 
username = extracted
password = ******

but still when I boot it says it can not find /home/extracted/Sharename.....

:(

---

### Post by John.Michael.Kane on 2007-09-11
There seems to be a few ways to handle auto mounting.

You can try using fstab.
```
sudo gedit /etc/fstab
```

Here are two example lines. you will have to edit it.
```
//exatron/shared /shared cifs username=xxx,password=xxx,auto,user 0 0
```
```
//exatron/data /mnt/exatron cifs rw, domain=whatever it's name is,username=xxxx,passwd=xxxx,uid=administrator,gid=root 0 0

```

Script method
[Automatically mount and unmount network shares]("http://ubuntuforums.org/showthread.php?t=375563&highlight=automount+samba+shares")

---

