---
title: "VMWare broken on Feisty upgrade"
date: 2007-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ktulu1115 on 2007-04-19
I just did a upgrade to Feisty and everything went pretty smoothly, except that VMWare was broken.  Initially it was an issue with the kernel headers, as it didn't have the module compiled for the new version (2.6.20-15).  I tried playing around with it but couldn't get it to work...  it kept complaining about being unable to find a matching include/version.h for the matching kernel, so I just uninstalled then reinstalled the latest VMWare (1.0.2, I was on 1.0.0 IIRC).

I also installed the vmware-server-kernel-modules package, thinking it would be easier.  It detected them OK, but I got this error during compiling:

```

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I checked the URL, it seems VMWare doesn't support Feisty yet, it only had experimental support for 6.10 on x86_64.  Anyone find a workaround, or somehow got it working?

---

### Post by heimo on 2007-04-19
Did you try "any-any"-patch?
[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

---

### Post by ktulu1115 on 2007-04-19
Wow, thanks!  That worked perfectly.

---

### Post by tatster on 2007-04-20
Hi,

I tried the any-any patch but that didn't work for me.

However I did find that I didn't have g++ installed and this is what was bombing on my system.

After a quick  ```
sudo apt-get install g++
```

I then re-ran vmware-config.pl again and it worked.

Hope this helps someone.

Tat.

---

### Post by calciajd on 2007-04-21
> **heimo said:**
> Did you try "any-any"-patch?
[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

This worked for me as well.

After upgrading to Feisty I was getting:
```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

---

### Post by Hasen_A on 2007-04-21
Yes, this worked nicely.

I've heard that you could drag and drop from Ubuntu into the VM say for example into the WinXP desktop. I've just installed the Vmware server 6.0 right before upgrading to feisty and it isn't working for me right now under Feisty with Vmware tools installed. Is this feature available at all?

---

### Post by brazzmonkey on 2007-04-21
> **heimo said:**
> Did you try "any-any"-patch?
[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)
worked fine here too. thanks for the advice !

---

### Post by Tanker Bob on 2007-04-21
> **heimo said:**
> Did you try "any-any"-patch?
[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)
Fixed my upgrade issues, thanks!  :guitar:

---

### Post by jrjazzman on 2007-04-21
any downsides to this any-any solution?

---

### Post by Tanker Bob on 2007-04-21
Not that I've seen.  My WinXP VMs work perfectly, just as before.  I long for the USB2 support coming in VMWorkstation 6, but this fix got me up and running in minutes under Feisty.

---

### Post by turn1200 on 2007-04-22
I think you can also do the following (got this from someone on the vmware forums I think).

cd vmware-server-distrib/lib/modules/source/
tar -xvf vmmon.tar
vi vmmon-only/include/compat_kernel.h

change the line that says:
static inline _syscall1(int, compat_exit, int, exit_code);
to the following by removing two commas:
static inline _syscall1(int compat_exit, int exit_code);

sudo tar -cvf vmmon.tar vmmon-only/

[IMG]http://fakoamerica.typepad.com/photos/uncategorized/a_moute_noah.jpg[/IMG]

---

### Post by thinguy on 2007-04-22
Another solution found. Thanks

This forum rocks!

---

### Post by mcpoyle on 2007-04-23
Nice!


:ks

---

### Post by kc5hwb on 2007-04-23
I tried running the ./runme.pl file using the any-any solution and I am getting this error:

```
Unable to get the last modification timestamp of the destination file
/etc/vmware/ssl/rui.key.

Execution aborted.

root@samson:/tmp/vmware-any-any-update109#
```

I tried installing g++ and it tells me that the newest version is already installed.

---

### Post by kc5hwb on 2007-04-23
When I run sudo ./vmware-install.pl, I am getting this error..


```

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â...â before âcompat_exitâ
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â...â before âexit_codeâ
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to âintâ in declaration of â_syscall1â
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@samson:/tmp/vmware-server-distrib#
```

---

### Post by screenwriter on 2007-04-24
One more happy customer of VMware-any-to-any.

XPPro works fine.  RHEL is taking a little time to get going (smb mounts) but I'll get there.

Thanks.

//James

---

### Post by raymond3 on 2007-04-24
VMware crashes for me before I can get windows installed.  I've tried a few different CDs (home, pro, 2000) but keep getting the attached error randomly...

