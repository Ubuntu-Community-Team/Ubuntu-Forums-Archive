---
title: "Lagging issues"
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by burning_man13 on 2008-05-14
Oky... I've been having this strange issue ever since I upgraded... My computer lags off and on... One minute it will be running really well, then the next everything gets really jumpy... I have four gigs of ram in my computer, so there should be no reason why it would be lagging... Everything ran fine in Gutsy... I'm not too sure what info is going to be needed, so I will post when asked... Any help would be appreciated... Thanks in advance!!!

---

### Post by j2fraser on 2008-05-15
As a first investigative step, I would ask myself some questions:
Is there anything common to what happens when the lag happens? (e.g. running a certain program, downloading stuff in the background, updating the system?)
When the lag happens, does one or more programs become unresponsive?
Are there signs that your CPU is working overtime? (e.g. your computer heats up, the fan comes on, etc.)

I would look at the System Monitor to see if there is a process chewing away at your CPU. Ctrl-Alt-Esc should bring it up. Take a look and see if one process is using a lot of CPU time. Also, look to see what is going on with your network connection in terms of volume of traffic. You should also be able to see how much of that 4Gb of RAM is being used.

---

### Post by burning_man13 on 2008-05-16
There isn't any one program that makes it lag... as for programs becoming unresponsive... they go in and out... I'll get the gray screen of death for a half minute then it'll come back... I can usually predict it coming because my computer sounds like it's trying to run... then it'll sputter... I've checked the System Monitor and it doesn't look like any one program running in the background that is making it lag... One funny thing I saw, though, is that my computer is only registering 3 gigs of the available 4... I want to know what happened to the other gig... I know that if I was running a 32 bit OS it would only register 3 gigs... but I"m running a 64 bit version of Ubuntu, therefore it should register all 4 gigs... As for my computer getting hot... I have a laptop... so anytime it's plugged in, it feels hot...

---

### Post by burning_man13 on 2008-05-16
I kept my System Monitor running, and it went through a lagging spurt... but there wasn't any one program eating my resources... but under Resources -> CPU History it peaked at 94% and I was just playing a game of Solitaire...

---

### Post by j2fraser on 2008-05-16
Well, the memory display of ~3Gb when you have 4 is well known to me (see [here]("http://ubuntuforums.org/showthread.php?t=719280")), but it's probably not related to the problems you're having. Short story? Your system hardware is probably using the RAM (see link above). If you have bad RAM, though (which is quite possible), that could be causing freeze-ups. Does your system crash? What about memory usage during the laggy moments? Do you see a huge amount of memory being used up? I have to admit, I'm grasping a bit here. You could also go look at /var/log/syslog and see if there are a bunch of error messages in there.

---

### Post by burning_man13 on 2008-05-16
When it goes through the laggy periods it is still only using 800 meg of RAM... so out of 4 (3 registered) gigs of ram I'd say that 800 meg isn't bad...

---

### Post by burning_man13 on 2008-05-16
Well the laggy issues on my computer is done... I just had bad RAM... so I replaced it and all is fine... thanks for you help j2fraser...

---

### Post by j2fraser on 2008-05-23
Glad to hear that things are working now. Lag is no fun, especially when you've put out good $$ to get your system spec'd out! Enjoy. Cheers!

---

### Post by Zorael on 2008-05-23
On a closing note, Linux manages memory slightly differently from Windows; what good are those extra 3gb if they're not used?

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by burning_man13 on 2008-05-26
The reason why I use 4 gigs is because I do a lot of high end video editing and audio production... so I'm using anywhere between 5 and 30 different programs at any given moment...

---

