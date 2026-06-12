---
title: "Installing Ubuntu without CDs/DVDs"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by pulse00 on 2006-05-03
Hi,

i'd like to install Ubunto on my TiBook G4, but unfortunately my Superdrive is completely broken. It won't read nor write CDs/DVDs anymore :(

I've already tried to use an external firewire CD-drive and pressing the Option-Key while booting, which brings me to the boot-selection screen. Unfortunately, when i select the Ubuntu Install-CD, the screen gets coloured for some milliseconds, and then i'm back at the selection again.

I have no clue why this happens, i've also tried this using a Fedora Core 5 Installation DVD, same problem.

The last option i could think of is to copy the content of the Install-CD to my external firewire harddisk and install it from there.

It tried this using openfirmware (Alt-Mac-O-F during boot) but i couldn't get it working.
 
Is it possible to install it that way, and if yes, how can i acces the firewire-device through openfirmware?

Or maybe there's another way i'm missing out how to install a system without using the built in CD drive.


Thanks for your help 


-pulse00

---

### Post by evilgold on 2006-05-03
can you boot from a usb? If you can then im sure you could work somthing out with a server install and get the rest of the packages online. 

Also why not install it to your firewire hard disk from another pc, and mount your internal drive and something later.

Lastly...is replacing the internal cd drive not an option?

---

### Post by anders_gud on 2006-05-03
[QUOTE=pulse00]
Or maybe there's another way i'm missing out how to install a system without using the built in CD drive.
-pulse00[/QUOTE]

Hi!
Found this page on how to install via hd or network:
[http://www.debian.org/releases/stable/powerpc/ch05s01.html.en](http://www.debian.org/releases/stable/powerpc/ch05s01.html.en)

I suppose you can boot with a netinstall initrd and vmlinuz and get the rest from a mirror...

---

### Post by pulse00 on 2006-05-03
@ evilgold

no, i don't wanna buy a new drive as my external one works fine for everything else i need ,except booting from it :)

@ anders_gud


Thanks for the link, i'll give it a try!

---