---

### Post by reader4 on 2007-04-24
Still having problems here.  Things worked perfectly in 6.10, but after upgrading everything broke.  So, I completely uninstalled old vmware-server and downloaded 1.0.1...

```
$./vmware-install.pl
```

After a failed first attempt, I installed the any-any patch and followed turn1200's fix.  Then the modules build OK...

```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config7/vmmon-only/linux/driver.c:80:
/tmp/vmware-config7/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
/tmp/vmware-config7/vmmon-only/./include/compat_kernel.h:21: warning: &#8216;_syscall1&#8217; declared &#8216;static&#8217; but never defined
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config7/vmmon-only/linux/hostif.c:68:
/tmp/vmware-config7/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
/tmp/vmware-config7/vmmon-only/./include/compat_kernel.h:21: warning: &#8216;_syscall1&#8217; declared &#8216;static&#8217; but never defined
  CC [M]  /tmp/vmware-config7/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config7/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config7/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config7/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config7/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
The module loads perfectly in the running kernel.
```

But the networking install crashes...

```
Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: eth0, eth1, 
eth1:avah. Which one do you want to bridge to vmnet0? [eth0] 

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no] 

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.148.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.148.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.114.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.114.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmnet-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config7/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config7/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config7/vmnet-only/userif.o
/tmp/vmware-config7/vmnet-only/userif.c: In function &#8216;VNetCopyDatagramToUser&#8217;:
/tmp/vmware-config7/vmnet-only/userif.c:629: error: &#8216;CHECKSUM_HW&#8217; undeclared (first use in this function)
/tmp/vmware-config7/vmnet-only/userif.c:629: error: (Each undeclared identifier is reported only once
/tmp/vmware-config7/vmnet-only/userif.c:629: error: for each function it appears in.)
make[2]: *** [/tmp/vmware-config7/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config7/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```


Tried a few different versions of network installs with the same result.  Not sure what to try next... any advice?

---

### Post by PCE_Moose on 2007-04-24
Actually I tried the any-any-patch-109 after I used Synaptic to install build-essentials: it didnt work the first time around. It asked a bunch of questions, but ended in the same error.
For some reason, I tried it again, and it worked just fine. 
So moral of the story: if at first you dont succeed, try again...

---

### Post by reader4 on 2007-04-24
That's what I thought too... tried several times using different ways but the farthest I get is when I uninstall vmware server, install the patch, then install vmware server.  If I use the any-any patch to begin the vmware-config, I cannot even get the modules installed:

