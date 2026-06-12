---
title: "gconf error with 32 bit applications (swiftfox)"
date: 2009-01-30
forum: x86 64-bit Users
---

### Post by valmar on 2009-01-30
Dear all,

         I come to you again for help. But I hope this is the last time for some while. I installed manually swiftfox, which is a 32 bit application (even when you use the 64 bit package. It is just an optimized recompiling of firefox 32 bit ). WHen I start it, however, I get:


Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 2: IOR file '/tmp/gconfd-valerio/lock/ior' not opened successfully, no gconfd located: No such file or directory)


Now, gconf seems to be running when I do a 'ps -ef', even though the /tmp/gcond-valerio fodler does not exist. I googled for a solution and found that this is a common symptom of disk space running out. But this is not my case. I think what is happening is that the 32 bit application wants a 32 bit gconf running, not a 64 bit one. Is there some ia32- package that I can install to make it work?

Thanks in advance for your help

             Valerio

---

### Post by Yellow Pasque on 2009-01-30
The swiftfox program isn't looking in the correct place for the lock/ior file. As of Ubuntu Intrepid/8.10, gconf stores this in /home/<username>/.gconfd/, not the /tmp directory. You could report this issue to swiftfox.

You could also try working around it by making a symbolic link in /tmp
```
ln -s ~/.gconfd /tmp/gconfd-valerio
```

> Is there some ia32- package that I can install to make it work?You could use the getlibs script on the swiftfox binary to ensure it has the libs it requests. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by valmar on 2009-01-30
Uhmmm... I tried with the ldd command but all the libs are ok. No one is not found. I think the program does not depend on gconf, just wants it running

---

### Post by Yellow Pasque on 2009-01-30
The program is looking in the wrong/deprecated place (/tmp). It should be looking in ~/.gconfd
It is a bug in the program. What version of swiftfox is it?

[http://cgwalters.livejournal.com/2008/04/26/](http://cgwalters.livejournal.com/2008/04/26/)

---

### Post by valmar on 2009-01-31
Thank you dearly for all your help

The version of swiftfox is 3.0.4pre1

I have created a soft link for gconfd-valerio pointing to the .gconfd in my home directory. I get exactly the same error. I even tried to create the lock and later even the ior subfolder and file in the directory. I always get exactly the same error. Another software that gives me the same error is zattoo_player, again a 32 bit program. Again, ldd gives no missing libs.

zattoo player when started, before giving the error, gives an error of the kind make sure that you have gconf 2.12


          Valerio

---

### Post by valmar on 2009-02-01
Humm, forgetting zattoo and swiftfox, I think that I have stumbled into a more general problem.

I noticed that if I move to /emul/ia32-linux/usr/lib/libgconf2-4 and run gconf_sanity_check_2

I get

Please contact your system administrator to resolve the following problem:
Could not resolve the address "xml:readonly:/etc/gconf/gconf.xml.mandatory" in the configuration file "/etc/gconf/2/path": Failed: Error opening module `xml': /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: wrong ELF class: ELFCLASS64


So, when the 32 bit gconf_sanity_check_2 is called, it links to the 64 bit version of the libgconfbackend-xml.so

This, I think is the problem that prevents all programs from working. Does anyone know a way to force the sanity check to link to the 32 bit version?

Valerio

---

