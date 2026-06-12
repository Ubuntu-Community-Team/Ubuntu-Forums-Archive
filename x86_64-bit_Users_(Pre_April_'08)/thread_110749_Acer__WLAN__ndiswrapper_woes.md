---
title: "Acer / WLAN / ndiswrapper woes"
date: 2005-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by dissdigg on 2005-12-31
*warning: linux newbie. 1st post.*

Hi!

I have an Acer Travelmate 4400 and have been reading posts from people with similar hardware but haven't had any luck with my own.  Specifically the WLAN.

I know I have a Broadcom wireless nic and have downloaded what I believe to be the appropriate 64bit windows drivers for the card along with ndiswrapper-1.7.

My problem right now is installing ndiswrapper.

From some of the info in these forums, I've found that I need to have several extra packages installed to accomplish this: build essentials, kernel headers, and possibly others.

First I tried using Synaptic.  I found the "build essentials" package which I guess has gcc, make, and all that good stuff - so I marked, applied, done. whew, easy!

Second, I started a terminal, did uname -a(?Something, I think it was a) and it gave me version 2.6.12-9 (i think 9). Back in Synaptic I looked for the kernal headers for my version.  D'oh, I only see 2.6.11 -amd64-generic (or something similar) - Hmm, not the same version as  the kernel I'm running but I tried to install it anyway and it gave me an error about dependencies and stuff. Then I tried updating package info in Synaptic but it didn't show any new or different packages. So I gave up in Synaptic.
 
Third, back in the terminal. I tried "sudo apt-get install linux-headers-2.6.12-9-<many combinations of generic/amd64/nothing/whatever>" but I would get unknown package errors.

I tried making ndiswrapper anyway but it gave me some errors involving missing directories or links or something.  I'm betting it's because I don't have  kernel headers installed.  At least I don't think I do.

I have a default installation of Ubuntu, from a CD ISO I downloaded a week or 2 ago - and everything else (Video/Sound/LAN) all seem to work great on this laptop.

Any ideas?  

Thanks!

---

### Post by peanut butter on 2005-12-31
hi 
i have an aspire and when i was a newby i ran in to the same problem that all confused me. so i gave up and decided to install the i386 ubuntu and then used snaptic to download ndiswrapper and ndisgtk for my guide go here[http://ubuntuforums.org/showthread.php?t=106487]("http://ubuntuforums.org/showthread.php?t=106487") (thoe this is kde the main partfor wifi is all done in gnome)

---

### Post by dissdigg on 2005-12-31
As a newb, I know I don't have anything to lose but a little bit of time, so I might give up and try that route, but I'd at least like to give it a fair shot in 64 bit.

Anyway,

I looked in synaptic again for ndiswrapper-utils but it's not there.  I only see ndiswrapper-source and ndisgtk.  I get errors when trying to mark either:
ndisgtk:
 Depends: ndiswrapper-utils  but it is not installable
ndiswrapper-source:
 Depends: debhelper (>4.1.0) but it is not installable

---

### Post by peanut butter on 2005-12-31
theese packages are only in the 32 bit software repositories
for some reason the develpers only make i386 packages for their programs.

i do believe there is a tutorial on the ndiswarpped website on how to compile the package but that supposdly takes a whole afternoon

---

### Post by redsmoke on 2005-12-31
I have an acer aspire 5002 and have ndiswrapper working perfectly...try this in a terminal:

```
redsmoke@ubuntu:~$ uname -r
2.6.12-10-amd64-generic
redsmoke@ubuntu:~$ sudo apt-get install linux-headers-2.6.12-10-amd64-generic

```

After you have the kernel headers installed you will need to download the ndiswrapper-1.7 if you haven't already and extract it. 

```
redsmoke@ubuntu:~$ wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz
redsmoke@ubuntu:~$ tar xvzf ndiswrapper-1.7.tar.gz

```

I don't know what acer your using but with my aspire 5002 and for the purpose of this example I used this 64-bit driver:

```

redsmoke@ubuntu:~$ wget ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip
redsmoke@ubuntu:~$ unzip 80211g.zip

```

If you are unsure which one to use go here for a good list: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

after that I assume you have some of the necessary build tools since you said you iinstalled the build essentials so only other app I would install is checkinstall at this point. you can do this by doing the  following:

```

redsmoke@ubuntu:~ $ sudo apt-get install checkinstall

```

Next lets try compiling

```

redsmoke@ubuntu:~$ cd ndiswrapper-1.7
redsmoke@ubuntu:~$ make ; sudo checkinstall

```

if you encounter any problems during the compiling scroll up and see where the first error was it probably is missing a library or its development package. For example(this is just an example) it might say libc.so not found so what you can try is: *sudo apt-get install libc libc-dev* (the -dev if for the development package used for compiling programs this is essential! once you have done that rinse and repeat: make ; sudo checkinstall


do that until you have no errors. If you have no errors the checkinstall should load. accept the defaults until after you reach the section where you can change the architecture...On my machine it detects the architecture as x86_64 while this is correct the debian package system looks for amd64 not x86_64 so you will need to change this option to read amd64.

After that it should install the package with no errors. if you still have issues and if your kernel version matches mine you can try my debian package by PM me your e-mail address.

next you need to configure the ndiswrapper with your driver so here is how I did it with mine(note install ndiswrapper-utils first: sudo apt-get install ndiswrapper-utils ):

```

redsmoke@ubuntu:~$ cd ~/WL_T60H906(8.0.10.0,XP64_logo)
redsmoke@ubuntu:~$ ndiswrapper -i bcmwl5.inf

```

verify it installed properly by typing the following and you should get a simular output:
```

redsmoke@ubuntu:~/Downloads/WL_T60H906(8.0.10.0,XP64_logo)$ ndiswrapper -l
Installed drivers:
bcmwl5          driver present, hardware present

```

once you have done that your still not done. You need to load the ndiswrapper module.

```

redsmoke@ubuntu:~$ modprobe ndiswrapper

```

You will most likely not get any output which is a good thing. if you want this module to install everytime you boot up you will need to do one more step. be careful here as a mistake can mess up your system type this exactly!

```

redsmoke@ubuntu:~$ sudo echo ndiswrapper >> /etc/modules

```

in order to verify the driver is working properly you will need to run this command and you should get an output simular to mine:

```

redsmoke@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:"goaway"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:14:BF:33:E9:53
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:100/100  Signal level:-57 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:113  Invalid misc:32548   Missed beacon:0

sit0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.


```

You can now configure the wireless card for your network from the system->administration->networking menu

I hope this helps

---

### Post by dissdigg on 2005-12-31
Thanks redsmoke!

I'm almost there, so close I can smell it.

While playing around some more, I checked off all of the repositories in synaptic and ran the update again.  It found a lot of stuff out of date and a lot more packages!  (Which repositories should be checked?)

So I upgraded all the packages it said I needed, and I'm running the same kernel you posted above:
```

dissdigg@ubuntu:~$ uname -r
2.6.12-10-amd64-generic

```

I also found and installed the ndisswrappter-utils packages and I now have the SYSTEM > Administration > Windows Wireless Drivers utility.

Sounds like my ndiswrapper installation problems are over - but of course I now have the new problem of getting ndiswrapper working with my driver.

The 64 bit driver I tried first said the driver was installed but "Hardware present: NO"
I also tried the ferrari driver mentioned above but it wouldn't even get listed when I tried to install it.
Finally I tried what I think is a 32 bit driver, and it says "Hardware present: YES"
But I don't see any interface to configure.
Here's the output when I run the commands that you mentioned:
```

dissdigg@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

dissdigg@ubuntu:~$ modprobe ndiswrapper

dissdigg@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

dissdigg@ubuntu:~$

```

One thing I thought would be good to mention is that in Windows XP, I usually have this button/light on the front of my laptop that blinks when it's looking for WLANs and solid when it's connected.  I can also push that button to turn the wireless on/off.   In Ubuntu, I have yet to see that light come on.  

Any ideas while I poke around Acer's FTP for some other drivers to try?

Thanks again!

---

### Post by redsmoke on 2006-01-01
one idea...try the 64-bit driver again but this time do this

```

redsmoke@ubuntu:~$ lspci

```

this should output a whole list of devices find your wireless nic in that list the list will look something like that

```

redsmoke@ubuntu:~/Downloads/ndiswrapper-1.7$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP

```

see mine is 0000:00:0b.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02) . remember the first set of hexadecimal numbers mine being 0000:00:0b.0 . Now  run lspci again but this time like this
```

redsmoke@ubuntu:~$ lspci -n

```

this will output the list again but this time you will have only numbers...it will look something like this 
```

0000:00:00.0 0600: 1039:0760 (rev 03)
0000:00:01.0 0604: 1039:0002
0000:00:02.0 0601: 1039:0963 (rev 25)
0000:00:02.5 0101: 1039:5513
0000:00:02.6 0703: 1039:7013 (rev a0)
0000:00:02.7 0401: 1039:7012 (rev a0)
0000:00:03.0 0c03: 1039:7001 (rev 0f)
0000:00:03.1 0c03: 1039:7001 (rev 0f)
0000:00:03.2 0c03: 1039:7002
0000:00:04.0 0200: 1039:0900 (rev 91)
0000:00:06.0 0607: 104c:ac50 (rev 02)
0000:00:0b.0 0280: 14e4:4318 (rev 02)
0000:00:18.0 0600: 1022:1100
0000:00:18.1 0600: 1022:1101
0000:00:18.2 0600: 1022:1102
0000:00:18.3 0600: 1022:1103
0000:01:00.0 0300: 1039:6330

```

remember your number from earlier now you see how mine is 0000:00:0b.0 thats my nick now see set after it like this:
0000:00:0b.0 0280: 14e4:4318 (rev 02)
you need this set of numbers right here 14e4:4318 using my machine as example again. so you take those numbers identifing your wireless nic and you install your drivers again but this time identifying the the device. Note you should uninstall the other driver first by typing ndiswrapper -e <drivername>
```

ndiswrapper -i <drivername.inf>
ndiswrapper -d 14e4:4318 

```

note those are the numbers from my example replace with the device id of your hardware...also try the driver i used in my example the one that is for the ferarri 4000 if that doesn't work.

Let me know if that works...

---

### Post by redsmoke on 2006-01-01
oh and did you get ndiswrapper 1.7 installed? you need the latest version which is 1.7 because the one that will install from the ubuntu packages is older and will not work with my 64-bit wireless drivers for example only the latest version will.

---

### Post by redsmoke on 2006-01-01
oh and on the button thing my laptop has the same thing mine flashes now instead of staying on when its connected and transfering data.

---

### Post by dissdigg on 2006-01-02
I tried the 64bit driver again, and the commands you suggested, and the results look very similar to the ones you get on your laptop:
```
lspci
0000:06:05.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

 lspci -n
0000:06:05.0 0280: 14e4:4318 (rev 02)

```

So I did  ndiswrapper -d 14e4:4318 netbc564 and now it says driver present, hardware present, but there is no light, and still no configurable interface.

I believe the ndiswrapper I have installed must be the one from the packages because I don't remember successfully compiling the 1.7 version I downloaded.  I'll try that now.

---

### Post by redsmoke on 2006-01-02
Yeah you definately need to have 1.7 running like I said. The driver probably needs at least 1.7 version of ndiswrapper to work. and on the light on my acer laptop at least the light only comes on(blinks) when sending data so it not being on should be normal.

---

### Post by dissdigg on 2006-01-02
I uninstalled the packages for ndiswrapper 1.1, compiled and installed 1.7 with no trouble.  I did "sudo dmesg" and it said ndiswrapper version 1.7, but had errors of the driver not being 64bit.  ndiswrapper -l showed the wrong driver, so I loaded the 64 bit driver and did the -d command like you mentioned before so it showed hardware found.

I even compiled acer acpi and got my light on in the front, but I still don't get any interface to configure.

Also, now when I do "sudo modprobe ndiswrapper" the system completely locks up (I can't even break out of X to a login prompt or anything).

---

### Post by redsmoke on 2006-01-02
hrmm...possibly wrong drivers for your card did you try the driver for the ferarri 4000? the driver you said was the 32-bit one earlier was named simularly to the one i use for the 64-bit so I am thinking you should use the 64-bit driver for the acer ferarri 4000 and it should work.

---

### Post by Tiede on 2006-01-03
I followed your instructions to the letter redsmoke...
And...
Kt'ching!!! My wireless light is blinking looking for network and all. thank you, thank you, thank you.
It is the most awesome thing when you get a problem and fix it in a day in linux. (usually it takes me a week or two :D)
Thanks again!
Will repay you by helping someone else on the forums whenever it is in my abilities to do so!

---

### Post by Kuolio on 2006-01-03
Hi all!

I thought to post my experiences with acer+ubuntu64+wlan. I'm using acer laptop, model Aspire 5021.

Getting wlan to work was very straight forward with the info&instructions on [this website.]("http://lxer.com/module/newswire/view/46385/") It introduced me to the wonderfully easy world of ndiswrapper configuration GUI :)

So, all I did to configure my wlan was:

1. downloaded 64bit windows drivers for my card from acers support page
2. apt-get'd ndiswrapper, ndisgtk and ndiswrapper-utils
3. launched "Windows Wireles Drivers" tool from System menu
4. clicked and poked some settings, and voilá! Fully working wlan. (way easier than in 64bit windows btw).

---

### Post by dissdigg on 2006-01-03
[QUOTE=redsmoke]hrmm...possibly wrong drivers for your card did you try the driver for the ferarri 4000? the driver you said was the 32-bit one earlier was named simularly to the one i use for the 64-bit so I am thinking you should use the 64-bit driver for the acer ferarri 4000 and it should work.[/QUOTE]

Thank you so much redsmoke, you're the man.
I'm posting this reply over a wireless connection from my Acer Travelmate 4400.
To sum up:

uninstall any ndiswrapper packages.
install ndiswrapper 1.7
ndiswrapper -i (64bit ferarri 4k driver)
ndiswrapper -d <devid> ferarri4k    (gotten from lspci and lspci -n)
modprobe ndiswrapper  

#this gave me an interface wlan0

From here I couldn't make a connection to my router at first, but I knew it was working because I could see all the available networks (SSIDs) in the gnome network config tool.  Unfortunately, in this tool, I did not see any place to configure WPA, so I completely removed all security from my router and tried to connect again.  I still wasn't getting an IP from DHCP so I tried a static IP and that didn't work either.   So I rebooted ubuntu, and now DHCP and everything else are working!

Now I just need to learn how to get WPA working - I did happen to notice this in dmesg:
```
[   50.528711] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
```
so I know it must be supported.

Oh and hey, there goes my button/light flashing w/ activity!  That's really  cool!:cool: 

Thanks again for your help! You've made my day!

---

### Post by redsmoke on 2006-01-03
No prob dissdigg just glad to help.

---

### Post by norrback on 2006-01-05
hello

I have an acer 3003 with the same wlan chip (broadcom) that you are using but on an 32bit system. 
Finds the network but wont connect, the led is blinking.

> norrback@acer:~$ sudo iwlist wlan0 scan
Password:
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     Scan completed :
          Cell 01 - Address: DE:4E:7F:CA:EA:6E
                    ESSID:"hmm"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-36 dBm  Noise level:-256 dBm
                    Encryption key on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


> 
norrback@acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



---

### Post by Tiede on 2006-01-07
weird, mine is on a 32 bit an it connects puuurrfectly. I followed redsmoke's path until the checkinstall, after which I went in the ndisgtk to configure the netrok instead of staying on the command line. Try it out. Maybe that is where the problem is coming from.

---

### Post by norrback on 2006-01-07
which driver and ndiswrapper? tnx.

---

### Post by kurushi on 2006-01-07
Here there's a guide to install Wireless in some Acer computers

[https://wiki.ubuntu.com/WiFiHowto/Acer5021WLMiConfiguration?highlight=%28aspire%29%7C%285021%29%7C%28wlmi%29](https://wiki.ubuntu.com/WiFiHowto/Acer5021WLMiConfiguration?highlight=%28aspire%29%7C%285021%29%7C%28wlmi%29)

---

### Post by Tiede on 2006-01-08
I used the driver found in [ this package ](ftp://ftp.support.acer-euro.com/notebook/aspire_3000_5000/driver/802bg.zip) ([ftp://ftp.support.acer-euro.com/notebook/aspire_3000_5000/driver/802bg.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3000_5000/driver/802bg.zip)) with ndiswrapper version 1.7 and the ndiskgtk package.

---

### Post by ewok on 2006-01-12
oh you think you have problems... what the devil is this?

ewok@ewok:~/Desktop$ cd acer_acpi-0.3
ewok@ewok:~/Desktop/acer_acpi-0.3$ sudo make
make: Nothing to be done for `all'.
ewok@ewok:~/Desktop/acer_acpi-0.3$ sudo make install
mkdir -p /lib/modules/2.6.12-10-amd64-generic/extra
cp -v acer_acpi.ko /lib/modules/2.6.12-10-amd64-generic/extra/
`acer_acpi.ko' -> `/lib/modules/2.6.12-10-amd64-generic/extra/acer_acpi.ko'
depmod -a
ewok@ewok:~/Desktop/acer_acpi-0.3$ sudo modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.12-10-amd64-generic/extra/acer_acpi.ko): No such device

AND for some reason:

Installed drivers:
bcmwl5          driver present
netbc564                driver present, hardware present

what is this netbc564? why does it say that? help ... i am a newbie... forgive be but i need my hand held thru this one

cheers,

tyler

---

### Post by kumakun on 2006-01-13
alright, I'm running into problems with installing ndiswrapper-1.7. it will make just fine but it returns a message that the install fails. when viewing the log it returns this:

```

(Reading database ... 75083 files and directories currently installed.)
Unpacking ndiswrapper-1.7 (from .../ndiswrapper-1.7_1.7-1_i386.deb) ...
dpkg: error processing /home/justin/ndiswrapper-1.7/ndiswrapper-1.7_1.7-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.12-10-386/modules.alias', which is also in package linux-image-2.6.12-10-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/justin/ndiswrapper-1.7/ndiswrapper-1.7_1.7-1_i386.deb

```

So, I'm not sure what exactly I'm running into here. I've tried this on both the 64bit install and the 32bit install.

any suggestions for this one?

/K

---

### Post by Phuzion on 2006-01-15
I had no issues following the sub-section [ndiswrapper]("http://wiki.ubuntu.com/SetupNdiswrapperHowto") in the Wiki WiFi How To Guide.  

I have a 4402 Travelmate.  I still coudn't get it to work, even after successfully getting the driver created, loaded into the kernel without errors and could activate it.  I am still working on this issue.  Let youn know if I have any luck.

---

### Post by Phuzion on 2006-01-15
Just an update.  I can tell you that I have tried every XP driver from Broadcom for XP64 but none of them worked for my Ubuntu Amd64 Breezy Badger 5.10 distro.  My assumption is that you cannot run this WiFi card on the 64 bit version of Breezy Badger, using ndiswrapper.  For the 64 bit Ubuntu, wait for Dapper.  I am currently putting the 32bit version on my laptop.

Also,I found that it is much easier to create ndiswrapper manually, according to the [ndiswrapper Wiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

---

### Post by Andrew Shimmin on 2006-01-31
Phuzion- That's really disappointing, because I guess I'm in the same place you were two weeks ago.  I was able to load the driver, and get to: bcmwl5 driver present, hardware present. I could bring up wlan0 in 'System>Administration>Networking'.  But it won't detect the AP that I can get (with very strong signal) in winXP. The LED in front never so much as blinks, either.  Is it possible that it really isn't possible to make this work?

Has anybody gotten the wlan on an Acer TM44XX working?

---

### Post by Tiede on 2006-02-05
Guys, I am back... and asking for some help!

I recently -well, a week ago, to be precise- installed Dapper on my laptop after a cleaninstall of breezy. So I followed the same steps found here to try enabling my wireless card again, but now it wont work :(
The light in the front does not come on anymore.
I used the ndiswrapper 1.08 from the Dapper repository.
Now the odd thing is even before I installed ndiswrapper, dapper acted as if it recognized my wlan card, and it even showed up under System->Administration->Network. But it would never work either active or inactive.
Now after I installed ndiswrapper, I expected to go to the familiar wlan0 config, but my wireless card in shown as eth1, and I cannot seem to be able to turn it on.
Anyone has an idea of what I could try next. My idea-pool for wireless lan is not that big ;)

EDIT: I forgot to post this ```
marc@tuxed:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-14-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
marc@tuxed:~$

```
This makes me understand that the default driver that came with dapper is the prob'. Anyone knows how I go about taking that out?
Thanks.

---

### Post by Tiede on 2006-02-06
[info]
Ok, no one is answering, I am thus "bumping" the thread in the 'legal' way :D... Also modos, don't view this as an attempt to achieve the 200 beans mark - I realised this *after* I posted
[/info]

[bump]
I have just downloaded the acer-hk and the acer-acpi packages. I will try to install acer-hk first, and then acer-acpi. I don't know if that will make any difference, but i'll still try.
[/bump]

The true question is: My intuition tells me the problem arose from my card being identified by ubuntu (eth1) but not configured properly. Does anyone know how I can stop ubuntu from trying to configure it so I can do it just as it was once before, as I did in Breezy -cause then it worked flawlessly, and the button-light-thinggy was activated automagically, then. (no acer-hk/acpi was needed)

---

### Post by Andrew Shimmin on 2006-02-07
I finally (hooray!) got my Acer 4402's wlan working, so maybe I can help. I'm pretty sure you need ndiswrapper 1.7 (or later) in order to run acer_acpi. Can't remember where I saw that, but once I installed 1.7 (the on-disc version was 1.1, I think) the thing all of a sudden worked. When you say you're using 1.08, do you mean 1.8?

Second, lan0 is the ethernet card, not your wifi, I'm pretty sure. If wlan0 isn't in your network settings, it means the system doesn't believe you have one.  It shouldn't need Acer_acpi to see it (only to actually work), it's just a matter of ndiswrapper and the right windows driver. Until that's configured, nothing you do with Acer_acpi will make it work.

Good luck.

---

### Post by Tiede on 2006-02-08
I meant 1.8, yes. That is the version available in dapper. "fresh out the oven ;)"
I did not say lan0, there is no such interface in my Network config tool. There is eth0, which is associated with my ethernet card, and eth1 which is supposedly associated with my wlan card (it has a picture of a wlan card next to it)...
Do you know how I can get wlan0 to show up instead of eth1 or a simpler solution?
Thank you!

---

### Post by Andrew Shimmin on 2006-02-10
Nope. Sorry.  Maybe you really have got everything installed, just not turned on? Have you tried running:

> modprobe ndiswrapper
modprobe acer_acpi
echo "enabled : 1" > /proc/acpi/acer/wireless

If it doesn't work after that, it's out of my depth.

---

### Post by Tiede on 2006-02-11
But the module acer_acpi was never installed in the first place. It is for 64bit PCs, mine is only s 32-bit one. Whici is why I said it was odd for acer-hk to complain about finding a 64bit architecture on my PC or something along those lines...

I will try something someone else suggested. I will remove every bit of configuration I can find. (/etc/interfaces/); ndiswrapper... and let ubuntu reinstall the driver itself, and if that doesn't work, figure out what to do from there. (In other words, I am going to restart from scratch.) I'll keep you posted.

EDIT: IF I do
```
modprobe ndiswrapper
modprobe acerhk #I don't have acer_acpi installed
echo "enabled : 1" > /proc/acpi/acer/wireless
``` I get this:

```
marc@tuxed:~$ sudo modprobe acerhk
marc@tuxed:~$ echo "enabled : 1" > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Aucun fichier ou répertoire de ce type
marc@tuxed:~$

```
Do you by any chance know the path for acerhk. I'll try to find it before I go ahead with the clean/scracth start thing.

---

### Post by Tiede on 2006-02-14
All right, starting from scratch. It does not work with the BCM43xx driver, so I used ndiswrapper 1.8 (found in the repos of dapper.) It does not work. On another forum (i forgot which) a guy said that he was able to get his working with 1.9 since 1.8 could not get it to work. Went to sourceforge to download latest stable ndiswrapper version. (version 1.10)
Now here comes trouble:
Make install won't work, here is the output
```
marc@tuxed:~/Desktop/ndiswrapper-1.10$ make install
make -C driver install
make[1]: entrant dans le répertoire « /home/marc/Desktop/ndiswrapper-1.10/driver »
Can't find kernel sources in /lib/modules/2.6.15-15-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Erreur 1
make[1]: quittant le répertoire « /home/marc/Desktop/ndiswrapper-1.10/driver »
make: *** [install] Erreur 2
marc@tuxed:~/Desktop/ndiswrapper-1.10$


```

But no matter, since I have checkinstall, I tried to go with that instead. It's a long shot, but it could have worked :-?
The output:
```
marc@tuxed:~/Desktop/ndiswrapper-1.10$ sudo checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



Installing with "make install"...

========================= Installation results ===========================
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.

Copying documentation directory...
/var/tmp/MfpHQlkVSEgNWGqYjFRm/installscript.sh: line 13: 14456 Erreur de segmentation  mkdir -p "/usr/share/doc/ndiswrapper-1.10"

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

marc@tuxed:~/Desktop/ndiswrapper-1.10$


```

Anyone who has any ideas, please help a fellow ubuntero out!
My windows XP keeps on freezing which means I can't stand it even more than before! But I need internet, and my school only let the students use the wireless network on our laptops (No walls to go plug in an Ethernet cable :D)

---

### Post by neoflex on 2006-02-23
Hi tiede, i have an acer 5002 and the same problem as you with dapper and the wifi.
Have you found a solution ?
I m still looking for, i'll tell you if I found something...

---

### Post by mooswa on 2006-03-06
Thanks guys, I have managed to get it working on my Acer TravelMate 4404 under 32 bit Breezy Badger\\:D/ .

Here is the summary:

ndiswrapper-1.10
acer_acpi-3.0
bcmwl5.inf and bcmwl5.inf from the acer support site for TM 4404 (06/13/2003, 3.20.23.0)

After registering bcmlw5 with ndiswrapper I noticed that "ndiswrapper -l" doesn't say that hardware is present. Running "ndiswrapper -d" fixed that.

NOTE: After doing echo "eanbled : 1" > /proc/acpi/acer/wireless the light doesn't go on - it will only blink when wireless card is actually sennding/receiving(?) data. I wish I'd knew that - initially I assumed that lack of light means wireless doesn't  work. Man, did I waste a lot of time troubleshooting this!

---

### Post by Tiede on 2006-03-07
Sorry neoflex. I haven't gotten anything. I wish I had better news, but I have long since reverted to breezy. I do love dapper, but wifi is a *must* for me... :(

As we are on the subject, I noticed something quite strange with the behavior of the laptop when I am on a wifi hotspot. If I turn it on when I am there, it will only work once for every five (cold) reboots... Otherwise, nm-applet says I am connected, the light in the front of the laptop says I am connected, and even network-admin says I am connected, but Firefox cannot load nothing and I cannot ping nothing neither... I tried doing ```
sudo ifdown/ifup wlan0
``` many times, but that never works. Even stranger, if I turn of the wireless card when it that happens (to try to see if when it turns back on it would work) the computer freezes - nothing works, can't break out of X and Caps Lock light not coming all et al. - and I have to hard reboot it (hold I/O button for 5 secs...) Anyone can ditto the same with their PC or a possible fix?
This thing is starting to bug me as I simply *cannot* afford not having a reliable wifi connection...
Any amount of cents (from 2 cents onwards :D) on this issue greatly appreaciated.

---

### Post by E21Craze on 2006-03-07
Greetings.

First time poster here. Same problem with a Acer 5024: drivers installed but wifi not working. Managed to compile both ndiswrapper and acer-acpi fine. However, no matter what I do, I can´t get it to work.

Strange thing is that a couple of weeks ago everything was working fine: ndiswrapper loaded fine, wifi was enabled after acer_acpi was loaded and the "echo" command was issued.

Any clues? I _did_ had a couple of disk issues, e2fsck came up on startup quite often. Could this possibly be related?

---

### Post by Tiede on 2006-03-07
I wanna ditto E21Craze in saying that it stopped woking altogether. No matter what I do, I cannot get online. And the strange thing is EVERYTHING says I should be:
The light in the front of my laptop is "steady-on" meaning that the I should be online, the nm-applet on my taskboar shows a 100% signal strength status, ifconfig gives me the correct stats, the only odd thing is the number of packets sent is always less than 5 (?) while the number of received packets is going steadily up. It's as if I was behind a firewall and all the ports were blocked (which is not true since I haven't installed any firewall apps and only ubuntu's is there)...
I REALLY need to get this thing working.  I am currently on windows and all the things I want to use are all on my linux partition!
I tried these troubleshooting steps, but none worked :(
```
sudo killall nm-applet
``` to restart the applet.
```
sudo ifdown wlan0
sudo ifup wlan0
``` but it says: No persistent DHCP offers found in database, sleeping.
```
sudo gedit /etc/dhcp3/dhclient.conf
``` and set the timeout to successively 10, 7, 2 and 0. None worked.
I also tried going in network-manager and fiddle with anyting that seems relevant, but nada. it says that it is active and all, but FF says otherwise (and so does ping -ping says network is unreachable.)
I think the problem is somwhere in the configuration of the network interfaces, but I cannot pinpoint the exact problem. I know this because the two most frequent places for the computer to freeze/lock are either the step configuring network interfaces during startup or deconfiguring network interfaces at shutdown.
And of course the third one would be if I press the button to turn off the wireless card when Ubuntu won't go on the internet, as I already mentioned before. I just want to add that this is like a **guaranteed** way to freeze the computer. Don't know what happens then, but I am sure therein lies the problem. (If the network comes up though, turning it on or off does not freeze the laptop).
I also remember a message at shutdown complaining that wireless *something somethin' * is too big, but I cannot remember what it is exactly. If I see it again. I'll take not of it and post it here.

These are the steps I tried. If you know of any other that is susceptible to help, please don't hesitate to post them. I am growing impatient with this problem and I cannot express how happy I'd value anyone's responses!

Thanks in advance! Hopefully, I won't have to revert to windows for long.

---

### Post by equilibrium on 2006-03-09
I have a Acer Aspire 5024WLMI and have wireless working. The front wireless LED isn't constantly on when wireless is enabled like in windows. It flashes like a activity light.

I wrote a [howto in the laptop part of the forum](http://ubuntuforums.org/showthread.php?t=140007) with all the steps I took to get wireless working.

Not sure if it is helpfull to anyone.
 I used ndiswrapper 1.7, not sure if the newer versions give any advantage or not :confused: but 1.7 seems to work ok.

---

### Post by neoflex on 2006-03-09
i have suggesfully make my wifi work with dapper doing that :

```
rmmod bcm43xx
rmmod ndiswrapper
modprobe ndiswrapper
```

---

