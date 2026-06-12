---
title: "No movies or OpenGL apps in windows on Hardy Heron"
date: 2008-04-22
forum: x86 64-bit Users
---

### Post by Lucretia9 on 2008-04-22
Hi,

I've installed Hardy on my machine and have got the machine working to a point where the 3D desktop works. This is very nice and I'd like to use it all the time if possible, but when trying out an OpenGL application or playing a movie there is massive flickering, the other windows are fighting with the GL layer.

Is anyone else having this problem?

$ uname -a
Linux rogue 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

My graphics card is a PCIe ATi X1950XT on a ASUS P5B motherboard.

Luke.

---

### Post by terry1311 on 2008-04-22
Hi, yes have the same problem. I tried installing the last proprietary ATI driver too, but it didn't help. If I figure it out, I'll let you know :)

---

### Post by Lucretia9 on 2008-04-22
I tried messing with a few other options I've seen in other peoples configurations during my scan across the net, but still nothing. I can't even find the documentation on these options :(

```

Section "device" # 
	Identifier	"device1"
	Vendorname	"ATI"
	Boardname	"ATI Radeon X1950XT (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Option      "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option      "TexturedXRender" "on"
	Option      "UseFastTLS" "1"
	Option      "BackingStore" "on"
	Option      "RenderAccel" "on"
	Option      "AllowGLXWithComposite" "on"
	Option      "no_accel" "no"
	Option      "no_dri" "no"

#	Option	    "MergedFB" "off"
#	Option	    "TexturedVideoSync" "on"
#	Option      "mtrr" "on"
EndSection

```

Luke.

---

### Post by warp99 on 2008-04-22
> **Lucretia9 said:**
> Hi,

I've installed Hardy on my machine and have got the machine working to a point where the 3D desktop works. This is very nice and I'd like to use it all the time if possible, but when trying out an OpenGL application or playing a movie there is massive flickering, the other windows are fighting with the GL layer.

Is anyone else having this problem?

$ uname -a
Linux rogue 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

My graphics card is a PCIe ATi X1950XT on a ASUS P5B motherboard.

Luke.

In you xorg.conf change: 
```
Option "VideoOverlay" 
```
from "off" to "on" which should stop the flickering. You may have to change some of the other options per the ATI configuration guidelines:

[http://ati.amd.com/products/catalyst/linux.html](http://ati.amd.com/products/catalyst/linux.html)

---

### Post by Lucretia9 on 2008-04-23
> **warp99 said:**
> In you xorg.conf change: 
```
Option "VideoOverlay" 
```
from "off" to "on" which should stop the flickering. You may have to change some of the other options per the ATI configuration guidelines:


I changed that option, but I still get flickering.

> **warp99 said:**
> 
[http://ati.amd.com/products/catalyst/linux.html](http://ati.amd.com/products/catalyst/linux.html)

I can't find anything relating to any xorg.conf options in that link or anywhere on ATi's site.

I found the following in my Xorg.0.log:

```

(WW) fglrx(0): Option "RenderAccel" is not used
(WW) fglrx(0): Option "AllowGLXWithComposite" is not used

```

Thanks,
Luke.

---

### Post by warp99 on 2008-04-23
> **Lucretia9 said:**
> I changed that option, but I still get flickering.



I can't find anything relating to any xorg.conf options in that link or anywhere on ATi's site.

I found the following in my Xorg.0.log:

```

(WW) fglrx(0): Option "RenderAccel" is not used
(WW) fglrx(0): Option "AllowGLXWithComposite" is not used

```

Thanks,
Luke.

You don't need all of those options lines in your xorg.conf file since many of them are enabled by default, plus there is most likely a conflict between some of them.

Your xorg.conf device section for the fglrx driver should look something like this:
```
Section "Device"
        Identifier  "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Driver      "fglrx"
        Option      "PseudoColorVisuals" "off"
        Option      "OpenGLOverlay" "off"
        Option      "VideoOverlay" "on"
        BusID       "PCI:1:0:0"
EndSection
```

ATI must have changed their site after the AMD takeover so the configuration parameter files are not there. Anyway the options configuration is documented here with the aticonfig program:

[http://wiki.cchtml.com/index.php/Aticonfighelp](http://wiki.cchtml.com/index.php/Aticonfighelp)

and here is a troubleshooting guide for the fglrx drivers that should be helpful:

[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

---

### Post by Lucretia9 on 2008-04-23
It seems the flickering is a problem with the DRI implementation and won't be fixed until DRI2 is available.

Luke.

---

### Post by Wynne G Oldman on 2008-04-24
I have the same flickering problems with screensavers and Google Earth on my Thinkpad, which has an ATI X1400 graphics adapter in it. Works fine on my desktop machine though, that's got a Nvidia Geforce 7300LE in it.

---

### Post by soxs on 2008-04-24
@ Lucretia9: You have 2 device, monitor & screen sections in your xorg.conf. Get rid of one set.

---

### Post by Lucretia9 on 2008-04-25
> **soxs said:**
> @ Lucretia9: You have 2 device, monitor & screen sections in your xorg.conf. Get rid of one set.

It's a dual monitor card, but 1 is not in use. I will comment one out, but I can't see that fixing anything.

Luke.

---

### Post by soxs on 2008-04-25
Multimonitor is not bugfree, not at all.

---

### Post by ASULutzy on 2008-04-25
So of course you can always switch to Metacity, but one work around I have found is turning on non-redirect full screen windows in compiz settings.

That will eliminate any flickering you'd have while in full screen.

---

### Post by mattmattmatt15 on 2008-04-25
I don't think the problem is with the official ATI Drivers.  I believe it is a bug in Compiz (I could be wrong).  Goto System>preferences>appearance, and visual affects.  Change it to none.  Fixed it for me.

---

### Post by Wynne G Oldman on 2008-04-26
> **mattmattmatt15 said:**
> I don't think the problem is with the official ATI Drivers.  I believe it is a bug in Compiz (I could be wrong).  Goto System>preferences>appearance, and visual affects.  Change it to none.  Fixed it for me.I totally agree! I just tried the same thing and there's no more flickering. Looking on the bright side, my Thinkpad wouldn't work at all with previous versions of Ubuntu. It's great that we're seeing some progress with ATI graphics adapters.

---

### Post by st0nedpenguin on 2008-04-27
I resorted to taking a performance hit and sticking with the open source driver out of the box.

It's one of the perks of having a rusty old X800 I guess, at least the open source driver has 3d support.

---

### Post by bestguy on 2008-04-27
> **soxs said:**
> Multimonitor is not bugfree, not at all.

Yep .. at this time and with the 8.4 Ati driver theres no OpenGL support when running Dual Screen with Xinerama oder else. 

Dont know if its a hardy problem or Ati. 

I switch to single Monitor to enable OpenGL again.

---

### Post by Canis familiaris on 2008-04-27
> **Lucretia9 said:**
> Hi,

I've installed Hardy on my machine and have got the machine working to a point where the 3D desktop works. This is very nice and I'd like to use it all the time if possible, but when trying out an OpenGL application or playing a movie there is massive flickering, the other windows are fighting with the GL layer.

Is anyone else having this problem?

$ uname -a
Linux rogue 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

My graphics card is a PCIe ATi X1950XT on a ASUS P5B motherboard.

Luke.

I did solve the problem by installing xserver-xgl and it did stop the flickering and it played movies fine without flickering but whenever I tried to run an openGL app like glxgears my X would crash, it also crashed with any openGL game like Chromium, etc :-(
I finally gave up reinstated xserver-xorg and installed compiz again, but got back to square one and now I'm forced to use Metacity which solved the problem.
I use Ubuntu Gutsy, by the way.

---

### Post by ASULutzy on 2008-04-27
My fix does work, but it'll only work for full screen.

Click system, preferences, then whatever your compiz control settings manager is listed as (the thing that lets you play with all the compiz stuff, mine is different because using compiz-git)

Then go to general options, on the general tab you'll see an option called unredirect fullscreen windows. Check that.

Now whenever you run a 3d game, just run it full screen and you won't have any flickering.

If this isn't a good solution for you, install compiz fusion icon. This will let you easily switch back and forth from compiz to metacity with just a mouseclick.

---

### Post by mattmattmatt15 on 2008-04-27
found a thread that explains the problem, ATI drivers do not support dri2, so it causes problems when compiz and an opengl app is open at the same time. There is no fix at the time.

[http://forum.compiz-fusion.org/showthread.php?t=7045](http://forum.compiz-fusion.org/showthread.php?t=7045)

---

### Post by alexei.colin on 2008-05-10
> **ASULutzy said:**
> 
Then go to general options, on the general tab you'll see an option called unredirect fullscreen windows. Check that.

Now whenever you run a 3d game, just run it full screen and you won't have any flickering.


Awesome! Worked. No more pixelated DVDs and can play them in Compiz! 

Let me add, if Unredirect Fullscreen Windows has a checkmark next to it, but you still have the problem, then uncheck, run and exit some OpenGL app, go back to Compiz settings and check the box back. In my case the OpenGL flickering was gone after this. Hope this helps someone.

---

### Post by ASULutzy on 2008-05-10
> **alexei.colin said:**
> Awesome! Worked. No more pixelated DVDs and can play them in Compiz! 

Let me add, if Unredirect Fullscreen Windows has a checkmark next to it, but you still have the problem, then uncheck, run and exit some OpenGL app, go back to Compiz settings and check the box back. In my case the OpenGL flickering was gone after this. Hope this helps someone.

Yea, I think it's weird... I find solutions on the forums on incredibly impossible things, but it took me forever to dig up this simple fix lol

---

### Post by joegiampaoli on 2008-06-22
It's all due to the new xorg.conf, I have Nvidia card, I can't play most of the gl games nor my son, it just gives me refresh rate errors forcing me to force log-out. At the moment there is no fix and to tell you the truth I don't know when, This bug is a MAJOR bug, I can't believe they put so much experimental things that are so buggy on a LTS version of ubuntu and release it. I was waiting for this release with a lot of great expectances but it just has been error after error.

---

### Post by crosswalker21 on 2008-07-14
I have this problem as well on my ATI x1200 chipset.  the unredirect full-screen windows works fine, but for non-fullscreen windows the following might be of use:
[LIST=1]
[*]Open up CCSM (compizconfig-settings-manager from terminal, or "Advanced Desktop effects Settings" from the System->Preferences Menu) and click the "Extra WM Actions" plugin.
[*]Set up a keyboard shortcut for the "Toggle Redirect" option (make sure that the plugin is enabled via. the checkbox on the left side of the screen)
[*]Whenever you find a flickering window, hit that keyboard shortcut and it will stop flickering.
[/LIST]

**One caveat:** In most apps (all that I've tried) this will keep window menus from opening (alternatively, menus might open but the window starts flickering again).  Apparently compiz doesn't like to render "normal" and composited windows at the same time.  If you need to access menus, you'll need to hit the key combo again and deal with flickering for a bit.

---

### Post by Insperatus on 2008-11-02
Good temp fix, thanks!  I've been disableing compiz everytime I want to watch a movie but this is quicker.

---

### Post by frankob on 2008-12-10
this doesn't work for me...
Then I tried the "unredirect full screen windows" solution, instead. It works! :-)

EDIT: Well, it really works just for OpenGL stuff in full screen. The videos keep to flicker. But I found a work around for this, too. :-)

Open /etc/X11/xorg.conf

In Section "device", under Driver "fglrx" add the following line:

Option "TexturedVideo" "off"

Save, close, restart X, and that should do the trick! ;-)

BUT! My MPlayer crashes with some outputs (includinf xv) after I added this line in xorg.conf. But I can still use x11 video output (but this one works even without the fix), or gl or gl2. Both of the latter 2 will flicker in window and work just great in full screen.
I didn't notice any such problem with VLC or Totem. Everything seems to be fine with them.

---

### Post by perixx on 2009-02-15
Just for those, for which the suggestions here won't work at all or not reliably (so it was for me), here's a temporary fix from gatekeep, that should work for every body (I've also added my 5 cents):

[http://ubuntuforums.org/showthread.php?t=895182](http://ubuntuforums.org/showthread.php?t=895182)


perixx

---

### Post by goldenfleece on 2009-02-15
At the bottom of warp99's message (above) is a troubleshooting guide.  See the bit in the troubleshooting guide about turning off compiz.  It worked wonders for my flickering problem.

---

### Post by perixx on 2009-02-16
Thanks, goldenfleece,


but if you follow my link, you'll see, that I had no luck with those aticonfig-experiments.

The approach I prefer (based on some other's work) is a bit more sophisticated, so you don't have to switch off compiz completely, only 'on demand', so to say (per application).

Works very nice for me and I've tried about everything else around here in the forums for solving this problems. I like the advanced screen navigation controls of compiz, that's why I don't want to give it away...


perixx

---

