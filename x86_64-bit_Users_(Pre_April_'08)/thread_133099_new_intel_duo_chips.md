---
title: "new intel duo chips"
date: 2006-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by oldmanstan on 2006-02-19
I was wondering what the implications are of Apple switching to the intel chip are as far as ubuntu.  I would assume you can't install from the PPC cd image since it's a different chip, but will the x86 one work?  Or are they going to have to come up with a new version?  Also... could you still install from sources?

Thanks!

---

### Post by Ribs on 2006-02-19
The x86 install does not work... yet. This is due to Apple not using a BIOS, but using something else (I forget the name now).

Redhat have already said they will work hard to get their distro working on the new intel macs, and Apple have not made any effort to stop other operating systems being installed (just to stop MacOS being installed elsewhere). So it's only a matter of time.

---

### Post by Ptero-4 on 2006-02-20
Apple use a firmware called EFI. And there's elilo being developped. All that is needed is to add elilo to the x86 CD's and make it capable of recognizing wheter the computer is using a BIOS or EFI and load through grub or elilo depending on the check results.
Now about implications I can tell you something. Intel is planning to put a TPM embedded into their processors and the new Intel Macs will obviously be as screwed as the el-cheapo PC box that the local drug store sells when that plan takes effect.

---

### Post by oldmanstan on 2006-02-20
Call me ignorant but what is a TPM?

---

### Post by Tipo on 2006-02-20
Can two people be ignorant? I have no Idea either:p

---

### Post by jdp on 2006-02-22
Sometime a [quick Google search](http://www.google.com/search?rls=en-us&q=intel+tpm&spell=1) will tell you alot. ;)

---

### Post by adam.tropics on 2006-02-22
Similar thought, with Apple I think previously having had far better video drivers than linux, and with now Apple's OS being vaguely linux based, as well as  using the same video hardware as other laptops (since the Duo processor switch).....A bit confusing, but would the implication be that the Duo change will ultimately kickstart better drivers from the likes of ATI????

---

### Post by jdp on 2006-02-22
Apple has used ATI and nVidia chips for the better part of a decade.  Now, there might be an easier way to use binary-only drivers, but there hasn't been a problem with the particualr chips used.  If ATI wasn't playing hard-to-get with the source, we'd have fast video for many Macs.

---

### Post by adam.tropics on 2006-02-22
Ah I see. I kind of presumed that whilst I knew they used ATI and Nvidea, that because the systems were not intel based, the video cards/chips, whilst manufactured by the same companies as many pc video cards, would be totally different. Therefore that there might be a compatibility 'knock on effect' when some of the compatibility issues were addressed (by for example the intel switch. ATI in particular seem to have always been more cooperative with Apple then Linux, and I thought that if this meant the cards could now be more or less the same, and with Apple being linux 'inspired'( ! ) , that ATI would in effect unwittingly have to improve the chip support for Linux in order to continue their Apple support.

I hope that makes some kind of sense. The more I write about it, the more confusing it sounds!!

---

### Post by jdp on 2006-02-22
The reason cards aren't compatible between Mac and PCs are the ROMs on the card, not the video chips.  The Mac cards need ROMs that can work with Open Firmware, while PCs need ROMs that can work with a BIOS.  Both need to work until the OS boots far enough to load better drivers for faster 2D and 3D support from the HDD.  With a bit of hacking you can reflash the firmware of certain PC video cards, such as the Radeon 7000, to work on a Mac.

---

### Post by Ptero-4 on 2006-02-23
Hi, oldmanstan & Tipo. TPM means "Trusted Platform Module" and it's the key hardware piece in the TCPA ("Trusted computing platform alliance"). The TCPA is a set of hardware modules and specs which makes it easy for the big and greedy megacorps (read: **M$**, **MPAA**, **RIAA**, **Sony**, **Disney**, **etc**) to control and decide what **you** can do on **YOUR** computer including **which OS and applications you are allowed to install and use on it**.

For a better description of TCPA and it's dangers go to:
[http://www.gnu.org/philosophy/can-you-trust.html](http://www.gnu.org/philosophy/can-you-trust.html)

They got a very detailed explanation of the TPM and TCPA issues.

---

### Post by oldmanstan on 2006-02-23
thanks for the response, actually i did a google search after i posted and found some info. completely alarming how "1984"ish the "content" companies are trying to make the internet. for a device that does absolutely nothing but add and subtract 1s and 0s companies certainly are control freaks about computers.

i wonder how long it will be before i can patent the fact that 1+1=2 and license it to elementary schools to teach...

---

### Post by Ptero-4 on 2006-02-24
And the scariest part is that it has already begun and it's attacks on OSS are already visible like my experience with that hellish Pavilion which killed itself when I tried to install ubuntu on it b/c it's programmed to disallow installing non-M$ OS's, but it doesn't end there, M$ through social enginnering and preference manipulation using subliminal adverts has gotten as far as causing people to think that the desktop GUI "MUST" be Windoze-like to be good, and this tactics have succesfully reached into the gnome and xfce development communities, M$ tried to reach the KDE guys and where almost succesfull but failed by just inches.

---

### Post by adam.tropics on 2006-02-24
don't hold your breath, I fear they have not quite failed with kde. It's still headed in that direction...In many ways I think so is Gnome, but I guess only time will tell......

---

### Post by oldmanstan on 2006-02-25
in what ways are gnome and kde moving toward windows? i mean obviously the whole concept of applications running in frames is all ripped off from old xerox and mac concepts and windows is the biggest of the ripoffs. but still, window managers for unix have been around for a long time so i would hardly say that the gui is a windows concept.

besides that the underlying OS is still gnu/linux so i don't see how they are moving toward being like windows... explain?

---

### Post by Ptero-4 on 2006-02-25
oldmanstan. What I mean is that gnome (and possibly KDE too) tries to make their desktops look **only** like Windoze and to **not** provide users the ability to make the desktop Mac, NeXT or Amiga-like. gnome does this by making their panel only be placeable alongside a screen edge (no short corner panels possible, I tried and you can place them but they don't remember their placement across sessions), placing the menubar inside the window like in windoze and **proactivelly refusing to put the option to place the menubar in a special applet using stupod excuses to say they can't**. KDE initially had kinda the same attitude but they're improving and they at least doesn't cut off the features that allow the user to mold KDE to become a MacOS clone.The gnome ppl currently want you to have a taskbar, a menubar within each app window and no control strip bar to make the desktop look like if you took a screenshot of a Windoze95 box.

Ups I forgot to say. I know that it's linux, I just don't want my desktop to be a f*kin screenshot of Win95, I want it to be a clone of OS9, but I guess that probly it's impossible now that M$ has said that OS9 look is ungood and Win95 look is good and those how like the OS9 look are thought-criminals.

---

### Post by aeiah on 2006-02-25
[QUOTE=Ptero-4]oldmanstan. What I mean is that gnome (and possibly KDE too) tries to make their desktops look **only** like Windoze and to **not** provide users the ability to make the desktop Mac, NeXT or Amiga-like. gnome does this by making their panel only be placeable alongside a screen edge (no short corner panels possible, I tried and you can place them but they don't remember their placement across sessions), placing the menubar inside the window like in windoze and **proactivelly refusing to put the option to place the menubar in a special applet using stupod excuses to say they can't**. KDE initially had kinda the same attitude but they're improving and they at least doesn't cut off the features that allow the user to mold KDE to become a MacOS clone.The gnome ppl currently want you to have a taskbar, a menubar within each app window and no control strip bar to make the desktop look like if you took a screenshot of a Windoze95 box.

Ups I forgot to say. I know that it's linux, I just don't want my desktop to be a f*kin screenshot of Win95, I want it to be a clone of OS9, but I guess that probly it's impossible now that M$ has said that OS9 look is ungood and Win95 look is good and those how like the OS9 look are thought-criminals.[/QUOTE]

what?

---

### Post by ssam on 2006-03-06
good news on this front from todays dapper changes

> linux-source-2.6.15 (2.6.15-17.25)
Changes by Ben Collins
Enable EFI for x86 (MacBook Pro, come hither).

i imagine that there is a lot of work still to do, like the boot loader, maybe changes in the partitioner etc.

---

### Post by oldmanstan on 2006-03-07
[QUOTE=ssam]good news on this front from todays dapper changes



i imagine that there is a lot of work still to do, like the boot loader, maybe changes in the partitioner etc.[/QUOTE]

EXCELLENT!  I really love the apple laptops, they are so clean and easy to carry.  i think pc laptop designers are all wannabe modern artists, the things are so oddly shaped that they are hard to carry and easier to break.

---

### Post by Christiaan on 2006-03-10
[QUOTE=Ptero-4]Intel is planning to put a TPM embedded into their processors and the new Intel Macs will obviously be as screwed as the el-cheapo PC box that the local drug store sells when that plan takes effect.[/QUOTE]

Hi Ptero, would you care to offer evidence of this? I've just purchased a new iMac and I'm pretty sure there are no implications involved in putting Linux on it other than support for EFI.

---

### Post by phico on 2006-03-10
Good news : [http://www.mactel-linux.org/wiki/HOWTO](http://www.mactel-linux.org/wiki/HOWTO)

---

