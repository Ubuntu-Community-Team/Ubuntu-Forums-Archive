---
title: "CPU Frequency drops too much on battery power"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by ShokTHX on 2009-04-30
My CPU frequency drops to 800Mhz when I run on battery. At that setting, I can't really use the computer.
I've added the CPU frequency scaling monitor and I can get it to run faster briefly but then it will drop down again. It seems to bounce up to higher clock rates occasionally but mostly stays down at 800.
It seems to want to run at the Ondemand setting and then does not notice the actual load and clocks down.
Only happens like this on battery power but I am tired of plugging in every time I need to use the computer.

Any suggestions? Is there a threshold setting somewhere that could be tweeked?

I using an HP DV8000 laptop with an AMD 2.0Ghz Turion64.
Currently runnning Jaunty 64 AMD but had the same problem with Intrepid AMD 64. Jaunty seems to be a little better (it bounces up where Intrepid seemed to stay at 800.

James

---

### Post by squaregoldfish on 2009-05-01
If you look in /sys/devices/system/cpu/cpu0/cpufreq, you'll see all sorts of bits and pieces relating to frequency scaling.

If you look in scaling_available_frequencies, you'll see a list of the frequencies supported by your processor. Choose one of them, and set that to the minimum frequency by calling:

```
echo [freq] > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
```

as root (note that you can't sudo this command!)

You can put the above line in your /etc/rc.local file to have it set every time you boot.

Another thing you might want to try is to set the CPU usage threshold at which the processor speed ramps up:

```
echo 40 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
```

Will ramp up the processor speed as soon as it reaches 40% usage.

Steve.

---

### Post by ShokTHX on 2009-05-01
I'm not sure how to access using root.
I can see the files right now, but I cannot even open them to read them - I get "unexpected error -no such device."

It makes sense since I am not root but how do you check them as root?
It looks like this is where I need to go to fix this.

Thanks
James

---

### Post by miegiel on 2009-05-01
> **ShokTHX said:**
> I'm not sure how to access using root.

go root```
sudo su
```exit root```
exit
```

---

### Post by ShokTHX on 2009-05-01
I still get "Error-No such device"
James

---

### Post by ShokTHX on 2009-05-03
My rc.local file has nothing other then the description in it right now.
How can I check what the other files say without getting the error above?

James

---

### Post by Yellow Pasque on 2009-05-03
Do you have cpufreqd installed? If so, you can control it with /etc/cpufreqd.conf

I guess another possibility is an ACPI/BIOS issue. Updating the BIOS may help that.

---

### Post by aakhil536 on 2009-05-05
i ALSO HAVE THE SAME PROBLEM......MY BATTERY DISCHARGES VERY FASTLY....


HP DV5
AMD 64 TURION

---

### Post by Yellow Pasque on 2009-05-05
> **aakhil536 said:**
> i ALSO HAVE THE SAME PROBLEM......MY BATTERY DISCHARGES VERY FASTLY....


HP DV5
AMD 64 TURION
That would be the opposite of what the OP is reporting..

---

### Post by BrainwreckedTech on 2009-05-29
The Jaunty testers had a discussion about this problem here: [http://ubuntuforums.org/showthread.php?p=7035125](http://ubuntuforums.org/showthread.php?p=7035125)

In there you'll find that Jaunty ups the threshold for bumping up the CPU frequency to 95% (!!!) by default.  They also posted a quick fix.

Apparently this is affecting quite a few people.  I just stumbled upon this problem tonight and suddenly everything makes sense.  This is probably why my dedicated Boxee box is having such a hard time with CBS's 720p programming, why I frequently saw no bump in CPU frequency on said box in Gnome's CPU monitoring applet when I first went the full desktop route, why my desktop's CPU fan is no longer spinning up with YouTube-based flash overdoses, and why my desktop gets cases of the herky-jerkies when I had none before.

---

