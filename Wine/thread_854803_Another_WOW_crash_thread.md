---
title: "Another WOW crash thread"
date: 2008-07-09
forum: Wine
---

### Post by Cclips on 2008-07-09
So here is the problem, I've gotten to the login screen which functions perfectly (hooray), Get character selection and all that jazz, but it freezes once the loading is done. I've tried it in the virtual desktop, but it locks the entire system regardless.

I've added the openGl tag into the wtf.config with no results, and all the rest of the prescribed config adjustments, I've run WINECFG before, so that is working fine. I've copied the install from a windows system, so the install should be fine. 

I've tried disabling the desktop enhancements to no avail, I'm a bit stumped as to what to try next.

Ubuntu 8.04
WINE 1.1
WOW basic (no crusade) latest edition.
I can't get a terminal reading as it locks the entire system.
Memory test ran fine.

Hardware is a Dell 1420n, X3100 integrated graphics ( I know, I know). Core 2, 2 gb Ram, etc etc.



Any help is greatly appreciated.

FYI for those who can't even get the title screen to load, try changing the default resolution in the wtf.config to your native resolution. (I ran into that problem when copying it from my windows system).

---

### Post by thisismalhotra on 2008-07-10
I am sure you have done registry edit, if not do that.

Than try:-

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by Cclips on 2008-07-10
I've looked through the troubleshooting page already, and most of those fixes aren't applicable as I haven't even gotten in game yet. I've gotten the DLLs already, and tried both the openGL and d3d video settings edit of the wtf.config. 

SO, any ideas?

---

### Post by Cclips on 2008-07-10
No ideas from anyone?

---

### Post by thisismalhotra on 2008-07-11
**From Troubleshooting page**

ATI enter game world crash

For users with an ATI video card: certain cards have trouble rendering games and video in opengl using current flgrx drivers which will cause your computer to hard locks when you attempt to enter a domain. This error will occur just after character creation/selection, as the game environment is loading, or possibly after a short period of play. In order to fix this error, add the following three lines of code to your xorg.conf file in the ATI device section:

    *

       Option "Capabilities" "0x00000800"
       Option "UseFastTLS" "off"
       Option "KernelModuleParm" "locked-userpages=0"

      You edit the file by doing this command:

       gksudo gedit /etc/X11/xorg.conf

      The section should look something similar to this after editing:

       Section "Device"
         Identifier  "aticonfig-Device[0]"
         Driver      "fglrx"
         Option       "Capabilities" "0x00000800"
         Option       "UseFastTLS" "off"
         Option       "KernelModuleParm" "locked-userpages=0"
       EndSection

---

### Post by Cclips on 2008-07-11
> **thisismalhotra said:**
> **From Troubleshooting page**

ATI enter game world crash

For users with an ATI video card: certain cards have trouble rendering games and video in opengl using current flgrx drivers which will cause your computer to hard locks when you attempt to enter a domain. This error will occur just after character creation/selection, as the game environment is loading, or possibly after a short period of play. In order to fix this error, add the following three lines of code to your xorg.conf file in the ATI device section:

    *

       Option "Capabilities" "0x00000800"
       Option "UseFastTLS" "off"
       Option "KernelModuleParm" "locked-userpages=0"

      You edit the file by doing this command:

       gksudo gedit /etc/X11/xorg.conf

      The section should look something similar to this after editing:

       Section "Device"
         Identifier  "aticonfig-Device[0]"
         Driver      "fglrx"
         Option       "Capabilities" "0x00000800"
         Option       "UseFastTLS" "off"
         Option       "KernelModuleParm" "locked-userpages=0"
       EndSection

I don't have an ATI card, but I suppose it is worth a shot anyways.

---

