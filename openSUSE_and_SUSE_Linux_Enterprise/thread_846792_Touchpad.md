---
title: "Touchpad"
date: 2008-07-01
forum: openSUSE and SUSE Linux Enterprise
---

### Post by L815 on 2008-07-01
The settings on my touchpad using Opensuse 11 are horrid. I tried using different settings, but still ended up not good.

I was wondering, since Ubuntu gives me good setting for my touchpad automatically, if I can copy the configuration from the live cd over to Opensuse ? 

If so, where and what part do I copy so that the settings can be used with Opensuse? 

Thanks.

---

### Post by Sorivenul on 2008-07-03
For the most part that should work. I've included samples from my openSUSE 11 xorg.conf as a reference as well, though I set much of mine by hand. If you've got more questions, let me know.

Add these to the "Files" section:
  InputDevices "/dev/input/mice"
  InputDevices "/dev/psaux"

Add these to the "Module" section:
  Load	       "synaptics"

Add these as an "Input Device":
Section "InputDevice"
   Identifier	"Mouse[1]"
   Driver       "synaptics"
   Option       "SendCoreEvents"        "true"
   Option       "Device"                "/dev/psaux"
   Option       "Protocol"              "auto-dev"
   Option       "LeftEdge"              "130"
   Option       "RightEdge"             "840"
   Option       "TopEdge"               "130"
   Option       "BottomEdge"            "640"
   Option       "FingerLow"             "14"
   Option       "FingerHigh"            "15"
   Option       "MaxTapTime"            "180"
   Option       "MaxTapMove"            "110"
   Option       "ClickTime"             "0"
   Option       "MaxDoubleTapTime"      "100"
   Option       "EmulateMidButtonTime"  "75"
   Option       "VertScrollDelta"       "0"
   Option       "HorizScrollDelta"      "0"
   Option       "MinSpeed"              "0.60"
   Option       "MaxSpeed"              "1.10"
   Option       "AccelFactor"           "0.030"
   Option       "EdgeMotionMinSpeed"    "200"
   Option       "EdgeMotionMaxSpeed"    "200"
   Option       "UpDownScrolling"       "1"
   Option       "CircularScrolling"     "1"
   Option       "CircScrollDelta"       "0.1"
   Option       "CircScrollTrigger"     "2"
   Option       "SHMConfig"             "true"
   Option       "Emulate3Buttons"       "on"
EndSection

And don't forget to add this to your "ServerLayout" section:
  InputDevice  "Mouse[1]" "CorePointer"

---

### Post by L815 on 2008-07-04
Awesome, your settings run beautifully! 
The only thing that's not working is the scrolling (left side of touchpad), which didn't work with the defaults either.

---

### Post by Beyo on 2008-07-08
I've just installed OS 11. I was rathery happy with my OpenSuse 10.3 and I should remember not to change working distribution -never!
Why? because of problem with touchpad..it is not usable and I cannot find tool to set it correctly. In OS 10 everything worked fine.
So dont think to much - use Ubuntu not Suse

---

### Post by Sorivenul on 2008-07-11
Beyo, did you try using the settings that worked for myself and the OP?  Honestly I've had the same touchpad problems on any *buntu I've used, and a few other distributions as well, so it's nothing new to me to fix.  If it doesn't work at all just ALT+F2 and run a terminal, su and edit xorg.conf manually.  Keyboard shortcuts are our friends.  :)  Good luck!

---

### Post by rosencrantz on 2008-12-05
According to the [K/Qsynaptics homepage/]("http://qsynaptics.sourceforge.net/"), they changed the synaptics driver interface this summer, and touchpad control apps like ksynaptics, which I used to fine-tune my touchpad, don't work any more. The synaptics touchpad on my Samsung R55 has basic functionality on SuSE 11 (including vertical scrolling) with the default settings.

---

### Post by Sorivenul on 2008-12-06
> **rosencrantz said:**
> According to the [K/Qsynaptics homepage/]("http://qsynaptics.sourceforge.net/"), they changed the synaptics driver interface this summer, and touchpad control apps like ksynaptics, which I used to fine-tune my touchpad, don't work any more. The synaptics touchpad on my Samsung R55 has basic functionality on SuSE 11 (including vertical scrolling) with the default settings.

I've never been a fan of the graphical tools like K/Qsynaptics.  If the basic X configuration worked during the install but didn't after the install, that's an issue to me.  Granted, I got it fixed a while ago, and maybe the new X hardware detection and configuration would do a bit better.  Waiting until 11.1 is released to try a clean OpenSUSE install and see.

---

