---
title: "ipw2200 on aspire 5022?"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by trecciolino on 2006-03-04
Hello!

I've an acer aspire 5022 my WiFi card work right with the ndiswrapper. I use the win64 driver(bcmwl5.inf)...

I've to use the ipw2200 driver, is this possible with my card?? 

thanks

---

### Post by equilibrium on 2006-03-04
I thought the ipw drivers were for the intel pro wireless controllers :confused: 

The one on the aspire 5020's are broadcom.

I've just got a aspire 5024 and I have the wireless working using the ndiswrapper+[win64 drivers](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip) from the acer website.

The best guide I found was [here](https://wiki.ubuntu.com/WifiDocs/Acer5021WLMi_Amd64?action=show&redirect=WiFiHowto%2FAcer5021WLMiConfiguration)

you have to install acer_acpi for it to work as explained in the guide.
 It seems you need to compile the latest ndiswrapper manually instead of using the one on apt. Also make sure you have gcc-3.4 as gcc-4.0 doesn't seem to work ;)
```
wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz
tar xvzf ndiswrapper-1.7.tar.gz
cd ndiswrapper-1.7
make
sudo make install
```
not sure if this helps :)
I didn't have any troubles tho

---

### Post by equilibrium on 2006-03-05
I just wrote a [little howto](http://ubuntuforums.org/showthread.php?t=140007) on wireless and the acer aspire 502x series.

Not sure if it is of any help or not :confused:

---

### Post by trecciolino on 2006-03-05
thank you equilibrium...

But I've used the ndiswrapper a lot of time ago with the win64 driver and it works ok.
I've to use the ip2200 driver for my study....I think that I've to use a pmcia wireless card because m integrated one is Broadcom and the ipw is Intel...:(

---

