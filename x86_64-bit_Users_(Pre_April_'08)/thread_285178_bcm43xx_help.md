---
title: "bcm43xx help"
date: 2006-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by CeeDub on 2006-10-26
I'm running amd64 ubuntu and I'm trying to get my wireless network to work. this is the output of iwconfig:

> eth1      IEEE 802.11b/g  ESSID:"SaulBack"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I've been following this howto exactly with the fwcutter.  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")
I can see the different routers through Network Manager, but I can't connect.  Can anyone help out?

---

### Post by FedeXX on 2006-10-26
> **CeeDub said:**
> I'm running amd64 ubuntu and I'm trying to get my wireless network to work. this is the output of iwconfig:



I've been following this howto exactly with the fwcutter.  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")
I can see the different routers through Network Manager, but I can't connect.  Can anyone help out?

It doesn't work for me too from the console (dhclient), but it works from menu, system, networking by turning off and on the broadcom (it takes some time to do it)

If your kernel is 2.6.17 or above dhclient will work, but only after an 
```

sudo ifconfig eth1 down && sudo ifconfig eth1 up

```

Try...! Good luck ;)

---

