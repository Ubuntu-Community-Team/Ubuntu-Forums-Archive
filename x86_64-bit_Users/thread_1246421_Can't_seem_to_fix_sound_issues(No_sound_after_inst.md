---
title: "Can't seem to fix sound issues(No sound after install of 9.04)"
date: 2009-08-21
forum: x86 64-bit Users
---

### Post by JoshuaDB on 2009-08-21
Hi, I am new here, and I am also new at using terminal in Ubuntu.  I have been using Windows my entire life and have just recently dove head first into the Lunix world, without checking the depth first.  This is due to my frustration with Vista and the support I was recieving from HP.  I have been searching the web for answers to why my sound will not work after installing Ubuntu 9.04 64 bit.  I am dual booting with vista 64 bit as some software for work only work with windows.  I have tried a few things in the terminal and would just like to get a little more one on one than trying what others are doing.  If this matters, when I boot into vista the speaker light that is on my laptop is blue and i have sound, when I boot into ubuntu the speaker light is read with the circle slash through and I have no sound.  Nothing is muted and the volume is turned up. With vista if i touch the blue lit up speaker button the speaker turns red and sound shuts off if I hit it again it comes on.  With the Ubuntu it is red and does nothing when i touch the lit up button.  Just stays red.
If any other info is needed I can provide it.

If someone has time to help out I would greatly appreciate it.

JoshuaDB

---

### Post by JoshuaDB on 2009-08-21
I have typed "lspci -v | less" into the terminal and it does not show a device that is installed labeled Audio Device    Why is there no audio device discovered?

I typed in "aplay -l" and I have 3 different hardware devices
card 0 device 0
card 0 device 1 
card 1 device 3
Should I have 3?
 
When I type in "find /lib/modules/` -r` | grep snd"
I get a large list off kernel modules 
How do I know if they are the correct ones?
What else should I do to try to fix this issue? 

Any help would be greatly appreciated!

Thanks
Josh

---

### Post by JoshuaDB on 2009-08-24
Are these my sound cards, cause I'm new to this and not sure?
Should I have two of them?

  	 	 	 	 	 	   Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
 	Subsystem: Hewlett-Packard Company Device 1506 
 	Flags: bus master, slow devsel, latency 64, IRQ 16 
 	Memory at d2400000 (64-bit, non-prefetchable) [size=16K] 
 	Capabilities: <access denied> 
 	Kernel driver in use: HDA Intel 
 	Kernel modules: snd-hda-intel 
 

 Audio device: ATI Technologies Inc RS780 Azalia controller 
 	Subsystem: ATI Technologies Inc RS780 Azalia controller 
 	Flags: bus master, fast devsel, latency 0, IRQ 19 
 	Memory at d2310000 (32-bit, non-prefetchable) [size=16K] 
 	Capabilities: <access denied> 
 	Kernel driver in use: HDA Intel 
 	Kernel modules: snd-hda-intel 



If they are, does anyone know if there are drivers for them?
Thanks

---

### Post by Bear Knuckle on 2009-08-25
Maybe this thread holds helpful information: [http://ubuntuforums.org/showthread.php?p=7265128](http://ubuntuforums.org/showthread.php?p=7265128)

---

