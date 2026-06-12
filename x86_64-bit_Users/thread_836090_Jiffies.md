---
title: "Jiffies"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by accod on 2008-06-21
Hi all,

I've got a 64bit gutsy box running xen.  It used to crash a lot (once every few days) until I changed the time source to jiffies.  The box is used for mythtv and using jiffies everything is fine except lirc.  When I press a button on the remote, cpu usage goes to  100% and I have to wait for approx 15 seconds before the button action completes (eg move up one item in menu).  If I use the keyboard its instant.

The process hogging the cpu is xorg. I'm logged in as a user called myth (not root as shown below):

root      7142  0.7  1.4 101032 36332 tty7     Rs+  Jun20   7:39 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 

If I cat xen to current_clocksource lirc immediately starts working properly.

Any ideas?

Thanks.

---

### Post by pixel :-) on 2008-06-21
i think you will have beater luck there [http://ubuntuforums.org/forumdisplay.php?f=334]("http://ubuntuforums.org/forumdisplay.php?f=334")

---

### Post by accod on 2008-06-21
Ok thanks, I've started a thread there.

---

