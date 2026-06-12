---
title: "JDK on amd 64 with kubuntu"
date: 2006-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by bastiegast on 2006-02-13
Hi, Im trying to install sun's jdk on my ubuntu box, unfortunatly the install script wont work.. I start the installer: ./jdk-1_5_0_06-nb-5_0-linux.bin  , it extracts some files. after: Launching InstallShield Wizard........ I get the following error message:
The installer is unable to run in graphical mode. Try running the installer with           the -console or -silent flag.
So i run ./jdk-1_5_0_06-nb-5_0-linux.bin -console
After: Launching InstallShield Wizard........ again an error
The wizard cannot continue because of the following error: Invalid command line option: -console is not supported (1001) (403)
WARNING: could not delete temporary file /tmp/ismp001/7072742
WARNING: could not delete temporary file /tmp/ismp001/5525489
WARNING: could not delete temporary file /tmp/ismp001/5657365

Any suggestions?
(yes i tried sudo btw.)

---

### Post by oxpack on 2006-02-27
I downloaded and installed jre-1_5_0_06-linux-amd64.bin from sun and it worked with the one application I was trying to use which was JAlbum. I believe I tried the jdk with the application and it did not work.

---

