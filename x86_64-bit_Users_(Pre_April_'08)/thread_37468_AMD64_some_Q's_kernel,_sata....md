---
title: "AMD64 some Q's: kernel, sata..."
date: 2005-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by IndieRockSteve on 2005-05-27
Lately my only ATA133 drive seems to be freezing my computer. I haven't tried the regular 32bit kernel to see if that solves the problem(can I just install the 32bit kernel and boot or do I have to repalce all the libraries, etc?). But when I access the drive sometimes the system will freeze. This is a direct relationship(ie it only happens when accessing that drive, so for now I don't have it mounted).

Also, are people using the generic 64bit kerle for their AMD64 chips or are they using the K8 kernel?

and finally, I have a SATA DVDRW(the plextor) and can't get it to burn dvd's with growisofs(works fine for cd's though!), anyone else have this problem? I don't know if its AMD64 related or not, but since my setup is an amd64 i figured I'd ask...


Thanks!

---

### Post by rsw on 2005-05-27
I don't know about your ide drive issues, sounds like a malfunctioning drive & I would test it in another system to rule out a hardware problem (could be a problem with the drive or the ide controller on your motherboard or pci card, whatever you're using).

As for the SATA cdrw, I believe you need a patch for the kernel for it? Not sure, google around and see what you can find about that.

---

### Post by ::DoGG:: on 2005-05-27
[QUOTE=IndieRockSteve]can I just install the 32bit kernel and boot or do I have to repalce all the libraries, etc?
[/QUOTE]

Well.. since amd64 release have a 64 bit kernel and 64 bit environment You probably have to reinstall to 32 bit release to test 32 bit kernel, but i don`t think it could be a problem. If i were You i would connect it somewhere else (as above :D ) and check the disc (bad sectros etc...) if everything is ok then full format the drive and try to mount again, if that wont help i would dig in the proper module usage and fstab parameters.

---

### Post by IndieRockSteve on 2005-05-31
gunna try that, though right now the drive's smart shows all as being ok.

thanks for the suggestions!

---

### Post by FluffyElmo on 2005-05-31
Check your drives manufacturer support site. They have bootable drive diagnostic disks that go a little deeper than the SMART status. This way you can be sure it's not the drive before modifying your data.

Also, you might want to try accessing the drive using the Ubuntu LiveCD. It will let you try to reproduce the problem with a 32bit kernel without a full reinstall.

---

### Post by IndieRockSteve on 2005-05-31
can't do the manufacturer apps, they require windows.

I'm gunna try moving the drive. but now I've got to solve the random freezing problem that the linux gods have deemed not important enough to write a log file for.

not much of a server upgrade at this point. at least its amazingly fast...

---

### Post by projectle on 2005-06-02
[QUOTE=][/QUOTE]
 Just grab a livecd like Knoppix and test with that. Then you do not need to take apart the computer if it is a kernel issue. I would still suggest that if the problem remains that you should try the drive in another computer, and then another drive in this one in order to verify.
As far as troubleshooting goes, you should always test something as extensively as possible in the enviroment that it is causing the problem in order to attempt to diagnose and rectify the problem. 
That being the case, you would rule out whether you are dealing with a configuration issue rather than dismantling and leaving two devices in a non-operational state.

---

