---
title: "Ubuntu freezing problems on 100% processor use"
date: 2007-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by jllangston on 2007-03-11
Hello,

I have the i386 version of 6.10 on my AMD64 laptop. Quite frequently the machine freezes when the processor use is at 100%. It happens so often that when I look up at system monitor and see the system processor use at 100% and the fan is whirring at the  high rate, the machine freezes in roughly 7 sec.
 

Some things it has frozen on before:

When i attach my palm, sometimes gpilot causes it (roughly 30%). I can stop this before too long if I am quick about killing the program.

After I first installed 6.10, the machine went through the upgrade process and when it hit the capella part, the fan whirred up high and a couple of seconds later stuck.  Got a kernel panic and had to boot up into lower version kernel and do dpkg --configure -i to try installing upgrades again.

Just now, when running Automatix2 for the first time, so again I got a kernel panic.


I have run the memtest to see if that was the problem. Ran it all night, no errors.



I have several questions regarding this: Why does this thing freeze up so much? Is there a way of rebooting gracefully without turning the thing off and on? And lastly, if I can't reboot gracefully, it seems that just turning the computer off and on again is kinda harsh. Can I do anything to make things happier when I turn on (filesystem stuff, or ???) ?

This is a very frustrating problem. I am kinda new to Linux/Ubuntu. I would appreciate any and all takers!

Thank you,
Jeff

---

### Post by John Jason Jordan on 2007-03-11
> **jllangston said:**
> I have the i386 version of 6.10 on my AMD64 laptop. Quite frequently the machine freezes when the processor use is at 100%. It happens so often that when I look up at system monitor and see the system processor use at 100% and the fan is whirring at the  high rate, the machine freezes in roughly 7 sec.
Some things it has frozen on before:
When i attach my palm, sometimes gpilot causes it (roughly 30%). I can stop this before too long if I am quick about killing the program.
After I first installed 6.10, the machine went through the upgrade process and when it hit the capella part, the fan whirred up high and a couple of seconds later stuck.  Got a kernel panic and had to boot up into lower version kernel and do dpkg --configure -i to try installing upgrades again.
Just now, when running Automatix2 for the first time, so again I got a kernel panic.
I have run the memtest to see if that was the problem. Ran it all night, no errors.
I have several questions regarding this: Why does this thing freeze up so much? Is there a way of rebooting gracefully without turning the thing off and on? And lastly, if I can't reboot gracefully, it seems that just turning the computer off and on again is kinda harsh. Can I do anything to make things happier when I turn on (filesystem stuff, or ???) ?
This is a very frustrating problem. I am kinda new to Linux/Ubuntu. I would appreciate any and all takers!
I have had similar problems on my amd64 laptop since I got it almost two years ago and first installed Hoary amd64. The problem is that there are a million combinations of things that can cause these problems. I finally arrived at the conclusion that to run Linux you must assume you will always be running beta software. You can minimize the problems by using distros that are known to be more stable. In the Ubuntu world that would be Dapper 6.06. And even then, don't install upgrades right when they first appear -- wait a few days and lurk in the forums to see if there is any sudden screaming. You can always tell the pioneers -- they're the ones with the arrows in their backs.

In my case I use Edgy amd64 on my Compaq R3240 and wish I hadn't upgraded from Dapper. On the other hand, one of the reasons I bought this laptop was to learn Linux, so I deliberately installed the 64-bit version, knowing that it would have a few more problems than 32-bit Ubuntu. Every time something blows up I learn something new. It's a question of my personal tolerance for pain balanced with my desire to learn.

In your case it may not be just one problem. For example, since you mentioned your PDA, I immediately suspect the USB drivers. But the other issues you mention don't use the USB ports, so there may be something else going on as well. I would suggest you try a few command line things. Start with:

dmesg | less

Do this right after booting. The "| less" makes it display one screenful at a time. You have to hit the spacebar to get to the next page. Once you've got it all scrolled down you can do Edit > Copy and then paste it into something like Gedit to save it for future reference. It will be long, but read through it all even if you don't understand most of it. Error messages usually stand out and can give you a clue if there is a hardware/driver issue.

Also, post the error messages here (not the whole thing!) and ask if anyone has any suggestions. I would recommend that you post in the general forum instead of this 64-bit forum, because you'll get more viewers and the problem is more likely related to 32-bit Edgy than to the 64-bit hardware.

Another thing to try is to make one or two additional small partitions if you can and use them to install other distros. Try 64-bit Ubuntu Edgy or Dapper. Try Suse and some others as well. Sometimes the comparison can lead you to clues about what is wrong.

And don't give up. Linux is worth the occasional problem. Linux rocks!

---

### Post by Kilz on 2007-03-11
Welcome to the "My 64bit hardware doesnt run the 32bit version flawlessly" club. The 32bit os isnt guaranteed to run on 64bit hardware without problems.  the 32bit os  isnt the cure all, easy fix for 64 bit some people make it out to be.

---

### Post by JAPrufrock on 2007-03-11
> I have several questions regarding this: Why does this thing freeze up so much? Is there a way of rebooting gracefully without turning the thing off and on?

Does it freeze completely or can you still use system monitor?   I often get  100% cpu usage after  I use gpilot.  But if I go to system monitor/processes and click  "end process", my cpu usage drops down to near zero again.  Same for some other programs (but not all). 

If it completely freezes before you get to use system monitor, you can always kill and restart the desktop by using ctrl-alt-backspace (which is better than a reboot).  There's also probably a way to use *killall* from terminal, but I haven't tried that yet.

---

### Post by jllangston on 2007-03-12
> Does it freeze completely or can you still use system monitor? I often get 100% cpu usage after I use gpilot. But if I go to system monitor/processes and click "end process", my cpu usage drops down to near zero again. Same for some other programs (but not all).

If it completely freezes before you get to use system monitor, you can always kill and restart the desktop by using ctrl-alt-backspace (which is better than a reboot). There's also probably a way to use killall from terminal, but I haven't tried that yet.

Everything freezes. mouse won't work, Ctl-alt-backspace won't work, nothing.

---

### Post by jllangston on 2007-03-12
> **Kilz said:**
> Welcome to the "My 64bit hardware doesnt run the 32bit version flawlessly" club. The 32bit os isnt guaranteed to run on 64bit hardware without problems.  the 32bit os  isnt the cure all, easy fix for 64 bit some people make it out to be.

:) hehe, thanks!


John Jason Jordan,  Thank you for your advice, but I didn't see anything obviously wrong in dmesg.

Yes this is a learning process and I do enjoy it, but sometimes it is frustrating...

---

### Post by JAPrufrock on 2007-03-12
Can you exit gnome by using  Ctrl-Alt-F6 and getting into bash?  If so, you can use killall to kill the offending app.   For instance "killall gpilotd".  Then use Ctrl-Alt-F7 to get back to gnome.  Just a thought.

---

