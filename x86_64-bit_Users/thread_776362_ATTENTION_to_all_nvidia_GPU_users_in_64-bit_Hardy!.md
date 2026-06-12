---
title: "ATTENTION to all nvidia GPU users in 64-bit Hardy!"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by olmari on 2008-04-30
I couldn't install "nvidia" driver at all until I also installed ia32-libs and its depencies... No matter did I tried just with Ubuntu restricted drivers system or Envy, allways failure and no easy way to reverting into "nv" driver...

For an moment I spotted while trying to uninstall an failed nvidia driver installation that it complained something about /usr/lib32/libgl.0 or similar missing and aborting... Then I figured out to (again) completely reinstall Ubuntu and install ia32-libs first thing and that was it, Envyng worked like a charm and now using nvidia drivers :)

So this is an bug but I can't know is it where exactly... I mean is it nvidia trying to use something that isn't there (but yet it isn't no depency) or Ubuntus/Linuxes changed 32-bit compatibility stuff?

EDIT: Reason I suspected this "32-bit compatibility layer" as failurepoint was taht there is no /usr/lib32 directory when not instaleld ia32-libs, but there are after installing it.

---

### Post by Sef on 2008-04-30
My 8600 card worked just fine.  What card do you have?

I just installed the restricted drivers from Ubuntu.

---

### Post by Therion on 2008-04-30
> **Sef said:**
> I just installed the restricted drivers from Ubuntu.
Ditto.  8800GT here and zero problems.

---

### Post by olmari on 2008-04-30
I have 8600GT and 6600GT both (separate X screens)...

I installed my hardy with PXE-server and inet, so no live-CD... Can't figure out anything else that might have been affected... This config have worked many versions before too :)

So... Did you have "ia32-libs" isntalled or not by default after installation? Maybe there is some subtle diffirences between installation types (live-CD vs. netboot)

---

### Post by ruhtranayr on 2008-04-30
I have the GeForce 7100 GS and I had to install the latest beta driver (173.08) from the [Nvidia website]("http://www.nvidia.com/Download/Find.aspx?lang=en-us"). Worked like a charm.

---

### Post by Galban on 2008-04-30
GeForce 6200 here and lots of problems.Restricted drivers enabled (ver. 169.12), but no way to get Compiz to be other than NONE without a pop-up saying "Desktop effects could not be enabled".A "glxinfo" command only gives me "Illegal instruction" as an answer. I have been trying many things without success. What don't understand is why many others having Nvidia's GPU are saying here no problems to have Compiz running-up on Hardy.So far, no answers for this, not even in a thread that I did open about this. :(  :confused:

---

### Post by ruhtranayr on 2008-04-30
Galban did you try the latest BETA driver?

Find it here:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us]("http://www.nvidia.com/Download/Find.aspx?lang=en-us")

Make sure to disable restricted drivers and remove any older version you have installed:

#sh NVIDIA-Linux-x86_64-169.12-pkg2.run --uninstall

Good luck.

---

### Post by DandyDon on 2008-05-01
> **Galban said:**
> GeForce 6200 here and lots of problems.Restricted drivers enabled (ver. 169.12), but no way to get Compiz to be other than NONE without a pop-up saying "Desktop effects could not be enabled".A "glxinfo" command only gives me "Illegal instruction" as an answer. I have been trying many things without success. What don't understand is why many others having Nvidia's GPU are saying here no problems to have Compiz running-up on Hardy.So far, no answers for this, not even in a thread that I did open about this. :(  :confused:

Read the sticky from Reassuringly Offensive in the Multimedia and Video Forum. Pay particular attention to his instructions for getting all the libraries for the AMD64. Download them all again to make sure you have them. Some of yours my be corrupted or missing ( mine was). Just open Terminal and Copy/ Paste the scripts in. Remember, we are downloading over the internet, who knows how many server hops the files take. 

Go to EnvyNG site,follow instructions to remove the current drivers, again open Terminal and Copy/ Paste the scripts in. Download EnvyNG,it will install under Applications-System Tools. Run it. It will find the latest driver for your card, install it; and set up Nvidia X Server under System-Administrator. Use Nvidia X Server to check settings.

This is what worked for me.

---

### Post by olmari on 2008-05-01
It seems that for some reason the ia32-libs doesn't get installed with the hardy amd64 mini / netboot installer, but it does with live and server versions... Apaprently as kernel 2.6.24 did merge the 64 and 32-bit system (don't ask specifics, I don't know) the ia32-libs is "mandatory" package, but despite of that it doesn't seem to be actually depency of anything, but "anything" will just fail if it is not isntalled...

I hope I made any sense :-p

---

### Post by jim_24601 on 2008-05-01
Excellent! Thanks to you I now have accelerated graphics! I noticed the thing about failing to uninstall without lib32, found that it would uninstall if I created a dummy lib32 directory, and went on my way without making the connection.

I have a fresh Ubuntu64 Hardy install on a brand new computer (actually I'm using a beta because fakeraid5 support is broken in the release), and the ia32 libs were NOT installed by default. Seems there's a broken dependency somewhere.

---

### Post by Galban on 2008-05-01
THIS IS IN RESPONSE TO THE ANSWERS TO THE POST # 7 (thanks...any ways)

Just to let you know guys, that my AMD Athlon (1400) processor is not a 64 bit one, it's a 32. So for sure, I'm not using the 64 bit version of Hardy Heron. EnvyNG was unable to get working Compiz on my comp.And when I tried installing the driver from Nvidia directly and not the one on the repositories was not different on Compiz behavior that EnvyNg nor the repos one.All those ways only shows "Desktop effects could not be enabled" as soon as I try to pass from "None" to "Normal" or "Extra". Restricted drivers are up and running. Even the Nvidia's X Server Settings is up and no problem adjusting anything, for example "openGL settings" tab, no problems, but  again here, as soon as I tried to open "openGL/GLX Information" tab, signs that something is wrong appears, Nvidia's X Server Settings program just close not given any error message. Any hints?!!?!

---

### Post by Yellow Pasque on 2008-05-01
Are you sure you didn't accidentally download the 32-bit version of Nvidia's proprietary driver?

---

### Post by adi_8079 on 2008-05-01
No problems with my Quadro FX 570M. I've installed Hardy from the live CD then used EnvyNG to install the driver.

---

### Post by Galban on 2008-05-01
> Temüjin Re: ATTENTION to all nvidia GPU users in 64-bit Hardy!

--------------------------------------------------------------------------------
Are you sure you didn't accidentally download the 32-bit version of Nvidia's proprietary driver?  

I'm sorry if i'm confusing people posting a "32-bit hardware" problem in a "64-bit thread", but I repeat, I'm using a 32-bit processor, so no reasons to even try to use the 64-bit version of Nvidia's proprietary driver.

---

### Post by iSplicer on 2008-05-01
> **Sef said:**
> My 8600 card worked just fine.  What card do you have?

I just installed the restricted drivers from Ubuntu.

+1, Mine worked fine too, but thanks for the heads up anyway!

---

