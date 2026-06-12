---
title: "[SOLVED] NO DVD Play Back using Movie Player"
date: 2007-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-06-11
Okay, it works perfect in 7.04 32bit but not 64bit.  Player says it needs plugins installed.  Please tell me which ones need to be installed.  These are NON-Protect and Protected alike.

It just won't play DVDs

---

### Post by Kilz on 2007-06-11
> **crjackson said:**
> Okay, it works perfect in 7.04 32bit but not 64bit.  Player says it needs plugins installed.  Please tell me which ones need to be installed.  These are NON-Protect and Protected alike.

It just won't play DVDs

[Go here]("https://help.ubuntu.com/community/") Bookmark the page, the Ubuntu wiki has lots of good info for solving all kinds of problems. Type DVD into the search box in upper right hand corner. Find a result with restricted in the title. Read and follow the directions.  :D

---

### Post by crjackson on 2007-06-11
Did it, must be doing something wrong.  It installed everything as far as I can tell, but still complains of not having plugins to play DVD.  Guess I try again later.

---

### Post by crjackson on 2007-06-11
Oh yeah, it won't even play the NON-protected DVD's

---

### Post by crjackson on 2007-06-11
I tried installing Kaffeine and didn't work either.  Same exact error.  I'm missing something easy and fundamental.

Even had problems installing wine until Kilz was kind enough to break it down for me.  Went off without a hitch then....   I'm such a Linux newbie...   Ubuntubie I guess:D

It's funny, all my friends call me for help with hardware and windblows - Now I'm a neophyte with ubuntu.

---

### Post by Kilz on 2007-06-11
> **crjackson said:**
> I tried installing Kaffeine and didn't work either.  Same exact error.  I'm missing something easy and fundamental.

Even had problems installing wine until Kilz was kind enough to break it down for me.  Went off without a hitch then....   I'm such a Linux newbie...   Ubuntubie I guess:D

It's funny, all my friends call me for help with hardware and windblows - Now I'm a neophyte with ubuntu.

Welcome to WA (Windows Anonymous), you are at about step 5 of 10.  :D 

Ok lets take it one thing at a time. Exactly what did you do already to try and get the dvd player reading dvd's?  Also can you put a data dvd, like a game or other non video dvd, in the drive and access the files on it?

---

### Post by crjackson on 2007-06-11
> **Kilz said:**
> Welcome to WA (Windows Anonymous), you are at about step 5 of 10.  :D 

Ok lets take it one thing at a time. Exactly what did you do already to try and get the dvd player reading dvd's?  Also can you put a data dvd, like a game or other non video dvd, in the drive and access the files on it?

It reads DVD's fine as far as any files or Data, including video DVD.  It just won't play them.  I can play AVI files but not the MOVIE files of a DVD.

I installed the listed packages there were about 3 of them lib.... and I installd the CSS2... package.

Same result, MPlayer reports missing plugins.  I gave up on that and installed the Kaffeine player and it gives a similar error about plugins.

That's about it so far...

---

### Post by Kilz on 2007-06-11
> **crjackson said:**
> It reads DVD's fine as far as any files or Data, including video DVD.  It just won't play them.  I can play AVI files but not the MOVIE files of a DVD.

I installed the listed packages there were about 3 of them lib.... and I installd the CSS2... package.

Same result, MPlayer reports missing plugins.  I gave up on that and installed the Kaffeine player and it gives a similar error about plugins.

That's about it so far...

Did you install any of these packages?


libdvdread3
libxine1-ffmpeg
libdvdcss2

---

### Post by crjackson on 2007-06-11
> **Kilz said:**
> Did you install any of these packages?


libdvdread3
libxine1-ffmpeg
libdvdcss2


Yes, all 3

---

### Post by Kilz on 2007-06-11
> **crjackson said:**
> Yes, all 3

Ok, I went and looked at the Feisty package. The old setup script is still included.

Try this

open a terminal and type or copy/paste this in

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by capecove on 2007-06-11
I can verify that it works fine in Ubuntu Feisty 64 bit. I can also verify that I had a little trouble until I did exactly what Kilz suggested above. Now, it works like a champ!

---

### Post by Kilz on 2007-06-11
> **capecove said:**
> I can verify that it works fine in Ubuntu Feisty 64 bit. I can also verify that I had a little trouble until I did exactly what Kilz suggested above. Now, it works like a champ!

