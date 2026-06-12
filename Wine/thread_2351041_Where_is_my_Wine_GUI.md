---
title: "Where is my Wine GUI?"
date: 2017-01-30
forum: Wine
---

### Post by jsc12345 on 2017-01-30
I attempted to install Wine on my system a few minutes ago and it said I had it on my system already. Great! I thought. It seemed to be rather up-to-date, so I went ahead. Then I realized: Where is the GUI? Could someone help?

---

### Post by #&amp;thj^% on 2017-01-30
The extent of my wine use with a GUI is when I ran winecfg, have you run that command yet?

My understanding from my limited use of it is that the configuration portion uses a GUI, but the applications themselves create their own windows so it should require no additional user interface from wine.

Open up a terminal and type ```
winecfg
``` That will bring up the configuration GUI.

Winehq also has a good manual that will give you information about the settings [http://www.winehq.org/docs/wineusr-guide/config-wine-main#USING-WINECFG](http://www.winehq.org/docs/wineusr-guide/config-wine-main#USING-WINECFG).
Hope this helps.

---

### Post by oldfred on 2017-01-30
I had never installed a gui for wine.

But in trying to see if I could get xfinity to work, followed this thread and installed playonlinux which then became a gui.
[https://ubuntuforums.org/showthread.php?t=2348795](https://ubuntuforums.org/showthread.php?t=2348795)

I was able to get part of xfinity to work, but still could not view recorded shows with DVD.

---

### Post by deadflowr on 2017-01-30
default wine should come with 3 gui programs,
**configure wine**, which is winecfg.
**wine uninstaller** which is really a misnomer as you can use this to install programs
**winetricks** this is not a normal part of wine, but gets installed as an addition. (It is a recommended package and Ubuntu by default installs recommended packages when you install the main package)

Additionally, wine also adds an integrated utility to the file managers "open with" options, so you can open a windows app through the file manager:
This is usually called *wine windows program loader*. 
You can see it when you right click on a file go to open with and view "other applications" if it isn't listed as on e of the 3 or 4 options in the main open with listings.
If that makes sense.


But all that aside, once you use wine unistaller to install any app, that app becomes part of the normal system.
So if you install a windows app, it'll show like any other app in Ubuntu's menu, and then act like any other app.
(or that's the theory anyway)


And...
that said, we do not know which desktop version of Ubuntu is in use, which can help.
(Ubuntu, or Kubuntu, or xubuntu, all of which can have different methods of showing the programs in their respective menus.)

Hope it helps

---

### Post by Butthead on 2017-01-30
On my system (Kubuntu 16.04), all the Wine programs are found under "Lost and Found" in the Applications menu. :confused:

---

