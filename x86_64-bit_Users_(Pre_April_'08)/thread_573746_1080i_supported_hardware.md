---
title: "1080i supported hardware?"
date: 2007-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by CranKey on 2007-10-11
Hi all.
Recently I built an HTPC that is based on the abit AN-M2HD motherboard.  I've installed the 64bit version of Ubuntu and it seems to work OK for the most part.  What is very limiting at this point though is even basic graphics support.

I've installed the Nvidia drivers on the machine, hoping to be able to work with the video chipset on the the MB.  In fact, one of the reasons that I selected this MB is because Nvidia seemed to have driver support for Linux.  Unfortunately, my 32" Panasonic TV works at 1080i and while the drivers seem to do that resolution, they don't seem to do it very well.  I've chased this around through the nvnews forums and almost anywhere else that I can think of and the end result seems to be that Nvidia drivers don't do interlaced modes very well at all.

So, my question is as follows.

What PCIe graphics card will give me the support that I need at this point in time?  I want to be able to display 1080i solidly.  Because of the problems that I'm having I assume that it won't be an Nvidia card, so it would likely be ATI or someone else (does Matrox still play a role here?  I had a G400 on Linux when they came out and it worked really well.).

Does anyone have any good recommendations that aren't based on conjecture but rather on experience?  In the end I'll be laying out cash for a new card so I'd like to be getting something that I know will work.  I've already been down the "it should work' path with my present setup.

Thanks for the help.

---

### Post by bmilleker on 2007-10-12
I actually just ordered the same mobo and plan on running it at 1080i as well. There has to be a setup for xorg that will give the desired results.

You don't have much of a choice with video card and linux. I wouldn't get anything other than nvidia, so really is a new card even going to help?

Have you had any other problems with the board? Did you install the latest driver from the nvidia website, or from the ubuntu repositories? This is a new board and the newest drivers will probably have to be manually installed. Are you using HDMI out, or VGA?

---

### Post by CranKey on 2007-10-12
I haven't had any problems with the board at all, at least so far as I've gotten.  There are a number of things I'd like to get working on with the machine but the poor video is holding me back from doing a lot on it.  The basic install went well, and I've installed the latest drivers from Nvidia's website, outputting over the HDMI out with no additional configuration required..  USB and firewire seem to be working with no extra configuration.  I have an external HD connected and it never seems to power down, but I don't know if that is a mobo issue or just a power management setting.  I would pursue it further but the video is highest priority because if I have to put up with the shaky screen much longer I think it will give me a seizure.

I've messed around with the xorg.conf file quite a bit and tried a number of modelines, but to no avail.  At present I think I'd like to run at 960x540 on the backend so that everything is twice the size because I sit back on the sofa.  I'm open to trying other resolutions if anyone has some suggestions.  1920x1080i works, but it jumps around a lot which makes it very difficult to read when combined with the small size.  My current setting of 960x540 jumps around just as much but it's bigger so at least I can sort of use it.  The initial setting that it had was 740p or something.  It was nice and stable but rather square compared to my screen, so not so nice that way.

One other item that I should mention.  The machine overscans so I can't see outside edge of the screen.  This seems to be the case in all resolutions, except when I was in 740 I could see the sides but the top and bottom seemed to be even further to the outside.

---

### Post by bmilleker on 2007-10-12
The motherboard sounds pro, but the video problems sound awful. I am really disappointed that the new nvidia drivers still don't fix this, because the problem seems to have been known for quite some time now.

Ugg, i think i may be running windows till this problem is fixed.. unless there is a stable solution. I am in no way putting up with shaking video. My buddy is running 1080i in windows and says its beautiful, there is no reason why Linux shouldn't be the same :(.

Just out of curiosity, what bios version for the motherboard and what TV are your using?

---

### Post by CranKey on 2007-10-13
A refinement to my earlier post.  With the exception of overscan, the video displays solidly at the default 720x480 resolution.  Unfortunately this does not match the widescreen aspect ratio.  But it has a nice solid image and things are a size that I could live with, although I might want to tweak some things a bit.  When I say default I mean this is what comes up when using the xorg.conf file and the 'nvidia' driver from Nvidia's website, not the 'nv' driver.

I should also note that the shaking video at 1080i also occurs on 64 bit XP, so it's not really a Linux problem.  Perhaps if I could fix the overscan first then I could run in 720 mode until things got fixed on the 1080i mode.  Nvidia does seem to mislead people when they advertise this chipset as being able to do 1080i.  Technically I guess you could say that it does display it, but not in a usable manner.  It was because of the chipset that I decided on purchasing this board (abit AN-M2HD).

Does anyone know how to reduce the scanned area?  It would be nice to see the task bars and the edges of the screen too.  I've been thinking that it might be useful to start a thread that is dedicated to this chipset, as it is rather new so it would be nice to have a lot of information about it in one place.

The TV is a Panasonic CT-34WX54J and I'm using the HDMI output on the mobo and the HDMI input on the TV.  If someone can get me some pixel specs for this machine I would appreciate it.  I have messed around with the xorg.conf file a fair bit but didn't have any tech info on the TV and nothing more detailed than the owners manual seems to be on the Panasonic website.

By the way, pardon any spelling errors.  I sitting across the room while I'm typing so everything isn't quite as clear as it would be if I was sitting at my desk.

---

### Post by bmilleker on 2007-10-14
I have been reading around and I saw something mentioning that the resolution will be correct if you use VGA output (I don't have the website, so don't quote me on this). The buddy I mention above is using an Abit F-I90HD, which has on board ATI video processor so I guess he wouldn't have any of these issues.

Isn't the nvidia driver supposed to be able to fix overscan?

I am disappointed that even the Windows driver has this problem. Going the windows option was my last resort, but now there is no need. Thanks for the info!

Is it possible to output in 1080p, and then let the TV scale it to 1080i? This would be more intense on the on board graphics, but If it fixes the problem then It might even be worth it.

I have an LG 42LC7D, and my HTPC should be put together early next week so I will post how my situation is handled.

Check this forum post out. It explains why there is overscan. [http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=2007&p_created=1168038608&p_sid=xGPP98Oi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NiZwX3Byb2RzPTAmcF9jYXRzPTAmcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PTEwODBp&p_li=&p_topview=1](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=2007&p_created=1168038608&p_sid=xGPP98Oi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NiZwX3Byb2RzPTAmcF9jYXRzPTAmcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PTEwODBp&p_li=&p_topview=1)

---

### Post by bmilleker on 2007-10-18
I built my HTPC this week. Very easy except for I am using Gutsy and there is no HDMI audio and I cant seem to get LIRC working. Only problem I had with the install was having to use the VESA driver for graphics, not a big deal.

I connected it to my LCD last night and had big overscan issues in the HDMI2 slot on my TV. On my TV, when there is a computer attached you can adjust the position, width, and height of the screen, so this could have been fixed, but the max resolution was only 1280x720 (I did a lot of editing to try and adjust that as well). I also have a HDMI/DVI port which is meant for use with a PC connection. I used that instead of HDMI2 and I get an amazing picture. No jumpy video (which I never had even in HDMI2), 1360x768 resolution, and zero overscan. 1080p looks incredible on it.

For anyone having trouble with overscan, or resolution I would suggest trying out the different HDMI ports on the back of your TV, and if you only have one HDMI, then I am not sure what the next step is.

I am very happy with this motherboard and onboard graphics. 1080p runs smooth and what more could I ask for :).

