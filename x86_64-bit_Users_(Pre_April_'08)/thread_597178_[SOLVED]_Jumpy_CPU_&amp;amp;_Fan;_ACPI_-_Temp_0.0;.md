---
title: "[SOLVED] Jumpy CPU &amp;amp; Fan; ACPI - Temp 0.0; Systems - Temp 51"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by alphaa1 on 2007-10-30
*7.10 (Gutsy Gibbon) 64 bit*

My CPU usage increases when the consumption increases e.g. opening applications or running video but the_ irritating_ factor is my fan is keeping in sync i.e. if there is a spike in CPU usage for 2 seconds (i.e. opening applications) my fan switches on for 2 seconds. Also I found that if I watch a video my cpu keeps running on a higher gear close to 80% and sometimes 100% capacity and hence the cooling fan.

My googling led me to [http://ubuntuforums.org/showthread.php?t=53094]](http://ubuntuforums.org/showthread.php?t=53094]). For AMD Turion 2.2 GH single core passing a parameter no_timer_check in Grub solves the issue for older kernels. But in my case i have Gutsy latest kernel and that _solution didnt help_.

Doing further research i found that systems [Systems - Temp 51 [terminal command systems]] is detecting my CPU temperature correctly but ACPI is not detecting my CPU temperature/ Speed steps correctly [ACPI - Temp 0.0 [terminal command acpi -t]].

I think wrong ACPI reading may be triggering the Fan on and off. :(.Any Thoughts on this and how to fix this???:confused::confused::confused:

FYI: I have a dual boot system and under windows XP the fan and cpu meter work perfectly.

My configuration:

DV 5000z with AMD Radeon 200m 2.2 GH Turion Single core.

---

### Post by alphaa1 on 2007-11-04
Yet to find a solution as to why acpi is reporting CPU temperature as 0.0

but,
 
I found a workaround for the Jumpy CPU and fan issue. Installed the applet EMIFrequency  and set  the power profile as powersaving. After that I have watched a movie without the fan on for the whole 2 hours.:)

---

### Post by DeepNoob on 2007-11-05
"Installed the applet EMIFrequency..."

Where did you find this applet?  I searched for the string "EMIFrequency" in Synaptic and googled it but came up blank.

Thanks.

---

### Post by alphaa1 on 2007-11-05
Well i should have been specific... my bad...

it goes under the name emifreq-applet... More information at this link... [http://packages.ubuntu.com/gutsy/gnome/emifreq-applet](http://packages.ubuntu.com/gutsy/gnome/emifreq-applet) ... In synaptics you should be able to locate by using the keyword emifreq...

Further to my research as to why ACPI is reporting the thermal readings as 0.0 I found this link [http://forum.notebookreview.com/showthread.php?t=39153](http://forum.notebookreview.com/showthread.php?t=39153). So, I guess the Bios is not supporting the ACPI temperature readout. (I have got a Turion ML-40 & I have never upgraded the bios till date... so need to check out on it...):mad:

---

### Post by DeepNoob on 2007-11-05
Thank you.

I installed the applet, but I'm using KDE and it didn't show up in any of the menus.  I had to run it at the prompt, but all that did was launch a daemon.  Are you using Gnome, and did you get some kind of a front end to the applet?

I have a Turion ML-32 and did try the no_timer_check "trick".  But it looks like the line in menu.lst that reads:

"# kopt=root=/dev/hda2 ro console=tty0 no_timer_check"

is a commented-out example.  I added it to the kernel line, but after I run sudo update-grub it disappears.  So I'm kind of at a loss here.

By the way, I updated my BIOS about three weeks ago, from HP, so I don't think that's an issue for me.

---

### Post by alphaa1 on 2007-11-07
Yup... i am using Gnome... the best and easiest way to view and control the applet is to add it to one of the tool bars in Gnome... Though i am not that familiar with KDE... i guess the process should be the same... 

Once added to the toolbar you can click on it to set the power settings...

BTW what does your acpi -t show??

I need to check on the missing no_timer_check parameter... let me get home and check it... P.S: it is only required if your system clock runs twice as fast as the normal clocks... + this bug was fixed in the subsequent kernel releases... so for gusty we shouldnt require the no_timer_check in grub...

---

### Post by DeepNoob on 2007-11-07
acpi -t shows 0.0 degrees C.

The procedure he gave for no_timer_check works...once update-grub is run it puts no_timer_check in the kernel parameters.  The same thing as putting it in manually.  But it doesn't do anything about the fan.

I'll have to see about adding emfreq to the menus, but all I could find was the daemon, not the applet.  Oh well.

---

