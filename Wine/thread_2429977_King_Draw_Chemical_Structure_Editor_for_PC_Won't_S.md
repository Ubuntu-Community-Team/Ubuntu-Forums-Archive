---
title: "King Draw Chemical Structure Editor for PC Won't Start"
date: 2019-10-25
forum: Wine
---

### Post by sduverge on 2019-10-25
Hello!

I am trying to install this software on my Lubuntu 19.10 fresh install through wine [http://kingdraw.cn/en/index.html](http://kingdraw.cn/en/index.html)
Currently I use the APK on my phone, but I want it on my laptop to teach.
Installation process has two occurrences, one is to install NetFrameworks, then King Draw, and that tries to install King Draw on the Desktop as in display all program files right on the Desktop.

After install program won't run, even going into program file folder and directly choosing the .exe file to open with wine, doing so via terminal, nothing works.

Any Ideas as to why? I need this for Monday and have been tweeking my computer for about 4 hours now with no success.

Please help!

---

### Post by ajgreeny on 2019-10-25
Having looked on the wine application database at [https://www.winehq.org/search?q=king+draw](https://www.winehq.org/search?q=king+draw) I get the impression that you are not going to be lucky.

Wine works only with a limited number of Windows applications and there is no guarantee that an app will work; do you have any information to suggest that it should be a runner or are you just hoping it does?

As a final comment, not having used wine for many years, you may have better luck with CrossOverOffice or PlayOnLinux, the latter of which is in the repos.

---

### Post by uRock on 2019-10-25
You may also want to check into this approach. [https://www.makeuseof.com/tag/run-android-apps-games-linux/](https://www.makeuseof.com/tag/run-android-apps-games-linux/)

---

### Post by 5c0rch3r75 on 2019-10-25
Post the terminal output when running the program please.

Also i recommend you to check the native software on the software manager.

[https://www.linuxlinks.com/chemistry/](https://www.linuxlinks.com/chemistry/)

This link also might be usefull to you,but i am not a chemist so my knownledge in the area is weak.

---

### Post by sduverge on 2019-10-25
Thanks to all for your reply.
I was kid of hoping it did run, since most of what I choose to use wine for works right away.
I can't give you terminal output because there's none, it just hangs there in an empty line until I get tired and close it.
I'll give it a try with Anbox and the android version.

---

### Post by zimbuf on 2019-10-25
Looks like it only requires 2D acceleration. It might work well enough to install VirtualBox and use the [Windows 10 ISO]("https://www.microsoft.com/en-us/software-download/windows10") image in it. If memory serves, the "free trial" without a license key never actually runs out.

---

### Post by sduverge on 2019-10-28
Hi, thanks, I want to avoid installing VirtualBox because I have Chromebook running Lubuntu. Space is limited.
I've been trying with Play on Linux but my HDD got full, so I moved it to the SD card but now can't access that configuration. I'd already created a virtual drive, and can see the files on my SD card, but when I run Play on Linux, is nowhere to be found and can't browse for it from the app itself, and if I try to create a new one, tries to do so on in the /home folder.
I created the symlink, but don't see the effect.

---

### Post by Holger_Gehrke on 2019-10-29
KingDraw seems to be a mixed native / .net Application; support for .net in wine is problematic AFAIK. In a win32 wineprefix the KingDraw installer runs (but all it's output is completely and totally messed up; it's probably trying to show Chinese text). By clicking on the default buttons I got it to install but running it fails with a message about needing .net 4.5 (only got .net 4 through winetricks and that already warns that it doesn't work quite right; trying to get .net 4.5.2 through winetricks aborts because .net 4 is already installed).

Holger

---

