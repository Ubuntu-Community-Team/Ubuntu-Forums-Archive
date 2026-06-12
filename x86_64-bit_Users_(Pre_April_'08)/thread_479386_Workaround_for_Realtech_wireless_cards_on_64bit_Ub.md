---
title: "Workaround for Realtech wireless cards on 64bit Ubuntu"
date: 2007-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by RocketRanger on 2007-06-20
I have trying for days to make my 64bit Ubuntu's wireless capabilities work. I have finally found a solution that, although isn't very pretty, but at least it works and I now have a working wireless connection. If someone could expand on this perhaps it could be made even better.

I have a Zyxel Zyair g-302v3 card that uses a realtech chipset. The XP driver for this card won't work with ndiswrapper. However there is an alternative open source one that will. Go here for a guide on how to download and install it.

[http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

However my problem has been that my connection disppears on reboot when I use that driver. This happens for two reasons.

1) On load Ubuntu blacklists the driver. Do:
sudo nano /etc/modprobe.d/blacklist
and comment out the line that says r818x (add a # in front of it).

2) Subsequently Ubuntu loads a default driver for the networks card called r818x so in order to remove this driver and use the alternative linux driver the default one has to be removed and the alternative modules re-inserted into the kernel after each reboot.

My solution to this is the ugly (but functional!) hack.

Save this in a text file in the root of your home directory and make it executable.

```

sudo rmmod r818x
sudo rmmod r8180
sudo rmmod ieee80211_rtl
sudo rmmod ieee80211_crypt_ccmp_rtl
sudo rmmod ieee80211_crypt_tkip_rtl
sudo rmmod ieee80211_crypt_wep_rtl
sudo rmmod ieee80211_crypt_rtl

sudo insmod rtl-wifi/ieee80211/ieee80211_crypt-rtl.ko
sudo insmod rtl-wifi/ieee80211/ieee80211_crypt_wep-rtl.ko
sudo insmod rtl-wifi/ieee80211/ieee80211_crypt_tkip-rtl.ko
sudo insmod rtl-wifi/ieee80211/ieee80211_crypt_ccmp-rtl.ko
sudo insmod rtl-wifi/ieee80211/ieee80211-rtl.ko
sudo depmod -a
sudo insmod rtl-wifi/rtl818x-newstack/r8180.ko

sudo iwconfig wlan0 essid ####

```

If you replace the hashes with the name of your network and disabled wired networks in the networks manager this script will start you wireless network and attempt to connect.

This removes all the modules that have to do with this and reinserts them. It will output some errors when it can't find some of them. However after it has run your card should be enabled and you could select you network from the roaming list in the network manager. 

I don't know how to run the script automatically as you need to give your password when it runs (with all the sudo commands).

This has the disadvantage that you can't save you network id and has to login on each new session.

Furthermore the alternate driver doesn't display signal strength. Mine is at a fixed 30% compared to the 70% that is reported on similar install using ndiswrapper on a 32bit Ubuntu.

However if someone could help expand on this perhaps it could be made into a smooth solution for wireless realtech cards on feisty.

---

