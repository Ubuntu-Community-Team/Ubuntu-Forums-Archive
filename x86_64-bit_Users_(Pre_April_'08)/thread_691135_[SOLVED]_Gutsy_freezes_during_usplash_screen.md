---
title: "[SOLVED] Gutsy freezes during usplash screen"
date: 2008-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Angus77 on 2008-02-08
I've been using Gutsy for months now (upgraded as soon as I could).  I don't know why this would only happen now.

I just turned off the computer normally this morning (I don't remember installing any updates), and this evening I can't get past the usplash screen.

The progress bar fills up maybe a few pixels worth and then just hangs there.

Now my wife's pissed off at me because i can't get her logged in to check her email!

Help!

---

### Post by prince_niceguy on 2008-02-09
in the grub boot menu, hit "e" and remove splash and quiet from the entry.
now hit "b" to boot it will give you messages and you will be able to know where it is hanging...

post that and it should be able to help.

---

### Post by ffahog on 2008-02-09
I'm having a similar problem. My usplash screen gets about a quarter of the way across (it usually takes longer here and then zips to the end). Suddenly, the screen clicks and goes blank, except for a white underscore cursor that flashes in the top left corner.

One additional hangup that I'm having is that I turned off the boot menu (and put the "seconds" spent on it to 0), so I don't have a chance to hit 'e' and then watch to see where it gets hung up.

(I do have the Gutsy Ubutnu CD lying around, if I need to reinstall.)


Any suggestions on how to go forward?

---

### Post by ffahog on 2008-02-09
. . .and while I was here searching the forums (I'm on a Mac laptop), constantly restarting the PC, it worked.

Bizarre.

I hope that it does happen again. Is there any kind of 'checking' I can do to see what the problem may have been? I'm afraid to turn off the PC now that it's working.

---

### Post by Angus77 on 2008-02-10
What I get is:

```
Check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/bcf6edb3-1f4d-4f01-9f05-8d809393cd6c does not exist. Dropping to a shell!
```

Then it does indeed drop to a shell.

I have no idea what that uuid is supposed to be---it's not in my fstab, so I can assume it's not a drive partition?

---

### Post by prince_niceguy on 2008-02-11
is it possible for you to send you /etc/fstab?

if yes then post it. also, do you have idea about which partition is your root on. if yes, then we can modify the fstab to have your root entry done. I am positing my fstab for your reference.

I think the problem is that your root is not getting mounted.

---

### Post by Angus77 on 2008-02-11
Here's my fstab.  My root is on sda1.  (I'm working on another Gutsy installation with root on sda2 right now).

---

### Post by Angus77 on 2008-02-15
bump

---

### Post by prince_niceguy on 2008-02-15
any idea what was your root partition e.g. mine is /dev/sda5.

if you can get that then you can do the following.

in the grub menu, select the kernel you want to boot into, press e, then again press e. now change the root=UUIID............ to root=/dev/sda5 or whatever is your root. now press b.

it should start up. once in there go to your /boot/grub/menu.lst and change your root=UUID....... to root=/dev/sda5 or whatever is your root partition. to ensure it is permanently stored in grub. save and come out.

now try rebooting again to see if it working or not without the editing in grub.

---

### Post by Angus77 on 2008-02-17
Thanks a lot, prince_niceguy!

Problem solved!

---

### Post by prince_niceguy on 2008-02-17
Glad it helped...:-)..

---

