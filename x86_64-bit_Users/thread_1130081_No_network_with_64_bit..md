---
title: "No network with 64 bit."
date: 2009-04-19
forum: x86 64-bit Users
---

### Post by stans on 2009-04-19
OK - my journey to upgrade to 64 bit from 32 bit has taken an interesting turn... networking doesn't work with 64 bit Ubuntu OR Debian - but DOES work with 32 bit Ubuntu.

The NIC is onboard the motherboard so I tried a Linksys NIC with no change in behavior.

The motherboard must be my culprit. Has anyone else experienced this before ?

---

### Post by cariboo on 2009-04-19
How about posting some details, like what chipset does you onboard nic use. To find out open a terminal and type:

```
sudo lshw -C network
```

Jim

---

### Post by stans on 2009-04-19
Not much info posted cause I really didn't know what would be useful.

Interesting - I see the width as 32. How is that set ?




 *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:06:0c.0
       logical name: eth0
       version: 13
       serial: 00:17:31:8a:cd:f8
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.102 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s

---

### Post by Yellow Pasque on 2009-04-19
There seems to be a problem with the skge module in 64-bit. Try passing mem=3G to the kernel and see what happens.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131965](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131965)

BTW, what version of Ubuntu are you using? (Your profile says 8.04, but a lot of people don't update that.)

---

### Post by stans on 2009-04-19
I'm trying to install 8.10 - 64 bit.

I don't understand your suggestion of passing mem=3G to the kernel.

How does one do it ?

Most interesting reference you gave to the bug report - seems to be my problem exactly.

"To work-around, reloading the skge module works, making me strongly suspect the driver rather than hardware."

How can I reload the skge module ?

---

### Post by Yellow Pasque on 2009-04-19
Using boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Reloading module:
```
sudo modprobe -r skge
sudo modprobe skge
```

---

### Post by stans on 2009-04-19
Thanks for your assistance... 

Just tried both suggestions to no avail.

If the driver is 'buggy' I would think it needs to be fixed and there would be no 'work arounds'.

Interestingly enough, the same driver was selected when I had  LINKSYS nic for testing.

Networking fails with the Debian install as well.

---

### Post by marcelkoopman on 2009-04-20
Hello,

Try with the jaunty 64 bit release, this should contain a newer kernel and thus have newer drivers. 

Let us know if that helps.

---

### Post by stans on 2009-04-20
Thanks for the suggestion. 

What release is Jaunty ? The interchangeable use of names and release numbers continues to confuse me.

Is there any way to find out if this driver has been repaired in the new release ?

---

### Post by lisati on 2009-04-20
> **stans said:**
> Thanks for the suggestion. 

What release is Jaunty ? The interchangeable use of names and release numbers continues to confuse me.

Is there any way to find out if this driver has been repaired in the new release ?

"Jaunty" is the name for version 9.04, due for "official" release in the next few days.


Opinion: I don't think the networking issue is the fault of the 64-bit version being installed, but is more likely to be a driver and/or hardware issue. One of my laptops has the 64-bit version of 8.10 installed, and my "good" desktop has the 64-bit version of 9.04 installed: both seem to be able to handle networking without any hassles.

---

### Post by stans on 2009-04-20
Ah - so that's why I don't see it available now.

There may not be an interest in repairing that driver since the release isn't current any longer.

Look back in these replies - I was referred to a bug report that hits the nail right on the head regarding the SKGE driver.

---

### Post by stans on 2009-04-20
My optimism in installing Jaunty to 'see if it will work' has just dropped as I saw a post from someone with my DHCP problem - running Jaunty.

I'd love to get Ubuntu installed -

"Opinion: I don't think the networking issue is the fault of the 64-bit version being installed, but is more likely to be a driver and/or hardware issue."

Yes, the SKGE driver that is bundled with the release. The hardware works with 32 bit.

---

### Post by stans on 2009-04-20
OK - just installed 9.04 and still no networking.

Is there an alternative to SKGE ?

If not, how can I go forward with Ubuntu ?
------------------------------------------------------------------------------------

Followup: disable the onboard nic, install a LINKSYS nic, and reinstall openSUSE from the .iso CD.

It now works. 

Why openSUSE you ask ? Well - it probed my monitor correctly the first time - something Ubuntu hasn't done over several installs on several different machines. 

I just got tired of it.

---

