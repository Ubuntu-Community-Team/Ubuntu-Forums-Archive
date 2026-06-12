---
title: "Okay, I think I've got it... (Gaming on Ubuntu)"
date: 2006-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by SpotMiH on 2006-09-25
Okay... sooo... here's what I've come up with, and do keep in mind this is from a mind that has never had any previous knowledge of the awesomeness of Linux systems.

From the literature that I've found online, here's what I need to do in order to get things to operate as is. First off, I do have two games I really have in mind for making them work (City of Heroes/Villains & World of Warcraft, any of my others are truly bonuses), but the wikiguides are throwing curves as they are not working and I wanted to double check my strategy to see if I'm on the right path.

-First off, install Linux (Given.)

-Install WineHQ to handle the Windows based applications and what not.. and I've been instructed to force install the 32-bit system as the 64-bit has a bit more trouble?

-Install World of Warcraft by copying the CD's onto the hard drive then running the system. (Or just copying over the already working version, would that work? Just work it from the previous installation?)

-In theory, with WineHQ installed and the guides for getting the World of Warcraft to work, there shouldn't be any further troubles and City of Heroes I haven't approached yet for installation, but I wanted to make sure I'm on the right track or am I missing a step that would help me immensly? I've had a very difficult time getting WineHQ to install, and I don't know the command to force install the 32-bit version...

Am I on the right path or am I missing anything? Appreciate your time.

---

### Post by tymek666 on 2006-09-25
Look at the first topic in this forum. There's excellent Kilz script that install Wine in Your 64bit system. It's like click and play ;)

---

### Post by SpotMiH on 2006-09-25
Oh Wow! Thanks! I feel a little foolish for missing it now... guess I failed that perception test!  Thanks, I'll hopefully have it up and running before too long!

---

### Post by SpotMiH on 2006-09-25
Aaarrrrgggh!! I don't get it!! Okay, so walking thru a Step by Step archive for Wine installation and it's doing nothing but teasing with my brain and making this far more complicated than I think it should be, so let me toss these errors up there...

dpkg: dependency problems prevent configuration of wine:
 wine depends on libartsc0 (>= 1.5.2-0); however:
  Package libartsc0 is not installed.
 wine depends on libaudio2; however:
  Package libaudio2 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine


I'm feeling so horribly lost but everyone keeps hyping up how awesome Linux is... but I'm having a very difficult time with what seems (through the 
[Install Wine64 Guide]("http://www.ubuntuforums.org/showthread.php?t=185557"))to be a very simple procedure yet I'm so confused why it's crashing out on me... and it's late so I'm going to rest my mind and hopefully tackle this tomorrow, any feedback or suggestions would be great, I'm going to read through the forums as indepth as I can between work to see if there's something small I'm missing, thanks for your time in reading again.

Actual wine error I'm getting when running winecfg:
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

Yeah... totally lost right now, and I did follow step-by-step of the guides out there, and not a clue what I'm doing wrong! ... help? I don't have my nVidia drives, and I saw mention of those... if I need those, I'll get those out of the way, but not sure what is causing it otherwise... thanks again!

---

### Post by tymek666 on 2006-09-25
Did You update yous ubuntu? I mean, do you have all updates installed?

---

### Post by SpotMiH on 2006-09-25
Ah! I was missing quite a few updates... I'll grab those, and try again, and hopefully with better luck this round. Thanks! Didn't even think of that... but then again, 4AM and not much is functioning in the head.

Bah... updated all the files, and started over from scratch and still get the same error when installing wine...

sudo dpkg --force-architecture -i wine_0.9.21~winehq0~ubuntu~6.06-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 72480 files and directories currently installed.)
Preparing to replace wine 0.9.21~winehq0~ubuntu~6.06-1 (using wine_0.9.21~winehq0~ubuntu~6.06-1_i386.deb) ...
Unpacking replacement wine ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on libartsc0 (>= 1.5.2-0); however:
  Package libartsc0 is not installed.
 wine depends on libaudio2; however:
  Package libaudio2 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine

.. Le Sigh. Ah well, I'll have a look at it tomorrow, thanks for the feedback and any & all is appreciated.

---

### Post by Kilz on 2006-09-25
Ok lets look at the errors, I have updated the howto to reflect the new errors that wine is producing.
> **SpotMiH said:**
> 
 wine depends on libartsc0 (>= 1.5.2-0); however:
  Package libartsc0 is not installed.
 wine depends on libaudio2; however:
  Package libaudio2 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine
This is sound related. We may not get arts to work if you dont run Kubuntu. Its a kde library if I remember right.

You need to install the 32bit sould libraries. You can use Synaptic to install lib32asound2 and ia32-libs-sdl or open a terminal and type in.
```
sudo apt-get install lib32asound2 ia32-libs-sdl
```
You can also try and install the [32bit alsa-oss package]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") I made for Firefox32. It may help in some cases.


