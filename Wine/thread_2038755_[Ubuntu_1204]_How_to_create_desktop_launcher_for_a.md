---
title: "[Ubuntu 12:04] How to create desktop launcher for a program"
date: 2012-08-07
forum: Wine
---

### Post by EmpVal on 2012-08-07
Ubuntu: 12:04
Wine: 1.4 (from apt-get)

I am really sorry if this is a really basic question or if it has been covered before, I did try searching for the answer on the forums and the web, alas I have been unlucky so far.

I have installed Pharaoh from an iso file and I can run it from the terminal by using the following commands:

```
cd /home/adam/.wine/drive_c/SIERRA/Pharaoh

wine Pharaoh.exe
```In an attempt to save myself time I tried to create a desktop file which consisted of:

```
[Desktop Entry]
Version=1.0
Name=Pharaoh
GenericName=Pharaoh
X-GNOME-FullName=Pharaoh
Comment=Egyptian city-em-up
Type=Application
Categories=Application
Exec=
TryExec=
Terminal=false
StartupNotify=true
Icon=
```I have tried both of the commands below in exec and tryexec but I haven't had any luck with it so far.

```
/home/adam/.wine/drive_c/SIERRA/Pharaoh -wine Pharaoh.exe
```and
```

cd /home/adam/.wine/drive_c/SIERRA/Pharaoh; wine Pharaoh.exe
```Any help would be appreciated.

---

### Post by ranger1021994 on 2012-08-07
My desktop shortcut of CZ is like this :

> env WINEPREFIX="/home/shaival/.wine" wine C:\\Program\ Files\ \(x86\)\\Condition\ Zero\\hl.exe -game\ czero\ 


This is the case with my Condition Zero,change the PATHNAME to your game's directory

---

### Post by EmpVal on 2012-08-07
I have tried that; I entered this string which is where the main .exe is located, however, I still get the problem: 'There was an error launching this application'

Here is what I have put in the file now: 
```

env WINEPREFIX="/home/adam/.wine" wine drive_c/SIERRA/Pharaoh/Pharaoh.exe
```

I have double checked it and I can't see anything wrong with it.

Any help would be appreciated.

EDIT: I have managed to find out how to do this and I have documented it [here.]("http://empval.wordpress.com/2012/08/09/ever-since-i-ha/")

---

