---
title: "acx module problems"
date: 2008-11-25
forum: x86 64-bit Users
---

### Post by nzadLithium on 2008-11-25
Every time I update the kernel, the acx module fails to work correctly for about a month with the new kernel. I have to keep using the old kernel even though the update program has gotten me a new one. About a month later the restricted modules and some other packages get updated, and then the new kernel finally works. Now this wouldn't be so bad as I don't really mind using an old kernel, but this time it happened during my update to intrepid, and during the update intrepid removed most of my old kernels, then it took ages to start up, so I booted in recovery and told dkpg to clean it up, it the proceeded to remove my only other kernel that worked which i really would have preffered it didnt :S, so now I'm stuck with a kernel that has some weird problem with the acx module... 

Basically what happens is I've never got the /etc/network/interfaces file to work correctly, so what i've done is made a script: 
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "linksys" key 0069003651 mode Managed
sudo dhclient wlan0
sudo ./iptables.sh
```

now this script executes fine, i get a working internet connection, but when I try to use my browser or any other network app, my internet connection dies within the space of 10 seconds, so every time i want to change page i have to re-run my internet script. As I said this happens on every new kernel i've got since gutsy :S and then it gets fixed, but usually i have an old kernel to wait it out on, this time I don't...

So I checked the acx firmware packages, they all seem to be up to date, so I downloaded the latest acx module and compiled it. It wouldn't compile due to some change within ioctl or something, but I found a patch so I patched it, then it compiled, but its still doing exactly the same thing, I use then net for about 10 seconds then the connection dies...

If anyone knows of a fix that would allow it to work on the new kernel I would be glad to know it, otherwise does anyone have any ideas how I can install one of the old Hardy kernels?

---

### Post by nzadLithium on 2008-11-25
well I give up on installing an old kernel, it'll take too long to get the nvidia package working... Plus the networking is doing the exact same thing on there now as well...

So anyone got any ideas what I could do to stop the net disconnects? Nothing shows up in dmesg, I have no idea why its doing it, if u want me to post up some logs, just tell me which ones :D

And when it fails, ifconfig shows that it still has an ip address. lsmod still shows acx as loaded, the device wlan0 still exists, it could be something to do with dhcp as I just tell it to get me a new ip via the dhcp program and it goes again, but i'm confused as to what it could be :S

---

### Post by nzadLithium on 2008-11-25
I found out just now, its not totally dead. It's still dead the majority of the time, I think it may be recovering the connection by itself and then losing it again? I'm not sure, but it still dies within 10 seconds, then after a while it suddenly works but again dies after several seconds. I'm completely lost as to what would cause this, other than really bad signal quality (which I have never had a problem with before, and I have not moved anything) or a driver/kernel issue. I uninstalled network manager as I have seen alot of people have had problems with it when using acx111 cards, but it doesn't appear to have made a difference.

---

### Post by nzadLithium on 2008-11-26
I've submitted a bug to launchpad. I'm still looking for a fix though :D

---

### Post by nzadLithium on 2008-11-26
well, i still have no idea what was wrong, but I have a fix, if anyone else gets this problem, set ur networking up using the program network-config, its available in the repos and seem to work better to me than the NetworkManager program :p (Network Manager won't even start anymore XD).

---

