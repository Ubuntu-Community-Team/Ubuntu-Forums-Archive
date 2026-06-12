---
title: "Karmic Won't connect to Wireless"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by donjulio29 on 2009-10-30
I just upgraded to the release candidate for Karmic 9.10 and it will not connect to my wireless network. I've never had this problem with ubuntu before, usually it finds all available wireless networks immediately. I did the package updates then i went to hardware drivers, i tried the B43 packages and the STA and neither worked!!!! 
PLEASE HELP! i love ubuntu and this is the only issue i've ever had

Dell Studio 1555
4GB RAM
320GB HDD
Dell wireless 1397 WLAN mini card
Broadcom Net link GB ethernet

The ethernet works fine

---

### Post by pro003 on 2009-10-30
post the output of commands "sudo ifconfig" in your terminal and as well "sudo iwconfig".

---

### Post by donjulio29 on 2009-10-31
I figured it out, basically i wiped the partition with Gparted, and reinstalled ubuntu, but this time i was connected via ethernet while installing, i then downloaded and activated the proprietary STA drivers and after one more restart everything worked fine :D

now all we have to wait for is a 64bit flash player

---

### Post by semajg on 2009-11-01
> **donjulio29 said:**
> I figured it out, basically i wiped the partition with Gparted, and reinstalled ubuntu, but this time i was connected via ethernet while installing, i then downloaded and activated the proprietary STA drivers and after one more restart everything worked fine :D

now all we have to wait for is a 64bit flash player

I have the exact same laptop, and none of that worked for me. I'm somewhat a beginner.

I installed Windows 7 (first), and now Ubuntu 9.10 (second). Everything works great EXCEPT wireless. I can't get it to see a wifi network, no matter what I do.

Help? Wireless is crucial, else ubuntu is useless to me and I'll have to uninstall it.

---

### Post by nievous on 2009-11-10
Same problem here...

---

### Post by raygj on 2009-11-11
> **semajg said:**
> I have the exact same laptop, and none of that worked for me. I'm somewhat a beginner.

I installed Windows 7 (first), and now Ubuntu 9.10 (second). Everything works great EXCEPT wireless. I can't get it to see a wifi network, no matter what I do.

Help? Wireless is crucial, else ubuntu is useless to me and I'll have to uninstall it.
in 9.10 the wireless drivers(kernel modules)are set to ONLY connect to ONE 'wireless domain zone'.(my computer, on boot, defaulted to CN(china)).
 
to connect to your wireless network your computer and your wireless network router must be set to the same 'wireless domain zone'(zone=region/country)
what country are you in?
if USA then country code = US
if china then country code = CN
if Australia then country code = AU
if Great Britain than country code = GB
etc.etc...
to see what  your computer is set to,in a terminal 
> sudo apt-get install iwthen enter 
> sudo  iw reg getin-order to set 'wireless domain zone' to your 'country code'( which **sets up your wireless TX/RX frequencies/channels & TX power-level & RX antenna preamp levels to work correctly in your country/zone**).
**All** country codes are in **'CAPITAL LETTERS'**
 enter 
in a terminal



> sudo iw reg set <INSERT-COUNTRY-CODE>e.g.
i live in Australia so country code = AU
so I used 
> sudo iw reg set AU**note** use the **same** country code that your wireless network router is set up-to.
then enter 
> sudo  iw reg getto see if your 'wireless domain zone' has changed to your country code.
**All** country codes are in **'CAPITAL LETTERS'**
if ok then
 Add a startup script to be run at startup.
Write a bash script.e.g.
my bash script is named 'setwirelesscountrycode.sh'
containing my country code setting
> #!/bin/bash
##iw reg set <your-country-code>
iw reg set AUthis was to set my own country code.i pasted this inside a new bash text file.
ie.
right click on your desktop--> select Create Document--> select(click on) Shell script
rename to 'setwirelesscountrycode.sh'
double click on 'setwirelesscountrycode.sh' desktop icon
select display button.
a text editor opens up.
replace file' original contents
Quote:
> #!/bin/bashwith
Quote:
> #!/bin/bash
##iw reg set <your-country-code>
iw reg set <insert-your-country-code-here>**All** country codes are in **'CAPITAL LETTERS'**

save & close text editer


 put it in the /etc/init.d/ directory.
