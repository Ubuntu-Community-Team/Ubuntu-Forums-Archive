---
title: "AMD dual core -- but am I using both?"
date: 2007-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Footer on 2007-01-26
I hope this isn't a dumb question but here goes!

Just installed Kubuntu Edgy Desktop AMD64 on my system which has the AMD Athlon 64 X2 Dual Core processor (4200+).  When I go to System --> KInfoCenter Info Center --> Processor I see two processors but I guess I'm not completely sure they're both being used.  At the console, uname -r reports this kernel:  2.6.17-10-generic (does it need to be an SMP based kernel and if so, which one???).

Having lots of trouble getting the nVidia drivers to work as well.  Perhaps this is part of the problem?

Any and all help is greatly appreciated!

---

### Post by Kilz on 2007-01-26
> **Footer said:**
> I hope this isn't a dumb question but here goes!

Just installed Kubuntu Edgy Desktop AMD64 on my system which has the AMD Athlon 64 X2 Dual Core processor (4200+).  When I go to System --> KInfoCenter Info Center --> Processor I see two processors but I guess I'm not completely sure they're both being used.  At the console, uname -r reports this kernel:  2.6.17-10-generic (does it need to be an SMP based kernel and if so, which one???).

Having lots of trouble getting the nVidia drivers to work as well.  Perhaps this is part of the problem?

Any and all help is greatly appreciated!

All 64bit kernels are smp, they dont have it in the name because there are no non smp 64bit kernels.

---

### Post by ehowell on 2007-01-26
I just went through this same thing this week.

As I understand it...

The generic kernel includes dual core support out of the box. If you type /proc/cpuinfo you should see information for both cores (you can also look in System->System Monitor in Gnome). 

My problem was that when I installed the nvidia-glx package from Synaptic it switched my kernel on me to a i386 one, which DOES NOT support dual core. 

The solution was to follow the advice given in a LunaPark entry and to use Envy to automatically install the nvidia drivers. I saw a HUGE performance increase when I did this, and envy also uninstalled the old nvidia drivers as well.

I wrote my experience here: [Installing nVidia drivers on an AMD 4200+ Dual Core with Envy](http://www.xenocoder.com/blog/archiveposts/52) which was really me following what I read here: [Envy - Easy Way To Install Nvidia Drivers in Ubuntu](http://lunapark6.com/?p=2717) 

I take no credit for this besides just wanting to pass along information that worked for me! I am pasting what I did below but I would really check out the article as there is a cool interview with the guy that wrote the program envy as well.

If it doesn't work post back and maybe we can figure out more? I don't claim to know much but since I just had to suffer through this and the horror is fresh in my mind maybe I can spare you some time lol.

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu1_all.deb

sudo dpkg -i  envy_0.8.1-0ubuntu1_all.deb

then press Alt+Cntrl+F1 to kill X-Windows and type

envy

at the terminal. From there press a few “Yes” and you have the latest stable Nvidia drivers installed on your computer. The program even brings you back into X-Windows. Envy is one very sweet script. The author of the program is Alberto Milone, better known as tseliot in the Ubuntu Forums. He was nice enough to answer to some questions on Envy, as well Ubuntu. Click the read the rest of the entry for his answers…

*Note for users of previous Envy versions you should first do these two steps before the installation of version 0.8.1

sudo aptitude purge envy

sudo rm -R /usr/share/envy
```

---

### Post by Footer on 2007-01-27
WOW!  Amazingly simple!  envy is simply amazing!!!  And I did read the LunarPark interview with tseliot.  Thanks to Alberto for helping make Linux (and Ubuntu) a more enjoyable experience!  That was slick.  The nVidia X server settings now show everything properly and even my FP monitor was detected correctly.  So sweet ...  :D

And thanks for answering the dual core question ... I feel like an idiot.  :)

Rock on K(U)buntu!

---

### Post by 454redhawk on 2007-01-27
> **Footer said:**
> 

AMD dual core -- but am I using both?



```
cat /proc/cpuinfo
```

---

### Post by Footer on 2007-01-27
> **454redhawk said:**
> ```
cat /proc/cpuinfo
```

Yup.  And this works as well:

```
more /proc/cpuinfo
```

both of which show the two processors.

---

### Post by ehowell on 2007-01-27
Never feel like an idiot! It was a good question to ask as I had to dig around myself for the answer, so hopefully now this will be in place for the next person who has the same question!

Glad it worked out for you, not having to muck around from source files to get things working means that I am more productive, which is a good thing!

---

### Post by Footer on 2007-01-28
I hear you!  I'm sure the answer was out there somewhere but when I really get stuck, I always turn to these forums where you guys rock!

Tell you what, I'm very impressed with this 64bit version of Kubuntu Edgy.  It hasn't been near as buggy for me as the 32bit version and you've gotta love the speed!  Now I just need to find a Superkaramba widget to mointor CPU temps and other settings ... Striking out so far but haven't really looked all that much ... Perhaps I'll start another thread on that subject.

Thanks again for your help with the nVidia drivers ehowell!  That saved me a ton of time & frustration!

:)

---

### Post by Kilz on 2007-01-28
> **ehowell said:**
> Never feel like an idiot! It was a good question to ask as I had to dig around myself for the answer, so hopefully now this will be in place for the next person who has the same question!

That will never happen. People dont know what a search is. They just post new questions.

[http://www.ubuntuforums.org/showthread.php?t=167732&highlight=smp](http://www.ubuntuforums.org/showthread.php?t=167732&highlight=smp)
[http://www.ubuntuforums.org/showthread.php?t=221744&highlight=smp](http://www.ubuntuforums.org/showthread.php?t=221744&highlight=smp)
[http://www.ubuntuforums.org/showthread.php?t=270047&highlight=smp](http://www.ubuntuforums.org/showthread.php?t=270047&highlight=smp)
[http://www.ubuntuforums.org/showthread.php?t=260893&highlight=smp](http://www.ubuntuforums.org/showthread.php?t=260893&highlight=smp)
[http://www.ubuntuforums.org/showthread.php?t=243185&highlight=smp](http://www.ubuntuforums.org/showthread.php?t=243185&highlight=smp)

---

### Post by Footer on 2007-01-28
Ahh, but that's an old thread (we're talking Edgy now).

uname -a says this on my system:

[INDENT]Linux kubuntu64 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux[/INDENT]

But I'm confused in that thread by this:

[INDENT]"I noticed that the X86_64 kernel only runs one CPU."[/INDENT]

in the posters original question.

I'm running x86_64 but it's SMP and so using both processors?  I'm afraid if I would have found this thread first, I still would have posted my question.

:)

---

### Post by Kilz on 2007-01-28
> **Footer said:**
> Ahh, but that's an old thread (we're talking Edgy now).

uname -a says this on my system:

[INDENT]Linux kubuntu64 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux[/INDENT]

But I'm confused in that thread by this:

[INDENT]"I noticed that the X86_64 kernel only runs one CPU."[/INDENT]

in the posters original question.

I'm running x86_64 but it's SMP and so using both processors?  I'm afraid if I would have found this thread first, I still would have posted my question.

:)

Thanks for proving my point. People dont care that the answer is in the past. They will "I'm afraid if I would have found this thread first, I **still would have posted my question.**"

I linked in numerous posts. But to tell the truth there were 3 pages of results I could have linked in. The reason is you may find a problem with one. But each post says the same thing. They give the same answers. Just like you got in this post, the same answer. People dont look for past results, they just ask the same question over and over again.

---

