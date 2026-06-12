---
title: "Not booting correctly - ASUS M51 Series M51TA-X2 w/  ATI Mobility Radeon HD 3650"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by BigIslandVegan on 2008-08-24
Shortly after or during the booting of the kernel from the install CD the installation stops with a blank display.

We have tried Ubuntu 8.04 for AMD 64, 8.10 latest alpha for i386 / 32, Ubuntu 8.04 alternate, openSUSE 11-KDE, Mandriva Linux One 2008, Fedora 9 & 10 and probably some others that I am forgetting but no luck on any of them. I might be able to get him to try the latest SUSE Linux Enterprise Desktop later today...but I have serious doubts.

The computer was purchased from Newegg, a model that seems to be unique to Newegg as it is not even listed on the Asus site.

Item#:N82E16834220349 on Newegg

I would appreciate some suggestions / ideas on this.

I have spent months lobbying my friend to move from Mac to Linux and now he does and has all these issues. I would like to help him to have a workable linux system but I'm not sure what to do next.

---

### Post by kjb34 on 2008-08-24
Have you tried the regular 32 bit 8.04 or Linux Mint 5? They might work

---

### Post by BigIslandVegan on 2008-08-25
I believe we tried the 8.04 alternate for 32 bit computers, same thing.

I have NOT tried Linux Mint yet, do you think it would work?

I'll see if he can go through his bios settings with me.

Aloha

---

### Post by kjb34 on 2008-08-25
What kind of hardrive do you have? If it is SATA you may have change the setting in your BIOS. I am having a similar problem intsalling the 64 bit version but the 32 works fine. It seems like there is some sort of glitch with the Asus mobos. If i figure out to change the settings in my BIOS I'll post it here.

---

### Post by BigIslandVegan on 2008-08-25
I don't know what kind of hard drive is in there...it's the stock hard drive that comes with it. The manufacturer's site doesn't even list this model and the Newegg specs do not specify the interface for the hard drive - it does say there is an E-SATA port though, but that doesn't say much.

This laptop I mentioned uses the new Turion *Ultra* which has some differences from regular Turion. I understand that there is also a new AMD chipset in use on this laptop.

How likely is it that it simply won't work with any linux at all right now?

Should I explore PC-BSD, Solaris, or Nexenta (Solaris kernel, Ubuntu on top)?

---

### Post by kjb34 on 2008-08-25
You could try those. Can you get into the BIOS? it should have what type of harddrive it is. It if is a SATA or SATA II that might be the cause of your problem. After going to the Asus website I have this to be a common problem. You supposed to be able to fix with a BIOS update but that doesn't work for some people. There was supposed to workaround posted but apparently it's no longer there.

---

### Post by Yellow Pasque on 2008-08-26
I had this problem too with a Radeon HD 3200 IGP. The last release of the open-source radeonhd driver doesn't seem to do mode-setting for The HD 3xx0 series. The latest version available with git works, but of course, that doesn't help with a fresh install. I decided to toss in an old Radeon X300SE that I had lying around and use that until I could build the latest radeonhd source.

---

### Post by kjb34 on 2008-08-30
Try this when you boot the cd choose your language then press F6 and type this after -- all_generic_id floppy=off irqpoll this fix your problem

---

### Post by TheBramp on 2008-09-01
I have just been playing with a ASUS X56Se, which appears to have the same hardware as a ASUS M51Se.

Linux won't boot on it unless I use this kernel parameter: acpi=off, perhaps you have a similar problem to me?

Once Linux does boot, I can't get X to start, but that is a different problem :)

Andrew

---

### Post by highlandsun on 2008-09-02
> **TheBramp said:**
> I have just been playing with a ASUS X56Se, which appears to have the same hardware as a ASUS M51Se.


X56Se uses Intel chips, the M51TA is all AMD. Quite different...

---

### Post by parimo on 2008-09-08
Hello, I have the same laptop and I want to boot a LiveCD but I cant boot from it, I tried F11, F12, but it doesnt boot, when I go to the BIOS with F2, I cant make the first boot device to be the CD-ROM. Have you got any ideas?

---

### Post by soulsource on 2008-09-08
Ok, acpi=off made the life-cd boot for me, yet I don't intend to install a system that isn't able to use acpi on a laptop. Right now I'm downloading the 32bit version of 8.04 and the alpha of intrepid. Maybe one of those works. I'll report if I have any success.

@parimo: you can try to press ESC instead of F2. This should bring up a menu which let's you choose a device to boot from.

---

### Post by soulsource on 2008-09-09
Ok, neither does... Yet 7.04 boots with some ata errors. Anyhow, I'll install 8.04.1 and try to get a kernel running.

---

