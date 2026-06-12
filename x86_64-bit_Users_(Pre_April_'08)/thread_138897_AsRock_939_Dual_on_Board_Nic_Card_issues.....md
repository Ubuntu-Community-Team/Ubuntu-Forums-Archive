---
title: "AsRock 939 Dual on Board Nic Card issues...."
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sony102600 on 2006-03-02
posted this over in "Complete Beginners" (thats what I am), but was told this might be a better place for it.

This is my first time trying to get a handle on linux, and when installing it, it failed when trying to setup the dhcp network.....

I am not using wireless.

I am running ubuntu 64 er whatever with the AsRock board in the title

I have tried going to system>devices and activating the eth0 part... doesn't really change anything, even though it says the device is active.. I did a little reading on google and it seems others may have had issues with the AsRock 939 board, but I couldn't seem to seperate whehther it was wireless issues, or with the board.....

Any ideas would be much appreciated.

---

### Post by gmontag on 2006-03-03
Easiest option is to add another network card or wait.  The next ubuntu release may have the kernel support for the network card.  For the amount of time needed to fix this issue I would go buy a cheap card to add in.  $8-10 dollars stills leaves this motherboard a bargain.  You may want to go back and reinstall ubuntu in 32 bit mode as well.  The 64 bit version is a little rough for a newbie.

---

### Post by Spoofhound on 2006-03-04
I agree with gmontag. I have the same board and the same issue. My solution was to reuse my old network card (the asrock was a mobo upgrade on my system).
In addition, I would also recommend using 32 bit Ubuntu. I dual boot 32 bit and 64 bit and I find 32 bit generally less hassle i.e. I don't have to spend as much time tweaking things - but this is just my personal preference

---

### Post by bmichel on 2006-03-06
If you want to stay with a 64bit distrib, I've got the same Mobo since few weeks working very well under Dapper AMD64. The integrated Network card has been recognized without issue. But you can have other problems with Dapper which is still in developement stage...

---

### Post by tpoindex on 2006-03-07
I ran into the same problem, but there is a fairly easy work-around:

Add these two lines to  **[FONT="Courier New"]/etc/modules[/FONT]**:

```
-r tulip
tulip options=0x0d
```


For background, see my post at:
[http://ubuntuforum.com/showthread.php?p=589676#post589676](http://ubuntuforum.com/showthread.php?p=589676#post589676)

---

### Post by sony102600 on 2006-03-08
thanks tpoindex, I 'll give that a try

---

### Post by sony102600 on 2006-03-08
Sorry, but the..

-r tulip
tulip options=0x0d

into the ect/module file was a no go...

thanks for the help anyway

---

### Post by siman on 2006-10-14
wow, this fixed my problem.

I have the dual939 onboard NIC connected to a router, and this green light for "connected" on the router never was lit. I could activate/deactivate the NIC, never got an error but didn't work either :-)

Right now, I ifdowned the NIC and issued the two commands from your other thread, ifup and the light is green - network works... juhu!!

---

