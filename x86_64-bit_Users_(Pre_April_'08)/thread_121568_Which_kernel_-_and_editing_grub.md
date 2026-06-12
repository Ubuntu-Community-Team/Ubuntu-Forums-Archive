---
title: "Which kernel - and editing grub"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by v79 on 2006-01-25
Hi

Really this question is about editing the grub menu, as I have too many kernels listed. Ideally, all I want is the latest k8-smp-nvidia kernel, but it apparently requires k8-generic as well (if I try to remove k8-generic with synaptic it wants to remove the k8-smp-nvidia (restricted)) one too.

OK, I can live with this - except that I can't make k8-smp-nvidia the top / default option I think. In Warty, there was a program called grubconf but it's gone now...

Any suggestions?

---

### Post by Dragonbite on 2006-01-25
There is a grub config file which contains your choices and what is default.  Mine is located **/boot/grub/menu.lst**.

When you open it there is a lot of stuff automatically put in there, and then the ream "meat" of the matter near the bottom.

Near the bottom you'll find a list for each entry Grub shows up as an option.  The ordering of them starts at 0 .. 1 .. 2 .. etc.

You can either find a line that says 
```
default		0
```and change that to whatever number is the entry you want to make the default.

-- or --

Find the entry for the one you want and move it to the top of the list (which will be in position zero(0)).

---

### Post by Dragonbite on 2006-01-31
Just to keep in mind, when you install a new kernel it places 2 new menu links for it at the top (position 0 and fail-safe in position 1).

So if you redirect the **default** to another position (like 6 as I did for my Windows partition) then when you install an updated kernel you need to either increment the default by 2 or you need to remove or comment out (#) 2 lines (like the previous kernel? but that can be dangerous) so it points to the right location.

There is a way mentioned in the comment section about another way to save the default but I haven't tried it yet and I'm not in front of my machine to be able to post it.

---

### Post by NESFreak on 2006-03-10
grubconf can be downloaded [here]("http://packages.debian.org/unstable/admin/grubconf")
just do "sudo dpkg -i <the_file>.deb" from the commandline
and then run "sudo grubconf" (also in the commandline)

---

