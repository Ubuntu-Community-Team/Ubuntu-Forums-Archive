---
title: "Bug or due to a die'ing harddrive?"
date: 2009-03-26
forum: x86 64-bit Users
---

### Post by Lithum on 2009-03-26
When I try to run update manager i get this message:

'E:Read error - read (5 Input/output error), E:Read error - read (5 Input/output error), E:Problem opening /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

I've tried updating through terminal but it was giving me a bunch of BS as well.. I do have a dieing HDD, which is to the point where it tries to run the system check at bootup and if it goes too far in it wont boot up and i have to restart and catch it fast enough to skip the system check...

Any words of advice would be welcome. thanks in advance.

---

### Post by aurelieng on 2009-03-26
You can try to type the following lines in a terminal:
```
apt-cache clean all && apt-get update && apt-get upgrade
```

If this does not work, it's probably worth looking in the directory mentionned in the error message, and even check your filesystem for consistency with fsck.

---

### Post by Lithum on 2009-03-26
yeah thats not even working and i cant even access the file either...I spose its definitely time to invest into a new hard drive. Thanks.

---

### Post by Slim Odds on 2009-03-26
> **aurelieng said:**
> You can try to type the following lines in a terminal:
```
apt-cache clean all && apt-get update && apt-get upgrade
```

Those all need "sudo".

---

