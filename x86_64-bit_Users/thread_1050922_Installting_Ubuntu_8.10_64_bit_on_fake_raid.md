---
title: "Installting Ubuntu 8.10 64 bit on fake raid"
date: 2009-01-26
forum: x86 64-bit Users
---

### Post by siliond on 2009-01-26
I followed instructions listed here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) 

But failed to set up grub, starting with step #25 in "In Long without detail as above (2008-10-26 update)" section.

root@ubuntu:/dev/mapper# grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
grub> root (hd0,/boot/grub/stage1)
root (hd0,/boot/grub/stage1)

Error 11: Unrecognized device string

---

### Post by mjleppan on 2009-03-07
I have the exact same problem.... except I am trying on x86.

Everything works fine till step 25...


Then when I do a "grub --no-curses...
I get this error message. ...

Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

Please help, I'm stuck and really want to get more into Linux....

---

### Post by siliond on 2009-03-07
I've been waiting for a reply since January. I did research the problem but couldn't find a real solution, so I don't think there is one.

Back to Windows my friend.

---

### Post by Chibone on 2009-03-08
Umm, looking at your grub output,instead of 

```
grub> root (hd0,/boot/grub/stage1)
root (hd0,/boot/grub/stage1)
```

you would do 

```
grub>find /boot/grub/stage1
```

and then after running that

```
grub> root (hd0,x)
```

where X is what comes out when finding the run command, and it would usually be a number.

Hope this helps.

You could also try the alternate cd installer (not the desktop cd). according to the page you linked.

---

### Post by TomB19 on 2009-03-08
This may not be helpful but I just installed Kubuntu 8.10 on a software RAID 5 root.  I chose to install /boot on a 1GB USB key.  The key cost me about 6 bucks, doesn't waste any existing HD space, and doesn't add noise/heat like putting an old HD in for /boot would.

The install was perfectly straight forward with the alternate install CD.  Boot times are fine.  I put the USB key at the back so you can't even see it.

---

