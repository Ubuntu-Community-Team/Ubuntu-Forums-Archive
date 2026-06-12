---
title: "Processor Affinity"
date: 2007-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Death_Sargent on 2007-03-15
Is there a way to specify which CPU a program is using and/or set which it will use.

There was something similar that i found on the AMD forums under the name "Program To Set Affinity" and it was effective in both permanently assigning affinity as well as using a tray task so no permanent change would have to be made.

Some of the features are not 100% necessary but it would be nice to have a way to make it so my programs don't just bounce between processors.

---

### Post by koshcu on 2007-03-16
The kernel will already take care of things like this. Processes will tend to stay on a single processor unless the processor is busy and it can be handed to another one with less overhead then waiting for the current process to finish. I have 4 cpu cores and I already see certain processes tending to stay on certain cores but if I run very cpu intensive tasks other tasks will migrate over time to less busy cores.

So in general don't worry about it and let the kernel do its job.

---

### Post by JackandJohn on 2007-12-03
This is one of those disturbing trends that I have been seeing all over the internet; noone knows, and then someone responds in a way that seems to imply that the question should not be asked.

ALL questions deserve to be asked, even if they should usually ask a search engine first ;)

Here is what I have on this issue so far:

There is a program installed in Ubuntu (default with the minimal install) called "taskset"

You SHOULD be able to run a command like
taskset -c <core#> -p <process ID>

However, I am in 7.10 and I cannot run this successfully, getting either

```
#:~$ taskset -c 2 -p 6721
sched_setaffinity: Invalid argument
```

