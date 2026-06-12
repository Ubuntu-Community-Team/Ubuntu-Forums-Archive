---
title: "Programm has no fonts, Play on Linux and Winetricks show different versions"
date: 2017-10-19
forum: Wine
---

### Post by docdoc2 on 2017-10-19
Hello,

as can be seen on the screen shot below, a program, Shot Designer, which i installed via Adobe Air, has no fonts. Adobe Air seems to have been installed properly. 
Winetricks shows me i have wine 2.02
Play on linux shows me i have 2.19

this is very confusing, also there are so many versions. Which should i use?
I was unable to do any uninstall or reinstall. Even when i remove virtual drives and wine versions via Play on Linux, or uninstall Winehq, the installation persists. Any ideas?

[https://i.imgur.com/7kj799W.png](https://i.imgur.com/7kj799W.png)

---

### Post by yoshii on 2017-10-23
All I know is that you can put .ttf (true type fonts) into the c:\Windows\Fonts folder which is located within "/home/yourusername/.wine/drive_c/windows/Fonts/"

If there's nothing in there, that's part of why theres no font display.  A few programs really need specific fonts to be in there.  Luckily, all that needs to happen is to get the fonts and put them in there and restart the computer.

---

### Post by docdoc2 on 2017-11-07
Thanks! I just copied all the fonts which are normaly installed on windows in the emtpy folder and now it's working! Yay

---

