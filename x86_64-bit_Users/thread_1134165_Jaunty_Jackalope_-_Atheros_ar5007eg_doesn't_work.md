---
title: "Jaunty Jackalope - Atheros ar5007eg doesn't work"
date: 2009-04-23
forum: x86 64-bit Users
---

### Post by JimmyA on 2009-04-23
Today I upgraded to Jaunty from Inteprid.
The installation went fine but the Atheros ar5007eg network card is not working anymore.

I used ndiswrapper before but now it can't detect my network card anymore.
I tried to use the proprietary driver but when I click Activate I can see "This driver just got deactivated but is stil in use".

lspci -v does detect my network card.
```

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Atheros Communications Inc. Device 3067
	Flags: fast devsel, IRQ 16
	Memory at c0300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci, ath5k

```

---

### Post by jorgerojasfelix on 2009-04-23
Try with the madwifi driver it always works for me with 
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
I guess you&#314;l have to blacklist ndiswrapper and activate the support for atheros wireless.

---

### Post by JimmyA on 2009-04-23
I think I tried that too but I'm not sure.

A link to a guide would be nice next time...

---

### Post by MFilinK on 2009-04-23
How do I use madwifi? I'm a new user and would very much appreciate a little help.

---

### Post by jorgerojasfelix on 2009-04-23
Ok here's the method i use to get my wifi working with mad wifi.

1.- download the driver from [here ]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/") (I always choose the newest)

2.- Download all the things needed to compile
$sudo apt-get install build-essential linux-headers-`uname -r`

3.- extract the files
$sudo tar --xzvf /directory/file_name.tar.gz

4.- move to that directory
$cd /uncompressed_directory/file_name

5.- Compile
$sudo make

6.- Remove possible previous installed versions
$sudo rm -rf /lib/modules/`uname -r`/madwifi

7.- Install Driver 
$sudo make install 

8.- Reboot

this is from a guide from here (in spanish) that I used since 8.04 I'm gonna try it now with jaunty so I will post my experience for my box I'm using the atheros support from restricted drivers manager.

Hope it helps 

Greetings from México

---

### Post by jorgerojasfelix on 2009-04-23
Just updating my wireless card worked out of the box with jaunty

---

### Post by dBuster on 2009-04-23
Check out the HOW-TO for Atheros wifi setups using mad-wifi

[http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780")

---

### Post by JimmyA on 2009-04-24
Thanks for the replys :)

I tried bith of them but neither did work. They both installed and made the network card appear in the network manager but it can't connect to my router(which is a few meters from the computer).

System log:
```

Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) starting connection 'NG-***-A' 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  (ath0): device state change: 3 -> 4 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0/wireless): access point 'NG-***-A' has security, but secrets are required. 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  (ath0): device state change: 5 -> 6 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  (ath0): device state change: 6 -> 4 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0/wireless): connection 'NG-***-A' has security, and secrets exist.  No new secrets needed. 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: added 'ssid' value 'NG-***-A' 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Apr 24 13:40:10 jimmy-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 24 13:40:10 jimmy-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> disconnected 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  (ath0): supplicant connection state:  disconnected -> scanning 
Apr 24 13:40:13 jimmy-laptop NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> associating 
Apr 24 13:40:23 jimmy-laptop NetworkManager: <info>  (ath0): supplicant connection state:  associating -> disconnected 
Apr 24 13:40:23 jimmy-laptop NetworkManager: <info>  (ath0): supplicant connection state:  disconnected -> scanning 
Apr 24 13:40:25 jimmy-laptop NetworkManager: <info>  (ath0): supplicant connection state:  scanning -> associating 
Apr 24 13:40:26 jimmy-laptop NetworkManager: <info>  ath0: link timed out. 

```
The last 7 lines reappears several times.

---

### Post by dBuster on 2009-04-24
Not to sound odd here, but did you verify the security settings?  So it sees the network adapter and it from what your showing is seeing your network which is evident by:

```
NetworkManager: <info>  Activation (ath0/wireless): connection 'NG-***-A' has security, and secrets exist.  No new secrets needed. 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: added 'ssid' value 'NG-***-A' 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Apr 24 13:40:10 jimmy-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Apr 
```

So now it is not the atheros card but rather something about the wpa security that you are running on your router and Jaunty.  I would search for that and try to figure that out.  Possibly set a WEP security up on the router and see if you can connect via WEP.  If you can then you are narrowing it down to possibly a wpa issue.

From the looks of it though, your Atheros card is working, which contradicts the topic title..

I searched for WPA issues with Jaunty and there is an open bug report...  So if you were to change the router from wpa to say WEP I bet you would connect...

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/348275]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/348275")

---

### Post by digitalextremes on 2009-04-24
before you do anything, install this package:

**linux-backports-modules-jaunty**

that resolved the issue that I was experiencing, with Lenovo T60 Atheros 5008.

I followed this thread and it worked [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/275692](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/275692)

Basically, my laptop kept asking me for the WPA key and never connected just kept trying to connect, it only connected it a few times, but after I installed the package listed above, it connects right away.

---

### Post by JimmyA on 2009-04-25
Today when I started my computer the wireless did work!:eek:
I have no idea how or why but it just did. I haven't changed anything at all.
The connection is stable and no errors in my syslog.
Well it's working now so I won't do anything to mess it up.


Thanks everyone for heping me, really appreciate it!:)

---

