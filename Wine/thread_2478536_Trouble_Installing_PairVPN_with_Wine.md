---
title: "Trouble Installing PairVPN with Wine"
date: 2022-08-29
forum: Wine
---

### Post by cryoworm2 on 2022-08-29
[COLOR=#333333][FONT=&quot]Hello, I'm running Ubuntu 20.04 and installed Wine 7.0[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I am trying to install PairVPN:
[/FONT][/COLOR]
[https://pairvpn.com/](https://pairvpn.com/)

[COLOR=#333333][FONT=&quot]I right click the exe file and run it with Wine. It goes through the installation but then it fails with an error message:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]'Fail to install PairVPN Network Driver, error=11001'[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I'm very new with Linux, but is it difficult to install a network driver like this with Wine?[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Any ideas how to go about troubleshooting this? Or can anyone try to get it to work themselves?[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Cheers,[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]cryoworm[/FONT][/COLOR]

---

### Post by TheFu on 2022-08-30
It is doubtful that Windows VPNs will work under WINE+LInux.  VPNs tend to tie deeply into the OS kernel, which WINE won't have access.

But the good news is that if you are able to figure out which VPN PairVPN is actually using, then you can use the native Linux version of that software instead.  Most VPNs that aren't corporate will be using openvpn at the core. The openvpn support for Ubuntu is excellent, but it does require drivers and running as root.  

So ... first figure out which VPN technology is actually being used by PairVPN. Setting up a VPN client with the standard VPN tools isn't very hard - perhaps a 3 on the 1-10 scale.

---