> **SpotMiH said:**
> X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

This is a error that started showing up this version. It means you have no glx drivers loaded. Glx is your graphics acceleration. You need to install the graphics drivers for your card. What card do you have?

---

### Post by SpotMiH on 2006-09-25
Wow, thank you very much for all the feedback. Kubuntu... does that run with Ubuntu or is it kind of it's own system?

I'm running SLI cards actually with nVidia. Two nVidia 9700's, and I know that SLI is still pretty sketchy at this time, but I'm just excited to see about getting this working here. :)

But yes, thank you so much for the feedback, I'll grab the sound drivers & the video card and try getting it up and running again... here we go!

---

### Post by SpotMiH on 2006-09-25
dpkg: dependency problems prevent configuration of wine:
 wine depends on libartsc0 (>= 1.5.0-1); however:
  Package libartsc0 is not installed.
 wine depends on libaudio2; however:
  Package libaudio2 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine

Is the error still as I am NOW able to load up the winecfg & updated the nVidia drives with the latest open-source drives, and now I'm still getting this error when I go to load the patch for World of Warcraft... I installed & ran the audio files you suggested and while it made a little bit of progress as I can now actually run the wine application, I cannot get it to update with these settings for World of Warcraft, I did try tracking down where I can get the files but I mostly found references to MPlayer & downloading a w32codec package (wasn't sure if that was free though) so kind felt it was best to ask the experts here. Thanks for all the help, at least headway is being made!

---

### Post by Kilz on 2006-09-25
> **SpotMiH said:**
> dpkg: dependency problems prevent configuration of wine:
 wine depends on libartsc0 (>= 1.5.0-1); however:
  Package libartsc0 is not installed.
 wine depends on libaudio2; however:
  Package libaudio2 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine

Is the error still as I am NOW able to load up the winecfg & updated the nVidia drives with the latest open-source drives, and now I'm still getting this error when I go to load the patch for World of Warcraft... I installed & ran the audio files you suggested and while it made a little bit of progress as I can now actually run the wine application, I cannot get it to update with these settings for World of Warcraft, I did try tracking down where I can get the files but I mostly found references to MPlayer & downloading a w32codec package (wasn't sure if that was free though) so kind felt it was best to ask the experts here. Thanks for all the help, at least headway is being made!

Exactly what patch are you trying to install with the winecfg. Because I dont think thats possible. Did you visit my howto? If not click on Wine in my signature.

---

### Post by SpotMiH on 2006-09-26
Ooooh, I think I read that wrong in the Howto... pretty much if World of Warcraft is to be played, I need to use that version of wine (9.20) instead of 9.21? Wow, sorry, I completely was still in a different OS mode thinking of just patching/updating it, haha... wow, I'll get the hang of this. :) 

So just to clarify, use the file labeled wine-0.9.20_wow_i386.deb to play World of Warcraft instead of 9.21?  Thanks so much.

---

### Post by Kilz on 2006-09-26
> **SpotMiH said:**
> Ooooh, I think I read that wrong in the Howto... pretty much if World of Warcraft is to be played, I need to use that version of wine (9.20) instead of 9.21? Wow, sorry, I completely was still in a different OS mode thinking of just patching/updating it, haha... wow, I'll get the hang of this. :) 

So just to clarify, use the file labeled wine-0.9.20_wow_i386.deb to play World of Warcraft instead of 9.21?  Thanks so much.

Thanks for pointing out that the link was still to the 0.9.20 for wow. It now points to the 0.9.21. But yes use that wine deb instead for wow. The diffrence is that the WoW patches are already compiled in.

---

### Post by SpotMiH on 2006-09-26
Awesome!

Everything is now working, able to play online & switch between workspaces when needed to make sure I can bounce between resources! Thank you so much for the step-by-step help!  

The next venture is to wait for SLI capabilities in Linux, that'll just make it ever so much more sweeter, haha.  Thanks again.

---

### Post by eisle89 on 2006-09-26
Could you please direct me to a howto for AMD 64 ?? TIA

---

### Post by kopilo on 2006-09-27
That's fairly awesome, I didn't think WoW was playable under linux.

---

### Post by SpotMiH on 2006-09-27
Eisle, pretty much I just downloaded the install disc from the website [(www.ubuntu.org)]("http://www.ubuntu.org") and installed from there, didn't really have to do anything special, from reading in the posts you'd probably want to back up your information & just reinstall the 64 bit version as long as you have the hardware of course.

Kopilo, Yeah! I'm freaking stoked, and now going to try for City of Heroes & City of Villains but if it works similar I think I'll be in luck!  It does run a bit slower just because it doesn't handle my SLI cards at this moment, and I need to make sure my kernal is a AMD64x2 and what not, but yeah, can't complain! Drop the graphics down from uber maxed and it runs pretty smooth! 

Kilz, you rock! Thanks for all the help!

---

