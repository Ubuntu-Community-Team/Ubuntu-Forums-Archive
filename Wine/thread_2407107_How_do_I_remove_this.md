---
title: "How do I remove this??"
date: 2018-11-29
forum: Wine
---

### Post by dryan775 on 2018-11-29
Hello,

I bought realMyst Masterpiece edition from Steam, hoping to play this iconic game on my Ubuntu 16.04.4 LTS system.
Steam's inhouse version of Wine failed so I installed Wine from the system software installation system.
That failed same as the Steam version. Critical failure before anything happened.

So I went to WineHQ and downloaded the .deb file, installed it and launched the game.  I had to let it auto install a couple more small pieces, but the game RAN! 
I played for several hours, but when I went back tonight, it's crashing just like it did before

So miffed now that I just want to remove wine and I'll just buy the game again for my tablet and be done with it.

I've tried:
sudo apt remove wine
sudo apt-get remove wine
sudo apt remove wine
sudo apt remove wine --purge
sudo apt remove --purge wine
rm -r .wine


etc - all taken from forums and help systems, none of which work.  
The software installer doesn't think it is still installed and doesn't give em the option

most the of the CLI commands give this error:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'wine' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libsdl2-2.0-0 libsndio6.1 p7zip
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 58 not upgraded.

but then if I type wine notepad, good 'ol Windows Notepad.exe runs

HOW DO I GET RID OF THIS

---

### Post by again? on 2018-11-29
The command you use in terminal isn't necessarily the name of the installed package.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt install wine**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is a virtual package provided by:
  [COLOR="#FF0000"]wine-stable[/COLOR] 3.0-1ubuntu1
  wine-development 3.6-1
You should explicitly select one to install.
```

You can search for packages installed via a deb or the software manager using a partial string.
```
apt list --installed | grep -i wine
```

eg after installing wine through the software centre.
(Notice the package you installed is signified by "[installed]" while packages installed as dependencies are signified by "[installed,automatic]")
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt list --installed | grep -i wine**

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fonts-wine/bionic,bionic,now 3.0-1ubuntu1 all [installed,automatic]
libwine/bionic,now 3.0-1ubuntu1 amd64 [installed,automatic]
wine-stable/bionic,bionic,now 3.0-1ubuntu1 all [installed]
wine32/bionic,now 3.0-1ubuntu1 i386 [installed,automatic]
wine64/bionic,now 3.0-1ubuntu1 amd64 [installed,automatic]
```

To remove (if you installed a deb the name may be winehq-stable)
```
sudo apt purge wine-stable
```

Then remove package dependencies no longer needed.
```
sudo apt autoremove
```
I don't use wine but apparently your windows apps are installed to ~/.wine which you can delete.

---

### Post by dryan775 on 2018-11-30
Thank you! 

The list command returned 3 wine names (wine-gecko2.21, wine1.6, wine-mono0.0.8).  Removed them all and it seems to be gone

---

