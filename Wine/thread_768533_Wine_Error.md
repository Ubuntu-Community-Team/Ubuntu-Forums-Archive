---
title: "Wine Error"
date: 2008-04-26
forum: Wine
---

### Post by bossa on 2008-04-26
Hi All
Just installed Hardy and installed the latest Wine from Wine site and I get this when trying to run winecfg. Also if I try to install a program using Wine I get :

setup was unable to create the directory "C:\windows\is-OKQD4.tmp". Error 3:Path not found\


steve@steve-desktop:~$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
steve@steve-desktop:~$


Any Ideas ?

---

### Post by happyhamster on 2008-04-26
Take a look at:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

Good luck.

---

### Post by WeeManDan on 2008-04-26
Happyhamster got there first! I had the same problem yesterday and this cleared it right up

---

### Post by bossa on 2008-04-26
I'm getting this message now after following the instructions from the link :confused:

steve@steve-desktop:~$ winecfg
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
err:winecfg:load_drives GetVolumeInformation() for 'C:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'C:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
steve@steve-desktop:~$

---

### Post by bossa on 2008-04-26
OK I seem to have found a fix .I used this in terminal :

mv ~/.wine{,.backup}
wineprefixcreate 

Got it from this thread  [http://forum.winehq.org/viewtopic.php?p=3176&sid=b7f879da3574d1c1544be97031bfa0c0](http://forum.winehq.org/viewtopic.php?p=3176&sid=b7f879da3574d1c1544be97031bfa0c0)
All seems well now

---

### Post by coolkid5 on 2008-04-26
The report for that preloader bug says it's being fixed.  Perhaps it will go away in 0.9.61

---

