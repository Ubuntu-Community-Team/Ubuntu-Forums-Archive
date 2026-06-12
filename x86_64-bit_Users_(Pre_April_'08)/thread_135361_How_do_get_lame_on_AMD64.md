---
title: "How do get lame on AMD64?"
date: 2006-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by raydel on 2006-02-23
I've read the threads, but I can't seem to find the answer.
Is it just not in the repository?  Has not been ported to 64 bit?
Can I compile this myself or does it die?
Anyone know?  I'm not newb I just need a push in the write direction.

---

### Post by kariopto on 2006-02-23
Yes you can.. I compiled it myself on amd64... 
here is a tutorial..
[http://www.yolinux.com/TUTORIALS/LinuxTutorialMP3.html#LAME]("http://www.yolinux.com/TUTORIALS/LinuxTutorialMP3.html#LAME")
hope it helps!

---

### Post by raydel on 2006-02-23
Thanks

---

### Post by Hallavej on 2006-02-23
lame is in the multiverse repository.

---

### Post by awi on 2006-02-24
[QUOTE=Hallavej]lame is in the multiverse repository.[/QUOTE]

```
deb http://py.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

I have multiverse, and AMD64. There is no [COLOR="Green"]lame[/COLOR]. :(

---

### Post by John Jason Jordan on 2006-02-24
[QUOTE=awi]```
deb http://py.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

I have multiverse, and AMD64. There is no [COLOR="Green"]lame[/COLOR]. :([/QUOTE]
I have AMD-64, Ubuntu-64 Breezy, and I have lame and lame-extras in Synaptic. I have had both installed for a long time and they work just fine.

The only repositories I have are:

**Ubuntu 5.10 "Breezy Badger" (Source)**
Community maintained (universe)
Officially supported
Restricted copyright
Non-free (Multiverse)

**Ubuntu 5.10 "Breezy Badger" (Binary)**
   Community maintained (universe)
   Officially supported
   Restricted copyright
   Non-free (Multiverse)

Dunno why your Synaptic does not list them.

---

### Post by Hallavej on 2006-02-24
[QUOTE=awi]```
deb http://py.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

I have multiverse, and AMD64. There is no [COLOR="Green"]lame[/COLOR]. :([/QUOTE]

Those are backports of main restricted universe and multiverse. You need to add
> deb [http://py.archive.ubuntu.com/ubuntu/](http://py.archive.ubuntu.com/ubuntu/) breezy multiverse
to get multiverse and not just the backports of it.

---

