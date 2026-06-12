---
title: "Setup stops during install and Live CD :("
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by envytwo on 2006-03-24
Hey guys, I am realy interested in installing ubuntu, I have been for the last few weeks. 
I finaly got around to doing it today, and I plan on staying up until its all set up!

My problem is that 1 minute after I push enter to begin the installing, it stops, the last line reads:

"Running /etc/hotplug/usb.rc
[    42.453856] ohci_hcd 0000 :00 :13 .0: Unlink after no-IRQ? Controller is probably using the wrong IRQ."

And then it stops.

I tried installing and ran into some problems last week, and I got all the way to the x-server error, now it doesnt even get nearly as far in the set up. Any advice would be great as I am determined to finish tonite!

Thanks in advanced.

---

### Post by Sef on 2006-03-24
> Running /etc/hotplug/usb.rc
[ 42.453856] ohci_hcd 0000 :00 :13 .0: Unlink after no-IRQ? Controller is probably using the wrong IRQ."

Next time you install, hit F6 first.  At the bottom is a command to input, so your computer doesn't check the hardware.

---

### Post by envytwo on 2006-03-24
Hey, thanks for the quick response. I tried what you said, and I still get the same result.

What is weird is that I could get further in the installation last time I tried, a week or so ago, now it dies :(

---

### Post by arkangel on 2006-03-30
hi  I have installed 5.10  and during installantion all seems to be ok , however  when  it prompts to restart to complete the instalation  it reaches a part  , checking  hootplug subsystem and hangs , 

SO what is next 

is an Asus  A6000Av  with ati x700  and centrino 1,86   if sobody can help me please

---

### Post by NeoFlexer on 2006-05-14
I am having the same problem. 
[COLOR="Red"]Running /etc/hotplug/usb.rc
[4294678.093000] ohci_hcd 0000:00:13.1: Unlink after no-IRQ? Controller is probaly using the wrong IRQ.[/COLOR]
One person said they fixed this problem by unpluging all USB devices, but this didnt work for me. I have also tried the F6 thing and that has not worked either.
I am going to try to work on this problem and keep an eye on the forums to see if anybody has fixed this. If not I should have something within the next 6 hours I hope :-D

---

### Post by NeoFlexer on 2006-05-15
I found "a" fix to this problem.  Not sure if it is going to help everybody but it should because it sounds like its the same problem.

Go into your BIOS during start up and turn ALL USB support off, then boot into the CD like a normal install. Install Ubuntu and do the live update (There will be a ballon pop up telling you there are updates ready so you shouldent miss it) Then once all the updates are installed reboot the computer, go back into BIOS and turn your USB support back on and boot into Ubuntu and Walla! You are now using Ubuntu 5.10 with full USB support.

Something to keep in mind if you are still still having problems. You may need to turn USB Legacy support off if you cant boot into Ubuntu even after the updates.  If this is a problem for you then you may need to update your BIOS, and don’t ask me how to do that with Ubuntu because as of right now I only have like 27 hours of Ubuntu experience. [-( 


Have fun and enjoy Ubuntu :-D

---

