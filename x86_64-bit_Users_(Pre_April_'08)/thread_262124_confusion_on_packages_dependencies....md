---
title: "confusion on packages dependencies..."
date: 2006-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by poncenby on 2006-09-21
hello

kernel: 2.6.15-26-amd64-k8

i have uninstalled all nvidia debs and also the linux-restricted-modules deb.
i then installed the nvidia driver downloaded from their website. it works fine.

i now wish to install compix and Xgl, but when attempting to do this apt-get complains about the linux-restricted-modules not being present and also that nvidia-kernel-common isn't installed. if I install this package my installed nvidia driver will fail.

is their a way of blacklisting certain packages which are dependent on the linux-restricted-modules package, or blacklisting the linux-restricted-modules package itself.
 
i don't see why i need to install the linux-restricted-modules package to install compix or Xgl.

would be grateful for any help...

thanks in advance

poncenby

---

### Post by a-musing amazon on 2006-09-21
The instructions for the ATI driver (if you wanted to compile your own) are

<quote>
Blacklist old fglrx module from linux-restricted-modules

As ubuntu's linux-restricted-modules package includes the fglrx module from an old driver version (8.25.18), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

sudo gedit /etc/default/linux-restricted-modules-common

Edit DISABLED_MODULES to include fglrx
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"
</quote>

this is from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I used this when I wanted to install a more recent ATI driver/kernel module than the standard one in 6.06.

I would imagine that you could use a similar technique with NVIDIA.

---

