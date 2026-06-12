---
title: "Hardy 64-bit - Cisco VPN client, compile error trying to install"
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by ByteJuggler on 2008-06-24
Hello all,

I've been trying for a little while to get the Cisco VPN client installed and working on my Hardy 64-bit desktop install.  Some googling has revealed several pages, one of which is **[this]("http://ubuntuforums.org/archive/index.php/t-765975.html")** page on ye good'ol Ubuntu forums.  The instructions are supposed to work (and pretty much matches and is a superset of various pieces of advice spread over several other pages and forums. 

Now when I follow the instructions in the above thread I get the following: 

```
walterp@walter-desktop:~/cisco_vpn$ **tar -zxvf vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz **
vpnclient/
vpnclient/libvpnapi.so
vpnclient/vpnapi.h
vpnclient/cisco_cert_mgr
vpnclient/vpnclient
vpnclient/ipseclog
vpnclient/cvpnd
vpnclient/vpn_install
vpnclient/vpnclient_init
vpnclient/vpn_uninstall
vpnclient/driver_build.sh
vpnclient/sample.pcf
vpnclient/vpnclient.ini
vpnclient/license.txt
vpnclient/license.rtf
vpnclient/interceptor.c
vpnclient/linuxcniapi.c
vpnclient/linuxcniapi.h
vpnclient/vpn_ioctl_linux.h
vpnclient/IPSecDrvOS_linux.c
vpnclient/linux_os.h
vpnclient/frag.h
vpnclient/frag.c
vpnclient/linuxkernelapi.c
vpnclient/GenDefs.h
vpnclient/mtu.h
vpnclient/IPSecDrvOSFunctions.h
vpnclient/IPSecDrvOS_linux.h
vpnclient/Cniapi.h
vpnclient/unixcniapi.h
vpnclient/unixkernelapi.h
vpnclient/config.h
vpnclient/libdriver64.so
vpnclient/libdriver.so
vpnclient/Makefile
walterp@walter-desktop:~/cisco_vpn$ **cd vpnclient/**
walterp@walter-desktop:~/cisco_vpn/vpnclient$ **patch <../vpnclient-linux-2.6.24-final.diff **
patching file GenDefs.h
patching file interceptor.c
walterp@walter-desktop:~/cisco_vpn/vpnclient$ **patch <../cisco_skbuff_offset.patch **
(Stripping trailing CRs from patch.)
patching file frag.c
(Stripping trailing CRs from patch.)
patching file interceptor.c
Hunk #1 succeeded at 646 (offset 16 lines).
Hunk #2 succeeded at 685 (offset 16 lines).
Hunk #3 succeeded at 807 (offset 16 lines).
(Stripping trailing CRs from patch.)
patching file linuxcniapi.c
(Stripping trailing CRs from patch.)
patching file linuxkernelapi.c
walterp@walter-desktop:~/cisco_vpn/vpnclient$ **vi Makefile **
walterp@walter-desktop:~/cisco_vpn/vpnclient$ **sudo ./vpn_install**
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/walterp/cisco_vpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/walterp/cisco_vpn/vpnclient/linuxcniapi.o
In file included from /home/walterp/cisco_vpn/vpnclient/Cniapi.h:15,
                 from /home/walterp/cisco_vpn/vpnclient/linuxcniapi.c:31:
/home/walterp/cisco_vpn/vpnclient/GenDefs.h:26:7: warning: "HAVE_INTTYPES_H" is not defined
[COLOR="Red"]In file included from /home/walterp/cisco_vpn/vpnclient/Cniapi.h:15,
                 from /home/walterp/cisco_vpn/vpnclient/linuxcniapi.c:31:
/home/walterp/cisco_vpn/vpnclient/GenDefs.h:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘uint64’
/home/walterp/cisco_vpn/vpnclient/GenDefs.h:137: error: redefinition of typedef ‘uint’
include/linux/types.h:103: error: previous declaration of ‘uint’ was here
/home/walterp/cisco_vpn/vpnclient/GenDefs.h:138: error: redefinition of typedef ‘ushort’
include/linux/types.h:102: error: previous declaration of ‘ushort’ was here
/home/walterp/cisco_vpn/vpnclient/GenDefs.h:139: error: redefinition of typedef ‘ulong’
include/linux/types.h:104: error: previous declaration of ‘ulong’ was here
/home/walterp/cisco_vpn/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/walterp/cisco_vpn/vpnclient/linuxcniapi.c:421: warning: unused variable ‘pVABinding’
make[2]: *** [/home/walterp/cisco_vpn/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/walterp/cisco_vpn/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".[/COLOR]
walterp@walter-desktop:~/cisco_vpn/vpnclient$
```

So.  I've had a brief peek about to try and see what's wrong with the code, and the typedef in GenDefs.h line 89 does seem strange: 
```
typedef unsigned long long__int64 uint64;
```

But more importantly, why am I getting this error when the HowTo is supposed to work on Hardy 64-bit?  Has anyone else run into this problem?  If so how did you fix it?

For reference, my current kernet version is 2.6.24-19-generic (latest 64-bit hardy kernel.)

Any pointers would be appreciated.

---

### Post by beniwtv on 2008-06-25
Hmm... I did get an error also once with the VPN client. But that was on Gutsy...

Since then, I never tried again and I now use vpnc (available from the repos) to connect to my company VPN. You could give it a try and see if it works for you...

Hope this helps.

Cheers,

---

### Post by MakWarrior on 2008-10-17
Hi ByteJuggler, I have the problem as you. After spending some hours, I finally realized I did something wrong in the process and it may be helpful to you too. When changing the 'CFLAGS' to 'EXTRA_CFLAGS' in the Makefile, I used the Find and Replace All function in gedit. However, there are two places that refer to flag setting (line: 15 and line: 27). Line 15 refers to 'CFLAGS' while line 27 is referring to 'EXTRA_CFLAGS'. My Find and Replace All accidentally replace the line on 27 as well. So I received the same error as you mentioned. Actually only line 15 is needed to replace. After correctly replace the flag, I can proceed without problem. Hope this help.

---

### Post by ByteJuggler on 2008-10-17
Hey thank you for posting back, I'll try that.  I've probably done the same thing then. :)  By the way I've (in the meantime) just started using "vpnc" which works fine. (So you don't have to use the Cisco client to connect to an IPSEC VPN.)

---

