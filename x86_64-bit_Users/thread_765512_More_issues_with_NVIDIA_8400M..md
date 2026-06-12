---
title: "More issues with NVIDIA 8400M."
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by Pandemic187 on 2008-04-24
Yes, I know many people have reported issues with this chipset, but I installed the final release of Hardy x86-64 today, so I thought I would start from scratch and see if I can get this thing working on my setup.

When I open my restricted drivers manager, I see a check under "Enable" for the NVIDIA driver, but for the status of the driver it says "NOT IN USE." I unchecked the driver, chose to disable it, closed out of the manager, and tried to re-enable it. It said I needed to reboot at that point, so I did. When I rebooted and opened the driver manager back up, the driver was once again enabled but not in use.

I'd like to be able to use Compiz but since I'm obviously having an issue with my graphics drivers, that isn't going to happen yet. What would be the best way to try to resolve this issue? I saw that there is an AMD64 driver on the NVIDIA site for my chipset, but I'm not sure if that will help or not.

---

### Post by Falcorian on 2008-04-24
I had the exact same problem, even including the restricted driver manager reporting it as enabled but not in use. I have a 8800 GTS though...

But, the drivers on their site worked fine for me. You just need the build-essentials package and it should work.

You'll also have to shut down X, so log into a terminal (ctrl+alt F1 for example), do a:

```
sudo /etc/init.d/gdm stop
```

Then a:

```
sudo sh NVIDIAPACKAGENAME.run
```

And you should be good. You may have to restart at that point, although trying this won't hurt:

```
sudo /etc/init.d/gdm start
```

---

