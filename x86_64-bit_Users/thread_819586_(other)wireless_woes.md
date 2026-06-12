---
title: "(other)wireless woes"
date: 2008-06-05
forum: x86 64-bit Users
---

### Post by Nobody_Holme on 2008-06-05
Rather similarly to the original thread with this title, my wireless card hates ubuntu, it seems.

I ran through the instructions given for my card in particular, got ndiswrapper running, and got the driver done, but then it all went a bit wrong.

I'm a complete newbie to anything other than windows, sadly, so i'm miles out of my depth with this kind of problem...

anywho, I'm running 7.04 (feisty, i think?) amd64, my wireless card is a netgear wg311v3, and this is the end of the terminal work that happened. (no idea where mrv8335 came from, I've never been near it, but it is conspicuosly the same as in the ubuntu wiki guide i was reading ([https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)))

user@PC:~$ ndiswrapper -l
ls: /etc/ndiswrapper/mrv8335: no such file or directory
:invalid driver
wg311v3: driver installed
        device (11AB:1FAA) present
user@PC:~$ sudo modprobe ndiswrapper
user@PC:~$ iwconfig
lo           no wireless extensions

eth0         no wireless extensions

eth1         no wireless extensions


So yeah, if anyone can spot what i'm doing wrong, or if theres something obvious I just plain havent done, please slap me and tell me.

Thanks in advance, Steve.

---

