---
title: "ATI Driver 8.42.3 Screen issue"
date: 2007-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by hackount on 2007-11-29
Hi everyone,
i'm having trouble with the Ati driver 8.42.3, which seems to not recognize my monitor (Proview570). Here's what i did in particular:

i followed this guide (it's in italian but you should understand by the commands)

[http://divilinux.wordpress.com/2007/10/24/guida-facile-allinstallazione-driver-ati-fglrx-con-supporto-aiglx/](http://divilinux.wordpress.com/2007/10/24/guida-facile-allinstallazione-driver-ati-fglrx-con-supporto-aiglx/)

and succesfully installed the new driver for my 64 bit system (wooh-ooh.....), all good until i reboot.
Every time when trying to load X he doesn't recognize the monitor (vertical stripes all over the screen) and turns into safe mode, where he asks me to manually configure screen and video driver, which is automatically set to vesa...
once i set the right monitor and video card i can login but the proprietary drivers are unselected, so,,,i enable them again and reboot to start swearing again...

these are my pc spec. / P4 64 bit; ATI Radeon X800XL; Proview 570 monitor

---

### Post by viking777 on 2007-11-29
As far as I can see that how to that you used didn't mention using aticonfig after installing the new driver, you might like to try that.

```
aticonfig --initial
```

if it complains that xorg.conf already exists (or something like that) use 

```
aticonfig --initial --force
```

Normally I would say to make sure you have a backup copy of xorg.conf first, but as yours doesn't work it probably doesn't matter much!

---

### Post by hackount on 2007-11-29
thnx for replying, i've tried that and this is what i got back

hackount@anubi-desktop:~$ aticonfig --initial --force
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

what does "bad file descriptor" means?

---

### Post by hackount on 2007-11-29
ah never mind, i forgot to add sudo :D 
i'm going to reboot...if i don't get back in five minutes...you know what to do

---

### Post by hackount on 2007-11-29
ok now it works, i can login normally and see the enabled restricted drivers...BUT: is it correct that when i type in the terminal "fglrxinfo" the lines i get are

display: :0.0  screen: 0
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.0.1

it doesn't seem to be the right thing that should appear...

---

### Post by Jouke74 on 2007-11-29
Did you have XGL server installed before?

---

### Post by hackount on 2007-11-30
i just installed it before checking replies here in my post :D now everything seems to work but it is damn slow even if i installed accelerated graphics and all the stuff...any idea about what could be the trouble?

---

### Post by crjackson on 2007-11-30
Well, unless fglrxinfo indicates something different than what you posted earlier, I wouldn't expect to see any speed, as you are using the mesa drivers still...

---

