---
title: "sketchup + wine 1.6 problem"
date: 2013-06-25
forum: Wine
---

### Post by LudoTW on 2013-06-25
Hello,

I have just installed ubuntu 13.04. 
I then did:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.5
```

First for some reason i ended up with wine 1.6
```
 wine --version
wine-1.6-rc3
```

Then when trying to install sketchup 8 this is what I got in the installer window:

```
Prerequisite check for system component Microsoft Windows failed with the following error message:
"Installation of SketchUp requires Windows XP Professional x64 Service Pack 2 or later."
See the setup log file located at 'C:\users\ludo\Temp\VSDeb2b.tmp\install.log' for more information.
```

And in the terminal:
```
wine SketchUpWEN.exe 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
ludo@ludo-UX32VD:~/Downloads$ p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
```

What is wrong?

Ludo

---

### Post by dino99 on 2013-06-25
so check with winecfg that wine is set to use at least xp (better set it to w7)

---

### Post by LudoTW on 2013-06-25
dino99 thanks for the reply. It was set to XP already. But following your advice to set it to win7 did the trick.

---

