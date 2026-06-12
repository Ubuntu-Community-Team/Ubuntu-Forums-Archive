---
title: "troubled"
date: 2007-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by nate_nightroad on 2007-03-15
i just download the ubuntu 6.10 amd64 edition and i'm using intel pentium D 820 and when i start to install ubuntu, at the boot screen there are plenty of selection and i entered 'install in text mode' and then everythings hang. i tried 'install in oem', same thing happend!

so any advice??

thanks everyone for the time and have a nice day

---

### Post by John.Michael.Kane on 2007-03-15
More info is needed.

full system spec's.
Any errors shown on screen.
Is the install being done with the alternate cd or live desktop cd.

---

### Post by nate_nightroad on 2007-03-15
my spec is intel pentium d 820
msi 945P Neo
80SATA
msi 6600gt
sony dvdrw
samsung combo drive

yeah i got the alternate cd...

thanks

---

### Post by kleeman on 2007-03-15
What is the last text line before the hang?
Does any other distro work? Try knoppix....

---

### Post by nate_nightroad on 2007-03-15
i think the last text came up was 'loading kernal.....'

i tried linspire and freespire and they can install fine....

please advice and thank you for the time

---

### Post by John.Michael.Kane on 2007-03-15
have you tried downloading the alternate iso?

Or

Reburning the iso you have a slower speed.

Did you check the md5sum on the iso you downloaded?

---

### Post by nate_nightroad on 2007-03-15
yeah i download the alternate iso version

yeah i check the md5sum too...

pls advice...

---

### Post by kleeman on 2007-03-16
When you get to the first screen instead of pressing enter press f1 instead. This will give you help and a whole bunch of options to try passing to the kernel. It may be that one of these will work and you can get it to boot. Given that other distros work this or a crapped out cd seems most likely here. 

Unfortunately I have no concrete tips on which options work best but I have seen a lot of people passing acpi=off with success.....

Edit: Notice that on the first page there is an option for checking the cd for defects. Give that a try to rule out a borked cd

---

