---
title: "Error during install: unknown user 'root'"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stephen-I-M on 2006-06-03
I'm getting the following error when in the base-install portion of the install:

Running /usr/lib/base-installer.d/netcfg
debootstrap: dpkg: syntax error: unknown user 'root' in statoverride file

Any idea what this is about?

Stephen

---

### Post by Stephen-I-M on 2006-06-03
Here is some more information:

Warning: Failure trying to run: chroot /target dpkg --force-depends --install var/cache/apt/archives/base-files_3.1.9ubuntu7_amd64.deb  var/cache/apt/archives/base-passwd_3.5.11_amd64.deb

Stephen

---

### Post by Stephen-I-M on 2006-06-03
I never figured how to get around this one so I just installed the 32 bit version. That install went without a hitch.

Stephen

---

### Post by JoWilly on 2006-06-03
Strange... have you checked your media for errors (this is the most common cause) ?

---

### Post by Stephen-I-M on 2006-06-03
How can I md5sum a CD again? I'll take a look.

Stephen

---

### Post by henriquemaia on 2006-06-04
[quote=Stephen-I-M]How can I md5sum a CD again? I'll take a look.

Stephen[/quote]

Open a terminal and type:

```
md5sum /path/to/your/iso/file
```

It will compute the md5 check sum.

---

### Post by Stephen-I-M on 2006-06-04
The iso has the correct md5sum, but I thought you could somehow do the same on the burned CD.

Stephen

---

### Post by henriquemaia on 2006-06-04
[quote=Stephen-I-M]The iso has the correct md5sum, but I thought you could somehow do the same on the burned CD.

Stephen[/quote]

There is an option on the alternate instalation CD to verify the CD for defects. But I had a badly recorded iso burnt, did that verification and got an ok on that, and even so the CD didn't work.

My error was on the GRUB installation. I tried twice and then figured out this could be from the iso not being correctly recorded. Burnt the CD again and worked like a charm.

---

