---
title: "CoD4 startup problem: sound error"
date: 2008-02-23
forum: Wine
---

### Post by DingsBumps on 2008-02-23
Following ahaslm's post [here]("http://ubuntuforums.org/showthread.php?t=641987&page=2"), I set up 32bit wine and started CoD4 using the following command:

```
marc@marc-desktop:~$ cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare && wine iw3sp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f8fc,0x00000000), stub!
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

As you can see, there is a problem. When run the command, the CoD4 loading window comes up, and then the console comes up and flashed the message:

```
Error during initialization:
Video card or driver doesn't support separate alpha blend, glow will be disabled.
```

I click OK on that little pop-up window, and then the full console window comes up and shows:

```
----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
----- R_Init -----
Getting Direct3D 9 interface...
Pixel shader version is 3.0
Vertex shader version is 3.0
Video card or driver doesn't accelerate dynamic textures.
Video card or driver doesn't support separate alpha blend, glow will be disabled.


Error during initialization:
Video card or driver doesn't support separate alpha blend, glow will be disabled.
```

---

### Post by ahaslam on 2008-02-24
It looks as though the 3dmark patch didn't apply.

---

### Post by DingsBumps on 2008-02-24
So in that guide, I followed the x64 link and did those steps. Then, on your post, ahaslam, I skipped the first 2 code boxes. Was I supposed to do something with the code in those 2 first boxes? Which commands did I need to run?

---

### Post by ahaslam on 2008-02-24
Are you running 64bit or 32bit Ubuntu (you mentioned 32 in your op)? 
If you're on 32bit, follow my guide to the letter. If not, you need to incorporate the additional steps found within that link, not substitute them. I mentioned the parts that need attention, please read.

PS. What leads you to believe there's a sound issue?

---

### Post by DingsBumps on 2008-02-24
I'm running 64 bit. Sorry for the confusion, I was under the impression that what I was doing was compiling the 32bit version of the program. That might be a wrong impression. 

So you are saying that I need to first do all the steps in the link, then follow all the steps in your guide, to the letter?
If that is the case, and considering that I have already done all the steps besides the first two code boxes, could I just start at the beginning of the guide with no adverse effects?

The reason I beleived I had a sound issue was that the original error message regarded the Miles Sound System and being unable to access dx9. I then realized I hadn't copied the requied Dx9 files from a windows install. I did that, and this new error message started popping up when I ran CoD. The title is the result of a mind fart. Oops.

P.S. Thank you for all your help ahaslam. It's really appreciated!

---

### Post by ahaslam on 2008-02-24
> **DingsBumps said:**
> So you are saying that I need to first do all the steps in the link, then follow all the steps in your guide, to the letter?
If that is the case, and considering that I have already done all the steps besides the first two code boxes, could I just start at the beginning of the guide with no adverse effects?

No & no. Use the details within the 64bit link as an *addition* to my guide. I have specified the areas where attention is needed. Essentially all that's needed in addition to the 64bit guideis the the 3dmark patch:
> wget [http://bugs.winehq.org/attachment.cgi?id=8548](http://bugs.winehq.org/attachment.cgi?id=8548)
cp attachment.cgi\?id\=8548 wine-0.9.50/3dmark.diff && cd wine-0.9.50
patch -p1 < 3dmark.diff
I hope you get it working, if nothing more than to fragg you ;)

---

### Post by DingsBumps on 2008-02-24
Alright, so considering what I've already done, what should I do. How can I remove what I have already done?

And by the way, when I do get it working, watch your back or you won't even see my knife coming at you.

---

