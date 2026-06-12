---
title: "Verbose Mode"
date: 2008-06-18
forum: Wine
---

### Post by MacAnthony on 2008-06-18
Does wine have a verbose mode to it? There is a feature that isn't working within wine of one of my programs but there isn't any output when using that feature from the command line. Is there another way to get more information to see if it can be resolved?

---

### Post by cogadh on 2008-06-19
You could try using the [Debug Channels](http://wiki.winehq.org/DebugChannels).

---

### Post by MacAnthony on 2008-06-19
So I set the WINEDEBUG variable to something like WINEDEBUG=warn+all in the session before just starting wine and my app normally? That what I got out of that page but just wanted to make sure I was understanding it correctly.

---

### Post by cogadh on 2008-06-19
Yup, just run like this:
```
WINEDEBUG=warn+all wine foo.exe
```

---

### Post by MacAnthony on 2008-06-19
Thanks. Didn't seem to provide any further information. Looks like I'm stuck for now.

---

### Post by cogadh on 2008-06-19
What app are you trying to run?

---

### Post by MacAnthony on 2008-06-20
Cake poker.
[http://cakepoker.com/](http://cakepoker.com/)

In the interface, there are some tabs that don't work. They used to, but not convinced it's a regression issue since the software is updated so frequently.

---

### Post by cogadh on 2008-06-20
According to the AppDB page for the game, you need to install MSXML4 with winetricks to get it to work:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12334](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12334)

Have you done that yet?

---

### Post by MacAnthony on 2008-06-20
Um, that entry in appdb is mine :)

That was just to get it to run. I failed to test this one feature - which isn't a deal breaker in the program, but it's an annoyance.

---

### Post by cogadh on 2008-06-20
> **MacAnthony said:**
> Um, that entry in appdb is mine :)

That was just to get it to run. I failed to test this one feature - which isn't a deal breaker in the program, but it's an annoyance.

I was afraid of that. I noticed the name on the AppDB entry after I posted.

---

