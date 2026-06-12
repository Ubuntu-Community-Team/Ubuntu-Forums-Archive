---
title: "what the heck happened"
date: 2008-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by miesnerd on 2008-03-05
Ok, im by no means a newb, but I am totally lost as to undestand what happened. I installed aria, then things went awry. No big deal, I just reboot and my trusty ubuntu will be fine, but it wouldnt boot, I tried about 3x and it was a no-go. Now, since I just switched graphics cards to Nvidia, I dont see anything anymore before the GDM comes up. That's all fine and well, but the fact that I cant see anything prevents me from knowhing what went wrong.

FYI, to get back to my regular user, I had to boot into recovery mode, then logout of root, then it let me finally log in as my regular user, which I thought was extremly odd..

What log am I looking for to explain what went down? This was just weird beyond belief.

---

### Post by prince_niceguy on 2008-03-08
when the grub menu comes up press e.

now in the next screen again press e. remove the splash and quiet from the grub line and press b. now you would be able to find out where there is some delay or hanging.hope that gives some help to start of with

---

### Post by IanW on 2008-03-08
This is/was a known bug when using Nvidia graphics. ([https://bugs.launchpad.net/ubuntu/+bug/140908]("https://bugs.launchpad.net/ubuntu/+bug/140908"))

Once you've logged in by doing what prince_niceguy says above, you can make the same changes to /boot/grub/menu.lst

---