in a terminal enter
Quote:
> sudo cp ~/Desktop/setwirelesscountrycode.sh /etc/init.d/ 
make the file you created executable.e.g.
> sudo chmod +x /etc/init.d/setwirelesscountrycode.shset it to run on startup
> sudo update-rc.d /etc/init.d/setwirelesscountrycode.sh defaults note 'defaults' puts a link to start '/etc/init.d/setwirelesscountrycode.sh' in run levels 2, 3, 4 and 5. and puts a link to stop '/etc/init.d/setwirelesscountrycode.sh' into run levels 0, 1 and 6.
you can now reboot if you want.

output from my computer

> 
raymond@ubuntu:~$ sudo iw reg set jp
not a valid ISO/IEC 3166-1 alpha2
Special non-alpha2 usable entries:
00 World Regulatory domain

raymond@ubuntu:~$ sudo iw reg get
country CN:
(2402 - 2482 @ 40), (N/A, 20)
(5735 - 5835 @ 40), (N/A, 30)

raymond@ubuntu:~$ sudo iw reg set JP

raymond@ubuntu:~$ sudo iw reg get
country JP:
(2402 - 2472 @ 40), (N/A, 20)
(2457 - 2482 @ 20), (N/A, 20)
(2474 - 2494 @ 20), (N/A, 20), NO-OFDM
(4910 - 4930 @ 10), (N/A, 23)
(4910 - 4990 @ 40), (N/A, 23)
(4930 - 4950 @ 10), (N/A, 23)
(5030 - 5045 @ 10), (N/A, 23)
(5030 - 5090 @ 40), (N/A, 23)
(5050 - 5060 @ 10), (N/A, 23)
(5170 - 5250 @ 40), (N/A, 20)
(5250 - 5330 @ 40), (N/A, 20), DFS
(5490 - 5710 @ 40), (N/A, 23), DFS remember **All** country codes are in **'CAPITAL LETTERS'**
MY SYS.LOG OF SOME COUNTRY CODES
>  
         cfg80211: Calling CRDA for country: HK
         cfg80211: Regulatory domain changed to country: HK
          (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
          (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
          (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
          (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
          (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

         cfg80211: Calling CRDA for country: CN
         cfg80211: Regulatory domain changed to country: CN
          (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
          (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
          (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)

         cfg80211: Calling CRDA for country: JP
         cfg80211: Regulatory domain changed to country: JP
          (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
          (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
          (2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A, 2000 mBm)
          (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
          (4910000 KHz - 4930000 KHz @ 10000 KHz), (N/A, 2300 mBm)
         (4910000 KHz - 4990000 KHz @ 40000 KHz), (N/A, 2300 mBm)
          (4930000 KHz - 4950000 KHz @ 10000 KHz), (N/A, 2300 mBm)
          (5030000 KHz - 5045000 KHz @ 10000 KHz), (N/A, 2300 mBm)
          (5030000 KHz - 5090000 KHz @ 40000 KHz), (N/A, 2300 mBm)
          (5050000 KHz - 5060000 KHz @ 10000 KHz), (N/A, 2300 mBm)
          (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
          (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
          (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2300 mBm)
     
         cfg80211: Calling CRDA for country: AU
         cfg80211: Regulatory domain changed to country: AU
          (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
          (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
          (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
          (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
          (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

         cfg80211: Calling CRDA for country: US
          cfg80211: Regulatory domain changed to country: US
          (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
          (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
          (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
          (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
         (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
          (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)ps.
if you have problems with 'sudo apt-get install iw'
make sure in your Software Sources that you have a tick next to 
"Community-maintained Open Source software (Universe)"

if that still doesn't work then you can download it directly from

A)only  if you are running 32bit (i386 to i686) kernel
[http://archive.ubuntu.com/ubuntu/poo....14-1_i386.deb](http://archive.ubuntu.com/ubuntu/poo....14-1_i386.deb)
<http://archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.14-1_i386.deb>


B)only if you are running 64bit (amd64) kernel
[http://archive.ubuntu.com/ubuntu/poo...14-1_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...14-1_amd64.deb)
<http://archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.14-1_amd64.deb>
detailed information on using 'iw' is at
[http://linuxwireless.org/en/users/Documentation/iw]("http://linuxwireless.org/en/users/Documentation/iw")
<http://linuxwireless.org/en/users/Documentation/iw>

---

