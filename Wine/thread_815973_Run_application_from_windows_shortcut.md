---
title: "Run application from windows shortcut"
date: 2008-06-02
forum: Wine
---

### Post by donkeyX on 2008-06-02
Hey Guys,

I am a peoplesoft developer and trying to use ubuntu as my desktop. Anyway, i am trying to run my peopletools software from a windows link on a network share. The problem is that i don't know how to get wine to open the link up of if this will even work. 

Thanks in advance ;)

---

### Post by karth on 2008-06-02
I don't know if launching a windows program installed in a real windows environment with wine is a good idea. Wine is designed to run in its own directory (typically ~/.wine), mimicing windows' architecture, but embedding its own dlls that are supposed to replace windows' ones. Chances are that what you are trying to do will fail...

Secondly, windows shortcuts should be replaced by shell scripts launching the wine command (hence requiring that you installed your soft in a wine dir). Windows shortcuts are text files caught by windows runtime because of their extension. It basically contains the path to the .exe and a few arguments.

Shell scripts launching Wine commands should read like:

```
wine PATH_TO_EXE
```

You should consider installing your software locally in a wine directory. If you don't want to, or can't, I will leave the matter for more experienced users to aswer.

---

### Post by cogadh on 2008-06-02
> **donkeyX said:**
> Hey Guys,

I am a peoplesoft developer and trying to use ubuntu as my desktop. Anyway, i am trying to run my peopletools software from a windows link on a network share. The problem is that i don't know how to get wine to open the link up of if this will even work. 

Thanks in advance ;)

Its been a while since I have dealt with anything from Oracle. Is the Peopletools product anything like their past products where everything is managed through a web-based interface? Or is Peopletools an actual software product that runs locally on your machine? If it is web-based, then you probably don't need Wine, just point your regular browser at the correct URL. If it is an actual executable, then you first need to map the network drive where the executable is found (i.e. where does that Windows shortcut you are trying to use point to), then add that mapped drive to Wine, then run the executable normally:
```
cd /path/to/executable
wine executable.exe
```

---

### Post by donkeyX on 2008-06-03
Thanks for the replies, and it is a client ide called PeopleTools 8.48. The installs are done on a network server and configured there so i might be able to find a copy of the actual tool and install/configure myself, but it would just be a lot easier to run the shortcuts that are provided ;). I will give the mapping a go tonight and see what happens.

Cheers dave

---

### Post by donkeyX on 2008-06-03
I ended up finding the peoplesoft application and trying to run it in wine but got the following message:


[email]don@pluto:~/.wine[/email]/drive_c/Program Files/client/winx86$ wine pside.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:module:attach_process_dlls "PSCMN.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\client\\winx86\\pside.exe" failed, status c0000005
[email]don@pluto:~/.wine[/email]/drive_c/Program Files/client/winx86$ wine pside.exe 
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:module:attach_process_dlls "PSCMN.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\client\\winx86\\pside.exe" failed, status c0000005


I have no idea where to go from here, but just know that all the dll's and required stuff should be in the path the application is running from. "should be" ;)

Cheers David

---

### Post by karth on 2008-06-03
As for the preloader bug, check here [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

I had this issue prior to updating to Wine 1.0RC2 (current is 1.0RC3). The newer versions are only available through repo for the newest ubuntu (hardy), but I guess you can either find a .deb for gutsy and older ubuntus, or compile it yourself.

Maybe solving this bug will also get rid of the dll errors...

---

### Post by donkeyX on 2008-06-03
Thanks for that, it is now much closer as the initial error is gone : 

don@pluto:~$ wine /home/binneyd/.wine/drive_c/Program\ Files/ptools_8.48.5/pside.exe
err:module:attach_process_dlls "PSCMN.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\ptools_8.48.5\\pside.exe" failed, status c0000005

Sorry if this is an obvious error for wine but i have never used it before. 

cheers dave

---

### Post by cogadh on 2008-06-03
You should "cd" to the application's install directory before running it, otherwise it might have trouble finding some of the necessary DLLs:
```
cd /home/binneyd/.wine/drive_c/Program\ Files/ptools_8.48.5
wine pside.exe
```
If you still get that DLL failure, then you might need to copy that DLL from an existing Windows machine and place it in Wine's system32 directory.

---

### Post by donkeyX on 2008-06-27
Hey Again,

I have tried placing the error dll "PSCMN.dll" into the path : 
 
/home/don/.wine/drive_c/windows/system32

but still get the error:

[email]don@pluto:~/.wine[/email]/drive_c/Program Files/ptools_8.48.5$ wine pside.exe 
err:module:attach_process_dlls "PSCMN.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\ptools_8.48.5\\pside.exe" failed, status c0000005

This dll is actually in the directory that i am running from so i am not sure what is going on?

Thanks in advance

---

### Post by donkeyX on 2008-09-03
bump, any more help on this topic as i would really hate to have to do vmware just to run this small app?

Cheers dave

---

