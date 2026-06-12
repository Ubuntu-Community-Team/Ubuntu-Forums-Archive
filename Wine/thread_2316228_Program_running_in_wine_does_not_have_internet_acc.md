---
title: "Program running in wine does not have internet access"
date: 2016-03-06
forum: Wine
---

### Post by Pascal_Herms on 2016-03-06
Hi all,

I hope someone here can help me with this issue, because it's driving me crazy.
I have this windows program which is not available on Linux, so I have  to use wine to run it. So, on my Ubuntu 15.10 x64 system I have installed  wine 1.9.4, following the installation guide on winehq.org, including  the latest wine_gecko and wine-mono.

After that I have installed the program using the PlayOnLinux  installation scripts, which did complete succesfully. Now when I start  the program it cannot connect to the internet.

I have tried to remove libnss-mdns and install lib32nss-mdns. I have  also edited the /etc/nsswitch.conf file, so the line reads hosts: files  dns myhostname mdns4. 

I have also edited /etc/NetworkManager/NetworkManager.conf and commented  out the line dns=dnsmasq, so that /etc/resolv.conf contains the correct  DNS nameservers for my network, instead of the default 127.0.1.1.

I have exported WINEARCH-win32.

But still after all this, the program running in wine still has no network access.
Now I suspect the problem is somewhere in Ubuntu, because when I quickly  setup an Arch install in a VM running xfce, and install lib-nss, edit  /etc/nsswitch.conf, install wine, wine_gecko and wine-mone, install the  same program and run it, it does have internet access without any  problems.

Does anybody know how I can enable this program running in wine on Ubuntu 15.10, to connect to the internet?

---

### Post by Pascal_Herms on 2016-03-06
I'm not sure if this has anything to do with it, but after I have disabled the IPv6 in the networkmanager, the program I was running under wine, could connect to the internet.

---

