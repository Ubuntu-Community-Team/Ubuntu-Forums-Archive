---
title: "OpenSUSE ATI Driver Questions"
date: 2009-01-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Universal344 on 2009-01-24
I am running openSUSE 11.1 on VirtualBox 2.0.4 OSE and I want to configure the drivers for my ATI Radeon 2600 HD XT.  I found this on opensuse.org for 10.3 and 11.0:

```

The easy way of installing the proprietary driver has the benefits of being easy and does not require that one recompile the kernel module when updating the kernel. Please keep in mind that many older ATI cards are supported very well by the standard free driver. If you have such a card, consider sticking with that driver.

Unfortunately, the version 8.41.7 of fglrx for 10.3 is not recommended by AMD for any non-HD cards, and is known to be broken on AGP 4th and 5th generation radeons (ie. the AGP x700, x1300, x1600, etc.)

Before using the drivers below, try running your 3D application using open source drivers: radeon.
[edit]
openSUSE 10.3 and openSUSE 11.0

You can use 1-click-install that will install the latest fgrlx version:

<install link> Installs newest available drivers.

    * Open a terminal and type "sudo aticonfig --initial". This will configure X to use the ATI driver.
    * Restart X window manager by pressing CTRL+ALT+BACKSPACE (Twice for 11.0 and later). It will take 3-20 seconds. Alternative, you can restart openSUSE.
    * Skip all steps below and start using openSUSE! 
```

Will this work for 11.1?

Otherwise they give instructions for the "repository way," below those:

```

 The repository way

This is for people who prefer not using 1-click install can do it the direct way and actually see a bit of what is happening.
[edit]
Prerequisites

    * Beeing able to use yast-package manager or zypper
    * Know which kernel you use (default, pae, ...), use 'uname -r' in a console 


Add ATI Repository

Choose the one corresponding to your openSUSE version: http://en.opensuse.org/Additional_YaST_Package_Repositories#ATI_Video_drivers and add it to your repository list

Installation

KERNEL is {pae, default, trace, debug}, the one corresponding to your running kernel

install: x11-video-fglrxG01, ati-fglrxG01-kmp-KERNEL


Restart and run 'sax2 -r -m 0=fglrx' or whatever you like to setup the new driver configuration


```

First of all I don't understand the step, "KERNEL is {pae, default, trace, debug}, the one corresponding to your running kernel."

Secondly when it tells me to "install: x11-video-fglrxG01, ati-fglrxG01-kmp-KERNEL," can I do that through YaST?

Thanks for any help you can provide.

EDIT: The how-to by Vince4Amy did not work, it said there was error during installation.

---

### Post by Antman on 2009-01-25
Since openSUSE is running in a VirtualBox session, it will use the video emulator drivers contained within - installing the ATI drivers within the openSUSE guest will not work.

---

### Post by Vince4Amy on 2009-01-26
Just install the VM Additions and everything should run the way you expect. You won't be able to take full advantage of your GPU but it does support 3d now so you should get some performace. 

As Antman said, you don't need to install the ATI drivers on the guest.

---

