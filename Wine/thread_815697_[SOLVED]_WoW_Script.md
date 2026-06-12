---
title: "[SOLVED] WoW Script"
date: 2008-06-01
forum: Wine
---

### Post by Mauler5858 on 2008-06-01
Is there any way to do a script to do this in this order:

End Gnome
Start Ventrilo
Start Firefox
Start World of Warcraft

Then upon ending World of Warcraft:

Kill Firefox and Ventrilo
Restart Gnome

---

### Post by tamoneya on 2008-06-01
just put it into ~/.bash_rc
```
firefox
ventrilo
wine /path/to/wow

```
As for the killing of proceses you are going to need to get the pids of the processes by searching with their names. Then use ```
sudo kill -9 pid
```

---

### Post by Mauler5858 on 2008-06-02
> **tamoneya said:**
> just put it into ~/.bash_rc
```
firefox
ventrilo
wine /path/to/wow

```
As for the killing of proceses you are going to need to get the pids of the processes by searching with their names. Then use ```
sudo kill -9 pid
```

So i just start a standard bash script and execute my programs, but, how do i:

1. Get the PID's to kill the processes.
2.  Put a delay between starting each program by say 5 seconds.
3.  Ensure that when World of Warcraft is closed that gnome automatically restarts.
4.  And a little help on all the syntax.(I am extremely new to script writing)

Many thanks in advance.

---

### Post by Mauler5858 on 2008-06-02
I tried my luck at most of it.  Will this accomplish my idea in the most efficient manner?

```

#!/bin/bash

metacity --replace &
wine "C:\Program Files\World of Warcraft\wow.exe"     
gnome-panel nautilus --replace &

sleep 5

firefox

sleep 5

wine "C:\Program Files\Ventrilo\ventrilo.exe"

```

---

### Post by Mauler5858 on 2008-06-02
Seeing that i really have deviated off of wine with this post.  i will mark this one solved and take it to another section.

---

