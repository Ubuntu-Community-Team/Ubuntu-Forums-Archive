---
title: "Suspend Problems - Freezes after Resume"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Crypto-138 on 2007-05-10
After suspending my computer (either to RAM or Hard disk), I find that it often acts strange. Usually it locks up, but sometimes my internet access stops working completely, and the Frequency Scaling Monitor claims that my CPU is maxed out.

When it locks up, the X-server responds to mouse input, but I cannot click on or type anything, and switching to tty1-6 won't work. 
In fact, I can't even take off numlock!

I have no Idea why this is happening, I followed every tutorial I could find:

 I have ACPI set up so that it doesn't  warm boot my NVIDIA Card,
 I have AGP = 1 In my Xorg.conf (even though I have an integrated Chip).,
 I have an ACPI script to turn off Beryl before suspending.

The problem is that when my my PC resumes, it freezes shortly afterwards, especially when clicking GNOME buttons.
Gnome-system-monitor also claims the system load average is monstrously high after resume. 

I went through my system log and attached the suspend/resumes bit to my post. I don't exactly know what it means, though.

Can someone check it for me?

---

### Post by Ken_Lewis81 on 2007-05-16
There's a number of things that don't work too well with suspend/resume.

Your syslog shows that there's issues with the hard disc drivers.  Recently Ubuntu started using libata-pata for IDE disks, which has caused issues, but your comment seems to show that the keyboard isn't being woken up properly.

Suspend/Resume doesn't work reliably for all systems just yet -- I had it working beautifully in Dapper, but 'progress' has stopped that.  I'm looking into it, and advise reading the bug reports at [Launchpad.net](Launchpad.net) and the [Ubuntu](https://wiki.ubuntu.com) for more information about your problem and how to best report the issue.

Take care.
Ken.

---

