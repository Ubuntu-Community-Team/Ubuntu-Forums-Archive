---
title: "still no sound - no help vampire"
date: 2009-08-03
forum: x86 64-bit Users
---

### Post by gshockxc on 2009-08-03
First, I'm trying not to be a [Help Vampire]("http://www.slash7.com/pages/vampires"), and if my fangs start to show, please drive a stake through my heart!  Thanks, Kilz.  

I've been struggling with no sound for a couple of weeks now.  I've been trying to solve this problem myself, but I just can't seem to get a handle on what's causing it.  

First, the basics: 
**Jaunty 9.04, AMD 64-bit**.

**What was I doing?:** Installed some updates on or after 7/20/09, sound stopped working sometime after that.  I don't know exactly, because I don't play music or videos every day.

**Yes:** I've already checked the mixer, and everything is unmuted, and all volumes are turned up.  

**Multimedia - System Settings:**CA0106, Audigy SE, and PulseAudio are listed, in that order.

I was doing some searching on the forums, and trying to figure things out on my end at the same time.  Finally, I came across a couple of threads like [this one]("http://ubuntuforums.org/showthread.php?t=1197981") about a recent kernel update causing a loss of sound.  I've seen several other threads that have been posted around the same 2 week time period by users who have experienced a loss of sound, similar to mine, occurring after an update.

Tixetsal mentioned that the kernel update seemed to be the cause of the problem, and it was possible to get the sound back by booting 2.6.28-11-generic, instead of 2.6.28-13.  

Has anyone else had this problem?  If so, can you point me in the right direction of where to start?  I don't recall how to boot an older kernal, and I can't find anything in Synaptic history to go back to an older version.  Also, I got some help upgrading my 64-bit flash.  I've seen other posts where members have had sound and flash problems, and they seem to be linked.  But I can't tell if I have a similar situation.

```
aplay -l
```
Results: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

So I'm lost.  I don't know where to look next.  Thanks.

---

### Post by Jaesin on 2009-08-04
are your speakers plugged into the audio device ca106?  for it seems that if your using the audigy to play sound, then that needs to be the primary playback device.  I know when i got my new board it came with onboard sound, so now i have two audio devices, and the one i'm not using for one reason or another is the default.  So i had to change that.

---

### Post by gshockxc on 2009-08-04
> **Jaesin said:**
> are your speakers plugged into the audio device ca106?  

Yes, my speakers are plugged in to CA0106.  They have been all along.  I haven't changed anything.  My board does have sound, but if that's now the default sound device, why doesn't it show up?  And how do I disable it?

I want the sound quality I have from my Creative sound card.  That's why I bought it.  I don't want to have to use the onboard sound from the motherboard.

---

### Post by Rrasyrogenees on 2009-08-04
i am not sure if i will be much help being a "forever" noob but this is a small offer...

  i am using my onboard sound (asus m3a78-em) and went to using pulseaudio and everything seems to be working yet that is on my x86_64 9.04... on my i386 9.04 i am having major problems since i am trying to use wine for playing world of warcraft and that wants to use also or oss in which i am at a major loss to fix it.  although WoW has sound i cannot seem to get it to recognize my audio and video capabilities to have audio chat and change things in the video section.

  i only suggest this since sometimes "smart" people forget the simple things too.  now if i could mix some of that smart stuff with my brain i might get my i386 sound working properly... lol

   good luck and i find breathing for a few minutes gives me time to think of the next thing to try... (i think i forget to breath sometimes too)

oh yeah... i am a "closet" help vampire... too afraid to ask so i hide in the closet... lmao

---

### Post by gshockxc on 2009-08-04
I don't know enough about what's going on with PulseAudio and ALSA to know how they two might be interfering with each other, nor do I know if that's even a logical possibility.

What is PulseAudio?  Is that the sound driver?  ALSA is also a set of linux sound drivers, correct?  Are they mutually exclusive?

On my system, it usually boots so fast that I can't even get to the GRUB boot loader to see if I can choose an older version of the kernel.

---

### Post by Yellow Pasque on 2009-08-04
Try booting your previous kernel

> On my system, it usually boots so fast that I can't even get to the GRUB boot loader to see if I can choose an older version of the kernel.

You can change that:
```
gksudo gedit /boot/grub/menu.lst
```
Specifically, you'd be interested in the 'hiddenmenu' and 'timeout' options.

---

### Post by gshockxc on 2009-08-04
> **Temüjin said:**
> Try booting your previous kernel



You can change that:
```
gksudo gedit /boot/grub/menu.lst
```
Specifically, you'd be interested in the 'hiddenmenu' and 'timeout' options.

