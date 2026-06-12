---
title: "[SOLVED] Cannot compile slmodem-2.9.11: /usr/bin/ld: cannot find -lgcc"
date: 2008-05-18
forum: x86 64-bit Users
---

### Post by terencekent on 2008-05-18
I am trying to compile slmodem-2.9.11 on a 64bit 8.04 Server, but am unable too. I keep getting the error below:

```

make -C modem all
make[1]: Entering directory `/home/administrator/slmodem-2.9.11-20080417/modem'
rebuild profile...
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_main.o -c modem_main.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_cmdline.o -c modem_cmdline.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem.o -c modem.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_datafile.o -c modem_datafile.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_at.o -c modem_at.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_timer.o -c modem_timer.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_pack.o -c modem_pack.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_ec.o -c modem_ec.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_comp.o -c modem_comp.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_param.o -c modem_param.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o modem_debug.o -c modem_debug.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o homolog_data.o -c homolog_data.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o dp_sinus.o -c dp_sinus.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o dp_dummy.o -c dp_dummy.c
gcc -m32 -Wall -g -O -I. -DCONFIG_DEBUG_MODEM    -o sysdep_common.o -c sysdep_common.c
gcc -m32 -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o  
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status
make[1]: *** [slmodemd] Error 1
make[1]: Leaving directory `/home/administrator/slmodem-2.9.11-20080417/modem'
make: *** [modem] Error 2

```

Here is the uname output...
> 
Linux svc1 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2008 x86_64 GNU/Linux


I have ia32-libs installed, as well as libc6-i386. for 32bit compatibility...

I'm at a loss on how to proceed, any direction would be very helpful!

Thanks,
Terence.

---

### Post by jcwmoore on 2008-05-18
if the program is in the repositories then make sure you have all the dependencies for compilation,
```
sudo apt-get build-dep *name_of_program*
```

based on your output it looks like you are missing something need to build from source.

---

### Post by terencekent on 2008-05-19
I think you're right, but I don't know how to determine what I'm missing.

Here's a little history:
The package I'm trying to install, sl-modem, was removed from the ubuntu repository due to this bug: [https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/61749]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/61749")

However, since many people still need to use the package, there is a great posting for non-64bit systems on how to build from source here: [http://ubuntuforums.org/showthread.php?t=190728]("http://ubuntuforums.org/showthread.php?t=190728")

Which I have used to get it working on my 32 bit systems, but can't get it going on my 64bit (production) systems. Since the key variable here (at least as far as I can see) is 32bit vs 64bit, I'm hoping my is something I'm missing for 32-bit compatibility.

Thanks in advance,
Terence.

---

### Post by terencekent on 2008-05-19
Got it working, it turns out that the gcc 4.2 edition that is currently used with ubuntu 8.04 server (x86_64) was the cause of the problem. 

I installed gcc-3.4 and adjusted the symlink, /usr/bin/gcc, to point to the 3.4 edition instead of the 4.2 edition. After that slmodem compiled correctly and appears to be working.

---

### Post by pixel :-) on 2008-05-21
you can change in the makefille the gcc path,somewhere in the begining.Just to avoid symlinks.

---

### Post by pooyaplus on 2008-10-27
Just an idea here; why not compiling the 32-bit package with force architecture option on dpkg?  

As I want to get the sl-modem working on my tx2000 (amd64) laptop too. I am still searching for a complete solution. Will let you know if made a progress.

---

