---
title: "Atheros AR5007EG - yet another wireless question"
date: 2007-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by why? on 2007-05-29
I'm using Kubuntu, so there's no Restricted Driver Manager.

I'm fairly certain my wireless card, Atheros AR5007EG isn't even being recognized as a netowrk deive. The wireless card does not show up in the network settings, but my rj45 (eth0) does. 

iwconfig
```

lo          no wireless extensions

eth0     no wireless extensions

```

lspci -v
```

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
Sub: AMBIT Microsystems  Unknown device 0428
Capabilities: <access denied>

```
couldn't copy and paste, so I condensed. No internet on the affected laptop.


I've looked into the madwifi driver, but I don't know how to get it in KUbuntu, remember, no restricted driver manager. What can I do to get my wireless working?

---

### Post by why? on 2007-05-29
Oh, I think the problem is that the Atheros isn't being recognized as a network device. I"m not certain though. Is there a "Device manager" in Kubuntu?  I've tried the System settings, but nothing about the Atheros wifi was found.

---

### Post by druckus on 2007-06-01
Yeah I have the same card in my laptop as well.

The problem is in the madwifi driver. Apparently HAL in  madwifi doesn't support 7th gen Atheros yet.

I have been checking [http://people.freebsd.org/~sam]("http://people.freebsd.org/~sam") almost everyday since I had the laptop in hopes of a new HAL... but nothing yet.

---

### Post by why? on 2007-06-02
Yes, it's a shame the card is yet to be supported. The card itself, under windows, has remarkable range. The range is better than any other G card I've had. I can't wait for it to work with Kubuntu.

---

### Post by andrenl on 2007-06-08
I have a Acer Aspire 5100 with this wireless card and the same problem, now i'm using ndiswrapper but having some problens like system crashes, the final solution would be a native linux driver  i have been checking [http://people.freebsd.org/~sam/](http://people.freebsd.org/~sam/) every day wating for a new hal but nothing yet,:( .

lspci -v
>  02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at 34000000 (64-bit, non-prefetchable) [size=64K]


---

### Post by bobbyshafter on 2007-06-08
Same problem here.I thought the window driver is vista only.

I don think nds will work with a vista driver.

I have kubuntu fiesty on my 2 desktop,will be installing fiesty on my laptop as soon as there is a solution for wireless.

My labtop is the Acer Aspire 5570g.Do have a unstable cursor

---

### Post by why? on 2007-06-09
The 32bit XP driver for the 5007eg (AR2425 chipset) can be found at [http://www.atheros.cz/](http://www.atheros.cz/)  it works with XP, but not Kubuntu.

---

### Post by bobbyshafter on 2007-06-09
Will the xp driver work with ndis ?

Have anyone dual boot vista and fiesty 

I will have about 17 gig free after shrinking vista c drive.

Will fiesty overwrite vista mbr?

My laptop is a acer aspire 5570z with a 80 gig drive.

What about a usb wifi adapter i have a d-link WUA-2340 ,anyone able to get this working.

---

### Post by why? on 2007-06-10
I can't get the driver to work wih ndis, but maybe someone more skilled can fill us in.  

Fiesty will overwrite Vista MBR. Vista is a choice for boot from Grub, at least it was for me.

---

### Post by bobbyshafter on 2007-06-10
Can't wait to get fiesty on my laptop,i need wireless working.

Is there a  wifi usb adapter that's known to work with fiesty 

I would use this until support for the builtin adapter.

---

### Post by why? on 2007-06-11
I haven't seem to been able to find one that work with Kubuntu and the Atheros card installed. I tried blacklisting the Atheros driver and using an Asus WL107g, but it didn't work either :(

NOw I admit, the problem is likely in something I'm doing when trying to disable the Atheros card. BIOS doesn't let me disable it, so I had to blacklist the driver. I tried, per directions in another thread, and at least I could "see" available networks, but I couldn't connect to any of them, even ones without encryption. 

If you do find a cheap card, USB or PCIMA, please let me know.

---

### Post by why? on 2007-06-17
anyone had any luck with this chipset yet?

---

### Post by why? on 2007-06-21
O, I got it working, but I used PCLinux 2007. After install, I used ndiswrapper and the 32bit XP driver for the card and it worked right away!  This didn't happen with Kubuntu :(  but PC Linux isn't bad and it reminds me a lot of Kubuntu anyway :D

I used the driver from Atheros.cz

The connection worked with open, WEP and WPA without any configuration under PCLinux. I know this isn't a Kubuntu solution, but at least it's a step in the right direction.

---

### Post by Platypi007 on 2007-06-22
What did you do to extract the files for the driver?  As far as I can tell the reason it isn't working is because the .sys file that is needed for the driver is packed in a .cat file that the setup program extracts automatically...  In WinXP, at least.

---

### Post by marsmissionaries on 2007-06-22
I have had luck with the AR5008 chipset in the latest snapshots available here: [http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/)

Try the latest snapshot it may work for you despite you having a different chipset.

---

### Post by capiscuas on 2007-07-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/121819](https://bugs.launchpad.net/ubuntu/+bug/121819) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				:popcorn:
[Here]("http://ivangarcia.org/blog/?p=13") there is a post about how to install Ubuntu with a laptop with that WIFI Atheros card.

---

### Post by jakrav on 2007-07-10
I've got a Acer TravelMate 4310 with the Atheros AR5007EG chipset - and I have a working wireless connection.

Requirements:

Disable and remove madwifi module

Disable and blacklist the ath_pci module

Ndis driver: [Acer Ndisdriver]("ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip")

Ndiswrapper: version 1.47

I took me close to 2 weeks to find the solution ( = the right Ndis driver )

---

### Post by Mr. P. on 2007-07-10
My congratulations! 
I use SIDUX so far -- the Ndiswrapper install works even right on the Live-CD.
But I want Gnome, since this Acer Travelmate 2483 is for a newbee.

Can you please elaborate on the steps, how you managed to install the 1.47 Ndiswrapper and so on? I would be delighted if I could just copy & paste the code :D

Thanks in advance! ;)

And for the KDE-friends out there: So far this AR5007EG works out of the box only with Sidux and PCLinuxOS. Even Gutsy fails so far.

---

### Post by jakrav on 2007-07-11
This is how I remember(!) my way of getting the Ndiswrapper to work on my Acer TravelMate 4310 with the Atheros AR5007EG chipset. I might have missed a step or two, but we can add that later...

Step 1: Disable ath_pci

sudo rmmod ath_pci
sudo gedit /etc/modprobe.d/blacklist-common

add the following line at the end of the file

blacklist ath_pci

Save and close

Restart computer

Step 2: Remove the old ndiswrapper and all links to it's driver.
Code:
		  
sudo modprobe -r net5211
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper

Step 3: Build essentials

Code:
Use the synaptic package manager
Install the package called "build-essential" in the group called "Development"

Step 4: Install Ndiswrapper.

Go to [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
Download ndiswrapper-1.47.tar.gz to folder /home/username

Code:
     
cd /home/username/ 
sudo tar xvzf ndiswrapper-1.47.tar.gz 
cd /home/username/ndiswrapper-1.47/ 
sudo make 
sudo make install

Step 5: Load drivers with ndiswrapper.

Code:

cd /the_dir_you_put_the_wlan_drivers_into/ 
sudo ndiswrapper -i net5211.inf 
sudo ndiswrapper -l (shows if the driver is installed)

Step 6: Load ndiswrapper and check if it worked.

Code:

sudo modprobe ndiswrapper 
sudo dmesg (shows that the card is installed) 
sudo iwlist wlan0 scan (shows all APs surrounding you)

Step 7: Make sure Ndiswrapper is loaded during bootup.

Code:

sudo ndiswrapper -m

---

### Post by ddalavi on 2007-07-11
I have an Acer 5570Z and I have emailed them and Atheros asking for a driver that works with linux. I'll post it if I get a response. I'd suggest you all email Atheros and the companies that made your machines and ask for the drivers too. That way we can make our presence known and hopefully get more Linux compatibility from hardware manufacturers.

---

### Post by Mr. P. on 2007-07-12
> **ddalavi said:**
> I have an Acer 5570Z and I have emailed them and Atheros asking for a driver that works with linux. 

Ich _have_ this driver already!

[http://www.sharebigfile.com/file/191984/XP32-WHQL-5-3-0-35--Negative-Pole-70416-tar-gz.html]("http://www.sharebigfile.com/file/191984/XP32-WHQL-5-3-0-35--Negative-Pole-70416-tar-gz.html")

XP would not even recognise Atheros AR5007EG before I received this file from Acer Germany. I also got a modem driver "Silent_Install_Agere_2175(1040)_XP_WHQL" -- if somebody needs it.

So with this driver and the instructions of jakrav we might get Ubuntu Feisty do WLAN.

NB: This driver works fine with Ndiswrapper 1.47 under SIDUX, which is the future of Debian / Ubuntu.

---

### Post by jakrav on 2007-07-12
I have replaced my driver with the one from Mr. P. - It works!

Beware that Ubuntu uses an extra 20-30 seconds to boot ... I can't figure out why - yet.

---

### Post by jakrav on 2007-07-12
From my dmseg

[   39.631300] ndiswrapper version 1.47 loaded (smp=yes)
[   39.735159] ndiswrapper: driver net5211 (,04/05/2007,5.3.0.35) loaded
[   39.735362] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   39.735368] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   39.735416] ndiswrapper (ZwClose:2246): closing handle 0xf50e65a8 not implemented
[   39.735595] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   40.147619] ndiswrapper: using IRQ 19
[   40.251314] BUG: scheduling while atomic: ntos_wq/0/0x10000001/3872
[   40.251332]  [<c02eca48>] __sched_text_start+0x5f8/0xa90
[   40.251345]  [<c017dcb5>] do_lookup+0x65/0x190
[   40.251356]  [<c0120f46>] __cond_resched+0x16/0x40
[   40.251361]  [<c02ecf0a>] cond_resched+0x2a/0x40
[   40.251365]  [<c015c337>] __alloc_pages+0x247/0x340
[   40.251373]  [<c0172c91>] cache_alloc_refill+0x71/0x550
[   40.251380]  [<c015c463>] __get_free_pages+0x33/0x40
[   40.251383]  [<c0165abe>] __pte_alloc_kernel+0xe/0x60
[   40.251389]  [<c016aee5>] map_vm_area+0x105/0x160
[   40.251399]  [<c016b31c>] __vmalloc_area_node+0xdc/0x130
[   40.251407]  [<c016b42f>] __vmalloc+0xf/0x20
[   40.251411]  [<f8eabd62>] ExAllocatePoolWithTag+0x62/0x70 [ndiswrapper]
[   40.251448]  [<f8ea779f>] NdisAllocateMemoryWithTag+0x1f/0x40 [ndiswrapper]
[   40.251489]  [<f8ea87eb>] mp_timer_dpc+0x4b/0x70 [ndiswrapper]
[   40.251513]  [<f8eaa05c>] kdpc_worker+0x2c/0xd0 [ndiswrapper]
[   40.251537]  [<c0137314>] run_workqueue+0x94/0x140
[   40.251544]  [<f8eaa030>] kdpc_worker+0x0/0xd0 [ndiswrapper]
[   40.251568]  [<c0137d97>] worker_thread+0x147/0x170
[   40.251574]  [<c0120b40>] default_wake_function+0x0/0x10
[   40.251581]  [<c0137c50>] worker_thread+0x0/0x170
[   40.251584]  [<c013ac4a>] kthread+0xba/0xf0
[   40.251589]  [<c013ab90>] kthread+0x0/0xf0
[   40.251593]  [<c01044c7>] kernel_thread_helper+0x7/0x10
[   40.251600]  =======================
[   40.351174] wlan0: ethernet device 00:19:7e:7e:7c:3b using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   40.356290] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   40.359895] usbcore: registered new interface driver ndiswrapper

