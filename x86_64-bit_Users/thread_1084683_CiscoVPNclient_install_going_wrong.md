---
title: "CiscoVPNclient install going wrong"
date: 2009-03-02
forum: x86 64-bit Users
---

### Post by mandarb777 on 2009-03-02
Hello all,
I'm running Xubuntu intrepid 64-bit.  I have run the following patches:
cisco_skbuff_offset.patch
vpnclient-linux-2.6.24.diff
i got those from various searching (Google and these forums).
I installed earlier.  However, vpnclient command would not work.
I uninstalled and reinstalled with the following results:

```
$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.27-11-generic/build]/lib64/modules/2.6.27-11-generic/build

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.27-11-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib64/modules/2.6.27-11-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib64/modules/2.6.27-11-generic/build SUBDIRS=/home/Build/vpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/Build/vpn/vpnclient/.libdriver64.so.cmd for /home/Build/vpn/vpnclient/libdriver64.so
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
Copying module to directory "/lib/modules/2.6.27-11-generic/CiscoVPN".
Already have group 'bin'

Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Enabling start/stop script for run level 3,4 and 5.
Creating global config /etc/opt/cisco-vpnclient

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":
    /opt/cisco-vpnclient/license.txt

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/":
* New Profiles     : abington altoona beaver behrend berks brandywine COE-from-ISP COE-Wireless dickinson dubois EMS-from-ISP EMS-Wireless fayette greater_allegheny great_valley harrisburg hazleton ISPtoPSU lehigh_valley LIAS-VPN mont_alto new_kensington schuylkill shenango_valley smeal university_park wilkes_barre worthington_scranton york 
cp: cannot stat `vpnclient.ini': No such file or directory

Copying binaries to directory "/opt/cisco-vpnclient/bin".
Adding symlinks to "/usr/local/bin".
    /opt/cisco-vpnclient/bin/vpnclient
cp: cannot stat `vpnclient': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/bin/vpnclient': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/vpnclient': No such file or directory
    /opt/cisco-vpnclient/bin/cisco_cert_mgr
cp: cannot stat `cisco_cert_mgr': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/bin/cisco_cert_mgr': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/cisco_cert_mgr': No such file or directory
    /opt/cisco-vpnclient/bin/ipseclog
cp: cannot stat `ipseclog': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/bin/ipseclog': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/ipseclog': No such file or directory
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin".
    /opt/cisco-vpnclient/bin/cvpnd
cp: cannot stat `cvpnd': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/bin/cvpnd': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/cvpnd': No such file or directory
Copying libraries to directory "/opt/cisco-vpnclient/lib".
    /opt/cisco-vpnclient/lib/libvpnapi.so
cp: cannot stat `libvpnapi.so': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/lib/libvpnapi.so': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/lib/libvpnapi.so': No such file or directory
Copying header files to directory "/opt/cisco-vpnclient/include".
    /opt/cisco-vpnclient/include/vpnapi.h
cp: cannot stat `vpnapi.h': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/include/vpnapi.h': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/include/vpnapi.h': No such file or directory

Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient/Profiles (group bin readable)
    /etc/opt/cisco-vpnclient/Certificates (group bin readable)
chmod: cannot access `/etc/opt/cisco-vpnclient/vpnclient.ini': No such file or directory
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.

```


I am pretty sure these are the same as the results last time.
I am currently using vpnc but I keep getting kicked off the network (still says I'm still connected but I can't send/receive email, download, etc.)
so it'd be great to get the cisco working.
Thanks,
Dave

---

### Post by dcstar on 2009-03-03
> **mandarb777 said:**
> 
.........
so it'd be great to get the cisco working.
Thanks,
Dave

If you want a working Cisco VPN client then just install the **vpnc** and **kvpnc** packages - you can import .pcf files and I find it works fine.

---

### Post by radamo on 2009-03-04
> **dcstar said:**
> If you want a working Cisco VPN client then just install the **vpnc** and **kvpnc** packages - you can import .pcf files and I find it works fine.

I would agree.  I am a newbie and was able to install and setup vpnc with a bit of googling help on importing the pcf's.  It seems you need to "decode" the password string but a tool is available on line to do that.   Google is your friend...
RA

---

### Post by ncubede on 2009-03-04
> **dcstar said:**
> If you want a working Cisco VPN client then just install the **vpnc** and **kvpnc** packages - you can import .pcf files and I find it works fine.

Unless you need TCP tunneling or other Cisco-specific features, that vpnc does not yet implement.  I happily use vpnc, don't get me wrong, but I also have the native Cisco client for the few times I need it.

[http://projects.tuxx-home.at/ciscovpn/patches/](http://projects.tuxx-home.at/ciscovpn/patches/)

should have what you are looking for, the 4.8.02 stuff with 64bit patch worked fine for me.

---

### Post by gagnon88 on 2009-03-05
If you want to use vpnc or kvpnc, you'll need to decode the so-called "Group password" included in .pcf files. Use the following page to do so:

[http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode]("http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode")

I use Ubuntu 64 and I had a really hard time making cisco's proprietary client work. However, once you've hacked the group password, don't even bother using it :)

---

