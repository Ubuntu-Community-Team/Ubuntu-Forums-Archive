---
title: "Nwebie with SuSE 64 laptop"
date: 2008-08-15
forum: x86 64-bit Users
---

### Post by mmmooretx on 2008-08-15
I have SuSE 11 64 but have not gotten all items running.  Looking at umbuntu or kumbuntu 64 bit on a Presario F750US, 2 gig ram, 120 gig sata HD, wifi, bluetooth, etc.  I will start data mining this weekend but am considering moving if I can get wifi (madwifi works in SuSE), bluetooth (not working yet in SuSE), and sync with AT&T Tilt (HTC Kaiser) with 4 gig chip for calendar/address book (usb modem would be nice too).
Anyway I will read any links forwarded for tribal knowledge if it looks solid I will migrate.
Thank you in advance and greetings.

---

### Post by Thelasko on 2008-08-15
Speaking from personal experience from my days of using SUSE 9.2 back in 2005.  Ubuntu is way easier to use.  The big advantage of Ubuntu over SUSE is, you don't have to go searching for packages.  Maybe I didn't understand how SUSE works, but whenever I heard of a piece of software that was supposed to solve my problem, it wasn't available from Novell and I had to go hunt for it on some website and ended up in [dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell").

With Ubuntu, there are online servers (called repositories) that host every piece of software you will need.  You use a program called Synaptic to access these servers and it resolves all of your dependencies automatically.

I don't have Wifi on my Ubuntu machine because it's a desktop, but if madwifi worked in SUSE, I don't see why it won't work in Ubuntu.  Getting connected to the internet is really the most important part of installing Ubuntu so you can access the software repositories.

I have Bluetooth working on my machine.  I think I just had to install one piece of software, but I don't remember what it was (it took less than 5 minutes).  I can connect to my phone with a program called Wammu, but if you prefer, you can use bitpim.

Really, I don't know of many pieces of hardware that are completely unsupported in Ubuntu, the only thing that comes to mind are certain Lexmark printers.

---

### Post by Thelasko on 2008-08-15
[Here's]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi") how to install the madwifi driver in Ubuntu:
```
 sudo apt-get install linux-restricted-modules madwifi-tools
```

---

