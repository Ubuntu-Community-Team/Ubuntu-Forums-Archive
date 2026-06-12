---
title: "Where is the kernel source located ?"
date: 2007-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Biased turkey on 2007-02-11
I just typed the words " kernel source " in the search  options and all it returns is such stuff like "What advice would you give to women who think Linux is "hard"?  "
I have  the AMD 64 version of Ubuntu 6.10
uname -r gives : 2.6.17-10-generic.
I would like the kernel source just to try  to recompile the kernel, without modifying anything, just to see if I can do it.
I didn't even find anyrelevant  topic in the FAQ.
Tia for any help.
B.T.

---

### Post by Rui Pais on 2007-02-11
try the words **Master kernel** in the search field :)

here a wiki entry for the subject:
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

---

### Post by Biased turkey on 2007-02-11
Thanks a lot for taking some of your time to reply Rui Pais

For sure I bookmarked the link you mentioned.

From the wiki page:

"You got to this page by mistake, but checked it out because it looked interesting. Believe me, this isn't interesting at all  :) 
lol

---

### Post by Rui Pais on 2007-02-12
hi, no problem :)

well,
about that line... usually kernel compilation is not need for normal users, yes... ubuntu one works...
but theres more then that:

Ubuntu have a long tradition on using old kernels. 
On contrary to the rest of the distro, they upgrades sometimes broke things (latest is was one of those cases:()
You may need some features that only exist in more updated kernels. Either hardware (like latest wireless cards, some usb adsl modems, etc.) as software (suspend2, experimental schedulers, reiser4, etc).
You may need to build some stuff "inside" kernel instead as module (some hardware problem can be solved that way).
You may want to specify your specific cpu and optimal options/patchs instead of default arch and conservative options...

When you compile your one and give an careful look on default options of ubuntu kernels, you'll see they enabled almost everything on it. 
They are suppose to be generic, of course, but there is stuff there that only a very small group of people will need - scientific instrumentation, led stuff, video editing, highend/highspeed networks, kernel debugging, bizarre OS support, (do you really need the abilitty to mount Amiga, sco or plan9?;)), etc. 
And there is a lot of things marked as 'Experimental'  or 'You should only choose this if you really know what you are doing' enabled as default.

Besides compiling is a good exercise. You will end up understand better your hardware and eventually learn a few thing on how linux kernels work. It's, too, a very safe experiement, cause, contrary to most of the software, you can have as many kernels as you desire side-by-side, so one can be as wild as he/her wish, and it the result is a broken kernel it only needs to reboot a choose the previous working one or the default one. Compiling a kernel will not remove the default ubuntu kernel :)


Another thing. The wiki is not as informative as the thread i suggest you look for. don't forget to check it:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

have fun

---

### Post by Biased turkey on 2007-02-15
Thanks for detailing the multiple reasons for compiling the kernel.
I just want to try it, and at the same time trim some fat and features of the kernel almost no one is using.
I might need the ability to mount Amiga  filesystems, I expect to install UAE the Amiga emulator  :)

---

### Post by wesley_of_course on 2007-02-18
Wesley here ; 

Google Linux  :  [http://www.google.com/linux?hl=en&q=kernel+source&btnG=Search](http://www.google.com/linux?hl=en&q=kernel+source&btnG=Search)

  Hope it helps  .   [http://www.google.com/linux](http://www.google.com/linux)

Ubuntu Documents , first choice .

---

