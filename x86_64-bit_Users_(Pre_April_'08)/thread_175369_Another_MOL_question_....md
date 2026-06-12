---
title: "Another MOL question ..."
date: 2006-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by adodo on 2006-05-13
Hi

I am trying to install MOL on breezy as per the wiki howto at [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto) .

I have made it to the following stage.
After compiling the modules, create a debian package of the modules with the command

   bash:/usr/src/modules/mol$ sudo debian/rules binary-mol-modules

This will result in a debian package mol-modules-2.6.12-9-powerpc_0.9.70+ubuntu0_powerpc.deb in the directory /usr/src

When I try to execute the command above I get the following result:
$ sudo debian/rules binary-mol-modules
dh_testdir
dh_testroot
dh_clean
sh: -c: line 0: syntax error near unexpected token `)'
sh: -c: line 0: `rm -f debian/mol-modules- -r).*.debhelper'
dh_clean: command returned error code
make: *** [install-stamp] Error 1

Does anyone understand that output? Is it easy to fix? I am only a casual coder and am not sure how to trace back through that. I am not afraid to try though, if anyone is willing to try and tutor me.

Thanks

---

### Post by calum on 2006-05-13
[QUOTE=adodo]Hi

I am trying to install MOL on breezy as per the wiki howto at [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto) .

I have made it to the following stage.
After compiling the modules, create a debian package of the modules with the command

   bash:/usr/src/modules/mol$ sudo debian/rules binary-mol-modules

This will result in a debian package mol-modules-2.6.12-9-powerpc_0.9.70+ubuntu0_powerpc.deb in the directory /usr/src

When I try to execute the command above I get the following result:
$ sudo debian/rules binary-mol-modules
dh_testdir
dh_testroot
dh_clean
sh: -c: line 0: syntax error near unexpected token `)'
sh: -c: line 0: `rm -f debian/mol-modules- -r).*.debhelper'
dh_clean: command returned error code
make: *** [install-stamp] Error 1

Does anyone understand that output? Is it easy to fix? I am only a casual coder and am not sure how to trace back through that. I am not afraid to try though, if anyone is willing to try and tutor me.

Thanks[/QUOTE]

