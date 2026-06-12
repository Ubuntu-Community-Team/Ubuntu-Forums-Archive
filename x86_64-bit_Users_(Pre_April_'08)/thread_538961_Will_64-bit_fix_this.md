---
title: "Will 64-bit fix this?"
date: 2007-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thelasko on 2007-08-30
I am running a Dell Core 2 Duo E4300 with the G965 integrated graphics (yes, I have the latest intel driver from the repository).  I also dual boot with Vista.  I must have been living under a rock because I didn't realize the Core 2 was 64-bit and I installed x86 Feisty.  I have noticed a few problems and am wondering if switching to 64-bit Feisty might fix them.

1. The system clock (the one that tells the time) runs at about *half the speed* it should.  This is extremely annoying.  I am wondering if the 64 bit version might fix this since I have read so much about clocks running *fast* under AMD64 processors.  I tried all of the fixes for 32 bit and none of them worked.  It's not my hardware it works in Vista.

2. I have problems with video playback.  I know there are issues with compiz and video playback.  Gmplayer does work decently with compiz disabled.  However, no other video players will work.  VLC plays  video at about half the speed it should (I am wondering if this is related to the clock thing).  It seems like my graphics card runs out of power quickly under Linux but when I switch to Vista it's quite snappy.  This seems a little counter intuitive but may just be an example of Intel providing better drivers for Vista. 

I am wondering will switching to 64-bit Feisty have any effect on my clock and give my graphics card the boost it has in Vista (especially since it's integrated)?
:guitar:

---

### Post by nowhere.elysium on 2007-08-30
Switching to the 64-bit edition will make the processor responses feel quicker, certainly. not so sure about the integrated graphics. it depends on how tightly bound in with the processor it is, i suppose.

---

### Post by viciouslime on 2007-08-30
Have you tired running something that will stress the processor for a period of time? The processor will run at half the speed unless you actually try to use it, this is to lower power consumption. The same occurs in vista, vista just doesn't bother to tell you about it.

Your video issues are very odd however... there is no reason 64 bit will fix that, however, I would recommend using the 64bit version anyway. Flash is a little tricky to set up, but there are guides on the forums and once gutsy is released that will ship with nspluginwrapper which makes the whole thing a lot easier.

---

### Post by Thelasko on 2007-08-31
Last night I booted the 64-bit live CD.  WOW!  That is a **MASSIVE PERCEPTIBLE PERFORMANCE INCREASE**!  It actually *feels *twice as fast.  I bet if I ran some benchmarks I would discover that it *is *twice as fast.  I don't know if this is because the system is running from RAM but I doubt that's the reason.  Graphics are very impressive.  My machine now does new tricks I never knew it was capable of.

The clock seems to be fixed.  I ran it all night and it didn't lose any time.  I also installed VLC and it worked perfectly.  I installed Compiz and it too worked perfectly.  I can now play a video in VLC and drag it around the screen and watch it wobble.  I have *never *been able to do this.  Now I see why Ubuntu blows Vista out of the water.  

My guess is the GPU requires 64-bit to work.  There are many posts on the forums about problems with the G965.  It's probably because they are all running 32-bit Ubuntu.

I plan on installing 64-bit when I get some more time.  Can I simply copy my home folder from the old install to the new one to keep all of my settings?

Thanks,
The Lasko
:guitar:

---

### Post by dabl on 2007-08-31
> **Thelasko said:**
> 

Can I simply copy my home folder from the old install to the new one to keep all of my settings?



Boy, that sounds dangerous.  Supposedly you can ... so I hear, but what if there were settings applicable to your prior setup that were part of the problem?  Unless it took you a _lot_ of time to achieve your prior setup, I'm thinking I wouldn't risk it.  Just copy the data that is saved there to the new /home folder, and then set it up again the way you want it -- that would be my recommendation.

:popcorn:

---

### Post by raijinsetsu on 2007-08-31
You shouldn't have any settings in your home folder that affect system performance. It is normally safe to copy the home folder between systems. I've had the same home folder on my server, and it started in Gentoo, migrated to Kubuntu, and will soon be Ubuntu-64. You may want to clean up the directory before you move it though. For instance, delete all the hidden directories and files in your home directory, except for your web-browser or e-mail(so you don't lose bookmarks or e-mails) directories.

---

### Post by rsambuca on 2007-08-31
I am not so sure that using the same home folder from 32bit to 64bit will work, but if you are willing to try... :)

---

### Post by raijinsetsu on 2007-08-31
Home folders do not contain system/platform specific configuration. Home folders are not the Windows registry, or an extension of the etc folder. They contain settings for the programs a user has used. Also, there is no change between 32 and 64 bit, because there are no binary files, only text.

---

### Post by rsambuca on 2007-08-31
Cool!  Thanks for that info.  For some reason I was under the impression that there was more in the home folder than that.

---

### Post by raijinsetsu on 2007-08-31
Let me clarify: when I said "no binary files" what I meant was "no binary files used in configuring the system". I just forgot that documents and the like can be binary, but they have no control over the system.
So, unless you've done some extremely wrong and very very very strange things, then it's perfectly fine to copy home directories between systems.
If you're really worried, you can just delete all those "." hidden files, except those that you know you need (like the ones for your browser, e-mail, and IM client).

---

### Post by Thelasko on 2007-08-31
Excellent!  This should make my switch to 64-bit much quicker. Thanks!

---

### Post by Thelasko on 2007-09-04
I switched to 64-bit last night.  I tried to move my home directory over and it didn't like it.  It gave me an error about permissions to $HOME.  I think it's because I tried to replace the existing home directory with my old one.  I had to reinstall Ubuntu this morning and this time tried to just move the contents of my home folder over.  I chose not to replace some hidden folders that were about permissions and startup and shutdown logs.  Everything seems to work fine now.

---

### Post by afonic on 2007-09-04
> **Thelasko said:**
> 
1. The system clock runs at about *half the speed* it should.  This is extremely annoying.  I am wondering if the 64 bit version might fix this since I have read so much about clocks running *fast* under AMD64 processors.  I tried all of the fixes for 32 bit and none of them worked.  It's not my hardware it works in Vista.

It just does that for power saving. When the CPU is in high load it runs at full speed. It does it in Windows too, you just haven't noticed! :)

To test it, download CPU Burn-In for Linux:
[http://users.bigpond.net.au/cpuburn/](http://users.bigpond.net.au/cpuburn/)

Then open two terminals and runs it twice (so that it uses both cores). Type cat /proc/cpuinfo and you should see the "real" speed of your CPU.

---

### Post by Thelasko on 2007-09-04
I think I stated my question wrong.  I'm not a computer expert so I don't know how to differentiate the CPU clock from the clock that is displayed on my monitor that tells me what time it is.  When I said "system clock" I was referring to the one that tells me the time.  Sorry for the confusion.  It appears to be solved with 64-bit but I will confirm that after I let it run for a while.

---

### Post by rsambuca on 2007-09-04
Do you mean that it actually takes exactly two minutes for every minute?  Neat!  I have never seen that before.

---

### Post by mysticmatrix on 2007-09-04
> **Thelasko said:**
> I am running a Dell Core 2 Duo E4300 with the G965 integrated graphics (yes, I have the latest intel driver from the repository).  I also dual boot with Vista.  I must have been living under a rock because I didn't realize the Core 2 was 64-bit and I installed x86 Feisty.  I have noticed a few problems and am wondering if switching to 64-bit Feisty might fix them.

1. The system clock runs at about *half the speed* it should.  This is extremely annoying.  I am wondering if the 64 bit version might fix this since I have read so much about clocks running *fast* under AMD64 processors.  I tried all of the fixes for 32 bit and none of them worked.  It's not my hardware it works in Vista.

2. I have problems with video playback.  I know there are issues with compiz and video playback.  Gmplayer does work decently with compiz disabled.  However, no other video players will work.  VLC plays  video at about half the speed it should (I am wondering if this is related to the clock thing).  It seems like my graphics card runs out of power quickly under Linux but when I switch to Vista it's quite snappy.  This seems a little counter intuitive but may just be an example of Intel providing better drivers for Vista. 

I am wondering will switching to 64-bit Feisty have any effect on my clock and give my graphics card the boost it has in Vista (especially since it's integrated)?
:guitar:


Compiz problem are the one sure not to go away. remember, compiz is a ALPHA software. Hell it's not even Beta. So expect that things won't run smooth. The workaround to get both Compiz and Video's to run together is to use X11 driver for video output.

About intel driver support, it's as bad in vista as in Linux. Vista still has to wait for complete drivers for X3000, and linux one support only openGL 1.4(The hardware support 1.5).

Coming back to processor, our core 2 duo support dynamic clock rescaling, meaning CPU runs only to frequency that is needed. You can disable this from BIOS if you want. However your problem is that time indicating clock runs at half the speed which is a little weird.

Also try to increase your ram to full 384 MB from the bios. The default is set to 256 Mb, and increasing it generally help.

---

### Post by Thelasko on 2007-09-04
> **mysticmatrix said:**
> Compiz problem are the one sure not to go away. remember, compiz is a ALPHA software. Hell it's not even Beta. So expect that things won't run smooth. The workaround to get both Compiz and Video's to run together is to use X11 driver for video output.


My X11 driver didn't work in 32 bit.  The only thing that remotely worked was OpenGL and very poorly.  The X11 driver works in 64-bit very well.

Thanks

---

### Post by Thelasko on 2007-09-05
A note to those who read this and are thinking about moving their home folder from install to install:  Certain programs do keep their settings in that directory and can cause problems.  However I do think it is worth the trouble to copy over your home directory.  In summary:

Pros:

1) all of my e-mail and email settings transfered beautifully.

2) all of my Firefox settings transfered over beautifully.

3) Gaim/Pidgin settings transfered over beautifully.

4) My desktop settings transfered over.

Cons:

1) My Automatix settings transfered over.  I don't know why Automatix saves it's list of installed programs in your home directory but it does.

2) I have not confirmed this yet but it appears my Compiz settings transfered over too.  

3) any programs you had problems with in your old install will probably have problems in your new install if you carry over your settings with your home directory.

I also note that my 64-bit install can read and write NTFS file systems by default when my 32-bit install needed special software.  Odd.

---

### Post by rsambuca on 2007-09-05
> **Thelasko said:**
> I also note that my 64-bit install can read and write NTFS file systems by default when my 32-bit install needed special software.  Odd.
ntfs-3g is not enabled by default in Feisty.  Just so people know.

---

### Post by Thelasko on 2007-09-05
> **rsambuca said:**
> ntfs-3g is not enabled by default in Feisty.  Just so people know.

Is it in the repositories?  I thought I had to install it separately because of proprietary licenses.  I'm very surprised that I could read those partitions.  

I also noticed some of my links don't work.  Any thoughts on that?  It's no big deal, I can make new ones.

---

