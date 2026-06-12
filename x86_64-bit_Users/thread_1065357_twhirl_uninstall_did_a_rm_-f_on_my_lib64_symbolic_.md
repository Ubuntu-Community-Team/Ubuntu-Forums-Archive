---
title: "twhirl uninstall did a rm -f on my /lib64 symbolic link"
date: 2009-02-09
forum: x86 64-bit Users
---

### Post by PhilipJCaputo on 2009-02-09
I'm having a problem where when I uninstall twhirl on 8.10 amd64 where it deletes my /lib64 link to /lib.

A quick boot into a rescue disk and a ln -s /lib ./lib64 fixes the problem... but it requires a reboot.


Also, because I've had to recreate the /lib64 link from a rescue disk, it is currently chown 777, what should the /lib64 link permissions be?

---

### Post by dcstar on 2009-02-10
> **PhilipJCaputo said:**
> I'm having a problem where when I uninstall twhirl on 8.10 amd64 where it deletes my /lib64 link to /lib.

A quick boot into a rescue disk and a ln -s /lib ./lib64 fixes the problem... but it requires a reboot.


Also, because I've had to recreate the /lib64 link from a rescue disk, it is currently chown 777, what should the /lib64 link permissions be?

From my 8.04 system:

```
root@dc-master:/# ls -al lib64
lrwxrwxrwx 1 root root 4 2009-02-01 20:35 lib64 -> /lib
```

---

### Post by ndviking on 2009-02-13
It might be an Adobe Air problem and not specific to Twhirl.

I had this happen twice this week, once when updating Twhirl and again a couple of days later while updating Tweetdeck. In both cases it appeared to have happened during the uninstall of the older version.

---

### Post by jdong on 2009-02-13
Wow, that's nasty! I wonder if it looks at /lib64 as a symlink and concludes that it is "empty" and hence removable. Yikes!

Note that on Linux, permissions on symlinks are more or less undefined/ignored (they show up 777 as the owner of the person who made the symlink, by default); permissions are evaluated at the file that is linked to. This is not true of all *nix'es.

---

