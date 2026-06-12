---
title: "Nvidia 8800 gtx, black screen"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by felnar on 2007-12-05
Right....another newbie here. Recently installed gutsy 64 via the alternate cd yesterday.

The problem im having is the black screen after booting ubuntu. I know there is  a few threads on the forum...which i have tried like adding noapic nolapic. Well i havent got anywhere with them. If i leave the pc for a little while i can log on and here the sounds thats played(still without any visual), so theres definately some activity going on. Im currently connected to a HDTV via DVI, the native resolution is 1900x1080

Does anyone have any suggestions. Any help would be much appreciated


Specs:
C2D E66000
Asus PN32-E SLI plus
2x 1gig Corsair XMS2
2x Nvidia 8800 GTXs
2X 150 gig WD Raptors
Enermax Galaxy PSU EGA1000EWL

---

### Post by RAOF on 2007-12-06
Dear me.  Shiny new 8800GTXs :).

Have you installed the binary nvidia drivers?  Your shiny new graphics cards are likely to have some problems with the default, open-source drivers merely because few people would have had them around to test.  The nvidia binary driver should support them.

You should be able to install them in recovery mode - you'll either have to select that from the grub menu, or press "esc" during boot to bring up the grub menu.

From there you should be able to run "aptitude install nvidia-glx-new" to download the driver, followed by "nvidia-xconfig" to set it up.  Then you can type "exit" to continue booting, and the GUI should start properly.  Hopefully :).

---

### Post by felnar on 2007-12-06
Hi thanks for the reply.

Unfortunately the only time i have access to the internet is with Winblows! Is is possible to download the driver and burn it onto a disc or put it onto a thumb drive? 

Thanks
James

---

### Post by Cresho on 2007-12-06
64bit with 8800gt driver availability is nil.  I did manage to get the os running but it was so unstable.  black screen here and there.  Running 32bit with 169 beta driver works great at the moment with full 3d acceleration.

---

### Post by Cappy on 2007-12-06
Try using boot parameter ```
nosplash
``` or ```
nosplash noapic nolapic
``` and see if that fixes your problem.

> **Cresho said:**
> 64bit with 8800gt driver availability is nil.  I did manage to get the os running but it was so unstable.  black screen here and there.  Running 32bit with 169 beta driver works great at the moment with full 3d acceleration.

You may have had a bad experience but many others run 64-bit ubuntu with a 8800 without any problems. Statements such as "64bit with 8800gt driver availability is nil" are completely incorrect.

---

### Post by felnar on 2007-12-06
Hi, 

thanks for the suggestion...but adding nosplash noapic nolapic didnt work for me. I think my boot gets as far as "loading, please wait" or something similar to that.

I have no idea what i should try next. :(

---

### Post by Efaill on 2007-12-06
Oh jeez, I fixed this problem 2 days ago with my virgin voyage to ubuntu, I have a similar hardware setup too. It was something to do with the option from the bootloaded (lilo) in my case with option called splash and quiet. I will go hunting for the answer!

Edit: Here we go, this link [http://ubuntuforums.org/showthread.php?t=632658](http://ubuntuforums.org/showthread.php?t=632658) helped me with my problem that sounds similar. Hope it Helps.

---

### Post by Cresho on 2007-12-07
> **Efaill said:**
> Oh jeez, I fixed this problem 2 days ago with my virgin voyage to ubuntu, I have a similar hardware setup too. It was something to do with the option from the bootloaded (lilo) in my case with option called splash and quiet. I will go hunting for the answer!

Edit: Here we go, this link [http://ubuntuforums.org/showthread.php?t=632658](http://ubuntuforums.org/showthread.php?t=632658) helped me with my problem that sounds similar. Hope it Helps.

funny!  this link sends us back here!

---

### Post by Jouke74 on 2007-12-07
To start up, open a recovery session.

At login type your username followed by your password.

Then type "sudo nano /etc/X11/xorg.conf"    (Note linux is case sensitive)

Look for the section device.

Look for the word driver under device.

Change the driver into "vesa"

Then save your document on exit. Note not to change anything else. The nano editor is not the most advanced. Use help if needed.

Type "sudo reboot"

Now let it boot normal, it is supposed to start-up with the general vesa driver. Afterwards you can install the nvidia drivers with Envy, or the restricted drivers manager. And you can also make sure your internet is working (which I suggest you do first).

PS. I noticed that in my case I needed to use the root login, and I don't know how this is handled when you have not set-up any accounts yet after an install.

---

### Post by Efaill on 2007-12-07
> **Cresho said:**
> funny!  this link sends us back here!

oh bum I should pay attention when copying....[http://ubuntuforums.org/showthread.php?t=605282](http://ubuntuforums.org/showthread.php?t=605282). It was late is my exscuse, wasn't trying to be a smart git honest.

---

### Post by felnar on 2007-12-08
Thanks for the help. I have found that the problem is my hdtv. i can boot in recovery...just not normally, the pc now seems to just crash and requires me to reset the machine

---

