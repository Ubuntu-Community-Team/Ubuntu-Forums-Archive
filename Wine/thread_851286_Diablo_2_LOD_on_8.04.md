---
title: "Diablo 2 LOD on 8.04"
date: 2008-07-06
forum: Wine
---

### Post by sdlyr8 on 2008-07-06
Hey everyone, I recently came across my old Diablo 2 disk and thought I'd install it and start playing it again. I'm running ubuntu 8.04 and when I try to install it via WINE all I get is 
> $ wine /media/cdrom0/install.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb7ce525b


I am not a new ubuntu user but i rarely use WINE so I'm not too sure how to even diagnose the problem. Has anyone else encountered the same problem or have any idea how to fix it?

Thanks in advance!

---

### Post by The Unmaker on 2008-07-06
> **sdlyr8 said:**
> Hey everyone, I recently came across my old Diablo 2 disk and thought I'd install it and start playing it again. I'm running ubuntu 8.04 and when I try to install it via WINE all I get is 


I am not a new ubuntu user but i rarely use WINE so I'm not too sure how to even diagnose the problem. Has anyone else encountered the same problem or have any idea how to fix it?

Thanks in advance!


Hi there,

Seems there is a memory handling problem with Wine. A similar problem happens in DOS when the EMS memory isn't set up properly. What version of WINE are you using? Have you gotten other Windows apps to work?

Perhaps uninstall and reinstalling wine from winehq and not from the repositories (depending on the repository, sometimes the versions aren't the newest or are usually broken). Make sure you have the most recent stable version of Wine.

---

### Post by sdlyr8 on 2008-07-06
Ok I uninstalled and re-installed from winehq and after what seemed like forever, the installation finished. I tried wine /media/cdrom0/install.exe again and this time i got. 
> err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb7d76d28


Now what?

---

### Post by sdlyr8 on 2008-07-07
Ok I'm not sure what I did but now I get...

> err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

I searched google but no one seems to have the answer.

---

### Post by The Unmaker on 2008-07-08
> **sdlyr8 said:**
> Ok I'm not sure what I did but now I get...



I searched google but no one seems to have the answer.

I'm definitely not an expert here (and you really have to be to know a thing or two about exception codes), but it seems to me like Wine is seg-faulting or there is something in your system that is making Wine crash. 

I don't think I can provide any good suggestions... Perhaps run a memtest and see that everything is running smoothly and perhaps recompile the Wine code. I would also try to install some other windows app and see if it gives you a similar error. It could be the way it is detecting the CD (perhaps bash ties it up and it goes into some infinite loop?). Hopefully someone will have an answer. Best...

---

### Post by karth on 2008-07-08
edit: my mistake, bad answer

---

### Post by davidpeace on 2008-07-08
Did you try seeing if there was a "c/" drive? Open "configure wine" and flip through tabs. There should be an option on one of them to automatically detect drives. (I'm at a public computer at the moment, but try this.)

---

### Post by sdlyr8 on 2008-07-08
Ok.. today's error message is..

> root@stephen-desktop:/usr/bin/wine-1.0# ./wine "D:\\install.exe"
err:module:attach_process_dlls "binkw32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"D:\\install.exe" failed, status c0000005


I'm not sure what I did but now I get this. so far it keeps revolving around the "c0000005" status.

And I was not able to run 
> $ configure wine
I get command not found. I know older versions of wine had winecfg but wine 1.0 doesn't come with one. So I don't know. But I'm guessing since I can call it from the D drive, it is loaded. the cd drive does spin when i call it.

Also other win apps run fine. This is the first one I'm having an issue with.

---

### Post by karth on 2008-07-09
The command is ```
$ winecfg
```

---

### Post by darthmob on 2008-07-09
me and a friend of mine are currently playing diablo2 + lod via wine (those diablo3-trailers look really promising and we had to get it!).
the installation did not work out as we wanted it (corrupted files on the original disk (!) and the isos) and in the end we both installed it on our dualboot-windows, but play from ubuntu.

did you ever try _[playonlinux]("http://www.playonlinux.com/en/")_? it has got an installscript for both diablo2 and lod. I'm not sure how it works but it may be worth a try!

---

### Post by sdlyr8 on 2008-07-09
> **darthmob said:**
> me and a friend of mine are currently playing diablo2 + lod via wine (those diablo3-trailers look really promising and we had to get it!).
the installation did not work out as we wanted it (corrupted files on the original disk (!) and the isos) and in the end we both installed it on our dualboot-windows, but play from ubuntu.

did you ever try _[playonlinux]("http://www.playonlinux.com/en/")_? it has got an installscript for both diablo2 and lod. I'm not sure how it works but it may be worth a try!

I thought I was seeing light at the end of the tunnel.... but it was only a mirage! ](*,)
I downloaded and installed playonlinux and it opened fine. i hit install and loaded from the cd and it found the exes and everything... said it was starting to install and then the progress bar filled up and then stopped. said it finished. but no diablo files can be found in the .playonline folder and the terminal says... 
> ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
err:module:attach_process_dlls "binkw32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\d2l_Install.exe" failed, status c0000005

..back to square one i guess? it says something about the binkw32.dll which i did put in the system32 folder in the wine directory.. but still get the same message! this is really starting to tick me off..

---

### Post by The Unmaker on 2008-07-10
> **sdlyr8 said:**
> I thought I was seeing light at the end of the tunnel.... but it was only a mirage! ](*,)
I downloaded and installed playonlinux and it opened fine. i hit install and loaded from the cd and it found the exes and everything... said it was starting to install and then the progress bar filled up and then stopped. said it finished. but no diablo files can be found in the .playonline folder and the terminal says... 


..back to square one i guess? it says something about the binkw32.dll which i did put in the system32 folder in the wine directory.. but still get the same message! this is really starting to tick me off..

Linux is like that. I have domestic problems with it everyday. Don't give up. Be wary of those install scripts. Try inserting the cd (make sure the CD is mounted: i.e. when the CD icon appears on the desktop, right-click to get the menu, and select "mount" if it isn't already mounted), running winecfg, then selecting Autodetect from the Drives tab. Then try running the install normally by doing 

$wine /media/cdrom#/install.exe  Where # is the drive bay location (It helps by typing /media/ and after the "/" pressing tab, to see the available options. One of those will be the cdrom location).

Hopefully it's just a read/write issue and not a memory handling issue. Post back with any results/status changes.

---

