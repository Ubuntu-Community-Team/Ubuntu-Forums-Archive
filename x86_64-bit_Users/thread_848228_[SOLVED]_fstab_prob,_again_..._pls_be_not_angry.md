---
title: "[SOLVED] fstab prob, again ... pls be not angry"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by stabu on 2008-07-03
Hi,

I know there's tons of threads on getting fstab to automount different partitions, and, actually, I have read a few (not all!) of them, but my problems continue.

Say my extra ext2 partition, well it's not set up,. so I have tried manually editting fstab (as root) and no go. I can manually mount it (again, as root) with the usual "mount -t auto /dev/sda10 /media/sda10" but despite a different options in fstab, there's seems to be something preventing the automount. The partition is recognised in dmesg, so there shoul dbe no problem there. In fact, it will even fsck it  on startup if I say so in fstab. So fstab is being read. I don't need to do anything in HAl, do I? It's not a removable drive. Any advice welcome. Until then I continue to read the man mount, etc. in the hope they'll enlighten me.

I am using Xubuntu 64bit Hardy.

Thank you!

---

### Post by chrisccoulson on 2008-07-03
Hi stabu, it might be useful if you could post your fstab. Also, could you post the output of the following:
```
sudo fdisk -l
ls -l /dev/disk/by-uuid/
```

---

### Post by stchman on 2008-07-03
> **stabu said:**
> Hi,

I know there's tons of threads on getting fstab to automount different partitions, and, actually, I have read a few (not all!) of them, but my problems continue.

Say my extra ext2 partition, well it's not set up,. so I have tried manually editting fstab (as root) and no go. I can manually mount it (again, as root) with the usual "mount -t auto /dev/sda10 /media/sda10" but despite a different options in fstab, there's seems to be something preventing the automount. The partition is recognised in dmesg, so there shoul dbe no problem there. In fact, it will even fsck it  on startup if I say so in fstab. So fstab is being read. I don't need to do anything in HAl, do I? It's not a removable drive. Any advice welcome. Until then I continue to read the man mount, etc. in the hope they'll enlighten me.

I am using Xubuntu 64bit Hardy.

Thank you!

Edit your fstab file and put this:

/dev/sda10 /media/sda10 ext2 defaults 0 0

Make the mount point if not already done.

```
sudo mkdir /media/sda10
```

Then type this in a terminal.

```
sudo mount -a
```

You should get an icon on your desktop.

Now to write to that partition do this in a window:

```
sudo chown -R $USER:$USER /media/sda10
chmod -R 755 /media/sda10
```

That should be all you need.

---

### Post by stabu on 2008-07-03
Thanks for your replies, I didn't get anywhere, it's good to get suggestions.

There's little point in putting up my fstab, honestly, it's changing all the time. I am continuously varying the options and typing "mount -a". You see I think my syntax is OK. It's another problem I'm having, fstab is not liking the partitions, perhaps it uses some special option when invoking mount (I assume mount is the command behind fstab).

When I saw stchman's permission suggestion, I said, ah, that's it! That's the sort of thing that would stump me. Unfortunately, I tried that and nothing.

I know it's going to be something idiotic. Right now my errors concern bad blocks on the partition. Oh yeah? Well manually invoking mount, doesn't cause problems, so I'm sure that's another red herring. Anyhow, many thanks for suggs.

---

### Post by stabu on 2008-07-03
SOLUZIONE TROVATA!

it's an lvm "thang"

For some reason, lvm is not default. This is a gaping omission, I would have thought (though I'm sure there are proper reasons), and, not that's it's hard to fix (it ain't: "apt-get install lvm2" and reboot).

Though I'm not a partition expert, but anyhow, all has come good again. My partitions come up OK. Cheers!

---

