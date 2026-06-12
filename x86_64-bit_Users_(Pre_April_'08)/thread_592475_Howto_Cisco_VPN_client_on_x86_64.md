---
title: "Howto: Cisco VPN client on x86_64"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by peteguhl on 2007-10-26
First off, you have to use version 4.8.00.0490-k9 of the vpn client as version 4.8.01.0640-k9 has broken x86_64 for the kernel module compilation. Of course, this means you also need to patch the client to work with the 2.6.22 kernel. 

Here's what you do:
```

#!/bin/bash

# if you don't already have them, install headers and build-essential
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

# Install ia32 support
sudo apt-get install ia32-libs 

# Download the vpnclient archive (Must be 0490!)
wget http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz

# untar the archive
tar xzvf vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz  # extracts to 'vpnclient' directory

# Get the patch
wget -q http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff

# Patch the client
cd vpnclient
patch <../vpnclient-linux-2.6.22.diff  # actually patch the client

# Install the client
./vpn_install

# Make sure all the permissions are correct, lest the client pukes
sudo chmod 0777 /etc/opt/cisco-vpnclient/Profiles
sudo chmod 0777 /etc/opt/cisco-vpnclient/Certificates
sudo chmod 0666 /etc/opt/cisco-vpnclient/Profiles/*.pcf

## Fix acl to allow non-root user vpnaccess (using root is bad, m'kay)
sudo chmod 4755 /opt/cisco-vpnclient/bin/cvpnd  

# Have the vpnclient_init *actually* start at boot
sudo update-rc.d -f vpnclient_init remove
sudo update-rc.d -f vpnclient_init defaults


```

And that's all there is to it ;)  Make sure to keep your profiles permissions set to 666 else you'll get errors. Oh, one other note: make sure the filename of your root certificate is in 8.3 format before trying to install it.. the cisco_cert_mgr will puke if the filename is longer!  

P.P.S. - I suggest just copying the above code into a script and running the script.

Pete

---

### Post by Tlon on 2007-10-28
Dumb question:

Where can I find the client software itself?

---

### Post by loupy on 2007-10-28
I get an error when I try to run the install:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** No rule to make target `/home/user/Download/vpnclient/libdriver64.so', needed by `/home/user/Download/vpnclient/cisco_ipsec.o'.  Stop.
make[1]: *** [_module_/home/user/Download/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
```

Any ideas why?

---

### Post by lamnk on 2007-10-28
> **loupy said:**
> I get an error when I try to run the install
Are you sure you use 0490 revision ? Have you patched it ?

I installed/run the older version succesfully.

---

### Post by Tlon on 2007-10-28
Here's what I get when I try to run the patch:

> patching file frag.c
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 51.
Hunk #3 FAILED at 72.
Hunk #4 FAILED at 130.
Hunk #5 FAILED at 140.
Hunk #6 FAILED at 207.
6 out of 6 hunks FAILED -- saving rejects to file frag.c.rej
patching file interceptor.c
Hunk #1 FAILED at 5.
Hunk #2 FAILED at 342.
Hunk #3 FAILED at 558.
Hunk #4 FAILED at 577.
Hunk #5 FAILED at 597.
Hunk #6 FAILED at 686.
Hunk #7 FAILED at 701.
7 out of 7 hunks FAILED -- saving rejects to file interceptor.c.rej
patching file IPSecDrvOS_linux.c
Hunk #1 FAILED at 11.
1 out of 1 hunk FAILED -- saving rejects to file IPSecDrvOS_linux.c.rej
patching file linuxcniapi.c
Hunk #1 FAILED at 5.
Hunk #2 FAILED at 295.
Hunk #3 FAILED at 341.
Hunk #4 FAILED at 459.
Hunk #5 FAILED at 479.
5 out of 5 hunks FAILED -- saving rejects to file linuxcniapi.c.rej
patching file linux_os.h
Reversed (or previously applied) patch detected!  Assume -R? [n] 


---

### Post by peteguhl on 2007-10-29
It sounds like you are trying to patch the wrong vpnclient - please download the client from Alexander's (maker of the patch) site:

[http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz](http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz)


I'll edit my instructions at the top to include getting the software...

---

### Post by parker13 on 2007-10-29
Thank you *very* much for this. It works great for me.

I now have zero 64-bit regrets!

---

### Post by diver_strelok on 2007-10-29
Hi All,

I still have the following errors, after trying previous version of the client.
I did patch it, but still does not work for me.
Any help will be highly appreciated.

[INDENT]Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/ariel/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ariel/vpnclient/linuxcniapi.o
In file included from /home/ariel/vpnclient/Cniapi.h:15,
                 from /home/ariel/vpnclient/linuxcniapi.c:30:
/home/ariel/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /home/ariel/vpnclient/frag.o
In file included from /home/ariel/vpnclient/Cniapi.h:15,
                 from /home/ariel/vpnclient/frag.c:30:
/home/ariel/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /home/ariel/vpnclient/IPSecDrvOS_linux.o
In file included from /home/ariel/vpnclient/IPSecDrvOS_linux.c:20:
/home/ariel/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /home/ariel/vpnclient/interceptor.o
In file included from /home/ariel/vpnclient/Cniapi.h:15,
                 from /home/ariel/vpnclient/interceptor.c:33:
/home/ariel/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
/home/ariel/vpnclient/interceptor.c: In function ‘handle_vpnup’:
/home/ariel/vpnclient/interceptor.c:313: warning: assignment from incompatible pointer type
/home/ariel/vpnclient/interceptor.c:337: warning: assignment from incompatible pointer type
/home/ariel/vpnclient/interceptor.c:338: warning: assignment from incompatible pointer type
/home/ariel/vpnclient/interceptor.c: In function ‘do_cleanup’:
/home/ariel/vpnclient/interceptor.c:386: warning: assignment from incompatible pointer type
  CC [M]  /home/ariel/vpnclient/linuxkernelapi.o
/home/ariel/vpnclient/linuxkernelapi.c: In function ‘kernel_alloc’:
/home/ariel/vpnclient/linuxkernelapi.c:12: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
make[2]: *** No rule to make target `/home/ariel/vpnclient/libdriver64.so', needed by `/home/ariel/vpnclient/cisco_ipsec.o'.  Stop.
make[1]: *** [_module_/home/ariel/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
[/INDENT]

---

### Post by was1984 on 2007-10-29
Hi, I have done exactly as suggested here and I still can't get cisco VPN to install correctly on x86-64.  I really like Ubuntu, but I don't like having to reboot into Windows (which I retain for games) every time I want to log into work.  Here is the execution of the bash script provided.  I'm a new Linux user by the way, so please be gentle.  The incompatible pointers lead me to believe the problem is related to the x-64 architecture, but I'm not a good enough programmer to figure out what the heck is going on.

```
asmith@wash:~$ sudo bash vpnclient.bash
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
--21:28:48--  http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz
           => `vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz'
Resolving tuxx-home.at... 88.198.57.56
Connecting to tuxx-home.at|88.198.57.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,045,213 (2.0M) [application/x-gzip]

100%[====================================>] 2,045,213    547.27K/s    ETA 00:00

21:28:53 (404.03 KB/s) - `vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz' saved [2045213/2045213]

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
patching file frag.c
patching file interceptor.c
patching file IPSecDrvOS_linux.c
patching file linuxcniapi.c
patching file linux_os.h
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/asmith/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.22-14-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/asmith/vpnclient/linuxcniapi.o
In file included from /home/asmith/vpnclient/Cniapi.h:15,
                 from /home/asmith/vpnclient/linuxcniapi.c:30:
/home/asmith/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /home/asmith/vpnclient/frag.o
In file included from /home/asmith/vpnclient/Cniapi.h:15,
                 from /home/asmith/vpnclient/frag.c:30:
/home/asmith/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /home/asmith/vpnclient/IPSecDrvOS_linux.o
In file included from /home/asmith/vpnclient/IPSecDrvOS_linux.c:20:
/home/asmith/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /home/asmith/vpnclient/interceptor.o
In file included from /home/asmith/vpnclient/Cniapi.h:15,
                 from /home/asmith/vpnclient/interceptor.c:33:
/home/asmith/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
/home/asmith/vpnclient/interceptor.c: In function &#8216;handle_vpnup&#8217;:
/home/asmith/vpnclient/interceptor.c:313: warning: assignment from incompatible pointer type
/home/asmith/vpnclient/interceptor.c:337: warning: assignment from incompatible pointer type
/home/asmith/vpnclient/interceptor.c:338: warning: assignment from incompatible pointer type
/home/asmith/vpnclient/interceptor.c: In function &#8216;do_cleanup&#8217;:
/home/asmith/vpnclient/interceptor.c:386: warning: assignment from incompatible pointer type
  CC [M]  /home/asmith/vpnclient/linuxkernelapi.o
/home/asmith/vpnclient/linuxkernelapi.c: In function &#8216;kernel_alloc&#8217;:
/home/asmith/vpnclient/linuxkernelapi.c:12: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;size_t&#8217;
  LD [M]  /home/asmith/vpnclient/cisco_ipsec.o
  Building modules, stage 2.
  MODPOST 1 modules
/bin/sh: scripts/mod/modpost: not found
make[2]: *** [__modpost] Error 127
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
chmod: cannot access `/etc/opt/cisco-vpnclient/Profiles': No such file or directory
chmod: cannot access `/etc/opt/cisco-vpnclient/Certificates': No such file or directory
chmod: cannot access `/etc/opt/cisco-vpnclient/Profiles/*.pcf': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/cvpnd': No such file or directory
 Removing any system startup links for /etc/init.d/vpnclient_init ...
update-rc.d: /etc/init.d/vpnclient_init: file does not exist

```

---

### Post by Tlon on 2007-10-30
Ok, turns out my permissions were just a bit out of whack.  When I did everything from my home directory it worked like a charm.  Thanks.

The one remaining issue that I'm having is that, for some reason, when I connect Local LAN Access is disabled.  This is really frustrating, as it's the same problem that I had with vpnc, which is what drove me to go through with the Cisco VPN hassle in the first place.  I C&P'd the profile DIRECTLY from my Win install, so it should be good to go... right?  The only thing I changed (after it didn't work the first time) was the 'EnableLocalLAN' variable, which I changed from 0 to 1.  Any help would be GREATLY appreciated.

> 
am@e:/etc/opt/cisco-vpnclient/Profiles$ vpnclient connect MediabaseCisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at ********************
User Authentication for ******************

Enter Username and Password.

Username [*******]:
Password []:
Authenticating user.
Negotiating security policies.
Securing communication channel.

Welcome to *******************
Do you wish to continue? (y/n): y

Your VPN connection is secure.

VPN tunnel information.
Client address: ************
Server address: **************
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is active on port UDP 4500
Local LAN Access is disabled



ifconfig gives me this (details removed):

cipsec0   Link encap:Ethernet  HWaddr ********* 
          inet addr:*************  Mask:*************
          inet6 addr: fe80::20b:fcff:fef8:18f/64 Scope:Link
          UP RUNNING NOARP  MTU:1356  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:10 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11721 (11.4 KB)  TX bytes:12373 (12.0 KB)

eth0 # details removed... no different than it normally looks

Thanks for all of the help.

---

### Post by numerodix on 2007-10-30
Very helpful thread, but on my 2.6.22-14-generic (and following your instructions), I get frequent kernel panics, especially when my unstable wireless link goes down, I have to re-request an ip and reconnect to vpn. The panic comes from the cvpnd process, or at least seems definitely caused by the cisco driver.

Anyone seen this behavior? Can you tell me how to capture a kernel panic message?

---

### Post by loupy on 2007-10-30
I guess I must've downloaded the wrong version.  I used the links above and all is working perfectly now - thanks!!!!!!

---

### Post by parker13 on 2007-10-30
> **Tlon said:**
> Ok, turns out my permissions were just a bit out of whack.  When I did everything from my home directory it worked like a charm.  Thanks.

The one remaining issue that I'm having is that, for some reason, when I connect Local LAN Access is disabled.  This is really frustrating, as it's the same problem that I had with vpnc, which is what drove me to go through with the Cisco VPN hassle in the first place.  I C&P'd the profile DIRECTLY from my Win install, so it should be good to go... right?  The only thing I changed (after it didn't work the first time) was the 'EnableLocalLAN' variable, which I changed from 0 to 1.  Any help would be GREATLY appreciated.

Thanks for all of the help.

Whether local LAN access is disabled or not is determined by the server side and you don't have any control over it. I've found that the Cisco client is actually stricter at disabling local LAN access than VPNC.

You seem to imply that local LAN access works when you connect using Windows - is this the case?

---

### Post by Tlon on 2007-10-30
> **parker13 said:**
> Whether local LAN access is disabled or not is determined by the server side and you don't have any control over it. I've found that the Cisco client is actually stricter at disabling local LAN access than VPNC.

You seem to imply that local LAN access works when you connect using Windows - is this the case?

Ah, my apologies.  It turns out that "LocalLANAccess" isn't what I actually wanted to begin with -- I just made a bad assumption going by the name, ugh.  What I mean is that DNS isn't resolving properly.  E.g.  When I am at the office, where we are wired with a myoffice.com domain, I can access the internal site portal.myoffice.com simply by entering 'http://portal/'.  When I am connected using the Cisco VPN client under Windows, I can do the same thing, but remotely.  Using that same profile under Linux, I'm not getting any internal DNS resolution at all, with either the abbreviated or the full name.  I'd have to look up the IP addy's to try those, but I imagine that those work.  Does that make sense?

---

### Post by lisc998 on 2007-10-31
It's looking good! I was worried I was actually going to have to go to work back then! :KS

---

### Post by altersense on 2007-10-31
No need to patch anything anymore to build and install under newer kernels.

[http://tuxx-home.at/archives/2007/09/24/T15_26_49/](http://tuxx-home.at/archives/2007/09/24/T15_26_49/)

tried vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz and it works perfectly.

---

### Post by peteguhl on 2007-10-31
> **altersense said:**
> No need to patch anything anymore to build and install under newer kernels.

[http://tuxx-home.at/archives/2007/09/24/T15_26_49/](http://tuxx-home.at/archives/2007/09/24/T15_26_49/)

tried vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz and it works perfectly.


And uh, which 64 bit Linux are you running?

---

### Post by csimoes on 2007-10-31
Thanks so much, your script worked perfectly for me on my newly upgrade Gutsy.

---

### Post by lisc998 on 2007-11-01
> **lisc998 said:**
> It's looking good! I was worried I was actually going to have to go to work back then! :KS

OK, I spoke too soon. Since upgrading to Gutsy, my VPN is unstable. It seems to loose DNS after 20 minutes or so. It was fine before and is fine with Windows. I've tried Cisco 0490 patched, 0640, and also kvpnc. All connect but fail after a while. I get it on both my laptops. For a while I can continue with existing ssh sessions, but I can't create new sessions based on server name.  Then the existing sessions will die and I'll have to restart the vpn session.

Has anyone else experienced this?

Cheers,
Tim

---

### Post by Coops on 2007-11-02
Right, on 2.6.22-14-generic 64bit. I run the above script, but on running "vpnclient" I get:

Inconsistency detected by ld.so: dl-lookup.c: 232: _dl_lookup_symbol_x: Assertion `version == ((void *)0) || (flags & ~(DL_LOOKUP_ADD_DEPENDENCY)) == 0' failed!

Any ideas?

---

### Post by averagebeatboy on 2007-11-03
Hey Pete,

Thank you so much man.  I have the Cisco Aironet 802.11 a/b/g/ Wireless PC Adapter and it looks so awesome.  I just forgot that Linux would for sure not have the drivers.  The drivers on Cisco's site, of course, are for 2000 and XP.

Lo and behold, here comes a Cisco man to save my **** -- thank you thank you thank you.  I know how difficult Cisco can be.  Hence, why you are making so much money on gigs if you are a Cisco man.

When they were doing the transformation from First Union to Wachovia from North Carolina up the coast, I was stuck a lot of times with the Cisco language.  Once you learn it though and especially through a military Cisco Engineer and their Army Alphabet usage you get the hang real quick.

Thanks so much again for saving my ****.

Just a question when ya got a minute -- do you think your script will run on other Linux distros?

Cheers,

Averagebeatboy

---

### Post by peteguhl on 2007-11-03
It will work if you but out the first lines that use apt - just make sure that you have linux kernel headers or full source for your kernel. Also, make sure you have the tools required for building kernel from source (gcc, etc) along with 32bit support. The script *should* work on any debian based linux distro (ubuntu, debian, etc).


sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

# Install ia32 support
sudo apt-get install ia32-libs

---

### Post by cdenning on 2007-11-09
Has any one gotten the Cisco VPN Client to work when this error message is being generated?


HTPC-Repository:~$ vpnclient connect DDNA-NY
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: The Connection Manager was unable to read the connection entry, or the connection entry has missing or incorrect information.
There are no new notification messages at this time.

---

### Post by cdenning on 2007-11-09
Has any one gotten the Cisco VPN Client to work when this error message is being generated?


HTPC-Repository:~$ vpnclient connect DDNA-NY
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: The Connection Manager was unable to read the connection entry, or the connection entry has missing or incorrect information.
There are no new notification messages at this time.

---

### Post by peteguhl on 2007-11-09
Yes... that is usually indicative of bad permissions. As a test, try:

chmod -R 777 /etc/opt/cisco-vpnclient (or whatever directly your install your certs and profiles into)

---

### Post by LobbyDizzle on 2007-11-28
Here's my deal. I had no problem running all the code, but I only need to run the client when I am on campus. What do I do to run and close the VPN Client?  noob here

---

### Post by peteguhl on 2007-11-28
It is all command-line based, so fire up a virtual terminal and run the following command, replacing 'profilename' with the name of your profile without the '.pcf' extension.

vpnclient connect profilename

To end, just close the terminal or disconnect.

---

### Post by LobbyDizzle on 2007-12-10
How do I make a profile?? I have a username and password that I have to use to connect. I have no idea what ip address to use or anything else. I need it for the Penn State University Park campus.

---

### Post by aranoyas on 2007-12-10
> **parker13 said:**
> Whether local LAN access is disabled or not is determined by the server side and you don't have any control over it. I've found that the Cisco client is actually stricter at disabling local LAN access than VPNC.

You seem to imply that local LAN access works when you connect using Windows - is this the case?

you can win a control back with simple trik:
[http://ubuntuforums.org/showthread.php?t=430136](http://ubuntuforums.org/showthread.php?t=430136)
:popcorn:

---

### Post by pavkb on 2008-01-14
What is the module name that needs to be started. I tried to modprobe cisco_ipsec, says the module not found. Hopefully i will get an answer before i am forced to restart.

---

### Post by plato4me on 2008-01-20
I followed this HOWTO exactly.  Everything compiled.  Everything looks normal, but I can't connect to any internet site with vpn running.  Any ideas about what might be wrong?


Here are the details.

------------------

I started /etc/init.d/vpnclient_init and then did this:

vpnclient connect MyProfileName

(NOTE: "MyProfileName" is taken from a pcf file I got from the vpnclient at my university's vpn offering, which does NOT compile under 64-bit.)

All worked as expected.  I got the following responses in my terminal:

Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at 198.59.55.38
Contacting the gateway at 198.59.55.36 (balancing)
User Authentication for MyProfileName...

Enter Username and Password.

Username [my-login-name]: 
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.

Your VPN connection is secure.
VPN tunnel information.
Client address: 198.11.27.52
Server address: 198.59.55.36
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is active on port UDP 10000
Local LAN Access is disabled

--------------------------------------------------------------------

Looks good...  Right?

The trouble is that once I've done that I have absolutely no access to the WWW.  I thought it might be a DNS problem.  So I tried using a familiar url number in my browser.  Nothing doing.  The browser doesn't give me the familiar error page - it just doesn't go anywhere.

For what it's worth, I can get vpn to work under windows on a non-64-bit laptop.

---

### Post by plato4me on 2008-01-20
Sorry.  It's working now.  I have no idea why.  The only thing I did was to run a view other vpnclient commands:

vpnclient notify
vpnclient verify
vpnclient autoinit

Then I did 

vpnclient connect MyProfileName

And suddenly I had a usable vpn connection to the www.  I hope it stays that way.

Thanks for all the good info in this HOWTO!

---

### Post by lunatico on 2008-02-18
Hello,

Is the script at the beginning of this forum still valid? It is giving me errors...

Thanks!

---

### Post by peteguhl on 2008-02-19
Should be - can you post your errors?

---

### Post by f1r3br4nd on 2008-02-20
Hello. I am running 2.6.24-8-generic #1 SMP Thu Feb 14 20:13:27 UTC 2008 x86_64 GNU/Linux (Hardy alpha, Kubuntu). 

As per instructions to amd64 users earlier in this thread I made sure I had the needed packages, did wget [http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz](http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz), wget -q [http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff](http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff), untared, patched (and there was a Makefile problem nobody seems to have mentioned, which was solved by moving everything in CFLAGS to EXTRA_CFLAGS, fyi).

I still cannot compile when I run vpn_install. I get  the following output:

```

Making module
make -C /lib/modules/2.6.24-8-generic/build SUBDIRS=/media/sda2/home/a/temp/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-8-generic'
  CC [M]  /media/sda2/home/a/temp/vpnclient/linuxcniapi.o
In file included from /media/sda2/home/a/temp/vpnclient/Cniapi.h:15,
                 from /media/sda2/home/a/temp/vpnclient/linuxcniapi.c:30:
/media/sda2/home/a/temp/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
In file included from /media/sda2/home/a/temp/vpnclient/Cniapi.h:15,
                 from /media/sda2/home/a/temp/vpnclient/linuxcniapi.c:30:
/media/sda2/home/a/temp/vpnclient/GenDefs.h:111: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/media/sda2/home/a/temp/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/media/sda2/home/a/temp/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-8-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

If I try commenting out line 111 in GenDefs.h (if uintptr_t is already defined in the headers, we have no business redefining it, amirite?) I still fail to compile, with the following output:

```
Making module
make -C /lib/modules/2.6.24-8-generic/build SUBDIRS=/media/sda2/home/a/temp/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-8-generic'
  CC [M]  /media/sda2/home/a/temp/vpnclient/linuxcniapi.o
In file included from /media/sda2/home/a/temp/vpnclient/Cniapi.h:15,
                 from /media/sda2/home/a/temp/vpnclient/linuxcniapi.c:30:
/media/sda2/home/a/temp/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /media/sda2/home/a/temp/vpnclient/frag.o
In file included from /media/sda2/home/a/temp/vpnclient/Cniapi.h:15,
                 from /media/sda2/home/a/temp/vpnclient/frag.c:30:
/media/sda2/home/a/temp/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /media/sda2/home/a/temp/vpnclient/IPSecDrvOS_linux.o
In file included from /media/sda2/home/a/temp/vpnclient/IPSecDrvOS_linux.c:20:
/media/sda2/home/a/temp/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /media/sda2/home/a/temp/vpnclient/interceptor.o
In file included from /media/sda2/home/a/temp/vpnclient/Cniapi.h:15,
                 from /media/sda2/home/a/temp/vpnclient/interceptor.c:33:
/media/sda2/home/a/temp/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
/media/sda2/home/a/temp/vpnclient/interceptor.c: In function ‘handle_vpnup’:
/media/sda2/home/a/temp/vpnclient/interceptor.c:313: warning: assignment from incompatible pointer type
/media/sda2/home/a/temp/vpnclient/interceptor.c:337: warning: assignment from incompatible pointer type
/media/sda2/home/a/temp/vpnclient/interceptor.c:338: warning: assignment from incompatible pointer type
/media/sda2/home/a/temp/vpnclient/interceptor.c:347:25: error: macro "for_each_netdev" requires 2 arguments, but only 1 given
/media/sda2/home/a/temp/vpnclient/interceptor.c:347: error: ‘for_each_netdev’ undeclared (first use in this function)
/media/sda2/home/a/temp/vpnclient/interceptor.c:347: error: (Each undeclared identifier is reported only once
/media/sda2/home/a/temp/vpnclient/interceptor.c:347: error: for each function it appears in.)
/media/sda2/home/a/temp/vpnclient/interceptor.c:351: error: expected ‘;’ before ‘{’ token
/media/sda2/home/a/temp/vpnclient/interceptor.c: In function ‘do_cleanup’:
/media/sda2/home/a/temp/vpnclient/interceptor.c:386: warning: assignment from incompatible pointer type
make[2]: *** [/media/sda2/home/a/temp/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/media/sda2/home/a/temp/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-8-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

Has anybody else run into this? What other information should  I post to troubleshoot this? Any suggestions on what to try messing with next?

Thanks.

---

### Post by f1r3br4nd on 2008-02-20
A-ha! Haven't tried this yet, but it might work...

[http://forum.tuxx-home.at/viewtopic.php?f=15&t=461](http://forum.tuxx-home.at/viewtopic.php?f=15&t=461)

---

### Post by f1r3br4nd on 2008-02-21
Yes, it worked. Here are the instructions I followed:

[http://projects.tuxx-home.at/?id=cisco_vpn_client](http://projects.tuxx-home.at/?id=cisco_vpn_client)

Basically, I downloaded the 8.01 version, patched it with the patch he made for rc kernels (i.e. not the final patch) and then applied the skbuff patch to make it compile on amd64.


New question, though. When I run vpnconnect from home (behind a Linksys WRT54G, firmware v4.00.7) I get the following message:
```

Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

```
What log files should I read to figure out why I'm failing to establish a VPN connection? I'm guessing it's because of my router, though. What ports does vpnclient need enabled in order to connect properly?

Also, a more general 'philosophical' question about broadband routers:

It seems anytime you're trying to use some service besides vanilla http, ftp, or telnet you have to configure your router to do port-forwarding to some specific IP address (e.g. bit torrent and many online games). That's fine, but if you prefer to have dynamically assigned IP addresses on your home network that means you end up having to log into the router every time to set up port forwarding. Also, what if more than one person on your network wants to use that service at the same time? How do you people who (unlike me) actually know what you're doing accomplish this? There's got to be a more elegant and automated way to do it!

---

### Post by peteguhl on 2008-02-21
Sounds like a file permission problem on either your profiles or certificates. For a quick fix, try this:

chmod -f 777 /etc/opt/cisco-vpnclient/Certificates
chmod -f 777 /etc/opt/cisco-vpnclient/Profiles

I'll see if I can't update the script I wrote to work with the new stuff after my Algorithms exam.

Pete

---

### Post by mkalle on 2008-02-22
I had some problems connecting aswell, but after disabling unused interfaces (wlan0) i could connect.

---

### Post by L8erG8er on 2008-02-25
peteguhl:

Just wanted to say thanks very much for your first post in this thread.  I installed the latest version of the vpnclient, so it didn't need any patches, but I could not get the thing to run without doing the init sequence each time.

With your commands at the bottom of your script, the vpnclient now works slicker than hot snot.  Thanks again!

---

### Post by inphektion on 2008-02-25
> **L8erG8er said:**
> peteguhl:

Just wanted to say thanks very much for your first post in this thread.  I installed the latest version of the vpnclient, so it didn't need any patches, but I could not get the thing to run without doing the init sequence each time.

With your commands at the bottom of your script, the vpnclient now works slicker than hot snot.  Thanks again!

So you are able to run on something newer than 4.8.00.0490-k9?  If so tell me the version please.

---

### Post by L8erG8er on 2008-02-26
Yes.  I installed the latest version of the vpnclient from here (same location):

[http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz]("http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz")

I put the .pcf files from my company's Cisco VPN in the proper directory and set permissions, etc. as per peteguhl's script in the first post of this thread.

My kernel is 2.6.22-14-generic, by the way.  After setting everything from peteguhl's script, I made launchers for each connection, and I am able to run them right after booting the computer, which is sweet.

---

### Post by L8erG8er on 2008-02-26
I'm sorry, the actual version name didn't all show up in the link.

Alexander Griesser named it:

vpnclient-linux-x86_64-4.8.01.640-K9, so it's Cisco version 4.8.01-0640.

---

