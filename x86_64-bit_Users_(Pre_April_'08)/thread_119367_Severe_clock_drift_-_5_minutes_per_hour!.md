---
title: "Severe clock drift - 5 minutes per hour!"
date: 2006-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by fmalan on 2006-01-19
Hi

I am new to using Linux, and running Breezy on an AMD Athlon64 X2 4400+ at work. Not the best choice, as I am having all sorts of problems - mostly related to lack of support for AMD64. But mostly I can at least get some work done.

I noticed that the system time gains about 5 minutes per hour. This is unacceptable, and I am sure due to some kind of bug. I can manually sync with ntp servers, but automatic ntp slaving does not work due to this extreme drift.

Read a bit on news groups, and came across someone who mentioned that he had a similar problem which was solved by setting the kernel boot options with 
"noapic" and "acpi=off"

[http://kerneltrap.org/node/4872#comment-129554](http://kerneltrap.org/node/4872#comment-129554))

What are these, and how to I set these parameters?

Francois

---

### Post by lolcese on 2006-01-19
Enter
[FONT="Courier New"]sudo gedit /boot/grub/menu.lst
[/FONT]
Then, look into the file for a line like:

[FONT="Courier New"]kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash [/FONT]

Add at the end of the line the desired parameters [FONT="Courier New"]noapic acpi=off[/FONT]

I had a simmilar problem with the clock, and [FONT="Courier New"]noapic[/FONT] solved it.

---

### Post by gunksta on 2006-01-19
[QUOTE=fmalan]Hi

I am new to using Linux, and running Breezy on an AMD Athlon64 X2 4400+ at work. Not the best choice, as I am having all sorts of problems - mostly related to lack of support for AMD64. But mostly I can at least get some work done.

I noticed that the system time gains about 5 minutes per hour. This is unacceptable, and I am sure due to some kind of bug. I can manually sync with ntp servers, but automatic ntp slaving does not work due to this extreme drift.

Read a bit on news groups, and came across someone who mentioned that he had a similar problem which was solved by setting the kernel boot options with 
"noapic" and "acpi=off"

[http://kerneltrap.org/node/4872#comment-129554](http://kerneltrap.org/node/4872#comment-129554))

What are these, and how to I set these parameters?

Francois[/QUOTE]


No problem Francois.  This is common on some 64 bit machines and can take a little while to figure it out.  First, check to make sure you have the newest kernel available.  This is important for 2 reasons.

1)  Newer kernels are getting better about this, and your problem might just resolve itself by installing a new kernel.

2) I'm going to tell you how to adjust your kernel boot parameters.  But, Ubuntu's tools don't know you did this, so you'll have to redo this manually EVERY TIME you install a new kernel.  Fortunately, that doesn't happen too often.

OK,  here we go.  Open up your favorite terminal program.  Since I don't know how comfortable you are with the CLI, I'll do this step by step.  If you are comfortable with the CLI, I do not mean to offend.


[COLOR="Red"]sudo nano /boot/grub/menu.lst[/COLOR]


Scroll down past everything that starts with #

You are looking for something that looks like this:

[COLOR="Red"]    title           Ubuntu, kernel 2.6.12-10-amd64-generic Default
    root            (hd0,1)
    kernel          /boot/vmlinuz root=/dev/hda2 ro vga=771 quiet splash
    initrd          /boot/initrd.img
    savedefault
    boot[/COLOR]

Find the title with the biggest number.  Like 2.6.14 is bigger than 2.6.12 or something.  I'm pretty sure .12 is the biggest though right now.

go to the line that is labeled kernel.  That's where the action is.  at the end of the line add whatever parameters you want.

I would start by adding
[COLOR="Red"]
no_timer_check[/COLOR]

to the end of the kernel line.

Other things you could try are:
[COLOR="Red"]noapic 
acpi=off
clock=pmtmr notsc[/COLOR]

I've also seen a posting where they said that noapic AND acpi=off work better together for some weird reason.  If you want to add more than one argument don't use commas or and.  Make it look like:

kernel argument....[COLOR="Red"]noapic acpi=off[/COLOR]

You could also try a google search with a string like "HP model# linux" to see if there is anyone out there who has written a how-to for your machine.  When I got this laptop I found a Gentoo user who had written a write-up for my computer.  Almost everything that he did to his worked for me too.

Obviously, since I can't tell you exactly what is goin to resolve your issue, this could take a few reboots.  A fast way to experiment is to pass the kernel a modified argument at boot time.  I can't remember the exact steps, but I know it's pretty easy.  When your computer boots, you get a black screen for a few seconds with a listing of all the kernels / operating systems on your computer.  Hit the up or down key NOW! to stop the countdown boot timer.  Read Grub's instructions for modfying your boot command.  There's a way to edit that kernel line from Grub but your changes go away when you reset.  It's a one time only deal.  But, it could be a nice way to experiment until you find the combination that works for you.

I hope this has helped.  If you need more of a hand with this reply here or try dropping me a line on IM @ gnxorbust

--andy

---

### Post by fmalan on 2006-01-20
Thanks a lot for your detailed reply! I'll give these proposed fixes a try. Will report back soon...

---

### Post by stimpie on 2006-01-20
Adding "notsc" as a boot option solved this for me.

---

### Post by fmalan on 2006-01-27
Okay, so I didn't report back so soon after all. The *no_timer_check* option did fix this drift - or so I thought...

It's been a week now, and I notice that the clock  is drifting again, and at the same rate, even though the  *no_timer_check* is still enabled. I will give some of the other fixes a   try...

---