Temujin; thanks for the help.  I'll try that.

---

### Post by jocko on 2009-08-04
> **gshockxc said:**
> What is PulseAudio?  Is that the sound driver?  ALSA is also a set of linux sound drivers, correct?  Are they mutually exclusive?
Pulseaudio is not a sound driver, it is a sound server. It acts as a software mixer that mixes sound from all different sources and sends it as one stream to the kernel sound component (ALSA).
The normal setup in ubuntu is to set **all** applications to use pulseaudio, and let pulseaudio be the **only** application that have direct access to alsa. Unless your sound card has a hardware mixer (and a driver that supports it), you will always need a software mixer if you want to be able to hear sound from more than one source at the time.

---

### Post by gshockxc on 2009-08-04
> **Temüjin said:**
> Try booting your previous kernel



You can change that:
```
gksudo gedit /boot/grub/menu.lst
```
Specifically, you'd be interested in the 'hiddenmenu' and 'timeout' options.

OK, really weird result to that code.  I typed in the code, entered my password and got this: 

```
gshockxc@jarvis:~$ gksudo gedit /boot/grub/menu.lst
gshockxc@jarvis:~$
```

Nothing happened.

Makes me wonder what I screwed up this time.  ;-)

---

### Post by grege on 2009-08-10
While playing some music.

In the mixer go to Preferences and enable Analog/Digital Output jack and any others that you might need..

Then look for Audigy Analog/Digital Output jack setting in mixer.

Deselect it

This worked for me with my Audigy 4.

I also install PulseAudio volume control and the other PulseAudio stuff and enable Simultaneous Output .

Lastly, i did not read all the posts, but make sure you motherboard sound is turned off (assuming the Audigy is an add in card).

---

### Post by gshockxc on 2009-08-10
> **grege said:**
> While playing some music.

In the mixer go to Preferences and enable Analog/Digital Output jack and any others that you might need..

I went into the Mixer that I have, and I don't have a Preferences option, I have 'Configure Channels.'  I've been in there before, and made sure that everything is selected.  It was like this the first time I looked at it, so I just left it the way it was.

[IMG]http://i33.photobucket.com/albums/d89/kristanxc/Mixer.png[/IMG]

> **grege said:**
> Then look for Audigy Analog/Digital Output jack setting in mixer.

Deselect it

You must have a different version of Mixer than I do, because I don't see those options on the Configuration panel

> **grege said:**
> I also install PulseAudio volume control and the other PulseAudio stuff and enable Simultaneous Output.

I checked all the packages I have installed for PulseAudio in Synaptic, and I can't find anything for PulseAudio that I don't already have installed.



> **grege said:**
> Lastly, i did not read all the posts, but make sure you motherboard sound is turned off (assuming the Audigy is an add in card).

I'm not sure how to do that.  These are the devices that show up in the Mixer Settings window.

[IMG]http://i33.photobucket.com/albums/d89/kristanxc/Multimedia-SystemSettings.png[/IMG]

CA0106 is the sound card that I have installed.  It was working fine for months.  Somehow, one of the updates created some issue that I haven't been able to pinpoint.  I've seen similar posts where the user has been able to solve the problem by running an older version of the kernel, but I haven't been able to access the Grub loader before it boots.  Too fast.  Can't find it in Synaptic either.

---

### Post by grege on 2009-08-10
Configure Channels is what I meant and you have them all selected. The only thing I can see that is different to me is IEC958. I would Mute that as it is digital out. Mine is an Audigy 4 and I have three times as many channels so mine will not help much.

Another place to look is the Backend Tab in Multimedia System Settings - you should be using xine not gstreamer.

In Synaptic look for Xine and Phonon and make sure it is all installed and in particular ensure libxine1-ffmpeg is installed.

Some big changes will require you to log out and in again (not restart) to see if the sound works.

I have a SB Audigy 4, KDE 4.3 from PPA backport repositories and a 2.6.30-4 kernel (also from PPA) and I had no sound initially, but it all works now.

---

### Post by grege on 2009-08-10
I had some more thoughts over night.

Try installing Gnome or Xfce4 as well as KDE and see if sound works there.

Install alsa-utils then run aplay -l to list your sound devices to look for clues.

Open a terminal and navigate to a sound file and use aplay somesong.mp3 to test.

One last action would be to use Dolphin with hidden files visible and remove the .kde folder and log out and in again with a fresh config - Warning everything will need to be setup again the way you like it, eg Amorok will need to rescan the collection.

To access GRUB just start tapping the ESC key as it starts to boot this will stop the system at the login menu allowing you to try an older kernel. I doubt that the kernel is the issue, but anything is worth a try.

