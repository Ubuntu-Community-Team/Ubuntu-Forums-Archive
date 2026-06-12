---
title: "3D Desktop with xgl + beryl"
date: 2006-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by fedoux on 2006-12-22
Hello Linux Friends

Here is my report about Umbuntu edgy 6.10 x64 with xgl and beryl 3D Desktop, i´am a german user ... dont think about my english ;)

In front i will show a small collections of my screenshots from my 3D Desktop on ubuntu --> [http://www.fedouxia.de/gallerie/linux/xgl_beryl_x64/gxl_beryl_x64.html](http://www.fedouxia.de/gallerie/linux/xgl_beryl_x64/gxl_beryl_x64.html)

.... Ok people come back to ground ;) here is my report !

Hardware:
Mainboard --> [http://www.asrock.com/PRODUCT/K8NF4G-SATA2.htm](http://www.asrock.com/PRODUCT/K8NF4G-SATA2.htm)
--> with AMD Semprom 3000+ x64
Grafik: Onboard (nVidia Corporation, C51G [GeForce 6100]), ASRock Incorporation
Screen: Unknow Modell: MD1702
TV Card: Hauppauge computer works Inc., Brooktree Corporation, Bt878 Video Capture, WinTV Series

Ok,the instalation of ubuntu 6.10 edgy comes without problems, it was fast and easy !
The installallation of xgl also fast and easy :) here is the howto i have used --> [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
The Beryl Installation also fast and easy :) this is the howto i used --> [https://help.ubuntu.com/community/CompositeManager/InstallingBeryl](https://help.ubuntu.com/community/CompositeManager/InstallingBeryl)
(the repository I did not have to try any functioned with)

after installation i have a small problem with my keyboard layout "altGr" are BAD, this problem i fixed with this comand as user in a terminal ([http://friederschueler.de/linux/is-it-a-bug-no-it-is-a-feature-beryl-shift-backspace-feature/](http://friederschueler.de/linux/is-it-a-bug-no-it-is-a-feature-beryl-shift-backspace-feature/))

xmodmap -e “keycode 22 = BackSpace”
xmodmap -e “keycode 113 = Mode_switch”
echo ‘keycode 22 = BackSpace’ » ~/.Xmodmap
echo ‘keycode 113 = Mode_switch’ » ~/.Xmodmap

the composite problem with nvidia and Video under beryl and xgl i fixed with this howto --> [http://sarglord.wordpress.com/howtos/](http://sarglord.wordpress.com/howtos/)
i have to add 2 steps for my nvidia Card in xorg.conf.

Sections Device:
Option "RenderAccel" "true"
Option "AllowGLXWithComposite" "true"

and the end of the xorg.conf:
Section "Extensions"
         Option  "Composite" "Enable"
EndSection

that was all for enjoy videos on xgl with beryl and vlc player i used. I dont know what about the "BAD libdv**" and the video file are used this lib ! but i think there are no problems with it ;) !!!

I have installed this fantastic 3D desktop 5 days ago. In all this time i have nothing problems with my system, no frozen and no crashes or other ugly moments !
It is verrry stable for a beta, other applications are running without Porblems.

at last i have installed effectiv tools for default gnome settings. --> [http://wiki.ubuntuusers.de/GNOME_Konfiguration?action=show&redirect=Konfigurationseditor](http://wiki.ubuntuusers.de/GNOME_Konfiguration?action=show&redirect=Konfigurationseditor)

Ok ....

Here are my problems i have found at the last 5 days i have installed the 3D Desktop:

My TVtime have problems with show me a correct pictire, the tv screen are verry distorted, disturbed.
My gedesklets i cant move to the last 1/3 section of the right side the screen (desktop) and i cant move the desklets to le last 1/3 section of the buttom side from the screen (desktop). But the desktop icons will move to all places of the screen (desktop).

And the incommodity that for the moment still no Icons and Metacity Themes can be used are certainly in that finally version settled. I hope ;)

Up to then a very good work the Ubuntu, i have try to install the 3D desktop on other Linux Distru´s (No Suse) .... ok i say nothing ;)

thats all :)

bye
fedoux

---

### Post by xopher on 2006-12-22
> And the incommodity that for the moment still no Icons and Metacity Themes can be used are certainly in that finally version settled. I hope 

Actually, you can use metacity themes with Beryl (>= 0.1.3), the program you need (which you can replace emerald with if you don't want it) is called Heliodor.

```
sudo apt-get install heliodor
```

It's available in the beryl repositories.

and Icons? Those have always been changeable..

---

### Post by jpmontalbo on 2006-12-22
Hello thank you so much for your reports. I did notice on your screenshots that gnome was using gtk1 theme. I read somewhere in the beryl forums that you need to run

```
gnome-settings-daemon
```

If it works add it in your session start up. Hope that helps. I believe that will resolve your icon issues as well. :)

---

