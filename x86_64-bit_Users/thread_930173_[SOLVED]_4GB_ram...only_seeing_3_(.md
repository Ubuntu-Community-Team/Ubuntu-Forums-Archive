---
title: "[SOLVED] 4GB ram...only seeing 3 :("
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by gm04030276 on 2008-09-25
So I took two 1GB sticks out of one of my boxes and put it into this one making it up to 4GB. Planning some video editing with cinelerra and it will no doubt help :) But on rebooting it seems to have only found 3GB. Its running 64bit system on a C2D E6700 and the board (Asus commando) can take 8 I think...certainly 4 anyway!
Anyone know why its only seeing 3?

Thanks

---

### Post by uniko on 2008-09-26
How much memory BIOS shows? Does it report the full 4GB or something else? If BIOS shows only 3GB, then there could be some BIOS setting that needs to be changed.

---

### Post by bregale on 2008-09-26
i have same problem bios shows 4gb but os only shows 2.7 gb and im running ubuntu
any answers will be greatfull 
    thanks

---

### Post by uniko on 2008-09-26
Check out this thread: [http://ubuntuforums.org/showthread.php?t=413749]("http://ubuntuforums.org/showthread.php?t=413749") and look if you have similar setting in your BIOS. 

Bregale: are you running a x86_64 version too?

---

### Post by soxs on 2008-09-26
post the output from ```
uname -m
``` to confirm what you are running

---

### Post by punkybouy on 2008-09-26
Read your bios manual. Many bioses load code into RAM once you add more than say 3 GB of RAM and at 4 GB it is not unusual to see memory "losses" like you see.

---

### Post by punkybouy on 2008-09-26
Sorry, I meant to say they reserve memory for certain things.

---

### Post by mike1234 on 2008-09-26
In any 32-bit operating system, the virtual address space is limited, by definition, to the size of a 32-bit value: 
 
232 = 4,294,967,296

4,294,967,296 / (1,024 x 1,024) = 4,096

What's "missing" is being used by your OS.

Try 64 bit OS.

M.

---

### Post by gm04030276 on 2008-09-30
After a little bit of googling, I came across a archived mail message that was saying that memory needed to be remapped above 3GB because the address space after that would go to the graphics card. So I was restarting a few days later and thought I would take a look in the bios to see if I could see anything and lo and behold there was an "enable memory remapping" feature...so...if you have 4GB+ of memory and your computer isn't seeing it all...make sure you have memory remapping on in your bios...i think i found it under chipset settings on an asus commando, i would assume similar for other asus boards...can't say about other manufactures but have a look for it :)

---

### Post by soxs on 2008-10-01
> **gm04030276 said:**
> After a little bit of googling, I came across a archived mail message that was saying that memory needed to be remapped above 3GB because the address space after that would go to the graphics card. So I was restarting a few days later and thought I would take a look in the bios to see if I could see anything and lo and behold there was an "enable memory remapping" feature...so...if you have 4GB+ of memory and your computer isn't seeing it all...make sure you have memory remapping on in your bios...i think i found it under chipset settings on an asus commando, i would assume similar for other asus boards...can't say about other manufactures but have a look for it :)

It depends on the bios (award, american) and waether it's a shrinked laptop one or not.

---

### Post by Nikos.Alexandris on 2008-10-11
Apologies for the long post. Please take some time and read the problem I present. I would highly appreciate it if someone knowledgeable can shed some light.


**The laptop**

I own a Samsung R20, bought on March 2007 [COLOR="Red"][1][/COLOR]: a fully MS-compatible laptop :-). This laptop has following ID: MODEL: **NP-R20F001/SEG**, S/N: **353 V93 HP3 000 16Y** and had a **07SH** BIOS version.

This laptop was advertised with (technically at least) support for up to 4GB RAM (whenever the 4GB SODIMMs would appear on the market).[COLOR="Red"][2][3][/COLOR]
 

**The story**

Back in February 2008 I tried to use two non-original(=non-Samsung) 2GB RAM's. In fact, I tried several in different stores but none worked. The combination of 2x 2GB RAM SODIMM's [COLOR="Red"][4][/COLOR] would not let the machine start or the BIOS would take 2-3 minutes to read the whole RAM and afterwards it could not boot. Sometimes the boot process was starting but freezing at some random point.

