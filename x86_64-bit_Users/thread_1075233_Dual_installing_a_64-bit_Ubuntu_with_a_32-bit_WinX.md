---
title: "Dual installing a 64-bit Ubuntu with a 32-bit WinXp"
date: 2009-02-20
forum: x86 64-bit Users
---

### Post by Heavenly Bicorn on 2009-02-20
So I've been mucking around online for the past 3 days and have been trying to figure out why Ubuntu 7.10 won't load for me but WinXP will. 

I currently have both loaded on my computer but have noticed that winXP is a 32-bit system, and not a 64-bit, but Ubuntu 7.10 is. Is it possible that since I have a 32-bit os loaded that the 64-bit os is not reading my computer as 64-bit capable?

I'm thinking that's the issue...

---

### Post by kuja on 2009-02-20
And I assume Ubuntu was working before? Do you get any sort of error messages? If you installed WinXP afterwards, I would assume you're probably having an issue with the bootloader. If that's the case [this would help](https://help.ubuntu.com/community/GrubHowto)

Seeing as the OS's are **completely separate** I think what you're thinking highly unlikely. (with the vague semi-exception being wubi, I suppose)

Also, small note, while Ubuntu 7.10 is still supported for another couple months, it is kind of an old release, may want to consider upgrading soon :)

---

### Post by jespdj on 2009-02-20
> **Heavenly Bicorn said:**
>  Is it possible that since I have a 32-bit os loaded that the 64-bit os is not reading my computer as 64-bit capable?

I'm thinking that's the issue...
No, that's not the problem. It doesn't matter if Windows or any other OS that you have installed is 32-bit - if your processor is 64-bit capable, you should be able to install 64-bit Ubuntu alongside 32-bit Windows. I have 32-bit Vista and 64-bit Ubuntu on my laptop.

What processor does your computer have, an Intel? Lookup the model in [Intel's processor spec finder](http://processorfinder.intel.com/) and see if "EM64T" is mentioned as a feature. If it isn't, then your processor is 32-bit only.

---

### Post by pickboy87 on 2009-02-20
Would it even let you install a 64 bit OS if your processor isn't 64 bit? I know XP 64 won't let you.

---

### Post by Heavenly Bicorn on 2009-02-20
Okay, nvm. That was a dumb question, but that's what probably happens after one's been on their comp for the past 6 hours or so trying to figure out what's wrong/troubleshooting. ](*,)

Anyway, it's probably the boot loader in all honesty. I'm sure the MBR code or whatever was overwritten by Windows, hence Grub can't load.

@Kuja: Yea, you're right, thus I will get IIbex and try later when I'm not so worn out and hope it will work then. :o

@Pickboy87: No, you can't install a 64-bit OS if your processor isn't 64-bit. You'll get an error that will tell you straight up (remarkably! :roll:) that your processor isn't a 64-bit.

@Jespdj: Look above.

Thanks for replying, everyone. I'll see how IIbex goes and maybe I'll be back with the SAME PROBLEM (Fft, I hope not)! xD

---