```
$ sudo ./runme.pl 
Password:
Updating /usr/bin/vmware-config.pl ... now patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

You must read and accept the End User License Agreement to continue.
Press enter to display it. ...

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config8/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config8/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config8/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config8/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config8/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config8/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config8/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config8/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config8/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config8/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config8/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by pqhanh on 2007-04-25
> **heimo said:**
> Did you try "any-any"-patch?
[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

thank many many....
it goes back to my laptop Athlon XP-M 2100:guitar:

---

### Post by Jeremiah478 on 2007-04-25
Thanks everyone.  I couldn't get vmware to install in feisty; well it would install I just couldn't run the configuration.   I ran the any-any patch, and everything ran smooth after that.

---

### Post by Manfred.Knick on 2007-04-26
> **turn1200 said:**
> I think you can also do the following (got this from someone on the vmware forums I think).

cd vmware-server-distrib/lib/modules/source/
tar -xvf vmmon.tar
vi vmmon-only/include/compat_kernel.h

change the line that says:
static inline _syscall1(int, compat_exit, int, exit_code);
to the following by removing two commas:
static inline _syscall1(int compat_exit, int exit_code);

sudo tar -cvf vmmon.tar vmmon-only/

[IMG]http://fakoamerica.typepad.com/photos/uncategorized/a_moute_noah.jpg[/IMG]

Thanks for this valuable pointer!
Perhaps it was [INDENT][http://www.vmware.com/community/thread.jspa?messageID=616607](http://www.vmware.com/community/thread.jspa?messageID=616607)[/INDENT] ( Post # 4 from adaca ) ?

This way, no global "any-to-any-patch" is needed;
just only exactly the tiny "weird syntax error" corrected.

Concerning your untar / tar proposal:
ahildoer proposes a slightly more comfortable edit - hinted out at the end of the thread.

Kind regards!

---

### Post by gotmonkey on 2007-04-26
I just did a full install of Feisty on my system and tried to install vmware workstation, that did not work. So I downloaded the anytoany patch, run it and comes back with this.

Can anyone help?


simian@simian-laptop:~/shared/vmware-distrib/vmware-any-any-update109$ sudo ./runme.pl 
Updating /usr/bin/vmware-config.pl ... corrupted
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Workstation 5.5.2 or 5.5.3.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config2/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by yj09 on 2007-06-22
try this way.. I copy from this forum...but forgot the link... and it is work for me... 

VMware Server Howto (Feisty)

If you already have VMware Server installed and want it to use the Feisty modules you can jump to Step 3

Step 1 (Installing the modules from repository)
$ sudo apt-get install vmware-server-kernel-modules

Step 2 (Installing VMware Server)
$ tar -xzf VMware-server-1.0.1-29996.tar.gz
$ cd vmware-server-distrib/
$ ./vmware-install.pl

Step 3 (Make VMware Server Daemon work with Feisty modules)
$ sudo sed -i -e "s/\/sbin\/insmod -s -f \"\/lib\/modules\/\`uname -r\`\/misc\/\$1.o\"/modprobe -s -f \$1/" /etc/init.d/vmware

Step 4 (Make the configure script ignore the configure of a new module)
$ sudo sed -i -e "s/sub configure_module {/sub configure_module {\n return 'yes';/" /usr/bin/vmware-config.pl

Step 5 (Reconfigure)
$ sudo vmware-config.pl

Step 6(Restarting the application)
$ sudo /etc/init.d/vmware restart

Copy the tarball to the desktop and extract

clean up any previous installation

from a terminal window make the directory with the vmware source the current directort (cd Desktop, cd vm<tab>, etc.). Then:

sudo ./vmware-install.pl

The installer will begin to unpack and deploy a grunch of files. Accept defaults. At some point you will have to read the license. Proceed through, but do not do or go past the approval step.

Open a new terminal (leaving the other one open) and then navigate to

/usr/lib/vmware/modules/source

find the file vmmon.tar. In the second terminal window:

tar -xvf vmmon.tar

That should extract the content of vmmon.tar into a folder called vmmon-only

Use Krusader (root) if installed, or otherwise open the file :

/usr/lib/vmware/modules/source/vmmon-only/include/compat_kernel.h

in an root level editor.. Look for the code (toward the top):

* provided by x86-64, arm and other (but not by i386).
*/
#define __NR_compat_exit __NR_exit
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,19)
static inline _syscall1(int, compat_exit, int, exit_code);
+#endif

and move the close comment command (*/) to the line after endif, Add a * to the beginning of lines preceding the */ where needed. When finished, it will look like this:

* provided by x86-64, arm and other (but not by i386).
*
* #define __NR_compat_exit __NR_exit
* #if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,19)
* static inline _syscall1(int, compat_exit, int, exit_code);
* #endif
*/

Save the file and close the editor. Make sure that /usr/lib/vmware/modules/source is the active directory in the second terminal then type:

sudo tar -cf vmmon.tar vmmon-only



reconfigure vmware
sudo /usr/bin/vmware-config.pl

---

### Post by ktulu1115 on 2007-06-24
Thanks to all for the great info.  I have an additional question regarding vmware, wondering if anyone else has this - on my system, when I shutdown a virtual machine (right now I have WinXP and Win2k3 Server VM's), after the OS powers off I notice a large amount of disk activity....  vmware seems to be writing a lot of data to the disk, and it does so for a minute or so (in the meantime the vmware GUI hangs), then it finishes and the GUI responds again.

I'm thinking it has something to do with the virtual memory file that is associated with the VM itself.  I'm also fairly certain (IIRC) that both VMs reproduce the behavior.  Has anyone else noticed something similar?

---

### Post by Tanker Bob on 2007-06-24
That happens occasionally when I have it in the background. I think that it is writting to the disk at the time. Probably one of those annoying Windows' habits of "internal maintenance."

---

### Post by jpongin on 2007-06-24
> **heimo said:**
> Did you try "any-any"-patch?
[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

Had the exact same problem.  Your solution worked like a charm.  Thanks for the terrific link.

---

