---
title: "Treo 600 on Ubuntu x64?"
date: 2007-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by je_richardson on 2007-11-26
Hey, I've been reading through the posts and don't see anything directly related to this. I'm relatively new to Linux/Ubuntu but I'm tr ying to learn. I've tried to setup my Treo 600 in Ubuntu but it doesn't sync. I know the sync cable is good because it works on my Windows Machine.

My question is whether or not the Treo 600 will work on Ubuntu x64, also, if it does, is there a walkthrough on how to set it up. I feel as though I'm doing something incorrectly.

Thanks!!!

---

### Post by je_richardson on 2007-11-29
Any one? Just something...link to a forum???

---

### Post by fineas on 2007-11-29
Are these helpful?
[http://ubuntuforums.org/showthread.php?t=592428](http://ubuntuforums.org/showthread.php?t=592428)
[http://www.linux.org/hardware/pda.html](http://www.linux.org/hardware/pda.html)

---

### Post by mperry on 2007-11-29
Hi-

I've used a few different treo models with Debian and Ubuntu in the past.  On the past release, I got a Treo 650 working but had a rather large share of problems with the evolution and gnome-pilot thing so gave up there.  I instead installed pilot-link and jpilot which worked perfectly.  You can observe the process that Linux goes through id'ing the treo by looking at dmesg in a console or xtern when you plug it in.  You should see messages about loading the visor or palm driver.   When you see this go down, it may be at something like ttyUSB0 and ttyUSB1.  I don't know why it takes two.  With jpilot its pretty simply to sync.  I did have a few issues with how I did the sync.  I had to make sure that I touched the sync button the treo first if memory serves and then do the jpilot sync. 

You may have to play around a bit; but the treo 600 should work pretty well.  I just think that gnome-pilot and evolution have problems and I finally gave up after numerous days of trying.  In the end, my Treo 650 would spontaneously reboot when I tried to sync with evolution and gnome-pilot.

I believe that pilot-link and jpilot should be apt-gettable.

---

### Post by je_richardson on 2007-11-30
Thanks for the help. I got kpilot to recognize the device last night but I haven't actually got it to sync yet. I'm now working on installing jpilot and your other suggestion...we'll see how this goes :)

---

### Post by Fisher Warn on 2008-01-02
i m having the same problem. Thanks

---

### Post by old_salt on 2008-01-02
I have a Treo 680. 

I'm using Kubuntu Gutsy but using Evolution for email. I use the gnome pilot tool as it seems to work best for me. Kpilot won't synch, JPilot synched to what I'm not sure of.

Issue I have is the 1 way relationship for synching. I've setup a seperate addressbook called "Palm" in Evolution. I synch to that but changes made on the phone are not updated in the Address book. Only changes made in the address book are replicated to the phone. 

Kpilot never worked.

Jpilot synched to something but I'm not sure what. It flip flopped the address lines and numbers for all my contacts and I could never edit the contacts in the app, only on the phone. File transfers? I have yet to see that work.

Oh and forget Bluetooth as well. You won't get that working either. 

On a personal note - I see way too much effort spent on eyecandy in Linux overall (all distro's) instead of getting basic or mainstream apps, services, utilities and peripherals working or on par with other systems. I hope this changes soon as eyecandy gets you nothing really.

---

