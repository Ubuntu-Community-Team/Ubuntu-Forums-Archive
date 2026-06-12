---
title: "Wine in 32 bit and 64 bit versions of Ubuntu"
date: 2008-11-23
forum: Wine
---

### Post by almigi on 2008-11-23
This might be a silly question, but I was wondering if there is a difference in how Wine would function depending upon which version of Ubuntu it was running under. Right now on my machine I have the 64 bit version of 8.10, and I installed Wine the other day.  However, there is a program which according to information in Wine's appdb should function under Wine, however when I followed the instructions to install the program it did not work.

My question is this, if I were to download the 32 bit version of Ubuntu and install that on my system instead, is there a possibility it would work then, or would it be a waste of my time?

Here's some more info in case you're wondering: The program I'm trying to install is Final Fantasy XI.  I'm able to successfully run the setup.exe programs required to install it.  However, when I run pol.exe (The PlayOnline Viewer) the music plays, but I get a window that opens up, however there are no graphics in the window.  It's just a black window.

I've done some checking on the 'net to see what I could find, and there are a few reports of this happening, but I couldn't find any solution.  Does anyone here have any ideas?

Would running Wine under a 32bit version of Intrepid possibly solve my problem?

I've only had Ubuntu installed for a short period of time and I already enjoy using it 100% more then Windows, and if I can get FFXI to work under Wine, that would be great.

Also, the appdb for Wine mentions something about a "sanity patch" for Wine.  However, I've also read in other places that the new releases of Wine no longer require it.  Even so, is it possible that this is causing my problem?  If so, I'm still a Linux newbie, is it possible for me to obtain a version of Wine with the patch already applied instead of me trying to recompile the source code myself?

Thanks!

- Alan

---

### Post by almigi on 2008-11-23
I may have solved my own probelm!  I messed with some settings in winecfg and it works.

It seems that it does make a difference whether or not I enable a virtual desktop (according to the appdb it's optional for this program).  When I do, it works!

---

