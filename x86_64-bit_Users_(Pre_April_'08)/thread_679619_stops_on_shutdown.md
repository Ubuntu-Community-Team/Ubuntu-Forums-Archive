---
title: "stops on shutdown"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by archimedes1981 on 2008-01-27
i'm quite new to ubuntu , i booted it up on livecd and it hanged after booting so after a little experience i had on mandriva i booted it up with :
apm=power-off noacpi nolacpi
it worked fine so i decided to install it.
after installing i did all the updates and now it stops while doing shutdown.
a list of approximately 6 messages comes down where the last one is "libhal failed: connection closed" or similar
then the monitor seems to change resolution but just a blank screen and then it stops like that. i have to reboot manually.
i added apm=power-off noacpi nolacpi to /etc/modules but same problem kept occurring.
also at bootup there is a message but i can't stop it cos it's too fast.
1) can i see the errors somewhere?
2) can i see the boot up instead of the orange bar?
3) it never does the orange bar on shutdown now, any ideas?
thanks.

---

### Post by njparton on 2008-01-27
Can you post your hardware?

---

### Post by archimedes1981 on 2008-01-27
AMD 3200+
1Gb RAM
200Gb partitionned HD
ATI Radeon 9600 XT
ASRock motherboard 939A8X-M

---

### Post by njparton on 2008-01-27
It's most likely something to do with your motherboard so a little more detail on that would probably help

---

### Post by archimedes1981 on 2008-01-27
is there a command which i can type in terminal to get this info?
i'm quite new to linux.
thanks

---

### Post by njparton on 2008-01-28
No, your motherboard manual.  Once you know which chipset it is etc, it would be googling that plus the problems you're having to see if someone else has experienced it and found a solution.

---

### Post by archimedes1981 on 2008-01-31
can it be ALI or ULI ?
i also found out  that the livecd of the same ubuntu i installed does shutdown perfectly and so i thought that maybe it has something to do with the booting.
my configuration is set up like this.
hd0 - data (IDE primary)
hd1 - windows xp (SATA)
      - ubuntu
my grub is installed on hd0.
when i tried "grub-install hd1" it gave no errors but it didn't work.
as soon as i reconfigured the bios to the sata as boot, the grub loaded but the system wouldn't load because the partition could not be detected.-error 22
now i don't remember if there are any jumpers on my hdisks but i didn't change any.
also while booting(on hd0) an error loads exactly after grub which says something like- could not allocate region 0 of device 000000000 or something similar.
can these have anything to do with my shutdown problem?
also i want to point out that a restart is possible , although the orange bar doesn't show.
thanks,

---

### Post by archimedes1981 on 2008-05-21
noapic acpi=force apm=power_off : did the trick
however although the system shuts down completely i did not see the orange bar. How can i be sure that there is no harm done by forcing acpi ? is it safe?

---

