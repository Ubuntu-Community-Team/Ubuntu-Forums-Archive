---
title: "Failing to locate shared libraries"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cosmic_Crusader on 2005-10-17
I'm running a clean install of AMD64 Breezy.

I've installed the Citrix v9 client and it complains about not finding libraries which are installed in /usr/X11R6/lib.> ldd ~/Applications/ICAClient/linuxx86/wfcmgr
        linux-gate.so.1 =>  (0xffffe000)
        libXm.so.3 => not found
        libXp.so.6 => not found
        libXpm.so.4 => /usr/lib32/libXpm.so.4 (0x5557b000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x55590000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x55597000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x555b0000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x555c6000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x555c9000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x555da000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x55708000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x55756000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x55816000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55824000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55827000) 
Whereas the file does exist:> locate libXm.so.3
/usr/X11R6/lib/libXm.so.3
/usr/X11R6/lib/libXm.so.3.0.2 
I noticed that ldd has the path set:> cat /etc/ld.so.conf
/lib32
/usr/lib32
/usr/X11R6/lib32 but it should look in the respective "lib" directories as a last resort right?

Also if this information helps, the libXm.so.3 library does in fact correctly parse with the linker:> ldd `locate libXm.so.3`
/usr/X11R6/lib/libXm.so.3:
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0x00002aaaaae48000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0x00002aaaaaf62000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0x00002aaaab0c3000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0x00002aaaab1cb000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002aaaab2e8000)
        libXp.so.6 => /usr/lib32/libXp.so.6 (0x00002aaaab3f9000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaab501000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaab6dc000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaab913000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaaba15000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaabb19000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)
/usr/X11R6/lib/libXm.so.3.0.2:
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0x00002aaaaae48000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0x00002aaaaaf62000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0x00002aaaab0c3000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0x00002aaaab1cb000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002aaaab2e8000)
        libXp.so.6 => /usr/lib32/libXp.so.6 (0x00002aaaab3f9000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaab501000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaab6dc000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaab913000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaaba15000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaabb19000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000) 

And yet for a successful library I get:> ldd `locate libXpm.so.4`
/usr/lib/libXpm.so.4.11.0:
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaabd0000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaaadab000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaaaead000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab0e4000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab1e8000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)
/usr/lib/libXpm.so.4:
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaabd0000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaaadab000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaaaead000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab0e4000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab1e8000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)
/usr/lib32/libXpm.so.4.11.0:
        linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x5557a000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5563a000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x5563d000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x5576b000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x5576e000)
        /lib/ld-linux.so.2 (0x56555000)
/usr/lib32/libXpm.so.4:
        linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x5557a000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5563a000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x5563d000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x5576b000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x5576e000)
        /lib/ld-linux.so.2 (0x56555000) 
It seems to me there are 64bit libraries installed but no 32 bit?

This problem is causing a lot of breakages, another example is the fglrx drivers.

---

### Post by neurator on 2005-11-02
Have  you found a fix for this at all yet?  I'm having similar trouble with Citrix 9 (8 didn't work either).  I've got the same computer config you do, Breezy 5.10 with Amd64.

Thanks!

-R

---

### Post by Cosmic_Crusader on 2005-11-02
Alas no, I had to install a 32bit chroot and install Citrix in that.

---

### Post by timlg98 on 2005-11-06
Here's a link from Citrix on this issue. After I applied the symlink, my Citrix v9 client works.
[http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=68151&tstart=0](http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=68151&tstart=0)

---

### Post by bernardfrancois on 2006-03-08
[QUOTE=Cosmic_Crusader]I'm running a clean install of AMD64 Breezy.
I've installed the Citrix v9 client and it complains about not finding libraries which are installed in /usr/X11R6/lib. 
[/QUOTE]

How did you manage to install it? I can't install it in my 64bit environment...

---

### Post by jkroto on 2006-12-07
> **bernardfrancois said:**
> How did you manage to install it? I can't install it in my 64bit environment...

bernardfrancois,
Did you ever get an answer as to how to install or get working in 64-bit system.

EDIT: I got it to work and I posted how-to [here](http://www.ubuntuforums.org/showthread.php?p=1860514#post1860514)

---