The driver works fine, but the bug above is reported.

---

### Post by Mr. P. on 2007-07-12
> **jakrav said:**
> I have replaced my driver with the one from Mr. P. - It works!

GREAT! Before I erase my SIDUX-partition and set-up Ubuntu I want(ed) to be sure, that it really works. Please check your recent how-to again, if it is complete. 

BTW: I can offer the Agere-modem driver as well, which also is still not available @ftp.acer.

> **jakrav said:**
> 
Beware that Ubuntu uses an extra 20-30 seconds to boot ... I can't figure out why - yet.
As far as I judge from the verbose start-up screen in SIDUX the extra-time is due to the WLAN connecting process.

dmesg
```

ndiswrapper version 1.45rc3 loaded (smp=yes)
intel_rng: FWH not detected
ndiswrapper: driver net5211 (,04/05/2007,5.3.0.35) loaded
PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
ndiswrapper (ZwClose:2247): closing handle 0xdf0b94e8 not implemented
PCI: Setting latency timer of device 0000:03:00.0 to 64
ndiswrapper: using IRQ 17
iTCO_vendor_support: vendor-support=0
iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
wlan0: ethernet device 00:19:7e:24:da:f2 using serialized NDIS driver: net5211,
version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C
.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP w
ith WPA, WPA2, WPA2PSK

```

