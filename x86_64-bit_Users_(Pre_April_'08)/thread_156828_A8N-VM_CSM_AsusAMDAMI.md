---
title: "A8N-VM CSM Asus/AMD/AMI"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ve6hba on 2006-04-07
Re: All versions of Ubuntu 5.10. None works on the Asus Board.  All hang up during installation.

Memory: 512 MB
Hd: Maxtor 256 GB SATA (2), Maxtor 40 GB USB (1)
Processor: AMD 2210 MHZ
Bios: AMI, 2.3
Video: NVidia GForce 6150
Sound: SoundMax HD Audio 0

All Version work just fine on my older Intel Board.

Can Anyone Help? Please!

---

### Post by lnxconvrt on 2006-04-10
Not sure about Breezy, I'm on Dapper.  However, to install / run Dapper on this Mobo I had to add the acpi=off kernel boot option.  Maybe try that and/or noapic / nolapic and see if it helps.

---

### Post by WelterPelter on 2006-04-11
That motherboard is buggy for linux. [Note this thread]("http://www.ubuntuforums.org/showthread.php?t=150379"). I had nothing but trouble with it, and found that Asus wasn't fixing known problems. I got rid of it and got a comparable Gigabyte board instead.

---

### Post by brimbleshoes on 2006-06-14
everything worked great for me, except LAN on Dapper, this might help...
[http://ubuntuforums.org/showthread.php?t=168022]("http://ubuntuforums.org/showthread.php?t=168022")

---

