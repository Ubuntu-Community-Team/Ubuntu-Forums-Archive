---
title: "sudo permissions messed up"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubonetu on 2005-10-14
I installed as expert out of boredom and the installer prompted me for root passwd as well as a primary user.  Now whenever I sudo anything, it accepts the input, no response, but does nothing.  How do I fix this, please?

Thanks for listening,
UBONETU

---

### Post by ubonetu on 2005-10-15
I got it from the wiki, for some reason the installer doesn't add the primary user to the sudoers file which you can do (loggin in as root):

```
su
rootpasswd
visudo
```

Thenk add the user to the bottom of the file:

username  ALL=(ALL) ALL

ubonetu:D

---

### Post by ubonetu on 2005-10-15
okay the above is fine but very unsecure.  Now my sudo command requires no password.  Anybody?

Thanks,
ubonetu

---

### Post by ubonetu on 2005-10-15
I always talk to myself in here.  Here's the final "high tech" solution to the last onne:

```
sudo shutdown -r now
```

ubonetu;)

---

