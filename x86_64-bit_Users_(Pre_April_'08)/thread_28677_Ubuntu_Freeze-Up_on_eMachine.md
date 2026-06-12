---
title: "Ubuntu Freeze-Up on eMachine"
date: 2005-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by New10 on 2005-04-21
I replied to a couple of posts, but decided to start a new thread on this issue.

Coming from Windowsland, this is my first attempt at Linux. I took an eMachine, AMD 64, 512 MB, 160 GB, removed the windows partitions and installed Mepis via automatic install.  Mepis worked fine except that it would not recognize the eMachine's audio or ethernet hardware ("Failed to bring up eth0.")  After a lot of  sweat, forums and frustration, I changed distros to Ubuntu.  I did a complete new install of Ubuntu Hoary 64.  On the first boot, music came on. This was a great sign that Ubuntu was recognizing more of the eMachine hardware.  However, Ubuntu froze on the brown screen right after log-in.   From the Ubuntu forums, freezing seems to be a common problem.  I'll try Ubuntu Hoary 32 next.

-----------

I'm back. I booted up with the Ubuntu 32-bit distro that came with Linux Magazine.  This is a live CD, meaning that Ubuntu booted off the CD.  Like before with 64,  Ubuntu 32  booted up, the music came on, I logged in, and the PC froze on the brown screen.

In both cases, Ubuntu Hoary 64 and  32, only power off would clear the PC for reboot.

-------------

Back, again.  I booted off of the SystemRescueCD ([www.systemrescuecd.com)](www.systemrescuecd.com)).  That runs Gentoo. The PC booted up fine, and I could ping my gateway which I could never do before with Mepis ("Failed to bring up eth0") or with Ubuntu (freeze-up right after log-in).

---

### Post by mthaddon on 2005-04-21
Sorry to hear about the issues. Sounds like you're really taking the plunge if you're new to Linux - installing Ubuntu 64 bit and Gentoo, both of which are slightly more advanced! I'm assuming that your problem could probably have been solved with some different options on bootup (no apic, etc), but since I haven't experienced any of those problems, I'm afraid I can't help you with the specifics.

Gentoo's a great distro from what I hear, if requiring a little more "hands on" than others. Hope it works out well for you.

---

### Post by rmchan on 2005-04-25
[QUOTE=New10]I replied to a couple of posts, but decided to start a new thread on this issue.

Coming from Windowsland, this is my first attempt at Linux. I took an eMachine, AMD 64, 512 MB, 160 GB, removed the windows partitions and installed Mepis via automatic install.  Mepis worked fine except that it would not recognize the eMachine's audio or ethernet hardware ("Failed to bring up eth0.")  After a lot of  sweat, forums and frustration, I changed distros to Ubuntu.  I did a complete new install of Ubuntu Hoary 64.  On the first boot, music came on. This was a great sign that Ubuntu was recognizing more of the eMachine hardware.  However, Ubuntu froze on the brown screen right after log-in.   From the Ubuntu forums, freezing seems to be a common problem.  I'll try Ubuntu Hoary 32 next.

-----------

I'm back. I booted up with the Ubuntu 32-bit distro that came with Linux Magazine.  This is a live CD, meaning that Ubuntu booted off the CD.  Like before with 64,  Ubuntu 32  booted up, the music came on, I logged in, and the PC froze on the brown screen.

In both cases, Ubuntu Hoary 64 and  32, only power off would clear the PC for reboot.

-------------

Back, again.  I booted off of the SystemRescueCD ([www.systemrescuecd.com)](www.systemrescuecd.com)).  That runs Gentoo. The PC booted up fine, and I could ping my gateway which I could never do before with Mepis ("Failed to bring up eth0") or with Ubuntu (freeze-up right after log-in).[/QUOTE]
 You never really said what type of emachines system you have.  I have an emachines m6807 laptop running 64 bit Hoary just fine...

One thing to note.  Older emachines 64 bit laptops will probably need a bios flash because they came with some busted bios'es in the first place.

---

### Post by stranger on 2005-04-26
I've run into the same problem on a Compaq R3000Z with both 64-bit and 32-bit installations.

