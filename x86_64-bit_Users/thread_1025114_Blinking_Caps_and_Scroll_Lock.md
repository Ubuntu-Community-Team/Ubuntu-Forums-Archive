---
title: "Blinking Caps and Scroll Lock"
date: 2008-12-29
forum: x86 64-bit Users
---

### Post by CaughtDemon on 2008-12-29
Something really bad happend to me :(

Something got stuck in the processor's cooler and broke it. I turned it off and put another cooler.
Now, when I boot, the progress bar get stuck in the middle and my Caps Lock and Scroll Lock starts blinking.
I've found it means 'kernel panic', but what causes it? How can I fix it?

I tried to run Live CD too and it does the same thing at the same stage. Same happens with recovery mode.

Some further considerations:
1. I don't have wireless, so it's NOT a wireless issue, like I heard out there
2. It's not overheat either, cause when I boot into the Windows partition, I could still play games with full acceleration and it doesn't fry the hell out, so... if it doesn't happen to windows, it's only related to ubuntu, so, no overheat issue
3. My whole hard-disk can be mounted and it's readable [or not]
4. I use Ubuntu 8.04 64bit, Live CD was 7.10, I don't think it is relevant
5. It's a Dual Core 2x 64bit 2.80GHz clock with 2GB ram and 250GB HardDisk and ATI and OnBoard ethernet port [USB mouse and PS/2 keyboard]

Anybody could help me? I'm avaiable for any question you guys need to find a solution for that
thanks

---

### Post by dcstar on 2008-12-29
> **CaughtDemon said:**
> Something really bad happend to me :(

Something got stuck in the processor's cooler and broke it. I turned it off and put another cooler.
Now, when I boot, the progress bar get stuck in the middle and my Caps Lock and Scroll Lock starts blinking.
........

Chances are you have cooked your CPU. Linux pushes your hardware more than Windows (esp 32-bit Windows) so the latter working may not be a valid test, try a Live Ubuntu CD.

---

### Post by CaughtDemon on 2008-12-30
Live CD does the same, as described in the first post.

If my CPU cooked, why does windows use the same 'cooked' hardware and still works? I don't think any level damage on hardware would just affect Linux, but not Windows, in this kinda way

---

### Post by Yellow Pasque on 2008-12-30
> If my CPU cooked, why does windows use the same 'cooked' hardware and still works?
It's possible that physical damage occurred to a part of the processor that only affects x86-64 operation (like a 64-bit register or ALU). This sounds kind of unlikely, but I could actually see it happening since most of the CPU die area is taken up by L2 and/or L3 cache and power consumption (and heat generation) is probably greater in the small amount of the die devoted to actual "processing" I suggest trying a 32-bit Ubuntu Live CD to see if it works.

---

### Post by thschiavo on 2008-12-30
Uau, this is quite interesting for me. Look... If you cooked your CPU, it's too bad. You have nothing to do right now.

But, let's go straightforwad. Your live CD isn't running, right? So, it's not a problem in your file system. There's something Linux cannot deal with.

I didn't know Linux pushs harder than Windows (of course, considering the most general case), but if it's the case... Why not trying a lighter version? If you can find any light linux to try it, you could easily find if it's because Linux pushs harder than Windows your hardware or if it's the case of a problem Windows can deal with, but Linux don't. And, please, reading the post above mine, consider also using a i386 version of your linux.

I think this is the most natural thing to do, but it means also a lot of work to do. Let's wait a little for other answers.

---

### Post by CaughtDemon on 2008-12-30
I'll simply try the Ubuntu 7.10 32bit Live CD and see what happens...

I get back with an answer in a few hours, thanks

---

### Post by linux_tech on 2008-12-30
maybe the new cooler is incorrect?

---

