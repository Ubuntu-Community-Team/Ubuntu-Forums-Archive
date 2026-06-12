---
title: "[SOLVED] Live CD problems"
date: 2008-04-21
forum: x86 64-bit Users
---

### Post by jazzman65 on 2008-04-21
I thought I'd try the 64 bit version of Hardy, so I downloaded ubuntu-8.04-rc-desktop-amd64.iso file and burned it out.  However, when booting, after I choose the language option and choose the option to just try Ubuntu without installing it, the next thing I get is a message at the bottom of the screen that reads:

kernel alive
kernel direct mapping tables up to 140000000 @ 8000-e000

Eventually it proceeds to the Ubuntu splash with the orange bar _slowly_ going back and forth and then ... nothing.  Would anyone have any guidance for me?  I've tried a couple of different options to get the start-up further along, but no luck.

I appreciate any help!

---

### Post by Hopottinix on 2008-04-21
I had a similar problem with 4x DVD-RW media but a regular CD worked just fine.

---

### Post by jazzman65 on 2008-04-21
> **Hopottinix said:**
> I had a similar problem with 4x DVD-RW media but a regular CD worked just fine.

Wow!  That's pretty interesting because I had wondered if the media had anything to do with it.  I've burned a couple of different copies, but all on DVD-RW.  I'll have to try a regular CD then.

Thanks for the suggestion!

---

### Post by NightwishFan on 2008-04-21
Try this on your live cd you have now, as well.

To burn:
Check the md5sum of the download.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Use cd-r, memorex work nice.
Burn at slowest speed and check for errors.
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

To boot up:
Move over the option you wish to boot, press f6, and delete the lines "quiet" and "splash" then push enter.

See how that goes

---

### Post by jazzman65 on 2008-04-21
> **NightwishFan said:**
> Try this on your live cd you have now, as well.

To burn:
Check the md5sum of the download.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Use cd-r, memorex work nice.
Burn at slowest speed and check for errors.
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

To boot up:
Move over the option you wish to boot, press f6, and delete the lines "quiet" and "splash" then push enter.

See how that goes

Thanks NightwishFan, I appreciate the advice.  I'll try this out tomorrow.

Thanks again!

---

### Post by jazzman65 on 2008-04-22
Unfortunately, nothing has helped.  I've tried the CD-R at 4.7x speed and tried deleting "quiet" and "splash" and I'm still getting the same results.  I'm wondering if it could have anything to do with the nVidia glx-new driver or something like that?  I'm still pretty much a noob, so I'm just not sure what's going on.

---

### Post by jazzman65 on 2008-04-22
Well, I'm disappointed, but guess I'll have to give up.  I just can't figure out how to even get the Live CD to work, no matter what I try.  I really wanted to give the 64 bit a try too.

---

### Post by NightwishFan on 2008-04-22
What was the error message you got?

---

### Post by toxicgtr on 2008-04-23
I'm getting the exact same problem as #1 post. It gets to the Ubuntu loading screen and the orange bar goes across once and when its coming back it stops half way and freezes and nothing happens.

I'll have to try some of the suggestions made above and see how i get on.

---

### Post by Amorget on 2008-04-23
If the Splash screen is still showing then for some reason your deleting the quiet and splash isn't taking correctly.  I had this exact same problem with deleting it not working but now at 1 AM I can't think of the key combination to fix it...

---

### Post by toxicgtr on 2008-04-23
Ok, this time what i did was check the md5 checksum. That was the same. Then I used imgburn to burn the Ubuntu .iso image to a cd-r at 2X speed. 

When i booted into the live cd i pressed F6 and deleted the lines "quiet" and "splash". Then it does whats in the pic below and nothing else.

