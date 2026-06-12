---
title: "help partitioning drive"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thmanx on 2005-10-15
i am going to partition my harddrive 25gb for OSX and 15 for Linux

what format should i format the Linux part, "Free Space" or "Unix filesystem"

---

### Post by ubonetu on 2005-10-16
If you can, you need ext3 journaling filesystem for the linux and you'll need to make space for swap which is two times your RAM.  It should be formatted as Unix/Linux Swap.

---

### Post by Joe_lurker on 2005-10-16
Leave it as "Free Space".  During the Ununtu install you will use this free space for at least 2 additional partitions; one for linux system and one for swap space.  The  default filesystem is ext3.  You can change that duiring the install but ext3 is fine.
Joe

---

### Post by gpogo on 2005-10-16
Here's how I did it(a very easy way).

FIrst on the OS X installer disk partition you drive into two parts.  Make the second(or bottom partition) the OS X one and format it how you like.

Next in the ubuntu installer at the point where it wants you to partition do manual and set the partition that is not your OS X partition(the other big partition) to free space.  Write the changes, it will then warn you you haven't set a root filesystem and such continue anyways and then it sort of forces you back to the partitioner, at this point you will see it wrote that the space is free space, now select guided partitioning and select largest free space...maybe that doesn't sound so easy but it's how I did it...

---

