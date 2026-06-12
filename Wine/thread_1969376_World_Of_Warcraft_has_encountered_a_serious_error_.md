---
title: "World Of Warcraft has encountered a serious error and needs to close"
date: 2012-04-30
forum: Wine
---

### Post by Pinger05 on 2012-04-30
So here is the story. I stopped using Ubuntu after 9.10. Just got back into it with 12.04. My previous laptops I was able to install Wine then World of Warcraft and go about my merry way.

However that is not the case now.

So I have a Lenovo V570 with the Intel graphics card. I used the instructions provided on the WoW Wine Wiki [here]("http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine"). The actual install was the Windows install just moved over to the .wine/drive_c/Program Files/World of Warcraft/. directory. When I use the command > wine Wow.exe -opengl from the command line at the path above the Launcher comes up, I log in, choose a character then enter the realm. However after about 10 seconds I get a "Wow.exe has encountered a serious error and needs to close" error. The windows popup error is as follows

```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0032fbe4 EBP:0032fc44 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:000083f1 EBX:00008000 ECX:00000de1 EDX:160b1c58
 ESI:00000000 EDI:0ff32b78
```

Command line error is
```
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...

```

It is always a unhandled page fault.

Output of glxinfo | grep render is

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
    GL_NV_conditional_render, GL_ARB_ES2_compatibility, 
```

Wine version is 1.4.1.4-0ubuntu4.

I cant find anything conclusive in the /var/log/ directory regarding the error. Thank you for any assistance you can provide

---

### Post by Pinger05 on 2012-04-30
Ok I gave up. My research has indicated that this is a Wine error. So I am going to write a bug report and go back to Windows.

---

### Post by synaptix on 2012-04-30
I noticed you are using Wine 1.4...have you considering trying with the latest development version at all?

---

### Post by cwwilson721 on 2012-05-01
Search this forum for "intel+wow" and your answer will become obvious

---

### Post by Pinger05 on 2012-05-02
> **cwwilson721 said:**
> Search this forum for "intel+wow" and your answer will become obvious

There were 8 posts. Only one of them had a helpful suggestion:


Code:
sudo apt-get install driconf 
Open driconf, go to  the tab "image quality" and activate the S3TC texture compression, even  if the software support is not available. (Default is "no" change to  "yes")


Otherwise the  other 7 suggested I am SOL which is odd since i can run wow in Windows at high settings. My search string was "intel+wine".

---

### Post by cwwilson721 on 2012-05-02
> **Pinger05 said:**
> Otherwise the  other 7 suggested I am SOL which is odd since i can run wow in Windows at high settings. My search string was "intel+wine".

The reason you can run in Windows is explained many times.

Linux/wine uses OpenGL, which Intel FAILS AT MISERABLY.

Intel, for whatever reason, only cares about D3D, and thru that, Windows.

Good luck.

You'll need it. AFAIK, there have been very few real "successful" Intel/WoW/wine installs (By successful, I mean able to 25man raid at any type of usable framerate, ability to run around in a crowd in Stormwind, or not crashing or having odd video artifacts.)

It's not WoW's fault, nor wine, nor Linux, nor OpenGL. Blame is SQUARELY on Intel, and their lack of hardware support (and driver support) for OpenGL. They can do basic tasks very well, but as for games...Well, you have direct knowledge of that.

---

