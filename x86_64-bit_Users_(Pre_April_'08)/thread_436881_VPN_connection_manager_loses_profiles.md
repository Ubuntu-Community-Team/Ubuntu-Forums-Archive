---
title: "VPN connection manager loses profiles"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr. Brownstone on 2007-05-08
I've installed vpnc, openvpn, and the PPP Generic pptp connection-manager and I'm having problems with profiles.

For example: I add a new profile and it seems to stick. Then I add a second one and it appears in the profile-editor, but not in the submenu when clicking on the network icon so I cannot connect to it. If I then delete all profiles and try to start-over, not even new profiles are appearing anymore!

Thanks for any assistance. :)

---

### Post by Mr. Brownstone on 2007-05-08
I managed to delete the old profile using gconf-editor and manually deleting the folder in ~/.gconf/system/networking/vpn-connections/ , but now I'm victim to the known segfault problem with 64bit pptp: [http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2006/11/24/networkmanager-pptp-with-ubuntu-610-edgy-eft-on-amd64-crash-workaround/](http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2006/11/24/networkmanager-pptp-with-ubuntu-610-edgy-eft-on-amd64-crash-workaround/)

Ah well.

---

### Post by Mr. Brownstone on 2007-05-15
I still haven't been able to resolve the segfault problem with the default Network Manager VPN capability, but KVpnc works well in its place, so I have a full solution offered by two different applications. (I connect to both Windows and Cisco VPNs.)

I hope this is helpful.

---

