---
title: "Problem installing Ubuntu."
date: 2007-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by M79 on 2007-04-17
Hello. I've been interested in installing a form of Linux on my PC for a while, but never really got the courage to do so. Mainly because everyone I spoke to told me to stay away from Linux, because it's complicated, for advanced PC users, and I simply wouldn't know what to do. Basically, Linux isn't for you, because you're a twit. Stay with Windows, it's for simpler folk. I'll admit, I'm not the most tech savvy person, but I have used computers that run Linux as their operating systems at school, and I was impressed. 

Anyway, the main problem I'm having is that any version of Linux I attempt to install, fails. Ubuntu, Knoppix, openSUSE, etc. I know this isn't the Other versions of Linux forum, but I thought I'd add that to show how troublesome this has become. I first used an Ubuntu Live CD, which was nice. But I wanted to install the actual operating system. I then got my hands on a DVD version of Ubuntu. I thought to myself, "Ooohhhhh, this one must come jam packed with nice programs...." I downloaded and burned it to a blank DVD-R. Inserted it into my DVD drive, rebooted, and booted into the Ubuntu screen, which gave me a few options for installation. I chose the first one, it loaded the kernel files. Well, it tried to. This is the error I keep getting with Ubuntu.

[IMG]http://img.photobucket.com/albums/v225/Mikeym1979/DSCN0991.jpg[/IMG]

Now, this exact error, I don't get with the other Linux operating systems, but I do get error messages during the exact same process. Honestly, though, I wanted to install Ubuntu because someone told me it's the best, user-friendly Linux version I can get. So, I was wondering if anyone here could help me out in trying to solve why it won't install. :confused: 

In case it's needed, here are the specs of my PC.
512MB of ram
Intel P4, 2.9Ghz CPU
Windows XP Home Edition SP2
80 Gig HD x2
nVidia GeForce 5200FX 256MB

Thank you.

Edit: I apologise if I posted this in the incorrect section.

---

### Post by mac.ryan on 2007-04-17
I suppose the missing bit of the error message says "isolinux", does it?

If this is the case, it should be "just" a problem with your burned copy of ubuntu (i.e. some problem with the physical DVD).

What you can try is to burn a CD (instead of a DVD) at the slowest speed possible on your drive. This should limit to the maximum the possibility you get errors. Ubuntu CD and DVD are the same... All  missing things from CD, you can install via internet from "System -> Admin -> Synaptics", very very easy and trouble free procedure.

Should you discover your DVD/CD drive has unsurmountable problems, you can try an alternate install procedure (without  DVD or CD from [here]("https://help.ubuntu.com/community/Installation")). 

Final thought about whom GNU/Linux is for. GNU/Linux is free (like in freedom) software: it is not for advanced computer users, it is for advanced (i.e. aware) citizens. Classic reading about [Win vs. GNU/Linux]("http://linux.oneandoneis2.org/LNW.htm") for your friends...

---

### Post by tormodfoss on 2007-04-17
Hey, I had the exactly same problem when I was installing Ubuntu last week. There's probably an error with the dvd, you should try to burn ubuntu to another preferably new cd of high quality.

---

### Post by OPRIME on 2007-04-17
I had the same problem with my install CD.  Naturally I burnt another, but continued to have the same problem.  I switched to my other CD drive (From Sony to Pioneer), and the CD worked.

---

### Post by chakkaradeep on 2007-04-17
I have got the same when I wrote the ISO image to CD in high speed. After this incident,I write the ISO images only at 12x speed :o

---

### Post by ronocdh on 2007-04-17
> **chakkaradeep said:**
> I have got the same when I wrote the ISO image to CD in high speed. After this incident,I write the ISO images only at 12x speed :o

I always verify the integrity of the burn post-operation. I use an open source OS X app called "Burn" which does this automatically. Additionally, always remember to use the checksum on the Live CD! The option is available on the boot screen for the Live CD, listed as "Check CD for errors." I always do both on a new CD, and even rerun the Live CD checker if I haven't installed from the CD in several weeks. This is because CD-Rs tend to decay, though the rate varies with the quality of the media.

---

### Post by dabl on 2007-04-17
It's not a terribly unusual experience to have some troubles getting a good ISO burn, especially with a well-used CD/DVD drive -- check out this guy's misery, until he got a new drive:

