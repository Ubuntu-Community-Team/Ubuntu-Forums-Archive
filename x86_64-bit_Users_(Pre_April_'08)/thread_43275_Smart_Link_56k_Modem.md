---
title: "Smart Link 56k Modem"
date: 2005-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by pace_tua on 2005-06-21
[color=Red][resolved]
 Used Stupid Mode in wvdial \\:D/
 [/resolved][/color]

I know the Mods will hate me for double posting, but I think I'll get more answers here than in the Networking forum.

System:


[list]
[*]AMD64 mobile 3400+
[*]Smart Link 56k Modem
[*]Dual Booted Ubuntu and Windows 2000
[/list]Problem:
[list]
[*]Ubuntu cannot detect the Smart Link 56k Modem
[/list]If you want a documented trail of what I have done, [here's the thread]("http://ubuntuforums.org/showthread.php?p=222336"). But in short I have managed to install the [following packages]("http://ubuntuforums.org/showthread.php?p=222336") (that are supposedly multiverse) by [color=Sienna]sudo dpkg --force-all -i sl-modem*.deb[/color] from my CDROM. Then I [color=Sienna]cd /usr/src[/color] and repeated the command. I recieved no errors.

However, Ubuntu is still unable to detect my modem.

Thanks, and to lay it out, I'm a Linux newbie :-\"

---

### Post by jrev on 2005-06-21
Is it an external or internal modem ?

the package gnome-ppp was missing on my install  CD and install DVD so you can download it from the sources then you can configure your ISP dialup connection OK
 ;-)

---

### Post by pace_tua on 2005-06-21
[QUOTE=jrev]Is it an external or internal modem ?[/QUOTE]
It's internal.

[QUOTE=jrev] the package gnome-ppp was missing on my install CD and install DVD so you can download it from the sources then you can configure your ISP dialup connection OK[/QUOTE]
It's configured, Ubuntu can't detect the modem.

---

### Post by jrev on 2005-06-22
When I started on Linux I bought an external modem to get rid of he problem of internal winmodems
It's a simple solution for the beginner 
We have lots of problems to solve on top of this one which has no solution but make a new driver (if you can) :smile:

---

### Post by benson on 2005-06-23
Same problem here. Can't detect internal modem.

Can't get rid of windows  ](*,) I'm stuck with winmodems... :(

---

### Post by fizgig on 2005-06-24
I got my internal 56k modem working with the smart link drivers.  I talk about it on my [linux page]("http://mattsmith.hostmatrix.org/zx5078cl/").  Perhaps it will help.

---

