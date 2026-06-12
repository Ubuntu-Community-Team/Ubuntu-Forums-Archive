---
title: "Could not load kernel32.dll"
date: 2012-10-02
forum: Wine
---

### Post by lite1979 on 2012-10-02
So I upgraded from 10.04 LTS to 12.04 LTS recently, and I've been really happy with the upgrade, except for gaming performance in wine. I only play half-life 1 and half-life 2, but I was noticing that when I had Pandora playing music in Firefox, I would get no sound in wine.

This led to me trying to uninstall wine and re-installing it several times. I removed my .wine folder, Steam, and all of my gaming content, and upon re-installing, I can't even open notepad.

```
lite@lite-desktop:~/.wine/drive_c$ wine notepad
wine: could not load kernel32.dll, status c0000135
lite@lite-desktop:~/.wine/drive_c$
```I have been using this same PC since 2007, and I've only had linux on it (started with Kubuntu 7.04).

```
lite@lite-desktop:~/.wine/drive_c$ wine --version
wine-1.3.1
lite@lite-desktop:~/.wine/drive_c$ 
```As you can see, I obviously have some older stuff hanging around on my hard drive. It should read wine 1.5.14, since that's what comes up when I run 'winecfg', but I'm totally lost at this point. What should I do? I know the Steam beta for Linux is coming out this month, and I'm going to fight tooth and nail to be one of the 1000 users chosen to test it, but I'd still like to figure out what I'm doing wrong, especially if I'm not one of the lucky few.

```
lite@lite-desktop:~/.wine/drive_c$ whereis wine
wine: /usr/bin/wine /usr/bin/X11/wine /usr/local/bin/wine /usr/local/lib/wine /usr/share/wine /usr/share/man/man1/wine.1.gz
lite@lite-desktop:~/.wine/drive_c$
```The PC is an AMD Athlon 64x2 4800+ w/4GB RAM and an nvidia GT240. If it's time to finally format and install to a clean hard drive, I'll do that, but I want that to be a last option.
Thanks in advance!

[IMG]http://i49.tinypic.com/2weiagy.png[/IMG]


Edit: I just tried wine64 notepad and it worked... Hmmm.

Edit again: I'm currently installing Steam using the terminal:

```
msiexec /i SteamInstall.msi
```

---

### Post by lite1979 on 2012-10-03
Unfortunately, I couldn't read anything during the Steam install (font problems, maybe?). Also, winetricks isn't working at all. I'm not sure how to call it with wine64, either.. 

I definitely still have to remove some of the older wine versions that appear to be installed on my system, but I'm not sure which ones to remove. Any suggestions? Thanks again.

---

### Post by regor210 on 2012-10-03
In ubuntu 12.04 on my 64bit computer I install 

$ sudo apt-get install libc6:i386 libgcc1:i386 gcc-4.6-base:i386 libstdc++5:i386 libstdc++6:i386

before I install wine to get the 32bit lib's needed by wine to run 32bit apps.

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following command into the terminal window minus the $.

---

### Post by lite1979 on 2012-10-04
```
lite@lite-desktop:~$ sudo apt-get install libc6:i386 libgcc1:i386 gcc-4.6-base:i386 libstdc++5:i386 libstdc++6:i386
[sudo] password for lite: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc-4.6-base:i386 is already the newest version.
gcc-4.6-base:i386 set to manually installed.
libgcc1:i386 is already the newest version.
libgcc1:i386 set to manually installed.
libstdc++6:i386 is already the newest version.
libstdc++6:i386 set to manually installed.
libstdc++5:i386 is already the newest version.
libstdc++5:i386 set to manually installed.
libc6:i386 is already the newest version.
libc6:i386 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lite@lite-desktop:~$ 

```

```
lite@lite-desktop:~$ locate kernel32.dll
/home/lite/.wine/drive_c/windows/system32/kernel32.dll
/home/lite/.wine/drive_c/windows/syswow64/kernel32.dll
/home/lite/Downloads/wine-1.4.1/dlls/kernel32/kernel32.dll.fake
/home/lite/Downloads/wine-1.4.1/dlls/kernel32/kernel32.dll.so
/usr/lib/i386-linux-gnu/wine/kernel32.dll.so
/usr/lib/i386-linux-gnu/wine/fakedlls/kernel32.dll
/usr/lib/x86_64-linux-gnu/wine/kernel32.dll.so
/usr/lib/x86_64-linux-gnu/wine/fakedlls/kernel32.dll
lite@lite-desktop:~$ 

```

