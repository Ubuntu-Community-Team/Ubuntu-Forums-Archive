---
title: "Kernel Panic when Attempting to Run 32-bit Ubuntu on 64-bit System"
date: 2006-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by AltiusBimm on 2006-11-12
I have decided to try putting 32-bit Ubuntu on my AMD Athalon64 2800+ system because I would like to have an easier time with closed-source software that has been complied only for 32-bit archetecture.

This should be simple enough, as even other threads on this forum would indicate, but apparntly something is wrong in my case.

When I attempt to "Run or Install Ubuntu" on my 64-bit system, I get:
```

[	37.031037] EIP: [<c0209fb1>] acpi_hw_low_level_read+0xa/0x7c SS:ESP 0068:df
[	37.301183]   Kernel Panic - not syncing: Attempted to kill init!
[	37.301302]   _

```

Also, and I find this very significant: When I attempt to "Run or Install Ubuntu" using the 32-bit CD on one of my 32-bit systems, the loader hangs after several minutes.

I would tend to think I simply have written a corrupt CD, but I have downloaded and burned the 32-bit CD image **twice**, once in 64-bit Ubuntu, once in Windows XP SP2, and still I have the same problem...whereas with the 64-bit CD image it worked immidiately.
I am baffled by the possiblity that the disc image could be corrupted twice in a row, and I felt I should post here before wasting any more CD-Rs.
](*,)

---

### Post by Trebaruna on 2006-11-12
I'm no expert on kernels, but the acpi bit in one of those lines is interesting. Maybe you could see if there are specific power related options in your BIOS that could be turned off/on?

The fact that your system supports 64 bit should not mean 32 bit installs fail. In fact, I would go so far as to say you'd be better off looking for the cause elsewhere (like ACPI options).

One thing you could try is ordering a pressed Ubuntu disk. That way you can be sure the files are okay.

---

### Post by Kilz on 2006-11-13
> **AltiusBimm said:**
> I have decided to try putting 32-bit Ubuntu on my AMD Athalon64 2800+ system because I would like to have an easier time with closed-source software that has been complied only for 32-bit archetecture.

This should be simple enough, as even other threads on this forum would indicate, but apparntly something is wrong in my case.

When I attempt to "Run or Install Ubuntu" on my 64-bit system, I get:
```

[	37.031037] EIP: [<c0209fb1>] acpi_hw_low_level_read+0xa/0x7c SS:ESP 0068:df
[	37.301183]   Kernel Panic - not syncing: Attempted to kill init!
[	37.301302]   _

```

Also, and I find this very significant: When I attempt to "Run or Install Ubuntu" using the 32-bit CD on one of my 32-bit systems, the loader hangs after several minutes.

I would tend to think I simply have written a corrupt CD, but I have downloaded and burned the 32-bit CD image **twice**, once in 64-bit Ubuntu, once in Windows XP SP2, and still I have the same problem...whereas with the 64-bit CD image it worked immidiately.
I am baffled by the possiblity that the disc image could be corrupted twice in a row, and I felt I should post here before wasting any more CD-Rs.
](*,)


Welcome to reality. Installing a 32bit operating system on 64bit hardware does not always work. It is not the cure all some people make it out to be.

---

### Post by AltiusBimm on 2006-11-13
Well, that's news to me...
But what's interesting is that only the 6.10 version fails.
Unfortunately this happens even when I upgrade 6.06 to 6.10 via http.

---

### Post by kuja on 2006-11-13
Could be an issue in the kernel if the Ubuntu 6.06 x86 worked flawlessly. I recommend reporting a bug on the Ubuntu 6.10 kernel in launchpad.

---

### Post by RAOF on 2006-11-14
> **Kilz said:**
> Welcome to reality. Installing a 32bit operating system on 64bit hardware does not always work. It is not the cure all some people make it out to be.

Installing a 32bit operating system on **32bit** hardware doesn't always work.  No-one (ok, no-one who is informed) is saying it's a cure-all for hardware problems.  The fact that the CPU can execute x86-64 instructions does not mean it's any less able to execute IA32 code.

