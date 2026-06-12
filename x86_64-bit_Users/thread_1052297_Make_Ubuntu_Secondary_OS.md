---
title: "Make Ubuntu Secondary OS"
date: 2009-01-27
forum: x86 64-bit Users
---

### Post by nukenate on 2009-01-27
Ubuntu is great, and I use it quite a bit, but I want to change my main disk partition into my primary OS, the one that I'm automatically booted into.

Windows 7 is just better for me. Sorry folks, gotta have my Games and Zune!

And be able to have sound....
Still can't figure that out.

Anyhow, I tried using the BIOS but all I could do was change the boot order from external things like from a CD/flash drive.

Oh, and I'm using Ubuntu now, for what it's worth.

---

### Post by jeffjanzen on 2009-01-27
edit /boot/grub/menu.lst to make windows your default, and disable hiddenmenu. hope that helps!

post again if you need more details, of course.

---

### Post by nukenate on 2009-01-27
At first I thought that was something I was supposed to enter into the terminal, but after one try I figured out that it was a file location.

I opened 'er up and... Gulp....

Instant intimidation.

I'm terrified to do anything lest I ruin my computer. I believe this is the part I'm meant to edit.

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		2502cdf4-770d-4fe6-870e-4ec4954edf3f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2502cdf4-770d-4fe6-870e-4ec4954edf3f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		2502cdf4-770d-4fe6-870e-4ec4954edf3f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2502cdf4-770d-4fe6-870e-4ec4954edf3f ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2502cdf4-770d-4fe6-870e-4ec4954edf3f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2502cdf4-770d-4fe6-870e-4ec4954edf3f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2502cdf4-770d-4fe6-870e-4ec4954edf3f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2502cdf4-770d-4fe6-870e-4ec4954edf3f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2502cdf4-770d-4fe6-870e-4ec4954edf3f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

The only thing I feel safe enough to be willing to try without asking would be changing the name of the top "Windows" title to "Windows 7 Beta 64bit"

---

### Post by Tubes6al4v on 2009-01-28
At the top of that file there should be a lot of commented out text (i.e. with the # in front) and something that says "default  1" I would check what it actually is, but I am work and DSL doesn't have the same I think... Nope, it has isolinux. Anyway, just change that 1 to 7 or whatever the system is that you want to boot (just count). That will make it the default. So you can still choose Ubuntu if you want.

Grub is pretty easy once you get used to it. You can change the title of the OS to whatever you want (i.e. restrictive software with a lot of security holes)

---

### Post by cjazz on 2009-01-28
> **Tubes6al4v said:**
> At the top of that file there should be a lot of commented out text (i.e. with the # in front) and something that says "default  1" I would check what it actually is, but I am work and DSL doesn't have the same I think... Nope, it has isolinux. Anyway, just change that 1 to 7 or whatever the system is that you want to boot (just count). That will make it the default. So you can still choose Ubuntu if you want.

Grub is pretty easy once you get used to it. You can change the title of the OS to whatever you want (i.e. restrictive software with a lot of security holes)

All is accurate here, except, if I'm not mistaken, I believe the counting begins with 0. In other words, if Windows is the seventh item, the line would say "default 6."

---

### Post by drs305 on 2009-01-28
Install StartUp-Manager:
```
sudo apt-get update 
sudo apt-get install startupmanager
```

Run Startup-Manager:
System, Administration, StartUp-Manager

Select Boot Options, Default operating system, Choose windows.

For more information on StartUp-Manager and editing menu.lst:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by nukenate on 2009-01-28
God damn, you walking, wonderful, wonderful, code book.

Did you just know that off the top of your head?

Thanks, I wanted to try editing the file yet I am not yet confident enough to do so.

---

