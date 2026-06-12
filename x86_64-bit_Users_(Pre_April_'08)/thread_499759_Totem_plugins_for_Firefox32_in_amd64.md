---
title: "Totem plugins for Firefox32 in amd64"
date: 2007-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Herix on 2007-07-13
Hi. I have followed the following instructions  to install Firefox 32 bits in my amd64. [http://ubuntuforums.org/showthread.php?t=202537&highlight=how+to+firefox+32]("http://ubuntuforums.org/showthread.php?t=202537&highlight=how+to+firefox+32")

I used the manual Installation instead of the script. 

Everything works fine, the only problem is to get the totem plugins to my /usr/local/firefox32/plugins/ folder. 

That script to install totem doesn't tell me much. All I know is that it creates /usr/lib/win32/ directory, but the plugins for firefox are not there.... Where  are the plugins so I can put them in my firefox plugin folder?

Thanx

---

### Post by bollix47 on 2007-07-13
Try the following:

```
sudo updatedb
locate libtotem
```

The updatedb can take a while.

---

### Post by Herix on 2007-07-16
Thanks, this command is pretty handy.

---

