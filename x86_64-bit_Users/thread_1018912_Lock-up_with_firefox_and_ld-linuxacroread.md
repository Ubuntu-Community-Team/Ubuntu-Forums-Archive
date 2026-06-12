---
title: "Lock-up with firefox and ld-linux/acroread"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by sjbaugh on 2008-12-22
I have been experiencing periods of high processor usage and ever increasing RAM usage at the same time. The increasing RAM usage eventually causes a system lock-up.

After many experiments I have found that it happens when a .pdf link is clicked on in firefox and displayed in firefox and the pdf-containing tab is subsequently closed (this happens repeatably).

System monitor shows that when firefox opens the pdf link and displays it using the acroread plug-in a process called:
ld-linux.so.2
is started. This appears to be used to start acroread.

 When the pdf containg tab is closed this process has a continuous "running" status with high CPU usage and its memory usage continuously increasing. I was talking to a friend about this on Skype earlier and noticed that while we had a Skype connection open ld-linux was being killed when the pdf tab was closed (as I suspect it is supposed to). Guessing that it might be processor load related, I increased the processor rating from "On Demand" to "performance" using the CPU Frequency Monitor for both processors, they were now running at full speed (3GHz). This time the ld-linux process is killed correctly every time.

Is this a 64 bit issue? I feel I should report it to somebody but not quite sure who and how.

System:
Intel E8400 dual core processor at 3 GHz.
2 GB of memory
Ubuntu 8.10 64 bit
Acroread 8.1.3
Firefox 3.0.5

Steve

---

### Post by sjbaugh on 2009-01-06
Further to the above, I have now disabled CPU Frequency Monitor service and have had no trouble since.

I am still interested if anyone has any comments on what is going wrong or which application is likely to be the cause.

Steve

---

### Post by TheAL76 on 2009-01-06
I experienced the same thing as well.

I was considering switching back to the Document Viewer over Adobe Reader, as I don't need anything fancy in my PDF viewer.

---

### Post by stlouisubntu on 2009-01-13
Thanks so much for posting this.

I am trying to help my folks with their 64-bit Ubuntu Hardy AMD 2.4 Ghz
1 GB RAM machine locking up.

I talked them through a couple of about:config firefox fixes to help
patch memory leaks (and one fix in Thunderbird, too) and it seems to
have helped tremendously -- no lock-ups since.

However, now that you mentioned it, they do have acroread installed 
probably the plug-in, too.

When they launch firefox, the frequently get a message stating that
firefox is already running (but it isn't.)  I would really like to know how to fix that as it seems like part of the problem.

They also have three resource meters running on the taskbar (in the notification area), one CPU, one memory, one disk, and one network (okay
maybe four.)

They really don't need acroread, but they think they do.  Hard to make them understand that evince does the same thing when all the .pdf files
online tell them that they need acroread.

What kind of resource monitor were you using that you disabled (which helped you fix your problem)?

---

