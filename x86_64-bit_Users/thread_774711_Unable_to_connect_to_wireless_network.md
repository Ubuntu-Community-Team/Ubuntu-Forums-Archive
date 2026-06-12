---
title: "Unable to connect to wireless network?"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by Jakob Moss on 2008-04-29
I have found a strange problem :(

When I try to connect to the wireless network at my school, it won't?
It asks for the passphrase, and I enter it. Then after a while, it asks for the same passphrase again??
The network is using 128-bit WEP encryption.

But the most strange thing is, that I can connect to my private wireless network??
It is mac-address-filtered, hidden-SSID and WPA2-personal encrypted?

Why can't I connect to the wireless network at my school??
Is it something about the WEP-encryption?

I am using this:
Intel Pro/Wireless 4965AGN 300-Mbit

---

### Post by felker2 on 2008-04-29
Are you using 8.04 and a Centrino Wifi chipset? If so, it could be this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223111](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223111)

Workaround: use an older kernel, or another wifi card. Or use Ubuntu 7.10.

---

### Post by ii bk ll on 2008-04-29
I am getting the same thing, I am trying to connect to my schools wireless internet and it keeps asking for the pass phrase. Have you had any luck getting it to work? I am not sure if I can connect to any wireless network because I live at school and havent had a chance to try a different network

---

### Post by Jakob Moss on 2008-04-30
I've tried to use WICD as my network manager...

I can (with some trouble) connect to my private (WPA2) network, but I don't know about the wlan at my school.
I will try it monday, and post how it went :)

---

### Post by villindesign on 2008-04-30
May I ask how you are able to connect to a WPA encrypted network? I also have the 4965AGN, and further a TRENDnet N router. I had to switch to WEP (and therefore 802.11g speeds) because I cannot connect to a WPA1 encrypted network.

Is the key at school a shared key?

---

### Post by Jakob Moss on 2008-04-30
With the gnome-network-manager (the standard) I just chose to connect and entered my ESSID (we have hidden the network name), selected WPA2 as the encryption, and entered the key?
That worked from the first moment :)

Now I use WCID, because I think (don't know yet) that it might be able to connect to the WEP-encrypted network at my school...
I WCID I can also connect to my WPA2 :)

No, it's not a shared key... It's open or what it's called :P

---

### Post by wyllbyll456 on 2008-04-30
I am using 64-bit processor and my wifi or ethernet isn't working. It worked fine on windows!
Maybe 8.04 has problems. D:
I might try 7.10... or would that not work???
O K  I  A M  A  N O O B  B I G  T I M E

---

### Post by Jakob Moss on 2008-05-03
I don't know if 7.04 would work...?

I will test my school's WEP-network with WICD monday! Then I will post a status report :)

---

### Post by Jakob Moss on 2008-05-05
Yes, it's working! :D

Now I can connect to both my school's WEP-network and my private WPA2-network :)

I am using wicd as network manager, instead of the standart gnome-network-manager!
When I shall connect to the WEP-network I need to choose WEP(hex) as the encryption, and then it's working :)

---

