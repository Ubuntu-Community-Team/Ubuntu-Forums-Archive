---
title: "Ubuntu 64 Crash Investigation"
date: 2009-08-18
forum: x86 64-bit Users
---

### Post by jstorta on 2009-08-18
On a couple of occasions I have had an issue where Ubuntu (Jaunty 64-bit) will reboot out of the blue.  I have tried to find some common theme to the reboots, but I have been unsuccessful.

Here is my hardware.
Asus M3A motherboard
AMD Athlon 64 X2 4600+ CPU
3GB physical memory
XFX 8800 GT Alpha Dog 512MB DDR3 Standard (PV-T88P-YDF4) Video card with restricted driver (180)

The closest I can come to a commonality during the crashes is that I am running the following apps.
OpenOffice
Several Terminals
FireFox
jEdit

Keep in mind that I run these apps a lot so it is not like it is some unusual combination that causes the problem.  Also, the crash does not happen while doing anything particular.  I will use them for days at times and then have a crash.  When the most recent crash occured I was not even using the system.  I had left it for a few minutes and when I came back it had rebooted.

In my attempt to figure out the problem, I have done several things.

I looked through the assorted logs, but I cannot find anything that says 'crash caused by this!'. :)  

I looked through the Ubuntu HCL web site and found that my motherboard received excellent reviews.  My specific CPU (4600+) does not have a review, but AMD64 X2's got many excellent reviews.  My video card did not receive any reviews, but Nvidia cards seem to have pretty good support.

I booted off the live CD and ran a memory test.  I only let it run for an hour or so and it found nothing.  I was going to let it run overnight.


My question is not necessarily "what is causing the crash?" though an answer to that would be nice.  I am really looking to find out what I can do to try and zero in a little closer to the cause.

Is there any sort of utility for Ubuntu that will recognize a crash and gather information for bug reporting after the system is back up?  

Is there something I should look for in the logs that might provide a clue?

Any guidance would be appreciated.

Thanks,
John S.

---

### Post by ptn107 on 2009-08-18
Check your logs System -> Administration -> Log File Viewer for any similarities during the times the machine rebooted.

---

### Post by realzippy on 2009-08-18
...no idea about the logs;
/var/log/kern.log ,/var/log/messages
the only one I know...but,once I had a similar issue
with an Athlon Venice;I had to disable gnome-power-manager
and ACPI in the bios..

---

### Post by jstorta on 2009-08-18
I was just going through the logs and found what I think might be some interesting notes.  I have attached the log entries from the time of the crash.

Most of it does not mean much to me other than that it seems to be reporting some sort of issue and then dumping some information.


Any thoughts?


Thanks,
John S.

---

### Post by jstorta on 2009-08-18
This seems to be the message that starts the crash.