### Post by markbuntu on 2008-09-10
Nobody ever promised that 8.10 would work. Have you reported your results to the Intrepid developers?
I am sure they would be interested in your experience.

---

### Post by BigIslandVegan on 2008-09-24
Hmm, not sure what you mean by "nobody ever promised 8.10 would work" I don't think I suggested that :-) I'm just hopeful that it will.

I was looking around and spent some time trying to figure out how to efficiently communicate with developers of Intrepid but have not found something simple and effective.

Any friendly suggestions would be appreciated.

Aloha

---

### Post by UbuWu on 2008-09-24
> **BigIslandVegan said:**
> 
I was looking around and spent some time trying to figure out how to efficiently communicate with developers of Intrepid but have not found something simple and effective.

For problems/bugs launchpad is the most effective way, but I just saw you found that.

---

### Post by nacarino on 2008-10-02
I have successfully been able to install on a M51TA-X2 with acpi=off when booting.

Now I have an error with the graphics as it seems the proprietary driver of ATI only accepts the Radeon 3200 graphics. It seems that the laptop comes with two different chipsets for graphics. I'm supposing that this is to be able to switch when you are running on battery or something of the sort. The driver does seem to find both adapters when using the aticonfig --list-adapters command but when I force it to load the Mobility Radeon HD 3650 graphics, the X server gives an error saying that the BIOS information for the card is invalid and basically gives a black screen.

I'm using the 8.9 proprietary drivers from ATI.

Anyone else have this problem?

Btw, I loaded the HD card with the following command

aticonfig --initial --adapter=1 --input=/etc/X11/xorg.conf

---

### Post by Yellow Pasque on 2008-10-02
nacarino, check the manufacturer's site for a BIOS update, and if that does not fix the problem, report it to Asus.

---

### Post by JohnnyPea on 2008-10-07
is there any effective solution for that? I mean no hacks...is the final 8.10going to work ?

---

### Post by milkathecow on 2008-10-21
I am a total newbie to linux and am looking into installing ubuntu on an X56se-ap063 and have found some info that might help you a little. 

there is an issue with the 2 memory sticks of ram, take 1 out and go with 2Gb physical ram. 

add on the startup mem=2900M 

i'm looking into 8.10 to see if it solves some issues and will look more into it before installing it.

---

### Post by x-tir on 2008-10-23
Hi, everyone.
I got the M51Ta04 two weeks ago and all this time I've tried to solve the same problem.
First of all, an "acpi=off" option helped to boot from LiveCD (8.10 beta amd64). Then long installation procedure followed (even on P4 home computer it works faster). Booting the system always finishes with ** Checking battery state* or some. Thus I need to kill X-server and start it again using tty1. Hello, desktop!
System works slowly. And every time you boot you have to do all that to achieve GNOME or some...
Now I'm going to try to install Linux Mint 5... but that's not a thing I want... :(

upd: there is some EnvyNG that installs ATI and nVIDIA drivers and it says there was no driver for the HD 3650. And I still can't find the way to make display work at 1400x900 resolution.

---

### Post by geckon on 2008-12-13
Hi everyone,
I have Asus M51TR-AS068c and I have the same problem. Live cd boots only with "acpi=off". But I want to use ACPI, does anybody know how to get it working? I hope there is a solution.
Thanks

---

### Post by geckon on 2008-12-15
Well, good news, maybe. [Here]("http://bugzilla.kernel.org/show_bug.cgi?id=11541") is maybe the solution of the whole problem. One guy (he's called paulemeister) confirmed it [here]("http://forum.notebookreview.com/showthread.php?t=284429&page=21"). There is some problem with 3D, but it's better than "acpi=off", at least I guess. 

I hope it really works. I can't try it for now, because my laptop doesn't want to launch xserver. I'm trying to solve this, but I still don't have it. 
Maybe you are luckier.

---

### Post by L2L5 on 2009-03-08
> **TheBramp said:**
> I have just been playing with a ASUS X56Se, which appears to have the same hardware as a ASUS M51Se.

Linux won't boot on it unless I use this kernel parameter: acpi=off, perhaps you have a similar problem to me?

Once Linux does boot, I can't get X to start, but that is a different problem :)

Andrew

Hey! Did u get the Asus m51 to boot and install ubuntu? If so, pls explain it to me as well...cuz I've been trying for months. thx a lot

---

### Post by prince_niceguy on 2009-03-27
> **L2L5 said:**
> Hey! Did u get the Asus m51 to boot and install ubuntu? If so, pls explain it to me as well...cuz I've been trying for months. thx a lot

Yup I got jaunty beta to work on my this baby... make sure you do the following as this guy says on the [blog]("http://linux4humanbeing.blogspot.com/")...

compiz is not working for me too..

---