To be honest, I'd just ignore those instructions (and Ubuntu's ageing MOL packages), and build the lot yourself:
[http://dev.gentoo.org/~josejx/mol-0.9.71_pre8.tar.bz2]("http://dev.gentoo.org/~josejx/mol-0.9.71_pre8.tar.bz2")

Has always worked more reliably for me.  You'll need to install the kernel headers package corresponding to your kernel, and create a symlink from /usr/src/linux to /usr/linux-headers-<your-kernel-version>-powerpc.  Then just configure, make and make install.

---

### Post by Ptero-4 on 2006-05-13
if it already created the deb package all you need to do is to copy it out to your home dir and then do a sudo dpkg -i mol-modules-2.6.12-9-powerpc_0.9.70+ubuntu0_powerpc.deb to get it installed.

---

### Post by adodo on 2006-05-13
No, the deb file has not been created.

---

### Post by adodo on 2006-05-13
Thanks I will give the download from the gentoo link a try.

---

### Post by adodo on 2006-05-13
I have been trying to compile mol from the gentoo link provided in a reply above. I have now reached the following point and am not quite sure what I need to do next.

./configure worked after I installed a few extra libraries.

Here is output from make:
+ Entering Linux
  Building modules, stage 2.
Warning: could not find /usr/src/mol-0.9.71_pre8/obj-ppc/build/src/kmod/.traps.o.cmd for /usr/src/mol-0.9.71_pre8/obj-ppc/build/src/kmod/traps.o
    Kernel source                 : /lib/modules/2.6.12-10-powerpc/build
    Module compiled for           : 2.6.12-10-powerpc
    Running kernel                : 2.6.12-10-powerpc
+ Entering netdriver
make[4]: *** No rule to make target `/usr/src/mol-0.9.71_pre8/obj-ppc/build/src/netdriver/tun.c', needed by `/usr/src/mol-0.9.71_pre8/obj-ppc/build/src/netdriver/tun.o'.  Stop.
make[3]: *** [_module_/usr/src/mol-0.9.71_pre8/obj-ppc/build/src/netdriver] Error 2

Thanks in advance again

---

### Post by jdp on 2006-05-14
I haven't looked into it in a while, but weren't MOL drivers supposed to be released as official packages in the repos sometime ago?

---

### Post by ssam on 2006-05-14
in dapper the MOL modules are in the kernel, so you dont need to build anything

---

### Post by fraterf93 on 2006-05-15
I have successfully installed MOL in Dapper on my Mac mini, but when I run it in Breezy on my iMac G3 600  it just hangs, and the terminal keeps saying this: RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>

Over, and over again.  the only way to get it to stop is to close the MOL window.

---

### Post by calum on 2006-05-16
[QUOTE=adodo]I have been trying to compile mol from the gentoo link provided in a reply above. I have now reached the following point and am not quite sure what I need to do next.

./configure worked after I installed a few extra libraries.

Here is output from make:
+ Entering Linux
  Building modules, stage 2.
Warning: could not find /usr/src/mol-0.9.71_pre8/obj-ppc/build/src/kmod/.traps.o.cmd for /usr/src/mol-0.9.71_pre8/obj-ppc/build/src/kmod/traps.o
    Kernel source                 : /lib/modules/2.6.12-10-powerpc/build
    Module compiled for           : 2.6.12-10-powerpc
    Running kernel                : 2.6.12-10-powerpc
+ Entering netdriver
make[4]: *** No rule to make target `/usr/src/mol-0.9.71_pre8/obj-ppc/build/src/netdriver/tun.c', needed by `/usr/src/mol-0.9.71_pre8/obj-ppc/build/src/netdriver/tun.o'.  Stop.
make[3]: *** [_module_/usr/src/mol-0.9.71_pre8/obj-ppc/build/src/netdriver] Error 2

Thanks in advance again[/QUOTE]

IIRC, on the configuration screen that lets you choose which components to build, you should /uncheck/ the TUN driver, because MOL can just use the one in the kernel.  That should get rid of this error.

---

### Post by calum on 2006-05-16
[QUOTE=fraterf93]I have successfully installed MOL in Dapper on my Mac mini, but when I run it in Breezy on my iMac G3 600  it just hangs, and the terminal keeps saying this: RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>
RVEC-DEBUGGER <1882>

Over, and over again.  the only way to get it to stop is to close the MOL window.[/QUOTE]

One possible cause of this error is solved by [the patch referenced here]("http://lists.terrasoftsolutions.com/pipermail/mol-general/2004-November/003542.html"), so you should check if that's been applied in your case.  (If it has, I've no idea I'm afraid.)

---

### Post by adodo on 2006-05-17
Thanks Calum. That got things working for me. Now I just need to set up my extras.

---

### Post by adodo on 2006-05-18
Yes I got things working on my desktop at home running Breezy - both 10.3 and 10.4 - I was quite happy.

Now I am trying to do the same thing on my Powerbook. The compile and install goes smoothly, but when I actually try to start MOL I receive the following output.

Mac-on-Linux 0.9.71-pre8 [May 19 2006 08:32]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Loading Mac-on-Linux kernel module:
   /usr/local/lib/mol/0.9.71/modules/2.6.15-22-powerpc/mol.ko
insmod: error inserting '/usr/local/lib/mol/0.9.71/modules/2.6.15-22-powerpc/mol.ko': -1 Invalid module format

I am running Dapper Flight 7 on my PB.

Thanks again

---

### Post by calum on 2006-05-19
[QUOTE=adodo]Yes I got things working on my desktop at home running Breezy - both 10.3 and 10.4 - I was quite happy.

Now I am trying to do the same thing on my Powerbook. The compile and install goes smoothly, but when I actually try to start MOL I receive the following output.

Mac-on-Linux 0.9.71-pre8 [May 19 2006 08:32]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Loading Mac-on-Linux kernel module:
   /usr/local/lib/mol/0.9.71/modules/2.6.15-22-powerpc/mol.ko
insmod: error inserting '/usr/local/lib/mol/0.9.71/modules/2.6.15-22-powerpc/mol.ko': -1 Invalid module format

I am running Dapper Flight 7 on my PB.

Thanks again[/QUOTE]

Sounds like a kernel header mismatch... you're compiling with the 2.6.15-22 header files, but is that the version of the kernel you're actually running?  (The output of 'uname -a' will tell you.)

---

### Post by adodo on 2006-05-22
An upgrade to 2.6.15-23 has just been released, so I installed that and verified that My headers matched the running kernel using uname.

After removing all existing traces of mol and rebuilding things went crazy after running molvconfig. I am in the process of returning to 2.6.15-22 to try again.

---

### Post by adodo on 2006-05-22
My PB has been returned to running kernel-2.6.15-22-powerpc, dapper flight 7. Verified that the matching kernel-headers have been installed.

Removed all traces of mol.
Compiled and installed mol - using mol-0.9.71_pre8 from gentoo.org.

Still get the following output:
adodo@max:/usr/src/mol-0.9.71_pre8$ /usr/local/mol/bin/startmol --test
Mac-on-Linux 0.9.71-pre8 [May 22 2006 14:20]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Loading Mac-on-Linux kernel module:
   /usr/local/mol/lib/mol/0.9.71/modules/2.6.15-22-powerpc/mol.ko
insmod: error inserting '/usr/local/mol/lib/mol/0.9.71/modules/2.6.15-22-powerpc/mol.ko': -1 Invalid module format

Used the same build procedure on breezy on my desktop and things worked.

Just a note: When I used the MacOnLinux Dapper Howto, Mac OS X would start to run and then just before the login screen it would crash with the OS X equivalent of Microsoft's Blue Screen of Death.

---