[http://kubuntuforums.net/forums/index.php?topic=3081733.0](http://kubuntuforums.net/forums/index.php?topic=3081733.0)

Personally, I got a happy result with Feisty 64-bit with just the downloaded CD ROM ISO image.  Of course, the repositories got a workout shortly thereafter, but that's no problem with a broadband connection.  :popcorn:

---

### Post by M79 on 2007-04-17
Thanks for the help. 

Well, I reburned the ISO to a new, blank DVD at the slowest speed, which was about 4x. This time using something called Burn4Free. The last time I think I used Alcohol 120% or Nero. Anyway, I booted it up, and for some reason, my PC took forever to shut down, then forever to load up the Ubuntu loading screen. Then the screen went blank with a small white flashy, thing. Like this: _ <Like that. It was white, and flashed quite often. That stayed there for quite some time, and nothing ever loaded up.

---

### Post by mac.ryan on 2007-04-17
First question: when you downloaded the DVD image, have you done the md5 cecksum check? If your data is corrupted before you burn...

Second: have you tried installing it from a CD rather than a DVD as suggested above? A DVD has about 7 times the data density of a CD... which means burning needs to be 7 times more accurate (or that a problem has about 7 times more chances to lead to an error...). I can't guarantee this will fix your problem, but I can guarantee I saw more of a case in which it did...

Best luck! :)

---

### Post by M79 on 2007-04-17
> **mac.ryan said:**
> First question: when you downloaded the DVD image, have you done the md5 cecksum check? If your data is corrupted before you burn...

Second: have you tried installing it from a CD rather than a DVD as suggested above? A DVD has about 7 times the data density of a CD... which means burning needs to be 7 times more accurate (or that a problem has about 7 times more chances to lead to an error...). I can't guarantee this will fix your problem, but I can guarantee I saw more of a case in which it did...

Best luck! :)md5 checksum? Not sure how to do that. I did do the memtest, which passed. I'm going to try and burn a CD image of it at the slowest speed, just like I did with the DVD version, and see how that goes.

---

### Post by mac.ryan on 2007-04-17
> **M79 said:**
> md5 checksum? Not sure how to do that. I did do the memtest, which passed.

About the md5sum, you can find an how-to [here]("http://www.psychocats.net/ubuntu/iso"). The md5check verify the data as copied on your computer are identical to the one on the server (so it check for transmission errors). The memory test you did performs - AFAIK - just a check on your RAM memory...

Best luck with the CD version of ubuntu (I will keep finger crossed for you). As last resource, you can also try some of the [non-CD ways of installing ubuntu]("https://help.ubuntu.com/community/Installation")... they are a bit trickier, but you eliminate your problem at the root.

---

### Post by M79 on 2007-04-17
Well, after downloading and burning the Ubuntu CD image onto a blank CD, I got further than what I did when I tried using the DVD. However, this is what I encountered:

[IMG]http://img.photobucket.com/albums/v225/Mikeym1979/DSCN0995-1.jpg[/IMG]

And this followed:

[IMG]http://img.photobucket.com/albums/v225/Mikeym1979/DSCN0998.jpg[/IMG]

Seriously, is there any hope for me, or should I just stay with XP?

Edit: I'm terribly sorry about the image size. I uninstalled Photoshop, so using that to resize isn't an option. And, I don't know if MSPaint will do that.

---

### Post by mac.ryan on 2007-04-18
> **M79 said:**
> Seriously, is there any hope for me, or should I just stay with XP?

Well, in my mother tongue we have a saying that goes more or less like this: "Hope is the last to die"... ;) And anyhow there is will to support you, at least as far as possible via a forum.

My suggestion would be to try install ubuntu in "graphical safe mode": there is a known bug in 6.10 so you should follow [this how-to]("https://wiki.ubuntu.com/EdgyKnownIssues/59618") (rather than simply selecting "safe graphical mode" from the menu). Alternatively you can simply wait for tomorrow release of version 7.04 and see if it will boot normally. (If not you could try "safe graphical mode" with version 7.04).

Keep up updated with the progresses... every effort you do now will be rewarded by the satisfaction of having overcame an obstacle more! :)

---

### Post by M79 on 2007-04-20
Strange. I was able to successfully install Ubuntu Feisty on my brother's PC, which is a bit older than mine, and has an AMD CPU. Is that why no Linux will install on my PC? Because it has an Intel Pentium 4?

---

### Post by mac.ryan on 2007-04-20
I really don't think so. As you saw on the error message above, you are now being stopped by a problem with your graphical card. Have you tried to install in safe graphical mode yet?

---

### Post by M79 on 2007-04-21
It worked! :D The safe graphical mode. It actually worked. I think I know what the problem was, which is odd. See, I had two video cards connected to two monitors. The onboard card, and the nVidia card. Both were connected to two seperate monitors, which worked on XP. I think that was giving me the errors, because before, even after using safe graphical mode, it would give me the same errors. Yet, when I disconnected the monitor from the onboard card, and disabled it, it finally (Ubuntu Feisty Fawn) worked. 

[IMG]http://img.photobucket.com/albums/v225/Mikeym1979/Screenshot.png[/IMG]

Now, off to actually install it! :D Thank you all very much for the help.

---

### Post by mac.ryan on 2007-04-21
Glad you actually made it!
Welcome to ubuntu!

:) :) :)

---

