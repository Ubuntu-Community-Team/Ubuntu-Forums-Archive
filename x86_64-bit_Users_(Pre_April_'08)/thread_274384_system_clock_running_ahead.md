---
title: "system clock running ahead"
date: 2006-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Menyus on 2006-10-09
I have an intel core 2 duo E6400 cpu/ASUS P5B mobo system running Ubuntu desktop v 6.06.1 64-bit. Unfortunately, my system clock is running consistently fast. Does anybody have any idea what I could do to make it run on time without having to constantly synchronize with the time server?
Thanks,
Menyus

---

### Post by jpkotta on 2006-10-09
Is there a BIOS setting of some sort?  Does this happen on other OSes?  

You could complain to the manufacturer.  Also, [https://help.ubuntu.com/community/NTPTimeSynchronisation](https://help.ubuntu.com/community/NTPTimeSynchronisation)

---

### Post by Menyus on 2006-10-09
It's a dual boot system with Win XP & Ubuntu. There is no problem with the clock under XP.

I am sure it's some sort of a multiplier issue (although I haven't spent te time to figure out the rate), but I'm afraid if I changed some BIOS setting, my clock under XP would be screwed up.

---

### Post by siersmak on 2006-10-09
I had this same problem today on my Inspiron 6400 (Intel Core 2 Duo w/64-bit Dapper).  Booting with the kernel options 'no_timer_check' and 'notsc' seems to have fixed it.  

To test if this works for you, reboot your machine.  When the boot menu comes up, press 'e' to edit the current selection.  Cursor down to the line that starts with 'kernel' and press 'e' again.  Add 'no_timer_check notsc' to the end of the kernel line, and hit 'return'.  Then press 'b' to boot with those options.

If this does indeed work, you can add these options to the kernel line that corresponds to your default kernel in the /boot/grub/menu.lst using your favorite text editor.

-Ken

---

### Post by Menyus on 2006-10-10
Ken,

Thanks for the tip, it really seemed to solve te problem.

---

### Post by kuja on 2006-10-10
Good, then all that's left is to finalize it.

Open the file /boot/grub/menu.lst with your favorite editor with root privileges.

Scroll down a ways to a line that looks something like this:
```

#kopt=root=/dev/sda8 ro

```
Add the options no_timer_check and notsc to the end of it in the same manner you did before. Save the file.
Then, in a terminal, run the command "sudo update-grub" and it should be finalized, and will take effect with all future kernel updates too.

---

### Post by Menyus on 2006-10-10
All done. My clock is now dead on. Thanks again.

---

### Post by ankle on 2006-10-10
I had the same problem in Dapper - xine would play media too quickly as well. It was fixed by an update to Edgy.

---

### Post by eschwalb on 2006-10-15
I'm dual booting Windows XP and Dapper on an intel core 2 duo E6400 with a gigabyte GA-945P-S3 motherboard.  I tried no_timer_check to fix my clock problem with no luck after reading a few other threads.  However no_timer_check notsc combined did fix the problem (it also seems to haved fixed an audio quality problem that I've been having with Amarok v1.4.3 as well, perhaps this is related to the xine issues that others mentioned).  I'm happy this is working now, but can anyone explain what exactly adding no_timer_check notsc does?  Thanks in advance,

---