Looks like I have a path problem or an arch problem. I'm going to remove everything wine-related again and try re-installing.

---

### Post by cwwilson721 on 2012-10-04
Try this (in terminal):

```
export WINEARCH=win32
export WINEPREFIX=~/<Whatever wine folder you want to make>
winecfg
winetricks
```

First line sets up a 32bit wine environment
Second line sets up the folder you want the 32bit wine to be in
Third line creates the "bottle" as a 32bit wine, and installs all the registry files, gecko, etc.
Last line runs winetricks in that "bottle"

After that, in the same terminal, just run the setup file you need, and it will install to the "bottle" you just created (as long as you didn't close the terminal. If you did, open a new one, and do the 2nd line again)

---

### Post by lite1979 on 2012-10-06
The first two lines worked fine, but look at what happens when I try to run winecfg:

```
lite@lite-desktop:~$ export WINEARCH=win32
lite@lite-desktop:~$ export WINEPREFIX=/home/lite/.wine/win32
lite@lite-desktop:~$ winecfg
/usr/bin/winecfg: 52: exec: wine: not found
lite@lite-desktop:~$ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine1.5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lite@lite-desktop:~$ 

```

```
lite@lite-desktop:~$ sudo apt-get wine
E: Invalid operation wine
lite@lite-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
lite@lite-desktop:~$ 

```

---

### Post by cwwilson721 on 2012-10-06
Try:
```
sudo apt-get install ***[COLOR="Red"]wine1.5[/COLOR]***
```

Makes a difference

---

### Post by cwwilson721 on 2012-10-06
Sorry..Didn't read the whole thing.

You already have wine 1.5 installed. Trying to install regular wine will fail (as you have seen)

Go ahead and delete the wine folder you just made.

Then:
```
export WINEARCH=win32
export WINEPREFIX=(whatever you want)
winecfg
```

Then, do what you need to do

---

### Post by lite1979 on 2012-10-08
I still run into the problem of not being able to run winecfg:

```
lite@lite-desktop:~$ export WINEARCH=win32
lite@lite-desktop:~$ export WINEPREFIX=.wine/win32
lite@lite-desktop:~$ winecfg
/usr/bin/winecfg: 52: exec: wine: not found
lite@lite-desktop:~$ 

```I asked earlier in the thread how to call winecfg with my install of wine1.5. I'm sorry if I seem like a total noob right now, but I've been using wine without problems for so long until now that I'm really unsure how to solve this problem. 

I did exactly what you told me to do the first time and it didn't work for reasons that you've noted.

---

### Post by lite1979 on 2012-10-15
When trying to run steam from terminal, I get the following error in wine in its separate dialog box after trying to execute with this code:

```
lite@lite-desktop:~/.wine$ wine drive_c/Program\ Files\ \(x86\)/Steam/Steam.exe p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:dbghelp:elf_search_auxv can't find symbol in module

```

"Steam.exe (main exception): Unable to write to the current Steam application folder.
Please move Steam to a folder where you have write privileges."

Could this be because Steam didn't install correctly? I ran "msiexec /i steaminstaller.msi" and it seems to go through the install pretty well, but when it comes to putting in my username and password, I can't see any of the text at that point. I have an icon on my desktop for Steam now, but clicking it just locks my desktop and makes the ubuntu drum noise. This is driving me nuts!

---

### Post by lite1979 on 2012-10-16
Pics for clicks:

[IMG]http://i45.tinypic.com/3v3us.png[/IMG]

---

### Post by lite1979 on 2012-10-18
This thread has deviated so much from my original problem, I think it's time to call it "solved." I was able to install steam by going into winecfg and disabling dwrite.dll in the libraries tab. I then ran into an issue with GLX not working, so I stopped lightdm and did "sudo apt-get remove nvidia-current" then I installed the Nvidia driver using the script, and it appears to be working fine so far. I still can't play half-life or half-life2, but that's for another thread. Thanks for all of the help, guys.

---