### Post by digitalextremes on 2009-04-25
have you tried what I suggested in this thread?....I have yet to experience any issues after I installed the package I suggested...scroll up to see.

---

### Post by kevinbsmith on 2009-04-27
Sorry for hijacking this thread, but I wanted to post my solution *somewhere* and this thread was similar enough that I figured it could go here. Perhaps this approach will work for problems with other Atheros chip variants too.

I recently upgraded from 8.04 through 8.10 to 9.04 Jaunty, and lost my wifi in the process. I have a no-name laptop with an AR5001X+ chip. Once in a while it would connect, but 99% of the time it would fail, asking for the network password over and over. (It also couldn't connect to an unprotected network).

I really didn't want to rebuild my kernel or try ndiswrapper or any of the other wild ideas I read about in dozens of forum and bug report threads. The solution for me ended up being pretty easy, once I figured it out (on my own):

1. Install linux-restricted-modules-generic so I would have the older ath_pci driver

2. Blacklist ath5k by creating /etc/modprobe.d/blacklist-ath5k.conf with the line:
    blacklist ath5k

3. Un-blacklist ath_pci by editing /etc/modprobe.d/blacklist-ath_pci.conf and commenting out the "blacklist ath_pci" line.

4. Reboot

As a nice side-effect, my mouse cursor no longer hesitates and jumps. Apparently the ath5k driver was causing frequent system stalls, resulting in a jumpy cursor. 

I hope to use ath5k in the future, but at least on my system, it's not ready yet.

---

### Post by dummiebeginner on 2009-04-28
Can someobody help?

I have a clean install of jaunty and these instructions below don't work.

Please someone, I am tired of my laptop never having wifi on Ubuntu. I know it can be done and I need to learn as I learnt for the graphic card.

> **jorgerojasfelix said:**
> Ok here's the method i use to get my wifi working with mad wifi.

1.- download the driver from [here ]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/") (I always choose the newest)

2.- Download all the things needed to compile
$sudo apt-get install build-essential linux-headers-`uname -r`

3.- extract the files
$sudo tar --xzvf /directory/file_name.tar.gz

4.- move to that directory
$cd /uncompressed_directory/file_name

5.- Compile
$sudo make

6.- Remove possible previous installed versions
$sudo rm -rf /lib/modules/`uname -r`/madwifi

7.- Install Driver 
$sudo make install 

8.- Reboot

this is from a guide from here (in spanish) that I used since 8.04 I'm gonna try it now with jaunty so I will post my experience for my box I'm using the atheros support from restricted drivers manager.

Hope it helps 

Greetings from México

---

### Post by JimmyA on 2009-04-28
> **dummiebeginner said:**
> Can someobody help?

I have a clean install of jaunty and these instructions below don't work.

Please someone, I am tired of my laptop never having wifi on Ubuntu. I know it can be done and I need to learn as I learnt for the graphic card.
I found a way to make the Atheros ar5007eg card work:
First make sure he have build essentials:
```

sudo apt-get update && sudo apt-get install build-essential

```

Download the archive.
```

wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz

```
Untar it.
```

tar -xvf madwifi-hal-0.10.5.6-current.tar.gz

```
Change to the dir.
```

cd madwifi-hal*-*-*/

```
Build it
```

make

```
Install it.
```

sudo make install

```
Load at startup
```

sudo modprobe ath_pci

```

Reboot and it should be up and running.

---

### Post by dummiebeginner on 2009-04-28
Thanks. I did all of that and rebooted and of course it doesnt work. But I guess I need to tell Ubuntu about my wifi connection and insert my password for instance

Could you please tell me what I need to type in these windows? I really don't know. SSI? MODE?? BSSID?? WEP??? WPA??? this is crazy.

[[IMG]http://img216.imageshack.us/img216/2063/pantallazowhx.th.png[/IMG]](http://img216.imageshack.us/my.php?image=pantallazowhx.png)

---

### Post by stchman on 2009-04-28
For Jaunty enable the backports.

```
sudo apt-get install linux-backports-modules-jaunty
```

Your wireless will then work along with the LEDs.

This worked on my Aspire One with the same wireless card.

---

### Post by dummiebeginner on 2009-04-28
> **stchman said:**
> For Jaunty enable the backports.

```
sudo apt-get install linux-backports-modules-jaunty
```

Your wireless will then work along with the LEDs.

This worked on my Aspire One with the same wireless card.

Nope. Not working. Thanks.

Can somebody tell me how you insert your wifi password and so on? How to configure the connection? Maybe that is the first problem, I don't know...

---

### Post by stchman on 2009-04-28
> **dummiebeginner said:**
> Nope. Not working. Thanks.

Can somebody tell me how you insert your wifi password and so on? How to configure the connection? Maybe that is the first problem, I don't know...

Did you then enable the driver in Hardware Drivers?

---

### Post by digitalextremes on 2009-04-28
> **stchman said:**
> For Jaunty enable the backports.

```
sudo apt-get install linux-backports-modules-jaunty
```Your wireless will then work along with the LEDs.

This worked on my Aspire One with the same wireless card.

Enabling backports worked for me on a Lenovo T60, never a had an issue after I did that, it would just try and try and try but never connected before that.

It also helped my friend who is using a Dell Inspiron.

---

### Post by dummiebeginner on 2009-04-30
Yes I did all of that but, again, when I go to "Wireless connections", there is no one (see the image I placed above). I guess I have to create one and introduce my password and so on, isn't it? But I don't know how.

ENabling backports didn't change anything in my case.

---

