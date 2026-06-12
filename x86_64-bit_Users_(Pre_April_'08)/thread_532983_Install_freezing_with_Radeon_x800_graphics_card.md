---
title: "Install freezing with Radeon x800 graphics card"
date: 2007-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hyter on 2007-08-23
I'm installing Ubuntu 7.04 with a Radeon x800 graphics card.
I know for it to work I need to use the alternate CD to install, and I have been able to successfully install the 32-bit version.
When I tried to install the 64-bit version it freezes at ~75%.
The current operation is "Storing Language."

I have redownloaded, reinstalled, and the download as passed the checksum.

---

### Post by crjackson on 2007-08-23
I have the same video card (see my sig).  The LiveCD install works fine for me, I've done about 68 installs with it.  The only problem on my system is the splash screen (both live cd and after install).

For me (and many others) all I have to do is at the 1st menu level after booding the liveCD, hit F4 and change the resolution to 1024x768, then select the menu option to continue booting to the liveCD for Install.

Once installed, you have to boot into recovery mode, exit to desktop (for me anyway), then edit the grub.  There you will change the 2 instances of SPLASH to NOSPLASH.

That's it.  Give it a try and see if this will work for you.

---

### Post by Hyter on 2007-08-25
It still freezes during the install.

I'm going to try to download the normal disk and boot it live.

---

### Post by Kilz on 2007-08-25
> **Hyter said:**
> It still freezes during the install.

I'm going to try to download the normal disk and boot it live.

Make sure to check the md5sum of the iso before you burn it. To make sure you got a good image to burn. Sometimes errors happen during download.

---

### Post by Hyter on 2007-08-25
> **Hyter said:**
> ...and the download as passed the checksum.

Always do. :)

---

### Post by Hyter on 2007-09-08
> **crjackson said:**
> I have the same video card (see my sig).  The LiveCD install works fine for me, I've done about 68 installs with it.  The only problem on my system is the splash screen (both live cd and after install).

For me (and many others) all I have to do is at the 1st menu level after booding the liveCD, hit F4 and change the resolution to 1024x768, then select the menu option to continue booting to the liveCD for Install.

Once installed, you have to boot into recovery mode, exit to desktop (for me anyway), then edit the grub.  There you will change the 2 instances of SPLASH to NOSPLASH.

That's it.  Give it a try and see if this will work for you.

It works!
For some reason the alternate disk will not work, but a LiveCD install works perfect
I did have to go into recovery mode also and change SPLASH to NOSPLASH.

---