### Post by kgr132 on 2008-04-24
Did the restricted driver manager download a new driver package? If not, did you apply all of the updates to Hardy first, before enabling the restricted driver? When I installed the x86-32 release candidate version on Tuesday, I had the same exact problem. The driver was enabled and the restricted driver manager kept saying a restart was required. I actually reinstalled Hardy, then applied _all_ of the updates before trying to enable the restricted driver. It worked out great that time. The latest driver was downloaded when I enabled it (that didn't happen the first time) and after a reboot all was well. Good luck.

---

### Post by Pandemic187 on 2008-04-24
> **kgr132 said:**
> Did the restricted driver manager download a new driver package? If not, did you apply all of the updates to Hardy first, before enabling the restricted driver? When I installed the x86-32 release candidate version on Tuesday, I had the same exact problem. The driver was enabled and the restricted driver manager kept saying a restart was required. I actually reinstalled Hardy, then applied _all_ of the updates before trying to enable the restricted driver. It worked out great that time. The latest driver was downloaded when I enabled it (that didn't happen the first time) and after a reboot all was well. Good luck.
No, the restricted driver manager did not install any new packages. As for updates - I'm not using a release candidate like you - I'm using the final release, which of course was just released today. As a result, there are no updates as of yet.

I haven't tried installing the driver in text mode yet. I'm studying for an exam tomorrow but I will try doing that, probably tomorrow and let you know if I have any luck.

And, a side note: Am I crazy, or does it look like my desktop is running in less than 32-bit color? Maybe the driver issue will fix that if it is in fact resolved, but obviously anything less than 32-bit color is unacceptable nowadays. The image I've linked to shows what I'm talking about:

[[IMG]http://img166.imageshack.us/img166/6854/screenshotgq7.th.png[/IMG]](http://img166.imageshack.us/my.php?image=screenshotgq7.png)

Does that not look right, or is it just me?

EDIT: Apparrently this image will look right if you're running 32-bit color. I thought that if I took a screenshot you would be able to see what it looks, but right now I'm looking at the screenshot I took on Vista and it doesn't look weird like it does on Ubuntu. But I believe that Ubuntu is either running in 16-bit or 24-bit color for me. It's definitely not 32-bit.

---

### Post by Pandemic187 on 2008-04-24
Falcorian,

Can you make a suggestion as to which driver I should install? I tried to install [this]("http://www.nvidia.com/object/linux_display_amd64_173.08.html") driver and got a bunch of errors when I tried to install it in the way you have instructed.

---

### Post by Melk79 on 2008-04-24
This is exactly where I am at.  Same Nvidia and 64bit OS.  Same desktop image too... you can also see this effect at the Ubuntu login screen.

When I installed xubuntu 7.10 on an old laptop, I had this trouble and changed the display resolution in the xconf.org file.  On 8.04, this file just shows 'configured monitor'.

I'll post back if I can figure it out, please do the same if you find out.

Thanks.

---

### Post by vitalik on 2008-04-25
Same problem here with Nvidia 8600M GT.
Does Envy works with 64bit, did anybody gave it a try?

---

### Post by kavon89 on 2008-04-25
> **Falcorian said:**
> I had the exact same problem, even including the restricted driver manager reporting it as enabled but not in use. I have a 8800 GTS though...

But, the drivers on their site worked fine for me. You just need the build-essentials package and it should work.

You'll also have to shut down X, so log into a terminal (ctrl+alt F1 for example), do a:

```
sudo /etc/init.d/gdm stop
```

Then a:

```
sudo sh NVIDIAPACKAGENAME.run
```

And you should be good. You may have to restart at that point, although trying this won't hurt:

```
sudo /etc/init.d/gdm start
```

I did exactly that and I was smooth sailing and excited to try some games under wine with sucessful glxgears tests, but I needed to reboot and after that everything broke. I'm having similar problems and I also happen to have a card which shares the same chip as the 8400M, but from what I've seen on the forums it's more widespread than our specific chip.

nvidia-xconfig doesn't seem to do anything, I've tried uninstalling, reinstalling.

Restricting 'nv' and 'nvidia' got me some visual effects and the ability to open the Nvidia control panel, but I'm still locked into some weird 640x480 but not quite, like 5 pixels off resolution right now. :(

---

### Post by Falcorian on 2008-04-25
> **Pandemic187 said:**
> Falcorian,

Can you make a suggestion as to which driver I should install? I tried to install [this]("http://www.nvidia.com/object/linux_display_amd64_173.08.html") driver and got a bunch of errors when I tried to install it in the way you have instructed.

That's what I'm running... What errors are you getting?

---

### Post by KryoMouse on 2008-04-25
I've found that trying to install a new driver results in the nVidia text installer complaining about GCC 4.2, which I've tried to work around to no avail :/

---

### Post by jespdj on 2008-04-25
I had something similar (restricted drivers manager shows the driver, but not in use) on my XPS M1530 (with 8600M GT). I'm using 64-bit Ubuntu 8.04.

It seems to have corrected itself automatically after a reboot.

So reboot, and have a look again at what the restricted driver manager says. It's supposed to download the nVidia driver automatically.

On my system it wasn't necessary to use Envy or install drivers manually.

---

### Post by Melk79 on 2008-04-25
> **jespdj said:**
> I had something similar (restricted drivers manager shows the driver, but not in use) on my XPS M1530 (with 8600M GT). I'm using 64-bit Ubuntu 8.04.

It seems to have corrected itself automatically after a reboot.

So reboot, and have a look again at what the restricted driver manager says. It's supposed to download the nVidia driver automatically.

On my system it wasn't necessary to use Envy or install drivers manually.

That's great news.  I've seemed to have regressed on my front.  Originally, I had the Nvidia "enabled" on the hardware drivers screen with no status as others have mentioned.  Subsequent to that and after a reboot or two, now the "enabled" is no longer checked.  I've tried to install the Nvidia driver manually and ran into some errors about needing libc installed and that my kernel wasn't precompiled or something.  Was there anything from the package manager that you pulled in or did the reboot just do it?  Thanks.

Did we try this [link ]("http://www.psychocats.net/ubuntu/nvidia")from the sticky at the top of this forum?  I'm not at my CPU now to check if it works.

---

### Post by Pandemic187 on 2008-04-25
> **Melk79 said:**
> ...I've tried to install the Nvidia driver manually and ran into some errors about needing libc installed and that my kernel wasn't precompiled or something.  Was there anything from the package manager that you pulled in or did the reboot just do it?  Thanks.
Falcorian,

The problem I'm encountering seems to be the exact same one that Melk is describing. I got the message about not having the right kernel, then saying something about not having libc.

Melk, now I'm curious: What sort of laptop are you using? Mine is an HP dv6700t.

> **Melk79 said:**
> Did we try this [link ]("http://www.psychocats.net/ubuntu/nvidia")from the sticky at the top of this forum?  I'm not at my CPU now to check if it works.
EDIT: Nope, this doesn't really do anything. It's supposed to download a new driver, but it doesn't.

---

### Post by Melk79 on 2008-04-25
> **Pandemic187 said:**
> 
Melk, now I'm curious: What sort of laptop are you using? Mine is an HP dv6700t.

Yup, HP dv6700t Special Edition.  (Just updated signature too-- makes more sense).

---

### Post by Melk79 on 2008-04-25
The sticky link worked for me!

Summary:
After fresh install of hardy, I noticed the Nvidia driver showed enabled but not in use.  I read around.  Installed Nvidia Settings and Config tools from Synaptic Package Manager.  They wouldn't work due to driver missing.  Downloaded 64-bit Linux driver from Nvidia.  Tried to install, but ran into errors previously mentioned.  Read sticky link at work today.  Came home, opened Hardware Drivers manager and clicked enable for Nvidia.  Ubuntu located 1 package and installed.  After reboot, all is well.  Now time for some eye candy...

---

### Post by jespdj on 2008-04-25
I've discovered this:

You have to run
```
sudo apt-get update
```
and then look in the Restricted Drivers Manager (System / Administration / Hardware Drivers) and enable the driver there - then it will download and install the driver.

---

### Post by vitalik on 2008-04-25
sudo apt-get install envyng-gtk

sudo envyng -t

and choose the option that apply to your card

---

### Post by Pandemic187 on 2008-04-25
Luckily, I've managed to fix the problem the easy way. Melk, I suggest you do this if you're still having problems.

I can't guarantee this is what fixed it, but such seems to be the case. I opened the Synaptic Package Manager, went to Settings>Repositories, went to the Third-Party Software tab, and enabled both "partner" repositories. Interestingly, after reloading my repositories, closing Synaptic, and going back into my restricted drivers manager, the NVIDIA driver was no longer enabled. I checked "Enable," and this time it downloaded a new driver. After rebooting, all was well.

---

### Post by emeraldknight1977 on 2008-05-21
I had the same problem with the 8400GS and all I had to do was try and start Compiz and it downloaded the drivers.

P.C. Moxley

---

### Post by Muni Beduhin on 2008-05-22
Pandemic187, you rock! This worked great on one of my friend's screaming demon of a new laptop. Super easy and extremely effective.

---

### Post by scottuss on 2008-05-22
I have that chipset and everything worked fine for me straight "out of the box" on both beta and LTS... strange

---

