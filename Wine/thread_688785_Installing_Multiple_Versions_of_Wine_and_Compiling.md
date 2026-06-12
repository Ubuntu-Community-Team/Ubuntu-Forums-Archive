---
title: "Installing Multiple Versions of Wine and Compiling them.  Help please."
date: 2008-02-05
forum: Wine
---

### Post by Sugi on 2008-02-05
I am installing multiple versions of wine and I am having problems with it.  I have "wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb" and I need it to install to a special directory that won't affect my current installation of wine 0.9.54.  I am trying to compile the 0.9.35 .deb, but I have never compile anything.  So, I am unsure on how to go about compiling .deb file or anything.  Can anyone dumb down this steps for me?

If i install the 0.9.35 .deb from the terminal and i want it to install to a special directly.  would I type this in?:

     **code**
> dpkg -i /home/USER_NAME/Desktop/wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb ./configure --prefix=/usr/wine-0.9.35
is that corrent?


My refers:
IRC user:  > "if youre compiling from sources you can specify new dir when running configure (eg ./configure --prefix=/usr/wine-0.9.35)"
Compiling Website:  [http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")

Thank you,
Sugi

---

### Post by Sugi on 2008-02-06
Bump

---

### Post by happyhamster on 2008-02-06
Deb files are pre-compiled packages. The instructions you found are applicable when compiling from source. I don't know if you can do the same thing when using deb files (perhaps you could ask in the General Help forum).

I have no experience with running 2 instances of wine (when I need an older wine version, I just get rid of the current one (backing up all savegames and such) and install the desired version). Perhaps you could try making a new user account (never tried that either, heh).

- Anyway, when compiling from source, you need the source code:
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

- Extract the file into its default folder. Open the folder in a terminal.

- Grab all dependies you need:
sudo apt-get build-dep wine

- Normally, you would proceed:

./configure
make depend && make
sudo make install
(takes ~30 minutes on an average pc, could take much longer on a slow one)

- But in your case, for those last steps, you would need  to follow the wiki you found. This probably won't be easy though (and will take quite some time).
 
[http://wiki.jswindle.com/index.php/Installing_Wine#Multiple_Installs](http://wiki.jswindle.com/index.php/Installing_Wine#Multiple_Installs)

---

### Post by ArtInvent on 2008-02-09
I would also like to know how to run multiple versions of Wine. I have already compiled the latest Wine with no problems. What I can't really figure out is how **exactly** to use WINEPREFIX to run a particular version of Wine. The howto's I have found say simply something like 'Of course you will have to use WINEPREFIX . . . " but that's about all. Most of the instructions I've seen for using WINEPREFIX are oriented on making bottles for different apps run under a single version of Wine, but again, don't say exactly how you might run these bottle using ***different Wine versions***.

I am able to compile and use different versions of normal Linux apps. But most apps are standalone executables. Wine on the other hand is simply a layer that other apps are run through so I don't quite it. 

So I have my specially compiled Wine sitting in a directory. I did not do a make install so it is not installed system-wide, but the **wine** executable is there. Somehow you have to direct the WINEPREFIX command to the directory this directory that your desired version of Wine is in, and then also to the bottle directory that your app and c: drive and registry are in. What is the syntax of this command? When I try this it always uses the system-wide installed Wine instead.

---

### Post by Sugi on 2008-02-10
ArtInvent, I know the WINEPREFIX, but I don't know how to compile.  Can you write out step by step how you compile the wine version you used.  And when it comes to the WINEPREFIX, this is what you got to do.
env WINEPREFIX="/directory/you/installed/the/second/wine/directory" wine "/second/wine/directory/game/game.exe"

My real example:
env WINEPREFIX="/home/LongPENIS/.wineB2" wine "/home/LongPENIS/.wineB2/drive_c/Program Files/Diablo II - B2/Diablo II.exe" -d3d9 -w --emulate-virtual-desktop 800x650

Hope this help,  Please help me out on how to compile a .deb wine file,
Sugi

---

### Post by Ferrat on 2008-02-10
I'm not sure it's possible since both version would use the same calls and that could create a problem with the wrong wine picking up stuff it shouldn't ect. just running two instances of wine creates some problems with for ex. sound drivers and so on or perhaps it's possible but a lot of work getting two different version of wine to install on the same system, easiest way is just to have the .deb files of the wine versions you need in a folder and removing / installing depending on what version you want to use 

If you want to compile a .deb then you can use the link in my signature, a easy script that installs packages that are useful and compiles a .deb of the wine version of your choice :)

---

