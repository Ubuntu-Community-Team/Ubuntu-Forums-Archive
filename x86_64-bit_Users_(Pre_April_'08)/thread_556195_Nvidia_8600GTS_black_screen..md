---
title: "Nvidia 8600GTS black screen."
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Law506 on 2007-09-21
Alright,  followed other numerous links and downloaded the 64 bit linux driver from Nvidia.com and did the whole process of rcconf to turn off GDM and got into init 3.  Ran the setup and let it config my x file and everytime I start my computer (even before the driver install) the screen gets to the GRUB screen (dual booting XP and Ubuntu 7.04) and when i choose to go in to normal Ubuntu the screen blinks and is gone.  Recovery mode works fine, but without GDM on for now.

I have a Biostar TF7050-M2 AMD X2 64 6000+.  I got the network going on it and even the bluetooth going.  The onboard video works fine when 8600GTS is pulled out of the PCI-E slot.

I am still new to this and just curious to what can be done.  I dont know if I install the graphics driver without the card in if it would even work.  Or maybe there is some chipset driver I need?

Thanks Guys.

---

### Post by Law506 on 2007-09-21
Alright.  Ran envy, still no joy.  Manually did the updates for my system and then ran rcconf and turned off GDM and ran the install the Nvidia way.  Restarted X and bam, worked.  guess i was just missing updates or something.  Still cant get it off of 1024X768 though.. that is my next task. :guitar:

---

### Post by rh1zome on 2007-09-21
Law506, you've probably Googled this by now, but if not, you might want to grab the nvidia-settings utility using apt-get or Synaptic  (it's an official Ubuntu package). It worked great for my 7600GS card running in dual-head mode and gave me plenty of settings to tweak including being able to independently adjust the resolution of my two monitors.

---

### Post by dabl on 2007-09-21
> **Law506 said:**
> 
 Still cant get it off of 1024X768 though.. that is my next task. :guitar:
```

sudo nvidia-settings
```

Then set the resolution and refresh the way you want, and click the "Save to X Configuration File" button, and choose "merge" and "save".

Now you've set the default!  :)

---

### Post by Law506 on 2007-09-21
Alright, got all of that. :)  Thanks for the support.

Now, another problem.  For some reason everytime I restart the X - Server freaks and it acts like I never did anything, the only way to get into Ubuntu is to reinstall the Nvidia driver in recovery mode and then using envy to restart X - Server.  

I read the error and it said that the Nvidia module kernal isnt matching the system or something.   Everytime I reinstall I let it build its own Kernal.  Which also every time I install it cannot find the previous Kernal it had built apparently.  I am going to google this some more, but if anyone has any related experience on what I might be doing wrong, I would appreciate it.

Thanks again.

---

### Post by Law506 on 2007-10-21
Just adding to this.

With the release of 7.10 I decided to try Ubuntu once again.

Downloaded the CD and ran it and it worked.  Installed the restricted driver and everything runs smooth as can be.  So if your having trouble with 7.04, i recommend upgrading to 7.10

However, when i go to install the nvidia driver i restart the computer and I get a screen saying that it can figure out what card or monitor I had.  I just got rid of the nvidia driver and everything was good.  So, yeah.

Take It easy.

---

### Post by Cappy on 2007-10-21
If you are installing the nvidia driver from the nvidia site you aren't supposed to do that - just use the one from the restricted driver - you don't have to do anything in Gutsy for the 8600/8800 anymore.

---

### Post by Law506 on 2007-10-22
If i install the nvidia settings program, will that cause any kind of conflict using the restricted driver???  I want to use my dual monitor capabilities and it crashed when I went to restart the system after activating the second monitor, but this was also with the nvidia driver installed from the website and the restricted.

---

### Post by Cappy on 2007-10-22
> **Law506 said:**
> If i install the nvidia settings program, will that cause any kind of conflict using the restricted driver???  I want to use my dual monitor capabilities and it crashed when I went to restart the system after activating the second monitor, but this was also with the nvidia driver installed from the website and the restricted.

You can't install the package "nvidia-settings" (which is only for nvidia-glx-legacy). Instead, it is included in the nvidia-glx package. Just type ```
gksudo nvidia-settings
``` to run it.

Also you may want to look at System-->Administration-->Screens and Graphics because you can configure a second screen there.

---

### Post by Law506 on 2007-10-22
awesome, Thanks :)

---

### Post by psycho5 on 2007-11-09
How to solve this problem suppose you're doing a fresh install with that video card? 

I posted my inquiry here: [http://ubuntuforums.org/showthread.php?t=607551](http://ubuntuforums.org/showthread.php?t=607551)

I've got the same problem except that I'm doing a fresh install. Can someone guide this noob please?

---

