---
title: "Mystery Process utilising 50% CPU"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by DanglingPointer on 2009-06-04
Hi All,

I have an invisible process clocking up a large percentage of my CPU.  When I check System Monitor, the percentages do not add up in the Processes tab when compared to the  Resources tab.  On average, each core of the processor is averaging about 60%.

In the processes tab, Xorg and gnome-system-monitor are the only ones consistently on top of the table when organized by CPU utilization in descending order; and they are no where near consuming 50% of total CPU.

In other words, something is using my CPU which when added up with everything else running averages 60+% and it is invisible and not shown in System-monitor.

Any ideas anyone on how I can track this ghost process down and find out why it is running perhaps a muck?  To me it looks like an infinite loop.

Has anyone ever had similar experience?

Another thing I need to mention is that there is very little to no disk activity.  however since there is plenty of ram, perhaps I/O is happening to RAM instead?

---

### Post by ad_267 on 2009-06-04
Under one of the menus there's an option to show which processes are running. This is probably set to show only processes started by you, change it to show processes from all users.

---

### Post by AndyCee on 2009-06-04
Perhaps in a terminal type:

top

and take a look. It shows more info than the default system monitor.
(Type ctrl-c to quit.)

---

### Post by DanglingPointer on 2009-06-04
Thanks for your replies.  I think I finally figured out what was wrong.  However I need further mileage and testing to confirm.

SYS MON:
I was viewing all processes but still showed nothing that would account for the large CPU usage.

TOP:
Top showed the same amount of utilization as SYS MON and did not show anything as well.

HTOP:
I donwloaded a similar program called HTOP and it finally showed something that gave me a clue.  Red colour on the core usage indicate kernel process doing something.  The questions were "what?" and "why?"

I had an "auto hide" panel on the left side of the screen with system monitor gadget on it, as well as a battery meter and cpu scaler.  I removed all of them and deleted the panel.  At first, it showed like it didn't do anything (for about 2mins).  But eventually on HTOP cpu utilization dropped to near zero!
I manually ran System Monitor and it reflected HTOP.

I will monitor and see if this happens again after next login and reboot.  Hopefully it solved the problem.

Obviously if what I have described above is correct, then it implies, having panel/s on the sides which auto hide is buggy somehow with one or more of the gadgets mentioned above.  Or perhaps all gadgets.

If anyone has experienced similar occurences, please reply back and describe it in this thread.

Thanks for the quick replies and help so far...

---

### Post by DanglingPointer on 2009-06-05
OK, I think I have finally fixed it. The problem was indeed a kernel process running a muck.  BUT it wasn't the side panel.  It wasn't any of the gadgets either.  It was one of my startup applications.  To be precise, it was "Remote Desktop".

Brief history:
1) After my last post, the problem came back.  What I failed to mention in my previous post was that, after I had gotten rid of the side panel and the gadgets residing on it.  I attempted to log out and log in again to see if the problem was still there after.  However while loging out, a pop-up appeared and advised that it couldn't shut down an unknown process.  So I canceled out of the log out routine; and that was when I noticed that the cpu utilization had ended.  However what actually got rid of the run-away process was the log-out routine!  Not me getting rid of the panel.

2) Seeing that the problem was back after restart; I decided to slowly disable my start up applications one after the other until eventually pinpointing it to remote desktop.  I don't even remember enabling it!

Anyways, problem solved!

---

### Post by Cenna on 2009-06-30
That's correct its the vino remote desktop server. I don't remember if I enabled it too. I think when you access remotely to the desktop it goes to the startup automatically and then causes problem.
However I think it has conflict with something else because it don't happen immediately after running vino.

---

### Post by johenkel on 2009-08-04
Wow , I am so glad ! found this thread.
I got an AMD64 3000 with mythbuntu running and I got the same thing "dbus-daemon" overloads everything. "vino-server" did not look that big.
Anyways , I disabled autostart of "remote connection" and cpu usage is down.

My mythbuntu is sitting in my basement with the video cable fished through the floor to my tv. Now I just have to enable vnc before I want to use it and then disable it again.

Thanks again !!!
johenkel

---

