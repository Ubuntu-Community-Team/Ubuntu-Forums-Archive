---
title: "Looking for assistance"
date: 2009-06-08
forum: x86 64-bit Users
---

### Post by asmithey on 2009-06-08
Hi I am new here....
 
I have been having a problem with getting more than 4 gigs on my board.
 
Current set up.....
 
mb: s5000 xvnsata-(Can hold 32 gig of ram)
os: win xp pro x64 version 2003 sp2
Ram: 4 gigs
vc: PNY Nvidia Quadro FX 580
CPU's: Dual quad emt64 e5320"s
 
Basically what happens, is when I put more than 4 gig on the board it will not boot. I have tried several compatible ram brands and always get the same reaction during the boot up. It gets past the splash screen then just goes black. As soon as I stick 4 gigs back on the board it boots and runs fine. I have had no issues with instability at all in the last two years while running 4 gigs of ram.
 
So, I figured maybe it is an OS issue with a incompatible driver perhaps. I tried to install Vista Ultimate x64 and it gave me a stop error stating a driver. 
 
It installs win xp pro x32 just fine with 8 gigs on the board. But it will not use it, of course.
 
I need more ram..
 
So I figured I'd try ubuntu...Not familiar with it at all. I stuck in my ram (2 (4) gig Sticks)
and I selected the option to boot without actually writing to the hard drive. With in seconds it gave me this (end trace 4eaa2a868e2da22) and would not go any further.
 
Can anyone tell me what that code means? I ran memtest on the ram individually and it passed all tests. But when I run it in dual channel I get an "unexpected interrupt-Halting"
 
Could this be a faulty ram bus MB issue? Or an driver issue?
 
Thanks,
 
Aaron

---

### Post by keplerspeed on 2009-06-08
So the system posts, you can enter into BIOS, but cant boot to live cd.

I am running 6gig, no issues 3x2gig sticks. Since this issue is persistent across OS, then I would assume either mobo or the ram. Since the ram seems fine from memtest... I would say mobo. Do you have the mobo manual? Specs?

---

### Post by pbpersson on 2009-06-08
Here is the [list of specs]("http://www.intel.com/Products/Workstation/Motherboards/S5000XVN/S5000XVN-specifications.htm") for the mobo mentioned by the OP

---

### Post by asmithey on 2009-06-08
[FONT=Arial][SIZE=2]Yes...I built the machine. I have all the information for the MB. I can get into bios. The bios actually shows all the ram installed ok as well.[/SIZE][/FONT]
 
[SIZE=2][FONT=Arial]I have spent countless hours on the phone with Intel over the last couple years. Nothing has been solved. They think it is a driver issue. My warranty goes out in a few months. So I am trying to exhaust my options before returning it for a new one. So I thought Ubuntu would be an option. But it acts just like every other os I try with more than 4 gigs. I have tried 4(2gigs) stick configurations as well. Always the same results.[/FONT][/SIZE]

[FONT=Arial][SIZE=2]I am using this as a workstation and not a server.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Notice that memtest reports no errors while checking the ram sticks indvidualy but stops while checking it a dual channel configuration.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Thanks for posting the specs....[/SIZE][/FONT]
 
[SIZE=2][FONT=Arial]Aaron[/FONT][/SIZE]

---

### Post by pbpersson on 2009-06-08
I did a Google search and I was going to have you read [this post]("http://forums.legitreviews.com/about21129.html") but apparently that is you as well.

Are other people having this issue, or are you the only one on the planet?

Have you tried upgrading or re-flashing the BIOS?

---

### Post by asmithey on 2009-06-08
[FONT=Arial][SIZE=2]Yes. I am running the latest Bios. Every time I have flashed the bios over the past two years, nothing changes. [/SIZE][/FONT]
 
[SIZE=2][FONT=Arial]I have found a lot of people with the same symptoms I am having but with different boards and ram amounts. For instance. when I try to boot into safe mode, with more than 4 gigs installed, in xp pro x64 I get a stop when the os is trying to load acpitabl.dat. This seems to point to a driver of some sort always related to xp pro x64 os. [/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]So It makes me think it is a driver issue. But my inexperience has limited me to be able solve which driver and how to pin it down and fix it.[/FONT][/SIZE]

[FONT=Arial][SIZE=2]EDIT: I can load the live cd with one 4 gig stick installed.......[/SIZE][/FONT]
 
[SIZE=2][FONT=Arial]Aaron[/FONT][/SIZE]

---

### Post by asmithey on 2009-06-10
New mother board solved the problem.  Case colsed, thank GOD!!!!!!!!!!!!!!!!!!!!!!!!

---

