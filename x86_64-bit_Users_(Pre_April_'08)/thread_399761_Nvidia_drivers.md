---
title: "Nvidia drivers"
date: 2007-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sammyd253 on 2007-04-02
Hey guys, I have an SLI setup in my main rig and have already checked Nvidia's main page to confirm that my video cards are supported.

Basically what I want to be able to do is enable SLI in Ubuntu (64 bit).  Is it smarter to grab the installer off of Nvidia's site or grab a package from a repository?

---

### Post by kleeman on 2007-04-02
Use the packages (nvidia-glx and linux-restricted-modules) and then follow these instructions to enable sli:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/README/appendix-w.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/README/appendix-w.html)

---

### Post by sammyd253 on 2007-04-03
Sounds good.  Will this work in the newest version of Ubuntu (Fiesty)?

Also, what's a good way to test if SLI is giving me a performance increase?
(glxgears, UT2004)?

If UT2004 is a good test, is there any way I can monitor frame rates within this game?

---

### Post by StandardBlueCaboose on 2007-04-04
Glxgears is [not a benchmark]("http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark"), but you might as well run it for giggles.

You can run UT2004, and if you notice a difference, then that's swell.

---

### Post by sammyd253 on 2007-04-04
Thanks... 

btw, 1950 called, they want their words back ;-)

---

### Post by artisan002 on 2007-06-26
> **kleeman said:**
> Use the packages (nvidia-glx and linux-restricted-modules) and then follow these instructions to enable sli:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/README/appendix-w.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/README/appendix-w.html)

So, I needed the same info as this guy (dual GeForce 7300 GTs on 32 bit Kubuntu).  I followed what you said and got nothing but a black screen with a blinking cursor (no response to commands, either) after the usual nifty splash page.  Powered down, pulled the second card, fired back up and got the same big screen of nothing.  Any alternate suggestions..?

---

