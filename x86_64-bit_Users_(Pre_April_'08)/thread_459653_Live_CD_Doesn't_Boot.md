---
title: "Live CD Doesn't Boot"
date: 2007-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by teejay17 on 2007-05-30
I wasn't able to boot into the 64 bit version of Ubuntu or Kubuntu using the Live CD, although the 32 bit worked no problem. 
I have an AMD Athlon 64 3500+
CPU GHz 2.2
cache 512 kb
I also have an [B]ATI Radeon x850 XT Platinum Edition video card. 

[/B]

---

### Post by CrazyG on 2007-05-31
I have had intermittent problems booting from LiveCd (Ubuntu 64 6.06 only).  I had no problems the first time I used it, 2nd time I did, 3rd time I didn't.

Last week the LiveCd kept hanging every time I loaded it, and I saw a message re "kernel panic - not syncing:  Machine check". The hanging suddenly stopped  after I hit F6 and entered "acpi=off" in the parameter list (with "quiet" "splash", etc).  I have since reinstalled Ubuntu and have not tried the LiveCd on the new install.

Good luck!

PS:  I have an NVidia video card, with 1 GB RAM

---

### Post by ronocdh on 2007-05-31
> **teejay17 said:**
> I wasn't able to boot into the 64 bit version of Ubuntu or Kubuntu using the Live CD, although the 32 bit worked no problem. 
I have an AMD Athlon 64 3500+
CPU GHz 2.2
cache 512 kb
I also have an [B]ATI Radeon x850 XT Platinum Edition video card. 

[/B]
Can you give us more info on the error that occurred? Crazyg's post is a very good example of what to list. Are you positive you got a good burn? (Did you verify the checksum on the main screen of the live CD?) Is it an X failure, what?

---

### Post by teejay17 on 2007-05-31
> **ronocdh said:**
> Can you give us more info on the error that occurred? Crazyg's post is a very good example of what to list. Are you positive you got a good burn? (Did you verify the checksum on the main screen of the live CD?) Is it an X failure, what?
Sure thing. 
I'm pretty sure that the burn is all right. I have one Kubuntu and one Ubuntu 7.04 64 bit that came right from "Shipit." They both don't work. I also decided to download from the Net a 64 bit version of Ubuntu 7.04. It also doesn't work. 
I would have checked the integrity of the CDs, but the CDs don't even load. I don't get a splash screen, text, nothing. All the CDs do is reboot the machine almost instantly. There's no warning text or anything. 
I hope this helps; this is all the information I'm able to provide.
With the 32 bit editions, however, everything boots normally without a problem--into the Live CD, and onto the hard drive too (I now have Kubuntu 7.04 installed).

---

### Post by ronocdh on 2007-05-31
> **teejay17 said:**
> Sure thing. 
I'm pretty sure that the burn is all right. I have one Kubuntu and one Ubuntu 7.04 64 bit that came right from "Shipit." They both don't work. I also decided to download from the Net a 64 bit version of Ubuntu 7.04. It also doesn't work. 
I would have checked the integrity of the CDs, but the CDs don't even load. I don't get a splash screen, text, nothing. All the CDs do is reboot the machine almost instantly. There's no warning text or anything. 
I hope this helps; this is all the information I'm able to provide.
With the 32 bit editions, however, everything boots normally without a problem--into the Live CD, and onto the hard drive too (I now have Kubuntu 7.04 installed).
Are you sure that in your BIOS settings you have "boot from CD" enabled, and also that you have your CD drive as the primary boot device (followed by hard drive, probably)?

---

### Post by teejay17 on 2007-05-31
> **ronocdh said:**
> Are you sure that in your BIOS settings you have "boot from CD" enabled, and also that you have your CD drive as the primary boot device (followed by hard drive, probably)?
Absolutely. 
I was able to install Kubuntu 7.04 32 bit edition off of the Live CD. I have to press F8 to get to the temporary boot device screen, which is what I always do to boot of the CD ROM, and works no problem for (K) Ubuntu 32 bit. Not so for the 64 edition. 
I get rebooted right away, as soon as a start booting into the Live CD.

---

### Post by Power_Pickle on 2007-12-21
I have the same video card and with the Ubuntu AMD64 I'm experiencing the same behavior.

The motherboard is an ASRock 939Dual SATAII.

---

### Post by Guigo! on 2008-01-05
Hello I'm new using Ubuntu...

And I have a problem like the one described, but a little different
Last night I downloaded the Ubuntu 7.10 from the Ubuntu's web site, also a server is located in my country, so I selected that one.

Everything's right by now, when I came, I burned the CD image with Alcohol 120% 1.4.8
and no problem given while burning, or after it
The CD was burned right

I tried booting from the CD, and yes, it boots, but there's a little problem, after selecting the right language (Spanish), I also selected the Screen Size (1280x1024)... Hit on "Start or Install Ubuntu"
the message that says "Loading Linux Kernel" appeared, then the black screen with the Ubuntu Logo appears also... and... nothing more, stays there many time without changing, without anything... even the keyboard crashes because I press the Caps Lock key and the corresponding led doesn't blink.

I thought that maybe what made the system load crash was the optioins that I selected, so, what I diid was start again from the CD and don't select any option, I left the language in English, and the Screen Size with VGA... and the same error

This is how my screen stays...
[IMG]http://i69.photobucket.com/albums/i50/guigomora/P1030620.jpg[/IMG]

My computer features:
P4 2.80Ghz HT
512 RAM DDR
Motherboard AsRock 775i65GV
BIOS American Megatrends P1.40
160GB HD (in 2 partition of 100GB and 60GB)
nVidia GeForce4 MX4000 128MB
:(

Some help please, I really would like to start using Ubuntu

Down there's my MSN, any help would be apreciated

---

### Post by 6568912 on 2008-01-09
try booting in a safe mode:)

---

### Post by Guigo! on 2008-01-09
:oops:
And how?
There's any command that I enter for that?

---

### Post by 6568912 on 2008-01-09
when you boot from liveCD you get menu with ubuntu logo something: 
Install Ubuntu
start in safe graphics mode <<<<you need this one :) hope it will help coz it helped me

---

