---
title: "Age of Mythology under Wine, Ubuntu"
date: 2008-11-30
forum: Wine
---

### Post by Vorac on 2008-11-30
I am trying to install Age of Mythology, but get this output. As is SHOULD work :
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1979](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1979)
, I can't understand where's my mistake. Help!

```
s613n7157@adski-desktop:~$ cd /
s613n7157@adski-desktop:/$ cd /home/s613n7157/.wine/drive_c/Age
s613n7157@adski-desktop:~/.wine/drive_c/Age$ ls
00000000.016;1  AR505ENU.EXE;1  EBUEULA.DLL;1   INSTALL.TXT;1   README.RTF;1
00000000.256;1  AUTORUN.INF;1   EULA.RTF;1      INSTMSIA.EXE;1  SECDRV.SYS;1
00000001.TMP;1  CAMPAIGN        GEORGIAB.TTF;1  INSTMSIW.EXE;1  SETUPENU.DLL;1
AOM             DIRECTX         GEORGIAI.TTF;1  PATCH           setup.exe
AOM_D1.iso      DRVMGT.DLL;1    GEORGIA.TTF;1   PIDGEN.DLL;1    UPDATE
AOM_D2.iso      DX81BQFE        GEORGIAZ.TTF;1  PPEULA.TXT;1    WARRANTY.RTF;1
s613n7157@adski-desktop:~/.wine/drive_c/Age$ su
Password: 
root@adski-desktop:/home/s613n7157/.wine/drive_c/Age# wine setup.exe
fixme:font:WineEngRemoveFontResourceEx :stub
root@adski-desktop:/home/s613n7157/.wine/drive_c/Age# Sharing violation



```

PS: Btw this is the unzipped content of the .iso file. Maybe I should mount that somehow?

---

### Post by PocketDog on 2008-11-30
You don't want to be running Wine in a root shell. That can be Bad.

---

### Post by Vorac on 2008-11-30
Regardless, the result is still the same :(

---

### Post by PocketDog on 2008-11-30
[http://www.codeweavers.com/compatibility/browse/name/?app_id=764](http://www.codeweavers.com/compatibility/browse/name/?app_id=764) It looks promising. I've got AoM myself actually. I'll have a fiddle with it tonight after work, and report back if I can help.

---

### Post by Vorac on 2008-11-30
I cant believe it. I formated the whole drive; reinstalled Ubuntu, and then, with the system sterile, tried to Wine the setup file(downloaded it from torrents, unzipped the .iso, an renamed it from SETUP.EXE;1 to setup.exe). The SAME "Sharing violation".

---

### Post by PocketDog on 2008-11-30
Ok, I got it. Same error as you too. I installed from CD but a mounted ISO should do the same thing. Get [ MFC42.DLL ](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42) - unzip it and put it in your .wine/drive_c/windows/system32 folder. Install the game by typing (in my case) ```
/media/cdrom0/SETUP.EXE
``` Don't cd to the setup disc/directory before entering that. It should install with no issues. Worked for me! Hope that helps

---

### Post by PocketDog on 2008-12-01
Any joy? I don't know if you'd have seen my edit

---

### Post by macabe on 2008-12-14
-Don't know if it worked for the OP, but it certainly got me further along.  Though I have encountered new, strange problems once again.

Thanks for the help PocketDog

---

