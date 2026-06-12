---
title: "Strange WiFi problem"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kmramki on 2006-03-26
I have a HP Pavilion ZV5260. My wireless card is (found from lspci) Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03). I have the netbc564 driver loaded into ndiswrapper. 

Now, to start the wireless, I use these:
> sudo modprobe ndiswrapper 
> sudo iwconfig wlan0 essid "whatever_essid" 
> sudo dhclient wlan0

Sometimes, this does not work... Sometimes, iwlist returns no network at all. Sometimes, iwlist shows my network, but iwconfig does not connect to it (ifconfig shows HWaddr 00), and sometimes, iwconfig connects, but dhclient just wont get me an IP address. What's worse, in the last case, wifi-radar *says* it got an address, but still I cannot ping the router. But sometimes, it all runs so smoothly. 

I suspect that there is something abt the radio.... I dunno. One thing that *seems* to make things work (I have not tested this enough times) is if I wait for sometime after modprobing before I iwconfig. 

Worst of all, sometimes, I cannot do anything if all fail. I cannot even rmmod ndiswrapper, and I have to *reboot*. It feels more like Windoze ](*,) . Any idea what's happening here? And is there any way I can stop using ndiswrapper?

---

