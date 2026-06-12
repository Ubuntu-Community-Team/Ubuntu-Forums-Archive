---
title: "wifi walkthrough / howto help"
date: 2008-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Alistair1234 on 2008-02-25
I have recently installed gutsy 64 bit with no problems and many things worked right away. Unfortunately, wifi isn't one of them! When I look in network manager all i see is wired connection and modem connection - no mention of wireless.

I have searched the forums for any info but nothing seems to apply specifically to my system and since I am a bit of a newbie, I havn't  been able to make much sense of them. I have seen a few walk throughs which install ndiswrapper but nothing matches up with what I see when trying to do this so I get a bit lost!

Can someone help me sort this out or is there a howto around that people know of which will get my system working:

Acer aspire 5520
AMD64 turion x2
Nvidia GeForce 8400M 128mb card
2Gb ram
Gutsy 64-bit
Atheros AR5006EG 802.11 b/g Wireless PCI Express Adapter

Apologies if I have missed anything.

Any help is greatly appreciated.

Al

---

### Post by throwdart on 2008-02-26
I'm in the same boat, bro, just a slightly different netcard. I'll be watching this thread with avid interest.

---

### Post by throwdart on 2008-02-26
I downloaded ndiswrapper (allows ubuntu to run a "Windows bubble" of sorts, so that we'll be able to utilize the already functional Windows netcard driver in ubuntu) but the instructions were baffling to me. It's a completely foreign language, and I need a step by step how-to myself.
good luck to us both.

---

### Post by Yellow Pasque on 2008-02-27
@Alistair, the first step is obtaining the 64-bit Windows XP drivers for your chipset. Do you have them yet?

@throwdart, what kind of network card do you have? Have you located 64-bit Windows XP drivers for your chipset yet?

I found the following walkthrough useful to me (got my realtek8180 working on both Ubuntu and Arch Linux)

```
Hope this could be of any help.I have a Realtek 8185 Wireless card and was experiencing the same problems all of you describe. When I attempted to connect to a WEP enabled network my computer just locked (caps lock flashing) and nothing left to do but to press the power button and do a hard shutdown. After three or four freezes I would get the Kernel Panic message.


So I first typed
Code:

lshw -C network

in the terminal to find out which driver was controlling my wireless card and found that as in Rzulf's case it was the rtl8180 driver.

1. I followed Rzulf advice and blacklisted it and all of the options he describes in the /etc/modprobe.d/blacklist file

2. Then I installed ndiswrapper via synaptic (It installed version 1.45). And verified that it was installed issuing

Code:

ndiswrapper -v

3. After that I went to Realtek's website and downloaded the driver for my card (not RTL8180, but RTL8185, because that is the model of my card) and extracted the files to a folder in my Desktop.
The folder contained three files (net8185.cat net8185.inf rtl8185.sys).

4. Then in the terminal and inside the folder where the driver files were located I issued:

Code:

sudo ndiswrapper -i *****.inf

(where ******.inf is the name of the .inf file).
I verified that the driver was installed via

Code:

ndiswrapper -l

5. At this point after many tries, I finally got the message of net8185 driver installed device present.

6. I followed kevdog's detailed instructions to insert ndiswrapper module into the linux kernel

Code:

sudo depmod -a
sudo modprobe ndiswrapper

7. Next was to associate wlan0 with ndiswrapper

Code:

sudo ndiswrapper -m

8. The final part is to include ndiswrapper to be loaded at boot inserting the following line:
ndiswrapper
at the bottom of the /etc/modules file (you can edit it via...

Code:

gksu gedit /etc/modules

9. Rebooted my laptop

10. After reboot, I open a terminal window and issued

Code:

lshw -C network

and this time I had ndiswrapper+net8185 as the driver for mi wireless card, and now can successfully connect to open and secured networks without freezing or kernel panic.
```

---

### Post by YWELLC on 2008-02-27
Firstly, I am new to Ubuntu.  I am, however, networking competent (enough to manage my home / small office networks in XP).  I chose to upgrade to XP Pro X64 and try the 64 bit release of Gutsy 7 at the same time.   Through my own ignorance I did not plan ahead when purchasing my (new) WiFi adapter.  Instead I tried to retrofit the equipment after I screwed up.  Without overburdening anyone with the (tragically hilarious) details of the transition I wanted to post what little advice I can provide in regards to WiFi setup in x64 environment.

Bear in mind that I have only limited exposure to Linux.  As it pertains to driver installation, I only know what I have learned through trial and error over the past 72 hours.  I have followed many of the "howto's" as in Temujin post, without success.  Yes, ndiswrapper was installed and working properly, yes I  obtained and installed the x64 drivers with no errors on boot, manually configuring the network did not help, etc. etc.  Anyway, I have read several posts on the subject and there are apparently lots of issues with ndiswrapper (in particular with 64 bit drivers, WEP and WPA encryption) and overall driver support in general for 64 bit Linux (not to mention Windows XP and vista x64).  This is not to say that the software isn't an excellent tool if applicable to your system.  I am not sure what your budget is like or how quickly you require a resolve, currently my desktop is on the bedroom floor (only direct access to cable modem) and needs to be moved back to the den before my girlfriend ditches me and I default on my mortgage...

Anyway, I have read that people in similar situations (XP x64, Unix & Linux distros, etc.) have had success by using an Ethernet to 802.11g wireless bridge.  There is a potential loss of performance associated with this option.  The advantage is there are no drivers to install.  Assuming you have a 100/1000 network adapter and it is already working (mine auto-configed during Gutsy install), you should be able to plug right into the bridge and connect it directly to a wireless network.  Another advantage of the product below in particular is "internet-like" setup options, allowing you to manage the device, including SSID, the WEP and WPA encryption, mac address filtering, etc. through a web browser without any potentially OS non-compatible front-end.  I am not sure if this is a standard for this type of equipment but thought it prudent to mention.

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1134692497433]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1134692497433")

I have not yet personally used this product, I am just giving you another potential avenue to resolve your WiFi problem.  I plan on purchasing and (attempting) installation before the end of the week as  all of my other, admittedly not expert, efforts thus far have been for naught.

Good luck.

---

### Post by YWELLC on 2008-02-28
I wanted to follow-up on my post from yesterday.  I connected my 64-bit Gutsy install to my wireless network (with WEP) last evening using an Ethernet --> 802.11g bridge.  I purchased a slightly different model:

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175239647577&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4757745678B07]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175239647577&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4757745678B07")

as it was the same price and will be compatible if / when I decide to upgrade to a Wireless-N router.  My girlfriend (literally never touched a Linux box before) configured the settings in Fx while I was in the shower.

Not sure if this is a viable option for you, but hope it helps.

---

