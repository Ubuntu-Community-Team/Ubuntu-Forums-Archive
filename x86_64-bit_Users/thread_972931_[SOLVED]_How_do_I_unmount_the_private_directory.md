---
title: "[SOLVED] How do I unmount the private directory?"
date: 2008-11-06
forum: x86 64-bit Users
---

### Post by Linux user 66 on 2008-11-06
I've activated the private directory feature using this guide:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

After logging out and back in, I see the directory mounted on my desktop, but I'm unable to unmount it by using the unmount option. 

The error message says: 

"umount: /home/(user name)/Private is not in the fstab (and you are not root)". 

How do I unmount it?

---

### Post by cariboo on 2008-11-06
Have you tried:

```
umount.ecryptfs_private
```

run the above command in a terminal as a normal user. To mount the private directory type the following as a normal user:

```
mount.ecryptfs_private
```

Jim

---

### Post by xak on 2008-11-06
> **cariboo907 said:**
> ```
umount.ecryptfs_private
```

run the above command in a terminal as a normal user. To mount the private directory type the following as a normal user:

```
mount.ecryptfs_private
```

That's all well and good, but it sure would be nice to use the shiny new eject button in the nautilus "Places" pane to dismount the Private dir.  I'm assuming nautilus is running as root, and thus can't umount the user-mounted Private dir?  I wonder if there is a permission change that would allow the dismount through nautilus...

---

### Post by Linux user 66 on 2008-11-07
> **cariboo907 said:**
> Have you tried:

```
umount.ecryptfs_private
```

run the above command in a terminal as a normal user. To mount the private directory type the following as a normal user:

```
mount.ecryptfs_private
```

Jim

That worked perfectly! Thanks a lot! :)

Do you know if there's a way I can keep it from automatically mounting when I log in?

---

