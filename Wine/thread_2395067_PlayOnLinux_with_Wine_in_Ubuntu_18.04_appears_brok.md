---
title: "PlayOnLinux with Wine in Ubuntu 18.04 appears broken"
date: 2018-06-26
forum: Wine
---

### Post by ivan-samuelson on 2018-06-26
I am running the 64-bit version of Ubuntu 18.04 on my machine. I've ran 16.04 and PlayOnLInux worked fine. I have enabled the i386 architecture (sudo dkpg --add-architecture i386), installed the 32-bit version of Wine (tried also the 64-bit) but everytime I use PlayOnLinux to install a windows game that worked for me under 16.04, it hangs at the creating virtual disk portion. Sometimes I see it download the components based on what install I chose in PlayOnLinux, but it always hangs at the end. I've let it run for 20+ minutes and it never continues on.

Is there any issue with Wine under 18.04 right now? I know that WineHQ hasn't created a package for Bionic Beaver, so I'm just wondering why it doesn't work under 18.04 or does it? I can't get anything to install.

Thanks!

---

### Post by MikeCyber on 2018-07-01
I had to update Nvidia on 18.04 to get wine working again as on 16.04. There are also bionic packages now from winehq.

---

### Post by djking101 on 2018-07-03
I have the same problem on Xenial Xerus based XenialPup puppy Linux on my usb drive. Installing from Ubuntu Software Center (modded) using official repos

---

### Post by MikeCyber on 2018-07-03
run in terminal and paste the output. also try this: [https://wiki.winehq.org/Download](https://wiki.winehq.org/Download)

---

### Post by jselph on 2018-09-20
ivan-samuelson did you find a solution? I am having the same issue. 18.04 seems to be missing files, a link, something. Using wine I am having issues with free type i386 and missing kernel32.dll file.

---

### Post by monkeybrain20122 on 2018-09-20
Same issue I created a thread  4 weeks ago [https://ubuntuforums.org/showthread.php?t=2398938](https://ubuntuforums.org/showthread.php?t=2398938)

@MikeCyber, I have the terminal output.

---

### Post by monkeybrain20122 on 2018-09-20
> **jselph said:**
> ivan-samuelson did you find a solution? I am having the same issue. 18.04 seems to be missing files, a link, something. Using wine I am having issues with free type i386 and missing kernel32.dll file.

Also libpng12 is missing for POL as Bionic has libpng16, the usual trick of making symlink doesn't work so I have to compile and install libpng12 locally and export LD_LIBRARY_PATH.

---

### Post by monkeybrain20122 on 2018-09-20
> **MikeCyber said:**
> I had to update Nvidia on 18.04 to get wine working again as on 16.04. There are also bionic packages now from winehq.
Nothing to do with Nvidia. This is an intel machine and POL worked on 16.04 on same machine perfectly,.

---

### Post by dexMilano on 2018-09-29
Hello all
I've the same issue just after the upgrade to 18.04 LTS.

I tried to debug the launch and I've found few interesting lines

"
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:RegisterTraceGuidsA (0x30f9703e, 0x31034a58, {8736922d-e8b2-47eb-8564-23e77e728cf3}, 1, 0x33fcac, (null), (null), 0x31034a58): stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:RegisterTraceGuidsA (0x39b19f12, 0x3a048568, {8736922d-e8b2-47eb-8564-23e77e728cf3}, 1, 0x33f6fc, (null), (null), 0x3a048568): stub
fixme:advapi:RegisterTraceGuidsW (0x39b19f12, 0x3a05d4c8, {a019725f-cff1-47e8-8c9e-8fe2635b6388}, 1, 0x33f670, (null), (null), 0x3a05d4c8): stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:imm:ImmDisableIME (39): stub
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
fixme:time:GetCalendarInfoW flag CAL_NOUSEROVERRIDE used, not fully implemented
"

It looks like one of the problems is about the font (freefont).
I tried to launch Adobe Acrobat  and it start but without any text.
I look for [https://www.freetype.org/download.html](https://www.freetype.org/download.html)
but honestly I don not understand what I have to install and how.

Any comment will be welcome.

---

### Post by apollothethird on 2018-12-26
Currently, Playonlinux doesn't work properly on Ubuntu 18.04.

I spent weeks trying various fixes for many of the issues such as "Wine cannot find the FreeType font library.".  When using the various fixes and getting past one error you're confronted with others.

I have tried, starting over with fresh installs of Ubuntu 18.04 and none of the attempts succeeds with an install of the simplest default application such as Microsoft Internet Explorer or Firefox.

If compatibility becomes available via either an upgraded work on Ubuntu 18.04 or Playonlinux, I'll bring the resolution back to this thread.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by Tadaen_Sylvermane on 2018-12-26
I haven't had an issue withh POL on 18.04 yet. Use it for a few things, not a problem to speak of. Using the official repo packages saves me many headaches.

---

### Post by apollothethird on 2018-12-26
Any time I have a problem with something that is expected to be officially supported with an official repo, if I have a problem, I will perform a fresh install with all the official updates, then try the install.  Like you, it saves me a lot of headaches also to recognize that it will work in a clean unblemished environment.

So far in my Linux experience of over 20 years, this doesn't happen with POL on Ubuntu 18.04.

I spend a few hours a couple of times a month trying to make a default installation application such as Microsoft Internet Explorer or Firefox work on a clean Ubuntu 18.04 install, in hopes that the problem might be resolved.

First, I'll mention that it always installs without errors are any problems.  However, the application attempted to install never works.

I never had this issue with any other version of Ubuntu.

I wrote steps for a very computer illiterate client to install The Sims on Ubuntu 16.04.  It was about 10 easy steps.  Now I can't write steps that will work for installing Firefox or Internet Explorer for Ubuntu version 18.04.

It would be nice if you would take a vanilla install of Ubuntu 18.04 and identify steps that will work.  Most likely you can use it now because of something else you have done with your environment.  At present, a vanilla install can't get past the error "Wine cannot find the FreeType font library".  It's my impression that the next errors if you use many of the various steps passed around for resolving that issue, might actually create the many subsequent issues that happen.

If you post steps that work for you, for installing the default Internet Explorer, I'll test the steps on a fresh install of Ubuntu 18.04 and provide you with the exact failure... or of course, if I'm wrong, the success.

By the way, if the repository for POL ever starts working I'll revisit a number of forums where I have asked this question, and provide updates of the success.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by vivienne-lumina on 2018-12-28
One of the problems with Playonlinux in Ubuntu 18.04 was that winecfg and installation "windows" etc. were not showing at all. This was solved by searching for "libz.so" in ~/.PlayOnLinux/wine/linux-x86//lib directories and deleting all of those files.  Another problem was solved by removing and reinstalling fonts:     apt-get install libfreetype6:i386.     I found these solutions after a couple of days searching and trial and error. I can't remember where I found these solutions but I've put them here hopefully to help others.

---

### Post by apollothethird on 2018-12-28
> **vivienne-lumina said:**
> One of the problems with Playonlinux in Ubuntu 18.04 was that winecfg and installation "windows" etc. were not showing at all. This was solved by searching for "libz.so" in ~/.PlayOnLinux/wine/linux-x86//lib directories and deleting all of those files.  Another problem was solved by removing and reinstalling fonts:     apt-get install libfreetype6:i386.     I found these solutions after a couple of days searching and trial and error. I can't remember where I found these solutions but I've put them here hopefully to help others.

Thanks.  I performed those steps, but possibly not in the right order.  I'll start out with a fresh install of Ubuntu 18.04 and perform them again and document the exact steps and response and bring the results back to this thread.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

