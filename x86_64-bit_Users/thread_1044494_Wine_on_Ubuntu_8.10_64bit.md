---
title: "Wine on Ubuntu 8.10 64bit"
date: 2009-01-19
forum: x86 64-bit Users
---

### Post by Serrya on 2009-01-19
Hello I have a complicated question, I'll try to state it in the simplest way I can.

I currently have a laptop running Hardy Heron (pure Linux machine). and WINE. It has an AMD 64 bit core but an ATI graphics card. Wine will install PC games just fine, but when I try to run a game (like Tales of Pirates or Guild Wars for example) It will bring up the loading screen, load the game but just as its about to run, Wine and the game just shut down. (I have Wine set up so that it runs in its own "window" and the whole window shuts down). 

Now here is my real question. I am getting a new laptop with these specs:

INTEL CORE 2 DUO T9400 VHP 64BIT*
4G-DDR2,640GB(320X2)
BD COMBO
15.4"WSXGA+
NV 9800M 512M DDR3 

And I want this laptop to be pure Ubuntu linux as well, but I was wondering if I should expect the same problems with wine as I had before. Is it a 64 bit problem? An ATI problem? or merely an incompatibility with the programs I'm trying to run in wine? 

Any insight on how to make a Linux-only machine run non linux stuff (games: everything else I use open source) easier would be great :)

---

### Post by jespdj on 2009-01-19
Not all Windows software runs without problems on WINE. Look in the [WINE Application Database](http://appdb.winehq.org/) if there's information about those games you want to run.

Are you sure you have an ATI graphics card? Because this line:
> NV 9800M 512M DDR3
suggests that you have an **nVidia** 9800M, and not an ATI graphics card.

---

### Post by cjazz on 2009-01-19
> **jespdj said:**
> 

Are you sure you have an ATI graphics card? Because this line:

suggests that you have an **nVidia** 9800M, and not an ATI graphics card.

If you'll look again, jespdj, I believe you'll find the line you quoted refers to the system OP wants to get, not the one he or she already has.

---

### Post by Ng Oon-Ee on 2009-01-19
As jespdj says, you'll have to check the appdb, but I do believe Guild Wars was supposed to run Platinum? Haven't specifically looked for it yet.

Anyway, the general feeling seems to be that NVidia is (for now) the way to go, less problems overall. My laptop is running a 9300M, I can play the games I want (WC3, NWN2, and Civ4 currently, it changes with time). NWN2 is laggy, but that's because the graphics engine is so bad it even overloaded my then-current 6800GT...

If you run into problems with Wine, check out the [wine subforum]("http://ubuntuforums.org/forumdisplay.php?f=313") and ask there. If its nothing to do with Wine someone will tell you and you can go to the correct sub-forum. So far I haven't encountered an issue that couldn't be solved/workaround between google and ubuntuforums.

---

### Post by Serrya on 2009-01-23
Yes I am sure, this current system has an ATI Radeon Xpress something odd (1100 i think)

The specs were for my new system I will be getting on friday. I was basically asking because I know that ATI cards have issues with Linux, and  most games I play on Wine are Plat or Gold, which makes me wonder if it was messing up because of my ATI card or if it was my 64 bit linux? (since I heard Wine doesn't like 64 bit) 


It may be have to be get the new comp and try :/ but I wanted to know in advanced. 

Oh, on the note on Wine and Tales of Pirates, when I turn down my "visul effects" the game DOES load, and I do "get it" though its impossible to play (like super lags-a-lot to the point of no movement) but when the effect are at "Extra" that is when my games no longer work.

---

### Post by jespdj on 2009-01-23
Oh, sorry, I didn't read it properly.

Anyway, you will probably have less problems with your new laptop with nVidia card than with an ATI card.

WINE works normally on 64-bit systems. It's hard to say why something won't work. There's a good chance the Windows program isn't fully supported by WINE (remember that the developers who create WINE don't have access to the source code of Windows, they have to reverse engineer it and guess how the Windows API functions are supposed to be implemented).

Since ATI has a bad reputation with regards to their Linux drivers, there's also a chance that the ATI driver doesn't fully support the graphics that your 3D game needs.

Both those things are more likely than that the problem is caused by running on a 64-bit system. People often blame vague problems on the fact that they're running a 64-bit system, while there is really no reason at all to believe that that has anything to do with the problem.

---

### Post by purepout on 2009-01-26
Hello guys,
I have got exactly the same problem as Serrya, and I was googling and found that some people could do something with the result from loading it from terminal. I have got the result here:

> fixme:win:EnumDisplayDevicesW ((null),0,0x32eb54,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13b9e8) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x13b9e8) Dialogs cannot be disabled yet
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x27a08a0,0x27a0800): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1633318,0x27a0800): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1633318,0x27a0800): stub
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22


I'm no ubuntu expert, so maybe someone can help me (or us) with this problem.

purepout

---

### Post by Kilz on 2009-01-26
> **jespdj said:**
> Oh, sorry, I didn't read it properly.

Anyway, you will probably have less problems with your new laptop with nVidia card than with an ATI card.



I dont know about that. Since AMD bought ATI the release of drivers is very predictable. The major rewrite of the driver last year did momentarily cause some disruptions for a month or two. But the drivers we have now are improved over what was before it.
AMD also released a lot off the specifications to their Ati cards. This to me says, in a short amount of time open drivers will be available.

---

