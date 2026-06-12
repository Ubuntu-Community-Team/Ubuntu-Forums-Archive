---
title: "64 bit Ubuntu questions"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by dtrot55 on 2008-04-24
Does the 64bit Ubuntu have the same issues as some 64 bit windows users have...lack of 64bit software and driver support?  I am currently using the 32bit 7.10 and going to upgrade to 8.04 and was wondering if it would be better to go 64 or 32??

I just don't want to do it if im going to hit a lot of driver issues.

---

### Post by Anthony M on 2008-04-24
Hardy is my first experience with a 64bit OS and I had ZERO trouble with drivers and software. For my situation, it was no different than installing Ubuntu 32bit.

Run the livecd and see if your system behaves appropriately...

YMMMV

---

### Post by old_geekster on 2008-04-24
I began running 64-bit with Gutsy (See my sig).  I upgraded to Hardy with no problems.  I had to us 32-bit flash to get "Frostwire" to run.

---

### Post by dtrot55 on 2008-04-24
unfortunately for me i dont know what 32bit flash is ... <-- still noob :(

---

### Post by rs3 on 2008-04-24
You will hopefully find that most everything with Ubuntu amd64 works.  It's hard to say for certain if every piece of hardware you have will be supported, but I would definitely recommend grabbing a 64-bit live/desktop CD and trying it out.

I've managed to run 64-bit on my desktop system since 5.10 (Breezy) without hardware support problems, but laptops can be finicky for drivers.

As far as Flash goes, it's a product Adobe uses to provide animated graphics and movies in your browser.  You should find that Ubuntu amd64 (as of 8.04) supports Flash just fine for most cases, but if one of your favorite pages does not display right (or at all), it may require running a 32-bit browser with a 32-bit Flash plug-in.

Some sites that use Flash include [YouTube]("http://www.youtube.com") and, of course, [Homestar Runner]("http://www.homestarrunner.com") (to give you examples)

---

### Post by old_geekster on 2008-04-24
> **dtrot55 said:**
> unfortunately for me i dont know what 32bit flash is ... <-- still noob :(

Hang in there.  We were all newbies in the beginning.;)

You would use "Synaptic Package Manager" to install this package --ia32-sun-java6-bin.  I also installed "ia32-libs".  These two packages did what I wanted.

---

### Post by dtrot55 on 2008-04-24
still over my head...but i dont think i will be using frost wire...if anything bit torrent or limewire on windows

---

### Post by ASULutzy on 2008-04-25
The only issue I've had with 64 bit Hardy is getting a virtually noname wireless USB adapter to work with Ndiswrapper.

If you aren't using very obscure wireless USB adapters, 64 bit should be fine.

---

### Post by jespdj on 2008-04-25
> **dtrot55 said:**
> Does the 64bit Ubuntu have the same issues as some 64 bit windows users have...lack of 64bit software and driver support?  I am currently using the 32bit 7.10 and going to upgrade to 8.04 and was wondering if it would be better to go 64 or 32??

I just don't want to do it if im going to hit a lot of driver issues.
No it does not!

For Ubuntu / Linux, most software is open source, which means that it's easy to compile 32-bit and 64-bit versions for it. So for almost everything there's a 64-bit version.

On Windows, you have this problem because manufacturers don't think it's worth their time and effort to compile 64-bit drivers. On Linux you're not dependent on hardware manufacturers for most drivers.

---

### Post by lewisskinner on 2008-04-25
I used Gutsy 64-bit and the only problem I had was with my soundblaster X-Fi Xtreme - purely because Creative haven't pulled their finger out and got a decent driver yet!

But then this would also have been a problem on 32-bit, as they've not even *tried* to write a 32-bit Linux driver yet:roll:

---

### Post by omegamike on 2008-04-25
**Sorry about the double post!

Dude, OSS released beta drivers for the X-Fi Series. I got my X-Fi Gamer sound card to work. Check it out: [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

---

### Post by omegamike on 2008-04-25
Dude, OSS released beta drivers for the X-Fi Series. I got my X-Fi Gamer sound card to work with the 32-bit. I haven't tried the 64-bit. Check it out: [http://www.4front-tech.com/download.cgi]("http://www.4front-tech.com/download.cgi")

---

### Post by franklee on 2008-04-25
I fresh installed Hardy with a single / partition and a 100meg boot partition, no probs there at all, cept with the automated recommended layout, my soundcard works and manual partitioning causes some file error that defaults to no sound. I reinstalled with recommended partition layout after checking error messages and finding correct driver etc, only to find that unlike gutsy, Hardy seems to cak itself over sound. With my speakers up max, I can barely hear output. Ive checked default settings, played with the script and nothing seems to alter my volume settings. Gutsy was actually better for my system in general but Hardy Look so nice....I dont wanna backgrade....any ideas anyone? 

AMD 3200+ 64bit
1024 Meg DDRam
GeForce 7600 (128meg)
280gig HDD

---

### Post by Brian96 on 2008-04-25
> **franklee said:**
> I fresh installed Hardy with a single / partition and a 100meg boot partition, no probs there at all, cept with the automated recommended layout, my soundcard works and manual partitioning causes some file error that defaults to no sound. I reinstalled with recommended partition layout after checking error messages and finding correct driver etc, only to find that unlike gutsy, Hardy seems to cak itself over sound. With my speakers up max, I can barely hear output. Ive checked default settings, played with the script and nothing seems to alter my volume settings. Gutsy was actually better for my system in general but Hardy Look so nice....I dont wanna backgrade....any ideas anyone? 

AMD 3200+ 64bit
1024 Meg DDRam
GeForce 7600 (128meg)
280gig HDD

This may be too elementary, but I had a similar problem in 32-bit Gutsy (in a custom install off of a CLI base). The problem in my case was that "PCM" (which can be adjusted in Alsa-mixer) was defaulted to 3/4 volume. I maxed it out and had "normal" sound.

---