I know it is frustrating, I have had the sound borked with updates a few times but luckily I have always found the solution eventually. My own system occasionally plays music at double speed requiring a restart of Amarok or aTunes. I have not solved that one yet.

---

### Post by Yellow Pasque on 2009-08-10
Sorry, I didn't know you had KDE/kubuntu.
```
kdesu kate /boot/grub/menu.lst
```

---

### Post by gshockxc on 2009-08-10
> **grege said:**
> The only thing I can see that is different to me is IEC958. I would Mute that as it is digital out. 

**BINGO!!!!**

That's exactly what it was.  I muted it, and I heard a click in the speakers.  Clicked 'Play' in Amarok, and away it went.  

Now I feel stupid that's all it was.  It make sense to me to have something muted that shouldn't be.  But it never occurred to me that I should mute a device to get sound out of another device.

Thanks for the help.  :guitar:

---

### Post by grege on 2009-08-10
Perhaps this is a good usablity lesson for the KDE or KMix devs, labelling the switch "Toggle Analog/Digital" would make more sense. Although on some systems concurrent analog and digital is possible and desirable, so maybe it needs even more settings. My media box runs digital and analog concurrently through an onboard ALC889.

---

### Post by gshockxc on 2009-08-11
> **grege said:**
> Although on some systems concurrent analog and digital is possible and desirable, so maybe it needs even more settings. My media box runs digital and analog concurrently through an onboard ALC889.

Here's where I need a little more education on the subject, because I don't know much about analog/digital.  Obviously, I know what they are, but I'm not familiar enough with sound, playback, etc, and Linux.  I'm assuming that when I muted the IEC958 in my Mixer, it turned off the analog sound.  Am I correct in that assumption?  Or is it vice versa?  Muted digital, and allowed analog to play?

BTW, Xine is installed, I noticed that before in the Backend Tab under Multimedia System Settings.  So I think I'm good to go, but I definitely want to learn more about this, b/c I'm sure my sound will get 'borked' again after an update.  Good word.  I like that, 'borked.'  :lolflag:

Thanks.

---

### Post by Jaesin on 2009-08-11
yep mute the digital allows the analog to be used as sound out.

---

### Post by gshockxc on 2009-08-11
> **Jaesin said:**
> yep mute the digital allows the analog to be used as sound out.

OK, based on that, digital has preference over sound output.  What is digital sound?  Can you give an exmaple?  I thought my .mp3 files were digital, but I obviously not.  Websites, videos, music, all play now that digital has been muted.  So what would I use digital sound for?

If I were recording digital video with a video camera, the sound track would also be digital, right?  If I upload that video file to my computer and try to play it, would I need to un-mute the digital to hear the sound?

I know these are pretty basic questions, but sound processing and signals are not my specialty.  Thanks.

---

### Post by grege on 2009-08-11
> **gshockxc said:**
> OK, based on that, digital has preference over sound output.  What is digital sound?  Can you give an exmaple?  I thought my .mp3 files were digital, but I obviously not.  Websites, videos, music, all play now that digital has been muted.  So what would I use digital sound for?

If I were recording digital video with a video camera, the sound track would also be digital, right?  If I upload that video file to my computer and try to play it, would I need to un-mute the digital to hear the sound?

I know these are pretty basic questions, but sound processing and signals are not my specialty.  Thanks.

Digital is the digital transmission of data, bypassing the on board sound processor and passing it to an external decoder. Optical SPDIF or co-axial digital to an external amplifier in the same way as a DVD player. My Media PC uses an optical cable to my Yamaha amp. I use the normal analog connection to take stereo to the TV for watching avis or when I am using the PC as a VCR. For movies or music I fire up the amp for high quality sound.

All computer sound is stored digitally, converted by the sound card for playback on analog speakers - OR passed on to an external amplifier.

---

### Post by gshockxc on 2009-08-11
> **grege said:**
> Digital is the digital transmission of data, bypassing the on board sound processor and passing it to an external decoder. Optical SPDIF or co-axial digital to an external amplifier in the same way as a DVD player. My Media PC uses an optical cable to my Yamaha amp. I use the normal analog connection to take stereo to the TV for watching avis or when I am using the PC as a VCR. For movies or music I fire up the amp for high quality sound.

Proving that I'm not a Help Vampire, I'm going to "Google" some of the things you mentioned and educate myself a little bit.  Then come back and ask some relevant questions.  Probably start a new thread.  Thanks for helping me get my box back on track.  I'm very grateful to have my sound back.  Thanks again.

---