---

### Post by hxall on 2007-10-18
bmilleker,

would you mind posting the specs for your HTPC (including case), reasons for chosing that motherboard, etc

Thx.

---

### Post by bmilleker on 2007-10-18
> **hxall said:**
> bmilleker,

would you mind posting the specs for your HTPC (including case), reasons for chosing that motherboard, etc

Thx.

[LIST]
[*] Linksys WMP54G Wireless PCI 802.11G
[*] Hauppauge Win TV PVR 500 Dual TV Tuner 
[*] Abit AN-M2HD NF630A GeForce 7050PV mATX AM2
[*] G.SKILL F2-6400CL5D-2GBNQ PC2-6400 2GB 2X1GB DDR2-800
[*] Seagate Barracuda 7200.10 500GB SATA2 3GB/S 7200RPM 16MB Cache
[*] AMD Athlon 64 X2 4400+ Dual Core Processor Socket AM2 Brisbane 2.3GHZ
[*] Microsoft 3-IN-1 MCE Wireless IR Keyboard
[*] LG GSA-H62N SATA DVD+RW 18X8X16 DVD-RW 18X6X16 DL 10X
[*] USB-UIRT 
[*] Nmedia 400BA case with 400w power supploy
[*] 6ft hdmi cable
[/LIST]

I was either going to get the Biostar 7050pv, or the Abit 7050pv. I went with Abit because of the better name, bundled with a lot of extras (cables, etc..) and more than one motherboard fan control input.  I wanted either of those boards because they have the latest onboard GPU from Nvidia, hdmi out, mATX form factor, and probably some other reason i cant recall.

