---
title: "Problems with GPartEd in Ubuntu 8.04 64 Bit"
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by -kg- on 2008-12-27
I just did multiple searches and couldn't find anything on this problem.

I run Ubuntu (Gnome) 8.04 on both my laptop (32 bit) and my desktop (64 bit).  I have GPartEd installed on both.

While GPartEd runs fine on my laptop (2 physical hard drives), if I try to run it on my desktop (3 Internal and 1 External...I haven't tried it with the External disconnected) the computer will slow down almost to a stop...and I mean almost to a **_stop_**!

I launch it and it starts checking the hard drives as normal, but mousing actions are slow to nearly non-existant.  You click on anything, and there is a *huge* time delay before the action is taken.  Even when you finally get GPartEd to close, this slowness continues until finally you're able to reboot, then upon reboot the system is back to normal.

How large of a delayed action is based on how long you let it go.  If I realize that I just launched it accidentally, I can usually get it to close, then reboot (eventually).  But the first few times I was waiting for it to finish and display the screen, and it froze up so badly that I had to hard reboot it.

It's not really *that* great of problem, since any Live CD Partition Editor works as normal, but there are times it would be nice to do partitioning operations without having to reboot to a Live CD to do them (like the screenshots I needed to take of GPartEd operations).

Any ideas on what might be causing it?  Don't ask me to post any command outputs while it's running...I'd never be able to get them because of the freeze-up.

Irritating, to say the least!

---

### Post by cariboo on 2008-12-27
You may have a misconfiguration with gparted. I would suggest reinstalling gparted to see if that makes any difference. In a terminal type:

```
sudo apt-get reinstall gparted
```

One other suggestion start top first before starting gparted and see if there is anything that sticks out.

Jim

---

### Post by -kg- on 2008-12-27
Well, seemingly, it must have been the external drive, though why that would be I have no idea.  It could also have been BOINC, but since I have that running on the laptop as well, I wouldn't think so.

I disconnected the external drive on reboot and suspended BOINC projects, then launched GPartEd.  While I did have a little bit of hesitation (small freezes) it came up and, when I closed it, the system acted normally.

This still puzzles me, though.  GPartEd comes up almost instantly on my laptop with no hesitations.  On the desktop, it scans for *several* seconds (more like a minute or greater) (AND unless I have the external drive connected) and has small freezes until it comes up with my drives displayed in the window.  Without the external drive, I have three hard drives on my desktop, and two on my laptop.

I guess my next experiment needs to be connecting the external drive to the laptop and see if it slows *that* down.

> You may have a misconfiguration with gparted. I would suggest reinstalling gparted to see if that makes any difference. In a terminal type:

I've already tried that, though through Synaptics.  I uninstalled then reinstalled it to no avail.  Would "apt-get" make a difference, do you think?

---

### Post by Sef on 2008-12-28
> Quote:
 	 	 		 You may have a misconfiguration with gparted. I would suggest reinstalling gparted to see if that makes any difference. In a terminal type:  	 	 
I've already tried that, though through Synaptics. I uninstalled then reinstalled it to no avail. Would "apt-get" make a difference, do you think?


No, synaptic is simply a front-end GUI for apt-get.

---

