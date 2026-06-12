---
title: "Java support + Flash on AMD64 Xubuntu 8.04"
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by freshtealeaf on 2009-02-02
Hello

I can't get Java to work on any of my Mozilla browsers (I use Firefox and Seamonkey). Aside from that, flash is incredibly slow (depending on the Flash app) on Seamonkey, and most of the time nonexistent on Firefox. I can't even get Yahoo Games working, since all of their games run on Sun's JRE. I went to Add/Remove.. and installed the Sun Java package, along with the IcedTea Java package, still to no avail. I simply cannot get it working.

Can anyone point me in the right direction? I'm running Xubuntu 8.04 64 bit with an AMD64 3000+. 

I've already looked through the forums and don't quite understand what the problem is. I've already spent hours trying to figure out out too but I just don't get what is wrong with my system! 

Thank you !:popcorn:

---

### Post by smo0th on 2009-02-02
hi,

[[COLOR="DarkOrange"][/COLOR]this]("http://ubuntuforums.org/showthread.php?t=766683") thread will do it.

cheers :)

---

### Post by Therion on 2009-02-02
```
sudo apt-get install xubuntu-restricted-extras
```
Follow the prompts and you're good to go.

---

### Post by Yellow Pasque on 2009-02-02
See this thread: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)
Use the scripts that Kilz provides under "64bit Adobe Flash Alpha and Java Beta"

---

### Post by shane4stef on 2009-02-02
I totally agree with Temüjin..use kilz scripts. just used myself and its was just soooo easy..couple of clicks and all is working for me.

---

### Post by sloggerkhan on 2009-02-03
it might be an issue of **which** java.

---

### Post by freshtealeaf on 2009-02-08
Whatever version of Java is used for Yahoo Games and WebCT (the system my school uses to submit assignments and view course content online). 

I installed xubuntu-restricted-extras, no change.

I used Kil'z scripts in terminal, it did its whole shabangabang. 

However, I still can't use Yahoo Games. I'm going to try restarting my computer.

---

### Post by freshtealeaf on 2009-02-09
*bump*

Sorry guys, I've tried installing the scripts (They worked successfully) however I'm still unable to use Yahoo Games in Firefox :( 

Any other suggestions?

---

### Post by Bob63 on 2009-02-10
Try this.
I am using Ubuntu 8.10 (Intrepid) x64 running on an AMD Athlon 64 3400+.
I am using Open Java, IcedTea, and (for some reason) two Shockwave Flash plugins in FIrefox.
Typing "about:plugin" in Firefox's address bar shows that the two shockwave flash plugins are libswfdecmozilla.so and libgnashplugin.so.
All can be found through the Synaptic Package Manager.

To test Java I usually navigate to the National Weather Service Office's page which shows the radar map for my area. There is an enhanced radar view that uses Java to display overlays.

I also went to the Yahoo Games  and played a couple, so I know that my Shockwave works.

Hope this helps.

Bob63

---