Its been a problem for a long time. The documentation always seems to forget to post this solution. Im just glad they leave the script in place. Otherwise you cant play or backup movies. I have this need to backup every DVD I own because I have a 13 year old who cant quite get the idea that you need o put them back in th case after you watch a dvd. K9copy is a wounderful application that has saved me a lot of cash. Bought in the 100 stack, DVD +r's are .32 cents, much better than $19 for another copy of a movie from the store.

---

### Post by capecove on 2007-06-11
No kidding, thanks for the tip! My wife and I treat ours well but just because we do doesn't mean accidents can't happen.

---

### Post by crjackson on 2007-06-11
> **Kilz said:**
> Its been a problem for a long time. The documentation always seems to forget to post this solution. Im just glad they leave the script in place. Otherwise you cant play or backup movies. I have this need to backup every DVD I own because I have a 13 year old who cant quite get the idea that you need o put them back in th case after you watch a dvd. K9copy is a wounderful application that has saved me a lot of cash. Bought in the 100 stack, DVD +r's are .32 cents, much better than $19 for another copy of a movie from the store.

Good stuff - It's one of the reasons I still have an image of winxp for now.  I have 6 kids, and they always destroy DVD's as well.  I've backed up approx. 350 DVD's so far but I was wondering what the best app. for Linux is.  You have just averted one of my next threads.

I'm slowly setting up -U- one day at a time until I get everything worked out.  With each satisfactory tweak, I create/update my disk image to reflect same.  Then when I need to do something that my U install isn't ready for yet, I just restore my Acronis image of XP to get the task done.  I'm chipping away at it and booting into windows less and less now.

I have 8 machines in my house 7 are 64bit and 1 is 32bit.  7 of those will be U machines, the last one - 32bit will probably stay windows, because my wife doesn't want to learn a new OS.

Man, she screamed bloody murder when I upgraded her old (no longer exsistant) machine from Win-ME to XP.  She hates change, I love it...

I'm at work right now.  When I get home, I'll reload the U image and give that code a chance to work it's magic.  I'll also install the K9copy app and see how it does.  Does K9copy get updated for newer copy protections?

---

### Post by Kilz on 2007-06-11
> **crjackson said:**
> Good stuff - It's one of the reasons I still have an image of winxp for now.  I have 6 kids, and they always destroy DVD's as well.  I've backed up approx. 350 DVD's so far but I was wondering what the best app. for Linux is.  You have just averted one of my next threads.

I'm slowly setting up -U- one day at a time until I get everything worked out.  With each satisfactory tweak, I create/update my disk image to reflect same.  Then when I need to do something that my U install isn't ready for yet, I just restore my Acronis image of XP to get the task done.  I'm chipping away at it and booting into windows less and less now.

I have 8 machines in my house 7 are 64bit and 1 is 32bit.  7 of those will be U machines, the last one - 32bit will probably stay windows, because my wife doesn't want to learn a new OS.

Man, she screamed bloody murder when I upgraded her old (no longer exsistant) machine from Win-ME to XP.  She hates change, I love it...

I'm at work right now.  When I get home, I'll reload the U image and give that code a chance to work it's magic.  I'll also install the K9copy app and see how it does.  Does K9copy get updated for newer copy protections?

Slowly, but there will always be a dvd that will give you problems. If you use dvdshrink in windows, you will feel right at home with k9copy. Its a kde application, so it takes a little bit to start in gnome. Also some people dont like to mix applications from kde and gnome. But i like a mix.

---

### Post by crjackson on 2007-06-11
I've never tired DVDshrink.  I use DVDFabHDDecrypter to rip, and DVD2ONE to compress if needed - Then I usually burn using ImgBurn.

Man I wish these apps had Linux versions - I may try some wine with these progies once I get my other kinks worked out.  DVDFab updates so often it will make your head spin.  These and Vegas Video7 are my main tasks I need to work out in Linux.

---

### Post by capecove on 2007-06-11
crjackson...

