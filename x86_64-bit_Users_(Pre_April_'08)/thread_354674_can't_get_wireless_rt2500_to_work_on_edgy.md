---
title: "can't get wireless rt2500 to work on edgy"
date: 2007-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dekster on 2007-02-06
Hi all!

I am a newbie, using Edgy 6.10 on an AMD64 processor. My problem is getting my Edimax EW-7128g wireless card to work. I've been through allot of forum pages with allot of similar problems, and somehow all the solutions don't work for me.  :( 

I manged to install the rt2500 driver using ndiswrapper (the Edgy "out of the box" driver failed so I gave it a shot). I get:

```
[FONT="Courier New"]~$ ndiswrapper -l
filename : invalid driver!
rt2500 : driver installed[/FONT]
```

I notice that it says nothing about the hardware, which might indicate to the problem.

I played a bit with iwconfig to get:
```

[FONT="Courier New"]~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.447 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"Edi"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: < My MAC address>  
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.[/FONT]
```

most of which I inserted manually to /etc/network/interfaces, after SYSTEM->ADMINISTRATION->NETWORKING didn't get me going.

I tried to install the Rutilt I saw people talking about in forums, but it didn't even compile, I guess  it has something to do with gcc 4.1 being stricter  than previous gccs, but I'm not sure (I downloaded all the kernel headers and all that was required and still no luck).

My  /etc/network/interfaces reads:
```

[FONT="Courier New"]auto lo
iface lo inet loopback

iface eth0 inet static          [COLOR="Red"]## this is my wired card which does work##[/COLOR]
address 192.168.2.105
netmask 255.255.255.0
gateway 192.168.2.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet static  [COLOR="Red"]## I tried fashioning my wireless to resemble my wired card ##[/COLOR]
wireless-essid Edi
address 192.168.2.103
netmask 255.255.255.0
gateway 192.168.2.1


[COLOR="Red"]## This is an "Unknown interface" I thought might be my wireless card ##[/COLOR]
iface wmaster0 inet static  
wireless-essid Edi
address 192.168.2.104
netmask 255.255.255.0
gateway 192.168.2.1

auto eth0

auto wlan0

auto wmaster0[/FONT]
```

And finally, my device manager identifies my card as a RT2561/RT61 802.11g PCI. I don't really understand it, but I know my card should be 802.11g PCI, it's the rest I don't know about ( I thought it should be RT2500).

 I tried to be as specific as possible, this is my first post...:oops:  PLEASE HELP ME!

---

### Post by renzokuken on 2007-02-06
have a look here, your card is based on a ralink chipset so should work

[http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html](http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html)

---

### Post by mojoman on 2007-02-08
I've got that card up and running on two machines, one is an ubuntu server (dapper) and the other a debian laptop. On the laptop I ran it on Ubuntu and Xubuntu (dapper and breezy) right out of the box. However, both those machines are on 32-bit. Anyway, I had a minor hell trying to compile the drivers for Debian sarge (it didn't work out) but found a good howto for Etch and it went down real smooth. As the howto is for Etch and I did it on 32-bit it might not work but my guess is that it will work as all the necessary packages are in the repos (dapper at least, haven't checked edgy's). You might want to give it a go...

[http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto)

Best regards
/mojoman

---

### Post by Dekster on 2007-02-11
Thanks guys, I'll give it a try later on today and let you know...

---

### Post by Dekster on 2007-02-13
Well, I tried both solutions, but no success yet. maybe you could tell me what I'm doing wrong:

At first I tried renzokuken's advice, and got stuck at step #5 with:

```
$ make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/david/Desktop/RT2500-Linux-STA-1.4.6.6/Module/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: *** No rule to make target `/home/david/Desktop/RT2500-Linux-STA-1.4.6.6/Module/2.6.x/rtmp_main.o', needed by `/home/david/Desktop/RT2500-Linux-STA-1.4.6.6/Module/2.6.x/rt2500.o'.  Stop.
make[1]: *** [_module_/home/david/Desktop/RT2500-Linux-STA-1.4.6.6/Module/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2

```

I tried again with sudo to get the same results. :( 

I read the readme supplied by [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) but didn't understand the line about:
> $make -C /path/to/source SUBDIRS=$PWD modules

    Where /path/to/source is the path to the source directory for the (configured and built) target kernel.

:confused:  [COLOR="Red"]where is this place?? what am I looking for? what am I supposed to do?[/COLOR] :confused: 

After that I tried to get the Ralink Utility going, I followed the readme, but when I compiled it I encountered a disaster:
```
raconfigui.cpp:3236: error: invalid use of undefined type ‘struct QComboBox’
raconfigui.h:13: error: forward declaration of ‘struct QComboBox’
raconfigui.cpp:3247: error: invalid use of undefined type ‘struct QCheckBox’
raconfigui.h:12: error: forward declaration of ‘struct QCheckBox’
raconfigui.cpp:3248: error: invalid use of undefined type ‘struct QCheckBox’
raconfigui.h:12: error: forward declaration of ‘struct QCheckBox’
raconfigui.cpp:3249: error: invalid use of undefined type ‘struct QCheckBox’
raconfigui.h:12: error: forward declaration of ‘struct QCheckBox’
raconfigui.cpp:3250: error: invalid use of undefined type ‘struct QCheckBox’
raconfigui.h:12: error: forward declaration of ‘struct QCheckBox’
raconfigui.cpp:3251: error: invalid use of undefined type ‘struct QComboBox’
raconfigui.h:13: error: forward declaration of ‘struct QComboBox’
raconfigui.cpp: In member function ‘void RaConfigForm::About_OnActive()’:
raconfigui.cpp:3439: error: invalid use of undefined type ‘struct QLabel’
raconfigui.h:14: error: forward declaration of ‘struct QLabel’
raconfigui.cpp:3444: error: invalid use of undefined type ‘struct QLabel’
raconfigui.h:14: error: forward declaration of ‘struct QLabel’
raconfigui.cpp:3446: error: invalid use of undefined type ‘struct QLabel’
raconfigui.h:14: error: forward declaration of ‘struct QLabel’
make: *** [raconfigui.o] Error 1

```

And these are only the last few rows, it was as if not one row could be compiled properly.

So I tried mojoman's link, and everything went smooth, not an error, just that at the end of the process I was back at square 1. the exact same problem - I can see the card, it seems to be configured, but it doesn't work - I can send pings to my router (at least that's what 'Network Tools' suggest) but I can't receive, and the broadcast field in System->Administration->'Network Tools' is 0.0.0.0,
though the working eth0 wired card broadcasts at 192.168.2.255.

How can I get it to work?! ](*,) 

I appreciate all the help offered to me this far, and I hope to get more help because this is driving me crazy.

Thanks again and in advance to all who support us new guys,
                                           Dekster

---

### Post by Dekster on 2007-02-16
After days of surfing this forum and trying and erring, I finally managed to get my card to recognize my router on scans. I tried so many things that I can't even trace how I got it working. I think the last thing I did was download the daily cvs from serialmonkey and follow the readme.

Now my problem is that I can't ping or make a connection. I installed the  'Wireless Assistant' just to see my router with no possibility to connect.

i get:

```
~$ iwlist ra0 scanning
ra0       Scan completed :
          Cell 01 - Address:  # I don't know who this guy is, probably a neighbor 
                    ESSID:"FRANKIE"
                    Mode:Ad-Hoc
                    Channel:1
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address:  # My router MAC address
                    ESSID:"Edi"
                    Mode:Managed
                    Channel:8
                    Encryption key:off
                    Bit Rates:44 Mb/s

```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"Edi"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: # My router's MAC   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-31 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Everything should be working... but it's not!

Does anyone have an idea what I am doing wrong??

---

### Post by Dekster on 2007-02-17
IT WORKS!!! IT WORKS!!!

I don't get it, but I got it working in the end! So much work for something so basic like wireless connection! I think that as a newb I learned a valuable lesson about linux: yeah it's a good OS, but I think the real value of it is that in order to get stuff running like you want them to you have to get into the guts of the system, and it lets you. further more, during the process I fell in love with the Ubuntu community - so many people helping each other in such a polite manner. I think I'll stay.

Back to the problem - as I said I tried everything, and at the end I had RT61 and RT2500 drivers installed to my kernel. I deleted my /etc/network/interfaces and configured the RTxsta.dat files to my router specifications.
After that I ifconfiged it to find that the RT61 stuck, and after reading the man ifconfig page I kinda understood how to get it to ping my router.

when all that was done I used the 'System->Administration->Networking' tool to set my interfaces file and to get wireless started at boot.

Bottom lines:
- RT2500 cards can sometimes work fine with RT61 drivers, as does my Edimax  EW-7128-G
- Don't give up - if it should work it eventually will, if you keep fiddling with it.

I hope this thread could help anyone with the same problem, though I can't really write a nice HOWTO since I got it to work almost accidentally and I'm not sure I could do it again...

I thank the forum again,
                             Dekster.

---

### Post by ffxr on 2007-02-19
that Edimax EW-7128-g **IS** based on the RT61 chipset, i know cos i have the same card.. shame i didnt see this post earlier as i could have told you this.. 

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

nice to know my wireless card will work under AMD64 tho, when i get round to installing it later this week.. : )

---

### Post by RAOF on 2007-02-19
> **Dekster said:**
> ...
I think that as a newb I learned a valuable lesson about linux: yeah it's a good OS, but I think the real value of it is that in order to get stuff running like you want them to you have to get into the guts of the system, and it lets you.
...

Or rather "make sure that your hardware has linux drivers, because the hardware manufacturers almost always don't provide ones".

If your hardware is from companies with good linux support (like my new ASUS laptop - Intel wireless and chipset, nVidia graphics), things Just Work(tm).

---

### Post by sbmd on 2007-03-04
so my card has worked in the past, it shows up in networking, but does not work. 


I have installed the lastest beta from seamonkey. I have not installed any utility for it though. I am thinking i will soon, but this card has worked out of the box before on ubuntu and now it does not, I have tested it in windows and it works. I would like to see if anyone else has this problem and how to correct it, it shows up in device manager and in networking, but never scans for wireless networks. 


I am a noob to most of this stuff but i am capable of doing anything as i would just reinstall if i had to. 

what is the best kernel to use?

thankx to anyone.

---

### Post by ffxr on 2007-03-04
good god its that long since i config'ed this card.. , it is a little more involved for AMD64 for sure..., & i have it working fine in 2.6.16 & 2.6.17 & 2.6.20 kernels... i know you need the latest CVS drivers from serial monkey to get it to work on the 17 & 20 kernel.. 

have you built the kernel modules from source?

is it the Edimax EW-7128g your trying to setuip..?

u need to make sure , you know exactly what chipset is in your EW-7128g

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

this is a guide to compiling the kernel modules for the RT61:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28rt61%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28rt61%29)

you would exchange the ralink drivers of rthe serial monkey ones..

sorry for the slapdash reply.. my memory aint what it used to be.. if you ask a few more questions m sure i can help more...

---

### Post by sbmd on 2007-03-04
hey thankx

i have a hawking hwc54d


and i am on an inpsiron 1100, i will try the lastest cvs as i have the 17 kernel. 

thankx


let me know if there is any more you would like to know.

---

### Post by nepenthes on 2007-03-05
I was already wondering. Because I have an old PCMCIA Rt2500 card (Surecom 11b) that doesn't need any drivers under 32 or 64 bit Edgy - it just works out of the box. Still I need to go through ndiswrapper because of WPA support. But I just read that WPA will be also intergrated to the Linux Kernel these days. Life's good ;)

---

