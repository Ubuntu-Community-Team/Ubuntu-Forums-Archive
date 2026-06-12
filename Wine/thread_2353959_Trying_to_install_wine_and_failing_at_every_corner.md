---
title: "Trying to install wine and failing at every corner I turn"
date: 2017-02-26
forum: Wine
---

### Post by alpha2k on 2017-02-26
Ok first off I am not a linux person, and am very very linux challenged, the most I know about command lines is ls, for directory listing. I also am new to linux gui so I am learning stuff as I go.

That given THese are my spes and as much info as I can remember and give for better diagnosing:
I currently have a dual boot of (first) windows 10 pro - anniversary edition update and (second) 16.04.2 LTS installed (latest version) On an acer laptop v5-591G I5. It has 2 Video cards 1: Intel HD video shared 2: Nvidia gtx 950M. I have upgraded the ram to 16gb ddr4 and a samsung 850 250gb ssd drive.


I have partitioned off a 40gb partition in all, assigned 4gb swap file and the rest as the main (38gb I think it ends up being). I have successfully installed and gotten a dual boot and can boot to each OS just fine.

What I am after is installing a game called Lord of the Rings Online but have as of yet no luck in doing so

This leads me to two questions:

1: I had linux Mint latest version (18 I think it was) and ran wine but the video resulted in using the intel video card and not the nvidia card.
Will this same thing happen with ubuntu, and is there a fix to make it use the nvidia card?

2: On ubuntu I am having issues getting wine installed. It seems I get it installed and run winecfg via alt+f2 and the configuration comes up fine and I set to windows 10 as defaut config. When I run any sort of exe, be it c++, lotro install, ,net files, I don't get the option in the list to open it with the windows interaction (wine) at all, it's like wine is installed but nothing is there at all. So am I a missing perhaps a setup step or some file I need to run the files. I have tried running the exe file from both mounted drive c:\ with windows on it, basically just clicking it on that mounted drive, and I have also copied the exe file over to the .wine c:/ drive on ubuntu, but still with no luck on running the file.

I have scoured the net and looked at so many videos, but every single time I never have the results that those people have

In short I can (sort of) get wine to work but I cannot get the exe to execute via wine.

I am VERY limited in my knowledge of linux so please be simplistic and simple and most of all patient :).

I hope I was explanatory enough and gave enough information.

Thanks for any info and help