Have you seen [http://www.linuxeq.com](http://www.linuxeq.com) ? They may have some stuff there to help you out...

---

### Post by crjackson on 2007-06-11
> **capecove said:**
> crjackson...

Have you seen [http://www.linuxeq.com](http://www.linuxeq.com) ? They may have some stuff there to help you out...


Great stuff...  I already see a thing or two I'm going to grab.  Thanks...:)

---

### Post by crjackson on 2007-06-12
> **Kilz said:**
> Ok, I went and looked at the Feisty package. The old setup script is still included.

Try this

open a terminal and type or copy/paste this in

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

This code ran but it finally ended with an error 77 output.  I have no idea what that is.

However in a parallel thread at [http://ubuntuforums.org/showthread.php?t=440154](http://ubuntuforums.org/showthread.php?t=440154)

I followed the instructions and Bada Bing! it worked.  Mplayer now plays my DVD's - at least the non-copy protected ones.  I haven't tested the originals just yet, but I suspect they will work just fine.

---

### Post by crjackson on 2007-06-12
I've gotta say, so far I'm not happy with the DVD tools available.  Especially ones that are for making ISO's .  I really wish UltraISO came in Linux versions as well as DVDFabHDDecrypter.

WINE?  So far nothing I have runs correctly or even close using wine.  Gnome crashes and I get screen corruption.

I removed WINE.  I guess for now I'll have to maintain a duel OS system.:(

Even K9copy can't find my optical drives.  K3b does and NERO Linux does.  If NERO would only do ISO's like the Windows version I'd be okay.

---

### Post by capecove on 2007-06-12
Well, be patient. The tools you are looking for will come. This system requires us to give feedback for the tools we want to see/use. There are those out there receptive to others needs.

I really have to highly, yet again, suggest Virtualbox. It works so very well. :)

---

### Post by crjackson on 2007-06-12
> **capecove said:**
> Well, be patient. The tools you are looking for will come. This system requires us to give feedback for the tools we want to see/use. There are those out there receptive to others needs.

I really have to highly, yet again, suggest Virtualbox. It works so very well. :)

Your suggestions have not fallen upon deaf ears.  I intend to do just that, but 1st I need to work out as many kinks as possible, and learn my way around the OS.

I still have some hardware tweaks - ATI Video card driver - I know this one will be hard.  I can't even get my screen refresh above 60Hz at any resolution.

Then there is my Canon Scanner.  It's recognized and pretends to scan, but the scan light doesn't come on and it aquires a black page.

Once I get all the little things like that, then I'll tackle the bigger things like a Vbox.  That's totally foreign to me, so I'm taking this one issue at a time.;)

---

### Post by Kilz on 2007-06-12
> **crjackson said:**
> Your suggestions have not fallen upon deaf ears.  I intend to do just that, but 1st I need to work out as many kinks as possible, and learn my way around the OS.

I still have some hardware tweaks - ATI Video card driver - I know this one will be hard.  I can't even get my screen refresh above 60Hz at any resolution.

Then there is my Canon Scanner.  It's recognized and pretends to scan, but the scan light doesn't come on and it aquires a black page.

Once I get all the little things like that, then I'll tackle the bigger things like a Vbox.  That's totally foreign to me, so I'm taking this one issue at a time.;)

Take a look here for the ATI driver issue. If you want accelerated graphics you want to use method 2 and install the official ATI driver.
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by crjackson on 2007-06-13
> **Kilz said:**
> Take a look here for the ATI driver issue. If you want accelerated graphics you want to use method 2 and install the official ATI driver.
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Thank GOD for copy/paste - I followed the guide and it installed the ATI driver.  I have many more resolution options and a few more refresh options.

I ran the Post-Installation Check and it reports:

charles@charles-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 TCL
OpenGL version string: 1.3 Mesa 6.5.2

It placed the ATI Control Center Launcher in my Applications menu but it doesn't do anything at all when I click on it.

I got an error during the final steps when I cut and past the following code:

sudo mkdir /lib/modules/$(uname -r)/volatile
                                  and
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

I gried changing the $(uname -r) to my actual login name as well but still an error in creating a directory.  Also these didn't work either:

sudo aticonfig --initial

Then:

sudo aticonfig --overlay-type=Xv

It told me it was already configed...

Am I missing something or am I through?

Also how do I add the option to make my screen refresh 100Mhz?

Thanks for all the help...

---

### Post by crjackson on 2007-06-13
> **crjackson said:**
> Thank GOD for copy/paste - I followed the guide and it installed the ATI driver.  I have many more resolution options and a few more refresh options.

I ran the Post-Installation Check and it reports:

charles@charles-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 TCL
OpenGL version string: 1.3 Mesa 6.5.2

It placed the ATI Control Center Launcher in my Applications menu but it doesn't do anything at all when I click on it.

I got an error during the final steps when I cut and past the following code:

sudo mkdir /lib/modules/$(uname -r)/volatile
                                  and
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

I gried changing the $(uname -r) to my actual login name as well but still an error in creating a directory.  Also these didn't work either:

sudo aticonfig --initial

Then:

sudo aticonfig --overlay-type=Xv

It told me it was already configed...

Am I missing something or am I through?

Also how do I add the option to make my screen refresh 100Mhz?

Thanks for all the help...

**[SIZE="7"]KILZ[/SIZE]**

If you get a chance, please look at and respond the the above post.  Sorry to bug you, but it's the price you pay for being the most helpful person I've run accross here.

I want to know if the result was normal or not, and what/how do I edit to add missing refresh rates...

Thanks

---

### Post by Kilz on 2007-06-13
> **crjackson said:**
> KILZ

If you get a chance, please look at and respond the the above post.  Sorry to bug you, but it's the price you pay for being the most helpful person I've run accross here.

I want to know if the result was normal or not, and what/how do I edit to add missing refresh rates...

Thanks

What happened isnt really normal. The result from fglrxinfo should say ATI not Mesa. But I will admit , I am not the most knowledgeable on video drivers, I mainly send people to the page I linked to because its easy to do. You could also[ look at this page in the Ubuntu wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to see if it can help.
I will tell you that I was never able to get real high refresh rates myself. The highest was 80, and I have a Mitsubishi Dimondtron that should handle 100.

---

### Post by crjackson on 2007-06-13
> **Kilz said:**
> What happened isnt really normal. The result from fglrxinfo should say ATI not Mesa. But I will admit , I am not the most knowledgeable on video drivers, I mainly send people to the page I linked to because its easy to do. You could also[ look at this page in the Ubuntu wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to see if it can help.
I will tell you that I was never able to get real high refresh rates myself. The highest was 80, and I have a Mitsubishi Dimondtron that should handle 100.

Yeah, that's a long set of instructions on that wiki (for an old man with poor eyes like me;) ).  If I try to install again, should I remove these last ones first?  If so, how does one do that?  Can I install over top of them using a different method.

Perhaps I should just leave it alone - I don't know, **_what wouldj you suggest?_**

---

### Post by Kilz on 2007-06-14
> **crjackson said:**
> Yeah, that's a long set of instructions on that wiki (for an old man with poor eyes like me;) ).  If I try to install again, should I remove these last ones first?  If so, how does one do that?  Can I install over top of them using a different method.

Perhaps I should just leave it alone - I don't know, **_what wouldj you suggest?_**

That depends on what you are going to be using the computer for. If you need accelerated graphics for gaming or 3d modeling for example you need the ati to show not mesa.
But if all you need is to browse, look at videos, write emails and documents, listen to music. Then as long as the refresh is in the 75+ range its a waste of time to mess with it.
If you do try other things for the most part they will install over what you installed .... to my limited video driver knowledge. The reason I say it also is because if you start removing things, you may boot to a command prompt.
You might also try posting in the  [Video sub section]("http://ubuntuforums.org/forumdisplay.php?f=138") of the forum to get advice from people who have more knowledge on this subject than me.

---

### Post by crjackson on 2007-06-14
> **Kilz said:**
> That depends on what you are going to be using the computer for. If you need accelerated graphics for gaming or 3d modeling for example you need the ati to show not mesa.
But if all you need is to browse, look at videos, write emails and documents, listen to music. Then as long as the refresh is in the 75+ range its a waste of time to mess with it.
If you do try other things for the most part they will install over what you installed .... to my limited video driver knowledge. The reason I say it also is because if you start removing things, you may boot to a command prompt.
You might also try posting in the  [Video sub section]("http://ubuntuforums.org/forumdisplay.php?f=138") of the forum to get advice from people who have more knowledge on this subject than me.

I reinstalled again but it didn't change a single thing.  I do a fair amount of video editing but I'm using Sony Vegas 7 under WinXP that for right now.  I've started to check out an app. called Kino.  It's very bland but seems to to most of the basic stuff I need, so I'm learning it's feature set.

My refresh rate is 85Hz.  It's doable at 1024x768.  Higher resolutions drop the refresh rate to 60Hz and BELOW.  Not doable for anything at all.

I don't mind that if uninstalling botches things up.  I have a good backup image that I can restore in 3 minutes if it happens.

I just don't know how to go about attempting a removal so I can try for a good install.  I will poke around in the video forum as you suggest.  Thanks...

---

### Post by H264 on 2007-08-27
kilz: this script works for me too... whenever I put in a DVD it used to say "An error occurred Could not read from resource." now it works fine :)

crjackson: you should be able to use VLC to rip DVDs in any format... I used it once to convert an AVI movie into H.264 format. VLC is almost a front end GUI to FFMPEG.

---

