---
title: "[SOLVED] Trouble Installing the JDK 6u7"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by Bitslinger on 2008-08-24
Hey all,

I'm an inexperienced user with Linux.  I'm trying to install Sun Microsystem's Java Development Kit 6 update 7 but am having some problems.

I enter

```
./jdk-6u7-linux-x64.bin
```

And it brings up a license agreement.  I type yes and then am met with

```
Unpacking...
./jdk-6u7-linux-x64.bin: 450: cannot create install.sfx.11000: Permission denied
Checksumming...
/usr/bin/sum: install.sfx.11000: No such file or directory
[: 477: 54493: unexpected operator
[: 477: 69969: unexpected operator
chmod: cannot access `install.sfx.11000': No such file or directory
Extracting...
./jdk-6u7-linux-x64.bin: 480: ./install.sfx.11000: not found
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.
```

There doesn't seem to be any troubleshooting section on the page that I got this from, however:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter)

Any help would be appreciated.  Thanks.

---

### Post by Yellow Pasque on 2008-08-24
put sudo in front of the ./ command

---

### Post by mrsteveman1 on 2008-08-24
If you are running it from a directory you have ownership of it should work fine.

---

### Post by Bitslinger on 2008-08-24
Executing the bin as the super-user worked.  Thanks!

---

