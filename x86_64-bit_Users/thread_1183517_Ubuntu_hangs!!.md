---
title: "Ubuntu hangs!?!"
date: 2009-06-10
forum: x86 64-bit Users
---

### Post by davbren on 2009-06-10
Hey all, this is new problem for me, I'm reinstalling ubuntu along side windows 7 on a machine. I'm afraid that Ubuntu is hanging during the install. I can only get as far as a blank screen on the live cd and as far as partitioning in the "Install ubuntu" section. 

The mouse stops moving and activity stops. I noticed that the caps lock light on my keyboard started to flash when all this happens.

Any ideas?

---

### Post by davbren on 2009-06-11
*bump*

---

### Post by jocko on 2009-06-12
That looks like a kernel panic, i.e the kernel encounters a problem it can not recover from, so it locks up as a way to prevent damage.
There could be many reasons for that, but check the ubuntu cd for errors (boot up with the cd and when you get the cd boot menu select the option to check the cd).
If there is nothing wrong with the live cd, try installing with an alternate install cd or a live usb stick.
If none of this works, you may have a problem with some of your hardware.

---

### Post by majamba on 2009-06-12
i agree it might be hardware issue

try any of the other linuxes such as fedora and opensuse

see if they work because i had system a very old system i wasnt  able to boot any of the linuxes

---

### Post by Villiam on 2009-06-12
In windows xp I use Wubi to install Ubuntu. I am not sure if it works in Windows 7 or not. You may like to to try it: [http://wubi-installer.org/](http://wubi-installer.org/)

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by ddales on 2009-06-12
Sounds like a faulty CD to me.  I've experienced this problem before, reburned the CD, everthing fine thereafter.

---

### Post by davbren on 2009-06-12
Hey all, it was hardware, I burnt the cd a few times to check too. In the end it turned out to be a harddrive. I'm not sure what the problem was, it was working fine before. Meh, happens sometimes. Cheers peeps!

---

### Post by davbren on 2009-06-12
Small issue, I couldn't get into ubuntu so I thought I'd reinstall GRUb I tried that, no luck. so I thought I'd reinstall again. I'm getting the hang *again* I have no clue what it could be. The *only* possibility I can think of is the graphics card but I'm not sure what bearing that coul possibly have...

---

### Post by davbren on 2009-06-16
Ok it turns out that it probably is the graphics card. Do you think that installing using the alternative cd instead might work and then hoping it lasts long enough to install the driver before hanging?

---

### Post by davbren on 2009-06-17
*bump*

---

### Post by merlinus on 2009-06-17
The only way to find out is to try it.  The alternate install cd will often work when the live one will not.

BTW, you never mentioned which graphic card...

---

### Post by davbren on 2009-06-18
Well the alternate cd installed fine, not grub won't work. the boot order is fine the menu even starts to come up but it hangs on Grub loading, please wait...

This is starting to drive me nuts. I've tried reinstalling grub but i can't coz when i bootinto the live cd i get a kernel panic.

I'm using an Nvidia Geforce 8300GS...

---

### Post by davbren on 2009-06-25
Ok this is really starting to get to me... 

I installed mandriva on my desktop, just about everything is hunky dory. I can really see why it is the linux for beginners. However, it just isn't Ubuntu. 

Why is the Ubuntu kernel panicking and the mandriva one isn't?? 

Also the stuttery sound is starting to ake me twitch, its not a sexy look. I do quite like KDe though i must say, I can still get that with my Ubuntu tho :( 

I really need help with this.


Plz...

---

### Post by clackamas on 2009-06-29
Try adding 'acpi=off' to the boot options.

This is not desirable, but some buggy ACPI can cause problems.  If that does work, then search for folks with your motherboard and see if they have a further work around.

---

### Post by nmaster on 2009-06-29
> **Villiam said:**
> In windows xp I use Wubi to install Ubuntu. I am not sure if it works in Windows 7 or not. You may like to to try it: [http://wubi-installer.org/](http://wubi-installer.org/)

i've heard that wubi doesn't work with windows 7.

---

### Post by davbren on 2009-06-29
> **clackamas said:**
> Try adding 'acpi=off' to the boot options.

This is not desirable, but some buggy ACPI can cause problems.  If that does work, then search for folks with your motherboard and see if they have a further work around.

Hmm just tried this and it still hangs... cheers for the input.

Any other ideas?

---

