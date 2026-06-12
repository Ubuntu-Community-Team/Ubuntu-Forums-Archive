---
title: "Synaptic Package Manager &quot;broken&quot;"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by bukido on 2008-11-02
When I open Synaptic Package Manager in 8.04, I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and then it closes. If I try to install using other methods I get error messages telling me that I can't have more than one install manager open at the same time. It's as if the Synaptic Package Manager is seen by the operating system as always open.

I'm a GUI guy. Never used the terminal, but I'm up to the challenge if I have to use it. Any help is appreciated!

---

### Post by em4r1z on 2008-11-02
I've seen this error after a crash while Synaptic is running. I couldn't solve it easily and had to reinstall Synaptic using dpkg. Try the "sudo dpkg --configure -a" solution first and post the errors (most likely some weird symbols within some lines of the database.)

---

### Post by bukido on 2008-11-02
Where / how can I learn quickly about terminal basics? I've used a little DOS years ago, but I don't know how I would use theose commands. Just type that line into the terminal? Do I need to use other commands first to get to the root level first, like DOS?

That's what happened with Synaptic, btw. It crashed during an install...

---

### Post by em4r1z on 2008-11-02
Use the search feature.
[http://ubuntuforums.org/search.php?searchid=50787364](http://ubuntuforums.org/search.php?searchid=50787364)
That's just one option, you could also try "synaptic start", "synaptic crash", etc.

Anyway, enter that command and see if it solves your problem. Most likely it'll not but it'll provide you some clues about the packages affected during the crash, then you'll be able to install those packages manually or try a different workaround.
You should read various threads about the same problem and take notes of the different solutions (for the crash might have affected different things, i.e. my error was so critical that I couldn't start an X session.)

---

