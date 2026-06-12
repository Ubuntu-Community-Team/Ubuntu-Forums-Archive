---
title: "Things quitting unexpectedly"
date: 2006-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by xmastree on 2006-02-23
I recently got a new motherboard, Asus K8V-MX with an Athlon 64 and 1GB Ram.
At first, I booted from my previous 5.04 installation, and it worked. Almost.
But things kept quitting. Desklets would die. Taskbar elements quit. Applications would suddenly quit.

So, I started over with a fresh disk and installed Breezy. I didn't do too much with it as my net connection wasn't so good last night.

This morning, whilst checking my email, the clock applet quit unexpectedly.

That **never** happened with my previous setup (Athlon 2400/Asus/52MB).

I'm not running the 64 bit distro, just the regular 386 version. Should I run the K7 kernel with this chip?

Edit: Update, I just lost everything apart from the trashcan in my lower task bar...

---

### Post by bernardfrancois on 2006-02-23
The computer I use most of the time at school also has a similar problem. Some days it will be logging me out (from KDE in FC4) and closing my applications (especially emacs, which is the application I use the most over there).

The error hasn't been identified yet, and I dunno if they solved it already or not.

Probably there's some hardware error. First they thought someone was bugging me and logging on to my computer with ssh and killing my login-session and my programs, but that turned out to be unlikely (since later it turned out that the same machine also had problems in windows).

---

### Post by xmastree on 2006-02-23
I think I may have found the problem. Faulty memory.
I ran the memtest option at boot and left it running. Came back later and there were errors, all at the upper end of the memory range (I have 2x512MB).
[ATTACH]6393[/ATTACH]
I swapped them over, and re ran it. This time the errors were all below 500MB.

I removed the suspect one and it passed the memtest. I'll see if it continues to work now.

---

### Post by xmastree on 2006-02-24
Update. Since then it's been fine. Not one problem. :-D
So, Bernard, run memtest (it  should be there in your Grub menu) and see if you end up with a screen like the one I posted above.

---

