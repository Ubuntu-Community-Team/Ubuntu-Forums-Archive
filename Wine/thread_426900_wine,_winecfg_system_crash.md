---
title: "wine, winecfg system crash"
date: 2007-04-28
forum: Wine
---

### Post by jshipley on 2007-04-28
Whenever I try to run wine or winecfg the system hangs completely.  The mouse doesn't respond, ctrl-alt-backspace doesn't work--the only thing I can do is push the reset button on my computer.

I'm running on a system that is several years old.  The graphics card is a GeForce 2 MX, and I am running the nvidia-glx video driver.

I've spent a couple of hours googling and searching these forums and winehq's forums, but I can't figure out what's wrong.  Does anybody have any ideas?

---

### Post by jpeddicord on 2007-04-30
Try deleting the .wine folder in your home directory:```
rm -r ~/.wine
```winecfg also does some things with the graphics engine, so that might be part of the problem.

Jacob
UAResolved

---

### Post by insyte2 on 2007-05-06
Also having the same problem, im using the via driver in my xorg.conf.

---

### Post by ubunubu on 2007-05-16
same thing is happening to me too...

AMD 64 x2 3800+
GeForce 7600GT  w/1.0-9755 driver

i tried both 0.9.37 and 0.9.36 versions of wine

I've tried on both x32 and x64 feisty with the same results..maybe its a sign i shouldn't game  hehe

just kickin in my .02

---

### Post by misfitpierce on 2007-05-16
No idea why this is happening i'll look into it more. If you do however want better support games you love perhaps try cedega? [http://transgaming.com](http://transgaming.com) - Can try the 3 month hookup 5 dollars a month $15 bucks total and it runs and configures games much better than through Wine. I use it and am very happy with results.

---

### Post by ubunubu on 2007-05-16
thx for the suggestion misfitpierce :) but for me personally cedega is not an option.  honestly i am just more baffled than anything else as to why the entire system locks up.

---

### Post by Sliver85 on 2007-05-16
Same problem here.  Complete system crash.

AMD Athlon 64X2 4400+
NVidia BFGTech 6800 Ultra

---

### Post by hikaricore on 2007-05-16
If wine crashes your system cedega will no doubt do the exact same thing. lol

---

### Post by Sliver85 on 2007-05-18
Can anyone help us out here?

---

### Post by nikolajsheller on 2007-06-04
I'm seeing this problem as well on Ubuntu 7.04 Feisty. 

3800+ AM2 64 bit AMD X2
Via K8M890 Graphics card with OpenChrome 2D driver

From the message file:

Jun  4 23:17:16 MiniMe gconfd (nikolaj-11025): Resolved address "xml:readwrite:/home/nikolaj/.gconf" to a writable configuration source at position 0
Jun  4 23:24:41 MiniMe gconfd (nikolaj-11025): Received signal 15, shutting down cleanly
Jun  4 23:24:41 MiniMe gconfd (nikolaj-11025): Exiting
Jun  4 23:24:42 MiniMe kernel: [ 2014.333797] mtrr: base(0xc0000000) is not aligned on a size(0x1080000) boundary

23:24 is when I attempted to run winecfg.

Is this a 64 bit issue?

---

### Post by sikes on 2007-06-04
I am having much the same problem - only different configuration.

Pent 3 733Mhz
3DFx Voodoo Banshee

Wine ran just fine for the most part. However, I decided to take care of a load issue with the login screen - it would take on too large a resolution and flicker. So I deleted the high resolutions from the xorg.conf.

Things looked just fine after that. Except for wine. It started logging me out every time I attempted to run anything related to it.

No wineconsole, no wincfg, no running any windows based programs.

I attempted a removal of the .wine home files, but that did nothing.

I attempted a total removal and re-installation of wine, but that did nothing.

So... I seem to be out of luck, if I want to keep this xorg.conf the way it is. Unless someone has found a work around or magical incantation.

---

### Post by sikes on 2007-06-05
After copying over etc/X11/xorg.conf.bak for the original xorg.conf settings, wine starting working again.

So I'm stuck with the flickering startup resolution until either I get a new videocard, or find some way around this conflict. Probably involving the xorg.conf and wine config files... I don't know.

But it's a direction to assault my problem.

---