I kind of fixed it once, but it has since failed on a different installation (I'm trying various distros to see what works best on this laptop).  What I did was boot into a failsafe terminal session, start synaptic (which ran fine) and downloaded the kde (kubuntu) desktop.  I could log into that fine.  On one try I was also able to log into gnome after getting the kde desktop to work.  On the next installation, that didn't work.  

It might seem odd that I've tried to install Ubuntu more than once on this computer, but I've switched to Ubuntu on my desktop machine, and really want to have both machines running the same system.  I have two problems with it, though: logging into gnome and getting ndiswrapper to work with Ubuntu.  I can do it with Kanotix, but not Ubuntu.

Anyway, this might be an amd64 issue, as I have an amd64 3000.  Otherwise, it has an NForce3 chipset, so maybe it's that.

Good luck.  If you decide to ditch Ubuntu you might want to give kanotix a try.  It's a very nice distro, but I'm not a big KDE fan.

---

### Post by kpenrose on 2005-04-27
rmchan:  I see you're running hoary on an emachines 6807?  I was trying to use the 64bit  live cd, and it freezes on start-up sometimes, and when it doesn't freeze it complains that it can't find the clock frequency using any know method, and then X can't start and there's a ton of other error messages.
Did you do anything special to install?  I'm currently using Mandrake (Mandriva) but I like the availability of more packages in kubuntu.  

Thanks in advance.

Oh, and I have flashed the bios with the new bios version from the emachines website.  :smile: 

-- Kevin

---

### Post by dickohead on 2005-05-09
Hey Guys,

I'm new here, but not new to Linux. I am having a similar problem as above with multiple Distros, but I like the idea of Ubuntu's Philosophy, so I figured i'd give it a try. Having so far Tried SuSE 9.2 64 bit, Mandriva SE2005 64bit and Ubuntu, I am now beggining to see a pattern - they are all locking up at either:

System Startup, before login (console and gui)
Before Installation - Mandriva discovered an unknown error and rebooted, but Ubuntu locks straight up, SuSE 9.2 32bit had package errors when reading from the cd (yet the cd is fine, used it plenty of times before)

What would most likely cause a system to lock up like this, constantly? I am successfully running windows on my eMachine (Arima) Laptop, it is an Arima W720-K8M, but i'm not sure which e-machine it corresponds to. I purchased this Laptop in Australia, it has been rebadged by a company called TPG. The system specs are as follows:

512MB 333Mhz SODIMM RAM
AMD Athlon 64 2800+ (1.8ghz)
60 Gig Hard Disc (30 windows, 14(/)-14(/home)-2(swap) Linux)
15.4 inch widescreen

Is anyone able to give me some advice as to how i can get this system working? Even in console mode, I can work it from there!

---

### Post by rush_ad on 2005-05-09
[QUOTE=dickohead]Hey Guys,

I'm new here, but not new to Linux. I am having a similar problem as above with multiple Distros, but I like the idea of Ubuntu's Philosophy, so I figured i'd give it a try. Having so far Tried SuSE 9.2 64 bit, Mandriva SE2005 64bit and Ubuntu, I am now beggining to see a pattern - they are all locking up at either:

System Startup, before login (console and gui)
Before Installation - Mandriva discovered an unknown error and rebooted, but Ubuntu locks straight up, SuSE 9.2 32bit had package errors when reading from the cd (yet the cd is fine, used it plenty of times before)

What would most likely cause a system to lock up like this, constantly? I am successfully running windows on my eMachine (Arima) Laptop, it is an Arima W720-K8M, but i'm not sure which e-machine it corresponds to. I purchased this Laptop in Australia, it has been rebadged by a company called TPG. The system specs are as follows:

512MB 333Mhz SODIMM RAM
AMD Athlon 64 2800+ (1.8ghz)
60 Gig Hard Disc (30 windows, 14(/)-14(/home)-2(swap) Linux)
15.4 inch widescreen

Is anyone able to give me some advice as to how i can get this system working? Even in console mode, I can work it from there![/QUOTE]
 i have the same freezes but not on emachine. it just happens no matter what you use.

---

### Post by dickohead on 2005-06-28
Alright! After getting SuSE 9.2 64bit to work on my laptop, i have now gotten Ubuntu 5.04 working aswell!!! What I do is:

When installing the system, press F2(i think) to get to where you can choose which kernel to load, F3 or F4...F5... etc should give you some tips on how to fix display issues you might have when installing, i then typed:

```
linux noacpi nolacpi acpi=off (option to fix display)
```

and then when i boot the system, i set ub grub so that the default option would pass the folloing options to the kernel:

```
noacpi nolacpi acpi=off
```

and now Ubuntu works like I dream!!!

---

### Post by Optimal Aurora on 2005-06-28
[QUOTE=rush_ad]i have the same freezes but not on emachine. it just happens no matter what you use.[/QUOTE]
Same here however, I haven't had it with ubuntu, but have had it with fedora and other linuxes...

---

### Post by abiezerm on 2005-06-29
only for information i have a emachines 6805 with ubuntu 5.04 and works very well (Rocks),
only my wireless tha i don't know how work's in ubuntu.

Bye.

---

### Post by dickohead on 2005-06-29
[QUOTE=abiezerm]only for information i have a emachines 6805 with ubuntu 5.04 and works very well (Rocks),
only my wireless tha i don't know how work's in ubuntu.

Bye.[/QUOTE]
 I have the same problem! Now the only thing that won't work is my wireless!!! ARGGHH!!! If i get it going i'll let you know.

---

