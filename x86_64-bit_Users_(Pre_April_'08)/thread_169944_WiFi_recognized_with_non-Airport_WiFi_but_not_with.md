---
title: "WiFi recognized with non-Airport WiFi but not with Airport"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by HarrisonBea on 2006-05-03
I have a MacBook Pro running Parallels Virtual Machine and Ubuntu 5.10 installed.  When I am in my public library I can connect to the DHCP WiFi system.  When I am at home I can't get Ubutnu to connect.  No settings are different, just the available WiFi network.  When I switch from Parallels/Ubuntu back to Mac OS X my WiFi connection works fine in both places.  Any ideas, anyone?](*,)

---

### Post by Audiophiliac on 2006-05-04
Try using 5 char 40/64bit wep or 13char 128bit wep at home. More often than not its the encryption that messes up a wifi connection. I find the 5 char 40/64bit wep to be most stable but of course least secure.

---

### Post by HarrisonBea on 2006-05-04
[QUOTE=Audiophiliac]Try using 5 char 40/64bit wep or 13char 128bit wep at home. More often than not its the encryption that messes up a wifi connection. I find the 5 char 40/64bit wep to be most stable but of course least secure.[/QUOTE]

Thanks for the recommendation, but how do I do that?  Are these settings I can adjust from the "AirPort Admin Utility"?:confused:

---

### Post by AlphaMack on 2006-05-04
Did you try to add a 's:' (without quotes) to the beginning of the passphrase in Ubuntu?

Example:  passphrase is 'mywireless' ==> you would enter 's:mywireless'

---

### Post by Audiophiliac on 2006-05-05
Yes, you do that with admin utility. Borrow an OSX mac or pc. Or you can try installing Jon Sevy's Admin tool. It runs on java so it might run on Linux. Easiest would be to use OSX with Airport Admin.

---

### Post by HarrisonBea on 2006-05-05
[QUOTE=Audiophiliac]Yes, you do that with admin utility. Borrow an OSX mac or pc. Or you can try installing Jon Sevy's Admin tool. It runs on java so it might run on Linux. Easiest would be to use OSX with Airport Admin.[/QUOTE]

Well I am running this on my MacBook Pro with Tiger, so Airport Admin Utility is no problem.  I am just looking for how to change the setting. Thanks.

---

### Post by HarrisonBea on 2006-05-05
[QUOTE=alphasubzero949]Did you try to add a 's:' (without quotes) to the beginning of the passphrase in Ubuntu?

Example:  passphrase is 'mywireless' ==> you would enter 's:mywireless'[/QUOTE]


I don't understand what this does, why to do it, and how to do it.  Would you explain, please?

---

### Post by Audiophiliac on 2006-05-05
Most inability to connect among wifi deviced is due to encryption management. Using incorrect wep settings like the required number of characters causes such problems.

Open Airport Admin using OS X. Highlight your basestation name. It must be listed. If not, you must connect using a lan cable. Then click Configure. Click Wireless security. Choose 40bit wep and type in your 5 character ascii password (alll letters.) Then click OK. Then click Update. It will restart. Click OK. Your laptop must see the basestation after it restarts.

---

### Post by giaguara on 2006-05-06
Can't connect here either.

Currently no password in AP system.
Only MAC access control on, and the Kubuntu's wireless card address is on access control list of allowed machines.
 
I can't seem to be able to disable the WEP key in Neywork Settings on ubuntu. Also the eth1 = wireless interface gets active for less than one second, then disactivates always again.

So getting tired of ethernet connections ..

---

