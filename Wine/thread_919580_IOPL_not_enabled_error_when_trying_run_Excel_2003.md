---
title: "IOPL not enabled error when trying run Excel 2003"
date: 2008-09-14
forum: Wine
---

### Post by Czubek on 2008-09-14
Hi.
I'm trying to run MS Excel 2003 from windows partition and I get error:

"IOPL not enabled"

I'm using:

wine-1.1.4
ubuntu 8.04.1

I have: 
WINEPREFIX="/home/czubek/.wine" in /etc/enviroment

It looks [here]("http://ubuntuforums.org/showpost.php?p=4885918&postcount=12") like winetricks should help but I get another strange error with it:

sh winetricks dcom98
rm: nie mo&#380;na usun&#261;&#263; `/home/czubek/.wine/drive_c/winetrickstmp/set-winver.reg': Permission denied
Setting Windows version to win98
winetricks: 1510: cannot create /home/czubek/.wine/drive_c/winetrickstmp/set-winver.reg: Permission denied
Executing wine regedit /home/czubek/.wine/drive_c/winetrickstmp/set-winver.reg
Executing wine /home/czubek/.winetrickscache/DCOM98.EXE
Using native,builtin override for following DLLs: ole32 oleaut32 rpcrt4
winetricks: 1510: cannot create /home/czubek/.wine/drive_c/winetrickstmp/override-dll.reg: Permission denied
winetricks: 1510: cannot create /home/czubek/.wine/drive_c/winetrickstmp/override-dll.reg: Permission denied
winetricks: 1510: cannot create /home/czubek/.wine/drive_c/winetrickstmp/override-dll.reg: Permission denied
winetricks: 1510: cannot create /home/czubek/.wine/drive_c/winetrickstmp/override-dll.reg: Permission denied
Executing wine regedit /home/czubek/.wine/drive_c/winetrickstmp/override-dll.reg
regedit: File not found "/home/czubek/.wine/drive_c/winetrickstmp/override-dll.reg" (2)
Note: command 'wine regedit /home/czubek/.wine/drive_c/winetrickstmp/override-dll.reg' returned status 1.  Aborting.

Someone know what's wrong?

Thanks in advance.

---

