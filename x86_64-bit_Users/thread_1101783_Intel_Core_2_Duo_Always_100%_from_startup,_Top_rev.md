---
title: "Intel Core 2 Duo: Always 100% from startup, Top reveals nothing"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by thedesburrito on 2009-03-20
My problems began when windows crashed and wouldn't let go of two partitions, one of which is on my external drive, which windows runs from but linux accesses (FF and Thunderbird files are kept there). The other is an additional drive in the module bay on my thinkpad r61.

I got to them in linux after windows crash and they were corrupted. I seemed to have fixed that problem, but I'm getting massively slow performance--unusable. One core seems to always be at around 100 percent, but even when it drops to 50, things are still very slow. I had gotten errors about applets, and so am currently reinstalling them. sudo aptitude reinstall gnome-applets has taken almost an hour.

Top reveals no greedy processes. It says 97%+ is wa, which I believe means it's waiting for I/O. Any idea how I can pinpoint the problem here? I seem to be able to read from these drives, just super slowly.

Thank you, and sorry for the length.

---

### Post by Rog-Mahal on 2009-03-20
What did you do to "fix" your corrupted drive? Does Windows boot? If it doesn't, do you get any error messages? It definitely seems like the problem is with your hdd. If it's a modular drive and is only used for storage, can you remove it and does Ubuntu act normally? Provide as much info as you can.

---

### Post by 3Miro on 2009-03-21
If you go system monitor can you identify the process that takes one core of your CPU. I have seen nautilus mess up after using Samba, it took one full core to 100% and wouldn't let go for hours. I had to kill nautilus.

---

### Post by thedesburrito on 2009-03-22
Rog-mahal: Windows does not boot, and does not give me an error message. It's just black.  I hope to get my hands on a windows CD today and hope to go at it that way.

I'm thinking more and more that the windows partition is what is causing the problem. The computer is fairly quick to boot, but gets slow afterwards. So i think the computer doesn't have much problem reading from the partition which has ubuntu, since the OS loads fairly quickly. I don't quite know why (aside from small things) ubuntu would want to access that drive.

The modular drive is out.

To "fix" my drive, I tried different ways of mounting, including force mounting a drive. I tried ntfsfix on the two drives that were having trouble, and I also did a smartctl test on the drives, although i stopped the long test because I thought it was slowing things down.

3miro: It's no specific process, both top and system monitor reveal that the biggest process (usually xorg) is using about 6 or 7 percent. I think the main hold up on the processor is waiting for I/O.

---