---

### Post by soulitary on 2007-07-12
I was soo close to returning this Acer 5570Z and getting somethign else because the wireles din't work and I have an UUGGGly D-Link PCI card sticking out. THANK YOU for figureing this out. I love you guys.

Acer Aspire 5570Z
Ubuntu 7.04 w/ COmpiz Fusion..


Wifi WORKS!!!!:)

---

### Post by Mr. P. on 2007-07-13
> **soulitary said:**
> THANK YOU for figureing this out.
Wifi WORKS!!!!:)

Can you plz elaborate for all the desperate Acer-users out there on how you achieved it ? 

Did you just follow jakrav's instructions here [http://ubuntuforums.org/showpost.php?p=3003336&postcount=19]("http://ubuntuforums.org/showpost.php?p=3003336&postcount=19")
and loaded "my" driver?

Cheers =D>

---

### Post by soulitary on 2007-07-17
used Jakrav instructions and Mr. P's driver which you cna find on any Atheros ubuntu 5570z google search.

---

### Post by mulan on 2007-07-27
Yes i followed the same path, and it recognised my card and now i can see the wlan networks in the network manager. BUT i cant connect to them??
As a 1 day old newbie i dont know what to do?
Did i do anything wrong, even though evertyhing appears looking good?

ok after some help i got to know about wicd a network manager, and afer instalation my WLAN works all right!

