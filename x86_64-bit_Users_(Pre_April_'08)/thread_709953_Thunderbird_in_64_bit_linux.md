---
title: "Thunderbird in 64 bit linux"
date: 2008-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by TouchuvGrey on 2008-02-27
I'm running 64 bit linux, ubuntu 7.04 Feisty Fawn. It came with
v 1.5.0 14pre ( 20071023 ) While it is a good version i would
prefer at least 2.0.X is one available for 64 bit linux ? If so,
do i need to do anything specisal to get and install it ?

---

### Post by nanotube on 2008-02-27
you could try getting a swiftdove build (de-branded build of thunderbird) from the swiftweasel project:
[http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)

or you could try using the ubuntuzilla installation script to install the official mozilla build (though this one would be 32bit, not a native 64bit build, it will still work fine):
[http://ubuntuzilla.sf.net](http://ubuntuzilla.sf.net)

---

### Post by utUtu on 2008-02-28
> **TouchuvGrey said:**
> I'm running 64 bit linux, ubuntu 7.04 Feisty Fawn. It came with
v 1.5.0 14pre ( 20071023 ) While it is a good version i would
prefer at least 2.0.X is one available for 64 bit linux ? If so,
do i need to do anything specisal to get and install it ?

The Gutsy version is at 2.0.0.8 if you want to upgrade.

```
Package: thunderbird
State: installed
Automatically installed: yes
Version: 2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10
```

---

### Post by TouchuvGrey on 2008-02-28
> **utUtu said:**
> The Gutsy version is at 2.0.0.8 if you want to upgrade.

```
Package: thunderbird
State: installed
Automatically installed: yes
Version: 2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10
```

      I have Feisty on my HP laptop because i've read ( in this forum )
that Gutsy has issues with HP laptops. I'm waiting for Hardy and hoping
they will be resolved there.

---

### Post by utUtu on 2008-02-28
> **TouchuvGrey said:**
> I have Feisty on my HP laptop because i've read ( in this forum )
that Gutsy has issues with HP laptops. I'm waiting for Hardy and hoping
they will be resolved there.

I don't have any problem with my pretty old HP/Compaq Presario V2000 with the very first Turion X1 chip.  The only issue was the Broadcom wireless chip because of licensing.  But you can always install the bcm43xx-fwcutter package.  No big deal.

I have 3 partitions - Xp, fresh install Gutsy, and a feisty -> upgraded to gutsy -> added  kde4. If yours is working fine for Feisty, I see no reason why it should not for Gutsy.  Just document what you've done to make it work in Feisty.  You'll need them in Gutsy, or/and Hardy.

But if you are not comfy with it then feisty..hopefully in a couple of months you'd be hardy.  :)

Cheers..!!!

---

### Post by Kilz on 2008-02-28
> **nanotube said:**
> you could try getting a swiftdove build (de-branded build of thunderbird) from the swiftweasel project:
[http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)

It looks like the Swiftdove 2.0.0.12 builds are done. I just got one in a tarball, it looks nice. If things go as they have in the past .deb's will be next.

---