### Post by run1206 on 2007-06-05
i noticed when i'm running wine 0.9.36, my programs work, yet with 0,9.37 & 38, nothing works.  i tried running wine through the terminal and it says that wineserver crashed, please report this.  i think i'm just gonna stick with 0.9.36 unless someone can find the reason why the updated wine isn't working.:(

---

### Post by Sliver85 on 2007-07-24
Well, I tried isntalling a fresh copy of Ubuntu 7.04 (32-bit this time).  Wine and winecfg still cause a complete system lockup.  I then tried it on my 64-bit version, while in 'live cd' mode: same results.
My hardware is as follows:
ASRock 939 Dual-Sata2 Motherboard
AMD Athlon 4400+ X2 (not oc'ed)
BFGTech 6800 Ultra
Turtle Beach Riviera Sound Card
WC Cavier Sata 3.0 160 GB HDD

---

### Post by Chad.S on 2007-07-28
I was having the same issue with winecfg locking up my system. I have since narrowed the issue down to my sound card. I'm using a Dynex 5.1 PCI sound card. It appears as ICE1724 in ALSA. 

I thought it was odd because the sound card is working fine in every other application. So what I did was I took the sound card out of my computer and then when I ran winecfg it went through fine. I was then able to put the card back in and it then it let me launch winecfg. However, when I go to the audio section of winecfg it still locks my whole system up. I don't get any sound through the applications I install through wine either, which is a little annoying. 

I'm tempted to just go out and buy a different sound card.

---

### Post by ubunubu on 2007-07-29
> **Chad.S said:**
> I was having the same issue with winecfg locking up my system. I have since narrowed the issue down to my sound card. I'm using a Dynex 5.1 PCI sound card. It appears as ICE1724 in ALSA. 

I'm tempted to just go out and buy a different sound card.

This is good info for me because my onboard sound died and I replaced it with a Dynex card.  I am sensing a more linux friendly upgrade in the near future.

Thanks

---

### Post by johto on 2007-08-05
> **Chad.S said:**
> I was having the same issue with winecfg locking up my system. I have since narrowed the issue down to my sound card. I'm using a Dynex 5.1 PCI sound card. It appears as ICE1724 in ALSA. 

I thought it was odd because the sound card is working fine in every other application. So what I did was I took the sound card out of my computer and then when I ran winecfg it went through fine. I was then able to put the card back in and it then it let me launch winecfg. However, when I go to the audio section of winecfg it still locks my whole system up. I don't get any sound through the applications I install through wine either, which is a little annoying. 

I'm tempted to just go out and buy a different sound card.


Nice info, my system halts completely too ! 

i have Pentium 4 (Northwood), Asus P4P800, Nvidia GF 6600GT AGP, jadajadaja...AND **sound card Is Esi Juli@ which uses ICE chip too !** Alsa works ok on every other app. Maybe someone who know how, can tell to the wine developers about this issue with the ICE audio chip.. i believe many other "pro" cards uses that chip, including m-audio audiophile cards and so on..

---

### Post by Alp82 on 2007-09-11
I experience the same problems and have an ESI Juli@ Soundcard too. Are there any news or fix solutions for this?

---

### Post by bereanone on 2007-10-11
I just installed Gutsy on my HP Pavillion Laptop and my Compaq Presario.  Wine runs fine on my Laptop, in fact some of my programs I think run faster than they did in windows.  My Compaq on the other hand completely locks up when I try to either configure or run wine.  I know of no way to get out other then pull the plug.  Has ANYONE got a fix for this....

---

### Post by expert01 on 2007-10-18
I also have had this problem with Gutsy Gibbon since I first installed it. Unfortunately, I don't get any messages. I deleted all .wine folders in my home directory, didn't help. Typed "winecfg" in the console, said it was making the ~/.wine directory, was fine for about 5 seconds, then total system freeze. Not even the numlock key worked. Had to do REISUB (BTW, it's left alt and printscreen in ubuntu).Checked the logs, and no messages around time of crash.

---

### Post by voided3 on 2007-10-21
Same here on gutsy; winecfg hangs. What is notable though is I have the same Dynex 5.1 soundcard mentioned above w/ the ICE chip..... I'm running 0.9.46 from the repos.

---

### Post by Alp82 on 2007-10-21
Yeah, i still have the same problem in gutsy too. Esi Juli@ with ICE chip...

---

### Post by whatteaux on 2007-10-21
Wine's hanging for me on Gutsy (Kubuntu) too.

However, it's not a complete 'hard' hang. The screen goes black/blank, but I can recover by switching to a text-mode console (via ctrl-alt-F2), logging in, and killing the wine process (or the program it's failing to run). When I switch back with alt-F7, I'm back to a normal KDE desktop.

---

### Post by jroon on 2007-10-21
Wine caused my computer to freeze too, after upgrading to Gutsy.  I read on an Ubuntu forum that this was an old Wine bug, which already existed in Feisty, but didn't often come into play.  Someone on Wine live chat told me it was probably a video driver problem. 
I was using Openchrome on an Acer 1522 with a VIA K8N800 video adapter, which worked before the Ubuntu 7.10 upgrade.  I switched back to the more basic Vesa driver, and now I have Wine working in Gutsy.  (This would be a problem if the newer driver solved any of my other video problems like my lack of dual monitors.  Since iit doesn't I'll go with the Vesa driver for now.)

---

### Post by Alp82 on 2007-10-22
[I found a solution]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg388445.html") for all people who got a complete system crash. If you have a soundcard with [Ice1724]("http://alsa.opensrc.org/Ice1724") chip  (in my case an ESI Juli@) just move the file** /usr/lib/wine/wineoss.drv.so** to somewhere else. **You won't get any sound from windows applications**, but wine should work.

---

### Post by Enverex on 2007-10-22
> **Alp82 said:**
> [I found a solution]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg388445.html") for all people who got a complete system crash. If you have a soundcard with [Ice1724]("http://alsa.opensrc.org/Ice1724") chip  (in my case an ESI Juli@) just move the file** /usr/lib/wine/wineoss.drv.so** to somewhere else. **You won't get any sound from windows applications**, but wine should work.

Everyone should be using the ALSA driver in winecfg now anyway, so you -will- get sound if you select the right sound driver.

---

### Post by Alp82 on 2007-10-22
> **Enverex said:**
> Everyone should be using the ALSA driver in winecfg now anyway, so you -will- get sound if you select the right sound driver.
You are right, you just have to click on the Audio tab in winecfg and select Alsa. From now on wine should work with sound. Thank you.

---

### Post by voided3 on 2007-10-22
GENIUS!!! Thanks!

---

### Post by JusticeZero on 2007-10-24
Sorry, for some things Cedega works worse than WINE. 
I like to play Dark Age of Camelot for instance - in Ubuntu 7.10 and latest WINE, I have no cursur, but the game is playable for me; after a few hours it might hang crash on me.
In Cedega, the mouse cursor works, but it ALWAYS!!! hang-crashes within the first five minutes - completely unplayable.

---

### Post by expert01 on 2007-10-24
I have the unichrome graphics, but I don't believe I have the sound card. Tried removing the sound extension and it didn't work (total freeze). Wouldn't let me switch to VESA graphics.

Unichrome support sucks. No automatic 3D acceleration.

---

### Post by nu2this on 2007-10-28
I tried that moving wine audio that didn't work for me.

---

### Post by nu2this on 2007-10-29
bump

---

### Post by buntunub on 2007-10-29
hmm... Dark age of Camelot works flawlessly for me with Cedega only. No matter what I do it refuses to run in wine at all. This is in Gutsy.

---

### Post by atrus123 on 2007-11-17
> **Alp82 said:**
> [I found a solution]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg388445.html") for all people who got a complete system crash. If you have a soundcard with [Ice1724]("http://alsa.opensrc.org/Ice1724") chip  (in my case an ESI Juli@) just move the file** /usr/lib/wine/wineoss.drv.so** to somewhere else. **You won't get any sound from windows applications**, but wine should work.

Thanks guys.  I figured this was a problem with my ICE card, and it's been stumping me for the past few days.  Glad I found this post.

---

### Post by Alp82 on 2007-11-17
No Problem :) I also made a blog-post for all people having trouble with ICE1724 cards: [**_Get Wine to work with Alsa Ice1724_**]("http://ubuntu.alperortac.de/2007/10/22/get-wine-to-work-with-ice1724-alsa-drivers/")

