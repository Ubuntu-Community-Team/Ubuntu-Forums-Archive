---
title: "new install hangs on login"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by lnihlen on 2006-01-29
Hi,

I just installed ubuntu for the first time.  I usually take the time to build a Gentoo system up from scratch, but I really need a linux platform working this weekend and a friend recommended ubuntu, so here I am.  Setup is as follows:

AMD Athlon 64 4400+ Dual Core
Gigabyte nForce4 SLI MB
2 GB Corsair TwinX Ram
eVGA Geforce 7800GT PCI-E card
DELL 2005fpw widescreen LCD
USB Microsoft mouse
PS/2 Logitech keyboard

Ubuntu installed just fine, and I created a user account.  My first concern is that I don't know the root password on this ubuntu install, but I'm sure on RTFM I can figure it out.  

My biggest concern is that when I log in under the user account I created, the screen goes dark brown and a little bit of garbage is displayed in the center of the screen and then the system sort of hangs.  I can still manipulate the (I assume) hardware mouse, but that's it.  No CTRL+ALT+F1 or F2, no CTRL+ALT+BACKSPACE, not even a CTRL+ALT+DELETE, nothing works but the ol' reset button.

I'd appreciate any advice that anyone has on how to make this thing work.

Thanks,

Luke

---

### Post by nutzmurphy on 2006-01-31
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=85888")

---

### Post by coredump25 on 2006-02-05
Do you mean that it hangs after it reboots and attempts to complete the instal?  

I had this problem and here is what I did:

Reboot with the recovery mode kernel.  Go into /etc/init.d and try disabling the powernowd.

Then when you reboot again, it will boot into the first console mode (text mode).
After you login, do a sudo apt-get update.  There will be an error and it will tell you to 
run dpkg with some parameters.  Follow those instructions, then do an apt-get update
again.

---

