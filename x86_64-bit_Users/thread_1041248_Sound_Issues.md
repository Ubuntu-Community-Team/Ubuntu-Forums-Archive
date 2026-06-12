---
title: "Sound Issues"
date: 2009-01-16
forum: x86 64-bit Users
---

### Post by fooballz on 2009-01-16
Hi all,

I am currently running on Hardy with a Lenovo Thinkpad T61 and I keep running into some sound issues.

Most notably is when I try to run Skype, it fails to initiate a call (something about no access to audio) if I have *any* program open that would use audio. For example, if Rhythmbox is open (not necessarily playing music) then Skype won't work. I have to close Rhythmbox first, then open Skype. Also I find that if re-open Rythembox, now its audio won't work. I am using the ALSA sound configuration right now. I have the same issue with Firefox being open too (I think gmail chat uses audio, which is usually what causes the same problem).

My question is if there is anything I could do to make Skype more friendly with my other programs (ie let both programs have access to sound). It really sucks that I can't even have Firefox and Skype open at the same time and is forcing me to sometimes revert to my dual-boot of windows.

A slightly unrelated issue is if I turn the volume to max then I hear cracking noises in the background, even if nothing is using audio at the moment.

Thanks a lot!

-- Justin

---

### Post by oooh on 2009-01-17
Your problem is quite common:
Just check Ubuntu documentation:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

And go to trouble shooting, in section:

*4. ALSA Configuration*

They explain your problem.

I run Hardy Heron and always had your problem. However, I updated to the last headers last week, and the problem **WAS SOLVED** ! I dont know why.

However, after a computer restart, the problem **APPEARED AGAIN**, so I still have the problem.

I understand this is not of very much help so far, but at least you know it is a well known issue.

Some proposed solution from the link I sent you are:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)
[http://juljas.net/linux/skype/](http://juljas.net/linux/skype/)

Good luck

---

