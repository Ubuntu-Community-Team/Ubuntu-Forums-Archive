---
title: "Oracle 10g R2 installation failure"
date: 2006-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by gbevin on 2006-01-06
Hi, I'm trying to install Oracle 10g R2 (10.2.0.1.0) Enterprise/Standard Edition for Linux x86-64 on Breezy for an AMD 64 cpu machine. I followed all the installation steps in the official installation guide, when I run the installer, I get this error though:

> Preparing to launch Oracle Universal Installer from /tmp/OraInstall2006-01-07_02-08-01AM. Please wait ...oracle@ferrari:~/database$ Oracle Universal Installer, Version 10.2.0.1.0 Production
Copyright (C) 1999, 2005, Oracle. All rights reserved.

Exception java.lang.UnsatisfiedLinkError: /tmp/OraInstall2006-01-07_02-08-01AM/jre/1.4.2/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory occurred..
java.lang.UnsatisfiedLinkError: /tmp/OraInstall2006-01-07_02-08-01AM/jre/1.4.2/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at oracle.sysman.oii.oiif.oiifm.OiifmGraphicInterfaceManager.<init>(OiifmGraphicInterfaceManager.java:222)
        at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.createInterfaceManager(OiicSessionInterfaceManager.java:193)
        at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.getInterfaceManager(OiicSessionInterfaceManager.java:202)
        at oracle.sysman.oii.oiic.OiicInstaller.getInterfaceManager(OiicInstaller.java:436)
        at oracle.sysman.oii.oiic.OiicInstaller.runInstaller(OiicInstaller.java:926)
        at oracle.sysman.oii.oiic.OiicInstaller.main(OiicInstaller.java:866)
Exception in thread "main" java.lang.NoClassDefFoundError
        at oracle.sysman.oii.oiif.oiifm.OiifmGraphicInterfaceManager.<init>(OiifmGraphicInterfaceManager.java:222)
        at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.createInterfaceManager(OiicSessionInterfaceManager.java:193)
        at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.getInterfaceManager(OiicSessionInterfaceManager.java:202)
        at oracle.sysman.oii.oiif.oiifm.OiifmAlert.<clinit>(OiifmAlert.java:151)
        at oracle.sysman.oii.oiic.OiicInstaller.runInstaller(OiicInstaller.java:984)
        at oracle.sysman.oii.oiic.OiicInstaller.main(OiicInstaller.java:866)


I checked, and the libXp.so.6 library is present in /usr/lib.  The output of ldconfig also lists the library. I also tried adding the dir to LD_LIBRARY_PATH.

Has anybody got an idea about how to solve this and get the installer to run? Thanks for the help.

---

### Post by lnxpwr on 2006-01-08
hi,
did you check all the prerequisits (/etc/sysctl.conf, /etc/security/limits.conf) and the neccessary components ? 
make sure you have installed the following (works at my breezy):
linux-headers, linux-sources, gcc, make, binutils, lesstif2, libc6, libstdc++5, libc6-dev, rpm
than start the runInstaller with   <  ./runInstaller -ignoreSysPrereqs  >
greetinx
pete

---

### Post by gbevin on 2006-01-08
Hi Pete,

thanks for your reply. I'm sure I carefully followed everything that needs to be setup in /etc/sysctl.conf and /etc/security/limits.conf. I also installed all the packages you suggest, but to no avail, I still get the same errors.

Are you sure you're using the 64 bit version of Breezy and the 64 bit version of Oracle 10g R2?

Best regards,

Geert

---

### Post by lnxpwr on 2006-01-08
Hi Geert,
yes, I used the 64 bit version, but the first beta download (from oracle) didn't worked (also can't get runInstaller to run). So I got a new one which works fine from the first klick (...because the prereqs are set ). The machine was reinstalled again after this test, but I'll try to find the url I downloaded it from for you.
Greetinx
Pete

---

### Post by gbevin on 2006-01-08
Hi Pete, thanks a lot for the follow-up.