---

### Post by roger_1960 on 2007-11-26
Hi

Exactly same thing with Gutsy- system locks completely as soon as I try to use wine from GUI (havn't tried terminal)  Nothing responds except the off button!

Acer Aspire 1353 AMD Athlon XP-M

Help!

---

### Post by Alp82 on 2007-11-26
What's your soundcard?

---

### Post by roger_1960 on 2007-11-26
Its a VT8233/A/8235/8237 AC97 Audio Controller I think.  This seems to have an ALSA capture device, so I will try moving the wine audio files.........

---

### Post by Alp82 on 2007-11-26
Sorry, no idea then.

---

### Post by roger_1960 on 2007-11-26
Have now installed wine several times (latest version 9.49) using GUI and terminal with no error messages.  Hangs the PC every time (screen freezes and nothing responds) .  The same after moving the audio files as suggested above by Alp82.  Anyone have any ideas. (Every thing else with 7.10 has worked fine so far..)

Laptop Acer Aspire 1353LC Athlon XP-M  VIA 8235 sound.

---

### Post by frychiko on 2007-12-07
Haha, finally I can use wine after a year since this bug cropped up! cheers!

---

### Post by Enverex on 2007-12-07
> **frychiko said:**
> Haha, finally I can use wine after a year since this bug cropped up! cheers!

Did the "move files" method work for you or something else?

---

### Post by skyout on 2007-12-16
I seem to be having the same problem.  Just cropped up when I installed Gutsy on a new system.  Biostar K8M800 Micro AM2 MoBo with AMD Sempron 3400.  Problem same for 64bit and 32bit distro.  When running winecfg the system hangs.  Only thing that works is sitting on the power button to shut it down.  Moving wineoss.drv.so made no difference.  I have no idea what it means, but running strace winecfg hangs with: clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7cf06f8) = 6039
waitpid(6039, 

Apparently waiting for some process to finish that never does?

It seems to get as far as creating a file ~/.wine-?????? where ?????? is a 6 letter alphanumeric, different for each time I run winecfg.  

Does anyone know if a wine bug report exists for this?  I can't seem to find one that matches.  The key (for me) is the complete lockup of the system, with the only option a power reset.

Any help, suggestions, questions, appreciated

---

### Post by Sliver85 on 2007-12-16
If you have a soundcard try removing it to do the winecfg.

That's what fixed it for me.

---

### Post by run1206 on 2007-12-16
i just waited til the newer version of wine came out, i still have a stock sound card on my laptop, but with 0.9.51 all my windows apps work now, with sound

---

### Post by peap on 2007-12-21
Some old problem here. Latest wine (.51) and onboard AC97 soundchip and onboard via graphics. No dice removing the audio files.

Would there be any other possible workaround?

I'm on a fresh install of x86 Gutsy, no special video driver installed.

---

### Post by skyout on 2007-12-24
I cannot physically remove my soundcard, since sound is integrated on the motherboard.  I checked device manager and it reports  a VIA8237 AC'97 Audio Controller.  The manual says it has Realtek ALC655/658 sound.  Windows XP device manager reports a Realtek AC'97 Audio for VIA Audio Controller.  Checking the hardware there is indeed a VIA VT8237P plus and a ReakTek ALC655 chip on the board.

I tried installing the Realtek Drivers from the RealTek site, but problem is the same.  Is there a way that I can somehow disable the sound drivers in Ubuntu to try and isolate the problem?  

Again, I also tried moving /usr/lib/wine/wineoss.drv.so with no effect.  Any suggestions appreciated, particularly for how to isolate if it is sound chip related....

Thanks!

Oh yeah, I am (trying to ) run wine ver .51 as well  dbc

---

### Post by Sandsound on 2008-01-24
> **Alp82 said:**
> [I found a solution]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg388445.html") for all people who got a complete system crash. If you have a soundcard with [Ice1724]("http://alsa.opensrc.org/Ice1724") chip  (in my case an ESI Juli@) just move the file** /usr/lib/wine/wineoss.drv.so** to somewhere else. **You won't get any sound from windows applications**, but wine should work.

Aha... so if I have a trouble with my graphics in wine, I just remove the graphics-card :confused:
(sorry... couldn't resist ;) )

Most users (including myself) only need wine to play games, and Guild Wars without sound is rather boring imho.
I found a .asoundrc file that did the trick for me, some thing about making a master for alsa, I admit I don't understand this file in detail, but it does the trick on my UbuntuStudio 7.10 and wine from the repros.

So if your soundcard use an ice1712 chip, you can try pasting the following into a file, name it .asoundrc and save it in your home-dir :

> 
pcm.ice1712 {
type hw
card 0
}

ctl.ice1712 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "softvol"
}

# softvol - Volume Control
pcm.softvol {
type softvol
slave.pcm "ice1712"
control {
name "PCM Volume"
card 0
}
}

# OSS to softvol:
pcm.dsp0 {
type plug
slave.pcm "softvol"
}

ctl.mixer0 {
type hw
card 0
}

---

### Post by sagarhshah on 2008-01-24
I have a similar configuration as skyout. K8M800 MoBo,  AMD Sempron 3600.

And my wine also crashes/hangs/freezes/you know what i mean
At first I thought it was my install of gutsy but searched the forums and found that I wasn't the only one.

Anyone work it out, please let us know

I'll be keeping an eye on this thread.

Sagar

---

### Post by Sliver85 on 2008-01-24
To fix it, I just removed my sound card, and Wine worked perfectly.

---

### Post by sagarhshah on 2008-01-24
If anyone has managed to get wine working on their systems could you please let us know what configuration you have on your computer so that other people with similar configurations may try it out.

I hate reading one/two line answers like
"I just fixed it by removing the soundcard and it worked."
or
"Haha, finally I can use wine after a year since this bug cropped up! cheers!"

It doesn't help us at all.
What we need is details.
What configuration your computer is and what you did to get it working.

Sagar

---

### Post by Sliver85 on 2008-01-24
Alright, sorry.

I have an AMD 4400+x2
Turtle Beach Riviera Sound Card
AC'97 Onboard Sound
Nvidia card (2 different ones that both caused crashing separately)

Wine crashed for me with both 32 and 64-bit versions of Ubuntu even on completely fresh installs.  Complete system hang as described in the thread.  All I did was remove my sound card and wine worked like a charm.  I could even plug it back in once the winecfg was created.

---

### Post by Sandsound on 2008-01-25
> **sagarhshah said:**
> If anyone has managed to get wine working on their systems could you please let us know what configuration you have on your computer so that other people with similar configurations may try it out.

As I mentioned in a [**previously post**]("http://ubuntuforums.org/showpost.php?p=4198365&postcount=48"), making a .asoundrc file did the trick for me.
ALSA have [**this**]("http://www.alsa-project.org/main/index.php/Asoundrc") page about it, but you might wanna google for one thats made for your card unless you want to make your own.

My specs are :
Athlon64
ASUS A8N-SLI Motherboard
Nvidia 6600GT
M-Audio Audiophile 2496

Besides the video-drivers from the "restricted drivers manegment", my Wine, ALSA and so on, is straight from the repros. I use standard UbuntuStudio 7.10 (Gutsy) and have installed from the Alternate CD.

I can use [**EnergyXT2**]("http://www.energy-xt.com/xt2.php") (and vst-instruments) with wine-alsa and play games like Guild Wars with wine-oss.

btw. If you play around with wine and need to reboot, you can just write wineboot in a terminal, this will reboot wine.

---

### Post by Alexstone on 2008-01-25
Still a problem here with ESIJuli@. (Ice 1724)
Wine hard freezes, and thats with Alsa already selected in wincfg (Took the card out and put it back.) No good either with renaming wineoss.drv. (I don't use oss)

Is there likely to be a fix for this in the near future? I've been to various sites so far, and no one seems to be interested in solving this, including the team at Alsa. Their response to one chap who wrote asking for help with the ice1724 issue, wasa bit curt to say the least, andthe chap did ask nicely. I appreciate their efforts over at Alsa, but it seems a bit like black magic and voodoo to understand what they're doing, and they don't seem to like a question or two at times.

I've had no response from Wine either, so i don't know if they're going to be rude to me or not! :)

If someone could at least explain WHY this doesn't work, and point me in the direction of a module that we can read and edit, then i can ask colleagues if they would assist. But not being able to get into the modules to fix anything seems a bit like commercial protection attitudes from here, and not in the spirit of open source.

Because if i can't get this going, then i'm stuck with using xp, or something else.
I write music (classical) full time, so it's essential for me to see this through, one way or the other.

It's times like this that i REALLY wish i could code, and i continue to admire and respect those that can, and give me the opportunity to use these tools.

Alex.


p.s. 

This a plea to the devs at Wine and Jack to get Jack midi working in wine audio. Jack works outstandingly well in linux for me (i'm using jackdmp from the brilliant dev Stephane) and with a tweak or two really performs well at low latencies.
If you chaps can do this, then the alsa problem ceases to exist, as the only contact with the HW and alsa will be from within Jack, and that bit's ok. (At least for Alsa, even if oss remains problematic.) I can live without oss, at a pinch, but having a stack of Jack midi ports available would mean i didn't need wineasio either, just simply route midi and audio to my wine DAW (Reaper) and back out again into linux. I write classical music, with sometimes up to 300 plus tracks at a time, so good routing is essential. with an onboard sound card i can do this with the help of a user compiled wineasio (recently rebuilt by a great fellow called 'Drumfix' from the Jacklab team), but using a soundcard with great convertors is out of the question at the moment.

I also make an optimistic plea to those devs who are building linux daws to consider using jack midi as priority as well for much the same reasons.Whether you like win programmes like Reaper or not, they do this well, and Reaper in particular provides a great model for how a DAW can be built that's easy to use, and does what it says on the tin. I like the principles of opensource and support them, but I remember when daws first came out, and how much of their code was taken from the opensource arena. Perhaps it's time to do the same in reverse, and have a look at cherry picking all the best bits from the commercial world.
Please don't construe this as a criticism. I'm here in linux using Ubuntustudio (which runs like clockwork) and happy with the extra options it gives me to work. There's just a few bits to tidy up as the saying goes. I will continue to support opensource, and as soon as a DAW hits the streets that really fires in a commercial usage capacity, then they will have gained a vocal, passionate, and determined supporter. 

Sorry about the rant, but all of you in the linux world are just one step away from taking over the world, and i'd dearly like to see it happen sooner rather than later.

You continue to have my full support and encouragement, as is evidenced in a thread i started over at the Reaper forum, documenting my journey in linux from the beginning.
[http://www.cockos.com/forum/showthread.php?t=15238](http://www.cockos.com/forum/showthread.php?t=15238)

---

### Post by Sandsound on 2008-01-25
> **Alexstone said:**
> Still a problem here with ESIJuli@. (Ice 1724)
Wine hard freezes, and thats with Alsa already selected in wincfg (Took the card out and put it back.) No good either with renaming wineoss.drv. (I don't use oss)

And you have tried the .asoundrc solution ?

I'm no expert, I just refuse to give up, so if you're up for the challenge, I'll gladly help out :-)

---

### Post by Alexstone on 2008-01-25
> **Sandsound said:**
> And you have tried the .asoundrc solution ?

I'm no expert, I just refuse to give up, so if you're up for the challenge, I'll gladly help out :-)

Sandsound, i'm the same, never give up, never surrender, hehe.

Tried the asoundrc, but it doesn't work. Wine still hard freezes when i open Reaper, or attempt  to open the audio tab in winecfg.

I had a thought though. I wonder if it's possible to compile Wine without any OSS at all?

Alex.

---

### Post by Sandsound on 2008-01-25
> **Alexstone said:**
> I had a thought though. I wonder if it's possible to compile Wine without any OSS at all?

I think It's possible to compile wine without OSS. you just use the --without switch ( --without-PACKAGE ) when compiling.
Not sure how to define without OSS thou, but if you want to compile without OpenGL, its :
> ./configure --without-opengl
so my guess is that you can do something similar like :
> ./configure --without-oss :-k


btw. did you install a clean Ubuntustudio 7.10 or just install the Studio-package in the repros ?

I haven't tried Reaper in a long time, so I'm of to do that :-)

---

### Post by Alexstone on 2008-01-25
> **Sandsound said:**
> I think It's possible to compile wine without OSS. you just use the --without switch ( --without-PACKAGE ) when compiling.
Not sure how to define without OSS thou, but if you want to compile without OpenGL, its :

so my guess is that you can do something similar like :
 :-k


btw. did you install a clean Ubuntustudio 7.10 or just install the Studio-package in the repros ?

I haven't tried Reaper in a long time, so I'm of to do that :-)


Clean install Sandsound.

How does Opengl affect this problem?

Alex.

---

### Post by Sandsound on 2008-01-26
> **Alexstone said:**
> How does Opengl affect this problem?

It doesn't, it was just the only example I could think of with the "./configure --without"

I guess you have tried to run winecfg from the terminal, does it say anything at all before it crashes ?

Tried Reaper last night, it acted kind'a strange, couldn't see my midi-ports (among other things) but I don't know if this is normal behavior for Reaper ? it almost felt like being back in Cubase... not exactly my cup of the :-)

---

### Post by Sandsound on 2008-02-02
Found this on WineHQ :
> **Running winecfg seems to hang or complain about files when I click the audio tab**

The hang is caused by the "NAS" sound driver. This causes it to pause for a while but it should respond eventually. The only way to get around this is to remove NAS from your system and/or build Wine without NAS support in the first place. If you see messages about JACK in the terminal they can be ignored unless you intend to use the JACK driver. If you wish to use the JACK driver then you need to install JACK's libraries onto your machine before JACK will work.

Have anyone tried removing NAS ?

EDIT: or perhaps setting the default sound driver in wine regedit ?

> Run "wine regedit", and locate the path:

    * HKEY_CURRENT_USER/Software/Wine/Drivers 

Change the value of the key "Audio" according to your system. If this is a fresh install, the "Audio" key may not be present, so just create a new one. This key is created when winecfg saves changes for the first time.

    * Audio = "" to disable the default sound driver
    * Audio = "OSS" to select the OSS sound driver. (This value has been reported as case sensitive)
    * Audio = "ALSA" to select the ALSA sound driver. 

Disabling the sound driver has allowed the Audio tab in winecfg to work on some systems, but on systems with aRts this may not work. Selecting the sound driver with winecfg will allow sound to work for your applications even if the Audio tab crashes.

---

### Post by samib on 2008-02-06
Total lock up appears to be a common problem with AMD64 installations. Had never tried using wine in Feisty however following upgrade to Gutsy thought I would try out wine. Thought the lock up the lock up may be due to Gutsy not upgrading correctly, so have completely removed wine and started again. Still lock up. Also tried running from terminal, message displyed about creating folder .winecfg then complete lock again. Also tried changing sound card settings but still lock up.  I have two machines one running Windows and the other Gutsy. My aim is to end up never having to use a Microsoft program and this lock up problem is frustrating my progress. Hopefully with more people raising this issue a solution will be found.

---

### Post by sneakmonkey on 2008-02-06
im having the same problem as everybody else in this thread i guess
my build is 

amd 4800+ X2
ati X1800XT 
and im using a PCI sound card Auzentech X-Plosion 7.1

one thing i noticed is that when starting an app with wine, occasionally i would hear a sort of crack from my speakers and im guessing theres some connection between hardware and wine but by reading the earlier posts in the thread thats already been determined.

I'm just posting to bump and help keep this thread up since it seems to be a common problem and I can only hope we can find a resolution.

---

### Post by Sandsound on 2008-02-07
Can any of you start regedit ?
$ wine regedit

If you can, then perhaps the problem is in winecfg's auto-detect feature.

---

### Post by messatsu on 2008-02-07
Nope.  Any wine command from the terminal (well, everywhere even) attempts to start the config dialogue which then locks the system up (for me).  I have no complete .wine folder as far as I can tell (only 18 files and mostly directories) at this point.

---

### Post by linus1970 on 2008-02-07
I had the same problem (winecfg locks up pc). Solved following the solution I found here: [http://td-e.com/tip/gutsy-wine-freeze.php](http://td-e.com/tip/gutsy-wine-freeze.php)

replacing "via" with "vesa" did not make the trick but  I addedto the  /etc/X11/xorg.conf : 

Section "Module"
        Disable "dri"
        Disable "glx"
EndSection

and it worked.

---

### Post by messatsu on 2008-02-07
That did it for me.:guitar:

---

### Post by sagarhshah on 2008-02-08
bump

---

### Post by alinalberta on 2008-04-26
I had the same problem (winecfg locks up pc). Solved following the solution I found here: [http://td-e.com/tip/gutsy-wine-freeze.php](http://td-e.com/tip/gutsy-wine-freeze.php)

replacing "via" with "vesa" did not make the trick but I addedto the /etc/X11/xorg.conf :

Section "Module"
Disable "dri"
Disable "glx"
EndSection

and it worked.

I am very much a newbie to ubuntu and was wondering if someone could expand on how to do this. This is pretty much greek to me.

Thanks

---

### Post by samib on 2008-04-27
I have finally solved my Wine lockup problem. 

Today I installed a new nvidia Geforce 5200 graphics card and can now configure Wine without any lockup.

I have tried running one Windows program under Wine and it seems to be running normally.

Hopefully this will save someone else hours of investigation.

---

### Post by alinalberta on 2008-04-28
> **alinalberta said:**
> I had the same problem (winecfg locks up pc). Solved following the solution I found here: [http://td-e.com/tip/gutsy-wine-freeze.php](http://td-e.com/tip/gutsy-wine-freeze.php)

replacing "via" with "vesa" did not make the trick but I addedto the /etc/X11/xorg.conf :

Section "Module"
Disable "dri"
Disable "glx"
EndSection

and it worked.

I am very much a newbie to ubuntu and was wondering if someone could expand on how to do this. This is pretty much greek to me.




Thanks



Never mind the above. I upgraded to the new Ubuntu 8.04 version (Hardy Heron ) and I can use Wine with no crashes.

---

### Post by Erratio on 2008-08-09
still have same problem here. thinking to upgrade to 8.04. is 8.04 stable?

---

### Post by ja2z on 2010-10-11
The last post on this subject seems to have been August 2007!! Did it get resolved?

I'm a newbie and have at last been able to get Ubuntu 10.4 running OK (fingers crossed) on my Samsung NC20, until now no other distro worked. But now Winecfg freezes the laptop completely, have to reboot.
I've done a purge wine and downloaded the 1.2.1 tarball but still no luck.
Can someone tell me how to be sure I'm installing the tarball and not some other corrupt version of wine please.

Many thanks in advance.
John

---

### Post by sendblink23 on 2010-10-11
> **ja2z said:**
> The last post on this subject seems to have been August 2007!! Did it get resolved?

I'm a newbie and have at last been able to get Ubuntu 10.4 running OK (fingers crossed) on my Samsung NC20, until now no other distro worked. But now Winecfg freezes the laptop completely, have to reboot.
I've done a purge wine and downloaded the 1.2.1 tarball but still no luck.
Can someone tell me how to be sure I'm installing the tarball and not some other corrupt version of wine please.

Many thanks in advance.
John

Can you test the new *wine.... first Uninstall your wine and use the latest one through this...

Open up Terminal:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.3
```

Then you will have wine 1.3.4 .. but if afterwards you still have the issue of freezing the computer... then on that case... its your hardware the issue :(

---

### Post by Enverex on 2010-10-11
Do what SendBlink suggested first and update Wine (although 1.3 is still old).

System lockups with Wine are almost always due to graphical driver issues, does your system lockup if you run glxinfo or glxgears?

---

### Post by ja2z on 2010-10-11
Many thanks for your speedy responses.
I followed all that, rebooted and it looked good until I tried to configure wine, which I think is the next step, then got the message:
"Wine could not find Gecko...wine can install it for you"
but the system was frozen so couldn't click the install button.
Followed the instructions on Gecko-the official wine wiki site ($ wget [http://downloads.sourceforge.net/wine/wine_gecko-1.1.0-x86.cab](http://downloads.sourceforge.net/wine/wine_gecko-1.1.0-x86.cab)
$ sudo mkdir -p /usr/share/wine/gecko
$ sudo mv wine_gecko-1.1.0-x86.cab /usr/share/wine/gecko/)
On trying to configure wine system froze, rebooted tried browse C.Drive got to the programme I want to install (Google Sketchup) then it froze, opened wine notepad, typed OK but it froze on save. 

I am using Ubuntu 10.4 Netbook version which seems to be working OK. Before this I tried other Ubuntu distros but always the display either pulsed plain coloured screens or flashed and flickered so I gave up until now. I wonder if this problem isn't due to something like a display driver etc.

---