I almost forgot to add this:
I went to this link [https://ubuntuforums.org/showthread.php?t=871535](https://ubuntuforums.org/showthread.php?t=871535) and tried to install wine there via the link at number one and got this (warning it's long)

```
installArchives() failed: Selecting previously unselected package wine-devel-amd64.
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 179662 files and directories currently installed.)
Preparing to unpack .../wine-devel-amd64_2.2.0~ubuntu16.04.1_amd64.deb ...
Unpacking wine-devel-amd64 (2.2.0~ubuntu16.04.1) ...
Selecting previously unselected package wine-devel-i386:i386.
Preparing to unpack .../wine-devel-i386_2.2.0~ubuntu16.04.1_i386.deb ...
Unpacking wine-devel-i386:i386 (2.2.0~ubuntu16.04.1) ...
Selecting previously unselected package wine-devel.
Preparing to unpack .../wine-devel_2.2.0~ubuntu16.04.1_amd64.deb ...
Unpacking wine-devel (2.2.0~ubuntu16.04.1) ...
Selecting previously unselected package wine-gecko2.40:amd64.
Preparing to unpack .../wine-gecko2.40_2.40-0ubuntu1_amd64.deb ...
Unpacking wine-gecko2.40:amd64 (2.40-0ubuntu1) ...
Selecting previously unselected package wine-gecko2.40:i386.
Preparing to unpack .../wine-gecko2.40_2.40-0ubuntu1_i386.deb ...
Unpacking wine-gecko2.40:i386 (2.40-0ubuntu1) ...
Selecting previously unselected package wine-mono4.5.6.
Preparing to unpack .../wine-mono4.5.6_4.5.6-0ubuntu1~ppa1_all.deb ...
Unpacking wine-mono4.5.6 (4.5.6-0ubuntu1~ppa1) ...
Preparing to unpack .../wine1.8-amd64_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_amd64.deb ...
Unpacking wine1.8-amd64 (1:1.8.6-0ubuntu1~16.04~ricotz1) ...
dpkg: error processing archive /var/cache/apt/archives/wine1.8-amd64_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/wine/cscript.exe.so', which is also in package libwine:amd64 1.8.6-3ubuntu2~16.04.york0
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../wine1.8-i386_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_i386.deb ...
Unpacking wine1.8-i386:i386 (1:1.8.6-0ubuntu1~16.04~ricotz1) ...
dpkg: error processing archive /var/cache/apt/archives/wine1.8-i386_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/wine/cscript.exe.so', which is also in package libwine:i386 1.8.6-3ubuntu2~16.04.york0
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../wine1.8_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_amd64.deb ...
Unpacking wine1.8 (1:1.8.6-0ubuntu1~16.04~ricotz1) ...
dpkg: error processing archive /var/cache/apt/archives/wine1.8_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/wine/fonts/vgasyse.fon', which is also in package fonts-wine 1.8.6-3ubuntu2~16.04.york0
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package wine.
Preparing to unpack .../wine_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_amd64.deb ...
Unpacking wine (1:1.8.6-0ubuntu1~16.04~ricotz1) ...
Selecting previously unselected package winetricks.
Preparing to unpack .../winetricks_0.0+20170101-1ubuntu2~16.04.york0_all.deb ...
Unpacking winetricks (0.0+20170101-1ubuntu2~16.04.york0) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.8-amd64_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_amd64.deb
 /var/cache/apt/archives/wine1.8-i386_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_i386.deb
 /var/cache/apt/archives/wine1.8_1%%3a1.8.6-0ubuntu1~16.04~ricotz1_amd64.deb
Setting up wine-gecko2.40:amd64 (2.40-0ubuntu1) ...
Setting up wine-gecko2.40:i386 (2.40-0ubuntu1) ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.8; however:
  Package wine1.8 is not installed.
```
```
dpkg: error processing package wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winetricks:
 winetricks depends on wine; however:
  Package wine is not configured yet.
```
```
dpkg: error processing package winetricks (--configure):
 dependency problems - leaving unconfigured
Setting up wine-devel-i386:i386 (2.2.0~ubuntu16.04.1) ...
Setting up wine-devel-amd64 (2.2.0~ubuntu16.04.1) ...
Setting up wine-mono4.5.6 (4.5.6-0ubuntu1~ppa1) ...
Setting up wine-devel (2.2.0~ubuntu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
```

Perhaps someone can decipher that mumbo jumbo, because it might as well be german to me heheh.

---

### Post by mr-good555 on 2017-03-12
I'm no expert, but I play games on Wine.

Double-clicking an .exe will usually show you what's inside the exe, instead of actually running it. (Imagine reading DO,RE,MI instead of actually listening to music)

To run an Exe in Ubuntu's wine, rightclick it, then choose "Wine Windows Program Loader".

============

If you want a way to be able to double-click it instead, I haven't mastered this yet, but you need to make a shortcut.

Open a "Leafpad", either through the Start Menu, or typing "leafpad" on either "CTRL + ALT + T" or "Windows + R". This is like Notepad for Linux.

Then paste this stuff, changing "/home/MyUserName/Example/Path.exe" with where you kept the EXE file. The rest should also give you a hint of what needs to be there, and is otherwise harmless to change.

```
[Desktop Entry]
Name=My Exe File
Exec=wine /home/MyUserName/Example/Path.exe
Terminal=false
Type=Application
Categories=Application;
```

Save this on your desktop or whatever as "My Exe File.desktop" and it should change to a double-clickable thing. To rename it though, just edit it with leafpad again.

---