Everything else is pretty standard for a normal computer build.

HDMI audio out is broken in Gutsy and the last stable release of Feisty, so that and LIRC not working are my only problems so far. This board plays 1080p very smooth. I was worried I would need to get a better video card, but there isn't any point now.

---

### Post by hxall on 2007-10-18
thanks for the very detailed info, too bad HDMI audio is not currently working...

---

### Post by bmilleker on 2007-10-18
Just an FYI.... if you look at the changelog for kernel 2.6.23 ([http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.23-git13.log](http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.23-git13.log)) it looks as though they made some improvements to ALC883, which is what I think the abit mobo uses.

> 
commit 11370ee2c1c578a704f47d5513d57274c335db43
Author: Tobin Davis <tdavis@dsl-only.net>
Date:   Mon Sep 17 12:46:12 2007 +0200

    [ALSA] hda-codec: Add two new systems to ALC883
    
    This patch adds support for the Asus M2A-VM HDMI and Abit IP35-PRO
    motherboards.
    
    Signed-off-by: Tobin Davis <tdavis@dsl-only.net>
    Signed-off-by: Takashi Iwai <tiwai@suse.de>
    Signed-off-by: Jaroslav Kysela <perex@suse.cz>


---

### Post by CranKey on 2007-10-19
It sounds like you're using 1080p?
My TV won't do 1080p, only 1080i, so I'm not sure I can get your results as the problems with the Nvidia driver seem to be with interlaced modes.  At least that's what I got off of nvnews.
I only have a single HDMI port on my TV so my next move was to try a component connection.
I haven't been able to put audio over HDMI either, but I use the analog audio input on my TV and that works OK.  Of course, I'd rather be using the fully digital HDMI audio connection.

---

### Post by bmilleker on 2007-10-19
> **CranKey said:**
> It sounds like you're using 1080p?
My TV won't do 1080p, only 1080i, so I'm not sure I can get your results as the problems with the Nvidia driver seem to be with interlaced modes.  At least that's what I got off of nvnews.
I only have a single HDMI port on my TV so my next move was to try a component connection.
I haven't been able to put audio over HDMI either, but I use the analog audio input on my TV and that works OK.  Of course, I'd rather be using the fully digital HDMI audio connection.

My tv is only 1080i. I get 1360x768, which is my TVs native resolution. No idea how it works, but it works well.

How are you using audio in? My tv has it, but it requires a weird input (i dont know what it is).

---

### Post by notz on 2007-10-25
> **bmilleker said:**
> Just an FYI.... if you look at the changelog for kernel 2.6.23 ([http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.23-git13.log](http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.23-git13.log)) it looks as though they made some improvements to ALC883, which is what I think the abit mobo uses.

can anyone verify if it is a ALC883 chip on board? because on most of the MCP67 based boards there is a ALC888 onboard and also most of the shops around are saying that there is a ALC888 on board.

there seams not so much diffrent between these to chips, because most code of the driver is shared between those chips.

so i think the card is wrong detected from bios and there need be somthing added to "patch_realtek.c" like lenovo MS7195 to get digital output working.

---

### Post by notz on 2007-10-25
so the card is detected as ALC888

```

root@hollywood:~# cat /proc/asound/card0/codec#0
Codec: Realtek ALC888

```

```

root@hollywood:~# aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

im currently not at the box, but tried anyone to use the 2. device?

---

