---
title: "Ubuntu (now) runs very sluggish on an excellent system?"
date: 2008-12-13
forum: x86 64-bit Users
---

### Post by computer_freak_8 on 2008-12-13
My computer (which is fairly high-end - see link in signature for specifications) is running rather sluggishly. 

I always thought it was just because I had Folding@Home hogging my GPU and half of my CPU, but I noticed that, even without running any of the clients, my computer is almost just as slow.

I have already disabled a lot of start-up items that I don't need, and my CPU/RAM usage in the Gnome System Monitor is minimal.

As I was viewing my open processes, I accidentally clicked a button I hadn't noticed before: the one that sorts the processes by their nice value.

That's when I noticed that a process by the name of "krfcommd" is running at a nice value of "-10" (Very High Priority).

It is immune to my attempts at killing it; both "sudo kill 6939" and "sudo killall krfcommd" do nothing.

I have not yet been able to find out what this program is - though it appears (via Google and naming conventions) that it is a Bluetooth (Google) Radio Frequency Communication Daemon for the K Desktop Environment (naming conventions).

I have not found it (as installed or not installed) in package management software (Synaptic, "apt-get" and Aptitude).


*Update: Starting a terminal with a nice value of -11 proved useless, as well.

---

### Post by Ng Oon-Ee on 2008-12-15
Just because it has a high priority doesn't mean its affecting other apps, especially if its usage is very low.

Why are you running a KDE component in Gnome anyway?

You could just run 'top' in the terminal and see what (if any) apps are hogging your CPU. If nothing is hogging the CPU, the issue is likely to be hardware, somehow. Try creating a new user and see if that user has a responsive interface.

---

### Post by computer_freak_8 on 2008-12-15
Not sure about the KDE in Gnome thing... as far as I knew, the only KDE component I had installed was KCron - and that's because Gato would not/will not work.

Well, I've rebooted, cleared the CMOS, and the problem's still there.
However, I have a different thought on it this time: Now, I notice many instances of a process by the name of "gvfsd-trash" - I looked at the bottom when I noticed this, and my trash basked icon is gone, and I can't seem to add it again.

So I try "sudo killall gvfsd-trash", and they all go away (30 of them). But, within the time it took to type this far, (less than three minutes,) 32 instances of it are back. 

I tried "sudo apt-get remove gvfs-fuse", followed by "sudo apt-get install gfs-fuse", but the problem remains.

Combined, these instances of that process amount to almost half my CPU load at times (according to gnome-system-monitor).

[ a few hours passes; realizes post hasn't been posted (only clicked "Preview") ]

Well, I finally was able to load the trash, and then (nearly) empty it. (One empty, stubborn folder remains...)


But still, the system is... I don't know... I used the word "sluggish" before, but the more I experience it, it seems like "stuttering" would be a more appropriate term. Also, "jerky", "momentarily freezing, only to unfreeze immediately thereafter", and "pause, go, pause, go, pause, go..." all come to mind.

I have also tried logging to a spare account I created a while back, the issue persists.

On my list to try: a previous kernel version.

---

### Post by computer_freak_8 on 2008-12-16
> **computer_freak_8 said:**
> On my list to try: a previous kernel version.
Change of plans. I just installed the newest updates, and one of them was a kernel upgrade. So, I edited the "menu.lst", booted the new kernel, and it seems much better now. I think that fixed it.

As a note, just in case it might have been the problem, and/or might help anyone else, I noticed that the kernel I had been using did not have the "ro" (read-only) argument passed to it, but I did include it for the new kernel.


Thanks,
computer_freak_8

---

### Post by Ng Oon-Ee on 2008-12-16
Ah. Kind of weird, wonder why specifically that would happen on your system.

Good to hear you've got it solved, though =). Happy Ubuntu

---

### Post by voltsy on 2008-12-21
Hi computer_freak_8,

You said << .... I noticed that a process by the name of "krfcommd" is running at a nice value of "-10" (Very High Priority). It is immune to my attempts at killing it; both "sudo kill 6939" and "sudo killall krfcommd" do nothing. I have not yet been able to find out what this program is - though it appears (via Google and naming conventions) that it is a Bluetooth (Google) Radio Frequency Communication Daemon for the K Desktop Environment (naming conventions). >>

I noticed krfcommd too after visiting some dubious web sites. Also for me, the kill and killall commands failed to shift it, but it does seem to be related to bluetooth, because turning off System > Administration > Services > Bluetooth Device Management and rebooting means it is no longer a running process.

HTH ;-)

---

