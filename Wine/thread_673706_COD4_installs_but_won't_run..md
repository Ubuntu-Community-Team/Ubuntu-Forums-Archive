---
title: "COD4 installs but won't run."
date: 2008-01-20
forum: Wine
---

### Post by logicalyrandom on 2008-01-20
I just switched to Ubuntu a few days ago, and ran into a few bugs getting a few games to work with wine. 
I'm running the latest version of Wine (just downloaded it today), and the first thing I went to install was CoD4. I popped the CD in, ran the setup.exe, and typed 
```
env WINEPREFIX="/home/robert/.wine" wine "C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe"
``` into the terminal, and got this result: 

```
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:module:import_dll Library D3DX9_34.DLL (which is needed by L"C:\\Program Files\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe" failed, status c0000135

```


I also tried running the game from the menue to see what would happen to no avail. 
I've got a Nvdia Geforce 7300 for my graphics card, and haven't changed any of the defaults for Wine.

Thanks in advance

---

### Post by upbeat.linux on 2008-01-24
A bit of reading, but try:

[http://www.linuxquestions.org/questions/linux-games-33/call-of-duty-4-on-linux-597725/](http://www.linuxquestions.org/questions/linux-games-33/call-of-duty-4-on-linux-597725/)

or

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4&back=HOWTO+INDEX+Wine+Games)

---

