---
title: "qemu won't work"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuntubrian on 2006-04-15
Has anyone gotten qemu to actually work on ppc? If so, how?
Thanks

---

### Post by hentaidan on 2006-04-15
By installing from the repos'.

What specific problems are you having?

---

### Post by ubuntubrian on 2006-04-17
my desktop crashes. I think it's perhaps due to having MacOnLinux installed also as I had configured /dev/net/tun for MOL and that's the error that I get when I point qemu at an image I get: "warning: could not open either /dev/net/tun: no virtual network found" and then the crash. It doesn't matter what image I try or an actual disk, even Dapper live cd.

---

### Post by hentaidan on 2006-04-18
Try appending "-net none" to the command to launch qemu?

i.e. qemu -hda image.img -boot c -m 256 -net none

I gave up with /dev/net/tun' and use the default (no config) settings :rolleyes: 

> -net none
Indicate that no network devices should be configured. It is used to override the default configuration (`-net nic -net user') which is activated if no `-net' options are provided.

---

### Post by ubuntubrian on 2006-04-18
Here's my attemtp to run the puppyLinux live cd image:
qemu puppy-1.0.8r1-mozilla.iso -net none
qemu: invalid option -- '-net'

---

### Post by ubuntubrian on 2006-04-18
I also tried "-n none" append and no message, just a desktop crash.

---

### Post by hentaidan on 2006-04-18
[QUOTE=ubuntubrian]I also tried "-n none" append and no message, just a desktop crash.[/QUOTE]

I take it your using Breezy? There was a big overhaul between the qemu in Breezy and the 0.8.0 version in Dapper, and I guess "--net none" was one of them.

Have you tried compiling the newest version from [http://fabrice.bellard.free.fr/qemu/]("http://fabrice.bellard.free.fr/qemu/")? Or undo the changes from installing MoL? Thats about all I can suggest :confused:

---

### Post by ubuntubrian on 2006-04-18
thanks-I'll try the compile route.

---

### Post by ubuntubrian on 2006-04-18
I downloaded the source code and tried compiling. At "make":

dyngen: blr expected at the end of op_bsfw_T0_cc
make[1]: *** [op.h] Error 1
make[1]: Leaving directory `/home/brianokeefe/Desktop/qemu-0.8.0/i386-user'
make: *** [all] Error 1
 
I am, of course, using a ppc mac.

---

### Post by ubuntubrian on 2006-04-18
I downloaded an .rpm file from Fedora for ppc of the latest version, installed it with dpkg and the same thing-desktop crashes.
Oh well!

---

### Post by hentaidan on 2006-04-19
File a bug? :rolleyes:

---

