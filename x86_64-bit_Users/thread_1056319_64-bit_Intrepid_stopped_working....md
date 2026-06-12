---
title: "64-bit Intrepid stopped working..."
date: 2009-01-31
forum: x86 64-bit Users
---

### Post by mjpatey on 2009-01-31
Hi, group-

I just tried booting into my 64-bit Ubuntu 8.10 install... during boot, I start to see the Ubuntu usplash animation, then it backs out to some text:

> Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/b2c26272-2888-4963-9035-74dde0f182ca) = dev(8,6)
kinit: trying to resume from /dev/disk/by-uuid/b2c26272-2888-4963-9035-74dde0f182ca
kinit: no resume image, doing normal boot...

Ubuntu 8.10 mjpatey-desktop tty1

mjpatey-desktop login: mjpatey
Password:
init: tty1 main process (3680) killed by SEGV signal
init: tty1 main process ended, respawning

Ubuntu 8.10 mjpatey-desktop tty1

mjpatey-desktop login: _As you may be able to tell, I attempt to log in as myself, then type my password, and it responds by saying it was killed by a SEGV signal, and respawns tty1, asking me for username and password again. This continues as an endless loop if I keep trying to log in.

So I'm stuck without the ability to boot into my 64-bit Intrepid install. I can get to a root prompt if I boot to Recovery mode, but when I attempt to start X, or repair it, I get errors saying my filesystem is "read-only".  I tried booting to an earlier kernel, but that yields the same errors described in the quote box above. I do have a 32-bit install that I can fully boot into... it and the 64-bit install share a /home partition, so all is not completely lost, thankfully.

Still, I want my 64-bit install back... any idea what to do?  Thanks in advance for any light you can shed!

-Mark

---

### Post by Yashiro on 2009-01-31
Boot using a LiveCD and run a fsck (or do a check with partition editor) on your OS filesystem.

---

### Post by mjpatey on 2009-01-31
I will try that, though for some reason, when I boot into my 32-bit installation (akin to booting from a live CD for this purpose), I'm able to write to the partition-- it does not register as "read-only" as it now does from the 64-bit install.

I actually did the fsck that appears in the menu when booting in Recovery mode, and it was unremarkable.

---

### Post by Yashiro on 2009-01-31
There is nothing you recall tweaking or installing prior to your last successful boot?

---

### Post by mjpatey on 2009-01-31
No.  But this was the first time since adding/removing some iffy software that I've done a system update.  The re-boot after updates went fine, though.  This is the second reboot after updating.

The "iffy" software I'm referring to is "Splashy", a replacement for the default Usplash.  I had to follow a "howto" to install it, and it involved making some changes to a system file or two (I wish I could remember what!) in order to make the latest version work with Ubuntu 8.10 64-bit.  When removing it and re-installing Usplash (as SPlashy did not work well for me), I didn't go back and undo the changes I'd made manually.  Maybe this is what's causing the problem, though it's strange to me that it didn't fail like this the first time I tried to reboot, only from the second time onward.

---

### Post by Yellow Pasque on 2009-01-31
If you were altering files related to the splash screen, try booting a non-recovery kernel without the splash keyword (i.e. edit the kernel line in grub and remove 'splash' and 'quiet')

---

### Post by mjpatey on 2009-01-31
That sounds like an AWESOME idea.  I will try that as soon as I get home tonight.  Thanks for the suggestion; I'll post back here with the results!

-Mark

P.S.:  I would SSH into it from work, but network security here is very tight (tied into a very large corporate network), and the only time I've tried it, I quickly received a note form the head of IT saying, "Please don't."  :-D

---