kernel: [95378.877785] kernel BUG at /build/buildd/linux-2.6.28/fs/inode.c:263!
kernel: [95378.877790] invalid opcode: 0000 [#1] SMP 

I am not sure if this points to anything in particular (file system) or if it is one of those generic messages.

I did a Google search and I see references to it from several years ago, but can't seem to find any reference to it in Jaunty.

I will keep looking.

John S.

---

### Post by realzippy on 2009-08-19
tested to disable power-management and ACPI in bios??

---

### Post by jstorta on 2009-08-19
I tried to disable ACPI in the BIOS, but after doing that I was unable to boot the system.  It was almost like it couldn't find the boot drive.

I couldn't believe that disabling ACPI could make the system unbootable, but after re-enabling it in the BIOS, the system booted up fine.

I was going to try and edit the boot command to disable it there, but I have not figured out the best way to do that yet.


Thanks,
John S.

---

### Post by jstorta on 2009-08-19
I was just on You Tube watching a video and X apparently crashed.  My whole system did not crash, it just dropped me back to the login screen.  I am not sure if this is related to my system crash issue or if it is just part of my ongoing frustration with Flash.

I did get some messages in the logs so I attached those excerpts.

Curious if any of these messages mean anything to anyone. 

Also,
I am curious if someone has any insight into what ACPI might be doing that would cause a crash.  I have heard on this and other forums as something to turn off, but I am not really clear as to why.


Thanks
John S.

---

### Post by jstorta on 2009-08-19
X just crashed again.  This time I did not even have Flash enabled in Firefox.

I've attached the latest log excerpts, which appear to be similar to the previous set.

Any thoughts would be appreciated.

Thanks,
John S.

---

### Post by j.bell730 on 2009-08-19
What type of video card do you have?
If nVidia, what driver version do you have installed?

---

### Post by linux4me on 2009-08-19
There's a [bug #342324 in launchpad]("https://bugs.launchpad.net/ubuntu/+bug/342324") that may help you. It sounds like the same issue you're having.

---

### Post by realzippy on 2009-08-19
"XFX 8800 GT Alpha Dog 512MB DDR3 Standard (PV-T88P-YDF4) Video card with restricted driver (180)"



You have a windows installed to compare?

---

### Post by jstorta on 2009-08-19
linux4me,
That bug does look like the issue I am having with X crashing.  I do not see a solution though.  They mention commenting out a line in xorg.conf, but I do not have that line in that file.  

They also mention turning off the effects.  I may try that and see how long I go without X crashing again.  I hate that though because with it being an intermitent problem, how do I know if it solved the problem or if it is still lurking.

Unless someone believes that X crashing and the system crashing are the same issue, then I will post my X issues to that other thread and keep this one back on the topic of actual system crashes.

My system just crashed again before posting this.  I see no messages in the logs this time.  It just shows boot messages all of a sudden.

realzippy,
I am not sure I understand your question.  Are you asking if I have MS Windows installed?  I have Windows installed on another hard drive.  What were you wanting me to compare?



Thanks,
John S.

---

### Post by linux4me on 2009-08-19
I always like to find a single explanation for these things, but it's possible you have two problems. It's really frustrating trying to troubleshoot something you can't reproduce. 

Do you have a screensaver enabled? How about the settings you're using in System->Preferences->Power Management->On AC Power? I would be interested to know what happens with the X crashing if you disable the screensaver and set the power management settings to "never." If you go long enough without the crashes that way, you can reintroduce one at a time and see how it goes.

Random reboots in the absence of anything in the logs makes me think you may have a hardware problem like overheating or power supply problems since it sounds like you have ruled out memory issues.

---

### Post by jstorta on 2009-08-19
I have screen saver set to blank screen and I have both power options set to 'Never' when on AC power.  I set those a week or so ago while trying to resolve this same issue.

Other than the one time when it crashed while I was away, the other crashes have been while I am in the middle of using the system, but never has it been while doing the same thing.

I don't know how much this factors into identifying a hardware issue, but I had been using Windows on this system until a few weeks ago when I decided that I wanted to switch to Ubuntu.  I never had any such crashes under Windows.

If it is hardware, I was thinking it might be some incompatibility or conflict, but I cannot find anything.


Thanks,
John S.

---

### Post by linux4me on 2009-08-19
Dealing with the random reboots and not the X crashes, if you haven't added any hardware between the time that you ran Winblows successfully and now, it would be a real coincidence to suddenly have a hardware problem, but not out of the question. I would still wonder about a power supply issue. 

I wonder if you could have some Windoze-specific hardware settings in your BIOS--like the old "PNP OS installed" that appeared in the Advanced section, for example--that could be causing problems?

---

### Post by tgalati4 on 2009-08-19
First validate your RAM:

/boot/memtest86+.bin

Run it for 30 complete cycles.  It will take overnight probably.

You should have no errors in 30 cycles.

---

### Post by j.bell730 on 2009-08-19
Is [this thread]("http://ubuntuforums.org/showthread.php?t=1121691") relevant? The bottom includes a solution.

---

### Post by jstorta on 2009-08-19
I just checked BIOS and I see the PNP OS setting is set to 'No'.

I tried to see if any other values looked Windows specific.  Nothing jumped out at me.

Any recommendations on how to go about testing the power supply?


John S.

---

### Post by linux4me on 2009-08-19
> **jstorta said:**
> I just checked BIOS and I see the PNP OS setting is set to 'No'.

I tried to see if any other values looked Windows specific.  Nothing jumped out at me.

Any recommendations on how to go about testing the power supply?


John S.

If you don't have another power supply you can swap, there are a few options. One is to [buy a power supply tester]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=power+supply+tester&x=0&y=0"). You can get them for less than $30. A second option is to take your power supply out and take it in to a computer store that will test it for you. You may be able to find some place that will do it for free. A third is to buy a new power supply from somewhere you can return it if it turns out it's not the problem and swap it with yours temporarily. None is fun, unfortunately.

Your video card has some pretty serious amperage requirements, which, along with the other hardware you're running will require a fairly stout power supply, so you won't be able to get by with a cheap one. If you do buy one to test with, get a good one.

While the video driver could be responsible for the problem with X restarting, I don't believe it could be the cause of the random error-less reboots. That sounds like a hardware issue to me, still.

---

### Post by Yellow Pasque on 2009-08-19
If memtest checks out, I would try other Linux distros (by using LiveCD's) before troubleshooting hardware. When running from the LiveCD, try doing things that stress your system.

---

### Post by realzippy on 2009-08-20
"I never had any such crashes under Windows"...
...I asked for windows just to see if your error is linux specific or not.You could run 3Dmark in Windows e.g. to force errors...

Please test to disable Power Management completely:

System/Settings/Sessions

If nothing helps,I would test another driver.I'm on 8.10 (9800gtx),and use the 173 nvidia,cause the 180 driver causes different issues.And,the older driver is faster...

---

### Post by jstorta on 2009-08-20
Just to confirm memory I ran the memtest86+ overnight.  It completed and had no errors.

My power supply is 450W.  I am wondering if it is undersized.  I never had any problems with it under Windows even while running GPU intensive games like Company of Heroes.  When the crashes occur in Ubuntu, I am not doing anything even approaching that, but if the PS is undersized, then maybe that is a contributing factor.

To pursue the power as an issue, I would like to disable ACPI.  I do not really know what ACPI does so it is hard for me to say if this would have anything to do with the issue, but I have seen it mentioned a few times.

I tried to disable ACPI in the BIOS, but I was then unable to boot the system until I turned it back on.  Maybe that is a clue.  I was going to try to disable it via the boot command, but I have seen both acpi=off and noacpi as options.  How do I know which I need?  or do I need both?

My Power Management settings are currently set to 'Never' for both Actions and Display when on AC power.  

One other thing I have thought about is SATA.

I have one SATA drive with an NTFS file system.  The OS is loaded on an IDE drive.  It may be a coincidence, but when I have had the crashes, I have had files opened from that NTFS mount on the SATA drive.  I saw some stuff on the web about Ubuntu and SATA being maybe unstable.  Most of these notes were old, but it raised an eyebrow.

One of the crashes did record this message in the kernel log.
kernel: [95378.877785] kernel BUG at /build/buildd/linux-2.6.28/fs/inode.c:263!
kernel: [95378.877790] invalid opcode: 0000 [#1] SMP 
kernel: [95378.877796] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
kernel: [95378.877802] Dumping ftrace buffer:

That first line points to a file system issue.

The full set of logs for that crash were attached earlier in this thread.


Anyway.  That is where I am now.  I appreciate everyone's input.

Thanks,
John S.

---

### Post by linux4me on 2009-08-20
In terms of the adequacy of the power supply, see if you can find an amperage requirement for your video card in the materials that came with it or the manufacturer's web site, then compare that to what your power supply is rated for. They may make wattage recommendations as well, but those are more easily met. I think some of those 8 series cards require something like 25 A, which is well below what most 450 W power supplies can provide. I can't explain why you wouldn't have had a problem in Windows, though that might be coincidental.

I would think that if you were dealing with a distro issue rather than a hardware issue, you would be getting some more info in your logs, but I don't know that for a fact. Trying a different distro via a Live CD sounds like a good test. You could just let it run all night since you have experienced the reboots with and without activity.

As for SATA being the cause, I can say that I have been running a SATA-only (HD's and DVD burner) system since 8.04 without any instability or problems, so I suspect that the SATA problems aren't universal even if they do occur on some systems.

---

### Post by tgalati4 on 2009-08-20
Depending on your CPU and GPU, the scaling governer can declock both.  This has shown instability in some systems.  You will have to do some research to determine how to turn off scaling on both, yet leave acpi running since it is required to interact with the hardware.  ACPI is what controls your sleep/suspend, power-off.  Without it, some computers will run, but won't shut off.  

As for the power supply, use a voltmeter to measure the 5V and 12V leads from a spare power connector.  Any dips in either voltage during heavy use (3d game) can indicate that the PSU can't supply enough current, resulting in a voltage drop.  When voltage drops too low, strange things happen.

It's possible that you have discovered an instability with 64-bit, scaling, AMD processor, your GPU, and mixing IDE and SATA.

You could also declock your CPU (say cut in half) and run it for a while to see if it is stable.  If so, then slowly bring the speed back up max.  It might take a few weeks of testing to determine what CPU speed triggers the problem.

---

### Post by Yellow Pasque on 2009-08-20
I find this guide helpful for boot parameters: [http://www.mjmwired.net/kernel/Documentation/x86/x86_64/boot-options.txt](http://www.mjmwired.net/kernel/Documentation/x86/x86_64/boot-options.txt)

---

### Post by jstorta on 2009-08-20
I hooked up my voltmeter and ran about a dozen apps that I thought would consume some CPU and memory.  I do not have any games installed on Ubuntu so I really do not have anything that can tax the GPU.

I got the system running to where the CPU was at about 60-70% busy.  I let it run like that for a few minutes and checked both the 5v and 12v readings.

I got 5.2v and 12.2v continuously.  I saw no fluctuations.  Not sure if 2-3 minutes is enough time to get a meaningful reading.


I opened a case with XFX to find out what the power requirements are for my graphics card.  They indicated 400W or higher and 26A at 12v.  My PS is rated at 450W and 24A at 12v.  Technically, I am coming up short on Amps, but then I am not using the graphics card so who knows.  And it never gave me issues under Windows when I was taxing the video card.


I guess my next step is to muck around with ACPI and CPU clocking and see what happens.


Thanks,
John S.

---

### Post by jstorta on 2009-08-20
X just crashed again.  I had a bunch of apps open.  Essentially all of the apps that were open when I was testing the voltage, though I had disabled Flash.

I was posting a message on a message board (not this one) when it crashed.

From daemon.log
Aug 20 15:16:56 aragorn x-session-manager[3195]: WARNING: Detected that screensaver has left the bus 
Aug 20 15:16:56 aragorn gdm[2757]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Aug 20 15:16:57 aragorn acpid: client 2761[0:0] has disconnected 
Aug 20 15:16:57 aragorn acpid: client 2761[0:0] has disconnected 
Aug 20 15:16:57 aragorn acpid: client connected from 12151[0:0] 
Aug 20 15:16:59 aragorn acpid: client connected from 12151[0:0] 


From messages
ug 20 15:16:57 aragorn bonobo-activation-server (john-12111): could not associate with desktop session: Failed to connect to socket /tmp/dbus-SUkOtBChGD: Connection refused
Aug 20 15:17:09 aragorn pulseaudio[12332]: pid.c: Stale PID file, overwriting.

From syslog
Aug 20 15:16:56 aragorn x-session-manager[3195]: WARNING: Detected that screensaver has left the bus 
Aug 20 15:16:56 aragorn gdm[2757]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Aug 20 15:16:57 aragorn bonobo-activation-server (john-12111): could not associate with desktop session: Failed to connect to socket /tmp/dbus-SUkOtBChGD: Connection refused
Aug 20 15:16:57 aragorn acpid: client 2761[0:0] has disconnected 
Aug 20 15:16:57 aragorn acpid: client 2761[0:0] has disconnected 
Aug 20 15:16:57 aragorn acpid: client connected from 12151[0:0] 
Aug 20 15:16:59 aragorn acpid: client connected from 12151[0:0] 


Yesterday I had several X crashes and then the whole system crashed.  We'll see what happens today.


John S.

---

### Post by tgalati4 on 2009-08-21
Be sure to turn off your screensaver.  If you have random screensavers enabled, then it's possible that you have a broken screensaver that can cause X to crash.  Not all screensavers work on all machines.  Test them individually and you may be surprised.

---

### Post by jstorta on 2009-08-21
Just to follow up on tgalati4's suggestion.  My screen saver is set to blank screen and only once has the problem occured while the system is idle.  Every other time, I have been in the middle of doing stuff.

****This is evening I had what I consider a major development****

I was trying a ton of stuff trying to get the system to crash.  I finally succeeded at duplicating the crash, mostly.

I basically kept repeatedly opening video files in VLC.  Literally double-clicking on the same MOV file over and over and over.  I found that eventually this would cause the system to crash.  

Sometimes the screen would just freeze.  Other times it would actually reboot.  Sometimes I would get a message in the kern.log just before the crash.  Other times nothing.  But I was at least able to get it to crash almost on demand.

After it would reboot, I would immediately start double-clicking the file again trying to get it to crash.  It always seemed to be fine for a while and then all of a sudden, after resting my finger, I would click once and it would die.

I was also checking the voltage while doing this and it never fluctuated until the system would crash or freeze.  When it would freeze, the voltage would drop from 12.2v to 12.1v, but other than that, no change.

I then started reviewing the logs and I found something interesting.  In all cases, it would only crash after the system had been up for about 10 minutes or so.  Prior to that I had no issues.

I then looked closer at the logs and I found something interesting.  In all cases, the following message is the last message that appears before the reboots.
kernel: [  179.000027] Clocksource tsc unstable (delta = -291437086 ns)

It is not always immediately before the reboot, sometimes several minutes, but I have no crashes until after this message appears.  And this message appears consistently 10 minutes after the reboot.

Also, when I do get a message prior to the reboot, it is always something like this.
kernel: [  243.859496] general protection fault: 0000 [#1] SMP 
kernel: [  243.859506] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor


Based on this information, I am thinking I definitely have some issue related to either the SMP on the dual-core CPU or something related to the clocking of the CPU.  At least that is what I interpret from Googling Clocksource and SMP.


Now the question is, what do I do with this information?


Thanks,
John S.

---

### Post by jstorta on 2009-08-22
I am ready to say that this problem has been resolved, though as I do so I am vigorously knocking on wood. :)

After my previously posted investigations, I felt confident that the issue had something to do with the CPU.  So I started looking at what could be modified.  My intention was to systematically make changes to the boot command based on some things I saw at other message boards and see if anything fixed my problem.

ACPI had been mentioned here.  Earlier I had tried turning that off in the BIOS but that left me with an unbootable system.  I decided instead to try adding 'noapic nolapic apci=off' to the boot command.  I did this and it did get rid of the Clocksource error, but instead I got ACPI errors and my ethernet connection would not work.  The network would come up and I saw no errors, it just wouldn't communicate.

Obviously that was a step backwards.

I decided to revisit the BIOS.  I poked around and found a 'Feature' called 'AMD Cool n Quiet'.  It has something to do with the CPU power management so I disabled it and rebooted.

The problem has not returned since.

The Clocksource message is gone.  I was not able to force the crash like I was during my testing last night.  I even spent all day today playing as many flash videos as possible.  Not a single issue.

This 'Cool n Quiet' feature apparently was the cause of all my woes.  System reboots, X crashing, Flash hanging Firefox.  Everything now works perfectly.

Thank you to everyone that provided input on this thread and stuck with me while I worked through this.  Without your input I would still be at square one.


John S.

---

### Post by Yellow Pasque on 2009-08-23
I'm glad you found the cause of your problem, but the workaround isn't ideal (you're now running your CPU at full speed/voltage all of the time).

I also get the "clocksource tsc unstable" message (though only once at boot), but this is to be expected on a CPU with dynamic clocking. However, you shouldn't be using that as your actual clock source. See:
[http://kerneltrap.org/node/8306](http://kerneltrap.org/node/8306)

The Asus M3A series is a modern mobo, so it should support hpet (High Precision Event Timing) and Cool'n'Quiet should work.

If you want to troubleshoot further, I would suggest:
1) Making sure your BIOS is up-to-date
2) Re-enabling Cool'n'Quiet and also see if there is an option for High Precision Event Timing in the BIOS
3) Seeing what clock sources are available by using that command, i.e.:
```
cat /sys/devices/system/clocksource/clocksource0/available_clocksource
```
4) Experimenting with the clocksource= boot parameter

---

