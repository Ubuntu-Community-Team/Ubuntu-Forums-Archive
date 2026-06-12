---
title: "Problems with networking."
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by pokechu on 2007-05-03
First problem:
My Wifi-Radar doesn't detect the wlan0 interface, whenever I launch the Wifi-Radar app it couldn't detect wlan0. I used to have my wireless device installed as eth1 but due to some problems I reinstalled it as wlan0. But now whenever I boot up my laptop, Wifi-Radar or Gnome Network Manager couldn't detect wlan0 as a wireless device, hence not detecting any wireless network. HELP? I could still associate with my AP using iwconfig in the terminal. I could surf the net, but just couldn't get wifi-radar or g-network-manager to work.

Second problem:
Networking with my Windows XP box used to work when I'm connected to the wireless. But now even though I could connect to the net while being associated with my AP, I still couldn't reach my router page, 192.168.1.1 nor my windows box. Any ideas why? It used to work. 

Oh yeah, whenever I boot up Ubuntu, the bar stucks half way for a very very long time, though I could still boot into Ubuntu. Never happened before until I messed with the networking settings. Then I tried booting Ubuntu in recovery mode, I found out that it stucks at configuring network interfaces part for a very long time. So I guess it must have everything to do with all this. I'm using openDNS, does that have to do with any of these problems? Because I had to reinstall the whole wireless card with ndiswrapper when I started using openDNS. Though it might not be it's fault, but it's when I configured everything to work with openDNS that I started messing the configs up, so I reinstalled the wireless card and now networking doesn't work for me. Please help! Thanks in advance. I know I could count on you guys here. Thanks. I'm a Linux newb, been using for 2 months or so.

---

### Post by chriscando on 2007-05-03
For the first problem, you might try looking in /etc/wifimanager/ (sorry i dont know the exact location, but something like that) for a config file. I believe there is an option to set the interface. You might just want to make sure its set to wlan0.

Second problem: so you can connect to the net just fine (google and stuff), just not the router or anyother computers on the local network?

---

### Post by pokechu on 2007-05-03
Yeah, exactly, for the second problem. I can google or msn just fine, just couldn't connect to the routers and other computers. Thanks!

---

### Post by chriscando on 2007-05-04
You might try using this port scanner called 'nmap' to help troubleshoot. You can apt-get it:
```
sudo apt-get install nmap
```
And then port scan your local network to detect other hosts
```
nmap 192.168.1.*
```

If it returns nothing its possible that your windows box has a firewall and is rejecting traffic. Also, maybe your router's address is something different than 192.168.1.1, if it has been reset maybe it defaults to something else (192.168.0.1 ??). Another way to check is to see if you windows box can connect to the router.

Btw, did you get wifi-radar to detect wlan0?

---

### Post by pokechu on 2007-05-04
Yeah, I got that wlan0 interface working with wifi-radar. Regarding the second problem, it used to work. I used to be able to connect to my fileshare in Windows XP box. Just that now it stopped working. I have no idea why. And when I connect the laptop using LAN cable, I could access the fileshare again. Just not with the wireless connection. Help! Using a D-Link DSL G604T Wireless Router here. Any idea which configurations to change to allow the traffic?

---

### Post by chriscando on 2007-05-04
check the settings on your routing table, type 'route'
Sometimes I would have problems when switching from wired to wireless. Sometimes traffic would be directed to my wired interface (eth0) instead of my wireless (eth1). If you see both interfaces up when you type route, do a 'sudo ifdown <wired-interface>' and see if that works.

---

### Post by chriscando on 2007-05-04
Also, regarding the long boot time. I edited my /etc/networking/interfaces file and commented everything except the lo entries. I think that wifi-manager or whatever you use will bring the network up when you login anyway. But at anyrate this fixed the problem for me. My /etc/networking/interfaces file looks like this:

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```

---

### Post by pokechu on 2007-05-04
OMG! Thanks man! It works. Thanks for the help. Greatly appreciated! Thanks a lot. You people are marvelous.

---

### Post by pokechu on 2007-05-04
Hey, I got pretty much everything working. Just that the Network-Manager-Gnome couldn't detect the wlan0 interface. Any ideas? Thanks!!

PS: I got it now. THANKS!

---

