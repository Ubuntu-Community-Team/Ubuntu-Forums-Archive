---
title: "PowerBook Lombard Issues"
date: 2006-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by jhupiter on 2006-03-23
Newbie install of Ubuntu 5.10 Breezy on a well cared for PowerBook Lombard. Install itself seemed to go ok. BUT,

Problem 1) I tried to update Firefox and Thunderbird Followed directions in HowTo for Firefox, Thunderbird. But they don't run. Original Firefox and Thunderbird seem to work ok, but I'd like to have the features of v1.5+. How do I get my install to works and how do I check to make sure the install went properly?

Problem 2) Motorola WiFi PC card WN825G not recognized. I originally got this card because the old Airport on my old PB Titanium wasn't 801.11g compatible. But I understand that BCM4306 chipset based cards are not supported. Or at least not well supported for PPC/Ubuntu.

Problem 3) As workaround for Problem 2, I had AsusTek WL-167g USB WiFi adapter. No dice.

I've checked all the fora and haven't found any that address these problems. Any help appreciated.

John

---

### Post by ssam on 2006-03-24
to get firefox to work you'll need powerpc linux packages. you can use mine from [http://www.tygier.co.uk/linux/firefox.html](http://www.tygier.co.uk/linux/firefox.html) then use the same instructions as for the x86 install.

have a look at [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards) for info on which wireless cards work with ubuntu. (anything that needs ndiswrapper wont work on powerpc)

---

### Post by jhupiter on 2006-03-30
Here's my workaround: Read that Dapper is more PPC friendly. Tried to do install from CD.iso. Caused screen to go black and white (1/2 black and 1/2 white). Reinstalled Breezy 5.10 then set up upgrade script to upgrade to Dapper 6.06, which went without a hitch. Still no support for Airport card or Asustek WiFi adapter. But, local CompUSA store has sale on Belkin USB WiFi adapters, which are RALink chipset, which supposedly is better supported. Will try that first as time-saving (and therefore inexpensive) alternative before working through [https://wiki.ubuntu.com/HardwareSupp...ssNetworkCards](https://wiki.ubuntu.com/HardwareSupp...ssNetworkCards) .

---

