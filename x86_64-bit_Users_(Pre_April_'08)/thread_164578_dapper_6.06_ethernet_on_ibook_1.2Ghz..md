---
title: "dapper 6.06 ethernet on ibook 1.2Ghz."
date: 2006-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by larrinski on 2006-04-23
I have given the wifi a college try(probably more like elementary...), and have given up. There is just too much playing around to do when I don't have any internet connectivity in ubuntu.:confused: 

  So, my question is, how do I get the ethernet to work? I have tried to go into network and select activate for it (eth1),and it says active. The status though says Idle when looking in Network Connection. The network connection in the menu bar shows packets going back and forth, but I have no internet. If I can get this running, which I think it's close, I will see if I can connect my ibook to my imac with an ethernet cable and surf from there. I am hoping that I can use my imac(which connects to my airport express wirelessly) as a sort of router for my ibook. I feel that if I can just get ubuntu "online" then I can play around with the wifi thing latter...

---

### Post by ssam on 2006-04-23
did you configure the ethernet before you activated it? select eth0 click the properties button in system->administration->networking. if you are lucky setting configure using DHCP will work.

if the imac running linux or mac os X?
in mac os x, go to system preferences -> sharing -> internet
on linux you will need to install firestarter (or look up configuring iptables manually.) in the setup wizzard you can enable sharing.

---

### Post by 3rdalbum on 2006-04-24
I'm assuming that you have DHCP turned on in Ubuntu?

Try turning it off and using hardcoded IP addresses instead (you may need to consult a website or someone to find the DNS addresses). I'm not the only one who's had mysterious problems using DHCP on an iMac.

---

