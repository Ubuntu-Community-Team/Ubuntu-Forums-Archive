---
title: "DDO/lotro install help! Errors on install. Steam and .exe"
date: 2012-07-15
forum: Wine
---

### Post by Newuser901 on 2012-07-15
I'm not understanding the other threads I've found or I don't think they are having the same issue exactly. I also can't find the one installer for lotro some things say I need to install first. I'm assuming it's a general installer like SOE has for turbine or something. Maybe that is a simple solution if I could find it. didn't see it anywhere on the lotro site. And I set both to executable so that isn't the problem. In fact the error is identical with and without it being checked for executable.

My OS:
Ubuntu12.04 (64bit)
Wine 1.4

I have DDOhigh.exe, and lotrostandard.exe for that matter, both give the same two errors:

"Fatal error in gc
Get thread context failed"

Then:

"Wine Program Crash
Internal errors- invalid parameters received"

I also went through the trouble of dling them on steam and tried to run and get this error during the attempted .net setup:

Screen info:

".NET preparing first time setup.
Installing: Microsoft .NET Framework (step 1 of 2)"

Error:

"Fatal error
Failed to delay load library mscorlib.dll(Win32 error:0).
This program can no longer run and will now terminate."

This error happens twice on the (step 1 of 2) window. After clicking ok to remove the windows twice it goes to (step 2 of 2) and then shuts down.

This happens identically to both the steam versino of DDO and LOTRO.

And what is better to install under plain Wine or Steam. Should I choose one over the other if I have a choice?

I also tried installing .NET framework from the installer from microsofts site to see if it would help. It starts to install but says I have the same or better version already installed. This was installing into Wine. Not sure which version I have or If I have one at all. I'm assuming I do now.





Edit: Also there is an error but I can't see it if I run under mono runtime(terminal) I'm not sure how to make the terminal stay up or run the .exe in a normal terminal.

Edit#2: I used ./ddohigh.exe to run it and got an error with a log. How do you make the qoute like box with a scroll bar so it doesn't make the screen 50 feet high if I post it? It was saved by default as backtrace.txt I beleive.

lotrostandard.exe got the error:

./lotrostandard.exe
Log file is being written to C:\users\*******\Temp\lotrostandard.exe.log
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

---

### Post by DoktorSeven on 2012-07-16
You need the program "PyLOTRO", the native launchers do not work at all.

Instructions are [here](http://www.mcgillsociety.org/PyLotRO/index.html).

---

### Post by coreymanshack on 2012-07-16
> **DoktorSeven said:**
> You need the program "PyLOTRO", the native launchers do not work at all.

Instructions are [here]("http://www.mcgillsociety.org/PyLotRO/index.html").

That site does not have the program 'PyLOTRO'. I've been to almost everywhere google points me and I am unable to find a download of the PyLOTRO script for wine. I've downloaded crossover (A PAID SOLUTION)...... and it is unable to find microsoft visual c++ 2003 (From the site that pylotro is supposed to be at but is suspended). I downloaded microsoft visual c++ from microsuck and pointed crossover to this and it didn't work.

Crossover **does** have a working pylotro inside it. I copied all the pylotro files from crossover to my new wine prefix and did a few more things and I got DDO working tonight. If you need help with this I can probably write up a howto and provide pylotro files.

---

### Post by brainwash on 2012-07-16
> **coreymanshack said:**
> That site does not have the program 'PyLOTRO'.
Did you scroll all the way down? You can download the installer for the Windows version of PyLotRO from that site. However, it might be outdated.
> Download the most recent PyLotRO installer here: [pylotro-setup.exe]("http://www.mcgillsociety.org/PyLotRO/pylotro-setup.exe") (version 0.1.15a)

---

### Post by coreymanshack on 2012-07-18
> **brainwash said:**
> Did you scroll all the way down? You can download the installer for the Windows version of PyLotRO from that site. However, it might be outdated.

Ahh.... the one link that people go to that page before is basically hidden... and they don't have the native linux version >.>

---

### Post by wmpetkowicziii on 2012-09-29
I'm having the same exact problem as the first guy.  I read the comments and downloaded both PyLOTRO and Crossover, but neither are working.  The same errors keep coming up.  Could I be doing something wrong?  I'm new to Ubuntu and Linux, and I'm not the most computer-savvy person out there.  Please help me!

---

