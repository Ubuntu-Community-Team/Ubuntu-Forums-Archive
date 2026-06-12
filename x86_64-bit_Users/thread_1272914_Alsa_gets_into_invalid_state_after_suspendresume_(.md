---
title: "Alsa gets into invalid state after suspend/resume (issue and workaround)"
date: 2009-09-22
forum: x86 64-bit Users
---

### Post by foxmajik on 2009-09-22
Hello,

I discovered that Alsa gets into an invalid state if these conditions are met:

Your platform is 64 bit
You are using firefox/swiftweasel/swiftfox/thingwossname
You suspend your machine and then resume
You try to play sound in a Flash application

The system gets into a state where you can only play sound in Flash if no other application is playing sound.

In the terminal you get the output:
```
unable to open slave
unable to open slave
unable to open slave
unable to open slave
unable to open slave
unable to open slave
unable to open slave
unable to open slave
unable to open slave
```

After doing some googling I discovered that restarting Alsa resolves the problem and that subsequently you can play audio in Flash and other applications at the same time.

So I made a gnome-panel launcher that executes this command:
```
gksudo /sbin/alsa force-reload
```

I would speculate that when the system is suspended and resumed the PID file for Alsa becomes invalid because the time jumps ahead, but this is just a guess.

---

### Post by amd-64 on 2009-09-23
Yep. Reloading Alsa worked for me too. 

[http://ubuntuforums.org/showthread.php?t=1249885](http://ubuntuforums.org/showthread.php?t=1249885)

---