I made some progress, I downloaded the i386 version of the libxp6 and libx11 libraries from [http://packages.ubuntu.com](http://packages.ubuntu.com) (I took the amd64 version too to be able to restore later).

Then I installed the i386 versions like this:
> sudo dpkg -i --force-architecture libxp6_6.8.2-11ubuntu1_i386.deb
sudo dpkg -i --force-architecture libx11-6_6.2.1+cvs.20050722-8_i386.deb


After that the installer runs without any problems. It's currently busy installing the database, so I can't report about general success but at least I got it to start.

Afterwards the previous libraries should be restored with:
> sudo dpkg -i libx11-6_6.2.1+cvs.20050722-8_amd64.deb
sudo dpkg -i libxp6_6.8.2-11ubuntu1_amd64.deb

---

### Post by gbevin on 2006-01-08
Damn, I'm stuck again, this time it fails during the linker phase of the RDBMS binary:
> INFO: gcc -m32 -o /u01/app/oracle/product/10.2.0/db_1/rdbms/lib/extproc32 -L/u01/app/oracle/product/10.2.0/db_1/rdbms/lib32/ -L/u01/app/oracle/product/10.2.0/db_1/lib32/ -L/u01/app/oracle/product/10.2.0/db_1/lib32/stubs/   /u01/app/oracle/product/10.2.0/db_1/rdbms/lib32/hormc.o  /u01/app/oracle/product/10.2.0/db_1/rdbms/lib32/defopt.o  /u01/app/oracle/product/10.2.0/db_1/rdbms/lib32/homts.o                 -lagtsh -lpls10  -lplp10 -lpthread  -lclntsh -lsnls10 -lnls10  -lcore1
0 -lsnls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lxml1
INFO: 0 -lcore10 -lunls10 -lsnls10 -lnls10 -lcore10 -lnls10 /u01/app/oracle/product/10.2.0/db_1/lib32/libgeneric10.a   `cat /u01/app/oracle/product/10.2.0/db_1/lib32/sysliblist` -Wl,-rpath,/u01/app/oracle/product/10.2.0/db_1/lib -lm    `cat /u01/app/oracle/product/10.2.0/db_1/lib32/sysliblist` -ldl -lm
  -L/u01/app/oracle/product/10.2.0/db_1/lib  -lvsn10

INFO: make[1]: Leaving directory `/u01/app/oracle/product/10.2.0/db_1/rdbms/lib'

INFO: /u01/app/oracle/product/10.2.0/db_1/lib32//libagtsh.so: undefined reference to `nnfyboot'
collect2: ld returned 1 exit status
make[1]: *** [/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/extproc32] Error 1
make: *** [extproc32] Error 2

INFO: End output from spawned process.
INFO: ----------------------------------
INFO: Exception thrown from action: make
Exception Name: MakefileException
Exception String: Error in invoking target 'all_no_orcl' of makefile '/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/ins_rdbms.mk'. See '/u01/app/oracle/oraInventory/logs/installActions2006-01-08_09-19-22PM.log' for details.
Exception Severity: 1

This is quite a setback as there's almost no info about this that google returns :-(

---

### Post by mindead on 2006-01-08
I think I have the same problem (not sure 'cause I'm using the graphical installation interface) and it's saying can't find the "/usr/bin/make" command. However, I'm on a 32 bits arch.

thanks

---

### Post by mindead on 2006-01-08
OK, I resolved my previous issue. (missing package, no comment :???: )

but now I'm stuck on this error message:

```

INFO:  - Linking tg4pwd utility

INFO: rm -f /opt/oracle/oracle/product/10.2.0/db/rdbms/lib/tg4pwd

INFO: gcc -o /opt/oracle/oracle/product/10.2.0/db/rdbms/lib/tg4pwd -L/opt/oracle/oracle/product/10.2.0/db/rdbms/lib/ -L/opt/oracle/oracle/product/10.2.0/db/lib/ -L/opt/oracle/oracle/product/10.2.0/db/lib/stubs/ -L/usr/lib -lirc   /opt/oracle/oracle/product/10.2.0/db/rdbms/lib/tg4pwd.o	 /opt/oracle/oracle/product/10.2.0/db/rdbms/lib/defopt.o  /opt/oracle/oracle/product/10.2.0/db/rdbms/lib/homts.o		  -lagtsh -lpls10  -lplp10   -lclntsh -lsnls10 -lnls10  -lcore10 -lsnls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lxml10 -l
INFO: core10 -lunls10 -lsnls10 -lnls10 -lcore10 -lnls10 /opt/oracle/oracle/product/10.2.0/db/lib/libgeneric10.a   `cat /opt/oracle/oracle/product/10.2.0/db/lib/sysliblist` -Wl,-rpath,/opt/oracle/oracle/product/10.2.0/db/lib -lm    `cat /opt/oracle/oracle/product/10.2.0/db/lib/sysliblist` -ldl -lm   -L/opt/oracle/oracle/product/10.2.0/db/lib  -lvsn10

INFO: /opt/oracle/oracle/product/10.2.0/db/lib//libagtsh.so: undefined reference to `nnfyboot'
collect2: ld returned 1 exit status
make: *** [/opt/oracle/oracle/product/10.2.0/db/rdbms/lib/tg4pwd] Error 1

INFO: End output from spawned process.
INFO: ----------------------------------
INFO: Exception thrown from action: make
Exception Name: MakefileException
Exception String: Error in invoking target 'utilities ctx_on' of makefile '/opt/oracle/oracle/product/10.2.0/db/rdbms/lib/ins_rdbms.mk'. See '/opt/oracle/oraInventory/logs/installActions2006-01-08_03-43-06PM.log' for details.
Exception Severity: 1


```

---

### Post by lnxpwr on 2006-01-09
Hi Mindead,
was the missing packages  glibc and glibc-devel ?
greetinx
p.

---

### Post by mindead on 2006-01-09
Here is the [guide]("http://www.hicham.cliranet.com/slashroot/index.php?2005/12/01/25-installation-d-oracle-10g-sur-une-ubuntu-brezzy-badger")
 I found to help me through this task.

It is really complete for the basic installation.
You will also find a short list of required libraries at the beginning.

Hope this will help you as much as it helped me.

---

### Post by Nicolas Jouanin on 2006-01-29
Hi,

I'm still sticked with that installation problem you had:
```

INFO: gcc -o /u01/app/oracle/product/10.2.0/db102/rdbms/lib/tg4pwd -L/u01/app/oracle/product/10.2.0/db102/rdbms/lib/ -L/u01/app/oracle/product/10.2.0/db102/lib/ -L/u01/app/oracle/product/10.2.0/db102/lib/stubs/ -L/usr/lib -lirc   /u01/app/oracle/product/10.2.0/db102/rdbms/lib/tg4pwd.o    /u01/app/oracle/product/10.2.0/db102/rdbms/lib/defopt.o  /u01/app/oracle/product/10.2.0/db102/rdbms/lib/homts.o                  -lagtsh -lpls10  -lplp10   -lclntsh -lsnls10 -lnls10  -lcore10 -lsnls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lxml10 -l
INFO: core10 -lunls10 -lsnls10 -lnls10 -lcore10 -lnls10 /u01/app/oracle/product/10.2.0/db102/lib/libgeneric10.a   `cat /u01/app/oracle/product/10.2.0/db102/lib/sysliblist` -Wl,-rpath,/u01/app/oracle/product/10.2.0/db102/lib -lm    `cat /u01/app/oracle/product/10.2.0/db102/lib/sysliblist` -ldl -lm   -L/u01/app/oracle/product/10.2.0/db102/lib  -lvsn10

INFO: /
INFO: u01/app/oracle/product/10.2.0/db102/lib//libagtsh.so: rÃ©fÃ©rence indÃ©finie vers Â« nnfyboot Â»

INFO: collect2:
INFO: ld a retournÃ© 1 code d'Ã©tat d'exÃ©cution

INFO: make: *** [/u01/app/oracle/product/10.2.0/db102/rdbms/lib/tg4pwd] Erreur 1

INFO: ArrÃªter la sortie |  partir du processus gÃ©nÃ©rÃ© dynamiquement.
INFO: ----------------------------------
INFO: Exception provoquÃ©e par l'action : make
Nom de l'exception : MakefileException
ChaÃ®ne de l'exception : Erreur lors de l'appel de la cible 'utilities ctx_on' du fichier Make '/u01/app/oraacle/product/10.2.0/db102/rdbms/lib/ins_rdbms.mk'. Pour plus de dÃ©tails, reportez-vous |  '/u01/app/oracle//
oraInventory/logs/installActions2006-01-29_04-36-19PM.log'.
GravitÃ© de l'exception : 1


```

I checked the needed package ...

Did you find THE final answer to that problem ?

Thanks,

Nicolas.

---

### Post by Ben Ballard on 2006-02-09
I'm new to these forums, but have been following this thread with interest.  I've been trying to install Oracle on Ubuntu 5.10 for amd64, and I've reached the conclusion that this won't work.

I first tried to install ORacle 10g XE for Linux, thinking that would be simpler.  There is another thread in these forums that has discussed converting the .rpm to a .deb using alien, and then what additional steps are needed.  Unfortunatel, I found that this simply wouldn't work because it simply wasn't compiled to run on a 64-bit linux.

Next I tried Oracle 10g R2 Enterprise Edition.  The comments in this thread have been very helpful, but I am giving up.  The comments on this debian forum have convinced me this can't be done, at least not without great difficulty:
[http://lists.debian.org/debian-amd64/2005/10/msg00804.html](http://lists.debian.org/debian-amd64/2005/10/msg00804.html)

I was getting the error related to libXp.so.6, which prevented the java installer from running.  I was able to get around that following the instructions to download the .deb files for libxp and libx11 for i386, and install them using force-architecture.  I found this enables the installer, but breaks other things on my system.  So you have to install the i386 versions with force-architecture, then run the installer, and then install the amd64 versions again, otherwise, you can't even log out and log back in to X Windows.

But all of this was moot because when the installer reached 65%, I got this error:
Error in invoking target "install" of make file '/oracle/oracle/product/10.2.0/db_1/ctx/lib/ins_ctk.mk

From the debian list I linked above, it seems that running Oracle 10g on Ubuntu or Debian for AMD64 is just a bad idea.  Since Red Hat and SuSE use lib64 for 64-bit libraries and lib for 32-bit libraries, but Ubuntu and Debian are pure 64-bit, this will probably never work.

My next attempt will be to see if the Gnome configuration of OpenSuSE 10 is tolerable.  I'm quite attached to Ubuntu, so I'd rather not switch, but I've used many distros in the past.  If I can't stand SuSE, then I'll probably try the 32-bit version of Ubuntu 5.10 and give this Oracle install one more try.

I don't need any help, but just thought I'd post my experience in case anyone else out there is trying Oracle on Ubuntu for amd64.  If anyone has been successful, please let me know, but I'm assuming at this point that it won't work, at least until Oracle gets around to supporting Debian.

Best regards,
Ben

---

### Post by Ben Ballard on 2006-02-09
I meant to also mention, I tried the amd64 version of Oracle 10g R2.  So the probabl isn't that I tried to run 32-bit Oracle on Ubuntu for amd64.  Everything was "for amd64", but Oracle seems to expect a mixed 32/64 bit environment, since that's how SuSE and Red Hat have done 64-bit, not pure 64 like Debian and Ubuntu.

Hopefully Red Hat and SuSE will eventually catch up and move to a pure 64-bit implimentation, and then Oracle will revise the database to work with only 64-bit, and then we might have more luck running it on Ubuntu. ;)

Someone please tell me if they were successful with Oracle for amd64 on Ubuntu! ;)

---

### Post by mmilkin on 2008-03-28
amb64 install is a nightmare however it is duable you can force_archetecture if you needto there are some libs i needed to install but in the end i packed 64bit up and went with 32 cause oracle simply would not work.  If you are installing 10g do not try to run the 10.2.0.1 apply all the patches before attempting to create a db.  It helped fix some of my db creation issues

---

