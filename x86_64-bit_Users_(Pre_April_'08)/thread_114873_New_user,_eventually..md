---
title: "New user, eventually."
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by linix on 2006-01-09
Hiya,

         I have tryed to load ubuntu 5.10_64 on my pc and it has stopped after base building, after removing the install cd.

          Now i think it is bad sectors on the hdd, can i fix them. like scan disc in windoze, it marks the bad sectors so as not to write to them.

I have a screen full of messages with a red fail in the top right corner.

fsck failed.  Please repair manually and reboot.  Please note that the root file system is currently mounted read only.  To remount it read-write:

      # mount -n -o remount,rw /

There is more, much more.

I know i should just buy a new disc and i will but i want to learn about fundementals, so i will have a play.

cheers nick

---

### Post by FluffyElmo on 2006-01-09
Do you have a prompt? Try typing *fsck* and enter or *fsck -a* to automatically say yes to all prompts.

Oops, just noticed that it's mounted read-only. You can try issuing the command in the error. But other than that?

---

### Post by linix on 2006-01-09
Hiya,
         Yes prompt is:
root@(none);~#

The squiggle is at the top though, not in the middle

i typed fsck to see what would happen and it come back with

fsck 1.38 (30-june-2005)
e2fsck 1.38 (30-june-2005)
/dev/hda1 is mounted.

WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue (y/n) ? yes

/: recovering journal
fsck.ext3: Bad magic number in super-bloock while trying to re-open /e2fsck:  io manager magic bad !
root@(none):~# _

Thanks for reply, sorry about delay.

There is nothing else on the disc other than the attempted install

Nick

---

### Post by linix on 2006-01-09
Not sure what this means, incedently i had already carried out this action before posting, it does not matter if it mucks up as it is a new machine i built over christmas, i just woundered if there is a way to use this hdd as i cannot get another replacement for a while, it was out of an old duron 700 that died on me, and the floppy and atx case all other is new parts.

Oops, just noticed that it's mounted read-only. You can try issuing the command in the error.[/QUOTE]

---

### Post by FluffyElmo on 2006-01-09
Try running fsck from the install disk. Boot from the install cd, type "rescue" from the prompt and then *fsck /dev/hda1* at the prompt.

---

### Post by linix on 2006-01-09
OK,

    I have rebooted and am in rescue mode and it wants to know this;

enter a device you wish to mount as your root file system.

After this message, if the file system was mounted succesfully, you will be given a shell with that fils system on "/".  if you need any other file systems (such as a separate "/usr"), you will have to mount those yourself.

When you exit this shell, the system will reboot.

Device to mount as root file system:

/dev/discs/disc0/part1
/dev/discs/disc0/part2
/dev/discs/disc0/part5

Im guessing they are the partisions?

I dont know which one has the damaged sectors

---

### Post by FluffyElmo on 2006-01-09
Did you choose a seperate /boot partition during setup? In that case I think /dev/hda2 would be the partition to fsck. Try the second one, alternately you could hit Esc at boot (from the hd) and choose rescue mode?

---

### Post by linix on 2006-01-09
I just allowed it the std install, it is the downloaded iso i burned to disc,

I tryed all three and none would work so i chose back to the install list

im in ash now trying to mount dev/hda3 i was thinking this would be the dvd drive and i could try to repair the hdd from the install cd but it says it cant find /dev/hda3 in /etc/fstab

---

### Post by linix on 2006-01-09
Hiya,

   Thinking back to the install there were 4 choices i chose the 2nd one, i figured the first option was for duel booting and the 3rd had the same as the second except for LVM whem i serched this it seemed to be somthing for servers.  the choice was somthing like ,  format entire drive....... can not recall any more, should i try another reboot from here and when should i hit esc

---

### Post by linix on 2006-01-09
I have rebooted and am back at the root device choice, selecting the2nd choice, i get this message,

An error occured while mounting the device you entered for your root file system () on /target.

Please check the error log on the third console or /var/log/messages for more information.  

The chioces are continue or go back

---

### Post by linix on 2006-01-09
Hiya,

          Continue just goes back to the three choices, and in fact they all do the exact same thing,

However go back is more fun, it goes to the installer list, selecting shell takes me to ash (shell) i just chose cdrom integrity and that is good i can type out the list, there is no obvious choice for the hdd test

Nick

---

### Post by linix on 2006-01-10
Hiya,

         Thankyou FluffyElmo for trying to halp me do the imposible, i went and bought a new maxtor 80g today and ubuntu installed no problem, I have put the old hdd as slave, ill use it for LP to CD recording hopfully if i can repair it but i'm just reading now, Not sure what all the talk about Firefox1.07,flash and 64bit is about as it came in my download and i'm using it now. I'm off to the beginers forum.

Thanks again for your efforts.

      Nick

---

