---
title: "What is 64bit?"
date: 2007-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by RealG187 on 2007-03-21
What exactly is 64 bit PC? I know it is a PC [There aren't 64bit macs are there?]  with a 64bit CPU installed but what is that?

I hear that 64 But CPUs are faster.

I also hear they cause incompatibilities, Like my XP SP2 CD won't update XP 64 bit. I hear that 64 bit is faster and running 64 bit XP is even faster but you still can run normal XP, is the same true for Linux?

Could I run x86 version on a 64bit machine?

I am so new to 64 bit and confused about what it even is...

---

### Post by mjhb on 2007-03-21
[http://en.wikipedia.org/wiki/64_bit](http://en.wikipedia.org/wiki/64_bit)

Happy reading...

---

### Post by dfreer on 2007-03-21
You should read the wikipedia entry as it's pretty good. But here are some direct answers:
> I hear that 64 But CPUs are faster.
In some ways. This is a bit of a touchy subject and I'm in no way an expert, so I would read up on it (This forum has some great posts already about it). But in general you will only see a speed increase when dealing with video editing/transcoding, and you will be able to use more than 4 GB's of RAM when using a 64-bit processor.

> I also hear they cause incompatibilities, Like my XP SP2 CD won't update XP 64 bit. I hear that 64 bit is faster and running 64 bit XP is even faster but you still can run normal XP, is the same true for Linux?
 
Hmmm, not quite sure what you mean here. A 64-bit processor can run a 64-bit OS, or it can run a 32-bit OS (with no speed increase, AFAIK exactly like running a regular 32-bit processor. So a 3.0 Ghz 64-bit processor in a 32-bit machine will still be 3.0 Ghz NOT 6.0 Ghz or whatever). You cannot upgrade any OS from 32-bit to 64-bit, linux or windows. You will need to perform a clean install using a specific 64-bit OS install cd. So no, your XP SP2 CD will not upgrade to XP 64-bit, you will need to use the XP 64-Bit Install CD. 

But why not use Ubuntu instead? ;)

> Could I run x86 version on a 64bit machine?

Sure! 64-bit processors are backwards compatible with 32-bit. Not only that, they can run 32-bit code in a 64-bit enviroment (blows your mind right?). So basically, on my 64-bit machine I am running the 32-bit version of Firefox, Wine, ZSNES, etc and so forth. Not to say that it is super easy, but with the help of people on this forum and a few install scripts it shouldn't be any harder than the x86 version.

[QUOTEI am so new to 64 bit and confused about what it even is...[/QUOTE]

That's where the wikipedia entry will help :D

---

### Post by Kilz on 2007-03-21
> **RealG187 said:**
> 
Could I run x86 version on a 64bit machine?


While it is possible, there are reported cases where the 64bit hardware has issues running the 32bit operating system. In my case the 32bit os refuses to see the cdrom drive.

---

### Post by stmiller on 2007-03-21
[QUOTE]> **RealG187 said:**
> What exactly is 64 bit PC? I know it is a PC (There aren't 64bit macs are there?) 

The G5 chip in Powermacs/iMacs is 64bit. To run Linux on it, you must use a 64bit flavor of PPC Linux (this is a specific requirement to the IBM PPC chip, and not x86/x64 chips). In the intel/amd PC world you can run a 32bit distro on a 64bit chip.

And also the current core 2 duo chip in the intel Macs is a 64bit chip. So macs are actually already there.

Firstly, software must be written to take advantage of 64bit goodness. Some video and other encoding programs are currently able to take advantage of this, and do encoding or processing very quickly. (Like Blender, for instance.) Other software is getting there. It's partly a business/money reason (companies aren't going to spend a fortune rewriting their apps for 64bit when 32bit Windows is still the main OS out there, and the platform where they are making money). 

But 64bit is the direction we are headed. Computers have been 8bit -> 16bit (windows 3.1) -> 32bit (current state) -> 64bit (is coming/here already!) 

And Linux has solid 64bit support (software and drivers), way ahead of windows or os x...

---

### Post by dptxp on 2007-03-22
64 bit is 2 to the power 64, and so on. A typical ANSI character uses 8 bits ( a number between 0 and 255, 255 is 2 to the power 8 minus 1). So if are moving a text line (any data actually) with 128 bytes (1 byte = 8 bit) or characters with a 8 bit system one by one, you need 16 steps. With a 16 bit machine you transfer 2 bytes each time, so 8 steps. With 64 bit machine, you need just 2 steps (or say cycles).

So for some operations in any program, speed doubles as we move from 32 bit to 64 bit. Some operations get even faster (much more than 2) like multiplication.

You can benefit in 64 bit if your program too is designed for 64 bit. But do not expect double speed, like if you need to shift only one byte at a time, a 8-bit m/c shall be as fast as 64 bit. So in reality users have observed speed improvement by maybe 30%.

To understand better, you have to know the binary number system where you have only two numerals, 0 and 1, not 0 to 9 as in Decimal system.

---

### Post by RealG187 on 2007-03-22
> **stmiller said:**
> [QUOTE]

The G5 chip in Powermacs/iMacs is 64bit. To run Linux on it, you must use a 64bit flavor of PPC Linux (this is a specific requirement to the IBM PPC chip, and not x86/x64 chips). In the intel/amd PC world you can run a 32bit

I have the one CD here and it says "This mac edition will run on modern G3, G4, and G5 computers, including iBooks and Powerbook"

Are are G3-5 64bit? So then this means that I have a 64 Bit Mac version?

My mac is a 5125 CD [Performa](http://en.wikipedia.org/wiki/Performa), is has a PPC chip but its like a G0! [that's right a G-Zero!] It's only 90Mhz, how many bits is that?

I am pretty sure my Pentium III is a 32bit, what's the difference between Clock [MHz] and bit?

---

### Post by stmiller on 2007-03-22
> **RealG187 said:**
> [QUOTE=stmiller;2334454]

I have the one CD here and it says "This mac edition will run on modern G3, G4, and G5 computers, including iBooks and Powerbook"

Are are G3-5 64bit? So then this means that I have a 64 Bit Mac version?

My mac is a 5125 CD [Performa](http://en.wikipedia.org/wiki/Performa), is has a PPC chip but its like a G0! [that's right a G-Zero!] It's only 90Mhz, how many bits is that?

I am pretty sure my Pentium III is a 32bit, what's the difference between Clock [MHz] and bit?

The ubuntu PPC install CD has kernel images for ppc32 and ppc64. When installing, you pick the version to boot from at the command line. That's why it says  'For G3, G4, G5, etc.' on that disc. Same for the OS X install disc as of 10.3. Retail OS X discs actually contain a 32bit and 64bit version.

The G3, G4 cpus are 32bit, btw.

I would suggest searching wikipedia for more info on PPC chips, and G4, G5.

And as for your Performa: that is an old-world mac. It it somewhat difficult to set up, but a version of Linux could run on this machine most likely. Search for 'old-world mac and Linux.' Gentoo has some good info for Macs and Linux.

---

### Post by DKwhite on 2007-03-22
> **RealG187 said:**
> [There aren't 64bit macs are there?]


There are.  In fact of all 3 platforms Apple's O.S. is the best when dealing with 64 bit hardware. (unlike Linux and Windows). 

I'll probably get hated on for saying this, but my group of friends and I have been discussing Linux distro's quite a bit and it seems to us that the Linux community has become too much of a follower in the O.S. world and not enough of a leader like they used to be.

I still fail to understand why the Linux community hasn't finalized their 32 bit versions of their O.S's and moved on to focusing on their 64 bit versions.  It makes no sense to continue to spend such resources on 32 bit versions when the 32 bit computers that run them are a dying breed.

I Also don't understand why they can't make a reasonably attractive I.M. heh.

---

### Post by stmiller on 2007-03-22
> **DKwhite said:**
> 
I still fail to understand why the Linux community hasn't finalized their 32 bit versions of their O.S's and moved on to focusing on their 64 bit versions.  It makes no sense to continue to spend such resources on 32 bit versions when the 32 bit computers that run them are a dying breed.


There is still a bit of Linux software that is 32bit only. Browser plugins (java, flash, etc.) which require a 32bit install of Firefox. Openoffice has mainly only been available as a 32bit version, but I think a 64bit version is out now.

And other software here and there is still only 32bit. So it IS getting there. But until the desktop user stuff (browser plugins) are 64bit, using a 32bit Firefox will remain.

---

### Post by dptxp on 2007-03-23
The reason for 64 bit having taken so long has perhaps to do with Intel and Microsoft. Not many have/had AMD64 chips, many stick to Intel name, and since XP was 32 bit , 32 bit stayed and stayed.

The 64 bit problem is there in Vista too. And not all XP applications are going to run even in 32 bit Vista.

You can also see in the forum that users are discouraged to go for 64 bit. Fortunately Ubuntu (and many others) are bringing out 64 bit with 32 bit and it is just a matter of time when we have our favorite applications in 64 bit.

For basic home use and office use, 64 bit is already mature.

---

### Post by cmost on 2007-03-23
> **Kilz said:**
> While it is possible, there are reported cases where the 64bit hardware has issues running the 32bit operating system. In my case the 32bit os refuses to see the cdrom drive.

...and in my case, the 32 bit OS cannot use AGP.  In addition, even with AGP disabled, I cannot use AIGLX (or nVidia's implementation thereof.)  That being said, I've had no notable problems whatsoever with the 64 bit implementation.

---

### Post by Kilz on 2007-03-23
> **cmost said:**
> ...and in my case, the 32 bit OS cannot use AGP.  In addition, even with AGP disabled, I cannot use AIGLX (or nVidia's implementation thereof.)  That being said, I've had no notable problems whatsoever with the 64 bit implementation.

These are things some people never hear about, but need to.

---

### Post by RealG187 on 2007-03-23
My PC has AGP, but I dont have a card.

Would Core Duo be 64 bit?

---

### Post by maxamillion on 2007-03-23
> **mjhb said:**
> [http://en.wikipedia.org/wiki/64_bit](http://en.wikipedia.org/wiki/64_bit)

Happy reading...

[http://en.wikipedia.org/wiki/X86_64](http://en.wikipedia.org/wiki/X86_64) <---compliment article to that ^ one

---

### Post by kuja on 2007-03-23
> **RealG187 said:**
> My PC has AGP, but I dont have a card.

Would Core Duo be 64 bit?
Core Duo = 32-bit
Core 2 Duo = 64-bit

---

### Post by RealG187 on 2007-04-13
I dont have any 64 bit, I am gonna get a laptop but it's probably "Core Duo = 32-bit", if I did it probably would come w/ Vista, is that made fir 32,64 or both, and if I want Linux should I get a 36 or 64 bit distro?

---

### Post by John Jason Jordan on 2007-04-13
> **RealG187 said:**
> I dont have any 64 bit, I am gonna get a laptop but it's probably "Core Duo = 32-bit", if I did it probably would come w/ Vista, is that made fir 32,64 or both, and if I want Linux should I get a 36 or 64 bit distro?
If you get a 32-bit computer all you can put on it is a 32-bit distro. If you get a 64-bit computer you can put either a 32-bit distro or a 64-bit distro on it. Except for closeouts, almost all new computers today come with 64-bit CPUs.

---

### Post by marsmissionaries on 2007-04-13
> **John Jason Jordan said:**
> If you get a 32-bit computer all you can put on it is a 32-bit distro. If you get a 64-bit computer you can put either a 32-bit distro or a 64-bit distro on it. Except for closeouts, almost all new computers today come with 64-bit CPUs.
Actually almost all budget PCs are still shipping with 32bit processors, the majority of the computer market is still running 32bit.

---

### Post by ronocdh on 2007-04-13
> **marsmissionaries said:**
> Actually almost all budget PCs are still shipping with 32bit processors, the majority of the computer market is still running 32bit.

This could balloon into quite a debate, but I'm going to side with John Jason Jordan here and say that if you're buying a new computer, it's probably going to be 64-bit. If you're getting a 32-bit, you're buying a bargain PC, and so you should expect outdated hardware.

Yes, XP was 32-bit, for way too long, and indeed that may have helped the market stagnate. But the world does move on, people, despite Microsoft's lethargy. ;)

---

### Post by marsmissionaries on 2007-04-13
you are correct, new computers will probably be 64bit, but there are still a majority of 32bit computers that nobody buys because they have lower specs.

What I have noticed however is just recently, with the release of vista, single core processors have become harder to find in PCs and laptops, most name brand PCs are shipping with dual cores now, so the shift from 32bit to 64bit is definately happening as AMD dual core CPUs are 64bit, and intel has their core 2 duo which is 64bit, however with 32bit versions of vista being included by defualt, the mainstream shift could be years off...as vista is way too expensive to buy a seperate copy so you can have true 64bit. (reason number one for my shift to ubuntu...that and vista is ugly)

As for the topic of this thread: "What is 64 bit". If you have to ask, you probably wont notice the difference...except for your flash player not working by default, 64bit processors are generally the same speed as their 32bit counterparts, meaning my 64bit turion ml-30 1.6ghz CPU is the same speed as an equivalent 32bit 1.6ghz CPU. 

With switching to 64bit, however i have noticed a tiny bit of speed, HOWEVER this is most likely because the switch was from WINDOWS to LINUX, 32 bit to 64bit. My experience in the past with Mandrake (9 i think), Fedora core 2, and Slackware 10 and 11, and now ubuntu is that linux is just....faster. So I am unaware whether or not the boost in speed is a result of the switch from 32 to 64bit.

Right now, I would not advice the switch to 64bit for an average computer user, it just isn't needed yet and you will be disappointed in some of the programs you will loose.

---

### Post by RealG187 on 2007-04-13
Then what's the point of it? If it's the same speed as 32 bit...

---

### Post by rsambuca on 2007-04-13
> **RealG187 said:**
> Then what's the point of it? If it's the same speed as 32 bit...

It depends greatly on what tasks and applications you are using.  If you are just surfing the net, writing emails, listening to music, etc, you probably won't notice a difference.  If you are doing heavy cpu intensive tasks with the right applications you can experience upwards of a 30% performance gain.  Things such as video encoding, 3D-Rendering, etc.

I personally don't think you lose anything by going 64-bit, unless you are going to use some obscure programs.

---

### Post by dabl on 2007-04-13
Old farts like me remember the identical debate 12 or 15 years ago when we migrated from 16-bit to 32-bit OS, and 10 years before that when we went from 8-bit to 16-bit.  First comes the hardware, then comes the OS, and last come the apps.  It takes awhile for the availability of productivity-improving apps to drive the older hardware architecture out of the market.  But it will happen -- today's 32-bit hardware will go where the 80286s are, and the software will gradually follow.

---

### Post by rsambuca on 2007-04-13
> **dabl said:**
> Old farts like me remember the identical debate 12 or 15 years ago when we migrated from 16-bit to 32-bit OS, and 10 years before that when we went from 8-bit to 16-bit.  First comes the hardware, then comes the OS, and last come the apps.  It takes awhile for the availability of productivity-improving apps to drive the older hardware architecture out of the market.  But it will happen -- today's 32-bit hardware will go where the 80286s are, and the software will gradually follow.

I agree completely.  Software developers are always playing catch-up.  Some of us are just more impatient than others.:)

---

### Post by RealG187 on 2007-04-13
If I rip CDs and convert WMA --> MP3, play games will 64 bit be better?

---

### Post by marsmissionaries on 2007-04-14
should be.

---

### Post by RealG187 on 2007-04-14
> **marsmissionaries said:**
> should be.

Will it be noticeable?

---

### Post by kuja on 2007-04-14
> **RealG187 said:**
> Will it be noticeable?
yes.

---

### Post by stmiller on 2007-04-15
> **RealG187 said:**
> If I rip CDs and convert WMA --> MP3, play games will 64 bit be better?

Convert from a lossy format to another lossy?? Please tell me you don't...

---

### Post by RealG187 on 2007-04-16
> **stmiller said:**
> Convert from a lossy format to another lossy?? Please tell me you don't...

Why? It takes less space, and everything is MP3 compatible!

---

### Post by RealG187 on 2007-04-16
> **kuja [Answer to the question if 64 bit is noticeable] said:**
> yes.

> **marsmissionaries said:**
> 64bit processors are generally the same speed as their 32bit counterparts, meaning my 64bit turion ml-30 1.6ghz CPU is the same speed as an equivalent 32bit 1.6ghz CPU. 


These two statements contrdict each other, which is correct?

---

### Post by kuja on 2007-04-16
The clock speed is indeed the same; however, a 64-bit CPU has 64 registers instead of 32, allowing for certain operations to be performed significantly faster at the same clock speed. The boost varies anywhere from no real boost in performance, all the way  up to about a 100% boost. I'd say with MP3 encoding 20-30% would be what you'd likely see.

---

### Post by kuja on 2007-04-16
> **RealG187 said:**
> Why? It takes less space, and everything is MP3 compatible!
What he means is converting from one lossy format to another lossy format IS a bad idea. 

In essence, when you encode something in a lossy format, part of what the encoder does is look for artifacts to remove. For the most part the ones they pick you won't be able to hear easily (but as you lower the bitrate the encoder gets more aggressive and you can start to hear the difference). When converting from one lossy format to another, that becomes more pronounced. 

Lets give an (over)simplified example:

Lets say MP3 will remove artifacts A, B, C, and D from the sound. You can't tell the difference right?
Lets say OGG would remove artifacts C, D, E, and F from the sound. You can't tell the difference there either.

But lets say we encode to OGG, then re-encode with MP3. artifacts A, B, C, D,  E, and F would all be removed from the sound. More has been removed in effort to make the file smaller, and as such the chance that you'll be able to hear the difference is greater. If you personally can't tell the difference then there is no real reason to worry about it, but that's just something to consider. I wouldn't want to keep them in *.WMA format either :P 

As per things, OGG actually produces smaller files than MP3 does. The OGG files generally sound better than MP3 would at a lower bitrate. The OGG format can't encode at a lower bitrate than about 50, however, so if you need the smallest possible file (even at the expense of sound quality) you'd be better off with MP3 (Or perhaps WMA, surprisingly enough)

---

### Post by dptxp on 2007-04-16
[SIZE="2"]> **RealG187 said:**
> If I rip CDs and convert WMA --> MP3, play games will 64 bit be better?

When you rip CDs you normally rip it to WAV format. It is not compressed, file sizes are about 40 or 50 MB per track. CD Quality is 41000 Hz, it will carry audio frequencies up to 22050 Hz (Half).

You compress (convert to MP3, WMA or OGG) from WAV. WAV is not lossy, not compressed. From the original WAV, you make other files, not one from other.

FLAC is a lossless format but file size becomes half of WAV, 20 MB in place of 40.

You can have good quality MP3 at 192 kbps, fairly good at 128, fair at 96, acceptable at 64.

If you go below that, well, no comments.[/SIZE]

---

### Post by RealG187 on 2007-04-17
Instad of ripping WMA and converting to MP3, sould it be better to just rip directly to mp3>

Also about Hertz, Mhz:

What does Hertz have to do with computers and stuff, like my MP3s are 22, 41, or 48 MHz, or my SPU is 677 MHz, what does cycles have to do with my computer, does it spin? I dont see anything! And how can digital files spin? Also, I hear humans only hear 20 Hz, then why put my MP3s higher? How can sound cycle?

What's the difference between Sample rate and bit rate?

---

### Post by dptxp on 2007-04-18
[SIZE="3"][SIZE="2"]Humans hear from below 20 Hz to about 16 khz (16000 Hz), depends on the human. Dogs and many animals hear much higher frequencies too. The sampling rate has to be double of the highest frequency you want to hear. 32 KHz sampling is adequate for home, 41 KHz is standard for CD quality.

Bit rate changes with compression, higher bit rate means better quality, but bigger file size as more data is needed for same audio.

When you convert WMA to MP3 direct, the 'direct' is what you see externally. Internally it rips to RAW (sort of WAV), then encodes to MP3.


[/SIZE][/SIZE]

---

### Post by RealG187 on 2007-04-18
Why does it have to double, so If I put my MP3s at 48 [high] or 22 [low] KHz, theres no point cuz I cant hear it, and doesnt Hertz mean cycles [I take Physhcis] what does that have to do with sound?

---

### Post by dansus on 2007-04-19
lower frequencies act as carriers to the higher freq, allowing you to hear them.

although you wont hear a single flat tone of say 22khz, the interactions of multible freq are important as discoverd recently, ie when playing music.

teenagers can hear upto around 22k, young adults upto 18k, after it gets worse as you get older and damage done your hearing by lifestyle choices ie standing next to a large speaker in a club for 4 hours and not realising its loud cos your of your tits (my bad) ;).

---

### Post by RealG187 on 2007-04-20
So yuo can tell the differences in freq?

---

