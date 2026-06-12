---
title: "Help Plz"
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by fatrabbit5 on 2006-05-01
I just built a new pc with a amd athlon 64 bit 3000+ with the asus x serires 1 gig ram and a 128 ati graphics card and once i installed ubuntu it will load the login gui but would not show the desktop gui just a brown wallpaper anybody can help PLZ!!!!](*,)

---

### Post by VoiceOvGod on 2006-05-01
Sounds to me like something didn't load up properly.

If you have access to the terminal, you could try apt-get for your desktop (default is ubuntu)

---

### Post by Jason_25 on 2006-05-01
I have a feeling you have a video driver problem.  Logout, ctrl-alt-f1, login, ```

sudo dpkg-reconfigure xserver-xorg

```
Choose relevant options, then when it comes to the driver, choose vesa, then finish.  Now to restart GDM
```

sudo /etc/init.d/gdm restart

```

---

### Post by fatrabbit5 on 2006-05-08
:eek: I'm pretty new with Ubuntu so i was wondering i log out and once i log out I enter a command line or something because I havent tried it yet I just wanted to make sure what Im going to do this correct.:eek:

---

