---
title: "cant get ubuntu to install or load"
date: 2007-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by computerjunkie on 2007-08-04
I recently built a computer and am going through linux withdrawal. I have tried ubuntu 6.06 and 7.04. the 32 bit dapperdrake hit a kernel panic and the 64 bit version was soooooo slow it was unusable even in a live environment. I tried to load up 7.04 but all I got was a black screen


any special boot options I can try?

My CPU is amd athlon 64 x2 4600+

---

### Post by Cappy on 2007-08-05
Try
```
nosplash
```
or
```
nosplash noapic nolapic
```
on the 7.04 (Feisty)

---

### Post by xieu90 on 2007-08-05
hehehehe
hi brother
we have the same cpu
check my topic amd x2 is its name
I think you have the same problem like mine

when the boot screen appear with the menu
choose the start or install ubuntu
press F6 when that menu appear then at the end before -- type noapic nolapic nosplash (I don't really get what these thing mean, and at me noapic is enough)
after typing it there press enter
i hope this will help you
special thank to SD-Plissken and Xzero
if you can ask those two, I'm in love with their knownledge about ubuntu

---

### Post by computerjunkie on 2007-08-05
That didnt work.

I pressed F6 and deleted all of the other boot options that were there and typed nosplash noapic nolapic 
and I actually got text instead of a black screen until :

" 1.012000 kernel panic - not syncing: VFS: unable to mount root fs on unknown block (104,1)"

oh, maybe I was supposed to leave those other boot options there. Reboot, F6, left the other boot options and added the three I tried before, pressed enter. "loading please wait" black screen and and cd stopped spinning.

um...that wasnt supposed to happen. bad cd or image maybe? it gave me a black screen and stops spinning when i try to test the cd as well.

---

### Post by Anti-medic on 2007-08-05
I am having a similar problem.  I have an intel duo core with 4 gb ram bfg 8800gtx312 video card.  Vista home premium on one drive and I am trying to install ubuntu on the other drive.  I insert cd and reboot machine and the boot menu appears.  I click on install and the machine runs but blank screen.  I have a nvidia 680sli mb.

---

### Post by xieu90 on 2007-08-05
eh
I don't know
I pressed F6 and [COLOR="Red"]added[/COLOR] those 3 between quiet splash and  --
like this
quiet splash [COLOR="Red"]noapic[/COLOR] --

and then about 5 second it continues
+ be careful with ubuntu versions 
ubuntu for 64 bit are different from 32 (i think)

if that won't work then try to ask those two I mentioned

yeah, how did you get the cd or dvd ? did they send you the cd or you downloaded ?
mine is 7.04 for 64 bit

---

### Post by computerjunkie on 2007-08-05
a friend downloaded the image for me and threw it on a cd that I took the image off of and burned a new cd as an iso disc. I dont know what bit version she downloaded for me, but i know it was 7.04. maybe 32 bit since it hit a kernel panic just like 32bit dapperdrake did. I really hope i can install ubuntu. i really do love it, synaptic and all, its a wonderful OS and much easier to manage package wise than RPM based distros, but maybe its time to look into solaris or back into fedora, as that was the first linux I ever used. I wonder how far its come since I used it. my motherboard is a chepo JETWAY board, is this throwing off linux because of improper or nonexistant drivers? The board is based on the AMD 690G and SB600 chipsets. This board uses Radeon X1250 chipset for video and has an HDMI port. Does Ubuntu work with these chipsets?

I bought this board from newegg.com, here is the link:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153064](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153064)

---

### Post by Anti-medic on 2007-08-06
I will try that when I get home from work tonight.  I am running 64bit and have a 64bit cd/dvd that was sent to me from the ubuntu site.  I am glad that I am not alone in this.  Computerjunkie can share my woes.

---

### Post by six on 2007-08-06
I had exactly the same problem to start with. Try just this in your F6 kernel parameters:

```
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet --
```

