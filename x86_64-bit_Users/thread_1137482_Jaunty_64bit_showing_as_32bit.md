---
title: "Jaunty 64bit showing as 32bit?"
date: 2009-04-25
forum: x86 64-bit Users
---

### Post by neilneil2000 on 2009-04-25
Hi all, 

I recently upgraded my server to 9.04 and everything went smoothly.  However today I did a ```
uname -a
``` and the output is

```
Linux Mediacentre 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686 GNU/Linux
```

This command is the only way I have ever used to tell me if I am running the 64 bit OS or not, and I am sure that before the upgrade it said ```
x86_64 GNU/Linux
```.

Maybe I am imagining things but is there any other way to check?

---

### Post by dBuster on 2009-04-25
uname -a Shows me that I am running the 64bit version...  Are you sure the distro you installed was a 64bit version???

---

### Post by neilneil2000 on 2009-04-25
I could have sworn it was!

But as I say, I just did a "do-release-upgrade" on it, and obviously can't go back and check.

The main reason for this post was that I was using "uname -a" as it seemed to correlate but I didn't know if this was the correct way to check or not

---

### Post by old_geekster on 2009-04-25
> **neilneil2000 said:**
> I could have sworn it was!

But as I say, I just did a "do-release-upgrade" on it, and obviously can't go back and check.

The main reason for this post was that I was using "uname -a" as it seemed to correlate but I didn't know if this was the correct way to check or not

When I use uname -a, it also shows that I have "9.04 X86_64-bit" installed.

---

### Post by jespdj on 2009-04-26
It is really impossible that the upgrade process replaced your 64-bit installation with a 32-bit installation. There is no way to upgrade (or downgrade) from 32-bit to 64-bit or vice versa; changing the architecture always requires a full installation of Ubuntu.

So if uname -a now indicates that you have the 32-bit version, then it is really not the case that you had the 64-bit version before the upgrade.

---

### Post by kamitsukai on 2009-04-26
Isn't it i686 = 64 bit and i386 = 32 bit?

so you are running 64 bit....

---

### Post by Sef on 2009-04-26
This is what it should looklike if you have 64-bit installed.

> Linux geeky 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux


---

### Post by neilneil2000 on 2009-04-26
Thanks all, obviously my brain is playing tricks on me!

---

