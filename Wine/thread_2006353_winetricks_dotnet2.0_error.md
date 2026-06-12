---
title: "winetricks dotnet2.0 error"
date: 2012-06-19
forum: Wine
---

### Post by Xplorer4x4 on 2012-06-19
I am running (Kubuntu)Precise and need to install wintracks dotnet2.0 but run in to a problem about running a 64 bit system.

From konsole:
> winetricks dotnet20
Executing w_do_call dotnet11
Executing load_dotnet11
------------------------------------------------------
This package does not work on a 64-bit installation
------------------------------------------------------
xplorer4x4@xplorer4x4-MS-7673:~/iso2god_v1.3.6-360h$ winetricks dotnet20
Executing w_do_call dotnet20
Executing load_dotnet20
Executing w_do_call fontfix
Executing load_fontfix
Setting Windows version to win2k
Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet20\set-winver.reg
Executing mkdir -p /home/xplorer4x4/.cache/winetricks/dotnet20
Executing unzip -o -q -d /home/xplorer4x4/.wine/dosdevices/c:/windows/syswow64 l_intl.zip
Executing mkdir -p /home/xplorer4x4/.cache/winetricks/dotnet20
Executing wine dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\xplorer4x4\\Temp\\IXP000.TMP\\" 00000000
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:advapi:LsaOpenPolicy ((null),0x33f31c,0x00000001,0x33f344) stub
fixme:advapi:LsaClose (0xcafe) stub
------------------------------------------------------
Note: command 'wine dotnetfx.exe' returned status 26.  Aborting.
------------------------------------------------------It launches the installer for dotnet2.0 but when I click next for the first time I get to the next screen and it says it failed to install since this is a 64 bit system. So I tried doing export WINEARCH=win32 but got a diffrent error when trying to run  winetricks dotnet20  again but I got a diffrent error this time:
wine cmd.exe /c echo '%ProgramFiles%' returned empty string

How can I fix this? I initally tried all of this under the repository version, but tried again under the latest wine version avaliable in the PPA and the steps are reproducable evrytime. How can I fix this?

---

### Post by Perfect Storm on 2012-06-19
Moved to wine forum.

---

### Post by Xplorer4x4 on 2012-06-19
> **Artificial Intelligence said:**
> Moved to wine forum.

Sorry about that. It's not visible from the forum index so I didn't realize there was a forum for wine.

---

### Post by ergo-proxy on 2012-06-19
Do export **WINEARCH**=win32  before creating a new wineprefix

---

### Post by Xplorer4x4 on 2012-06-19
> xplorer4x4@xplorer4x4-MS-7673:~$ export WINEARCH=win32
xplorer4x4@xplorer4x4-MS-7673:~$ export WINEPREFIX=$HOME/.new_wine 
xplorer4x4@xplorer4x4-MS-7673:~$ winetricks dotnet20
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------
xplorer4x4@xplorer4x4-MS-7673:~$ 

Did I miss anything?

---

### Post by ergo-proxy on 2012-06-19
Nope, it should be working. Make sure .new_wine doesnt exists prior creating a new prefix, after creating the prefix you might wish to run winecfg to set windows version you want. Finally, are you using wine ppa? Anyway, you can try to test any ddl with winetrics as they do work only with wine32.

---

### Post by Xplorer4x4 on 2012-06-19
Yep I am using Wine from the PPA. Acording to the wine wiki 1.3 is stable and 1.4 was not, but yet the ppa has 1.5. I assumed the wiki I was reading was simply out dated as it was quite a mess imo. Is 1.5 indeed stable?

I made sure .new-wine did not exist in my home dir first this time and here is what it got me this time:
> xplorer4x4@xplorer4x4-MS-7673:~$ export WINEARCH=win32
xplorer4x4@xplorer4x4-MS-7673:~$ export WINEPREFIX=$HOME/.new_wine 
xplorer4x4@xplorer4x4-MS-7673:~$ winecfg
wine: WINEARCH set to win32 but '/home/xplorer4x4/.new_wine' is a 64-bit installation.
xplorer4x4@xplorer4x4-MS-7673:~$ 


---

### Post by ergo-proxy on 2012-06-19
You got that message because your wineprefix already existed. You cant change the architecure of existing prefix. The latest "stable" wine version is 1.4.1 wile the latest dev version is 1.5.6 I would stick to dev version. As far as I remember the were some problems with older versions (1.3?) of wine tested on precisex64.

---

### Post by Xplorer4x4 on 2012-06-19
Thanks I didnt realize I needed to actually delete the dir itself. I assumed deleting the contents was sufficent. So dotnet20 is good, but how come when I try to install other versions of dotnet it always loads the installer for dotnet20? As far as I know dotnet frameworks are not backwards compatible are they?

---

### Post by ergo-proxy on 2012-06-19
Hmm I dont know if they are compatible backwards but .net doesnt run very smooth under wine, especially newer versions, check winehq db.

---

