---
title: "After install then... Udate? Nvida for ATI?"
date: 2009-03-28
forum: x86 64-bit Users
---

### Post by Gekkido on 2009-03-28
Ok.. This is what the problem was.  I kept reinstalling ubuntu, and running the update.  I have it on automatic login as well.  So on with the explanation.  This is my first time using Ubuntu, and I had to reinstall like 4 times before I realized that the Updater was wanting to download Nvidia Xorg drivers for ATI.

I didn't realize this after about the fourth re-install when I finally caught it.  Unfortunately it was too late on that time around.  So my silly self decided to turn around and re-install again.  I unchecked the three of them, and it actually got to Ubuntu after restarting, after the reinstall.

Well what kept happening I was getting a blank screen after booting to the updated kernal, or whatever it is called.

Now what I am asking....  Am I correct right here?

Basic System Specs: HP Laptop DV5 1250US

AMD Turion X2 Ultra
ATI 3450HD 512MB
4GB RAM


Oh... One more thing... how do I get to compizconfig?  It's not under System\Preferences.. =/

---

### Post by Slim Odds on 2009-03-28
You have an ATI card, so you don't need anything nvidia

It's either or.

You can't get compiz working until you get a 3D video driver working.

---

### Post by Gekkido on 2009-03-28
I got the right driver(s) though.  Just did the compiz download.

Now I need to get those three Nvidia updates to go away.
Any suggestion on how to do that?

---

### Post by 3startuna on 2009-03-28
This was happening with my computer as well. In my case 
what worked for me was to ctrl+alt+ F1 during startup
then 
sudo get-upgrade ubuntu-desktop

once it was done it worked fine. Not sure if this will work for you as well but its worth trying.

Also dude why do you have your system set to auto log on.

---

### Post by Gekkido on 2009-03-28
> **3startuna said:**
> Also dude why do you have your system set to auto log on.

I'm the only one who will ever be using my laptop. =/  Besides... I can always turn it off if anyone else will ever end up using it.

Don't even know why I put that in the post. X.x

---

### Post by bford16 on 2009-03-29
> **Gekkido said:**
> Ok.. This is what the problem was.  I kept reinstalling ubuntu, and running the update.  I have it on automatic login as well.  So on with the explanation.  This is my first time using Ubuntu, and I had to reinstall like 4 times before I realized that the Updater was wanting to download Nvidia Xorg drivers for ATI.

I didn't realize this after about the fourth re-install when I finally caught it.  Unfortunately it was too late on that time around.  So my silly self decided to turn around and re-install again.  I unchecked the three of them, and it actually got to Ubuntu after restarting, after the reinstall.

Well what kept happening I was getting a blank screen after booting to the updated kernal, or whatever it is called.

Now what I am asking....  Am I correct right here?

Basic System Specs: HP Laptop DV5 1250US

AMD Turion X2 Ultra
ATI 3450HD 512MB
4GB RAM


Oh... One more thing... how do I get to compizconfig?  It's not under System\Preferences.. =/When I installed Linux on my new desktop (with a Radeon 3200 HD integrated video card), I also got the black screen.  I rebooted in recovery mode, dropped to a command prompt, and ran```
sudo apt-get install xorg-driver-fglrx dkms
```Then I ran "sudo aticonfig --initial," and proceeded to boot normally.  Problem solved. Now if I could just get decent video performance with compositing enabled...

---

### Post by Gekkido on 2009-03-30
Thanks.. I think I'll give this a try.  Sorry for slow reply.  Been away for a couple of days.

---

### Post by Gekkido on 2009-03-30
sudo apt-get install xorg-driver-fglrx dkms  (FAIL)

This did not work.  Now all my screen does is turn off.  It's not just a blank screen... monitor shuts its self off. My max resolution for my laptop is 1280X800... then again I don't even hear the Ubuntu drums, and stuff playing either.  So it can't be that it is just over the resolution.

This is after another update I did right here.  Even after I left out the Nvidia drivers, and other stuff to deal with Nvidia.

Going to try to boot to Kubuntu see if it goes any better.. Probably not, but going to try.. installing it right now.  (FAIL)

---

### Post by hellblade on 2009-03-31
First of all try running:
```
sudo aptitude update
sudo aptitude upgrade
```
to make sure you have the latest package versions available.

Then reset you X configuration to the default values using:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure -p high xserver-xorg

```
and accepting the defaults when asked.

Then try starting the X server again to check if everything works ok using vesa or whatever is the fallback driver.
```
sudo /etc/init.d/gdm restart
```

If that works use the "Hardware Drivers" Ubuntu GUI to install fglrx. That should be located somewhere in the panel menus. Under KDE (what I use) it can be found under Applications > System.

Try it and let us know.

[I]
FYI you can find more information about why the xserver didn't start in /var/log/Xorg.0.log
To read that file in a console use:
```
less /var/log/Xorg.0.log
```
You can exit less by pressing Q.[/I]

---

### Post by Gekkido on 2009-04-01
Ok.  None of that really worked, but when the updates were installing I noticed two errors.  One was about some ISO image, and I don't really understand that, but I did see one that could easily be a bit of trouble.  Since I caught them this time around I was able to re-install them.

it was gnome-cups-manager.desktop and gtk-theme-selector.  Don't know if these would of done it, but heck.  I did however get the updated kernel to boot this time around after doing this.  (All cup files were just re-installed, and anything that resembled the gtk about the gnome desktop was re-installed as well.)

---

