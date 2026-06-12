---
title: "[SOLVED] Unable to install, Phenom 9500"
date: 2008-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cullen on 2008-03-06
Just got a brand new machine for myself, I was stoked to load up Ubuntu x64 and see it rock on along, but my hopes were dashed and I'm clueless what to do.

Specs:
Asus M2N-SLI Motherboard (Utilizing on-board audio, and on board nic, one sata HDD, one IDE HDD (slave), and a IDE DVD/CD Burner)

Hitachi Sata 500gb 7200

Two Nvidia 8600GT in SLI

Acer AL2216W LCD

2 GB OCZ ram

and a partridge in a freakin pear tree.

Put in the live cd turn on the machine, it boots to the intial selection screen. I select boot from cd, I get a little bit of text scrolling past, then just goes to a blinking cursor in the upper corner, then my monitor stops receiving a signal, however I never hear the Ubuntu drums, so I don't think it's purely a video issue.

Tried the alternate CD, runs through the install beautifully (I even garnered a little hope for my system there) and then pretty much the exact response as the live CD, only faster.....

Any thoughts?  Any ideas? Have I missed, or overlooked something essential? I really don't wanna switch back to windoze, and I'm not too familiar with other distros, I was finally starting to feel comfortable in this distro....

Help if you can, thanks in advance....

---

### Post by damvcoool on 2008-03-06
any Bios setting that you can modify to increase stability? what if you try with single card.

i know is not a video issue but could be having issues detecting SLI.

---

### Post by Cullen on 2008-03-06
I tried the install on the live cd with only one card and didn't have any luck.  I honestly didn't try the alternate cd install with one card.

---

### Post by talcite on 2008-03-06
This sounds like an Xorg problem to me. Have you checked your xorg.conf settings over? Also, what vid driver are you using? SLI won't work nicely without the nvidia drivers.

---

### Post by mad_max0204 on 2008-03-07
I'll try and help you. When u get into boot menu edit boot parameters and delete splash and then boot.

---

### Post by Cullen on 2008-03-07
> This sounds like an Xorg problem to me. Have you checked your xorg.conf settings over? Also, what vid driver are you using? SLI won't work nicely without the nvidia drivers.

Once the machine "boots" and I have the blinking cursor in the upper left hand of the screen it is unresponsive, pressing crtl-alt F1, F2, F3 does nothing, therefore if the issue is with the xorg, I can't fix it.

> I'll try and help you. When u get into boot menu edit boot parameters and delete splash and then boot.

I will try this ASAP and let you know the results.

---

### Post by bb002 on 2008-03-07
Seems that Xorg is picky about your wide-screen LCD monitor, too.

Xorg gets the resolutions correct but doesn't get the proper refresh rates and i have to add them to the xorg.conf file by hand. If I don't everything boots up just fine but my monitor goes blank except for "Signal out of sync" bouncing around the screen.


I looked around for your monitor specs. I found the refresh rates on the french version of the page (dunno why but manufacturers are incapable of putting full specs of any product on the US English pages) [http://www.acer.fr/public/page9.do?sp=page4&dau34.oid=19161&UserCtxParam=0&GroupCtxParam=0&dctx1=8&CountryISOCtxParam=FR&LanguageISOCtxParam=fr&ctx3=-1&ctx4=France&crc=81774165](http://www.acer.fr/public/page9.do?sp=page4&dau34.oid=19161&UserCtxParam=0&GroupCtxParam=0&dctx1=8&CountryISOCtxParam=FR&LanguageISOCtxParam=fr&ctx3=-1&ctx4=France&crc=81774165)

What we are looking for is the refresh rates. they turn into these two lines when formated for the xorg config.```

HorizSync "30-82"
VertRefresh "56-76"

```


Now the monitor section of /etc/X11/xorg.conf file needs to be updated with these two lines.
Most likely if your monitor is as picky as mine the Ubuntu boot splash doesn't even show up during the boot process and you will have to remove the splash references in the /boot/grub/menu.lst file. Meaning a blank monitor or a flashing cursor in the top left after the grub menu vanishes. This also means that the virtual consoles on Ctrl+alt and f1 thru f6 are just blank screen.


I'd help you replace those lines but that requires root access and with me being inactive for quite some; I'd rather learn more about this "Malicious Commands" announcement before i go posting too much. I'd rather not get a permanent ban because I posted something, while not malicious, it was against a new guild line.

---

### Post by mad_max0204 on 2008-03-07
Maybe hes done it since he didnt post back :D

---

### Post by Cullen on 2008-03-15
No I'm not done, and sorry for the length of time since my last post, I was out of town (therefore away from my Desktop) all of last week.

The removing of the splash doesn't shed any additional light on the subject, basically the same exact response.

I understand the how to edit the xorg but if I am unable to boot into a working linux environment, how am I to pull that off?

---

### Post by Cullen on 2008-03-31
Ok

I booted into recovery mode and edited the xorg to reflect the appropriate referesh rates

Downloaded Hardy and tried it with that, still nothing.

Can anyone tell me how to install the NVIDIA Drivers from bash?

Any ideas?

---

### Post by rajeev1204 on 2008-03-31
I suggest you remove one graphics card , and after installing OS and nvidia driver only try SLI again,



regards

rajeev

---

### Post by bailbath on 2008-03-31
Hi I had similar problems with gutsy on a wide screen laptop used text install then after it boots press esc to get to get to grub menu then used rescue option to get to a command line then sudo dpkg-reconfigure xserver-xorg. I think the solution will be on the last question it asked you either go for simple mode and choose the correct size or if you know the refresh rate use the other options.
Incidently I also have a sli setup with a asus board but with dual core intel I used hardy alpha5 and had no problems.I think it will be down to the monitor detection. On the widescreen laptop out of interest I don't get the same problem with any KDE distro!
IAN

---

### Post by WeeWoh on 2008-03-31
I dont know a lot about ubuntu but i had a similar problem with a 5 year old computer that was running a 1.2GHz celeron. My laptop (a dell vostro 1000 with an ATI Radion Express X1500 or something) wont boot into kubuntu 64 bit normally. I have to select start in safe graphics mode. Have u tried that?

---

### Post by Cullen on 2008-04-16
So I don't know what changed, but it is working now.

The other night I was getting ready for bed, told the computer to reboot and left the room.  When  I walked back by the Ubuntu login screen was waiting for me.  I rebooted again, and it came right up to it.  

So to recap, it is working after adjusting my xorg.conf files, and with both video cards still installed in the machine.

---

