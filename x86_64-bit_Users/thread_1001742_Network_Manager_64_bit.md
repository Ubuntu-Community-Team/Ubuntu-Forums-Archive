---
title: "Network Manager 64 bit"
date: 2008-12-04
forum: x86 64-bit Users
---

### Post by laser25 on 2008-12-04
I just installed Ubuntu 8.... 64 Bit, the network manager does not show up where it should...and when I try to install it its telling me that it does not support the 64 bit, so i can't get online from that desktop wired or wifi. Any suggestions? is there a 64 bit version of this network manager

---

### Post by Nepherte on 2008-12-04
Sure there is, although it's odd it doesn't show up of course. Just add nm-applet to System > preferences > sessions.

You can already verify that nm-applet works by running the command in a terminal. It should show up in the notificatin area.

---

### Post by andreasis on 2008-12-04
That is really odd, I agree.  Never happened to me.  Maybe neither your wired, nor wireless adapters are installed (properly) and so the network manager doesn't load... 

So you're saying when you run nm-applet or nm (I forgot which, I use wicd) from terminal, you get a message telling you that it's only 32 bit?  Are you using a stable release?  Some screenshots may help...

---

