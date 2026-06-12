---
title: "[SOLVED] ATI R600/RV6xx (HD 2400 to 3870) intrepid 64 compiz flash video tear flicker"
date: 2008-11-21
forum: x86 64-bit Users
---

### Post by yct on 2008-11-21
Please stay strictly on topic in this thread and don't report/solve problems for Intel or NVidia graphics cards.

I really tried to search all around but there seems to be no fully working workaround for this.


Known incomplete workarounds:

- turn off compiz  (not a preferred solution)

- turn off compiz when watching Flash videos or movies (inconvenient)

- use X11 video output  (doesn't fix it for Flash videos)

- tell compiz to not use redirection for fullscreen windows  (doesn't fix it for Flash videos, ugly until you fullscreen a movie)

- use RadeonHD driver  (doesn't have proper 3D support yet)



If you know something not listed here please add it. Recompilation, patching, anything.


Thanks!

---

### Post by yct on 2008-11-21
Ok, adding the following to the Device section in the xorg.conf solved 
the flickering:

```

        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "on"
        Option      "TexturedVideo" "off"

```

HD videos in Compiz are not as fluent as without Compiz, and MPlayer doesn't stretch video in fullscreen but I think these are issues for new threads.

Vertical scrolling in Firefox is still sluggish, but with videos working it's bearable.

---

### Post by Enmi on 2008-12-22
> **yct said:**
> Ok, adding the following to the Device section in the xorg.conf solved 
the flickering:

```

        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "on"
        Option      "TexturedVideo" "off"

```

HD videos in Compiz are not as fluent as without Compiz, and MPlayer doesn't stretch video in fullscreen but I think these are issues for new threads.

Vertical scrolling in Firefox is still sluggish, but with videos working it's bearable.
This was the first and only fix that has worked since Intrepid's ATI drivers! ... Well, besides disabling compiz altogether. >.> 

Thank you! As far as vertical scrolling is concerned... it's a just a bit sluggish, but that's been like that since I upgraded to Intrepid. It's faster in every other browser though... hmmn. Anywho, thanks!

---

### Post by alfredska on 2009-03-30
Sorry to dig up an old thread, but I found this when I was trying to solve my video flickering problem with an ATI HD3200 under Ubuntu 8.10 w/ Compiz enabled.

Another solution has presented itself in the release of [ATI Catalyst 9.3]("http://support.amd.com/us/gpudownload/Pages/index.aspx").  Installation of the driver is pretty self explanatory, but a short howto is [here]("http://ubuntuforums.org/showthread.php?t=1109768"). (Remember to uninstall your old proprietary ATI driver if you're using one!)

A quick demo of the improved compositing is at [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=amd_catalyst93_composite&num=1").  I'm using the driver now and am very pleased.

---

### Post by asuastrophysics on 2009-05-03
> **alfredska said:**
> Sorry to dig up an old thread, but I found this when I was trying to solve my video flickering problem with an ATI HD3200 under Ubuntu 8.10 w/ Compiz enabled.

Another solution has presented itself in the release of [ATI Catalyst 9.3]("http://support.amd.com/us/gpudownload/Pages/index.aspx").  Installation of the driver is pretty self explanatory, but a short howto is [here]("http://ubuntuforums.org/showthread.php?t=1109768"). (Remember to uninstall your old proprietary ATI driver if you're using one!)

A quick demo of the improved compositing is at [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=amd_catalyst93_composite&num=1").  I'm using the driver now and am very pleased.
**EDIT**-> I didn't see that you had gotten this from an earlier thread, sorry ;)

This isn't exactly a workaround if you've upgraded to Jaunty. 
Your how-to is only for 8.10 and below.
Are there any other solutions for those of use who made the mistake of upgrading to Jaunty? Compiz hasn't been working since I upgraded 2 months ago and it's getting really old. 

ATI Radeon 2400 HD + Ubuntu 9.04 = No compiz and almost unusable under metacity.

Has anyone filed a bug report for this? Even the Catalyst 9.4 drivers don't work. I do not believe the above card was dropped from support.
(I bought it 4 months ago)
What is the deal here? How long am I going to be stuck with Metacity?

---

### Post by nasrat on 2009-05-05
> **asuastrophysics said:**
> 

ATI Radeon 2400 HD + Ubuntu 9.04 = No compiz and almost unusable under metacity.


I am using KDE4.2 and Kwin, just bought a Radeon HD 2400 card, and thinking of returning it. I am getting serios video corruption using the "radeon" driver in KDE and cannot see the cursor. All other drivers "radeonhd", "fglrx" blank my screen and cause serious pain by not giving me access to my machine. Does anybody here have a solution to this problem? :(:confused::(:confused::(:confused::(

---

### Post by shabazzk on 2009-05-06
> **asuastrophysics said:**
> **EDIT**-> I didn't see that you had gotten this from an earlier thread, sorry ;)

This isn't exactly a workaround if you've upgraded to Jaunty. 
Your how-to is only for 8.10 and below.
Are there any other solutions for those of use who made the mistake of upgrading to Jaunty? Compiz hasn't been working since I upgraded 2 months ago and it's getting really old. 

ATI Radeon 2400 HD + Ubuntu 9.04 = No compiz and almost unusable under metacity.

Has anyone filed a bug report for this? Even the Catalyst 9.4 drivers don't work. I do not believe the above card was dropped from support.
(I bought it 4 months ago)
What is the deal here? How long am I going to be stuck with Metacity?

1. Uninstall ATi drivers
2. Uninstall flash if it is NOT the native 64bit driver from Adobe labs.
3. Install MANUALLY ATi drivers from AMD using this [guide]("http://wiki.cchtml.com/index.php/Ubuntu").
4. Install Adobe Labs native 64 bit Flash from [here]("http://labs.adobe.com/downloads/flashplayer10.html"), using this [**guide**]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install").

I have a machine with an ATi Radeion 2400 HD Pro (AGP mind you) with 1GB or RAM and an AMD Sempron 2600+. I've been using the ATi driver since 9.1 (installed using this [COLOR="Red"]**[Guide]("http://wiki.cchtml.com/index.php/Ubuntu")**[/COLOR], I recommend the manual install) along with the Adobe Labs native 64-bit driver. And I'm glad to say I do not get tearing.

---

### Post by alejandro.mc on 2009-05-07
Digging again. I have a motherboard M3A78-EM, that comes with the onboard Ati HD3200. Everything, and I mean eveything is flickering! Flash, videos of any kind, google earth, applications, all of them when Compiz as a Window Manager. Of course I turn that off and evything is back on track, but that's not a workaround, I want all the effects!

Can anyone help me?

---

### Post by shabazzk on 2009-05-08
> **alejandro.mc said:**
> Digging again. I have a motherboard M3A78-EM, that comes with the onboard Ati HD3200. Everything, and I mean eveything is flickering! Flash, videos of any kind, google earth, applications, all of them when Compiz as a Window Manager. Of course I turn that off and evything is back on track, but that's not a workaround, I want all the effects!

Can anyone help me?

What drivers are you running ATi catalyst 9.4 or open source that came with 9.04?

---

### Post by alejandro.mc on 2009-05-08
Ub 8.10

Catalyst 8.54.3

Thanks!

PD: I heard that going with this onboard to the last version of Ubuntu is not a great idea for the moment.

---

