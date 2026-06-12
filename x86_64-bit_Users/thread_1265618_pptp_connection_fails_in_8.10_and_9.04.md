---
title: "pptp connection fails in 8.10 and 9.04"
date: 2009-09-13
forum: x86 64-bit Users
---

### Post by CowboyCoffee on 2009-09-13
I am having problems getting connected to my work VPN. I was able to connect with 8.04 without issues, but when I updated to 8.10 I lost the ability to get connected. The problem has carried over to 9.04 as well. I am able to get connected from a very slow and old computer running 32-bit 9.04 from my same home network. I followed the steps here [http://mylinuxnotebook.blogspot.com/2009/05/pptp-vpn-ubuntu-linux-howto.html](http://mylinuxnotebook.blogspot.com/2009/05/pptp-vpn-ubuntu-linux-howto.html) for both setups. Could this be a 64-bit thing, or am I doing something wrong? Any help would be appreciated. Thanks.

---

### Post by katakaio on 2009-09-13
It's not likely. To my knowledge, the VPN tools aren't architecture specific. Are you using the VPN utility in Jaunty's NetworkManager applet? If not, I would recommend installing **network-manager-pptp** and giving it a whirl. It allowed me to connect to my work VPN finally after much trial and error. Hope it helps!

---

### Post by CowboyCoffee on 2009-09-14
Installing network-manager-pptp was one of the first things I did, but I am still coming up empty. All settings match my working connection from the other pc too. Any other suggestions?

---

### Post by sean.grooms on 2009-09-14
I would love to see a solution for this!  My USB CDMA dongle uses PPP to connect as well.  It functions flawlessly on 32-bit Jaunty (netbook remix), but fails to connect on either of my 64-bit machines...

---

