---
title: "Why is Breezy computer starting by itself?"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by poiuytr on 2006-03-30
Weird problem.  I will shut my Ubuntu AMD_64 desktop computer down completely, and after an hour or so it has turned itself back on.  Happens whether I am Internet-connected at the time, or not.

I'm guessing some type of cron job is running (one I have not consciously had anything to do with creating!)

So:

1.  What could possibly cause my Ubuntu computer to suddenly start doing this?

and 

2.  What config files or whatever do I need to check/change to stop this from happening right now?

and

3.  How do I stop this permanently from ever happening with this computer again?  (Is there typically a BIOS setting, for example, which allows or disallows automated Power On?)

Ideas?

---

### Post by mozetti on 2006-03-30
Are you connecting to the internet through a router? The first thing I thought of was that your ethernet card has the 'Wake-On-Lan' function enabled, and it's getting a hit from a router or other computer on the network and waking up.

As far as fixing that -- I can't really help, since I just getting started with Linux, myself.

---

### Post by poiuytr on 2006-03-30
No, no router.

---

### Post by hajk on 2006-03-30
Why do you think the problem is Breezy? Your mother board probably has some wake up function enabled (LAN, USB, ...) that is receiving a signal and starts the default OS in GRUB. So, check the BIOS settings on your mobo.

---

### Post by poiuytr on 2006-03-30
Sorry, I didn't mean it that way - I'm a long-time free software supporter and am not intending to disparage Breezy in any manner.

But you're right, my assumption is that it was Breezy, because that has been the only OS I have been using on this computer, and I have never encountered this kind of problem before.  I haven't recently changed any BIOS settings, for example, so why all of a sudden now would the machine suddenly start waking up every hour?

The only changes I have been making to the machine have been Breezy changes, for example, regular patches.

So, yeah, I am assuming a possible cause (e.g. cron in this particular Linux distro),  but I don't even know what other guesses to make.  If anyone has other suggestions to check into, I would welcome any and all of them.  Thanks.

---

### Post by maury on 2006-03-30
I can't remember exactly what caused it, but I worked on a E Machine that did that and it turned out to be the power supply. I'll try to google it up and if I find it I'll post it here.
After going out on Google I see there are several things that can cause it to happen. The EMachine did have power supply problems that caused it to happen and I solved it by replacing the power supply but that is the only time I've seen it happen.

---

### Post by dmb on 2006-03-31
No, crons jobs only run when computer is on and linux is running. It would have to be something relating to the bios, or possible, maybe your computer is being turned off completely. 

Im almost compltely sure its not related to linux in any way. It has to be something with the bios, and first thing i thought of was wake on lan.  Go into the bios setting and find WOL or wake on event or anything like that and turn it off.  It could also be a USB device waking it up, so just turn those options off in your bios config.

---

### Post by poiuytr on 2006-03-31
Thanks for all your help, guys.  Wake up on LAN WAS enabled in the BIOS.  I turned it off, and problem seems to be solved.

I don't know whether that was just recently enabled, or if it has been enabled all along.  But in any event, I did a week or so before connect a new USB device (Epson printer), so maybe that was the cause.  Weird, huh?

Thanks again!

---

### Post by rplantz on 2006-04-01
[QUOTE=poiuytr]I don't know whether that was just recently enabled, or if it has been enabled all along.  But in any event, I did a week or so before connect a new USB device (Epson printer), so maybe that was the cause.  Weird, huh?
[/QUOTE]

I have a Mac running Mac OS X. If my Samsung USB printer is on when I shut down, the system immediately reboots. My Epson USB printer does not cause the reboot. From working with this stuff for some 30 years, I've concluded that printers do some weird things.

You could, of course, try turning wake up on LAN back on and disconnecting your printer. On the other hand ... if it ain't broke, don't fix it.

---

