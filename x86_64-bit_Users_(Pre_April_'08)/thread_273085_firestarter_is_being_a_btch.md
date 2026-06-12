---
title: "firestarter is being a b*tch"
date: 2006-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-10-07
I dont remember why exactly i even install firestarter, but lately it's been being a real b*tch and not letting me uninstall it, even in recovery mode. For some reason every time i try to uninstall it, firestarter tries to start, and then it gives me a bunch of errors etc, etc. Look at this:

this is when i try apt-get remove

> The following packages will be REMOVED:
  firestarter
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1962kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169441 files and directories currently installed.)
Removing firestarter ...
 * Stopping the Firestarter firewall...                                         FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
                                                                         [fail]
invoke-rc.d: initscript firestarter, action "stop" failed.
dpkg: error processing firestarter (--remove):
 subprocess pre-removal script returned error exit status 3
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 100
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)


and when i try dpkg -r it gives me the same bullcrap... if anyone can help it'd be appreciated, the firewall doesn't even work anyway... everytime i start it says my kernel does not support iptables... even tho iptables in konsole returns: iptables v1.3.3

---

### Post by xstaticxgpx on 2006-10-08
*bump*

can anyone please help me with enabling iptables? I just recently installed the 2.6.18 kernel from kernel.org... am I gonna have to recompile/reinstall it with iptables enabled? And even if I do have to, I don't know how. I searched google and the forums both results show that this seems to be a unknown problem.

---

### Post by RAOF on 2006-10-09
Your kernel obviously doesn't have the ip_tables module loaded.  Either you can:
1) load that module (if it's built, but not loaded) with 
```
sudo modprobe ip_tables
```or 
2) if you built your kernel without IP Tables support you should load one of the Ubuntu kernels, and uninstall Firestarter from there.  The Ubuntu kernels are built with ip_tables support.

If you don't know how to rebuild your kernel with iptables support, you almost certainly don't need to be rebuilding your kernel **at all**.  Just use the Ubuntu ones, it's much, **much** easier :).

---

### Post by xstaticxgpx on 2006-10-09
yea, thats what I did, but isn't rebuilding a kernel just like building it in the first place? Which I certainly do know. I just don't know the parameter for iptables

anyway, ty for the reply

---

### Post by bartman on 2007-01-22
xstaticxgpx: Have you had any success with removing firestarter?

I'm having similar issues. My custom kernel HAS iptables support but the uninstall process still bugs out:
```
bartman@nw8240:~$ sudo dpkg --purge firestarter
(Reading database ... 123279 files and directories currently installed.)
Removing firestarter ...
 * Stopping the Firestarter firewall...                                  [fail] 
invoke-rc.d: initscript firestarter, action "stop" failed.
dpkg: error processing firestarter (--purge):
 subprocess pre-removal script returned error exit status 3
Errors were encountered while processing:
 firestarter
```

The problem is that Firestarter isn't even running because I've deleted it's configuration scheme. The problematic script is located at **/etc/firestarter/firestarter.sh**:
```
*snip*

if [ "$NAT" = "on" ]; then
*snip*
        INMASK=`/sbin/ifconfig $INIF | grep Mas | cut -d : -f 4`
*snip*
        if [ "$INMASK" = "" -a "$1" != "stop" ]; then
                echo "Internal network device $INIF is not ready. Aborting.."
                exit 3
        fi
fi

*snip*
```

Help anyone?

---

### Post by bartman on 2007-01-23
I have been able to partially remove firestarter by booting with the official edgy kernel. It seems that firestarter wasn't happy that I disabled packet mangling options in my kernel.

Anyway, the program binaries and scripts were uninstalled successfully but the *# dpkg --purge firestarter* command bugged out while trying to delete the configuration scheme... I guess I shouldn't have done it by hand!

---

