---
title: "Problems with AMD X2 6000+"
date: 2007-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by LaughingFalcon on 2007-11-02
Here are my specs
AMD Athlon 6000+
Foxconn nForce 590
EVGA 8600GTS
3 GiB Patriot memory (all works 100%)

My problem is that whenever I go to install the 64bit (I have tried 6.06, 7.04, and 7.10) it gets to a screen where it says

"Kernel Alive
kernel direct mapping table up to 100000000 @ 8000 - d00"

and then the monitor says that it has no signal.

I have searched the forums and seen how many other people had the same problem and I have tried all of the suggested remedies, I tried using "nosplash noapic nolapic nacpi acpi=off irqpoll" after pressing f6 and setting the screen to 640x480x16 and it still doesn't work. I also have ACPI turned off in the BIOS.

I have also done md5 checks on all the cd's that I have used. And I tried the alternate install (the cd botted up and installed but then I couldn't boot into the system).

Is there anything else that I can try?

---

### Post by crjackson on 2007-11-02
> **LaughingFalcon said:**
> Here are my specs
AMD Athlon 6000+
Foxconn nForce 590
EVGA 8600GTS
3 GiB Patriot memory (all works 100%)

My problem is that whenever I go to install the 64bit (I have tried 6.06, 7.04, and 7.10) it gets to a screen where it says

"Kernel Alive
kernel direct mapping table up to 100000000 @ 8000 - d00"

and then the monitor says that it has no signal.

I have searched the forums and seen how many other people had the same problem and I have tried all of the suggested remedies, I tried using "nosplash noapic nolapic nacpi acpi=off irqpoll" after pressing f6 and setting the screen to 640x480x16 and it still doesn't work. I also have ACPI turned off in the BIOS.

I have also done md5 checks on all the cd's that I have used. And I tried the alternate install (the cd botted up and installed but then I couldn't boot into the system).

Is there anything else that I can try?

Instead of using nosplash, how about deleting the word splash and try that.  It shouldn't be any different, but it is on one of my machines.

---

### Post by bdamon on 2007-11-02
I have had the same thing happen. If you wait long enough you'll eventually get  to the desktop and can perform the install. The problem still existed for me after installation. I tried a number of the fixes from the forums none of which worked for me so I changed splash to nosplash in the grub menu.lst file for the time being.

---

### Post by LaughingFalcon on 2007-11-02
Alright that worked, thanks.

The only problem is that now I can't tell if it is booting up properly :( , so I guess I will have to keep on the lookout for a fix.

---

### Post by American_Outcast on 2007-11-02
> **LaughingFalcon said:**
> Alright that worked, thanks.

The only problem is that now I can't tell if it is booting up properly :( , so I guess I will have to keep on the lookout for a fix.


Same issues for me as well. I have an AMD x2 4000+. Once the system is installed go into boot>grub>menu.lst and take out the entries for quiet. That should let you see it booting and shutting down.

Mine looks like this,

> title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d581e8f2-25f6-4be9-ac12-5cf53a2624b1 ro
initrd        /boot/initrd.img-2.6.22-14-generic

---

### Post by LaughingFalcon on 2007-11-02
That worked perfectly, thanks a lot.

Slightly off-topic but the speed difference in Thoggen under 64 bit is amazing.

---

### Post by dagyrox on 2008-03-29
For some people, you might have to wait long enough and the hit ctrl+alt+f7.   I don't know why it does this, but so far on my installs i've had to do this.

---

### Post by Nythain on 2008-03-29
another alternative on the installation end of things for people having this problem... use the alternate install iso... it doesnt "boot into" a desktop environment to install, it has its own "text based" installer, wich works marvelously

also, an alternative to removing the "splash" at a grub level, is to search these forums for "adjust usplash resolution" or something similar... it will give a few results on how to set a resolution that your monitor is much more likely to accept, thus curing teh "out of range" issue...

---

### Post by crjackson on 2008-03-29
> **Nythain said:**
> 
also, an alternative to removing the "splash" at a grub level, is to search these forums for "adjust usplash resolution" or something similar... it will give a few results on how to set a resolution that your monitor is much more likely to accept, thus curing teh "out of range" issue...

That doesn't work as consistently as just removing the word splash.  I've done nearly 200 installs on various machines and while this will often give good results, it will often fail as well in my experience.

---