or```

# taskset -c 0 -p 6721
execvp: No such file or directory
failed to execute -p
```
(Which is fine since I don't think c 0 is valid)

I would really like the ability to automatically set a process to a core, even though the kernel is pretty good at it, some apps break the mold.

I will attempt to update this as I research.

---

### Post by John Jason Jordan on 2007-12-03
> **JackandJohn said:**
> There is a program installed in Ubuntu (default with the minimal install) called "taskset"
You SHOULD be able to run a command like
taskset -c <core#> -p <process ID>
However, I am in 7.10 and I cannot run this successfully, getting either
```
#:~$ taskset -c 2 -p 6721
sched_setaffinity: Invalid argument
```
or```

# taskset -c 0 -p 6721
execvp: No such file or directory
failed to execute -p
```
(Which is fine since I don't think c 0 is valid)
I would really like the ability to automatically set a process to a core, even though the kernel is pretty good at it, some apps break the mold.
I will attempt to update this as I research.
If and when you come up with something, please report back.

I have a bluetooth mouse and a bluetooth headphone. I have both working fine in Gutsy x86_64, but when using the headphones they cut out occasionally when I move the mouse. I probably can't do this, but it would be cool to assign each to one of my dual core CPUs. Unfortunately, they are probably controlled by the same utility, but I'd still like to see what you come up with.

---

### Post by JackandJohn on 2007-12-03
Update: I found that I was able to set the affinity with this command when I was first launching an app, just not when it was already running.
I used this to modify the startup command of one of the resource-intensive gnome panel applets.



John Jason Jordan:

 I'm not sure if you can separate the mouse and headset in the system, but try it out; dig and you might find it.
 You may want to play with this command, as well as the "nice" command (you can also modify the "nice" value for a process with the System Monitor)

---

### Post by mellowd on 2007-12-03
> **John Jason Jordan said:**
> If and when you come up with something, please report back.

I have a bluetooth mouse and a bluetooth headphone. I have both working fine in Gutsy x86_64, but when using the headphones they cut out occasionally when I move the mouse. I probably can't do this, but it would be cool to assign each to one of my dual core CPUs. Unfortunately, they are probably controlled by the same utility, but I'd still like to see what you come up with.

I doubt having a core each working on one of these will make any difference. More likely this problem is called by inteference

---

### Post by John Jason Jordan on 2007-12-03
> **mellowd said:**
> I doubt having a core each working on one of these will make any difference. More likely this problem is called by inteference
I'm not saying you're wrong - I know next to nothing about how these things work. But I do know that each device has its own address and the computer will not talk to a device until it has been paired up with the device at its specific address. I know this because I had to return my first DR-BT50 headphones and get a different pair. I got no sound until I edited the .asoundrc file and put in the address of the new headphones. I also know that my bluetooth mouse has its own address. If the computer sends signals to the specific address, there should be no interference, right?

I suppose I need to start by finding out exactly what utility or module is responsible for sending data to bluetooth devices.

---

### Post by mellowd on 2007-12-03
> **John Jason Jordan said:**
> I'm not saying you're wrong - I know next to nothing about how these things work. But I do know that each device has its own address and the computer will not talk to a device until it has been paired up with the device at its specific address. I know this because I had to return my first DR-BT50 headphones and get a different pair. I got no sound until I edited the .asoundrc file and put in the address of the new headphones. I also know that my bluetooth mouse has its own address. If the computer sends signals to the specific address, there should be no interference, right?

I suppose I need to start by finding out exactly what utility or module is responsible for sending data to bluetooth devices.

There shouldn't be. Bluetooth uses radiowaves though. The fact that your headphones cut out when the mouse is moved leads me to believe the problem lies somewhere here. I don't have a similar setup so I can't really say for sure. Are they from the same manufacturer? If so, have you checked with their support to see if other people are experiencing the same sort of problem?

---

### Post by jpkotta on 2007-12-03
koshcu is absolutely right.  Do not worry about it.  You *may* be able to make things run better if sit there tweaking things, but the gain will be small for the effort you'll put in.  The utility to set affinity is for people who need to squeeze every ounce of preformance out of their machines -- they have run out of other options.  

The bluetooth problems are not caused by the CPU.  Think about it: your dual core computer can't keep up with a mouse and headset?  Meanwhile, they talk to the computer over a shared medium (radio waves).  It is interference.  The fact that they have separate addresses means that when they talk they can be distinguished, not that they won't trample all over each other's messages.  

Bluetooth is handled by the bluez subsystem in Linux, down in the kernel, so you can't even use that affinity utility on it.  You will be better off starting your own thread about your bluetooth problem so bluetooth-aware people can help (I am not one of them unfortunately).

---

### Post by JackandJohn on 2007-12-04
Just to throw this in here, because all questions deserve to be asked:

 I have a bluetooth audio gateway, and I know that when I do something cpu intensive, the audio will cut out or clip. Especially annoying when attempting to watch 1080p.

Granted, this experience is in OSX 10.5, but this leads me to assume that bluetooth is routed through the kernel, and is affected by cpu latency.



Granted; it may definitely be an interference issue (bluetooth uses a small set of frequencies in the 2.4Ghz range, which means that your devices are clustered in the same frequencies as 802.11b/g, and most wireless phones), but we cannot discount a cpu-related issue. It's at least worth testing, which is my original statement

---

### Post by JackandJohn on 2007-12-04
> **jpkotta said:**
> 
The bluetooth problems are not caused by the CPU.  Think about it: your dual core computer can't keep up with a mouse and headset?

Not quite a valid argument; we are hypothesizing about cpu/bus latency, not power.
Case in point; I found this thread because I am abusing the gnome link-monitor applet; it's pinging 50 hosts every second, and uses about 10% of one core.

Obviously my system can keep up, right?

However, when link-monitor and xgl/compiz share the same core, I get window stutters and visual annoyances; It's not that my system cannot keep up (cpu never goes above 40%), it's that both things need the resources "NOW" (latency vs power).

After moving link-monitor to the second core, I have no more visual stutters.

---

### Post by John Jason Jordan on 2007-12-04
> **JackandJohn said:**
> Not quite a valid argument; we are hypothesizing about cpu/bus latency, not power.
Case in point; I found this thread because I am abusing the gnome link-monitor applet; it's pinging 50 hosts every second, and uses about 10% of one core.
Obviously my system can keep up, right?
However, when link-monitor and xgl/compiz share the same core, I get window stutters and visual annoyances; It's not that my system cannot keep up (cpu never goes above 40%), it's that both things need the resources "NOW" (latency vs power).
After moving link-monitor to the second core, I have no more visual stutters.
I am not sure who is right - whether it is interference or CPU bottleneck. But I can add one more data point to consider. I have bluetooth on my laptop (which is where the cutting out occurs if I move the  bluetooth mouse while listening to the bluetooth headphones), and I also have a bluetooth transmitter for my iPod. I can use the headphones to listen to the iPod and the sound never cuts out when I move the mouse. If both devices are using the same frequency, then the cutting out cannot be due to frequency interference.

---

### Post by JackandJohn on 2007-12-04
John Jason Jordan:
 Quick question;Can you watch the processes in 'top' (shell command), or system monitor and see if there is any type of spike in a process when the audio cuts out?

Just a hunch; and I noticed that that is one way that I can tell when mine cuts out (every computer I work on has a cpu meter on all the time). It doesn't have to get to 100% or anything, just if there's a little spike.

---

### Post by picopir8 on 2007-12-04
> **John Jason Jordan said:**
> I am not sure who is right - whether it is interference or CPU bottleneck. But I can add one more data point to consider. I have bluetooth on my laptop (which is where the cutting out occurs if I move the  bluetooth mouse while listening to the bluetooth headphones), and I also have a bluetooth transmitter for my iPod. I can use the headphones to listen to the iPod and the sound never cuts out when I move the mouse. If both devices are using the same frequency, then the cutting out cannot be due to frequency interference.

Not exactly.  There are are several iterations of the bluetooth standard.  Devices that use the older standards will not have as robust error correction or frequency hopping so they are more prone to errors.  Two bluetooth devices will always drop down to the highest standard supported by both devices.  So the headphones could work great when connected when connected to one device and be more susceptible to interference when connected to another.

Since the headphones are the device that is prone to error, keep those connected to the computer and try using the bluetooth mouse on a different computer and see if you still have problems.  If you do then it is the channel between the headphones and your computer.  Perhaps getting a new bluetooth transmitter/receiver would solve the problem.

If the problem goes away then it is most likely not the wireless channel and it is something in the computer.  But I seriously doubt it is any sort of CPU bottleneck.  My gut feeling is that either the bluetooth modem or the driver is struggling with simultaneous channels that require real time signaling.  A newer bluetooth transmitter/receiver that supports the lastest standards would have a more robust modem.  If the driver is struggling it could be due to coding limitations or resource limitations.

---

### Post by John Jason Jordan on 2007-12-04
> **JackandJohn said:**
> John Jason Jordan:
 Quick question;Can you watch the processes in 'top' (shell command), or system monitor and see if there is any type of spike in a process when the audio cuts out?

Just a hunch; and I noticed that that is one way that I can tell when mine cuts out (every computer I work on has a cpu meter on all the time). It doesn't have to get to 100% or anything, just if there's a little spike.
I just performed this test, but I didn't see anything that stood out as remarkable. I used both top and System Monitor, but I couldn't figure out what top was displaying, so the following comments are from what I saw in System Monitor.

While playing an MP3 with Exaile to the bluetooth headphones I moved the  mouse around at random and did miscellaneous clicks and movements with the scroll wheel. One thing I noticed was that just moving the pointer around did not generally cause a sound interruption, but a click did about a third of the time. However, movement alone did sometimes cause a sound interruption if I moved the pointer over something clickable - e.g., a button. Furthermore, a click on the Gnome panel to minimize or restore a running application window would cause an interruption in the sound about 80% of the time. Furthermore, that particular activity caused CPU2 to go to 50% or so. Nothing else ever got either CPU over about 25%.

So yes, it appears that it is cutting out when there is a spike, particularly a spike in CPU2. In fact, CPU1 did not spike nearly as much as CPU2. It strikes me as odd that neither CPU got over 50%, yet sound was cutting out on a spike.

I also have a little CPU frequency applet in my Gnome panel. It displays 800 MHz - 1.2 GHz - 2.0 GHz depending on how much the CPU is being used. However, I think it monitors only one core. I notice that it frequently goes to 2.0 GHz even though System Monitor never goes above 50%. Just playing an MP3, even without the bluetooth headphones, tends to make it hover back and forth between 1.2 and 2.0 GHz.

I don't know what any of this means.

---

### Post by John Jason Jordan on 2007-12-04
> **picopir8 said:**
> Not exactly.  There are are several iterations of the bluetooth standard.  Devices that use the older standards will not have as robust error correction or frequency hopping so they are more prone to errors.  Two bluetooth devices will always drop down to the highest standard supported by both devices.  So the headphones could work great when connected when connected to one device and be more susceptible to interference when connected to another.

Since the headphones are the device that is prone to error, keep those connected to the computer and try using the bluetooth mouse on a different computer and see if you still have problems.  If you do then it is the channel between the headphones and your computer.  Perhaps getting a new bluetooth transmitter/receiver would solve the problem.

If the problem goes away then it is most likely not the wireless channel and it is something in the computer.  But I seriously doubt it is any sort of CPU bottleneck.  My gut feeling is that either the bluetooth modem or the driver is struggling with simultaneous channels that require real time signaling.  A newer bluetooth transmitter/receiver that supports the lastest standards would have a more robust modem.  If the driver is struggling it could be due to coding limitations or resource limitations.
That is very interesting. Unfortunately, I cannot perform the test because I do not have another computer with bluetooth.

As for the components, the headphones are Sony DR-BT50 which are fairly new on the market and they use A2DP. The mouse is a Logitech V270 and I have no idea what protocol it uses - google didn't help me find out anything about it.

Another interesting thing is the lspci did not list any bluetooth devices in the computer. However, Blueman says it is:

Bluetooth version: Bluetooth 2.0 + EDR
Revision: 43.65 / 211
Manufacturer; Broadcom Corporation
Major class: computer
Minor class: laptop

The computer is a Thinkpad T61, which is also relatively new on the market, and mine is only a couple months old.

---

### Post by pondochris on 2007-12-04
> **JackandJohn said:**
> Update: I found that I was able to set the affinity with this command when I was first launching an app, just not when it was already running.
I used this to modify the startup command of one of the resource-intensive gnome panel applets.



John Jason Jordan:

 I'm not sure if you can separate the mouse and headset in the system, but try it out; dig and you might find it.
 You may want to play with this command, as well as the "nice" command (you can also modify the "nice" value for a process with the System Monitor)

what are the commands you are referring to?  Do you mean the ones in your first post?  Please let me know as I have been having trouble with some games un-maximizing and freezing up and I think it may be due to being bounced between processors.
  The reason I think this is because I recently installed the Beyond The Red Line demo and in the readme it says I may have graphics problems if I don't set my processor affinity to use only one core.

Thanks.

---

### Post by Jouke74 on 2007-12-05
> **John Jason Jordan said:**
> 
I also have a little CPU frequency applet in my Gnome panel. It displays 800 MHz - 1.2 GHz - 2.0 GHz depending on how much the CPU is being used. However, I think it monitors only one core. I notice that it frequently goes to 2.0 GHz even though System Monitor never goes above 50%. Just playing an MP3, even without the bluetooth headphones, tends to make it hover back and forth between 1.2 and 2.0 GHz.

I don't know what any of this means.

Let me help.

First, there used to be a utility called "schedutils" which you could use to assign the affinity up to Ubuntu 7.04. However with the new Kernel this utility does not want to work anymore, as it is replaced by taskset I think. Taskset is pointed out in the second or third post here. Take note that trying to install the "schedutils" utility will remove other "core" utilities including taskset (last time I tried) and will screw current Ubuntu (I think). 

Second, the problem with your CPU might be that it is using CPU frequency scaling. The CPU will increase the frequency when required. Hence you will see it going from 800 mhz doing little until 2.0 Ghz if you do some heavy work. However this also takes processing power, and may cause hick-ups in games sometimes as I have noticed. At my computer it seems to flip up and down all the time as soon as I start something (AMD X2). I got tired of the small delays and frequency flipping so I disabled CPU frequency scaling (aka cool n' quiet).
You can do this by removing CPU frequency scaling from the startup "sessions ". You can also get rid of it permanently by disabling cool n quiet (or intel deriviate) in the BIOS.
Mind that your CPU frequency will not scale down to 800 Mhz anymore, so you will use more energy (=less battery life) and CPU will get a tad warmer.

Third, the CPU frequency scaling is done by adjusting the motherboard multiplier of both CPU cores. Thus the scaling is always done on both cores simultaneously (unless you a currently unreleased AMD quadcore which can do each core separately). Therefore it is also not required to see the scaling graphs of both cores. If you would show these graphs it would show the same.

Fourth, the system monitor show the total load of your processor, with both cores. Therefore if it shows 50% then one core is being fully utilized for one process. With 100% you have two cores running full time. Processes, unless programmed to otherwise, will only use a single thread for things and use one core. 

Start two calculators. Enter some small number e.g. 234. Use the X^Y function. Then eneter a huge number 10.000.000. You will see that with the first calculator it goes to 2.X ghz for 50%. With second the monitor goes to 100%. Mind, with second probably the computer will get very slow, so make sure that you can kill the process with the system monitor. 

:guitar:

---

### Post by JackandJohn on 2007-12-06
> **John Jason Jordan said:**
> 
So yes, it appears that it is cutting out when there is a spike, particularly a spike in CPU2. In fact, CPU1 did not spike nearly as much as CPU2. It strikes me as odd that neither CPU got over 50%, yet sound was cutting out on a spike.

I also have a little CPU frequency applet in my Gnome panel. It displays 800 MHz - 1.2 GHz - 2.0 GHz depending on how much the CPU is being used. However, I think it monitors only one core. I notice that it frequently goes to 2.0 GHz even though System Monitor never goes above 50%. Just playing an MP3, even without the bluetooth headphones, tends to make it hover back and forth between 1.2 and 2.0 GHz.

I don't know what any of this means.

Ok, these were some excellent test conditions, and interesting results.
They seem to support my hypothesis that the cpu is at least the main culprit

First thing of note: I would suggest finding a way to disable cpu scaling for a test run;
I have also noticed that there are little hiccups when switching frequency, and chose to disable it on my amd64 when I had that tower (especially annoying for things like semi-transparent menus that would stutter every time)
Do be aware, though, that this is very much like the difference between driving properly and pushing the pedal to the floor non-stop as noted by Jouke7 : the cpu will use more electricity and will get warmer, but it will always be "revved up"
I am not sure how to disable it in gutsy - check the forums; I remember terminal commands in 7.04.
To see if you were able to disable it; since you use that nice little applet, it will simply say something like "CPU Frequency Scaling not supported" when you log in, and it will stay at 2Ghz

Second thing; the scaling affects both cores simultaneously

Third; It's possible that with two cores, it may be doing "funky math", and when both cores are maxed it would show 50% on each; 100% divided by two, you see. Definitely test this with Jouke74's method of pinning the cpu, and seeing how system monitor responds (Combined with the taskset command, you could also pin just one CPU)

---

### Post by stedevil on 2007-12-13
Regarding setting HARD affinity (as opposed to kernel automatic soft affinity) I just gave that answer in the below thread 

[http://ubuntuforums.org/showthread.php?p=3943329&posted=1#post3943329](http://ubuntuforums.org/showthread.php?p=3943329&posted=1#post3943329)

Hope it helps someone :)

---

### Post by mozetti on 2007-12-13
Let me hop onto this "setaffinity" train.

I run a XP VM in Virtualbox so I can use Tversity to stream content to my Xbox360. When I'm running the VM, especially when TVersity is transcoding video, I notice a slowdown in performance and response when doing other tasks.

Do any of you with more knowledge of core affinity think that assigning VirtualBox to the 2nd core would alleviate some of the performance drag?

---

### Post by stedevil on 2007-12-13
I donno, but try it and see.

Personally I hope it does, because I myself started out this chase of info since Im tinkering with virtualisation and running XP via KVM/Qemu on a dual core CPU. Keeping all of Windows on 1 CPU instead of having it jump back and forward (as it does in soft affinity mode) should logically save a lot of memory access to refill CPU lvl 1 & 2 cache.

---

