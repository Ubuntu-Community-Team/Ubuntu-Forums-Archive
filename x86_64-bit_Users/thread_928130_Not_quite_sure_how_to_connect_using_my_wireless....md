---
title: "Not quite sure how to connect using my wireless...."
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by CaesarsAdvocate on 2008-09-23
Hi,

Trying to make my wireless work (my only option to access the internet) has been an endless source of frustration. To describe it simply: I have no idea what's going on.

Ran lsusb, ifconfig, iwconfig. Posted the results here:
[http://pastebin.com/m2bf91bf8](http://pastebin.com/m2bf91bf8)

Dunno how to interpret them. Read the "documentation" on the official Ubuntu site - makes no sense. Tried configuring the network, using the network-manager button.... dunno what's going on. I keep restarting into XP to connect and try and figure it out, but I just don't know......

I mean, I entered the configuration data (Network name, password, encryption, tried the static option also - I have all the IPs), and after entering configuration data and saving, there is no option to connect under the network-manager.

.....
CA.

---

### Post by lisati on 2008-09-23
Do any wireless networks show up when you enter the following at the terminal?
```
iwlist scan
```

---

### Post by CaesarsAdvocate on 2008-09-23
In iwconfig, ESSID shows my network (in the page I linked to it doesn't, but it does since I configured the connection).

Does that answer the question? I just want to avoid restarting too often (now I'm in Windoze XP).

---

### Post by CaesarsAdvocate on 2008-09-23
I've started reading the Ubuntu help (wireless networking), and reached the stage when it suggested to:

Boot the kernel with the pci=noacpi option.

(if iwconfig shows my network name but I still can't connect).

---

### Post by CaesarsAdvocate on 2008-09-23
iwlist scan
---------


wlan0     Scan completed :
          Cell 01 - Address: 00:1B:9E:8D:4A:22
                    ESSID:"Kransen"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/100  Signal level=-74 dBm  
                    Encryption key: on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000020dc3b9c66b

============================================================

My network properties, as displayed in windoze, are:

Network Authentication: WPA2-PSK
Data Encryption: AES

---

### Post by CaesarsAdvocate on 2008-09-25
You know what, don't bother.
I'll go to a windoze forum and ask how to reformat the ext3 partitions into FAT or NTFS.

---

### Post by Yellow Pasque on 2008-09-25
> You know what, don't bother. I'll go to a windoze forum and ask how to reformat the ext3 partitions into FAT or NTFS.
You have my deepest sympathies.

Your wireless interface appears to be up, but not configured correctly. For example, it doesn't show an associated access point and it shows encryption off.

Try the following commands:
```
man iwconfig
man ifup
```

---

