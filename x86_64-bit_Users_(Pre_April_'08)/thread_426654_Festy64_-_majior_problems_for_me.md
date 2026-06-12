---
title: "Festy64 - majior problems for me"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by theorem_hunter on 2007-04-28
my hardware :
CPU : AMD64 Athlon 3000+ 
RAM : 1 gig DDR 400 (2x512)
Main Board : Nforce4
VGA : ATI Radeon X700

hd1 : Western digital SATA 250G - all ext3 -
200M = /boot
50G = /
rest = /home

hd2 : Samsung 120G - all ext3, just 1 big partition

i installed with the 64bit alternate Festy 7.04 - did the check & everything is ok.

1. i am aware of the X700 problem with festy, i have tried using fglrx driver - didnt fix my problems...

when boot my PC i get a error 22... not found or something like that...
so what i do is press e e & edit the boot hard drive to hd(0,1) - or something like that to boot

i have to select to run in fail safe mode because of the X700 issue...

so 2 questions so far... which file do i edit to set grub to boot from the right hard drive

what can i try to get my X working properly so that i can boot straight into Ubuntu with out using fail safe mode?

currently i have to type "gdm" to start X....

i want to use XChat-Gnome, but every time i start it, it shuts down/crashes...

i was working fine, but then i was building some libraries that i think have nothing to do with XChat - building the libraries failed & XChat crashes...

were is the error log for XChat stored so i can try fix the problem?

trying to launch from the terminal does not give me anything useful to work with... 
xchat-gnome 
Segmentation fault

i tried installing normal Xchat but the same thing happens...

any help would be great :)

{i like using 64bit Ubuntu... i dont want to use 32bit }

---

### Post by kuja on 2007-04-29
Edit the /boot/grub/menu.lst file. As per the graphics issue, you can try to play around with graphics drivers by using this command: "sudo dpkg-reconfigure xserver-xorg -phigh"

---

### Post by theorem_hunter on 2007-04-29
i reformatted back to edgy64... im doing a 3rd year project & i lost time trying to fiddle with things... i'll try 64bit festy in the holidays again...

---

