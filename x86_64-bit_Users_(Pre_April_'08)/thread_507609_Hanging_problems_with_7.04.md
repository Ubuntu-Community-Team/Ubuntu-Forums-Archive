---
title: "Hanging problems with 7.04"
date: 2007-07-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by GumbyX on 2007-07-23
I seem to be having a locking-up/hanging problem with the 64-bit version of 7.04. I will be doing something, and suddenly, I cannot click anything on the screen, but I can still move my mouse. It happens are random times and can be days in-between problems. I have researched it a bit, and it seems that people who are running my chipset seem to have a problem like this. (I am running a ADM dual core 3300 I believe). Has anyone else had a problem like this? If so, is there a way to stop this from happening? Thanks ahead of time.

---

### Post by MrHippocampus on 2007-07-23
You might be suffering from a problem which only occurs on 64-bit and is to do with the system hanging on IO with a hard drive. There is a large thread about this on the gentoo forums [here]("http://forums.gentoo.org/viewtopic-t-482731-postdays-0-postorder-asc-start-475.html").

It can be one of a number of things, but one thing you can try is to execute the following command(s) as root

```

echo deadline > /sys/block/sda/queue/scheduler
echo deadline > /sys/block/sdb/queue/scheduler 
etc....

```

this needs to be done for all of the sd* devices in /sys/block/, I have the same problem on my gentoo install and this seems to help. Just run the commands and then use your system as normal and see if it is any better, if it is youll need to place the commands in a script which runs when ubuntu starts (cant quite remember where this is located off the top of my head).

---

### Post by Cappy on 2007-07-23
I had this same problem but they fixed it a few weeks ago so make sure you have all your updates installed. It is possible that you have a different problem than [https://bugs.launchpad.net/bugs/41301](https://bugs.launchpad.net/bugs/41301)

You should still try boot params ```
noapic acpi=off
``` and see if that fixes it. You can find out how to add it your /boot/grub/menu.lst here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by GumbyX on 2007-08-05
> **Cappy said:**
> I had this same problem but they fixed it a few weeks ago so make sure you have all your updates installed. It is possible that you have a different problem than [https://bugs.launchpad.net/bugs/41301](https://bugs.launchpad.net/bugs/41301)

You should still try boot params ```
noapic acpi=off
``` and see if that fixes it. You can find out how to add it your /boot/grub/menu.lst here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Sadly this cased my USB keyboard to no longer work. :(
I also got a lot of errors on boot. After removing it, I only got one:
```
MP-BIOS Bug 8254
```

Anyone know what this is or where I can research it (other then a random google search)?

Edit: I have looking in the forums for solutions, but the only one i found (placing just apci=off as a boot paramater) caused the system to just hang right after the same error message came up.

---

### Post by GumbyX on 2007-08-06
Um.. I don't want to get in trouble for double-posting (if I am not supposed to), but just trying to get this up somewhere people can see it. Anyone got any ideas?

---

