---
title: "64 bit Gusty a lot like 32 bit Feisty"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thelasko on 2007-10-22
hello all,

I wrote in a few months back when I made the switch from 32 to 64 bit Feisty.  I was having a number of problems with 32 bit including poor video support and a clock that ran at half the speed it should.  Even my curer moved faster when I hit the backspace key.  It "just worked."

I have upgraded to Gusty Gibbon 64 and found all of my problems have returned.  I figured it would be a good upgrade because of the "improved 64-bit support."  Does anyone have any suggestions?

Dell Dimension E520
Intel Core Two Duo 4300 @1.8GHz
Intel 965 Integrated Graphics Card
1GB RAM

PS The strange part is I know Dell sells a similar machine with Ubuntu pre-installed

---

### Post by Inxsible on 2007-10-22
What exactly are those problems? You haven't mentioned any in detail. Maybe, if you do, someone can help you out.

About Dell selling a similar machine, they probably install the 32 bit Ubuntu. Most manufacturers do not install the 64 bit OS unless you specifically request for it.

---

### Post by Thelasko on 2007-10-23
Attached is a link to my original post about Feisty:

 [http://ubuntuforums.org/showthread.php?t=538961](http://ubuntuforums.org/showthread.php?t=538961)

I should also note that I haven't tried playing video yet under Gusty.  I notice little things.  The computer seems half as fast as it should be.  It takes forever for programs to load.  Menus take a second or two longer than they should to display.  As I said before when I hold backspace my cursor moves much slower than it should.  The clock ( the one that displays the time in the upper right hand corner) runs at half the speed it should.  When I minimize windows they minimize very slowly.  Everything is just significantly slower!

Since originally posting I changed my video driver from the experimental Intel driver to the i810.  I didn't notice a difference other than my screen resolution is stuck at 1280x1024.  I think it's a problem with the kernel or something.  I'm not a total noob (i can edit Xorg.conf) but I don't know if I want to be messing around with different kernels.

I should also note that it's not a RAM issue.  Under Feisty 64 I would regularly use 500MB of ram in normal use.  Under Gusty I am using about 350MB.  I ran
```
sudo lshw -C cpu
```
and that told me I was running 64 bit.

any ideas?

---

### Post by Inxsible on 2007-10-23
so the live CD works fine, but after install things go south ?

Are you following the install procedure correctly? Seeing that you have the problem in 32 and 64 bit, you might want to first check your system and verify if all the hardware is compatible with Ubuntu. 

I cannot say for sure, but it could be your video driver(thats why the choppy images). But I still cannot explain how the live CD would be flawless as you say it was. :confused:

---

### Post by NotTheMessiah on 2007-10-23
> **Thelasko said:**
> 
I should also note that it's not a RAM issue.  Under Feisty 64 I would regularly use 500MB of ram in normal use.  Under Gusty I am using about 350MB.  I ran


How is the CPU usage? do you scale its frequency?

---

### Post by Thelasko on 2007-10-23
The live CD was the one for Feisty 64 back in August.  After I installed it worked great.  The problem occurred when I upgraded to Gusty.  Please allow me to recap:

1) Installed Feisty 32 bit in June or July and had problems with slow video and clock.

2) Installed Feisty 64 bit and all of my problems were solved.

3) Installed Gusty 64 bit and all of my problems ( I haven't tried video yet) are back again.

I have the Intel 965 integrated video card which can be a little flaky at times but I was able to run Compiz and watch full screen video under Feisty 64 with the right settings (using X11 video output instead of OpenGL).  I upgraded to Gusty because of improved 64 bit support that was touted, along with what I had heard was better support for the Intel 965 (upgrade to the 2.0 driver).  I already tried switching from the Intel driver to the i810 which under Feisty didn't give my monitor full resolution but was very capable otherwise.  The i810 didn't solve the problem.

> How is the CPU usage? do you scale its frequency?

I don't quite follow your question.  If you are asking about Speedstep I haven't had any problems with it in the past.  I don't think the Core Two Duo's have it.  My computer is a desktop so I don't see why it should.  My current CPU usage is typically around 5%

---

### Post by Inxsible on 2007-10-23
oh did you upgrade to Gutsy or did you do a fresh install ?

maybe the upgrade didn't work quite as well...Try a fresh install and see if that works. If you have a separate home folder, all your settings should remain too. Just make sure you don't format the /home mount point during the installation.

---

### Post by Thelasko on 2007-10-23
Asking about my installation can become a long story.  Nothing but problems with upgrading and the alternate CD doesn't recognize my keyboard.

I did a fresh install using the Live CD and moved over my files by copying my /home folder to my windows partition and then copying it back after the install.

---

### Post by Thelasko on 2007-10-24
After playing around with my xorg.conf settings.  I discovered that some of my settings aren't being saved.  In particular the new screens and graphics menu seems to be slow and doesn't save my settings.

I managed to disable and reenable the Intel driver and the machine worked fine.  I tried to enable the GL desktop from the menu and the machine slowed down again.

I suspect it's a misconfigured graphics driver but I am having trouble making changes in Gusty.

I ran glxgears and this was the output

```
glxgears
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
```

anybody have any ideas?
Thanks in advance

---

### Post by Thelasko on 2007-10-24
Video issues are confirmed.  The playback is slow and intermittent. Just like it was under Feisty 32 bit.  Something is wrong.

---

### Post by Thelasko on 2007-12-17
The problem has been intermittent for quite some time.  Some boots the system runs fast and some boots it runs slow.  I finally applied "noapic acpi=noirq" to the GRUB menu and although it gives me some error messages, it has booted and run quickly with a correct clock twice in a row.  I got the idea from [this post]("http://ubuntuforums.org/showthread.php?t=75281&highlight=double+clock+speed+problem").  I hope this helps someone in a similar situation.

---

