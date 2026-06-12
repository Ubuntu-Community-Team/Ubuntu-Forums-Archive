---
title: "Lock up requiring Hard Reset"
date: 2008-07-07
forum: x86 64-bit Users
---

### Post by saru411 on 2008-07-07
I'm running 8.04 AMD64 and I've noticed bugs for some time. Mainly it has been programs crashing but recently I've come across Hard Lock-ups. The keyboard and mouse both become totally unresponsive. Ctrnl + Alt + backspace= nothing..This is the reason i left Windows. Hard Lock-ups are a serious problem for me. I notice this problem most often when multitasking. Normally i have KGS(Cgoban3 go client(java based)), Rhythmbox music player, Swiftweasel(firefox variant(Intel build), and Kombilo05(python sgf search engine) running. I'm unsure where to begin with debugging this problem. I've looked at system logs but I'm unsure of what to look for or which log to look into. If you know where to begin please help me.

Thanks
David B.

---

### Post by Cappy on 2008-07-07
The relevant information would have the highest number in the log.

You should try boot parameters ```
acpi=off
```
```
noapic
```
or both, together and see if it helps.

Guide on how to edit boot parameters (/boot/grub/menu.lst):
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by PilotJLR on 2008-07-07
What is present in /var/log/messages during the time of the freeze? Next time this happens, check out /var/log/messages for a gap around the time of the crash; in other words, a gap in the timestamps where a crash could have occured. Any messages just before this time might be useful.

Also - when it does crash, can you get to a console by doing a Ctrl - Alt - F1 ?

Lastly - install openssh-server, if you haven't already. When the machine crashes can you ping it from a different computer (if you have access to another machine)? If so, can you ssh into it while the local session if frozen?

The last 2 questions are basically meant to help determine if the machine is completely crashed, or if it's just video  or X.

---

