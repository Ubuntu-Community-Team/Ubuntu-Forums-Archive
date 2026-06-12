---
title: "Google earth"
date: 2007-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by rajeev1204 on 2007-04-15
Hi

Does anyone have google earth installed on 64 bit? 

Iam not able to on feisty beta .complains about some pango modules


any help please




regards
rajeev

---

### Post by dabl on 2007-04-15
Yep -- runs great here.  Intel Core 2 Extreme, Intel D975XBX main board, Nvidia GeF 7900GS graphics, Ubuntu Feisty Beta.  I downloaded the installer for Debian systems and followed the instructions -- no problems, didn't see any errors whatsoever. I did that a week ago today, so I think it was still 2.6.20-14 kernel.

---

### Post by rajeev1204 on 2007-04-15
where did u get the debian installer from ? 

The site only has a .bin format for linux

---

### Post by John.Michael.Kane on 2007-04-15
You can get it here. [http://medibuntu.sos-sts.com/packages.php](http://medibuntu.sos-sts.com/packages.php)

---

### Post by rajeev1204 on 2007-04-15
HI

thanks guys . actually i had a 32 bit library missing .  ia32 libs gtk 

I installed direct from bin file 

Also plissken , is that medibuntu thing similar to automatix?

---

### Post by dabl on 2007-04-15
Right -- medibuntu is the source.

Raj, you need to add medibuntu to your apt source list. Follow the steps here and you'll be set:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

:)

---

### Post by John.Michael.Kane on 2007-04-15
> **rajeev1204 said:**
> HI

thanks guys . actually i had a 32 bit library missing .  ia32 libs gtk 

I installed direct from bin file 

Also plissken , is that medibuntu thing similar to automatix?

From what i can tell It does not depend on it. Seem to be just a repo that's used to make patent encumbered  programs available for users via synaptic

---

### Post by mac.ryan on 2007-04-21
I have very recently converted from Edgy32 to Feisty64. I am very satisfied of how the 64 architecture is running and have no major problems with it.

The only thing I can't get past of is installing Google Earth.

I am trying to install via the bin file downloaded from google. I have the 32bits libs I read about in this and other threads (ia32libs gtk/kde/kdl), yet when I try to launch the program I get:

```
Segmentation fault (core dumped)
```

Googleing for it gives very few hits, none of them being conclusive.

PS: I know - as an "extrema ratio" - I might try the 3rd party repo... but i would really love to understand what this problem is, and try to fix it, if I can. Learning something new is cooler than work around an obstacle...

Many thanks in advance! :)

---

### Post by mac.ryan on 2007-04-22
I finally gave medibuntu a try, and after having uninstalled GE from the /opt directory manually, I used the repo to install it again but...

**it gives me the same error code: _Segmentation fault (core dumped)_ !** (actually, when I click from the menu nothing happens, but if I launch it via the CLI, I get the exit code...)

:( :( :(

Oh, mighty community of 64bit worshippers... give me some ideas on what to try next!

---

### Post by rajeev1204 on 2007-04-23
what graphics card do u have ?

---

### Post by mac.ryan on 2007-04-23
> **rajeev1204 said:**
> what graphics card do u have ?

Hello rajeev, and thanks for helping out with this. I have a 512MB DDR3 nVidia GeForce Go 7950 GTX, for which I installed the drivers from here:

[http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html)

I run on a Dell XPS M1710 Core 2 Duo Processor T7400 (2.16 GHz, 4 MB L2 cache, 667 MHz FSB).

---

### Post by BIGtrouble77 on 2007-04-23
Mac,
Why didn't you install the drivers through the repos?  It's much better to do it that way because x won't break during a kernel update.  97.55 is the version in the Repos, btw.  Are you sure opengl is even working properly?

---

### Post by mac.ryan on 2007-04-23
> **BIGtrouble77 said:**
> Mac,
Why didn't you install the drivers through the repos?  It's much better to do it that way because x won't break during a kernel update.  97.55 is the version in the Repos, btw.  Are you sure opengl is even working properly?

it was not a very much reflected decision: I simply couldn't browse comfortably at 640x480 in a monitor designed for 1900x1200... I wanted to fix this immediately after installation, and - given that Feisty didn't recognised the card nor the resolution, while Edgy did, I imagined it was a 64bit issue and went on nVidia website...

I would have no problem in swapping to repos now. The only thing that confuses me - though - is that I believe the repo drivers are the "nvidia-glx-new" package, but if this is the case, the package IS already installed! :-/

---

### Post by pcraven on 2007-04-25
I tried installing Google Earth via the .bin file on Edgy 64-bit. I get the following:

./googleearth-bin: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory

---

### Post by kry10 on 2007-04-28
> **pcraven said:**
> I tried installing Google Earth via the .bin file on Edgy 64-bit. I get the following:

./googleearth-bin: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory

Try installing ia32-libs-gtk. That fixed the error for me.

---

### Post by mac.ryan on 2007-04-30
The issue is still on: anybody having advices for me? :)

> **mac.ryan said:**
> I have very recently converted from Edgy32 to Feisty64. I am very satisfied of how the 64 architecture is running and have no major problems with it.

The only thing I can't get past of is installing Google Earth.

I am trying to install via the bin file downloaded from google. I have the 32bits libs I read about in this and other threads (ia32libs gtk/kde/kdl), yet when I try to launch the program I get:

```
Segmentation fault (core dumped)
```Googleing for it gives very few hits, none of them being conclusive.

PS: I know - as an "extrema ratio" - I might try the 3rd party repo... but i would really love to understand what this problem is, and try to fix it, if I can. Learning something new is cooler than work around an obstacle...

Many thanks in advance! :)

---

### Post by stchman on 2007-05-02
I must say that you should install Google Earth using sudo.  Otherwise it puts it in your /home/<your_home> folder.  If you sudo the install it puts it in /opt/google-earth so that all accounts can use Google Earth.  you can then make a symbolic link to the launch script in that folder on your desktop.

---

### Post by stchman on 2007-05-02
> **mac.ryan said:**
> Hello rajeev, and thanks for helping out with this. I have a 512MB DDR3 nVidia GeForce Go 7950 GTX, for which I installed the drivers from here:

[http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html)

I run on a Dell XPS M1710 Core 2 Duo Processor T7400 (2.16 GHz, 4 MB L2 cache, 667 MHz FSB).

Can't install the driver that way.

Install Envy from [www.albertomilone.com](www.albertomilone.com), download the .deb for your distro.

Once you do that boot the PC into recovery mode and type envy -t

Completely remove the nvidia driver you tried to install (I believe option 6).  Then install the nvidia driver (option1).  You are set then.  Simple, plainless process.  This installs the latest drivers 97.55.

---

### Post by stchman on 2007-05-02
> **BIGtrouble77 said:**
> Mac,
Why didn't you install the drivers through the repos?  It's much better to do it that way because x won't break during a kernel update.  97.55 is the version in the Repos, btw.  Are you sure opengl is even working properly?

With Google Earth you will know if opengl is functioning properly.  Without hardware acceleration it will be very jerky.  He need to use Envy.

---

