---
title: "Hibernate in Ubuntu 9.04 64bit doesnt work?"
date: 2009-07-18
forum: x86 64-bit Users
---

### Post by brandysnap on 2009-07-18
I clicked Hibernate to put my computer to bed for the night but all that happened was the screen went black and a flashing white cursor appeared in the top left corner of the screen.

no disk activity, no nothing and it stayed like that until i switched the machine off at the power.

Whats the problem?

ubuntu x86 amd 64
amd x2 64 4400
4gb ddr2
radeon 3870
audigy 2zs

---

### Post by bford16 on 2009-07-18
> **brandysnap said:**
> I clicked Hibernate to put my computer to bed for the night but all that happened was the screen went black and a flashing white cursor appeared in the top left corner of the screen.

no disk activity, no nothing and it stayed like that until i switched the machine off at the power.

Whats the problem?

ubuntu x86 amd 64
amd x2 64 4400
4gb ddr2
radeon 3870
audigy 2zs

I see that you have a Radeon card.  You might try editing /etc/default/acpi-support, and setting RADEON LIGHT to 'TRUE.'  You will find the option around line 107 in the file.  You must be root to make this change.

---

### Post by darco on 2009-07-18
any tips for Nvidia users :)

darco

---

### Post by brandysnap on 2009-07-19
> **bford16 said:**
> I see that you have a Radeon card.  You might try editing /etc/default/acpi-support, and setting RADEON LIGHT to 'TRUE.'  You will find the option around line 107 in the file.  You must be root to make this change.


thanks for that, will give it a tray later.

just to add, when i switched on my computer this morning ubuntu said it was waking up but then all i got was a black screen with a white cursor (which i could move around the screen) and some corrupt graphics where the top and bottom bars would be.

a further reset got everything back to normal, but it put me off trying hibernate again. :/

---

