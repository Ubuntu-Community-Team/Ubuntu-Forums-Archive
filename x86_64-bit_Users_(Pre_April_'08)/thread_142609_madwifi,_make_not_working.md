---
title: "madwifi, make not working"
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bonjourmate on 2006-03-10
Just switched to Ubuntu from OS X(tried Debian previously but was unhappy.  Decided to switch completely after the Live ubuntu CD autodetected EVERYTHING) and am trying to setup madwifi to work with a Netgear WG511T.

I thought I correctly installed the headers but when I use make I get a whole ton of errors.

I really don't know where to start on solving this problem and any help would be great.

Thanks.

---

### Post by Bonjourmate on 2006-03-10
Ok, yeah.  I think I've narrowed it down to the kernel headers what-not...  really wish I could find some documentation on what this is.

Anyways, my kernel is 2.6.12-10-powerpc but I can't seem to find any way to get the headers (synaptic didn't seem to work and using apt-get gives the following)

root@Wookie:~# apt-get linux-headers-2.6.12-10-powerpc
E: Invalid operation linux-headers-2.6.12-10-powerpc

---

### Post by ssam on 2006-03-11
hi

first point its recommented on ubuntu that you use sudo rather than loggin in as root, have a look at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for info.

```
apt-get linux-headers-2.6.12-10-powerpc
```
should be 
```
sudo apt-get **install** linux-headers-2.6.12-10-powerpc
```

you will probably also need
```
sudo apt-get install build-essential gcc-3.4
```

if your are still getting errors can you post them here

good luck

---

### Post by Bonjourmate on 2006-03-11
Alright, got this

```
bonjourmate@Wookie:~/madwifi-ng$ make
Checking requirements... ok.
Checking kernel configuration... ok.
sed: can't read SNAPSHOT: No such file or directory
echo -n '#define SVNVERSION "' > svnversion.h
/bin/sh: svnversion.h: Permission denied
make: *** [svnversion.h] Error 1

```

Not sure what that means.

---

### Post by Bonjourmate on 2006-03-12
Anyone know?

---

### Post by jdp on 2006-03-13
"Permission denied" error would indicate that you should probably use **sudo make** to over come them.

---

### Post by Bonjourmate on 2006-03-13
[QUOTE=jdp]"Permission denied" error would indicate that you should probably use **sudo make** to over come them.[/QUOTE]

Heh, received this.

```
bonjourmate@Wookie:~/madwifi-ng$ sudo make
Password:
Checking requirements... ok.
Checking kernel configuration... ok.
sed: can't read SNAPSHOT: No such file or directory
echo -n '#define SVNVERSION "' > svnversion.h
if [ -d .svn ]; then \
        echo -n "1473" >> svnversion.h; \
elif [ -s SNAPSHOT ]; then \
        echo -n "" >> svnversion.h; \
else \
        echo -n "2006-03-13" >> svnversion.h; \
fi
echo '"' >> svnversion.h
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/home/bonjourmate/madwifi-ng/ath_hal'
make -C /lib/modules/2.6.12-10-powerpc/build SUBDIRS=/home/bonjourmate/madwifi-ng/ath_hal MODVERDIR=/home/bonjourmate/madwifi-ng/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-powerpc'
  CC [M]  /home/bonjourmate/madwifi-ng/ath_hal/ah_osdep.o
  LD [M]  /home/bonjourmate/madwifi-ng/ath_hal/ath_hal.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/bonjourmate/madwifi-ng/ath_hal/.hal.o.cmd for /home/bonjourmate/madwifi-ng/ath_hal/hal.o
  CC      /home/bonjourmate/madwifi-ng/ath_hal/ath_hal.mod.o
  LD [M]  /home/bonjourmate/madwifi-ng/ath_hal/ath_hal.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-powerpc'
make[1]: Leaving directory `/home/bonjourmate/madwifi-ng/ath_hal'
make[1]: Entering directory `/home/bonjourmate/madwifi-ng/net80211'
make -C /lib/modules/2.6.12-10-powerpc/build SUBDIRS=/home/bonjourmate/madwifi-ng/net80211 MODVERDIR=/home/bonjourmate/madwifi-ng/net80211/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-powerpc'
  CC [M]  /home/bonjourmate/madwifi-ng/net80211/if_media.o
cc1: warnings being treated as errors
In file included from include/linux/skbuff.h:30,
                 from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/bonjourmate/madwifi-ng/net80211/if_media.c:58:
include/net/checksum.h: In function 'csum_and_copy_from_user':
include/net/checksum.h:34: warning: pointer targets in passing argument 2 of 'csum_partial_copy_generic' differ in signedness
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/bonjourmate/madwifi-ng/net80211/if_media.c:58:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
make[3]: *** [/home/bonjourmate/madwifi-ng/net80211/if_media.o] Error 1
make[2]: *** [_module_/home/bonjourmate/madwifi-ng/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-powerpc'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bonjourmate/madwifi-ng/net80211'
make: *** [modules] Error 1

```

---

### Post by jdp on 2006-03-13
Where did you get the source for MadWifi?  Their current codebase is in [http://madwifi.org/browser/](http://madwifi.org/browser/) in the **trunk** section and the old codebase is in the **cvs-import** section.  How long ago did you grab the code if it was from the trunk section?

I know nothign of their code setup other than what I read on the madwifi.org site, but thise seems the most logical starting point.

---

