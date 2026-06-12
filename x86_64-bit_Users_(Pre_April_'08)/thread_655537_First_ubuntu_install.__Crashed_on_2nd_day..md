---
title: "First ubuntu install.  Crashed on 2nd day."
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrchaos101 on 2008-01-01
Windows user here.

On my 2nd day of Ubuntu I managed to crash it.   I was playing the streaming audio from [www.kbpi.com](www.kbpi.com)

I was in firfox surfing the net.  I tried to open up Evolution Mail.  It thought about it for a while but would not open up the email client.  I tried to open up email 4 more times with same result.  I figured I should reboot (just like a windows box)  but was under the impression things like this were not common.  So, I elected to just log off. 

The system never logged off.  The music kept plalying and it was locked up. I could not do any thing other then hit the reset button on the box.

Any idea what happened?

---

### Post by ~LoKe on 2008-01-01
It was probably just hung up on those extra processes (I'm betting they were running, you just couldn't see them).  In the future I would advise killing a process if you started it but see nothing.

---

### Post by mrchaos101 on 2008-01-01
> **~LoKe said:**
> It was probably just hung up on those extra processes (I'm betting they were running, you just couldn't see them).  In the future I would advise killing a process if you started it but see nothing.

How do I kill a processes?


Noob sorry.

---

### Post by ~LoKe on 2008-01-01
> **mrchaos101 said:**
> How do I kill a processes?


Noob sorry.

Don't be sorry, we're here to help.

You can kill a process by opening up the terminal and typing the following:
```
killall processname
```
For firefox, as an example, you might need to do this....
```
killall firefox firefox-bin
```
Evolution
```
killall evolution
```

Sometimes that doesn't work and you'll need to kill the actual process id number (pid).  You can find this number by typing this...
```
pidof firefox
```
For me it would return...
> [15:47:16 loke]$ pidof firefox-3.0
16920

So I could just do..
```
kill -9 16920
```

Sorry if I've said anything that confused you.  If you have any questions, just ask.

---

### Post by mrchaos101 on 2008-01-01
is there a command to list all processes currently running?

---

### Post by ~LoKe on 2008-01-01
> **mrchaos101 said:**
> is there a command to list all processes currently running?

```
top
```
It'll be ordered by resources, on the left is the PID, on the right is the name of the process.

---

### Post by snakeeyes on 2008-01-01
In kde u can use ksysguard, its like that thing that comes up in windows when u press alt+ctrl+del, is it a task manager or something. I AM FINALLY FORGETTING WINDOWS, YES!

You should have a system monitor in gnome as well!

---

### Post by khensucat on 2008-01-02
> **snakeeyes said:**
> You should have a system monitor in gnome as well!

Click on "System", then "Administration", then "System Monitor". It's included by default. So you'll have it unless you deleted it on purpose ;)

You can also add it to any panel by right clicking the panel, anywhere, choose "Add to panel", click "System Monitor", click "Add" in the bottom right corner, and then click close :)

---

### Post by jken146 on 2008-01-02
Instead of doing a hard reset of your computer you can restart the X server with Ctrl+Alt+Backspace if it locks up horribly.  Try to find the culprit and kill it first though.

---

### Post by slopis on 2008-01-02
well mrchaos101, you are not so bad if crash only on secound day :D
when i first  started (a year ago) i crashed it every day. i had maganed to crash core too :D
after 2 weaks of faithing with ubuntu i stoped to use, and now i am back.
and thx all helpfull ppl, sone of those commands i usefull, now i will know that such things exist here :D

---

