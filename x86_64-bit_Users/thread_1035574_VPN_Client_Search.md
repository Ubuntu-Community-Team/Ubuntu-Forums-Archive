---
title: "VPN Client Search"
date: 2009-01-09
forum: x86 64-bit Users
---

### Post by nkingcade on 2009-01-09
Has anyone heard of a Cisco VPN client that works with Ubuntu 8.10_x86_64? Or better yet, an IPSEC client that works with Ubuntu 8.10_x86_64? Thanks.

Neal

---

### Post by pytheas22 on 2009-01-09
I don't know about IPSEC, but you should be able to install a nice Cisco VPN plugin into Network Manager by typing:
```

sudo apt-get install network-manager-vpnc
```

Then simply left-click the Network Manager applet and you should see an option for configuring a VPN connection.

I know that I also compiled the command-line version of Cisco's VPN client last September on 64-bit Ubuntu 8.04, but I had to patch the source code first.  I thought the patch was required because Cisco didn't keep its code up to speed with the latest Linux kernel, but the fact that my system was 64-bit may have been a problem as well; I don't remember.  I'm not sure where I found the patch, but I can try to find it again for you if the Network Manager option won't work.

I'd bet a lot of money that there are IPSEC clients available too if you do some googling in the right places.

---

### Post by sillyxone on 2009-01-09
I've been using vpnc (the CLI version) for 2 years and it works very well. 

Sometimes it connects but has no activity (usually on public wireless). Using "--natt-mode cisco-udp" option fixed it.

Since vpnc is free software, I assume the 64bit version is no different from 32bit version.


You can try the UMN's instruction (scroll to Ubuntu section):
[http://www.cs.umn.edu/help/offsite/vpn.php](http://www.cs.umn.edu/help/offsite/vpn.php)

---

### Post by nkingcade on 2009-01-10
Thanks for the information. Will this client work with WICD Network Manager or do you know. I have a household wireless network. Again, thanks for your help.

Neal

---

### Post by pytheas22 on 2009-01-10
> Will this client work with WICD Network Manager or do you know.

No, unfortunately the Network Manager plugin won't work with wicd.  I don't know of anything that integrates VPN access with wicd.  Is there a reason you can't use Network Manager?

The command-line client should still work though.  Just type:
```

sudo apt-get install vpnc
```

to install it (I didn't realize in my original post that vpnc is in the repositories...I compiled it from source, but that was on Ubuntu 8.04; maybe there was no package for vpnc then).

---

