---
title: "Services that do not automatically start"
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by skotos on 2009-11-13
In my LAN the *DHCP server* and the *privoxy* services do not automatically start.
I always have to manually run
```
sudo /etc/init.d/dhcp3-server start
sudo /etc/init/privoxy start
```Is there a way to fix this behaviour?
I have the following correct links:

[LIST=1]
[*]/etc/rc2.d/S40dhcp3-server -> /etc/init.d/dhcp3-server
[*]/etc/rc3.d/S20privoxy -> /etc/init.d/privoxy
[/LIST]
but no idea on what might be wrong.
Any idea?



OK SINCE I STRANGELY CANNOT ADD ANY MESSAGE TO A THREAD I HAVE STARTED, HERE FOLLOWS THE SOLUTION[INDENT]The solution is:
[/INDENT][INDENT] ```
sudo mv /etc/rc2.d/S[COLOR=Red]**40**[/COLOR]dhc3-server /etc/rc2.d/S[COLOR=Blue]**80**[/COLOR]dhc3-server
sudo mv /etc/rc3.d/S40dhc3-server /etc/rc3.d/S**[COLOR=Blue]80[/COLOR]**dhc3-server
sudo mv /etc/rc4.d/S40dhc3-server /etc/rc4.d/S[COLOR=Blue]**80**[/COLOR]dhc3-server
sudo mv /etc/rc5.d/S40dhc3-server /etc/rc5.d/S[COLOR=Blue]**80**[/COLOR]dhc3-server
```When rebooting, the DHCP Server will automatically start!

FYI
- I think it is a wrong *upstart* configuration/sequence
- I just tried 50 and it did not work, that's why I tried 80, a high enough value (99 being the maximum allowed). If you want to dig more, you can try values in the range [51,79]. The first reasonable values I would try might be 60 and 70...
[/INDENT]

---

