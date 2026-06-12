---
title: "No USB devices detected"
date: 2008-12-19
forum: x86 64-bit Users
---

### Post by weezer316 on 2008-12-19
Help!!

right, basically im on a fresh install of ubuntu, 8.10. Whenever i plug a usb device in, nothing happens. Ipod, wireles card, webcam, anything. They simply arent recognising. They all work on other machines fine, and on windows on this machine!

Here is the output of lsusb:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


and lsmod |grep usb

usbcore               175376  3 ehci_hcd,ohci_hcd


Anyone have any ideas? I dont ever seem to be able to install ubuntu without some crazy hitch like this!

Any help appreciated

Wheeler

---

### Post by Billxyzzy on 2008-12-19
I posted a similar question a couple of days ago. I was trying to use
USB card readers (CDR, Sandisk etc.
Here is what I found If my card reader was USB 1.1 I had the same 
problem.  I had a USB 2 card reader and everything worked.
Card reader showed up on the desktop and file browser show the
contents of the SD card.  USB 1.1 devices worked in Win XP but not
In IBEX. Be aware of what your devices are, USB 1.1 or 2.0
Good luck

---

### Post by onering on 2008-12-19
I have the same problem.  Ubuntu 7 used to auto detect my USB drives.  I did a clean install of Ubuntu 8.10 and now my USB drives are not detected. :-(

---

### Post by weezer316 on 2008-12-20
Its insane. I mean, the motherbaord I have is an Asrock and its really **** hot, never had an ounce of trouble with it. I also tried to re-install ubuntu (wiping the windows partition on the same disk) and nana, still the same.

Someone must have an idea out there? I promise mince pies and hot milk to the man who gives me a fix!

---

### Post by carml on 2008-12-20
I suggest that you try to boot with the recovery mode,this way you can correct the possible problems :confused:

---

### Post by weezer316 on 2008-12-20
No mince pies for you my friend!! tried it, Repair boken packages, the lot, still the same.another re-install, still the same, but all the devices work perfectly!

Anyone got any other ideas??

---

### Post by Billxyzzy on 2008-12-20
Ok maybe a little more info on the problem will help
Go to Applications>Accessories>terminal
Have one of your problem devices connected to a USB port
enter lsusb  post the resulting output

---

### Post by Brownout on 2008-12-20
There are some known issues about USB mass storage devices detection, see [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789").

---

### Post by Billxyzzy on 2008-12-20
I am going to add a bit more to this,  whether this helps or not I
am not shure.  I had a USB powered hub laying around and thought I 
would try it.  I connected one of my USB 1.1 card readers through it
and they card options showed up immediately in Places>computer.
After a bit the SD card showed up and I was able to open it and
see the contents.  There was a delay so something about that bug
report is still true but at least now I can see devices that I could
not see earlier.  Give this a try and please post results.
Maybe this will be a workaround until the kernel problem is fixed
properly.

---

### Post by weezer316 on 2008-12-20
Billxy,


Here you go. Belkin wirelss adaptor tested 2 hours ago on a vista laptop and known to work on a previous installation of ubuntu


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


As you can see, exactly the same as when nothing is there! the usb port work on the pc under windows, and the devices work.

That link has alot in it. Is there a bug preventing them from being recognised?

---

### Post by Billxyzzy on 2008-12-20
Your hardware is not responding like mine.
Here is my lsusb output:
bill@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 007: ID 050f:0003 KC Technology, Inc. KC82C160S Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bill@ubuntu:~$ 
Right now I am at a loss.
because your lsusb is not showing anything I just don't know what
to  suggest.  I suspect your system is never going to respond while
nothing shows up in lsusb.
Like you,  my win installation is fine. It has got to be something in
the kernel.

---

### Post by nicov2 on 2008-12-20
I'm having the same problem, though I'm not on the 64-bit platform. This is my first time with ubuntu and when i first installed it, usb devices would work sporadically. flash drives would often mount automatically, but if i unmounted them and tried to remount them again, they wouldn't be recognized until i rebooted. now nothing works, and my lsusb is the same with or without devices plugged in. 

i've reinstalled ubuntu a couple of times, and it always sees the liveusb drive. 

also, on bootup, it sometimes gives repeated messages about not being able to enumerate the usb hub on various ports, if that could be significant, i can write down details.

any help would be appreciated.

---

### Post by weezer316 on 2008-12-21
I know, its crazy. I tried both kernels I have here, 2.7 and 2.9 but neither works.

Could someone point me on how to compile a new kernel? I have seen guides and tried to follow them but when it comes to the options you have with your kernel I stopped because I simply dont know what is what.

Wheeler

---

### Post by Billxyzzy on 2008-12-21
I am going to join you there.
I also would like to try to compile a new kernel.
It looks like we have to do this on our own as the developers
don't seem to think this is a big problem right now.
Post what you find and I will do the same.  I started to look
at the compiler issue but was only looking in passing and did
not really start to study.  Now it is time to hit the books.
Lets go.

---

