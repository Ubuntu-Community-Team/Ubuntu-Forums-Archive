---
title: "System hang on line 130.790320 during install."
date: 2006-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by swinster on 2006-03-17
Hi,

I am attempting a Kubontu 5.10 install on my Rock Quaddra T64 laptop. This is an AMD 64Bit Turon processor so I have downloaded the AMD 64 image (DVD ISO).

I have tried to install or simply run the live disk and the procedure fail in both instances. The start-up routine gets to line 130.790320 just after setting the RAM disk space and then simply freezes.

I haven’t a clue now what I should do or what other logs I could retrieve to post here.

Further info - The laptop is currently installed with Win XP HOME. The hard rive has all it's space allocated to NTFS partitions, although I was hoping to resize these partitions and create something suitable for Linux during the install - which I had assumed would be possible. Do I need to resize the partitions and create space with something like Partition Magic BEFORE even running live disk?

Help is appreciated. I am a relative Linux noob. I did mess with it 7 years ago but found it cumbersome. I had hoped thing would have improved especially as the motto of the distro is that it "should just work!"

Many thanks

Chris

---

### Post by swinster on 2006-03-17
Ooops, The line number I gave above is obviously not a line number, it is a time stamp so makes no relevance what so ever.

However, the line the system hangs on is always the same:

[NET, registered protocol family 2].

Maybe this will give some better ideas.

Chris

---

### Post by swinster on 2006-03-17
Ok, after a bit of reading I ran the command LINUX with the noapic and nolapic options. This installed everything and the system appears to be functioning with two slight issues.

1) It didn't detect my on board NIC during the Network Detection phase. I'm not sure if this is something that can be tackled after install. I also have a wireless adapter (MSI) that I would really like to use, although I have read these can be a pain.

2) I can't see anything on the screen! Everything seems to boot up fine, and KDE starts, the modules load and the progress bar hits 100% then the screen goes black. I know there should be a logon screen and if I enter my user detail (blind) I can see the HDD start to have activity as though the desktop is loading - I just can't see it. I can even press the power button on the laptop and the PC will shut down correctly. During the set up I chose a resolution of 1440x900 which is the native resolution of the laptops 17 inch widescreen display and what Windows runs in. The graphics chip in the laptop is an ATI Radeon X700.

I&#8217;m not sure whether to continue on with this distro or try something else, but I may just be that Linux simply still isn&#8217;t mature enough to support this basic hardware.

---

### Post by swinster on 2006-03-17
Ok, after a bit of reading I ran the command LINUX with the noapic and nolapic options. This installed everything and the system appears to be functioning with two slight issues.

1) It didn't detect my on board NIC during the Network Detection phase. I'm not sure if this is something that can be tackled after install. I also have a wireless adapter (MSI) that I would really like to use, although I have read these can be a pain.

2) I can't see anything on the screen! Everything seems to boot up fine, and KDE starts, the modules load and the progress bar hits 100% then the screen goes black. I know there should be a logon screen and if I enter my user detail (blind) I can see the HDD start to have activity as though the desktop is loading - I just can't see it. I can even press the power button on the laptop and the PC will shut down correctly. During the set up I chose a resolution of 1440x900 which is the native resolution of the laptops 17 inch widescreen display and what Windows runs in. The graphics chip in the laptop is an ATI Radeon X700.

I’m not sure whether to continue on with this distro or try something else, but I may just be that Linux simply still isn’t mature enough to support this basic hardware.

---

