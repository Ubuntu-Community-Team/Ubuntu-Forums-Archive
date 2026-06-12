---
title: "World of Warcraft and Skype - Bad Sound"
date: 2014-02-05
forum: Wine
---

### Post by Arch_Nemesis on 2014-02-05
Ok, so I've noticed a couple of things here...  Mainly, whenever I attempt to run Skype and World of Warcraft at the same time, I get issues with sound coming from one or the other program.  Now, I've done all kinds of searching, to see if I can get this solved on my own, and if someone can offer me a link to a "How-To" then that would be great.  However, where I've checked so far doesn't seem to have the right info, or I am searching for the wrong things.

TL;DR -- Skip to Bottom

[http://www.wowwiki.com/Wine_troubleshooting](http://www.wowwiki.com/Wine_troubleshooting)

I've gone there, and if you go down to the "Audio" section of the troubleshooting guide, there is a spot that mentions that there are issues with running Voice Chat programs and world of Warcraft at the same time.  Then it references a section that no longer exists inside the troubleshooting guide.  Either that, or I've scrolled over the guide at least 10 times now.

Also, whenever I open up a terminal and I run the command "winecfg" (without Quotes), I get back the actual winecfg menu, but something else pops up in the terminal that seems like some form of error.  That "Error" reads as...

p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory


Now, again... It still opens the Wine Configuration Menus, but under the Audio Section, when I am referenced by the wowwiki troubleshooting guide, it says I should be able to "Deselect" or "Select" certain drivers?  I am not able to do so... Under "Driver Diagnostics" it lists "Selected Driver: winealsa.drv", which I am assuming means I am using the ALSA Drivers for my sound, but it gives me no option anywhere to use any OSS drivers.  I'm again assuming that my system is not using any OSS drivers, hence the reason why it is not available.

Another thing to note, is that I am using a RealTek Sound Card, but the actual driver is listed as an HDA Intel ALC889 Digital and HDA Intel ALC889 Analog.  Now, those are the options for the "Output" and "Input" for both my speakers and my mic under Wine, and again through the research I've done, those sound like the proper drivers or hardware names that should be there for Realtek devices.

TL;DR --

Sound Card issues, causing my sound to become scratchy, or non-existant, while running World of Warcraft in Wine whenever I run a Voice Chat Program alongside it.

---

