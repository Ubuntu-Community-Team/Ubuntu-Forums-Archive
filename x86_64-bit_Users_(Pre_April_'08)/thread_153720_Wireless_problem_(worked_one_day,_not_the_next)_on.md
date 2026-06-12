---
title: "Wireless problem (worked one day, not the next) on V200Z"
date: 2006-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by JoeyCorless on 2006-04-01
I'm using Ubuntu (32-bit version 5.10) on a  Compaq V2000Z with a Turion processor, with a built-in Broadcom wireless card.  I'm using a D-Link DI-524 router for my home network.  The wireless card worked fine yesterday after I installed the windows drivers and used ndiswrapper, and my connection was fine.  This morning, though, it was no longer able to connect to the network.  I checked the router, and it seemed that the setting were all restored to the defaults for some reason (the changes being that the port-forwarding I'd done was gone and the SSID was changed back to 'default').  So I changed everything back to how I had it, but my laptop still couldn't connect.  However, I booted it up in Windows and it auto-detected the network and connected fine.  I have a feeling it has to do with the settings not matching up.  Iwconfig shows the following:
lo      no wireless extensions.
eth0   no wireless extensions.
wlan0  IEEE 802.11g   ESSID:off/any
         Mode:Managed   Frequency:2.437GHz   Access Point:  00:00:00:00:00:00
         Bit Rate:54Mb/s     Tx-Power: 25dBm
         RTS thr:2347 B       Fragment thr: 2346
         Power Management: Off
         Link Quality:100/100   Signal level:-10 dBm      Noise Level:-256 dBm
         Rx invalid nwid:0   Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0   Invalid misc:0   Missed beacon:0
sit0    no wireless extensions.

Under interface properties, it is enabled, the Network name is Rumplestiltskin, the key type is hexadecimal, the WEP key is blank (I turned off WEP on the router as well to remove one complication until I figure this out), and it's using DHCP.

On my router's wireless settings, it has:
Wireless Radio : Enabled
SSID : Rumplestiltskin
Channel : 6
Mode Setting : Mix Mode
SSID Broadcast: Enabled
Security : Disabled


I can't figure out what the problem is (what's different now from yesterday).

Does anyone have any ideas how I could resolve this, or what the problem is?  It seems like it has to be a problem with my wireless settings in Ubuntu, since when I boot up in Windows it works fine.  Thanks for any help.

-Joey Corless

---

