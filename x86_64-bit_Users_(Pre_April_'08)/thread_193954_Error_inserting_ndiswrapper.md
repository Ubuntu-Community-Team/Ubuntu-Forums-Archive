---
title: "Error inserting ndiswrapper"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by thewierdone2000 on 2006-06-10
Hey, I am having a problem getting my wireless card working (BCM94318MPG), and was hoping I could get some help.  I am trying to get ndiswrapper to work, as no linux drivers for it are availible. I have used the propper inf file, and as far as I am aware ndiswrapper is configured properly. The errors come in when I try to modprobe.

Headers are installed, and I have since then built the kernel. (Though the kernel running was not built when kernel-headers were installed)

```
chives@tuxmiester:~/Desktop/80211g$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
chives@tuxmiester:~/Desktop/80211g$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-amd64-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Realivent Dmesg stuff:
```
5789.985857] ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
[ 5789.985864] ndiswrapper: Unknown symbol per_cpu__softnet_data
[ 5789.985978] ndiswrapper: disagrees about version of symbol misc_deregister
[ 5789.985982] ndiswrapper: Unknown symbol misc_deregister
[ 5789.986141] ndiswrapper: disagrees about version of symbol unregister_netdev
[ 5789.986152] ndiswrapper: Unknown symbol unregister_netdev
[ 5789.986324] ndiswrapper: disagrees about version of symbol create_proc_entry
[ 5789.986328] ndiswrapper: Unknown symbol create_proc_entry
[ 5789.986582] ndiswrapper: disagrees about version of symbol register_netdev
[ 5789.986586] ndiswrapper: Unknown symbol register_netdev
[ 5789.986614] ndiswrapper: disagrees about version of symbol free_netdev
[ 5789.986618] ndiswrapper: Unknown symbol free_netdev
[ 5789.986768] ndiswrapper: disagrees about version of symbol proc_net
[ 5789.986771] ndiswrapper: Unknown symbol proc_net
[ 5789.986799] ndiswrapper: disagrees about version of symbol proc_mkdir
[ 5789.986803] ndiswrapper: Unknown symbol proc_mkdir
[ 5789.986824] ndiswrapper: disagrees about version of symbol misc_register
[ 5789.986828] ndiswrapper: Unknown symbol misc_register
[ 5789.986914] ndiswrapper: disagrees about version of symbol netif_rx
[ 5789.986918] ndiswrapper: Unknown symbol netif_rx
[ 5789.987117] ndiswrapper: disagrees about version of symbol remove_proc_entry
[ 5789.987121] ndiswrapper: Unknown symbol remove_proc_entry
[ 5880.597655] APIC error on CPU0: 40(40)
[ 5893.763920] ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
[ 5893.763926] ndiswrapper: Unknown symbol per_cpu__softnet_data
[ 5893.764040] ndiswrapper: disagrees about version of symbol misc_deregister
[ 5893.764044] ndiswrapper: Unknown symbol misc_deregister
[ 5893.764204] ndiswrapper: disagrees about version of symbol unregister_netdev
[ 5893.764215] ndiswrapper: Unknown symbol unregister_netdev
[ 5893.764388] ndiswrapper: disagrees about version of symbol create_proc_entry
[ 5893.764392] ndiswrapper: Unknown symbol create_proc_entry
[ 5893.764646] ndiswrapper: disagrees about version of symbol register_netdev
[ 5893.764650] ndiswrapper: Unknown symbol register_netdev
[ 5893.764678] ndiswrapper: disagrees about version of symbol free_netdev
[ 5893.764682] ndiswrapper: Unknown symbol free_netdev
[ 5893.764829] ndiswrapper: disagrees about version of symbol proc_net
[ 5893.764833] ndiswrapper: Unknown symbol proc_net
[ 5893.764861] ndiswrapper: disagrees about version of symbol proc_mkdir
[ 5893.764864] ndiswrapper: Unknown symbol proc_mkdir
[ 5893.764886] ndiswrapper: disagrees about version of symbol misc_register
[ 5893.764890] ndiswrapper: Unknown symbol misc_register
[ 5893.764976] ndiswrapper: disagrees about version of symbol netif_rx
[ 5893.764980] ndiswrapper: Unknown symbol netif_rx
[ 5893.765179] ndiswrapper: disagrees about version of symbol remove_proc_entry
[ 5893.765183] ndiswrapper: Unknown symbol remove_proc_entry
[ 5977.946569] ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
[ 5977.946576] ndiswrapper: Unknown symbol per_cpu__softnet_data
[ 5977.946697] ndiswrapper: disagrees about version of symbol misc_deregister
[ 5977.946701] ndiswrapper: Unknown symbol misc_deregister
[ 5977.946860] ndiswrapper: disagrees about version of symbol unregister_netdev
[ 5977.946864] ndiswrapper: Unknown symbol unregister_netdev
[ 5977.947037] ndiswrapper: disagrees about version of symbol create_proc_entry
[ 5977.947041] ndiswrapper: Unknown symbol create_proc_entry
[ 5977.947301] ndiswrapper: disagrees about version of symbol register_netdev
[ 5977.947305] ndiswrapper: Unknown symbol register_netdev
[ 5977.947334] ndiswrapper: disagrees about version of symbol free_netdev
[ 5977.947337] ndiswrapper: Unknown symbol free_netdev
[ 5977.947479] ndiswrapper: disagrees about version of symbol proc_net
[ 5977.947483] ndiswrapper: Unknown symbol proc_net
[ 5977.947510] ndiswrapper: disagrees about version of symbol proc_mkdir
[ 5977.947514] ndiswrapper: Unknown symbol proc_mkdir
[ 5977.947536] ndiswrapper: disagrees about version of symbol misc_register
[ 5977.947540] ndiswrapper: Unknown symbol misc_register
[ 5977.947626] ndiswrapper: disagrees about version of symbol netif_rx
[ 5977.947630] ndiswrapper: Unknown symbol netif_rx
[ 5977.947836] ndiswrapper: disagrees about version of symbol remove_proc_entry
[ 5977.947839] ndiswrapper: Unknown symbol remove_proc_entry
[ 6135.719570] ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
[ 6135.719577] ndiswrapper: Unknown symbol per_cpu__softnet_data
[ 6135.719691] ndiswrapper: disagrees about version of symbol misc_deregister
[ 6135.719695] ndiswrapper: Unknown symbol misc_deregister
[ 6135.719861] ndiswrapper: disagrees about version of symbol unregister_netdev
[ 6135.719865] ndiswrapper: Unknown symbol unregister_netdev
[ 6135.720038] ndiswrapper: disagrees about version of symbol create_proc_entry
[ 6135.720042] ndiswrapper: Unknown symbol create_proc_entry
[ 6135.720302] ndiswrapper: disagrees about version of symbol register_netdev
[ 6135.720306] ndiswrapper: Unknown symbol register_netdev
[ 6135.720334] ndiswrapper: disagrees about version of symbol free_netdev
[ 6135.720338] ndiswrapper: Unknown symbol free_netdev
[ 6135.720479] ndiswrapper: disagrees about version of symbol proc_net
[ 6135.720483] ndiswrapper: Unknown symbol proc_net
[ 6135.720511] ndiswrapper: disagrees about version of symbol proc_mkdir
[ 6135.720515] ndiswrapper: Unknown symbol proc_mkdir
[ 6135.720536] ndiswrapper: disagrees about version of symbol misc_register
[ 6135.720540] ndiswrapper: Unknown symbol misc_register
[ 6135.720626] ndiswrapper: disagrees about version of symbol netif_rx
[ 6135.720630] ndiswrapper: Unknown symbol netif_rx
[ 6135.720843] ndiswrapper: disagrees about version of symbol remove_proc_entry
[ 6135.720847] ndiswrapper: Unknown symbol remove_proc_entry
[ 6181.272633] ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
[ 6181.272640] ndiswrapper: Unknown symbol per_cpu__softnet_data
[ 6181.272754] ndiswrapper: disagrees about version of symbol misc_deregister
[ 6181.272758] ndiswrapper: Unknown symbol misc_deregister
[ 6181.272917] ndiswrapper: disagrees about version of symbol unregister_netdev
[ 6181.272921] ndiswrapper: Unknown symbol unregister_netdev
[ 6181.273101] ndiswrapper: disagrees about version of symbol create_proc_entry
[ 6181.273105] ndiswrapper: Unknown symbol create_proc_entry
[ 6181.273359] ndiswrapper: disagrees about version of symbol register_netdev
[ 6181.273363] ndiswrapper: Unknown symbol register_netdev
[ 6181.273391] ndiswrapper: disagrees about version of symbol free_netdev
[ 6181.273395] ndiswrapper: Unknown symbol free_netdev
[ 6181.273544] ndiswrapper: disagrees about version of symbol proc_net
[ 6181.273548] ndiswrapper: Unknown symbol proc_net
[ 6181.273576] ndiswrapper: disagrees about version of symbol proc_mkdir
[ 6181.273579] ndiswrapper: Unknown symbol proc_mkdir
[ 6181.273601] ndiswrapper: disagrees about version of symbol misc_register
[ 6181.273605] ndiswrapper: Unknown symbol misc_register
[ 6181.273691] ndiswrapper: disagrees about version of symbol netif_rx
[ 6181.273695] ndiswrapper: Unknown symbol netif_rx
[ 6181.273894] ndiswrapper: disagrees about version of symbol remove_proc_entry
[ 6181.273898] ndiswrapper: Unknown symbol remove_proc_entry
[ 6463.260001] APIC error on CPU0: 40(40)
```

Any help would be extremly appreciated.

---

### Post by Fully216 on 2006-08-03
I had ndiswrapper and my Broadcom BCM4306 card working.  When I updated to the new nvidia driver found at nvidia.com, it required me to uninstall the linux-restriced-modules (required for ndiswrapper).  Now I am getting the same error you are.  

Does anyone have a solution?  I want to keep the working Nvidia driver so I can use video acceleration for Matlab 7, but a working ndiswrapper needs the  package restriced-modules.

FYI, I thought this might shed some light on your problem.

---

### Post by Fully216 on 2006-08-04
I ended up reinstalling the restricted modules after the nvidia update, and my video card works fine.  I guess it is only for the installation of the graphics driver that the restricted module should not be present.

So running sudo make uninstall under the ndiswapper directory was not enough to get everything in a pre-installed state.  I had to do a 'locate ndiswrapper' (in terminal window) and manually remove all the other stuff that was put all over my system with:

 sudo rm -fr /(directory leading to files)/ndiswra*

I had to reinstall my linux-headers package via synaptic package manager because I modified it when I removed all the ndiswrapper stuff.

From there I followed the steps found in this guide.

 [http://www.runithard.com/HOWTO-BCOM64WIRELESS/](http://www.runithard.com/HOWTO-BCOM64WIRELESS/)

Notice that most people forget to link their kernel headers with the following

 ln -sf /usr/src/linux-headers-2.6.15-26-amd64-generic /lib/modules/2.6.15-26-amd64-generic/build

from there, the installation is simple.  Uncompress and install the ndiswrapper package with:

 sudo tar xvfz ndiswrapper-1.21.tar.gz
 cd ndis*
 sudo make distclean
 sudo make
 sudo make install

I extracted the 64-bit driver for my broadcom bcm4306 and loaded it into ndiswrapper by doing the following.

 ndiswrapper -i netbc564.inf

You should install the corresponding driver for your wireless chipset.  Most of them can be found in these forums using the search function.  Ther are also some linux drivers listed here:

 [http://aircrack-ng.org/doku.php?id=drivers](http://aircrack-ng.org/doku.php?id=drivers)

As before, ndiswrapper -l displays:
  
 Installed ndis drivers:
 netbc564        driver present, hardware present

Now when I run

 modprobe ndiswrapper

I get no errors!!  Yea!!  Hope this helps!

---

### Post by thewierdone2000 on 2006-08-23
Sorry for a very late response, but thank you for the great post above. I got to the point, when i type ndiswrapper -i file.inf, to which it echo's back ```
Forcing parameter IBSSGMode|0 to IBSSGMode|2
```

ndiswrapper -l shows driver and hardware as present, and it modprobes with no error, but then when I type ```
ifconfig wlan0 up
``` it says no such interface.

lsmod shows ndiswrapper as installed.

Any more help? Thanks!

---

### Post by Fully216 on 2006-08-24
if you type iwconfig, it will list wireless interfaces instead all all interface types.  your card is probably not listed under wlan0.  In my case for example, my broadcom card is under eth1 and my Proxim atheros card is listed as ath0.

You might also might want to check to see what is your default device.  You you go to admin > networking, you should see all the devices (modem, ethernet, and now your wireless).  Make sure at the bottom that the default device is one of the devices instead to blank.  In my case, I use my wireless device, eth1.  This will also help give you the device name.

Could you post the output of the iwconfig command so we can see if there is a possible conflict.

Let me know if that helps.

---

### Post by Fully216 on 2006-08-24
.

---

### Post by WhiskeyTangoFoxtrot on 2006-09-29
```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

