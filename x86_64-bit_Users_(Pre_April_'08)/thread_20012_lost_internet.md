---
title: "lost internet"
date: 2005-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by smb2004 on 2005-03-14
i took my box home for school and tried to get ubuntu running with a wireless card to no success.  after a few boot up it stoped looking for internet on boot up.  now back and school with the internet and card installed ubuntu on i cant seem to get internet back.  ifconfig eth0 doesnt show an ipadress, and trying though networking, i click activate but the box simply becopme unchecked a few seconds later.

how can i simply reset the internet or run the application during install that dectected all that.  im running on dchp.

---

### Post by Boomstickz on 2005-03-14
try popping up a terminal and do a sudo dhclient with the ndiswrapper module loaded or whatever you use, and if you don't have to use ndiswrapper just ignore that and do the sudo dhclient, if that doesn't do it, thats just wierd

---

### Post by smb2004 on 2005-03-15
that did it.  thats what i knew i needed to do i just didnt know the command name. thakns!

---

