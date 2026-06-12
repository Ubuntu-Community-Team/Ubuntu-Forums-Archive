---
title: "Manual DHCP requests"
date: 2006-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by kamaiak on 2006-03-11
Hello all! I'd like to know how to turn off the automatic DHCP request at startup (this takes very long time if the computer is offline). Or can this be skipped "on the fly"? 

And finally, how can that request be done manually later? Both in GUI and in konsole would be nice if possible :)

---

### Post by Koybe on 2006-03-11
Comment "auto eth0" from your /etc/network/interfaces file.

If you want to manually ask for a dhcp request :
```
sudo dhclient eth0
```

---

### Post by kamaiak on 2006-03-11
That was fast :) Thank you!

EDIT: I had no "auto eth0" but i took  "iface eth0 inet dhcp" instead and it seemes to be working : )

Also, a follow up question: at startup i now get "synchronizing to ubuntu....etc FAILED". Now how can this check be removed, and what does it really do?

---