---

### Post by bmartin on 2007-07-29
I've started a [thread with a HOWTO]("http://ubuntuforums.org/showthread.php?t=512828") on this chipset (AR5007EG). I hope it works for you.

---

### Post by fofo412 on 2007-08-03
My solution to the linux-laptop-wireless-trouble is:  Netgear WG511T.

It's an Atheros based card that you stick in the side of your laptop, and works out of the box (54 mbps, Wireless G, blah blah blah).

The card sells for < $30 USD on eBay.  Granted, it sucks having to shell out more cash for a new card, when your computer (which I can only assume is a new laptop) already has one, but A.) It saves you the hassle and  headache  B.) IF you ever get that wireless card working -- sell the Netgear!  Or not, since it works right out of the box, and has been loyally connecting you to the internet for years!

---

### Post by ntlam on 2007-08-16
helpers...
I've been following many solutions with no success.
Here's what i did:

Step 1: Disable ath_pci

sudo rmmod ath_pci
sudo gedit /etc/modprobe.d/blacklist-common

add the following line at the end of the file

blacklist ath_pci

Save and close

Restart computer

step 2. remove old ndiswrapper by using synaptics

Step 3: Build essentials
Use the synaptic package manager
Install the package called "build-essential" in the group called "Development"
But I already got it installed

Step 4: Install Ndiswrapper.

Go to [http://sourceforge.net/project/showf...group_id=93482](http://sourceforge.net/project/showf...group_id=93482)
Download ndiswrapper-1.47.tar.gz to folder /home/username

Code:

cd /home/username/
sudo tar xvzf ndiswrapper-1.47.tar.gz
cd /home/username/ndiswrapper-1.47/
sudo make
sudo make install

Step 5: Load drivers with ndiswrapper.
sudo ndiswrapper -i net5211.inf

installing net5211 ...

forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
........ a lot of lines like above...

then:
sudo ndiswrapper -l 
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

Step 6: Load ndiswrapper and check if it worked
sudo modprobe ndiswrapper 

Check it: 
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Then I did:

sudo ndiswrapper -m


But no wireless after reboot

Any suggestion? 

Thanks

---

### Post by bmartin on 2007-08-16
That sounds pretty similar to my experiences.

The only thing I can think of is to check /etc/iftab and add a mapping to your WiFi card. You need the MAC address of your card. So if your MAC address is 00:08:05:17:FD:EB, you'd have a line in it that says:

wlan0 mac 00:08:05:17:FD:EB arp 1

Or something similar to that. If it doesn't match your card, then that's the problem, but I'm guessing there's no such line in there. I'm not an expert on the iftab file; I don't know what kind of effect adding the line in manually would have.

---

### Post by ntlam on 2007-08-16
Here what i got in that file:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:1b:24:52:f6:c1 arp 1


so there is no wlan0...

---

### Post by ntlam on 2007-08-16
it worked
[http://ubuntuforums.org/showthread.php?p=3202754#post3202754](http://ubuntuforums.org/showthread.php?p=3202754#post3202754)

---

### Post by bks on 2007-10-24
I have an Aspire 5050 with the infamous wifi card and I have opted to use my Belkin PCMCIA card.  I jack it in and its good to go.  A shame I have to suppliment with another card, but it could be worse...I could be using M$!

---

