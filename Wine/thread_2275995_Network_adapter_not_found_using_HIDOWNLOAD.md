---
title: "Network adapter not found using HIDOWNLOAD"
date: 2015-04-29
forum: Wine
---

### Post by mike311 on 2015-04-29
I managed to install Hidownload using Wine,however it will not detect my network adapter,I had the same problem with Wireshark but after these commands
It listed my wlan 0 and other adapters

sudo addgroup _system wireshark
sudo chown root:/wireshark /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
sudo usermod _a _g wireshark myusername to find

It listed my wlan and other stuff

Is there a similiar command i could use for Hidownload it is located in browse C: using wine 

Im guessing im not putting the paths in right 

I did try to copy the above command and change the system name to Hidownload

As its in a different folder can i still somehow set it up so its looks in the wine system?

Thanks

---

### Post by mike311 on 2015-04-30
No good guys? .Need to resolve this problem asap. Thank you

---