```i am also having the same problems as stated above in this string. ```
 sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-amd64-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)

``` any ideas ?

---

### Post by Fully216 on 2006-10-05
I think I remember reading that the issue is with the restricted-modules package.  I would check to see if it is present on your system when compiling ndiswrapper, but do not quote me on that.  I would try it with that package present to see if it helps.

There is also this guide that many people have found useful.  It provides a way to get ndiswrapper running without compiling it from source, which might fix the issue that you have.  In any case, it is worth looking into.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have also found personally and have read where people have had luck with using older versions of ndiswrapper.  I am now using version 1.8 instead of 1.25 (which gave me a phython debug error when I tried to upgrade versions).

Let me know if this helps!

---

### Post by mekas2024 on 2006-10-11
> **Fully216 said:**
> I think I remember reading that the issue is with the restricted-modules package.  I would check to see if it is present on your system when compiling ndiswrapper, but do not quote me on that.  I would try it with that package present to see if it helps.

There is also this guide that many people have found useful.  It provides a way to get ndiswrapper running without compiling it from source, which might fix the issue that you have.  In any case, it is worth looking into.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have also found personally and have read where people have had luck with using older versions of ndiswrapper.  I am now using version 1.8 instead of 1.25 (which gave me a phython debug error when I tried to upgrade versions).

Let me know if this helps!

Hey man, i have the problem of the error, this error:

mekas@mekas-laptop:~/Desktop$ sudo modprobe ndiswrapper FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-amd64-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg) 

Please could u help me, i have all day and all night long doing this and i just cant... i tryed what u said in a newer post about uninstall

> 
I ended up reinstalling the restricted modules after the nvidia update, and my video card works fine. I guess it is only for the installation of the graphics driver that the restricted module should not be present.

So running sudo make uninstall under the ndiswapper directory was not enough to get everything in a pre-installed state. I had to do a 'locate ndiswrapper' (in terminal window) and manually remove all the other stuff that was put all over my system with:

sudo rm -fr /(directory leading to files)/ndiswra*

I had to reinstall my linux-headers package via synaptic package manager because I modified it when I removed all the ndiswrapper stuff.

From there I followed the steps found in this guide.

[http://www.runithard.com/HOWTO-BCOM64WIRELESS/](http://www.runithard.com/HOWTO-BCOM64WIRELESS/)

Notice that most people forget to link their kernel headers with the following

ln -sf /usr/src/linux-headers-2.6.15-26-amd64-generic /lib/modules/2.6.15-26-amd64-generic/build

from there, the installation is simple. Uncompress and install the ndiswrapper package with:

sudo tar xvfz ndiswrapper-1.21.tar.gz
cd ndis*
sudo make distclean
sudo make
sudo make install

I extracted the 64-bit driver for my broadcom bcm4306 and loaded it into ndiswrapper by doing the following.

ndiswrapper -i netbc564.inf

You should install the corresponding driver for your wireless chipset. Most of them can be found in these forums using the search function. Ther are also some linux drivers listed here:

[http://aircrack-ng.org/doku.php?id=drivers](http://aircrack-ng.org/doku.php?id=drivers)

As before, ndiswrapper -l displays:

Installed ndis drivers:
netbc564 driver present, hardware present

Now when I run

modprobe ndiswrapper

I get no errors!! Yea!! Hope this helps!


Well, i installed ndiswarapper 1.19, cuz i found in another trhead that some guy could make this work with this version of ndiswrapper and my broadcom 4311, hooo by the way my ubuntu doesnt recognize the wireless card, when i do 

mekas@mekas-laptop:~/Desktop$  lspci | grep Broadcom\ Corporation
0000:05:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

i get that, but when i do :

mekas@mekas-laptop:~/Desktop$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present

So i dont understand very well, i have well installed the driver but not the card or what ??

I hopee u could help me :( im getting frustrated here !!

Thx A lot

Regards

MeKaS

---

### Post by Fully216 on 2006-10-12
There have been reports of people getting the 4311 chip working with version 1.23 of ndiswrapper.  From my experience, I have notice that this particular error indicates you should try a different version of ndiswrapper.  That was my workaround at least.

For installation help, see the following guide.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The drivers for you particular chipset can be found here.  It is a list of the known working computers and chipsets.  I would recommend a search for your particular machine on the list and match the revision, driver, and ndiswrapper version (if 1.23 fails).

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

A more difficult solution might be to try what user Radarsat-1 did: compiling the latest wireless-2.6 kernel (domesday branch), patching for PCI-E support, manually patching bcm43xx to recognize 4311, and installing the correct firmware (wl_apsta.o).  Depending on your level on linux know-how, I would recommend trying different version of ndiswrapper first.  The bcm43xx package is very problematic depending on your system configuration, which is why it is more complicated to get it working evidentally.

User capnrick has also got the 4311 working with version 1.23, although there is reported connectivity degridation (which might be unrelated to the ndiswrapper package).  He might be able to help with the details of the install.  There is also a how-to at the bottom of this page.

[http://www.ubuntuforums.org/showthread.php?t=140214&page=2](http://www.ubuntuforums.org/showthread.php?t=140214&page=2)
[http://www.ubuntuforums.org/showthread.php?t=193350](http://www.ubuntuforums.org/showthread.php?t=193350)  (notice: for ndiswrapper 1.17)

I know this is a lot to take in, but I am tring to offer as much help and resources as possible.  Good luck and let me know if you get any other problems or if there is anything else I can do.

---

### Post by mekas2024 on 2006-10-12
Hooo well... i still have the same error, i think i will format everything and install a fresh ubuntu, to start all over again and then i tell u wath happend !!

Thanks a loot for answer my question

See u later with the i hope good news lol, 

Take care

MeKaS

---

### Post by mello151 on 2006-10-18
I'm getting the same error as you and I just finished a clean install.  Let me know if you figure out how to fix it.

---

### Post by chevrier on 2006-10-19
I used to be able to use my Broadcom 4311, no matter which ndiswrapper I installed, by simply following the instructions given everywhere.
Now, I installed Ubuntu 64 bits, and nothing is working anymore!

specifically -   I am getting everyone else's problem:  no wireless extensions show  up anymore when i give "iwconfig".     I have not changed anything in the way I set up ndiswrapper.

also  my pointer is now acting weird.  When I click a window, it sometimes does nothing, sometimes work.  It was really bad, so I "upgraded" to edgy, and it did get better some.  but it's still not great!

Also, when I open something, it's incredibly slow, but when I type, then to the contrary, characters happen increddiiibly fast (see - this time, I left it, without fixing the re-types).  I had been using ubuntu without problems in 32 bits, but g... shifting to 64 bits seems tough!

Thanks for any inputs you may have.  rggds,
thomas

---

### Post by Fully216 on 2006-10-19
I understand your frustration with 64-bit ubuntu.  There is a lot more tweeking that needs to be done compared to the polished 32-bit version.  I had flash issues and more.  I did exprience the same strange issues with typing, where the text would be delayed (stored in buffer) and then fill the screen very fast.  This I fixed with powernowd to control the cpu frequency and changing to the correct keyboard settings.

Mouse problems could be fixed with a proper driver and xorg.conf setup.  For example, my laptop uses an Alps touchpad, which does not work well at all without the synaptic touchpad driver.  I then changed a few setting in my xorg.conf file and now it works beautifully.  I would suggest a similar procedure.  

[http://www.ubuntuforums.org/showthread.php?t=207371](http://www.ubuntuforums.org/showthread.php?t=207371)
[http://www.ubuntuforums.org/showthread.php?t=227147](http://www.ubuntuforums.org/showthread.php?t=227147)

Here is the link for the synaptics driver (if that is what you have).  [http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

---

