---
title: "Ubuntu 8.10-Intrepid Ibex x86_64 - eth0 settings not saving."
date: 2008-11-04
forum: x86 64-bit Users
---

### Post by caladan1810 on 2008-11-04
Hi everyone I'm having issues with the ethernet settings not saving.

Network settings are not being saved when session closes and system reboots. Unable to save settings for eth0. 
When I reboot I have no network access and have to setup the network with IPA/Net Mask/Gateway/DNS.

Is there a way this can be fixed as I have rebooted several times and every time I've had to this same problem.

I'm using the following system:
Operating System: Ubuntu 8.10-Intrepid Ibex x86_64 
Kernel: kernel 2.6.27-7-generic
DM: Gnome  2.24.1
CPU: Intel Core2 Duo 2.6 GHz
RAM: 3 GB
Ethernet: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
Dell XPS M1530

any assistance greatly appreciated.

thanks
Cal.

---

### Post by TryHarder on 2008-11-04
You can try to edit network interface file manually. type
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo gedit /etc/network/interfaces
```
in opened window insert manually your network configuration.
Then if you need to setup DNS edit /etc/resolv.conf file.
Save and close, restart, check for changes.
Additional info about editing those file found in [https://help.ubuntu.com/7.10/server/C/network-configuration.html](https://help.ubuntu.com/7.10/server/C/network-configuration.html)

---

### Post by Arup on 2008-11-13
Its quirky but it works, you have to delete all the auto entries, then select new connection, give it a name and select system tab. Then go to the IPV4 tab and manually enter all the IP, gateway, DNS etc and click OK, it works, far better than the disaster in Kubuntu, where no matter whatever you input, it won't take your connections till you manually do the interfaces file. Best part in the new Gnome network manager is that you can set the MTU for your connection, a very thoughtful and nifty add on.

---

### Post by caladan1810 on 2008-11-13
> **Arup said:**
> Its quirky but it works, you have to delete all the auto entries, then select new connection, give it a name and select system tab. Then go to the IPV4 tab and manually enter all the IP, gateway, DNS etc and click OK, it works, far better than the disaster in Kubuntu, where no matter whatever you input, it won't take your connections till you manually do the interfaces file. Best part in the new Gnome network manager is that you can set the MTU for your connection, a very thoughtful and nifty add on.

Thank you a 1000 times it worked

---

