---
title: "Forte Agent crashes under Wine"
date: 2008-09-30
forum: Wine
---

### Post by bob12564 on 2008-09-30
I'm new to Ubuntu/Linux and have gone back and forth from Ubuntu and Windows XP.  I need some help.

I had Agent newsreader v 1.93 (an old timer but reliable!) running under Wine 0.9.46, which I found in the Ubuntu repository that came with Ubuntu 7.10/Gutsy.  The Wine website says that this is a safe combination.  It worked well for about a month until I accepted some Ubuntu updates and discovered that I could no longer start Agent from the Wine menu.  Someone suggested running Agent and Wine from a terminal window instead and that worked well for about 2 months.  Now that also crashes.  Coincidentally, I had just installed some more Ubuntu updates.

Can someone help me find the error?  The error message seems to come first and then the terminal window scrolls quickly before I can read it.  If I scroll the terminal window up all I see is a dump.  Is there a Wine log file that has the all of the messages?

In addition to Agent, I also have an old version ACDSee (3.2?) image viewer running under Wine.  That's running well.

I am planning to upgrade Ubuntu to 8.04/Hardy soon and I understand that there's a newer version of Wine that comes with it that may solve the problem with Agent.  Is that true?  Should I remove Agent, Wine, and ACDSee before I upgrade?

Thanks for any help!

---

### Post by asdfoo on 2008-09-30
> **bob12564 said:**
> I'm new to Ubuntu/Linux and have gone back and forth from Ubuntu and Windows XP.  I need some help.

I had Agent newsreader v 1.93 (an old timer but reliable!) running under Wine 0.9.46, which I found in the Ubuntu repository that came with Ubuntu 7.10/Gutsy.  The Wine website says that this is a safe combination.  It worked well for about a month until I accepted some Ubuntu updates and discovered that I could no longer start Agent from the Wine menu.  Someone suggested running Agent and Wine from a terminal window instead and that worked well for about 2 months.  Now that also crashes.  Coincidentally, I had just installed some more Ubuntu updates.

Can someone help me find the error?  The error message seems to come first and then the terminal window scrolls quickly before I can read it.  If I scroll the terminal window up all I see is a dump.  Is there a Wine log file that has the all of the messages?

In addition to Agent, I also have an old version ACDSee (3.2?) image viewer running under Wine.  That's running well.

I am planning to upgrade Ubuntu to 8.04/Hardy soon and I understand that there's a newer version of Wine that comes with it that may solve the problem with Agent.  Is that true?  Should I remove Agent, Wine, and ACDSee before I upgrade?

Thanks for any help!

hi bob12564

Sounds like it might be a regression (a change in Wine that might have fixed something else broke your app).

There's a procedure you can follow to identify the change that broke your program [http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting) - which you can follow if you're comfortable with compiling from source.   

If not, maybe you can provide a download link and I can take a look for you.

---

### Post by tankist on 2008-09-30
Instead of Forte Agent you can try Pan news reader. Very similar in the interface and functionality.

---

### Post by bob12564 on 2008-09-30
I was able to generate a Wine log and I now have the error messages.  Any ideas?  This is way over my head!

At the top I see this:

wine: Unhandled exception 0xc0000090 at address 0x7ed0e810 (thread 0009), starting debugger...
First chance exception: invalid float operation in 32-bit code (0x7bc629b7).


Later I see this:

0x7bc629b7 set_cpu_context+0x67 [/build/buildd/wine-0.9.46/dlls/ntdll/signal_i386.c:619] in ntdll: frstor	0xfffffd24(%ebp)
Unable to open file '/build/buildd/wine-0.9.46/dlls/ntdll/signal_i386.c'

The log file is too large for this forum so I can't attach it.  Hope this helps.

---

### Post by bob12564 on 2008-09-30
> **tankist said:**
> Instead of Forte Agent you can try Pan news reader. Very similar in the interface and functionality.


I tried Pan but the lack of documentation makes it tough to use.  I'm sure it can do a lot more than I was able to figure out, but I need something that works now.  The Wine/Agent combination seems to be very popular and Agent seems to be the most popular newreader on any platform.

---

### Post by bob12564 on 2008-09-30
> **asdfoo said:**
> hi bob12564

Sounds like it might be a regression (a change in Wine that might have fixed something else broke your app).

There's a procedure you can follow to identify the change that broke your program [http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting) - which you can follow if you're comfortable with compiling from source.   

If not, maybe you can provide a download link and I can take a look for you.


I doubt this is it.  I am still using the version of Wine that is available in the Ubuntu repository.  I never updated it and Ubuntu hasn't offered any updates to it. 

This was working fine 2 days ago.  Thanks for the suggestion.

---

