---
title: "emifreq powernowd cpufreq and athlon64 laptop running i386"
date: 2005-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by wbeck85 on 2005-04-08
Today, for some reason, Powernowd decided to stop running and my processor decided to just run at full speed constantly. I dont knwo how this happened, why this happened, or what I did to make it happen - i dont think i did anything. It just seemed to stop. the Cpu frequency monitor applet said the thing was running at 2ghz constantly. I thought some weird process might be running wild in the background, and i rebooted, since i am relatively new to this OS and didnt know how to find one runnaway process. Once back to the desktop, the applet still said it was at 2ghz.
So i reintalled Powernowd with synaptic. It didnt seem to do anything. Still the computer clocked at 2ghz.  I rebooted. 2ghz. I uninstalled powernowd, installed cpufreq and emifreq with hopes to control my cpu frequency from the emifreq applet. I then rebooted and got this when trying to load the emifreq applet:

"Backend initialization error.

The applet didn't manage to find CpuFreq support in the sysfs. You need your kernel to have built-in support for CpuFreq or use the module corresponding to your processor type in order to run this applet."

What does this mean? Powernowd was working fine earlier. So i thought that CpuFreq would already be enabled. And i installed CpuFreq from synaptic, so shouldn't the right module be working? What do I need to do to get this thing clocking the way I like?

And another thing: Is there a way to control voltages independant from frequency. In windows, there is this killer app called CrystalCPUID which allows me to lower my voltages, resulting in a cooler laptop than witht the factory defaults.  Is there something similar in linux?

I have an AMD Athlon 64 3200+ DTR (Desktop Replacement) processor in my Sager np4750 laptop. How do I get this stuff to work right?

---

### Post by soul_rebel on 2005-04-08
sudo /etc/ininit.d/powernowd restart

And post any output

---

### Post by wbeck85 on 2005-04-08
THankyou, it seems too be working now.

wbeck85@ganganork:~$ sudo /etc/ininit.d/powernowd restart
Password:
sudo: /etc/ininit.d/powernowd: command not found
wbeck85@ganganork:~$ sudo /etc/init.d/powernowd restart
/etc/default/powernowd: line 1: unexpected EOF while looking for matching `"'
/etc/default/powernowd: line 2: syntax error: unexpected end of file
/etc/default/powernowd: line 1: unexpected EOF while looking for matching `"'
/etc/default/powernowd: line 2: syntax error: unexpected end of file
 * Stopping powernowd:                                                   [ ok ]
 * Starting powernowd...                                                 [ ok ]
wbeck85@ganganork:~$

It seems to work now. I am at 800 mhz :) thank you

---

### Post by soul_rebel on 2005-04-09
check this file for errors:
/etc/default/powernowd
or delete powernowd COMPLETELY and try to reinstall it. Be sure that /etc/default/powernowd is deleted before reinstall.

---

