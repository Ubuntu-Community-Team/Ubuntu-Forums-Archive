---
title: "Wierd xserver stuff.. IM NEW"
date: 2005-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Boggles3 on 2005-07-18
Ok heres my wierd problem

i keep having to reinstall my nvidia driver from consol and every time i get thes wierd errors during install but it works anyways..

ok so sometimes when i boot i get this message after the screen flickers a few times...

"i cannot start the x server(your graphical interface). it is likely that it is not set up correctly.would you like to view the x server output to dianose the problem?
and gives me yer/no choice.
i select yes and it shows me some info on my xserver and kernel im running stuff like that.
then it asks me if i would like to view the detailed x server output as well? this gives me mostly the same info..

then i press enter for ok and i get this message...
"i will disable this x server for now. reset gdm when its configured corectly."
then i am dumped into console.


luckily the first time this happend i still had the nvidia accelerated driver for my card on my desktop so i could easily find it from console and run it ..(the first time this happend i freeked and after hours of dicking around i decided wtheck ill reinstall the driver just for giggles)..

this is what my install prosses looks like when i installed the driver(it also looked the exact same the first time i installed the accelerated driver).

so first off it gives me a message saying the driver is already installed and it will be replaced if i proceed.. yadayada(no this part did not happen the first time i installed thislol)
so i continue and i get this message
"no precompiled kernel interface was found to match your kernel; would you like the installer to attempt to dl from the nvidia ftp server?" yes/no (i choose yes)
then it comes back saying there was no match found on the ftp and it ses "this means that the installer will need to compile a kernel interface for your kernel. [ok] enter

then i get this message
"WARNING:your linux kernel has problems in its implamentation of change_page_attr kernel interface. the nvidia kernel module will attempt to work around these problems, but system stability may be affected. it is recommended that you update to a 2.6.11 or newer kernel.
i hit enter for [ok] and it starts biulding the kernel moduale and finishes that with no errors or anything..

then it asks
"install nvidia's 32 bit compatibility open gl libraries?" [yes/no]
i select yes.
it continues and then i get this msg...

"WARNING:your driver installation has been altered sence it was initionaly installed; this may heppen for example, if you have since installed the nvidia driver through a mechanism other than nvidia-installer (such as rpm or tarballs). the nvidia installer will attempt to install as best it can."
it uninstalles onld driver and then installs
then i get this msg...
"Error:the runtime configuration check failed for library 'libGL.so.l.o.7667' (expected:'/emu/ia32-linux/usr/lib/libGL.so.1',found:'/usr/lib32/libGL.so.1'). the most likely reason for this is a conflicting openGL libraries are installed in a location not inspected by 'nvidia-installer'. pleas be sure you have uninstalled any third party openGL and third party graphics driver packages."

then i hit enter and i get this
"Error:installation has failed. please see the file'/var/log/nvidia-installer.log' for details. you may find suggestions at nvidia read me file at the driver distribution page."

i know this sounds really bad but then when i do /etc/init.d/gdm restart again it actualluy loads.. i dont get that first x server error...and when i poke around in settings and look around nvidia it ses that the 7667 accelerated driver is installed...??? even though it just sed instalation failed

Now about the 32bit libraries.. if i choose not to install then then it ses instalation complete at the end and the library errer does not occure but all the rest is the exact same...HOWEVER this xserver failing crap still happens weather i installed the 32bit libs or not so thats not the problem..



and sometimes when i reboot i get THATSTUPID XSERVER NOT WORKING CRAP and have to reinstall the driver again..

any ideas.. do i need to somehow change my xorg.conf or something so it stops having issius   
thanx

---

### Post by Flac on 2005-07-18
not that it matters to me...but

[http://ubuntuforums.org/showthread.php?t=49475](http://ubuntuforums.org/showthread.php?t=49475) <--isnt this the exact same post? Just a humble request, i think we shoudl try to keep our posts organized as to not create mindless clutter.

---

### Post by Boggles3 on 2005-07-18
sorry i missed some of the sound stuff...
the sound is takin care of but this xserver stuff confuses me..

every other time i reboot it seems that i must reinstall the driver.. and it always says that th driver is already there... so why if i reinstall does can i restart gdm and then it works for 1 reboot and then i have the prob again..

i posted again because the other one kinda died.. and i sokved half of my problem..
im sure if the admins think im flooding then they will just delete the post or something..

anyways any ideas people???

---

