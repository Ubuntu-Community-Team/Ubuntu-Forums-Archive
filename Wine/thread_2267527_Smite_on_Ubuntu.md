---
title: "Smite on Ubuntu"
date: 2015-03-02
forum: Wine
---

### Post by gabe10 on 2015-03-02
[COLOR=#000000]My favorite game right now is Smite, a Moba by Hi-rez, but it is only for windows, and I don't want to run an emulator for that. I want to get smite working on ubuntu, whether it be with wine, or something else. I am very new to ubuntu. It is a DX9 game if that helps. Thanks[/COLOR]

---

### Post by Fincer on 2015-03-02
According to Wine Application Database, this game is not installable:

[LIST]
[*][Wine AppDB - Smite]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=31371") 
[/LIST]
  It's very unlike that you get the game working with Wine. The latest test result has been done with Wine 1.7.33 which is relatively a quite new Wine version. You can always try, though. Wine Application Database is not like a holy bible which you have to believe fundamentally word by word but it rather gives you some references on what to expect for if you try to install a program.

I've submitted several test results for some programs and got them working though they were claimed to be "garbage". Of course, earlier test results were very old at that time.

Anyway, since you're quite new on Linux Ubuntu, I give you a simple command sequence how you can install the latest Wine.

To install the newest Wine, copy & paste this into your terminal (internet connection required):

```
sudo apt-add-repository -y ppa:ubuntu-wine/ppa && \
sudo apt-get update && \
sudo apt-get install wine1.7
```

I recommend you to take a look on PlayOnLinux, too. With PlayOnLinux you  can have/manage multiple Wine versions on your system which is quite  useful especially with games. Take a look on
 
[LIST]
[*][PlayOnLinux.com]("https://www.playonlinux.com/en/") 
[*][Easily install Windows games on Linux with PlayOnLinux - howtogeek.com]("http://www.howtogeek.com/107462/easily-install-windows-games-software-on-linux-with-playonlinux/")[URL="http://www.howtogeek.com/107462/easily-install-windows-games-software-on-linux-with-playonlinux/"]
[/URL] 
[/LIST]
Regards,
Fincer

---

### Post by Fincer on 2015-03-02
Allright, I filled a bug report about this issue on Wine Bugzilla and linked it to Smite's Application Database page.

[[Bug 38172] Smite: Hi-Rez Studios Authenticate and Update Service fails - Wine Bugzilla]("https://bugs.winehq.org/show_bug.cgi?id=38172")

Regards,
Fincer

---

### Post by gabe10 on 2015-03-02
thanks a lot

---

### Post by Fincer on 2015-03-02
No prob.

To pull urgent attention to the installation issue on Wine, please take a step forward and register to the Wine Bugzilla and add yourself to bug-related CC-list. That's the way Wine developers can actually confirm the bug really exists ("affecting multiple users" -> confirmed) and the bug may get some extra attention instead of having a risk to become a forgotten/abandoned issue for years ahead simply because "nobody cared".

Simple instructions:
Register yourself to [Wine Bugzilla](https://bugs.winehq.org/) -> Log in -> go to the bug page ([link here]("https://bugs.winehq.org/show_bug.cgi?id=38172")) -> check "CC list" checkbox -> Save Changes

Thanks.

Regards,
Fincer

---

