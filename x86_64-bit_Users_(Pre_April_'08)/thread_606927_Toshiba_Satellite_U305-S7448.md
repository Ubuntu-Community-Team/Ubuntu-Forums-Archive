---
title: "Toshiba Satellite U305-S7448"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by dldeskins on 2007-11-08
A couple of months ago, I bought the Toshiba Satellite U305-S7448 laptop from [Office Depot]("http://www.officedepot.com/ddSKU.do?level=SK&id=592495&Ntt=u305&uniqueSearchFlag=true&An=text").  A nice little computer with enough HD that I could do a dual boot with linux (preferably Ubuntu).

After installing 7.04 (dual-boot), I realized that a LOT of the hardware didn't work (I spent some time reading the forum just to get the LiveCD to boot) .  Then I worked on it a bit, but decided to wait on 7.10 to see if there were any improvements.  After trying out the 64-bit 7.10 version on the livecd, I am pleased at how fast it runs and would like to get it installed with the hardware working.  What do I need to do to proceed?

Here is a list of hardware that does not work:
wireless (the wired works, so I can download,surf,etc with that)
camera
sound
dvd writer did not work with the 7.04 install
display will not go to 1280x800, but displays the default within the working area.

---

### Post by Fir3chi3f on 2007-11-09
I have a Toshiba satellite too
Here is what i did:

camera = search for cheese (using synaptic)

And for the [wireless]("http://www.uluga.ubuntuforums.org/showthread.php?t=512828") 

I don't know about the display or the sound both of those work on mine.  
You say the dvd writer didn't work with 7.04, what about 7.10?

---

### Post by sstusick on 2007-11-09
I have a Toshiba Satellite and all of my hardware worked out of the box on 7.04.

---

### Post by dldeskins on 2007-11-09
> **Fir3chi3f said:**
> I have a Toshiba satellite too
Here is what i did:

camera = search for cheese (using synaptic)

And for the [wireless]("http://www.uluga.ubuntuforums.org/showthread.php?t=512828") 

I don't know about the display or the sound both of those work on mine.  
You say the dvd writer didn't work with 7.04, what about 7.10?

Thanks for the reply.

Yes, the dvd was not recognized after i installed 7.04.

The display works correctly on yours?  wide-screen?

---

### Post by Fir3chi3f on 2007-11-09
got it working at 1280x800 with the restricted ati drivers ubuntu provides

I'm using 7.10 not 7.04. I couldn't get 7.04 installed at all.

---

### Post by Fir3chi3f on 2007-11-09
also i have satellite A215 series

---

### Post by dldeskins on 2007-11-11
> **Fir3chi3f said:**
> got it working at 1280x800 with the restricted ati drivers ubuntu provides

I'm using 7.10 not 7.04. I couldn't get 7.04 installed at all.

With mine, it is the Intel 965 chipset.  It actually is working, but a couple of oddities.  The login screen is 1024x768, aligned left-top (i.e., Not stretched).  Once logged, the menu bar is 1024 wide, the bottom bar can be moved but initially is 1024 wide.  
Neither of these cause problems, but is odd.

[Link to Screenshot]("http://www.flickr.com/photos/20231515@N02/1973939332/")

---

### Post by laltomar on 2007-11-12
For for U305-S7448 screen, you need to edit your xorg.conf.  This is noted in bug 136783.  The problem as I understand it is that internally the video card has a TV resolution interface. Becuase this interface has a lower resolution, that is what Ubuntu uses.  I'm running this on Ubuntu 7.10

Here are the edits for xorg.conf.  You need to add these two sections in xorg.conf:

Section "Device"
  Identifier "TV"
  Driver "intel"
  Option "monitor-TV" "TV"
EndSection

Section "Monitor"
  Identifier "TV"
  Option "Ignore"  "true"
EndSection

---

### Post by laltomar on 2007-11-12
For the Toshiba U305-S7448

If you want to quickly verify that the screen not showing on the full display is due to the external TV device bug 136783 run the following command in a terminal session:

xrandr --output TV --off

 
If your screen goes to full resolution, then you need to add the two sections in xorg.conf
 Section "Device"
   Identifier "TV"
   Driver "intel"
   Option "monitor-TV" "TV"
EndSection

Section "Monitor"
  Identifier "TV"
  Option "Ignore" "true"
EndSection

You will need to restart X (or just reboot).

---

### Post by dldeskins on 2007-11-13
OK laltomar, thank you for your help.  I will try this out tonight.

---

### Post by dldeskins on 2007-11-13
laltomar,

Everything is right now!  Thank you very much.

---

### Post by tgbrowning on 2007-12-21
Greetings,

Just bought a Toshiba Satellite (u305, s7467 version) and like the machine, pretty much, BUT.

Have had NO luck in getting a live CD install to run.  

Have had NO luck getting ANY ubuntu install to run. Granted, I've only been trying out 7.06 versions and early. Haven't tried Gutsy yet.

I noticed that some people had problems getting the live CD to run but overcame them -- how was that accomplished?  

Thanks,

Browning>>>

---

### Post by NDPeter on 2008-03-13
Just did this with my Satellite U305-2812.  Wanted to leave a note that it works here too!  Thanks!

Editted to note I'm referring to the known bug regarding the display.  I didn't notice any issues with my wireless in 7.10.

---

### Post by santiagogaitan@gmail.com on 2008-05-13
Hi dldeskins.

I've got the same problem with the ubuntu 7.x versions. I've installed the 8.04 64bits version from a live CD and the display problems has been solved. The speakers and the webcam are working too... Now i'm trying to fix up my mic... it isn't working.

I'll be so thankfully if sombody could help me.

---

### Post by santiagogaitan@gmail.com on 2008-05-14
Hi.

I just play with the option of the sound configuration. I checked the "capture" and "mic"options and just done! Now my oncase mic is working.

Thanks.

---

### Post by meditatingfrog on 2008-05-30
I have the same laptop ( u305-s7448 ).  I just installed 32bit hardy (8.04) and so far, video and sound work fine.  I haven't tried the webcam or the mic, because I don't use them.  The main problem now is the Atheros AR5006EG Wireless doesn't work.  I haven't attempted the ndiswrapper (whatever that is) fix yet (located [here]("http://www.uluga.ubuntuforums.org/showthread.php?t=512828")), to try and get this working.  

I'll post my findings.

---

