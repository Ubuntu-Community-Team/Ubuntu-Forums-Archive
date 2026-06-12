---
title: "Cannot access the hardware clock by any known method"
date: 2005-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by tweek! on 2005-01-13
I get this error on boot:

Setting the system clock using the hardware clock as reference
Cannot access the hardware clock by any known method

Anyone have an idea why this is happening?

---

### Post by dJCL on 2005-01-13
Ditto on my AMD64 laptop, but I definatly have the right time in the corner here...

Mobile AMD64 2800+

JC

---

### Post by HankB on 2005-01-15
I've noticed that too on my ABIT AV8. I have no idea why that's there.

My system has the right time too, but that could be because it uses ntpdate to sync up with ntp.ubuntu.org.

I also see a warning about not finding a file system on one of the partitions, but it is not looking for the filesystem that is indicated in /etc/fstab. I think it might be some sort of probe.

---

### Post by dJCL on 2005-01-17
Even when my router is not online I still get the message and still get the proper time on my system. It appears to get the right time even if it's giving these errors.

---

### Post by ernstp on 2005-01-17
Yes, I see two of those every time I boot!

---

### Post by dmatrix on 2005-01-17
Same problem here on an ASUS AMD64 mobo.

---

### Post by merc on 2005-01-24
I have a shuttle sk83g (uses the km800 chipset) and I get the same message. Twice during boot.

---

### Post by xpt on 2005-01-24
Same here on ASUS K8V mobo, AMD64 2800+

I think we can now say this is a Ubuntu bug.

---

### Post by smdeep on 2005-01-25
Same here on a MSI Neo Platinum board. 

Any fix?

---

### Post by mindwarp on 2005-01-25
Same problem on a emachines AMD64 M6805 laptop.

---

### Post by Kareema on 2005-01-25
And again: Same problem on an Acer Ferrari 3400 laptop

---

### Post by martijntje on 2005-01-25
[QUOTE=Kareema]And again: Same problem on an Acer Ferrari 3400 laptop[/QUOTE]
 Same here. Doesn't seem to be doing any harm though. Time is still right.

---

### Post by Giubodi on 2005-01-25
Same thing, but after few days it simply disappeared. I don't have idea of what it could be... Maybe some system upgrade (I've made some installations in theese days) fixed it.

---

### Post by 8oluf7 on 2005-01-25
Same problem on home-built SFF using MSI MS-7034 (K8NM-FISR) mobo - uses nForce 3/250 chipset. 

Not fatal - but I would like to know what's causing it, and remove it if possible.

**Update** - Problem solved. I assume that one or other of the updates I've installed using Synaptic has done the trick.

---

### Post by Compwiz on 2005-01-25
same here: AMD64 3000+ Nvidia Nforce3

---

### Post by ebonflame on 2005-01-25
Ditto

Amd Athlon64 3200+, ASUS K8V SE Deluxe

---

### Post by xkfu on 2005-01-25
Not only I have the same problem, but I also noticed my Windows XP time is off 6 hours after I logged on to ubuntu.

AMD 64 2800+

Windows XP and 4.10 The Warty Warthog amd64

Both OSs use central time zone. ubuntu time is displayed correctly, I also used ntpdate to synch with internet time server, there is no time change. However, once I logged back to Windows XP, I noticed the time has been changed 6 hours, exactly the difference between central time and GMT. Under Windows XP, I resynched the time with internet time server, the time is changed correctly. But once I back to Windows XP after I logged on to ubuntu, the Windows XP time is changed again by 6 hours! So my Windows XP time is always 6 hours off if I use ubuntu. A bug? Windows or Ubuntu?

---

### Post by martijntje on 2005-01-26
[QUOTE=xkfu]Not only I have the same problem, but I also noticed my Windows XP time is off 6 hours after I logged on to ubuntu.

AMD 64 2800+

Windows XP and 4.10 The Warty Warthog amd64

Both OSs use central time zone. ubuntu time is displayed correctly, I also used ntpdate to synch with internet time server, there is no time change. However, once I logged back to Windows XP, I noticed the time has been changed 6 hours, exactly the difference between central time and GMT. Under Windows XP, I resynched the time with internet time server, the time is changed correctly. But once I back to Windows XP after I logged on to ubuntu, the Windows XP time is changed again by 6 hours! So my Windows XP time is always 6 hours off if I use ubuntu. A bug? Windows or Ubuntu?[/QUOTE]
 The bug is with windows.

Windows has trouble with Timezones. What it does is get the time from the NTP-server, then add the time-difference between you and GMT, and set that as the local time. <-- this is incorrect.

Ubuntu gets the GMT time from the NTP server, sets that as the local time, and displays your local time by taking the GMT time from the hardware clock, and adding the time difference. <-- this is correct.

