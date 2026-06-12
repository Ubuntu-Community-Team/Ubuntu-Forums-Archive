---
title: "kubuntu amd64 Dapper F4: kwifimanager setups fine but 1 step away from connecting"
date: 2006-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Brachabre on 2006-02-19
wow It's almost there! oh yeah I'm on Kubuntu amd64 Dapper Flight4 using a Linksys WUSB11   802.11b usb wireless card (Atmel chipset)    kwifi detects what my card    and i setup the network info under configuration settings.  I don't think this is dapper-only problem b/c i think it was also the same problem on breezy so forgive me if its in the wrong section.

Network name=done (my network name is there)
Connectin type=Managed
access point=done   (the gateway MAC is recognized and listed)
Freq channel=done  (setup to the same frequency as gateway)
WEP encryption=done (kwifi certifies my key is a 64bit hex;type=open)

I press apply on all settings --->Activate


Now im back to the main screen---->network name is listed, access point MAC is listed, all i need is an IP address

So, I then click  search for networks------>Whola, the 3 networks that appear when i search for networks under windows.  I click my network to connect and then it gives me this nice message below


ERROR MESSAGE------>"Aborting network switching due to invalid WEP key specification"



beats me on what to do...any help is appreciated greatly. Thank you.

---

### Post by Brachabre on 2006-02-20
am i screwed? =\

---

### Post by rne13 on 2006-02-21
[QUOTE=Brachabre]am i screwed? =\[/QUOTE]
I'm not sure, but I can assure you - you're not alone (as it may have seemed).

I just switched from experimenting with Ubuntu and Edubuntu (Flight3 and 02/xx daily builds) where everything worked fine - to Kubuntu Dapper Flight4.

I'm not sure yet whether it is Kubuntu or Flight4 (and it is NOT AMD64 since i am regular i386) but I have same symptoms.
Also, when I try to configure 'ath0' interface I get nasty KDE app crash dialog.

---

### Post by Brachabre on 2006-02-21
yes i did that too....tried enabling the eth0 port under the system control panel labeled "network settings"   it enabled and just disables itself than kde gives crash message

---

### Post by Daggett on 2006-02-22
[QUOTE=Brachabre]
ERROR MESSAGE------>"Aborting network switching due to invalid WEP key specification"[/QUOTE]

I have the same USB adapter and it works great under Kubuntu Breezy.  I know this is obvious and you probably thought of it already, but:

1. Did you enter your WEP key as a hexadecimal value?  I think your original post says you did.  

2. Did you check it several times?  It's easy to mistype the key, especially when it's a long hexadecimal value. 

3. Did you specify that it was the right key number?  In most cases, it will be key number 1. 

Check your /etc/network/interfaces file.  It should include at least the following underneath your iface definition:

   wireless-mode managed
   wireless-essid (your ssid, no quotes)
   wireless-key1 (hexadecimal key, no quotes)

---