[[IMG]http://img171.imageshack.us/img171/7223/p1020301ys8.th.jpg[/IMG]](http://img171.imageshack.us/my.php?image=p1020301ys8.jpg)

---

### Post by NightwishFan on 2008-04-23
Just freezes there? Try the option checking for errors, if no problem, try adding acpi=off after where you deleted quiet and splash.

---

### Post by matthias.sitte on 2008-04-23
I was also experiencing boot problems with Hardy RC. It just didn't start up although I tried also with removing the splash and quiet options as well as the acpi=off flag. Didn't help it. Actually I downloaded the RC and afterwards the daily version, MD5 hash complied with those on the internet, and I burned them only at 16x though I have a very good burner + media and never experienced *any* burn problems before.

Anyway, the symptoms:
- squashfs seemed to take long time
- modprobe experiences a crash (some NULL pointer dereference if I remember correctly)
- after a few minutes of idle waiting, CUPS starts to load but never finishes.

Finally, tried this on another machine with even worse success. Here, ``sr0'' complained about something, leaving me with this box thing (kernel didn't load).

Need hardware/software specs?

---

### Post by chrisdugdale on 2008-04-23
If you get the 'no apic' message at startup, these kinds of problems can occur. It's just a slighly incompatible thing that doesn't need fixing. Trying multiple reboots was the solution for me. Also, the Nvida driver thing, I found that i needed to select 51Hz to get mine working properly. Low cd burn speed and a correct MD5SUM seem essential.

---

### Post by toxicgtr on 2008-04-23
My specs: AMD 6000+ X2, 4GB ram, 8600GT 512mb, 400gb HDD.

---

### Post by toxicgtr on 2008-04-23
Ok, i deleted the "quiet" and "splash" did the "apci=off" and this screen appears:

[[IMG]http://img337.imageshack.us/img337/7449/p1020302eg5.th.jpg[/IMG]](http://img337.imageshack.us/my.php?image=p1020302eg5.jpg)

---

### Post by jazzman65 on 2008-04-23
> **toxicgtr said:**
> Ok, this time what i did was check the md5 checksum. That was the same. Then I used imgburn to burn the Ubuntu .iso image to a cd-r at 2X speed. 

When i booted into the live cd i pressed F6 and deleted the lines "quiet" and "splash". Then it does whats in the pic below and nothing else.

[[IMG]http://img171.imageshack.us/img171/7223/p1020301ys8.th.jpg[/IMG]](http://img171.imageshack.us/my.php?image=p1020301ys8.jpg)

This is exactly what I've been getting as well.  I've tried deleting "quiet" and "splash" and replacing them with nothing, with "irqpoll" (can't remember exactly, I'm not at home at the moment).  I've tried most of the suggestions that I've come across in the forums and I just can't quite get over the hump.  I'm pretty sure my system is 64 bit capable, but it sure seems that something is conflicting somewhere.

On the other hand, 32 bit Hardy is working like a champ!  :)

---

### Post by asiancamel on 2008-04-23
Did you connect both VGA and DVI cable to the monitor?
If you did, disconnect the DVI one. After the installation and restricted video driver installed, re-connect the DVI cable.

---

### Post by jazzman65 on 2008-04-23
> **asiancamel said:**
> Did you connect both VGA and DVI cable to the monitor?
If you did, disconnect the DVI one. After the installation and restricted video driver installed, re-connect the DVI cable.


My normal set up is the DVI cable.  My video card only has DVI outputs, but I could put the DVI/D-sub connector on and hook it up to the monitor via D-sub.  Is that basically what you mean?

And thanks for the suggestion!

---

### Post by asiancamel on 2008-04-23
My card, MSI Nvidia 8400GS has both vga and dvi. I connect both, I have to disconnected the dvi( actually I did not try disconnecting the vga, as I think that one is even normal), otherwise, the live cd won't boot up.

So I think somehow the hardware is not working well with the soft.

---

### Post by jazzman65 on 2008-04-23
Skunked again.  :(  I tried the VGA hook-up instead of DVI and no difference.  Still can't get anything to boot up.

---

### Post by toxicgtr on 2008-04-23
What a pain! So frustrating!

---

### Post by jazzman65 on 2008-04-23
It sure is!  I'm racking my brain trying to figure out what the conflict or problem might be.  Normally I like challenges like this, but this one is kicking my tail so far!  ](*,)

---

### Post by jazzman65 on 2008-04-23
Would anyone else have any suggestions?  I'm very perplexed at this point!

---

### Post by toxicgtr on 2008-04-23
Yea we need help LOL. It's stupid because it will work with the 32bit version but not 64bit. 

I had the same trouble with the Gusty release. It wouldn't boot up with the 64bit version, but chuck the 32bit version in and its all go. Weird!

---

### Post by toxicgtr on 2008-04-23
jazzman65: See theres another thread about our problem here: [http://ubuntuforums.org/showthread.php?t=764011](http://ubuntuforums.org/showthread.php?t=764011)

---

### Post by jazzman65 on 2008-04-24
> **toxicgtr said:**
> jazzman65: See theres another thread about our problem here: [http://ubuntuforums.org/showthread.php?t=764011](http://ubuntuforums.org/showthread.php?t=764011)

Hi toxicgtr.  I had seen this thread too.  I've also tried digging around the BIOS and I've tried all sorts of iterations of the boot menu:  dropping "quiet", "splash", adding other lines like "acpi=off", etc.  I've also verified my disc and the md5sum is good, but absolutely nothing seems to work.  I can't explain why, but I get the feeling that somehow my video card is to blame?  I've searched the forums for my card type and I believe I've seen others with the same card running 64 bit, but I still for some reason feel like it's my card to blame.

I'll just keep plugging away though.

---

### Post by copyleft on 2008-04-24
Hey Everyone,

I have no idea if this is the fix for all of you, but what the heck - I was experiencing similar problems with Hardy 64 for the past two days and this fixed it for me. 

On my new Dell Inspiron 530, I was experiencing the loop of endless errors and failed installs with several different versions, downloads, and copies of Hardy 64 bit.

I installed Hardy 64 today with the Alternative CD.  I followed the advice above for "aspci=off" and erased "quiet" and "splash" but still no fix.   

I then went into BIOS and changed my ATA1 from IDE to RAID.  

I found it explained here in bugs:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/153702)

This worked for me. Now I can boot into Hardy with no problems.  

You probably do not have to follow this order either, you might be able to edit BIOS first and then just install.  I didn't try it though.

Hope this works for someone... 

Especially if the floor around you has turned into a CD graveyard like mine!

---

### Post by copyleft on 2008-04-24
Just to confirm:  after changing IDE to RAID in Bios, the actual Hardy AMD64 CD (not alternative) works as a normal GUI install without making the changes to F6 in the boot options screen.

---

### Post by jazzman65 on 2008-04-25
> **copyleft said:**
> Just to confirm:  after changing IDE to RAID in Bios, the actual Hardy AMD64 CD (not alternative) works as a normal GUI install without making the changes to F6 in the boot options screen.

Unfortunately, this didn't work for me.  I'm completely baffled at this point.  Absolutely nothing I've tried has made a bit of difference.

---

### Post by jazzman65 on 2008-04-25
I'm starting to wonder if somehow I did something wrong when I built my box?  I just can't figure out why I cannot make any kind of progress.  It certainly seems like I've got the right hardware, but nothing at all changes the results I get from the Live CD.

---

### Post by Apotheosis323 on 2008-04-26
here is what worked for me... all that I did after trying everything else to get pass the splash screen lock up was hit f4 and turn on safe graphics mode... nothing else... I usually never have problems installing ubuntu but this is the first fumble I've had,I am wondering if its video-card related (or maybe processor related?) I am using a core2 quad 6600 and a nvidia graphics card.

---

### Post by jazzman65 on 2008-04-26
> **Apotheosis323 said:**
> here is what worked for me... all that I did after trying everything else to get pass the splash screen lock up was hit f4 and turn on safe graphics mode... nothing else... I usually never have problems installing ubuntu but this is the first fumble I've had,I am wondering if its video-card related (or maybe processor related?) I am using a core2 quad 6600 and a nvidia graphics card.

I think I've tried that but then again, I've tried so many different ways that I'm starting to lose count!  I've been wondering all along if it is video card related as well.  

Did you get the "kernel alive" message at the bottom of the screen before you tried this fix?  That's what I've gotten every single time.

Thanks for the help!

---

### Post by NightwishFan on 2008-04-26
I get that on mine and it works flawlessly.

---

### Post by jazzman65 on 2008-04-26
> **NightwishFan said:**
> I get that on mine and it works flawlessly.

May I ask what your system specs are?

---

### Post by NightwishFan on 2008-04-26
Kubuntu 8.04 Hardy Heron 64-bit
AMD Athlon64 x2 3800+ 2.0ghz
2x512mb ram
Integrated Nvidia Geforce 6150SE Nforce 430

---

### Post by BLTicklemonster on 2008-04-26
As far as I get is, I see where I can choose to try the cd without changing anything, or install from the cd, etc.

Nothing works from that point on. 

I've tried burning with k3b, then gnomebaker, same problem each time.

Considering that the hardy version I have on a spare hard drive has been nothing but useless due to being totally slow, and non responsive, now this, would it be too much to think that somewhere along the way someone isn't paying attention to detail? 

Just looking around, my feelings are confirmed, "this is the worst release yet".

And I love ubuntu, so this is really uncool.

---

### Post by jazzman65 on 2008-04-26
> **NightwishFan said:**
> Kubuntu 8.04 Hardy Heron 64-bit
AMD Athlon64 x2 3800+ 2.0ghz
2x512mb ram
Integrated Nvidia Geforce 6150SE Nforce 430

Thanks Nightwishfan.  Given my system specs, I just can't figure out what the problem is.  ](*,)

32 bit Hardy works incredibly well, so I'm disappointed that 64 bit is such a failure on my system.  I'll keep trying though and searching the forums for answers.  No matter what, Ubuntu still rocks and for me, it's the best system I've ever used!

---

### Post by NightwishFan on 2008-04-26
Also try an earlier 64bit or perhaps another 64 linux distro. If they dont work its your system.

---

### Post by jazzman65 on 2008-04-26
> **NightwishFan said:**
> Also try an earlier 64bit or perhaps another 64 linux distro. If they dont work its your system.

I did happen to have a 7.10 64 bit disk and I tried that with the exact same results.  So I think you're right, it's probably something with my system.  Just can't figure out what that something is.

---

### Post by donovan1983 on 2008-04-27
For some reason I ran into problems booting the Ubuntu 8.04 64-bit desktop CD, but have no issues with either the Kubuntu or Xubuntu 8.04 64-bit desktop CD. If I remember correctly, I got an error about a USB device or hub or something and my screen just got filled with a repeating error message. The 64-bit versions of FreeBSD 7 and PC-BSD 1.5.1 both have kernel panics when they try to initialize what seems to be the root USB hub.

My system specs:
AMD Athlon64 X2 4200+
NVIDIA GeForce 6150/nForce 430 chipset
2x512MB Samsung PC5300 DDR2 DIMMs (1GB total)
320GB Seagate 7200RPM SATA hard drive
EVGA GeForce 7600GT 256MB PCI Express video card
HP LightScribe PATA DVD writer
LiteOn 16x PATA DVD-ROM

---

### Post by jazzman65 on 2008-05-01
Just an update that I finally figured out the problem and am even now posting this from 64 bit Hardy Heron goodness from the Live CD!  After stumbling around the forums for days, I finally came upon a thread from 2 years ago where someone posted that they added "mem=4096M' to the end of the grub boot.  I had started to suspect that perhaps the 4GB of memory may have been causing the problems I was having (or some other hardware issue), so I added the boot option above and voila, it booted right up!  Pretty exciting!

Now that I'm up though, the system monitor and free command only shows 3.1 GB, the same as 32 bit does.  Also, does the system monitor not show that the current Hardy being used is 64 bit?

Now that I've finally gotten the Live CD to work, I'll have to check everything out and see if it's worthwhile to change over or not.  If I did install it, would I have to change something in grub, such as the mem=4096M, permanently for this to always work?

Thanks to everyone who offered help!

---

### Post by jazzman65 on 2008-05-02
Is it not possible to mark threads as "SOLVED" any more?

---

### Post by jazzman65 on 2008-05-26
Just wanted to make sure I properly labeled this as "SOLVED".

:)

---

