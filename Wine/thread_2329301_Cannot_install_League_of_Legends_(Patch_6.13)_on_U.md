---
title: "Cannot install League of Legends (Patch 6.13) on Ubuntu 16.04 32bit"
date: 2016-06-29
forum: Wine
---

### Post by mcharitos on 2016-06-29
Hello, ..about 2 days ago I did a clean install of Ubuntu 16.04 32bit on my Desktop PC, and since then i'm unsuccessfully trying to install League of Legends..

My previous OS was Ubuntu Trusty Tahr and i managed to play LoL with the help of Play On Linux.
About two weeks ago, I had to format it though, cause i needed Windows for running a program that i needed for my school examinations. So, after that ended, i decided to return to Ubuntu, and try the latest 16.04.

Unfortunately, first thing i noticed was that PlayOnLinux was nowhere to be found on the new Software Center. As such, i downloaded and installed this file from the official site: PlayOnLinux_4.2.10.deb (it's here [https://www.playonlinux.com/en/download.html](https://www.playonlinux.com/en/download.html)). The reason i didn't do it through terminal, was that they haven't a command for 16.04.

So, [B]every time the game patches, it repeatedly crashes on 58% with this message
[/B]
[IMG]https://s32.postimg.org/qulviv2th/Errors.jpg[/IMG]

After some more attempts, i thought i should return to Ubuntu 14.04 32bit where it was working, and so i did. Unfortunately, things there where even worse, as for some reason the League of Legends installer now crashes immediately.

And..... i'm back to Ubuntu 16.04 32bit again, since i decided that i had a somewhat better result.

So what do you think? Is it a League client issue due to their new patch, or it's a PlayOnLinux one? I have no idea on how i should proceed, so any opinions are welcome -thank you :)

[COLOR=#b22222]My PC specs[/COLOR]
Memory: **2,0 GiB**
Processor: **Intel® Pentium(R) D CPU 3.40GHz × 2 **
Graphics: **Gallium 0.4 on AMD RV620 (DRM 2.43.0, LLVM 3.8.0)**
[COLOR=#b22222]My OS[/COLOR]
**ubuntu 16.04 LTS**
OS type: **32-bit**

[COLOR=#0000cd]PlayOnLinux 4.2.10[/COLOR]
i tried with two Wine versions: the recommended [COLOR=#0000cd]1.9.2-LeagueOfLegends5[/COLOR] and another one, the [COLOR=#0000cd]1.9.2-staging-LOL3[/COLOR]

---

### Post by Liam_Murphy on 2016-06-29
Launch Playonlinux through the terminal

Type this in a terminal

```
playonlinux
```

Then launch the game like usual, see if any errors on the playonlinux side come through.

---

### Post by mcharitos on 2016-06-29
I will try it with the recommended Wine version 1.9.2-LeagueOfLegends5 on the EUNE server, and i'll post if i find anything- thank you!

---

### Post by mcharitos on 2016-06-30
So hi again,

I completely uninstalled everything, and re-installed PlayOnLinux and LoL. The Wine version which prompted me to work with (and i did) is the 1.9.2-LeagueOfLegends5.
So after i done this, i closed PlayOnLinux, and re-opened it through Terminal. I chose LoL,  clicked the Run button, and it immediately stopped showing the above same error  message. These are the results shown on Terminal

user@user-123:~$ playonlinux
Looking for python... 2.7.11+ - wxversion(s): 3.0-gtk2
selected
[main] Message: PlayOnLinux (4.2.10) is starting
[clean_tmp] Message: Cleaning temp directory
[Check_OpenGL] Message: 32bits direct rendering is enabled
[POL_System_CheckFS] Message: Checking filesystem for /home/user/.PlayOnLinux/
[main] Message: Filesystem is compatible
[install_plugins] Message: Checking plugin: Capture...
[install_plugins] Message: Checking plugin: ScreenCap...
[install_plugins] Message: Checking plugin: PlayOnLinux Vault...
[update_check] Message: List is up to date
[POL_System_CheckFS] Message: Checking filesystem for lol.launcher.admin.exe
[POL_Wine] Message: Running wine-1.9.2-LeagueOfLegends5 lol.launcher.admin.exe (Working directory : /home/user/.PlayOnLinux/wineprefix/LeagueOfLegends/drive_c/Riot Games/League of Legends)
[POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See [http://www.playonlinux.com/fr/page-26-Winemenubuilder.html](http://www.playonlinux.com/fr/page-26-Winemenubuilder.html)
[POL_Wine] Message: Wine return: 0
[POL_DetectVideoCards] Message: Gettings GPU informations
[POL_LoadVar_Device] Message: VendorID : 1002
[POL_LoadVar_Device] Message: DeviceID : 95c6
[POL_Website_GET] Message: GET [http://www.playonlinux.com/api/s.php?data=MTAwMn45NWM2fjB%2bTGVhZ3VlIE9mIExlZ2VuZHN%2bMH4xfjF%2bfjB%2bVWJ1bnR1IDE2LjA0IExUU34w](http://www.playonlinux.com/api/s.php?data=MTAwMn45NWM2fjB%2bTGVhZ3VlIE9mIExlZ2VuZHN%2bMH4xfjF%2bfjB%2bVWJ1bnR1IDE2LjA0IExUU34w)
fjExMjA4ODg4NjYyODk1Njh%2bMX5MZWFndWUgb2YgTGVnZW5kc340LjIuMTB%2bMg==

---

### Post by mcharitos on 2016-07-08
Hi again,
so.. in the end i wasn't able to make it work on 16.04, so i'm back to 14.04
Things didn't go smooth there either, as the installation refused to complete. After some online search i discovered threads saying that for some reason, even though PlayOnLinux offers to install some microsoft fonts which are necessary, it never does and doesn't inform you about this. It just let's you think it was completed.  So, i installed these fonts after, through the terminal.
It's been a while since i did that, but i think the command is ```
sudo apt-get install ttf-mscorefonts-installer
``` and to accept the EULA you have to use TAB to get you to the bottom of the window where there is a "yes". I don't know why this issue hasn't been addressed yet since i found some posts about it, but idk.
So the only time i used the Terminal during the installation of LoL was to install these fonts.


Just today, i decided to install steam through PlayOnLinux, which was easy. From steam i installed Magic Duels, and though everything seemed to be working fine, when i ran the game, a window popped up with the title "Microsoft Visual C++ Runtime Library" writing "Runtime Error!" etc. And then game crushed.
Does anyone knows what this means?

Thank you!

---

### Post by squirrel3 on 2016-07-08
Ubuntu 16 may not be compatible with with Leagues, at least yet. It's just my educated guess.

---

### Post by mastablasta on 2016-07-11
does this mean you got it working? i am also on EUNE, but i play from windows occasionally.

furthermore, next time you need windows just install them in a virtual machine (virtualbox, wmware...).

also re: magic duels --> different issue - different thread.

---

### Post by mcharitos on 2016-07-13
I got it working on Ubuntu 14.04 but not on Ubuntu 16.04. And regarding Magic Duels i guess you're right i should and maybe i will.

Thank you all for help :)

---

### Post by alexmym10 on 2016-11-15
What work for me in Ubuntu 16.04 LTS as of patch 6.22 was changing settings of LoL launcher through PlayonLinux.

    1.Install the most recent version of PlayonLinux and install the League of Legends. (Do not start game after installation)

   2. Using PlayonLinux access the LoL game settings.

  3.  In PlayonLinux change the default wine version using the "General" tab.From 1.9.2 LeagueofLegends5 to the latest stagging version. When i wrote this answer it was "1.9.22stagging" i install both x86 and x64 wine versions. (again this all done through the playonlinux settings)

   4. Through playonLinux settings now access the "wine" tab and click on "configure wine" icon. There you will change the default windows version from Windows XP to Windows Vista. (all other don't seem to work at least not on my PC)

    5. Now using PlayonLinux start the LoL launcher (the screen will look weird, however, you should be able to see the League of legends logo on the top left, the percentage and download speed bar on the middle and the settings and minimize icons on the right.

   6. This installation takes longer than when using windows.For me using Windows LoL installs in about 2.5 hrs. However, using Ubuntu it took 5 to 6 hours to install. During the installation it might seem like if the installation freezes or your installation stops and your download speed might even reduce to cero for a while but "PLEASE BE PATIENT"

   7. Today is November 15, 2016 and i install LoL 6.22 and play.

    8.if there is any new patch i would try waiting for the new playonlinux stagging version of wine before removing or changing anything else.

---

### Post by vinxenxo on 2017-02-01
Alex you'r the boss. I'm running LoL on Ubuntu 16.10 64bits with your instructions, no bug, all fine

Really thx man :D

One more thing: are you download the new beta launcher 7.2 throught LoL interface? it works too?

Thanks man.

V

> **alexmym10 said:**
> What work for me in Ubuntu 16.04 LTS as of patch 6.22 was changing settings of LoL launcher through PlayonLinux.

    1.Install the most recent version of PlayonLinux and install the League of Legends. (Do not start game after installation)

   2. Using PlayonLinux access the LoL game settings.

  3.  In PlayonLinux change the default wine version using the "General" tab.From 1.9.2 LeagueofLegends5 to the latest stagging version. When i wrote this answer it was "1.9.22stagging" i install both x86 and x64 wine versions. (again this all done through the playonlinux settings)

   4. Through playonLinux settings now access the "wine" tab and click on "configure wine" icon. There you will change the default windows version from Windows XP to Windows Vista. (all other don't seem to work at least not on my PC)

    5. Now using PlayonLinux start the LoL launcher (the screen will look weird, however, you should be able to see the League of legends logo on the top left, the percentage and download speed bar on the middle and the settings and minimize icons on the right.

   6. This installation takes longer than when using windows.For me using Windows LoL installs in about 2.5 hrs. However, using Ubuntu it took 5 to 6 hours to install. During the installation it might seem like if the installation freezes or your installation stops and your download speed might even reduce to cero for a while but "PLEASE BE PATIENT"

   7. Today is November 15, 2016 and i install LoL 6.22 and play.

    8.if there is any new patch i would try waiting for the new playonlinux stagging version of wine before removing or changing anything else.

---

