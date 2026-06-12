---
title: "Getting back to Win XP from Ubuntu problem.."
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Enoki on 2007-12-04
Ok.. I'm Ubuntu user for several months now.. I have it on my laptop and it's great. But now I need to uninstall/delete it, to install Win XP (don't ask why) and then I'll make it a dual boot. This is where I found a big problem. When I put my Win XP Pro Boot disc, and I restart the pc, it start like any other win xp installation, but after the line "Setup is inspecting hardware acceleration" it goes blank black screen and it doesn't continue. I have tried several copies of Win XP and it's always the same. :(:(:(:(
Any solutions ?

(btw.. sorry for my not so good english.. :):):))

---

### Post by dabl on 2007-12-04
Maybe make a GParted Live CD (download and burn ISO from [[COLOR="SeaGreen"]**here**[/COLOR]](mount -t ntfs-3g /dev/sdf1 /mnt/sdf1 -o force) and use it to reformat the hard drive, or the first partition where you have to install Windows.  Don't forget to set the "boot" flag on that partition.  :)

---

### Post by Enoki on 2007-12-05
I successfully  formated the hard drive and installed Win XP..
dabl thank you for the solution of this problem, I appreciate it. :)

---

