---
title: "Two-finger scroll on trackpad ??"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by lusepuster on 2005-10-27
Hi there - 

After having installed and setup Ubuntu on PC's for my mom and my sister, I seriously consider putting it on  my iBook G4. There are some nicties in OS X that I would be very sorry waving goodbye to, though. 

One thing is the Sleep/Suspend capability, does that work on Ubuntu PPC? And another is the very, very mice two-finger scrolling on the trackpad of my iBook which has been activated by iScroll. Is there any way of activating that in Ubuntu? I would hate having to revert to the scroll bars on  my website; my life's too short for sacrollbars ;o)

---

### Post by Netherfox on 2005-10-27
Probably not going to happen :( It seems many of us cannot get the trackpad to behave as we would like it to to begin with. We will probably have to wait for future releases of Ubuntu for scrolling capabilities, sadly.

---

### Post by skeporang on 2005-10-27
Isnt there an option with the drivers to have the far sides of the touch pad as scrollable? Or is that with other "windows" style laptops?

---

### Post by ipn1nj4 on 2005-10-27
I just wish I could find out a true way to disable core taps. I have heard 3 different solutions and nothing seems to work. 
*sigh*

---

### Post by prometoys on 2005-10-28
Hi,

there is a problem with the synaptics driver in ubuntu. you need version 14.3, but in ubuntu is version 13.6, even the apt tell you it is 14.3 (if i understood correctly)

prometoys@book:~$ apt-cache policy xorg-driver-synaptics
xorg-driver-synaptics:
  Installiert:0.14.3+revertedto+0.13.6-0ubuntu3
  Mögliche Pakete:0.14.3+revertedto+0.13.6-0ubuntu3
  Versions-Tabelle:
 *** 0.14.3+revertedto+0.13.6-0ubuntu3 0
        500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy/main Packages
        100 /var/lib/dpkg/status

check your X-Logfile with:

grep EE /var/log/Xorg.0.log

you will find out, that there was no synaptics touchpad detected (tha appletouch driver connect the appletouch-pad to X like a synaptics-touchpad. it's irrelevant, that the touchpad isn't frim synaptics)

however, i had a working X config and self compiled synaptics driver. get the source from the synaptics site, extract and compile it (maybe you need some devs, try out "apt-get build-dep xorg-driver-synaptics") and copy the synaptics_drv.o to /usr/X11R6/lib/modules/input/synaptics_drv.o.

BUT: you should know what you do (I didn't know it really, but i didnt bother ubuntu maintainer with bugreports about my self-compiled synaptics driver) and you should backup your old synaptics driver.

check further information on 

[http://www.popies.net/atp/](http://www.popies.net/atp/)

and my xorg.conf will be found on 

[http://www.prometoys.net/downloads/xorg.conf](http://www.prometoys.net/downloads/xorg.conf)

(but it is not nice written...)

i use two finger tapping for middle mousebutton (and 3finger works for right mouse, but i didnt use it) instead of two finger scrolling. my left side of the touchpad is for vertical scrolling. i didnt use horizontal scrolling

---

### Post by lusepuster on 2005-12-11
Okay, I finally got myself together and dual-booted. Tiied to follow your instructions up there letter-by-letter except I'm using 14.4 and not 14.3. I even copy-pasted the Synaptics part of your xorg.conf into my own, but it doesn't work. When I try running GSynaptics, it says I should add the line 'Option     "SHMConfig"       "true"' to my xorg.conf. But thing is the line is already there. 

Am I doing anything wrong?

I'm running Breezy on my iBook g4 933.

---

### Post by stefanb on 2006-01-08
Ho!

Don't know if you got it working, but since i wanted the two-finger scrolling
anyways, I made some chages to the synaptics driver. I sent it to the maintainer of synaptics as well,
but he didn't respond in a while now :(
You can get the patch [here]("http://lanpartei.de/~mirage/stuff/synaptics_two_fingers.2.diff.gz").

You need to patch synaptics-0.14.4 (take the source package from [here]("http://web.telia.com/~u89404340/touchpad/") before) with
```

gunzip -c synaptics_two_fingers.2.diff.gz | patch -p0

```

Then run make and copy synaptics_drv.o to /usr/lib/xorg/modules/input/synaptics_drv.so
(backup that one before in case there are problems...).
For breezy copy it to /usr/X11R6/lib/modules/input/synaptics_drv.o.
After that add a line  
```

Option          "TwoFingerScroll"       "1"

```
into your InputDevice section of xorg.conf.
That way you can scroll in vertical direction by putting two fingers onto the touchpad and drag them up and down.

Please tell me if there are any problems!

Stefan

---

### Post by lusepuster on 2006-01-09
Hey - 

Looks interestting. Don't know which file in the driver folder to patch though...??

---

### Post by stefanb on 2006-01-09
[QUOTE=lusepuster]Hey - 

Looks interestting. Don't know which file in the driver folder to patch though...??[/QUOTE]

Well, actually you don't need to know. Simply extract the source in your home dir which creates the directory
synaptics-0.14.4 and then download the patch to your home dir and issue the command from above in your home dir,
that should patch synaptics.c and synaptics.h

Stefan

---

### Post by lusepuster on 2006-01-09
Hi, and thanx. I patched it and installed it, and X went bye-bye, so I re-installed  the backup from the console.

it said a lot about unresolved somethings (sorry, didn't write it down). Xorg.0.log says something about no synaptics device and no repeater detected...

May it be of interest that I have mouseemu installed? And should I have the appletrackpad driver installed besides the synaptics one?

---

### Post by dombleu on 2006-01-09
stefanb: Would you care posting that "input device section" because i'm getting confused since I got two sections about mouse/touchpad.

I recompile the patched driver and installed it. Works well. But no two fingers thing....

for curiosity sake:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option		"TwoFingerScroll"	"1"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option          "TwoFingerScroll"       "1"
EndSection
```

---

### Post by stefanb on 2006-01-10
Ok, here's my section in xorg.conf, it is however for a regular
synaptics touchpad. I couldn't test my patch for any other compatible device,
so chances are that there is a problem because of different hardware access-
How do you use you ibook touchpad, is that by the appletouch driver or do you have a 'normal' synaptics touchpad?

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"TwoFingerScroll" 	"1"
	Option		"MinSpeed"		"0.09"
	Option		"MaxSpeed"		"0.18"
	Option		"AccelFactor"		"0.0015"
EndSection

```

Doesn't look too much different from yours though... What does 
Xorg.0.log tell you exactly. And are you sure you're using the patched driver now?
I don't have any clue, what the reason might be... :(

So lets start hunting...

Edit: Don't know about mouseemu, but you should try it without, you wouldn't need it anyway :)

---

### Post by jerrykenny on 2006-01-10
Luse,   for a kludge, cant you plug in a usb mouse ?     Personally I just find those padmouse things a faff

---

### Post by lusepuster on 2006-01-12
Stefanb:

I-ve been busy for some time (and will be for some time to come), so I don't know when I can test it, but I sure will.

jerrykenny:

I use the trackapd a lot and for much use I prefer it to a regular mouse, hence the fuss....

---

### Post by x1um1n on 2006-01-14
hi, 
i'm trying to follow your instructions on my Powerbook Pismo.  I've patched/compiled/installed the driver but i'm having similar issues to lusepuster.  

My touchpad section in xorg.conf is like this:
```
Section "InputDevice"
                Identifier      "Synaptics Touchpad"
                Driver          "synaptics"
                Option          "SendCoreEvents"        "true"
                Option          "Device"                "/dev/input/mice"
                Option          "Protocol"              "auto-dev"
                Option          "LeftEdge"              "60"
                Option          "RightEdge"             "900"
                Option          "TopEdge"               "60"
                Option          "BottomEdge"            "511"
                Option          "MinSpeed"              "0.2"
                Option          "MaxSpeed"              "0.9"
                Option          "AccelFactor"           "0.07"
                Option          "FingerLow"             "55"
                Option          "FingerHigh"            "60"
                Option          "MaxTapMove"            "100"
                Option          "MaxTapTime"            "150"
		Option 		"MaxDoubleTapTime"	"200"
                Option          "HorizScrollDelta"      "0"
                Option          "VertScrollDelta"       "30"
        	Option          "SHMConfig"             "true"
		Option		"RTCornerButton"	"3"
		Option		"LTCornerButton"	"2"
		Option          "TwoFingerScroll"       "1"	
EndSection
```

don't know how much of this is neccesary, i just pulled it all in (i want both scrolling & more buttons ;) )

and X refuses to load with this error:
```
Symbol alps_proto_operations from module /usr/X11R6/lib/modules/input/synaptics_drv.o is unresolved!
```
(many times many)

and finally: 
```
(II) Synaptics touchpad driver version 0.14.4 (1404)

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting
```

any ideas on what i'm doing wrong?
is it something in my device section, should i perhaps go for a simpler one like yours stefanb?

thanx in advance

---

### Post by stefanb on 2006-01-15
Hmm, it seems you have an alps-touchpad which should be supported by the synaptics driver.
However, I think your problem has nothing to do with my patch.
Have you used the synaptics driver before without compiling it yourself?
It's quite weird that your file doesn't include alps_proto_operations since my synaptics_drv.so includes it.
But since i'm not too deep into this driver, I don't know of many problems that might occur especially with apple hardware.
You might try compiling it again without the patch or searching for that error message with your favourite search engine.

Sorry that i couldn't be much help on that, but please tell us if you found something out.

Stefan

---

### Post by gatiba on 2006-02-26
Works great for me! \\:D/ 
Tx Stefanb!

P.S.
What about horizontal scrolling?

---

### Post by stefanb on 2006-02-26
Nice to hear that someone's actually using it... :)
I've actually tried to make horizontal scrolling work the same way, but there are two
problems.
At present, the driver does not detect two finger presses when the fingers are placed beneath each other(might investigate a bit sometime...).
The other problem is that horizontal scrolling for example in firefox is by default bound to go forward/backward in history, which makes it totally useless for me. Please report any problems you might have otherwise though!

Stefan

---

### Post by svref on 2006-02-27
Is 2-finger scrolling something that can happen on any ol' apple laptop, say a white 800mhz G3?

---

### Post by stefanb on 2006-02-27
Since I don't own any apple hardware I can't answer that specifically. But to some point,
apple used touchpads from synaptics which were identical with those used on intel pc hardware.
Again some of those do support detecting multiple fingers.
It most likely that if you can use two fingers with the synaptics-driver for middle click
that you can use two finger scolling - just try it out I suppose :)

Good luck,
Stefan

---

### Post by stefanb on 2006-03-17
Update:

I put in horizontal scrolling, so now it is possible to put two fingers on your touchpad and scroll around large images or websites with one move.
The option values changed a bit, see the linked page.
Somehow I was a bit lame to just use a search engine to find out how to change the way firefox behaves...
By default, firefox goes forward/backward in history(uahh).
To bind horizontal scrolling to horizontal scrolling, go to about:config and
change "mouse.horizscroll.withnokey.action" from 2 to 0.
Changing "mouse.horizscroll.withnokey.numlines" to 2 might be nice as well.

To get the new patch, see [here]("http://lanpartei.de/~mirage").

---

### Post by vjrj on 2006-05-19
Hi,

Here it's my conf in a Powerbook5,8 17" using the Stephan patch:

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "auto-dev"
        Option "LeftEdge" "0"
        Option "RightEdge" "900"
        Option "TopEdge" "0"
        Option "BottomEdge" "645"
        Option "HorizScrollDelta" "10"
        Option "VertScrollDelta" "10"
        Option "TwoFingerScroll" "3"
        Option "MinSpeed" "0.4"
        Option "MaxSpeed" "2"
        Option "AccelFactor"           "0.1"
        Option "SHMConfig" "on"
EndSection

and it works good for me the two-finger scroll.

Thanks Stephan.

---

### Post by fuoco on 2006-07-22
Now versions 0.14.5 and 0.14.6 of synaptics have two-finger scrolling included. How do I get these versions ? Is there a repository for that ?

---

### Post by _carl0s on 2006-08-26
Hi all

i cannot get my 2 finger scroll working at all.
Here my xorg.conf section for the trackpad.

[HTML]
<pre>
        Section "InputDevice"
                Identifier      "Synaptics Touchpad"
                Driver          "synaptics"
                Option          "SendCoreEvents"        "true"
                Option          "Device"                "/dev/input/mice"
                Option          "Protocol"              "auto-dev"
                Option          "LeftEdge"              "0"
                Option          "RightEdge"             "850"
                Option          "TopEdge"               "0"
                Option          "BottomEdge"            "645"
                Option          "MinSpeed"              "0.4"
                Option          "MaxSpeed"              "1"
                Option          "AccelFactor"           "0.02"
                Option          "FingerLow"             "55"
                Option          "FingerHigh"            "60"
                Option          "MaxTapMove"            "20"
                Option          "MaxTapTime"            "100"
                Option          "HorizScrollDelta"      "0"
                Option          "VertScrollDelta"       "30"
                Option          "TwoFingersScroll"      "1"
                Option          "SHMConfig"             "on"
        EndSection
</pre>
[/HTML]

i try to configure it through gsynaptics and here's what he says

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

But i found lots of site with "on" instead of "true", and btw "true" doesn't work too.

even synclient says

"        root@vonnegut:~# synclient -l
Can't access shared memory area. SHMConfig disabled?
"

and last but not least here's what /var/log/Xorg.0.log reports

Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

i just want to have my 2 finger scroll working.
Btw it's a pre 2005 powerbook 1,33 Ghz.

any idea?

---

### Post by stefanb on 2006-09-07
Hi,

looks like you don't have a synaptics touchpad. I heard the appletouch driver might help in that case. Gsynaptics is btw. not usable because it deos not know about the additional options. You can use synclient though (if the driver initializes, that is)

---

### Post by Rhubarb on 2006-09-07
While I'm not using a mac here (and I think I have read somewhere that the mac touchpad is a little different to get going than PC ones are), if it's of any help you can using the synaptic defaults:

Scroll Vertically using the very right hand side of the touchpad, just drag up and down with one finger.

One fingered tap = left click
Two fingered tap = middle click (I think, haven't tried this)
Three fingered tap = right click

I can't see much of a reason envolving the labour of another finger to scroll.  (Ahh, it's a tough life isn't it?)

---

### Post by stefanb on 2006-09-11
Just for the record: You don't need the patch anymore since it's included in synaptics from 0.14.5 on.
You need to compile it yourself though until it is included in ubuntu (it is included in edgy).

Seems i didn't notice that it got released for a while... :)

---

### Post by fuoco on 2006-09-11
Will it get included in dapper ? There's an open bug about it but I never saw any response from a dev...

---

### Post by stefanb on 2006-09-11
Well, honestly, I don't know.
But I guess not, since that would break other tools like ksynaptics and it's not that important. Compiling it yourself is fairly easy I think... :)
Anyways, edgy should be ready soon.

BTW: I added a small patch today ([http://lanpartei.de/~stefan]("http://lanpartei.de/~stefan")) that makes it easier to put two fingers on the pad
(it's okay to do one finger after the other now ;)).

---

### Post by fuoco on 2006-09-11
Wow that is so cool - it probably fixes exactly the one issue that was still annoying about it comparing to OS X. Thanks a lot!
Too bad it won't be in dapper soon, or atleast patch backported into dapper if not the whole new version...

---

### Post by stefanb on 2006-09-11
Let's see, I still haven't figured out why the cursor jumps.
So I hope that's not too annoying...

---

### Post by SidneySM on 2006-09-17
OK, I'm a complete linux n00b, used to adminnning OS X. I have a last-rev PowerBook, and am attempting to get the latest synaptics driver, with two-finger, working. I used apt-get to install the neccesary tools, applied the patch linked above, and did a sudo make install. I the added the driver to my config file. When I try to run
```
synclient -l
```
I get the message
```
Incorrect size of shared memory area. Incompatible driver version?
```

What am I doing wrong? Thanks.

---

### Post by stefanb on 2006-09-18
Ah, yes, i might have forgotten that.
Besides the .drv file you have to copy the compiled versions of syndaemon and synclient to /usr/bin.
Afterwards you should be able to use synclient.

Edit: I see you used make install. Restart your x server then i guess...

---

### Post by SidneySM on 2006-09-18
> **stefanb said:**
> Besides the .drv file...
Eh? What do I do with this?

> **stefanb said:**
> Edit: I see you used make install. Restart your x server then i guess...
Done. No improvement.

---

### Post by stefanb on 2006-09-19
Ok, the file synaptics_drv.o, which is created when compiling, is copied to  /usr/X11R6/lib/modules/input/synaptics_drv.o when you do make install. However, ubuntu uses /usr/lib/xorg/modules/input/synaptics_drv.so, therefore you have to copy it there manually (it is .so not .o).
I think that should work.

---

### Post by SidneySM on 2006-09-19
> **stefanb said:**
> Ok, the file synaptics_drv.o, which is created when compiling, is copied to  /usr/X11R6/lib/modules/input/synaptics_drv.o when you do make install. However, ubuntu uses /usr/lib/xorg/modules/input/synaptics_drv.so, therefore you have to copy it there manually (it is .so not .o).
I think that should work.
Woohoo! Fully working. The 'pad isn't as smooth as in OS X, but sufficient.
Thanks, stefanb

---

### Post by molusk on 2006-09-29
@Stefanb :
I tested your patch on Debian (unstable) with X.org 7 on my Macbook (not Pro).

I replaced synaptics_drv.so, and it crashes... X doesn't start.
I get this message :

> (II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
Symbol psaux_proto_operations from module /usr/lib/xorg/modules/input/synaptics_drv.so is unresolved!
Symbol event_proto_operations from module /usr/lib/xorg/modules/input/synaptics_drv.so is unresolved!
Symbol event_proto_operations from module /usr/lib/xorg/modules/input/synaptics_drv.so is unresolved!
Symbol psm_proto_operations from module /usr/lib/xorg/modules/input/synaptics_drv.so is unresolved!
Symbol alps_proto_operations from module /usr/lib/xorg/modules/input/synaptics_drv.so is unresolved!

If I use the base driver, the Option "TwoFingerScroll" doesn't appear in the log. Quite normal thing...

Do you have an other magic patch ? :mrgreen:

---

### Post by vik4 on 2006-09-30
I've just installed edgy beta on a 800Mhz g4 ibook, but can't get the synaptics driver happening. It is entirely possible that it isn't a synaptics touchpad, but would be nice to know for sure. dmesg doesn't mention anything about synaptics (only about an ADB mouse), and the x.org logs say they can't find a synaptics device. Am I doomed not to be able to use two-finger tapping? In OSX, I can get this functionality using the iScroll2 extension. 

The appletouch driver mentioned earlier - where does this live?

---

### Post by molusk on 2006-09-30
the appletouch module is part of the last kernels but often, it isn't in the base images.
you may have to make your own kernel.

---

### Post by vik4 on 2006-10-01
As I understand it, the appletouch driver is for usb trackpads only? I have an ADB trackpad, and the adb drivers are loaded.

Also, I have read that it comes by default now in ubuntu kernels (I'm running 2.6.17), but I couldn't find it anywhere, nor could I find it in the kernel source. Any ideas where it is or if it will help me?

---

### Post by jasonparekh on 2006-10-16
I've installed Kubuntu on my MacBook.  Switched to the synaptics+appletouch trackpad drivers and had hope.  However, there were a couple of issues:  mouse pointer not nearly as smooth as it should be, and two/three finger detection (for scrolling, taps, etc.) not too accurate when fingers are close.

I've made a patch to fix these issues.  I've attached it, but you can learn more about what was being done/how I changed it at [my blog post]("http://www.jasonparekh.com/?p=6").

jason

---

### Post by fuoco on 2006-10-27
How can I disable the old edge scrolling now that I have two finger scrolling?

---

### Post by jasonparekh on 2006-10-29
> **fuoco said:**
> How can I disable the old edge scrolling now that I have two finger scrolling?

In your /etc/X11/xorg.conf, remove the lines similar to: 

```
        Option          "LeftEdge"              "100"
        Option          "RightEdge"             "1100"
        Option          "TopEdge"               "50"
        Option          "BottomEdge"            "300"

```

jason

---

### Post by fuoco on 2006-10-29
> **jasonparekh said:**
> In your /etc/X11/xorg.conf, remove the lines similar to: 

```
        Option          "LeftEdge"              "100"
        Option          "RightEdge"             "1100"
        Option          "TopEdge"               "50"
        Option          "BottomEdge"            "300"

```

jason

Are you sure it's not the "VertEdgeScroll" and "HorizEdgeScroll" options? 

Other than that - has anyone noticed that the two-finger scrolling is quite hard to control, unlike under OS X? it's hard to describe but it's somewhat jumpy. The edge scrolling behaves better for me. Is it related to settings or it's something that needs to be fixed in the driver still ?
I understand not all the patches from this thread have been applied to the synaptics package... ?

---

### Post by chevkoch on 2006-11-19
> **jasonparekh said:**
> I've installed Kubuntu on my MacBook.  Switched to the synaptics+appletouch trackpad drivers and had hope.  However, there were a couple of issues:  mouse pointer not nearly as smooth as it should be, and two/three finger detection (for scrolling, taps, etc.) not too accurate when fingers are close.

I've made a patch to fix these issues.  I've attached it, but you can learn more about what was being done/how I changed it at [my blog post]("http://www.jasonparekh.com/?p=6").

jason

How do I apply this patch? Do I have to recompile the kernel? Sorry I'm a n00b

---

### Post by stefanb on 2006-11-19
> **fuoco said:**
> 

Other than that - has anyone noticed that the two-finger scrolling is quite hard to control, unlike under OS X? it's hard to describe but it's somewhat jumpy. The edge scrolling behaves better for me. Is it related to settings or it's something that needs to be fixed in the driver still ?
I understand not all the patches from this thread have been applied to the synaptics package... ?


Yes, the pointer jumps if you add or remove one finger while keeping one on the pad. I think this might be possible to change in the driver, but I haven't had time to look for it. Feel free to have a look, if it is there, it should not be too hard to find :).

Stefan

---

### Post by chevkoch on 2007-02-20
Anyone still working for smooth trackpad controls?
The only thing that keeps me from using Ubuntu on my iBook is the jumpy, inaccurate touchpad driver.

---

### Post by fuoco on 2007-02-20
For me I like better the way it works on my linux than on os X - I can't get along with the way it is in os x anymore. But people who use os X feel the other way around - so I can't say for sure...

---

### Post by theolster on 2007-04-27
Hi I'm also having problems applying this patch, how do I do so?

---

### Post by madonion87 on 2008-06-16
is anyone still working on the driver?
I'm using 8.04 atm, two finger scroll works, but very jumpy when i lift my finger off
normal scrolling works though

---

### Post by stefanb on 2008-06-17
Well, not me at least because my notebook died and my new one seems to have a synaptics touchpad that does not support multiple finger detection (which is kindof sad for a new device, so don't buy thinkpad r61 ;) )
So I'm stuck with plain side scrolling.

---

