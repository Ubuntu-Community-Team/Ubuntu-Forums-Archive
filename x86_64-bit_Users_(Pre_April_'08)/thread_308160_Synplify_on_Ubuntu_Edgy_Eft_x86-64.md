---
title: "Synplify on Ubuntu Edgy Eft x86-64"
date: 2006-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aega on 2006-11-27
Sorry if this is highly specific, but I've done a lot of Googling and can't find a way to fix this problem I'm having running Synplify. I've upgraded this installation of Ubuntu from 6.06 to 6.10.

Here's the error I get while trying to run Synplify 8.6.2:

/usr/programs/synplify_862/linux/mbin/synplify: relocation error: /usr/programs/synplify_862/linux/mfw/lib-linux_optimized/libkernel32.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference


Many other forums talk about people having a similar problem running this program on Fedora 5 with the exact same error. Their solution was to use

export LD_ASSUME_KERNEL=2.4.1

however, when I do that prior to running synplify I get this:

/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory


I'm assuming this has something to do with something being setup incorrectly on my machine. I've successfully run this over X-Win in Windows to a 64-bit CentOS 4.2 machine which just pops up with this error:

Incorrectly built binary which accesses errno or h_errno directly. Needs to be fixed.

But that's ok as it still works.

Second problem: I'm not sure it's related, but when I ssh into that same CentOS machine in Ubuntu and try to run synplify it pops up with this error:

mwrpcss: relocation error: /usr/synplify_862/linux/mfw/lib-linux_optimized/libkernel32.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference



Any help or suggestions would be greatly appreciated.

---

### Post by Aega on 2006-11-29
Update.

I've determined part of my second problem is caused by Beryl. If Beryl is not running, I can use Synplify just fine off of the CentOS machine, however when I close the application, I still get the same error.

Running Synplify locally with or without Beryl doesn't seem to make a difference. 

Regarding my initial problem, after even more searching I came across this bug report for Ubuntu:
[https://launchpad.net/distros/ubuntu/+source/glibc/+bug/69879]("https://launchpad.net/distros/ubuntu/+source/glibc/+bug/69879")

So apparently LD_ASSUME_KERNEL will not work in Edgy.

---

### Post by Aega on 2006-12-07
My solution for the moment is to run the Windows version in Wine (which surprisingly enough works perfectly, including while having Beryl running). If I come across a better workaround I will try to post it.

---

### Post by steabert on 2006-12-10
Hi,

it seems somehow there is some library issue.
try "ldd synplify", it prints the shared libraries, perhaps you can find a clue there.

Have you tried running "sudo ldconfig" ?

grtz

---

### Post by Aega on 2006-12-11
Thanks for the response. 

Yes I have tried running "sudo ldconfig" (which runs and then comes back with a prompt, and I still get the same error when I try to run synplify).

I also tried "ldd synplify_pro" which returned "not a dynamic executable".

---

### Post by steabert on 2006-12-12
did you try explicitly "ldd /usr/programs/synplify_862/linux/mbin/synplify" ?

---

### Post by Aega on 2007-01-18
Thanks, that helped a lot.

Sorry for the delayed response, I've been extremely busy over the past month.

Here's the response:

> ldd /usr/programs/synplify_862/linux/mbin/synplify
        linux-gate.so.1 =>  (0xffffe000)
        libsynoe104.so => not found
        libsynot60.so => not found
        libsynoc60.so => not found
        libuuid.so => not found
        libsynog70.so => not found
        libgdiuser32.so => not found
        libadvapi32.so => not found
        libkernel32.so => not found
        libtcl8.4.so => not found
        libmwinitthunk.so => not found
        libcwrapper.so => not found
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7f9a000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f86000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7f82000)
        libutil.so.1 => /lib32/libutil.so.1 (0xf7f7e000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7eb5000)
        libcomdlg32.so => not found
        libshell32.so => not found
        libole32.so => not found
        libmfc400s.so => not found
        liboleaut32.so => not found
        libmsvcrt.so => not found
        libcomctl32.so => not found
        libm.so.6 => /lib32/libm.so.6 (0xf7e8d000)
        libc.so.6 => /lib32/libc.so.6 (0xf7d59000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7d56000)
        /lib/ld-linux.so.2 (0xf7fbe000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7d51000)


By contrast, here's the CentOS machine's output:
> ldd synplify
Incorrectly built binary which accesses errno or h_errno directly. Needs to be fixed.
	linux-gate.so.1 =>  (0xffffe000)
	libsynoe104.so => not found
	libsynot60.so => not found
	libsynoc60.so => not found
	libuuid.so => not found
	libsynog70.so => not found
	libgdiuser32.so => not found
	libadvapi32.so => not found
	libkernel32.so => not found
	libtcl8.4.so => /usr/lib/libtcl8.4.so (0x009eb000)
	libmwinitthunk.so => not found
	libcwrapper.so => not found
	libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0x00d04000)
	libpthread.so.0 => /lib/i686/libpthread.so.0 (0xf7f86000)
	libdl.so.2 => /lib/libdl.so.2 (0x009c0000)
	libutil.so.1 => /lib/libutil.so.1 (0x00ab1000)
	libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0x00ad5000)
	libcomdlg32.so => not found
	libshell32.so => not found
	libole32.so => not found
	libmfc400s.so => not found
	liboleaut32.so => not found
	libmsvcrt.so => not found
	libcomctl32.so => not found
	libm.so.6 => /lib/i686/libm.so.6 (0xf7f61000)
	libc.so.6 => /lib/i686/libc.so.6 (0xf7e38000)
	/lib/ld-linux.so.2 (0x00856000)