Back to the actual problem, it looks like an ACPI problem (which are not uncommon).  You should be able to specify additional boot parameters at the bootup prompt.  Try adding "noacpi" to those options, and seeing if it'll boot.

[This thread]("http://www.ubuntuforums.org/showthread.php?t=297520&highlight=noacpi"), and in particular [this post]("http://www.ubuntuforums.org/showpost.php?p=1751272&postcount=7") might be of help.

---

### Post by Kilz on 2006-11-14
> **RAOF said:**
> Installing a 32bit operating system on **32bit** hardware doesn't always work.  No-one (ok, no-one who is informed) is saying it's a cure-all for hardware problems.  The fact that the CPU can execute x86-64 instructions does not mean it's any less able to execute IA32 code.

Back to the actual problem, it looks like an ACPI problem (which are not uncommon).  You should be able to specify additional boot parameters at the bootup prompt.  Try adding "noacpi" to those options, and seeing if it'll boot.

[This thread]("http://www.ubuntuforums.org/showthread.php?t=297520&highlight=noacpi"), and in particular [this post]("http://www.ubuntuforums.org/showpost.php?p=1751272&postcount=7") might be of help.

Thanks for adding the no one who is informed. But its quite common in the beginners area that some people tell people with 64bit systems that its "easier" to install the 32bit os.
I have read quite a few posts that make it sound like its the best thing since sliced bread.

---

### Post by kuja on 2006-11-14
```
if not subforum == "x86 64-bit Users":
      bestthingsinceslicedbread = "386"
```

wtf??

If only there were more informed people ....

---

### Post by RAOF on 2006-11-14
> **Kilz said:**
> Thanks for adding the no one who is informed. But its quite common in the beginners area that some people tell people with 64bit systems that its "easier" to install the 32bit os.
I have read quite a few posts that make it sound like its the best thing since sliced bread.

The thing is, the IA32 version **can** help with hardware support, but essentially only when using ndiswrapper.  Anything with even a remotely open driver will work just fine in x86-64 (or at least will be as likely to work in x86-64 as IA32), but for those poor people who need to use windows drivers, the i386 kernel **does** provide better hardware support.

---

### Post by Kilz on 2006-11-14
> **RAOF said:**
> The thing is, the IA32 version **can** help with hardware support, but essentially only when using ndiswrapper.  Anything with even a remotely open driver will work just fine in x86-64 (or at least will be as likely to work in x86-64 as IA32), but for those poor people who need to use windows drivers, the i386 kernel **does** provide better hardware support.

It may, but most of the time hardware is never brought up. Its like its automatic. Here are the posts I hate most about the forums.
1. Install the 386. (that amd64 version is just to hard you know)
2. No matter what you want to install. Get Automatix! (new people cant install anything, right?)
3. Post a question no matter if its been asked and answerd 5 million times already! (The search function doesnt exist!)

](*,)  its just eenough to drive ya to drink. :D

---

### Post by AgenT on 2006-11-15
Assuming that the kernel giving you problems is 2.6.17-10-generic (x86). Assuming your root partition / is on /dev/hda1.

NOTICE: Instructions below say to use su, if this fails, use sudo with the next line below the su command instead like so: sudo mkdir....

Boot your favorite Debian (based) LiveCD and start a terminal then (Knoppix is always reliable):
```
su -
mkdir -p /media/ubuntu
mount /dev/hda1 /media/ubuntu
chroot /media/ubuntu
```Now do a test:
```
echo "bbb" < /dev/null
```If you do not receive an error, continue. If you do receive an error, something is wrong with your permissions. Make sure you were root before you executed chroot!
```
apt-get update
apt-get install --reinstall linux-image-2.6.17-10-generic
exit
cd /
umount /media/ubuntu
shutdown -r now
```Reinstalling the linux-image package not only reinstalls all the files, but also updates a lot of programs that may be causing the kernel panic.

---

