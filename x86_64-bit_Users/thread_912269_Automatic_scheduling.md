---
title: "Automatic scheduling?"
date: 2008-09-06
forum: x86 64-bit Users
---

### Post by Melindrea on 2008-09-06
If the title seems vague, it's because I'm not sure exactly what's going on. =)

Lately, I've had some problems with my Ubuntu installation. Suddenly I will get what looks like a terminal window, with some kind of checkup. (running cupsd, ok, running something else, ok, running apache2 server, error message, not changing to KDE4 since that's not the standard screen, running scripts in <some folder>).

Any idea what's going on, and what is triggering it, and more importantly: HOw do I either a) get it to stop and/or b) get back to my main window? It used to be that it happened once or twice in a week, but this is the third time today... The only thing that :may: have triggered it (or could be complete coincidence) is that it happened when I was closing a tab in firefox. On the other hand, I've closed tabs without it happening!

Thank you in advance,
Melindrea

---

### Post by pytheas22 on 2008-09-06
Do you get dumped out of the graphical environment completely when this happens?  If you press control-alt-F7, do you come back?  What if you press control-alt-F7, then control-alt-backspace?

It could be X crashing, but without some more details it's hard to say exactly what's going on.  Once we get a better idea, we can figure out which log to look at to pinpoint the source of the problem and find a solution.

---

### Post by Melindrea on 2008-09-06
Ctr+Alt+F7 doesn't bring me back. I haven't tried the other key-kombination.

What is it supposed to do? (I'll try it once it happens again, where I hope that'll be far from now... =)

But yeah, it dumps me out of graphical mode, but I think the graphical is somewhere behind, since I can hear things going on there (in particular it was a call on Skype that I could hear from behind the terminal).

---

### Post by pytheas22 on 2008-09-06
Interesting that you can hear Skype...it does sound like some kind of problem with X.  Control-alt-backspace forces X to restart, so if pressing it brings you back to a login window, then we'll know with a decent amount of certainty that the error is related to X, and can look at the X logs to figure out exactly why it's misbehaving.

If control-alt-backspace does nothing, what about control-alt-F2?  Does that bring you to a command prompt where you can log in?

---

### Post by Melindrea on 2008-09-06
Haven't tried Ctr+Alt+F2, but now I'll have some tips to try next time it happens, thanks a lot. =) (I'll not mark this thread as solved since I don't know if it is, but will post next time it happens and answer if it works).

Thank you, however, even if this doesn't work. =)

---

### Post by Melindrea on 2008-09-12
It happened again today. I tried Ctrl+Alt+Backspace, and that did nothing, after trying ctrl+alt+F7. Forgot to check (etc)+F2, however.

It seems like it was looking for KDE4 for some reason? I had that installed for a laboration in a class, but removed it since I prefer Gnome (probably more by habit than anything else). It did give me two packages that weren't needed anymore, so I removed them, but now there's something really funky going on with my conky - it insists on laying in the foreground!

I think that I'm going to be reinstalling Linux, perhaps I've played too much with it. =) Then comes the question... Am I better off using 32-bits, or should I stick to 64? (I don't think I've noticed problems that are 64-bit related, but that could be because I really don't know Linux/Ubuntu the way I do Windows. =)

---

### Post by pytheas22 on 2008-09-12
There could be issues with kdm (the KDE window-manager process) conflicting with gdm (Gnome's process).  Maybe reinstalling is the simplest solution, provided you don't have too much invested in your current system.

In general there's no reason not to use 64-bit.  There are a few specific areas where 64-bit Linux can be difficult, but it's mostly limited to places where you need to use closed-source software but 64-bit builds are not available.  Adobe's flash player is an example--it's only released in 32-bit, and while it's possible to "wrap" a compatibility layer around it to make it run on 64-bit systems, it can be buggy that way.  If you use ndiswrapper, you also need to make sure that there are 64-bit Windows drivers available for your wireless card.  Beyond that, though, there's no reason not to use 64-bit.  It's faster and in almost all respects works as easily as 32-bit.  Graphical stuff should work just as well under 64-bit.

---

### Post by Melindrea on 2008-09-12
I do have some investment, but I'm sure it's good for morale to write up a list on what I need to get, for next time stuff screws up. =)

I think the most important thing I've noticed a problem with is something someone else mentioned: BankID doesn't work. There's also another place where there's something that doesn't work fully, but I should be able to use my stationary computer, which doesn't have the prestanda for 64-bits.

Thank you!

---

### Post by Melindrea on 2008-09-16
Ctrl+Alt+F2 brings up a new login window.

When it "crashes", it checks for something in KDE4, but it was too long to remember and flickered by fairly fast. I tried to install KDE4 using apt-get, but was told that there were unmet dependencies.

Any suggestions, or should I start looking over posts to get everything to work once I've reinstalled? =)

---

### Post by pytheas22 on 2008-09-16
You should be able to install all of KDE (along with the rest of the default Kubuntu packages) by typing:
```

sudo apt-get install kubuntu-desktop
```

This will leave your existing system intact, but install KDE with all of its dependencies, which will perhaps solve whatever problem is causing the crash.  If you get an unmet-dependencies error from running that command, go to System>Administration>Software Sources and make sure that all of the boxes under the "Ubuntu Software" section are checked, to ensure that all of your repositories are enabled.

If that doesn't work and you want to reinstall, I'm happy to help you get things set up if necessary.

Also, when you say that control-alt-F2 brings you to a login screen, do you mean a graphical login like you normally get when you boot to Ubuntu, or a command-line?

---

### Post by Melindrea on 2008-09-17
Yeah, it gives me a command line login, though I couldn't manage to log in in the end, while still hearing everything that went on in the background.

And reinstallation seems to be the only thing for me. I'll do that once I've reinstalled my desktop, since I'm right now using my laptop a bit as a "file server". And I've considered reinstalling a while, even before this problem, to change the size of my partitions. Ubuntu was :supposed: to be the "play", and XP what I used, now I only log into XP if there's a problem with Ubuntu... =)

Edited to add: Oh, right. Trying to install kubuntu-desktop gives me "unmet dependencies", and I have all the repositories under Ubuntu Software checked. There's something really funky going on! =)

---

### Post by pytheas22 on 2008-09-17
> Edited to add: Oh, right. Trying to install kubuntu-desktop gives me "unmet dependencies", and I have all the repositories under Ubuntu Software checked. There's something really funky going on! =)

That's strange.  Does running:
```

sudo apt-get update
```

help (it will make sure that your sources list and repository databases are in sync).  If not, if you want to try to troubleshoot this, please post your /etc/apt/sources.list file here.  But if you want to just reinstall Ubuntu (which is probably easier), then that's fine too.  There probably is some deep-seated problem if apt-get doesn't want to work.

---

### Post by Melindrea on 2008-09-17
Yeah, it's probably for the best to reinstall. This time I should know more than what I did last time, which is always a good start. =)

(Last time was for school. I'd read a little bit on how to make partitions and such, but I didn't find ubuntuforums until after I was done installing. =)

---