The only difference I notice is with libtcl8.4.so, or are all of the libraries supposed to be linked to something?

---

### Post by Aega on 2007-01-22
Synplicity just released a new version of Synplify (8.8 ), so I've tried upgrading to that. 

The CentOS machine runs it fine without any errors.

On my Ubuntu machine the program starts, the window for it pops up, then after ~15 seconds the application crashes, after which I get the message

"libgcc_s.so.1 must be installed for pthread_cancel to work" 

in my terminal. This message keeps repeating every 30 seconds until I close the terminal.

No other error messages pop up.

I got rid of that error message by adding /usr/X11R6/lib, /usr/local/lib, and /usr/lib to /etc/ld.so.conf

It seems I can run this version in batch mode, but I still can't use the gui.

---

### Post by Aega on 2007-01-24
Update:

Ok, I found all of the missing libraries in the synplicity directory (now installed under /usr/programs/fpga_88 for version 8.8 ). So I just set my LD_LIBRARY_PATH to 

/usr/programs/fpga_88/mfw/mw/lib-linux_optimized:/usr/programs/fpga_88/linux/lib

and when I do ldd synplify the output looks like this:
```

        linux-gate.so.1 =>  (0xffffe000)
        libtcl8.4.so => /usr/programs/fpga_88/linux/lib/libtcl8.4.so (0xf7e58000)
        libsynotp80.so => /usr/programs/fpga_88/linux/lib/libsynotp80.so (0xf79de000)
        libsynog90.so => /usr/programs/fpga_88/linux/lib/libsynog90.so (0xf76b0000)
        libsynoe70.so => /usr/programs/fpga_88/linux/lib/libsynoe70.so (0xf7629000)
        libsynsfl20.so => /usr/programs/fpga_88/linux/lib/libsynsfl20.so (0xf7536000)
        libmfc400s.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libmfc400s.so (0xf726b000)
        libcomdlg32.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libcomdlg32.so (0xf7222000)
        libshell32.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libshell32.so (0xf714d000)
        libcomctl32.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libcomctl32.so (0xf709a000)
        libshlwapi.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libshlwapi.so (0xf700c000)
        libuuid.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libuuid.so (0xf6fe4000)
        liboleaut32.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/liboleaut32.so (0xf6ece000)
        libole32.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libole32.so (0xf6d2a000)
        libgdiuser32.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libgdiuser32.so (0xf6abc000)
        librpcrt4.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/librpcrt4.so (0xf6a30000)
        libadvapi32.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libadvapi32.so (0xf69fb000)
        libmsvcrt.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libmsvcrt.so (0xf69dc000)
        libkernel32.so => /usr/programs/fpga_88/mfw/mw/lib-linux_optimized/libkernel32.so (0xf6892000)
        libutil.so.1 => /lib32/libutil.so.1 (0xf687a000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf6876000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf6863000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf679a000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf678c000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0xf66d2000)
        libm.so.6 => /lib32/libm.so.6 (0xf66ac000)
        libc.so.6 => /lib32/libc.so.6 (0xf6578000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf656d000)
        /lib/ld-linux.so.2 (0xf7efb000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6569000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6564000)

```

It seems like everything is set up correctly, but the GUI will not run.

---

