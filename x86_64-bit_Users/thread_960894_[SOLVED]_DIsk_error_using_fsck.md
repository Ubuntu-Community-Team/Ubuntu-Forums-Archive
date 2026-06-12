---
title: "[SOLVED] DIsk error using fsck"
date: 2008-10-27
forum: x86 64-bit Users
---

### Post by roshanjose on 2008-10-27
my system runs an automatic disk error check up whenever i boot it....there are some errors which i encountered and i couldnt figure out what to do. I have put the errors at 

[http://paste.ubuntu.com/63243/](http://paste.ubuntu.com/63243/)


plzz check it and tell me as soon as possible

---

### Post by Megatog615 on 2008-10-28
Try doing this at the prompt:
```
fsck -y /
```

---

### Post by roshanjose on 2008-10-29
well this worked out!!

i had to run this command thrice.....

1st i ran it in terminal......

and once while booting and then had to restart and then run the command again to wipe out completely the errors

---

