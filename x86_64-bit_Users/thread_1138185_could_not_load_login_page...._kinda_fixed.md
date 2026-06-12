---
title: "could not load login page.... kinda fixed"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by piratemurray on 2009-04-26
:confused:

Yesterday I was messing about trying to get the ati proprietary drivers installed for my system and seemed to have messed up the booting of my machine.

I was also trying to get the usplash progress bar thingy to display since I've never ever seen that on my computer. I installed hardy on my parents computer and it appears there, just not on mine. 

Anyway I'm on jaunty now and I used it for about a day without any problems until I started to mess around.

The long and short of it is that I edited the file /boot/grub/menu.lst and removed 'splash' after the 'ro quiet' bit. I could never see the splash screen anyway so I thought why not?

> title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e2525aeb-9d55-44fe-afaf-d1f28f28a93c ro quiet  
initrd		/boot/initrd.img-2.6.28-11-generic
quiet


Jaunty loads now and I can see the graphical login. I haven't rebooted yet to see if it still appears but I hope it does. 

What I don't understand is whether this is a fglrx/ ati problem with jaunty (never experienced this under hardy), whether it was me tinkering with startup manager or something else I may have inadvertently done.

Anyways I hope this helps anyone else. Ubuntu is awesome and the community rocks.

My machine in case you need to know.

AMD Athlon 64 Processor 3200+
ATI X300
Jaunty

---

