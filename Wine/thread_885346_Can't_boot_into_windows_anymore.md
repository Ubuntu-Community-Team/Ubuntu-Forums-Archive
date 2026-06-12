---
title: "Can't boot into windows anymore"
date: 2008-08-10
forum: Wine
---

### Post by Heide264 on 2008-08-10
I recently gave Wine a go to make a sad attempt at running ruckus on my kubuntu OS... When I configured the settings through the system settings tab, I changed the directories (desktop, my documents, my pictures, etc) to my corresponding windows directories on my NTFS partition.

Well, after realizing it was not going to run without windows media player dependencies, I decided to just boot into windows and run it from there. Now my windows will not boot. It just comes up with a grey screen and stays there after the boot into safe mode/last confirmed settings boot options.

Any suggestions on how to reset all the registry and everything to the default values?

Thank you for any help

---

### Post by Heide264 on 2008-08-10
Bumping this up to see if anybody has any thoughts on the matter. Let me know if there is any info that would help. Just want to get my windows booting back up in case I need it for anything =(.

---

### Post by sandysandy on 2008-08-10
post output of [COLOR="Blue"]s[/COLOR][COLOR="Blue"]udo fdisk -lu[/COLOR]

---

### Post by y@w on 2008-08-10
Can you still access your data in your NTFS partition from within Ubuntu? If you mounted it read-write, it *could've* gotten corrupted. I know there's allegedly "safe" tools out there for writing to NTFS, but I'm not overly trusting of the filesystem.

---

### Post by Heide264 on 2008-08-11
my fdisk -lu...

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      417695    96229349    47905827+   7  HPFS/NTFS
/dev/sda3        96229350   117210239    10490445    5  Extended
/dev/sda5        96229413   113210054     8490321   83  Linux
/dev/sda6       113210118   117210239     2000061   82  Linux swap / Solaris


I can modify my NTFS partition through ubuntu and it auto mounts and everything still.

*EDIT* It does not auto mount anymore... but it does mount no problem manually.

Thanks for the help so far =)

---

### Post by Heide264 on 2008-08-13
No suggestions? =(

I remember it saying it was going to modify the registry, but I was assuming that was the registry wine made up... apparently not.

---

### Post by caljohnsmith on 2008-08-13
If you have your original Windows Install CD, you could do a "Windows repair", which will restore all your Windows system files back to the state of when you originally installed Windows without losing all your programs and personal data, etc. I had to do that recently on my Windows because my computer somehow crashed during a disk defrag in Windows. Nothing was lost after the repair, but then I had to download all the security updates again to get my Windows up-to-date; that can take a while if you have to download SP2, SP3, and everything else, but it is much better than reformatting and reinstalling.

---

### Post by Heide264 on 2008-08-17
Caljohn,

I never even thought of that. I am gonna go ahead and try that and let everybody know how it goes. Thanks for the suggestion.

---

