---
title: "Random full system freezes..."
date: 2009-08-04
forum: x86 64-bit Users
---

### Post by Topher88 on 2009-08-04
Several times since I have installed Ubuntu Studio on my new laptop, it has randomly frozen.  During these freezes, the mouse and the keyboard are un-responsive and I am forced to hold down the power button and restart the machine.  It always happens at a random times, too; it happened once while opening a folder, once while surfing the internet, once while installing updates, and one time it even happened at the login screen right after booting up!

I thought about reverting to regular Ubuntu, but i guess that wouldn't really matter since they're both practically the same except Studio has added specs...  Any ideas as to why this is happening??

---

### Post by Jaesin on 2009-08-04
check desktop effects.  causes my system to freeze as well.

---

### Post by Topher88 on 2009-08-05
Ok well, here's a quick Q:  I had assumed that reverting back to regular Ubuntu Jaunty would likely not fix the problem.  Am I correct in thinking this, or could there possibly be just a problem with studio that's causing this?  Frankly, I wouldn't mind reverting; Studio has been nothing but trouble for me.  I am willing to work through it, but it's kind of hard when I keep experiencing these crashes and I never know when another one will strike...

---

### Post by snowpine on 2009-08-05
Have you tried using the linux-generic kernel instead of linux-rt? You can easily test the generic kernel (install it from Synaptic) without completely reinstalling. I like the idea of the real time kernel, but have found it a bit buggy on my hardware.

---

### Post by Topher88 on 2009-08-05
> **snowpine said:**
> Have you tried using the linux-generic kernel instead of linux-rt? You can easily test the generic kernel (install it from Synaptic) without completely reinstalling. I like the idea of the real time kernel, but have found it a bit buggy on my hardware.

Thanks I'll try that!

---

### Post by Topher88 on 2009-08-05
Well, the installation ran seamlessly, and so far no lockups, but...  It seems to have totally removed support for my wireless card.  In the previous kernel, it was running propriety drivers, but now when I look in Hardware Drivers, it's no longer there.  Wireless is no longer an option in Network Manager.

---

### Post by snowpine on 2009-08-05
Glad it's working better!

Wireless should be an easy problem to fix. You probably just need the appropriate module for your new kernel. The terminal command 'lspci' will tell you exactly which wireless chipset you have, then the search command will help you find the solution. One possibility that often works for me is to install the linux-restricted-modules package.

---

### Post by Topher88 on 2009-08-05
Alright, sweet.  Download the restricted modules package and everything is in the order it was before.  However, as noted in [this thread]("http://ubuntuforums.org/showthread.php?p=7739244#post7739244"), my wireless wasn't working properly before and still isn't after the kernel switch.

---

### Post by Topher88 on 2009-08-06
Well, anyway...  Ben running Ubuntu in the Generic kernel all day and not a single freeze.  Thanks for the suggestion.

Just curious...  What's the key difference between the RT kernel and the generic?

---

