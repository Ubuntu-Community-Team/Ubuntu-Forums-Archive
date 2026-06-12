---
title: "[i got it to run] XFI, SLAB Kernel, Restricted Drivermanager and Compiz"
date: 2007-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by devzero on 2007-10-28
Hi,

After hours of getting mad with ENVY I tried the Restricted Drivermanager Workaround and the SLAB-Kernel. I Wonder but I got it to run sound, compiz, and the restricted Drivermanager.

Now I want to tell u how i merged some howtos :D

thanks to: NullHead
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)
thanks to: James Taji (stand on the bottom)
[https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)

and others who inspred me to do this :D

okay lets begin :D

===RESTRICTED DRIVER MANAGER===

First, you should do the part with the restricted driver manager:

Note: this will only work if you have created AND installed linux-image and linux-header or linux-source packages. If you just installed an upstream kernel purely by hand, then you're sort of on your own.

First, download the source package: 

i did:
```

sudo -i
cd /usr/src/
apt-get source linux-restricted-modules-common
and
apt-get build-dep linux-restricted-modules-common 
```

after the download and unpack
i got: inux-restricted-modules-2.6.22-2.6.22.4

ok get in there with 
```
 cd inux-restricted-modules-2.6.22-2.6.22.4
```

Now open the file with your editor of your choice the file:
```
debian/rules
```

now you see the abi version below #kernel i have:
```
 abi_version        = 14
```
remenber this number or write it down, you will need it later when u compile the kernel.

the line 
Make sure that this is the abi_version from your self-built package, and also make sure that the linux-headers-2.6.20-x-flavour packages are available in your repository. In fact check that they are by issueing:
```
 sudo apt-get build-dep linux-restricted-modules-2.6.20-xxx
```
can skipped I think, because u already installed the packages and the kernel comes after that.

then I did:

Now we need to edit the "flavors" line. This is not hard. Look for a stanza starting

```
ifeq "$(DEB_HOST_ARCH)" 
```

and including your ARCH (probably i386 or amd64). within it is a line like this:

```
flavours := $(addprefix $(kernel_abi_version)-,generic 386 lowlatency) [code]

change it to this:

[code]flavours := $(addprefix $(kernel_abi_version)-,generic 386 lowlatency custom)
```

I changed the lines:
```

ati_flavours := $(addprefix $(kernel_abi_version)-,generic rt xen custom)
nv_flavours := $(addprefix $(kernel_abi_version)-,generic rt xen custom)

``` 
too, I dont know if you need to but my graphic driver works.

i added custom, because I compiled the kernel with custom after that, as NullHead told me so ;-)

then change the binary arch line, mine is a little different

the howto says:  
```
 binary-arch: install build-udebs 
I have:
binary-arch: binary-debs build-udebs
```

just exlude the build-udebs
```
 binary-arch: binary-debs # build-udebs[code]

then save and close.

open: debian/control.stub.in

look for:

[code] package: linux-restricted-modules-@@ABIVER@@-generic
```
change it to:
```
 package: linux-restricted-modules-@@ABIVER@@-custom
```

then continue with the regulary manual with:

```

fakeroot debian/rules debian/control            # this rebuilds debian/control
fakeroot debian/rules binary-indep binary-arch  # this actually builds the packages

```

it should compile and build following (in my case)
```

linux-restricted-modules-2.6.22-14-custom_2.6.22.4-14.9_amd64.deb

```

install that with dpkg -i or double-click in nautilus etc.


===KERNEL COMPILATION===

I tried the following Kernel for my experiment, to get the version close to the original konfig:

```

get http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.tar.bz2
tar xjf linux-2.6.22.tar.bz2
ln -s linux-2.6.22 linux
cd /usr/src/linux

```

its near the same as NullHeads manual, I just altered the copied .config directly

at
```

#CONFIG_SLAB is not set
i added:
CONFIG_SLAB=y
and set 
CONFIG_SLUB=n
CONFIG_SLUB_DEBUG=n

```
I got somehow more confortable with that, than grinding in the make menuconfig

and one change for the compilation:

Original:
```

make-kpkg clean
make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

```
As you need to add the ABI Version you wrote down or remembered:
in my case:
```

make-kpkg clean
make-kpkg --initrd --append-to-version=-14-custom kernel_image kernel_headers

```

then compile install it and before the reboot I needed to alter my
xorg.conf or the xserver kicks you:

```

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTX]"
        Driver          "nvidia"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "nvidia"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce 8800 GTX"
EndSection

```

change it to:

```

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTX]"
        Driver          "vesa"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "vesa"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce 8800 GTX"
EndSection

```

I think I only got the 2nd device because of envy-experiments
If you reinstall the driver with restricted drivermanager
you need to alter the 2nd column back to nvidia manualy or
compiz wont start.

The installation of the sounddriver is the same as in NullHeads thread.

Ok that looks that it really sucks, but i needed much less time to get the whole thing
work as handle with envy and non working compiz....

I hope anyome can help me to make a good how-to of this (thats why I dont write 
in the title "how-to" :D)

If I forgot somethint please tell me and I ll correct it

---

