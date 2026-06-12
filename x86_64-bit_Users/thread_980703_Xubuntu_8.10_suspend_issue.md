---
title: "Xubuntu 8.10 suspend issue"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by Strelock on 2008-11-13
Just did a fresh install of Xubuntu 8.10 and I have a strange issue with suspend: Laptop suspends fine but on resume it just starts up like it was turned of!

Does anyone experience the same? I'm not quite sure if it is to do with upgrade of Ubuntu 8.04->8.10 or fglrx to 8.10 :)

---

### Post by lunar cranium on 2008-11-13
i've noticed the suspend feature in kubuntu 8.10 varying greatly from ubuntu 8.04.  if i suspend to ram it comes right back up really quickly, however it does not prompt for password.  if i suspend to disk, when i resume grub loads up, but still not prompted for a password.  and it is extremely slow loading.

i looked at the acpi-support and the screen should lock.  i dunno.

right now i'm kind of wishing i hadn't done a full install of 8.10 and just stuck with 8.04.  i had it all set up the way i liked.

so you're not alone in your 8.10 suspend confusion.  :)

---

### Post by Strelock on 2008-11-13
Lunar,

that's not quite what I meant. Speed is another issue. When you resume from standby you get the system right where you left it - windows open and on the same place etc. 

I get a fresh boot like I have turned off the system! The led is blinking like in standby though....

---

### Post by lunar cranium on 2008-11-13
> **Strelock said:**
> Lunar,

that's not quite what I meant. Speed is another issue. When you resume from standby you get the system right where you left it - windows open and on the same place etc. 

I get a fresh boot like I have turned off the system! The led is blinking like in standby though....

yeah.  i get you.  just letting you know that you're not alone with suspend issues in 8.10.

---

### Post by Strelock on 2008-11-13
oh that's true :) suspend is one of the most frustrating things :))

```
btw switching to gnome and installing compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf firefox-gnome-support gdm-guest-session gnome-themes gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools libpulse-browse0 libpulsecore5  pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils ubuntu-gdm-themes usplash-theme-ubuntu seemed to fix the suspend issue :)
```

Hmm yesterday standby worked once but then failed again.... still searching why doest my pc restarts rahter than resumes...

---

### Post by ken78724 on 2008-11-13
can one using Ubuntu hardy 8.04.1 on 64 bit PC with a significant number of files involved, can a 8.10 install be done without partitioning. I know one must always back up prior work. but housekeeping wise, is a partition needed to use 8.10 beta.... at age 69, i'd just as soon to keep using what works than to get out front of the jones and have the latest if there's a lot of housekeeping one best do.

don't be upset if you see a new thread asking the same questions.

---

### Post by lunar cranium on 2008-11-13
read through this.  see what you think.  [http://wiki.archlinux.org/index.php/Pm-utils](http://wiki.archlinux.org/index.php/Pm-utils)

i'm understanding that pm-utils is being used instead of acpi for suspend and hibernate.

---

### Post by Strelock on 2008-11-14
Lunar, the heading in /etc/default/acpi-support gives a very good explanation when which package is used :)

---

### Post by Strelock on 2008-11-15
I think I've got it! I have VMWare server 2.0 with Windows XP64 bit inside. If it's running system restart instead of resume....

---

