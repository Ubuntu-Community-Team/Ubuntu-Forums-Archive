---
title: "Bryce 5.5"
date: 2008-02-13
forum: Wine
---

### Post by JordanII on 2008-02-13
I am trying to install Bryce 5.5 under wine in Xubuntu Gutsy Gibbon. I get this message when I try to run it:

```
jordan@jordan-desktop:~$ wine '/home/jordan/.wine/drive_c/Program Files/DAZ/Bryce 5.5/Bryce55.exe'
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\DAZ\\Bryce 5.5\\B55Axiom.dll") not found
err:module:import_dll Library B55Axiom.dll (which is needed by L"C:\\Program Files\\DAZ\\Bryce 5.5\\Bryce55.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\DAZ\\Bryce 5.5\\B55Axiom.dll") not found
err:module:import_dll Library B55Axiom.dll (which is needed by L"C:\\Program Files\\DAZ\\Bryce 5.5\\B55ImageIO.dll") not found
err:module:import_dll Library B55ImageIO.dll (which is needed by L"C:\\Program Files\\DAZ\\Bryce 5.5\\Bryce55.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\DAZ\\Bryce 5.5\\Bryce55.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\Program Files\\DAZ\\Bryce 5.5\\Bryce55.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\DAZ\\Bryce 5.5\\Bryce55.exe" failed, status c0000135
jordan@jordan-desktop:~$ 
```

According to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1139&iTestingId=3068](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1139&iTestingId=3068) it should work. What should I do? Thanks! :)

---

### Post by FrozenFox on 2008-02-13
Are you using an old version? type wine --version in the terminal/console. iIf it's not 0.9.55, it's out of date, and the last comment on there says the newest one (at the time it was written) works, so I imagine it might work on 55. Please try that. Search for wine 0.9.55 in these forums, and I responded to one of them with a link to the .deb file.

Edit: found the post i was referring to.

[http://ubuntuforums.org/showthread.php?t=693917](http://ubuntuforums.org/showthread.php?t=693917)

---

### Post by JordanII on 2008-02-14
> **FrozenFox said:**
> Are you using an old version? type wine --version in the terminal/console. iIf it's not 0.9.55, it's out of date, and the last comment on there says the newest one (at the time it was written) works, so I imagine it might work on 55. Please try that. Search for wine 0.9.55 in these forums, and I responded to one of them with a link to the .deb file.

Edit: found the post i was referring to.

[http://ubuntuforums.org/showthread.php?t=693917](http://ubuntuforums.org/showthread.php?t=693917)

Thanks! I'll have to give that a try. :)

---

### Post by pemur1 on 2008-02-19
Did you happen to get Bryce 5.5 running with Wine 0.9.55?

---

### Post by Ofek86 on 2008-08-28
Hello,

I am new here, but I tried installing finale 2006 on Ubuntu 8.04, anyhow I also got the error regarding import_dll Library MSVCP60.dll. 

To solve it, what needs to be done is the following, type MSVCP60.dll and you will be given the option to download it, after you do, simply drag and drop or move via command line if you are on linux, to the folder or place where it is requested, and WALLA, at least for me, problem solved.

---