Here's my earlier thread for more info:

[http://ubuntuforums.org/showthread.php?p=3099809#post3099809](http://ubuntuforums.org/showthread.php?p=3099809#post3099809)

---

### Post by xieu90 on 2007-08-06
this is my error when I run with ubuntu 32 bit 7.04
[30.679359]..MP-BIOS bug:8254 timer not connected to IO-APIC.
[30.858010] kernel pani  - not syncing: IO-APIC + timer doesn't work! working with apic = debug and send a report. Then try booting with the 'noapic' option
[30.858036]

and here nothing will do a thing (frozen keyboard, without mouse)

is it like this ?

if so I tried to added noapic nolapic nosplash (even only noapic worked for me)
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet --   [before,oroginal when you press F6]

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet [COLOR="Red"]nosplash noapic nolapic[/COLOR] --  [after typing]

then press Enter and it will work if you have the same problem like I had, otherwise ... I have no idea

---

### Post by Anti-medic on 2007-08-06
when the boot screen appear with the menu
choose the start or install ubuntu
press F6 when that menu appear then at the end before -- type noapic nolapic nosplash (I don't really get what these thing mean, and at me noapic is enough)
after typing it there press enter


I did this and same thing.  Machine is running fine sounds like its installing but blank screen.  I am thinking its my video card.

---

### Post by xieu90 on 2007-08-06
before i installed ubuntu on my 64 bit computer I tried to install it on a laptop
something similar with blank screen
hard disk and cd run like crazy for about 2 hours then it gets into install menu, but
the whole system runs very slowly 
i don't really know what it could be
from now on I will observe this topic only
I wish you guys can find your way to Ubuntu

---

### Post by Anti-medic on 2007-08-06
I followed six's advice and read this thread: [http://ubuntuforums.org/showthread.p...09#post3099809](http://ubuntuforums.org/showthread.p...09#post3099809)  

I booted from cd and pressed F6.  Erased the word splash and typed NOAPIC and NOLAPIC after --. I am now staring at the ubuntu desktop ready to install it.  Started just fine.  Thank you SIX!!!!

I will keep you informed of any more problems as I finish this install.

---

### Post by six on 2007-08-06
Glad to hear it worked! 8)

Don't forget to remove **splash** parameter from the /boot/grub/menu.lst file as well. Let Ubuntu update itself with the ~100 or so updates after it's installed to HD, as it will find a newer kernel. If you do have to reboot before you get a chance to edit the menu.lst file, all you have to do is press F6 and remove the **splash** as before. (Editing the menu.lst file means you won't have to press F6 any more).

If you don't know how to edit the file, just open a console and type:

```
sudo gedit /boot/grub/menu.lst
```

and that will start a simple GUI text editor.

---

### Post by computerjunkie on 2007-08-08
Ok, thanks for the tip, but it didnt work. I finally didnt get a black screen, but it froze up on:

"Loading, please wait..."

thats all that would happen. i even tried adding the "--noapic --nolapic" after rebooting and deleting splash. nada! Anyone have any ideas?

---

### Post by computerjunkie on 2007-08-08
Im trying to install dream linux 2.2 now and this is freezing up as well. First it froze on the splash screen and never loaded past that, this time i took out the splash and it froze on "configuring system to udev". This is a debian based linux.

man this is annoying

---

### Post by computerjunkie on 2007-08-08
any ideas on why ubuntu wont boot?

---

### Post by butcher99 on 2007-08-09
I finally got it to install.  I have the DVD version and I am not sure what happened that it decided to install.  I changed the default resolution.  To start with I had a Linux partition setup and formatted and I deleted that and then it booted up and I got it installed.  
My system is an amd dual core and an ATI vid card.   I think a deadly combination.  

Once I got it to boot from DVD I installed it and went to reboot.   Now it will not reboot. 

  I do not get any errors, it just dies a few seconds in.

thanks 
jim

---

