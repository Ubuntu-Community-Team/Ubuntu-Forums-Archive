---
title: "VMWare install did not work on 64bit Edgy?"
date: 2007-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2007-02-07
during installation or rather configuration I get:

Unable to install the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during 
compilation and installation of the module can be found here: 
/tmp/vmware-config5

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file: 
'/tmp/vmware-config5/control-only/make.log'
********

The errors in the said log are:

Manifying blib/man3/VMware::VmPerl::ConnectParams.3pm
make: Leaving directory `/tmp/vmware-config5/control-only'
make: Entering directory `/tmp/vmware-config5/control-only'
mkdir /usr/local/man: File exists at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
make: *** [pure_site_install] Error 17
make: Leaving directory `/tmp/vmware-config5/control-only'


Is there something special I need to consider for 64bit install?

---

### Post by greenfrog on 2007-02-07
It looks like the Perl libs are missing.
I know I had to install Perl before I could install vmware server with drapper.

---

### Post by Saubazi on 2007-02-08
I have perl - only thing I can imagine is that some 32bit libs would be missing
but the error seems to me as if it just tried to recreate an existing directory or something.
Did you install some 32bit perl libs?

---

### Post by pinguin on 2007-02-08
Have you installed -dev packages of Perl libs?

---

### Post by Doug11 on 2007-02-08
I just installed vmware server last night on edgy 64 and everything went fine.

---

### Post by Saubazi on 2007-02-08
Probably the dev lib took me forward - now, I get 

Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.




Ups no - actually after running the config-utility I get the same error in the log:
make: Entering directory `/tmp/vmware-config1/control-only'
mkdir /usr/local/man: File exists at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
make: *** [pure_site_install] Error 17
make: Leaving directory `/tmp/vmware-config1/control-only'

---

### Post by Saubazi on 2007-02-10
Ok the problem or the solution was none of the guesses.

vmware started running all right after I answered "no" to the network question.
Apparantly this bit solved the network prob too, since after allowing networking vmware
command always invoked "not configured messages"

[http://www.linuxforen.de/forums/showthread.php?t=225262](http://www.linuxforen.de/forums/showthread.php?t=225262)

remove /etc/vmware/not-configured

I started vmware afterwards with "vmware" not "vmware -l" since the latter did not find
the windows anymore...

---

### Post by Bosk22 on 2008-02-27
About time I started to give something back so here it is - hope it helps someone!!!!!

During a fresh install of Ubuntu 7.10 (64 Bit) and Vmware Server 1.0.4 I got the following error:-

===== Begin - vmware-install.pl Script Snippet Output ========
Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Unable to compile the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed. Errors encountered during
compilation and installation of the module can be found here:
/tmp/vmware-config0

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file:
'/tmp/vmware-config0/control-only/make.log'
********

Hit enter to continue.

===== End - vmware-install.pl Script Snippet Output ========

The error message is very misleading and suggests there is a perl problem. This is however not true!!!! - I solved this by installing the libssl-dev code and the running the VMware install again.

To install libssl-dev enter the following

sudo apt-get install libssl-dev

The download can take a while on 1mb broadband so go make a cup of coffee and by the time you have done this the problem should be gone.

--------

Another problem I had with VMWare and 64bit Ubuntu was that the 32bit compatibility libraries are not installed by default. While VMWare is happy to run in 64bit it still needs these libraries. Again the error message for this one is misleading claiming that the vmware-ping cannot be found or executed and that no subnets can be automatically probed for.

Fix it with this:-

sudo apt-get install ia32-libs*

Good luck.

---

### Post by fjgaude on 2008-02-27
Also, you may have to install build-essential:

```
sudo apt-get install build-essential
```

---

