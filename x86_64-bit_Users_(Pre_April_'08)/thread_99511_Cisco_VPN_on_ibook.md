---
title: "Cisco VPN on ibook"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by williamx on 2005-12-05
Has anyone here got the Cisco VPN-client up and running on an iBook or Powerbook? 

I`ve tried almost anything, but I`m a newbie to ubuntu...

-
William S.

---

### Post by gruepig on 2005-12-06
Last I tried (about a year ago), Cisco's Linux VPN client didn't work on PPC.  I found the vpnc package and have been using that instead.

Install with 'apt-get install vpnc' (or using aptitude or whatever).
Run 'sudo vpnc-connect' to connect.
Run 'sudo vpnc-disconnect' to disconnect.

vpnc-connect will prompt you for all your settings.  Alternately, you can save your settings in /etc/vpnc/default.conf, e.g., 

```

 IPSec gateway ip.of.vpn.con
 IPSec ID GROUPID
 IPSec secret GROUPPASS
 Xauth username YOURID
 Xauth password YOURPASS

```

If you leave any of these out, you'll be prompted at connect time.

Hopefully this will just work for you.  If it doesn't, post any errors you are getting and the output of 'ifconfig -a' and 'route -n' (in particular, you'll be looking for tun0).

---

