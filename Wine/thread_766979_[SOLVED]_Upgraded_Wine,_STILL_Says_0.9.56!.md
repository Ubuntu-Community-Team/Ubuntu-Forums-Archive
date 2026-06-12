---
title: "[SOLVED] Upgraded Wine, STILL Says 0.9.56!"
date: 2008-04-25
forum: Wine
---

### Post by randy78 on 2008-04-25
Hello all...

I noticed this in Gutsy but just brushed it off, but now that it's continuing in Hardy, I would like to know what's going on and more importantly, how to remedy the situation.

I have installed every Wine release since 0.9.56, including the newest version today, only to run 'wine --version' in a terminal and have it come back saying 0.9.56.

I also ran Configure Wine, and checked the About section and it says the same thing...

Any help on how to correct this?

Thanks and Take Care

---

### Post by FrozenFox on 2008-04-25
* How are you installing? Synaptic, console command?
* Are you using the official hardy repos or the winehq repos?
* Are you setting wine in synaptic to "completely remove" as opposed to just remove? If not, I'd suggest trying that. If that doesn't help, I'd wager the version of wine in your repos is out of date, and please provide the contents of /etc/apt/sources.list and check the /etc/apt folder and subfolders for the wine source list.

---

### Post by Eck on 2008-04-26
Try running:

wineprefixcreate

after wine upgrades. It updates the wine registry to use the newer files and reloads with the newer settings.

---

### Post by randy78 on 2008-04-29
Sorry for the super late reply and thanx for the tip...

I just started a new job that has me up before dawn and it's taking some time to get adjusted!

I'll give it a shot and report back ;)

Take Care

Edit:

I just ran that command and this is the output I got:

randy@ubuntu:~$ wineprefixcreate
preloader: Warning: failed to reserve range 00000000-60000000
Warning: could not find DOS drive for current working directory '/home/randy', starting in the Windows directory.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:iphlpapi:NotifyAddrChange (Handle 0x7ca5b9f8, overlapped 0x7ca5b9dc): stub
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:shell:DllCanUnloadNow stub
err:qmgr:register_server register_service failed: 1073
/home/randy/.wine updated successfully.
randy@ubuntu:~$ wine --version
preloader: Warning: failed to reserve range 00000000-60000000
wine-0.9.56

---

### Post by cogadh on 2008-04-29
Fix for the memory reserve error:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

As for your problem updating, if your system and the Wine "About" page both report version 0.9.56, then that is the version that you must have. Running wineprefixcreate won't change that. All that command does is update your .wine directory and re-register any customizations you have made to the Wine registry. The Wine version is not included in your .wine directory or the registry.

The first thing I would do is run Synaptic and search for Wine, then check to see if you have forced the 0.9.56 version, which will prevent you from installing newer versions.

---

### Post by randy78 on 2008-04-29
Thanx!

I'll give it a shot ;)

Edit:

Gave it a go and here is the output:

randy@ubuntu:~$ wineprefixcreate
Warning: could not find DOS drive for current working directory '/home/randy', starting in the Windows directory.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7ca5b9f8, overlapped 0x7ca5b9dc): stub
fixme:shell:DllCanUnloadNow stub
err:qmgr:register_server register_service failed: 1073
/home/randy/.wine updated successfully.
randy@ubuntu:~$ wine --version
wine-0.9.56

---

### Post by randy78 on 2008-04-29
Alright...

Synaptic is saying that version 0.9.60 is installed and is the latest version...

Crazy, eh? :D

I did install 0.9.56 from source, but installed every other version from the repositories...

Take Care

---

### Post by Gunman1982 on 2008-04-29
I guess your installation from the source put the wine binary in /usr/local/bin and the repos installation in /usr/bin

try to execute:
/usr/local/bin/wine --version
and
/usr/bin/wine --version

then just the one which says 0.9.56

---

### Post by randy78 on 2008-04-29
Gunman1982, 

As per your instructions:

randy@ubuntu:~$ /usr/local/bin/wine --version
wine-0.9.56
randy@ubuntu:~$ /usr/bin/wine --version
wine-0.9.60

Whoo!
Progress!

Thanks a ton :D

How do I remove the faulty version?

---

### Post by Gunman1982 on 2008-04-29
sudo rm /usr/local/bin/wine

You are welcome

---

### Post by randy78 on 2008-04-29
Awesome

Thanx for all the help!

Went to mark as solved and the link disappeared! 

Randy

---