I was told to upgrade the BIOS from Samsung-Germany [COLOR="Red"][5][/COLOR] (*some Samsung guy told me so while another one said "we never recommend or customers to upgrade the BIOS"!!*). So I did from **07SH** to **14SH** using an ISOCD which can be found in Samsung's global download page [COLOR="Red"][6][/COLOR]. The problem was not fixed. I had a couple of conversations with Samsung Support people but nothing really came out.

Some days ago I bought 2 original 2GB Samsung PC2 RAM simms for my machine and built them in. Thhttp://www.samsung.de/common/contactus.aspxe BIOS is again very slow reading the memory. But I can boot :-) Yet, Ubuntu sees only 3GB. I am convinced that it is about the firmware.

There is a 15SH BIOS version but only available as an windows exectable file (for  XP/Vista) [COLOR="#ff0000"][7][/COLOR].


**The problem**
I don't have anymore the original DVD with the MS operating system (lost it) and I don't want to buy any, to get an illegal copy or just ask one from the store where I got the laptop. Actually I want to avoid messing up my system again by installing any MS operating system, which rewuires to back-up data, free-up xxGB of hard disk space, loose 3-4 hours and eventually end-up with a broken machine (..imagine windows crashing while upgrading the firmware!!).
Samsung wont provide any support for Linux as far as I know. Well, back then when I ordered the laptop I did not think that it would be **required to upgrade the BIOS in order to enable full 4GB support in a machine that was advertised with 4GB support**.


**More details**

# linux version
nik@vertical:~$ uname -a
Linux vertical 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

# total memory
nik@vertical:~$ grep MemTotal /proc/meminfo
MemTotal:      3096060 kB

# memory reserved
nik@vertical:~$ dmesg | head -25
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 17:53:40 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] Command line: root=UUID=680ab968-44bd-443e-88ef-4d1af24f1f88 ro nosplash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe90000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe90000 - 00000000bfe9c000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfe9c000 - 00000000bfe9d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfe9d000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
**[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)**
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used


**Questions**

1. **Would it be possible to upgrade the BIOS using the provided exe file from let's say WINE or any other LEGAL MS-like operating environment?**

2. In case an R20 owner wants to obtain the 64-bit Vista version and 4GB RAM, he has to upgrade to the latest firmware using the executable file - upgrade tool **[7]** (*which some people of Samsung's support said that they do NOT recommend it!!*) and even then, there is NO publicly available documentation anywhere whether this newer BIOS version fixes the problem. Samsung Germany (support service) **[5]** told me that they don't know if this will fix the problem or not ):P.
 **Is it correct from Samsung's side to advertise 4GB RAM support for a laptop which was sold with 2GB and a 32-bit operating system (Vista)?**

Thank you in advance.


**References**

[LIST=1]
[*] I can prove it since I have the receipt/delivery receipt ;)

[*][http://notebook.samsung.de/produkte/detail_printerfriendly.aspx?guid=b6d39af0-3d89-4196-b363-7665168224b7](http://notebook.samsung.de/produkte/detail_printerfriendly.aspx?guid=b6d39af0-3d89-4196-b363-7665168224b7)

[*][http://www.samsungpc.com/gb/support/r20/specs/r20spec.pdf](http://www.samsungpc.com/gb/support/r20/specs/r20spec.pdf)

[*] For example: MDT (c) - 2048MB, DDR2-667, CL5 [http://www.mdt.de/eShop/product_info.php?info=p34_MDT-2GB-TwinPack-DDR2-800-6400-CL5-SO-DIMM-200pin-fuer-Notebook.html&XTCsid=04bd17915fdf4ebce23488aa123ad051](http://www.mdt.de/eShop/product_info.php?info=p34_MDT-2GB-TwinPack-DDR2-800-6400-CL5-SO-DIMM-200pin-fuer-Notebook.html&XTCsid=04bd17915fdf4ebce23488aa123ad051)

[*] Tel: +49 61 96 66 11 30

[*][http://www.samsungpc.com/products/r20/r20_bios.htm](http://www.samsungpc.com/products/r20/r20_bios.htm)

[*][ http://support.samsung.de/support/support_down_detail.aspx?guid=b6d39af0-3d89-4196-b363-7665168224b7&fileid=1295678&filetype=FM]( http://support.samsung.de/support/support_down_detail.aspx?guid=b6d39af0-3d89-4196-b363-7665168224b7&fileid=1295678&filetype=FM)
[/LIST]

---

