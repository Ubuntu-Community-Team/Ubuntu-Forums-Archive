---
title: "RT2500 - no WPA option"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by _newbie on 2007-06-15
hi,

 i managed to install ubuntu 7.04 onto my MSI S271 notebook that has an RT2500 wifi card. The driver seem to work the only thing is that I can not select WPA as encryption in the gnome network config tool ... how do I connect to a WPA AP with hidden ESSID with gnome net config?

I could get it work by editing /etc/network/interfaces when inserting:

```

auto ra0
iface ra0 inet dhcp
pre-up iwconfig ra0 essid YOUR-SSID
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=7
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="YOUR-WPA-PSK"
pre-up iwpriv ra0 set TxRate=0

```

---

### Post by _newbie on 2007-06-15
according to this post  [http://ubuntuforums.org/showthread.php?t=463237&highlight=rt2500+wpa&page=2]("http://ubuntuforums.org/showthread.php?t=463237&highlight=rt2500+wpa&page=2")
> 
rt2500 does not support linux WPA extensions.
Network-manager requires linux WPA extensions.

:(

---

### Post by titaniumlou on 2007-09-10
I think you can get this working with ndiswrapper, but are you saying that you got it working so long as you manually edited the interfaces file above?

---

