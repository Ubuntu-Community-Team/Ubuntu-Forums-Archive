---
title: "Upgrading AMD 64 to Opteron"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2007-06-14
I am running an AMD FX-55 based system dual booting XP and Feisty 64.  I am considering changing the CPU to AMD Operton 180.  The machine was custom built by me around a DFI nF4 Lanparty motherboard and the exising bios will support this processor.    I have a pretty good idea of the steps I will have to take to upgrade XP without reinstalling the OS from scratch but am not clear what the impact on my existing Feisty installation will be.  I am also considering changing the video card to a BFG 7950.  

Anyone have any experience good or bad with this type of upgrade?  I searched the website for a how-to.  Is there on that addresses hardware upgrades specifically the AMD 64 environments?

Thanks,
joe

---

### Post by John.Michael.Kane on 2007-06-14
It should have no effect on your feisty install. I did the same thing moving from a 3000+ to a opteron148 without issue.

If your current video card is nvidia base the drivers under linux should see the new card, and apply the proper settings. if anything you may have to run dpkg-reconfigure to get xorg to see the video card, and you may need to re apply the drivers note this is highly unlike but may be needed.

If however your moving from say an ati card then you should uninstall those drivers first shutdown the machine install your nvidia card, and apply the drivers ect.

Hope this helps.

---

### Post by darknightuk on 2007-06-14
i wouldn't necessarily be in so much of a rush to upgrade u might find the new cpu to be somewhat of a down grade speedwise in day to day stuff, unless that is you have a specific reason to go 64bit?/

---

### Post by John.Michael.Kane on 2007-06-14
> **darknightuk said:**
> i wouldn't necessarily be in so much of a rush to upgrade u might find the new cpu to be somewhat of a down grade speedwise in day to day stuff, unless that is you have a specific reason to go 64bit?/

Looking at the specs of the FX55 it's a single core model while the opteron180 is dual core. While he may be giving up some speed it can be regained though overclocking so he is not giving up much, and is gaining an extra core.

---

### Post by darknightuk on 2007-06-14
> **SD-Plissken said:**
> Looking at the specs of the FX55 it's a single core model while the opteron180 is dual core. While he may be giving up some speed it can be regained though overclocking so he is not giving up much, and is gaining an extra core.ofc he could o/c if he wanted to and knew how, do u not think dual core would b slower in day2day suff less ur hammering it rendering compiles etc?

---

### Post by John.Michael.Kane on 2007-06-14
> **darknightuk said:**
> ofc he could o/c if he wanted to and knew how, do u not think dual core would b slower in day2day suff less ur hammering it rendering compiles etc?

Personally I don't feel it would be slower, however without knowing what the machine is being used for it will be very unwise to tell someone they are gaining or losing performance.

On top of that theres many reasons to go to dual core.  One thing can be said running dual core would allow him some flexibility with what he can do.

in the end It's a tool box you put the tool into the job. The OP feels dual core is needed for the job.

---

### Post by j0eb0b on 2007-06-14
The Fx-55 rig like all of my equipment, is overclocked.  I have a k7 based machine my wife uses that needs some attention and I was considering recycling the fx-55 into her machine along with the BFG 7600 GT video card  currently in my Feisty machine.  The BFG 7600/7950 are both nVidia chipsets.  I have been under the impression (maybe mistakenly) that Ubuntu (Linux) has problems with nVidia 8xxx cards due to Direct X 10 (Vista) and I wanted to make sure that the 7950 is not problematic.

I know I will have jump through some hoops with Windows.  If i swap the Opteron into my existing working Feisty 64 system, is it likely to boot out of the box (forget about video change initially).

Thanks,
joe

---

### Post by John.Michael.Kane on 2007-06-14
After the cpu swap it should boot with out issue.

As for the 7950 you may want to use the "nvidia-glx new" it should be listed in the feisty repos.

---

### Post by j0eb0b on 2007-08-02
FYI,

I popped in the BFG 7950 GT last night and it works without issue with the Feisty nVidia driver.  Should I still install the new nVidia driver via Synaptic?

Joe

---

### Post by John.Michael.Kane on 2007-08-02
> **j0eb0b said:**
> FYI,

I popped in the BFG 7950 GT last night and it works without issue with the Feisty nVidia driver.  Should I still install the new nVidia driver via Synaptic?

Joe

You can use the nvidia driver labeled nvidia-glx-new if you want,however. unless theres a major problem using the current driver I would leave the setup as is.

---