According to protocol, the time stored in the BIOS should be the GMT time. Therefor, Ubuntu behaviour is correct, and windows is, once again, being plain stupid.

The best solution is to remove Windoze. It ain't useful anyway, and should save you some Gigs...

---

### Post by chryz on 2005-01-27
[QUOTE=xpt]Same here on ASUS K8V mobo, AMD64 2800+

I think we can now say this is a Ubuntu bug.[/QUOTE]

I have a Medion CAD2000 laptop with this exact problem, and I previously had Mandrake 10.1 RC1 AMD64 installed and that distribution displayed the exact same error. Didn't get the error at shutdown though... which might imply that something get loaded in the meantime. I think this is a problem for all distroes - just not enough AMD64 users to make it show.   :-#

---

### Post by Sam on 2005-02-18
I have the same problem, the message also appears twice during boot.

AMD 64 3400+ / ASUS K8N-E.

---

### Post by dewey on 2005-02-19
I have been having that same error, and my windows clock also changed repeatedly, I haven't noticed it lately.
AMD 64 3000+
DFI Lanparty UT NF3 250gb socket 754

---

### Post by tonym on 2005-02-20
This is a known fault.

See [https://bugzilla.ubuntu.com/show_bug.cgi?id=1659](https://bugzilla.ubuntu.com/show_bug.cgi?id=1659)

---

### Post by dmatrix on 2005-03-18
What can we do to get this bug fixed for Hoary Final?

---

### Post by squidgit on 2005-03-21
Was having that prob.  Flashed BIOS and all is now well.

---

### Post by dmatrix on 2005-03-23
What BIOS did you flash from and to?

I currently am running 1003 but am willing to flash up to 1005.

---

### Post by Epicenter on 2005-04-08
I have the second-most recent BIOS For my VNF3-250 A64 board from Chaintech (new one just changes a default memory timing option, not relevant) and I get this error, then it tries to set system clock based on hardware, and then stops and never finishes. :( I can't run the Live CD at all because of this. Is there any workaround? Time is perfect in XP.

---

### Post by Diogo Boito on 2005-05-18
Same problem here on a AMD64 Asus, but I do not have the righ time and I can't fix it.

---

### Post by FrzzMan on 2005-06-23
Well, could you all please donot add more "Same here" replies :(

Someone know how to fix this?

---

### Post by thingy on 2005-07-02
I had the same error, and after compiling a custom kernel the problem was gone.

I did compile rtc support statically into the kernel, so if its a timing issue with the module loading then I will have circumvented it.

Asus KV8 Pro
Athlon 64 3700
Ubuntu 5.04

---

### Post by Turmoyl on 2005-07-16
Same thing here on an ASUS K8N and AMD64.

---

### Post by Jeffj on 2005-08-04
One part of the issue can be fixed with the following according to comments on bug report 1659:

#mv /etc/rcS.d/S18hwclockfirst.sh /etc/rcS.d/S26hwclockfirst.sh

---

### Post by cnspy on 2005-08-09
[QUOTE=martijntje]The bug is with windows.

Windows has trouble with Timezones. What it does is get the time from the NTP-server, then add the time-difference between you and GMT, and set that as the local time. <-- this is incorrect.

Ubuntu gets the GMT time from the NTP server, sets that as the local time, and displays your local time by taking the GMT time from the hardware clock, and adding the time difference. <-- this is correct.

According to protocol, the time stored in the BIOS should be the GMT time. Therefor, Ubuntu behaviour is correct, and windows is, once again, being plain stupid.

The best solution is to remove Windoze. It ain't useful anyway, and should save you some Gigs...[/QUOTE]

Maybe the ubuntu is smarter than windows. But it causes something wrong on my computer. 

The timing show on my laptop and the emacs app is the local. But when I use the Version control function of emacs, it use the GMT time as the update log time.

I hope anyone can help me to fix this problem.

---

### Post by Steve1961 on 2005-08-16
Same problem on MSI neo4 Platinum.  It doesn't seem to make any difference because the right time is there when Ubuntu boots.  However, when I boot into XP afterwards it's set the XP clock back 1 hour.  Any ideas?

---

### Post by Ptero-4 on 2006-08-12
> **martijntje said:**
> The bug is with windows.

Windows has trouble with Timezones. What it does is get the time from the NTP-server, then add the time-difference between you and GMT, and set that as the local time. <-- this is incorrect.

Ubuntu gets the GMT time from the NTP server, sets that as the local time, and displays your local time by taking the GMT time from the hardware clock, and adding the time difference. <-- this is correct.

According to protocol, the time stored in the BIOS should be the GMT time. Therefor, Ubuntu behaviour is correct, and windows is, once again, being plain stupid.

The best solution is to remove Windoze. It ain't useful anyway, and should save you some Gigs...

I agree with you here. Windoze is just screwing things up and eating HD space by the truckload.

---

