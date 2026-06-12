---
title: "suspend problem"
date: 2008-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by makeiteasy on 2008-01-29
My desktop suspends but does not resume normally.
You have to press the power button to wake it up, it tries to get to desktop and fails than it continues by itself and restarts the system.

Any "reasonably" easy solution?

AMD64 3700+
1G RAM
Asus Mobo with Asus (Nvidia SLI V.C.512MB)
SATA HD
Dual boot with XP64

---

### Post by steveneddy on 2008-01-29
Try adding **acpi_sleep=s3_mode** to the end of the kernel line in the 

/boot/grub/menu.lst

file.

Like this.

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
[COLOR="Red"]kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dc5e4ce2-5607-4cc7-931c-9543f2caf229 ro quiet splash[/COLOR] **acpi_sleep=s3_mode**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dc5e4ce2-5607-4cc7-931c-9543f2caf229 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

and you might want to try this

```

Try changing some of the options available on /etc/default/acpi-support

On my laptop, changing the
SAVE_VBE_STATE=true

and

POST_VIDEO=true

to false did the trick. 

```

from[ this thread]("http://ubuntuforums.org/showthread.php?t=679583").

---

### Post by iggi on 2008-01-29
> **steveneddy said:**
> Try adding **acpi_sleep=s3_mode** to the end of the kernel line in the 

/boot/grub/menu.lst

file.

Like this.

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
[COLOR="Red"]kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dc5e4ce2-5607-4cc7-931c-9543f2caf229 ro quiet splash[/COLOR] **acpi_sleep=s3_mode**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dc5e4ce2-5607-4cc7-931c-9543f2caf229 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

and you might want to try this

```

Try changing some of the options available on /etc/default/acpi-support

On my laptop, changing the
SAVE_VBE_STATE=true

and

POST_VIDEO=true

to false did the trick. 

```

from[ this thread]("http://ubuntuforums.org/showthread.php?t=679583").

I can't save that after I typed that in.

---

### Post by emredmrl on 2008-01-30
because of you do not have administritive privileges to save the file

for example if you are trying to edit  file  /boot/grub/menu.lst
try
1.opening a console
2.writing the following

```
sudo gedit /boot/grub/menu.lst
```

and then save the file.
it will work.

---

### Post by emredmrl on 2008-01-30
even though i know how to edit the files makeiteasy described, i still have that suspension problem.

if it will help,my laptop is fujitsu-siemens amilo pi 1557
1 g ram
1.83 ghz intel core duo processor
with nvidia graphics adapter.

---

