---
title: "Computer is bogging down when opening apps"
date: 2008-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by shane2peru on 2008-02-07
Ok, I'm a serious multi-tasker and that is one of the many reasons I love Linux it is for true multitaskers. :)  Anyway, I have recently installed the 64 Gutsy, and all is up to date.  Using it daily, and now when I open up Open office, or Firefox, it seems to take forever!  I thought my swap was turned off, but sure enough it is up and running.  It reminds me of my Windows days!  <---  it is that bad!  I'm not sure where to start trouble shooting this.  When I ran the 32bit, I didn't have this problem, so there is something not setup correctly somewhere, or something.  I know all of this is kind of vague, I'm hoping someone can give me some pointers on where to start, or look.  Thanks.

Shane

---

### Post by crjackson on 2008-02-07
> **shane2peru said:**
> Ok, I'm a serious multi-tasker and that is one of the many reasons I love Linux it is for true multitaskers. :)  Anyway, I have recently installed the 64 Gutsy, and all is up to date.  Using it daily, and now when I open up Open office, or Firefox, it seems to take forever!  I thought my swap was turned off, but sure enough it is up and running.  It reminds me of my Windows days!  <---  it is that bad!  I'm not sure where to start trouble shooting this.  When I ran the 32bit, I didn't have this problem, so there is something not setup correctly somewhere, or something.  I know all of this is kind of vague, I'm hoping someone can give me some pointers on where to start, or look.  Thanks.

Shane

While I don't really have an answer for you, I have to wonder if this is something that just started happening after some updates, or has it been this way for you from the start under 64-bit?

---

### Post by shane2peru on 2008-02-08
> **crjackson said:**
> While I don't really have an answer for you, I have to wonder if this is something that just started happening after some updates, or has it been this way for you from the start under 64-bit?

No, it wasn't like that in the beginning.  I setup th 64bit on a separate partition and ran it there for a bit, and then after 2 or 3 days, I was rather pleased, so I installed it on my primary partition.  It has run fine, but yesterday, seemed really slow.  I shut off Tracker (I don't like it or use it anyway).  I use Beagle, but it was the problem I killed it just in case, and still was slow.  I shut it down last night and will see if maybe something was hung up that I didn't know about.  So far seems better this morning, but I we will see as the day goes on.  Also there was a Firefox update this AM, perhaps that would fix it?  Not sure.  I will let you know.  Thanks

Shane

---

### Post by Krydahl on 2008-02-08
One common reason for slow start-up of apps is loopback not set up correctly. Check your host file to see if 127.0.01 maps to localhost and to the name of your computer.

---

### Post by shane2peru on 2008-02-08
> **Krydahl said:**
> One common reason for slow start-up of apps is loopback not set up correctly. Check your host file to see if 127.0.01 maps to localhost and to the name of your computer.

Ok, how do I do that?  I typed ifconfig, and it does show lo as 127.0.0.1  but I'm not sure if that is the same as what you are talking about.  :confused:
Shane

---

### Post by Krydahl on 2008-02-08
GUI: system -> admin -> network and select the hosts tab.

You can also look in /etc/hosts. The file should look something like:

```
127.0.0.1	localhost computername

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
```

Your IP6 stuff may not be commented out. Doing so can sometimes speed up internet access.

---

### Post by shane2peru on 2008-02-08
> **Krydahl said:**
> GUI: system -> admin -> network and select the hosts tab.

You can also look in /etc/hosts. The file should look something like:

```
127.0.0.1	localhost computername

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
```

Your IP6 stuff may not be commented out. Doing so can sometimes speed up internet access.

Ok, Mine does look like that, and I commented out the ip6 stuff, I will see if that changes my interent speed, although, I'm already pleased with it.  Are there any negatives to doing that?  

Shane

---

### Post by Krydahl on 2008-02-08
Not that I'm aware of, but I wouldn't claim to be an expert. Looks like I haven't fixed your main problem though. Sorry.

---

### Post by shane2peru on 2008-02-08
No problem, at least it would be easy to undo what I have done with the ipv6 thing.  I just commented out the lines like in the example.  Thanks anyway.

Shane

---

### Post by shane2peru on 2008-02-11
Ok, this is starting to get on my nerves.  Does anyone have any clue as to what to check?  I deleted all .config folders, except .gnome etc, because I did that when I installed.  It still seems to bog down, and not run as snappy as my 32bit did.  I may be forced to go back to the 32bit install I had, it worked well.  The work arounds (Java, Flash etc.)  seem to be fine for me for 64, but this problem of bogging down is really annoying.  I don't like waiting for my computer to catch up to me. 

Shane

---

