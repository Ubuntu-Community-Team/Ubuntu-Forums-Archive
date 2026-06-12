---
title: "can't su, but can sudo?"
date: 2009-08-29
forum: x86 64-bit Users
---

### Post by ryadav on 2009-08-29
Hi when I try to su, I get an error saying. "su: Authentication failure". However if I use sudo and type my password everything succeed OK.

Is this a bug? I don't think I have been compromised, since my PC is behind a router firewall. The most recent action I recall doing is installing new software and performing recent updates through system settings.

Anyone reported something similar?

---

### Post by TrueJournals on 2009-08-29
By default, the root account is locked in Ubuntu.  See: [https://help.ubuntu.com/community/RootSudo#Background Information](https://help.ubuntu.com/community/RootSudo#Background Information)

---

### Post by ryadav on 2009-08-29
Thank you for the reply, I just came to realize this also!

I must have been having flashback from my LFS experiences =P

---

### Post by aysiu on 2009-08-29
If you want a persistent root prompt, just use ```
sudo -i
```

---

### Post by jefelex on 2009-08-31
You could also enable root user in your users control panel - that is what I've done to let me use su (although I haven't used su on 8.10 - this was back with 7.04 - geesh it's been that long!! :-)

Time flies so quickly!!

John

I never knew about "sudo -i"  never dawned on me to use it that way!!

---

### Post by Clancy_s on 2009-09-03
Or try ```
sudo su
```

which used to work back in 7.10, I've not tried it since.

---

