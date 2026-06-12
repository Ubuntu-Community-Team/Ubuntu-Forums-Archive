---
title: "[SOLVED] wine errors, regedit, winecfg +others"
date: 2008-06-01
forum: Wine
---

### Post by no1cares on 2008-06-01
i get this error when i try to run some thing through command line with wine...
for example if i type in "winecfg"
```
paul@paul-laptop:~$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```
it does open up the window after all that crap,
when i try "regedit"
```
paul@paul-laptop:~$ regedit
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```
it then opens up after that..
when i try starcraft.. i get the same things but more, i have a separate post on my starcraft battle.net problems... here is the link.  
[http://ubuntuforums.org/showthread.php?t=814685](http://ubuntuforums.org/showthread.php?t=814685)

im thinking if i can fix those problems maybe my b.net will work... also about the slowness......this website [http://appdb.winehq.org/objectManage...ersion&iId=149](http://appdb.winehq.org/objectManage...ersion&iId=149) (scroll down) has a "cure for slowness" which links you here. [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) can someone please explain what to do for this???

Found under HKEY_CURRENT_USER/Software/Wine/Direct3D using regedit) 
i can go all the way to the /wine/ but there is no direct3d there... anyone know what to do...!!! please help

---

### Post by cogadh on 2008-06-01
You can get rid of those preloader errors by using the instructions here:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

As for the registry edits you are trying to do, you need to create the Direct3D key and all of the values underneath it yourself.

Also, Battle.net doesn't actually work fully with Wine yet. It is on the list of thing that they wanted to fix before the 1.0 release, but I'm not sure that is actually going to happen.

---

