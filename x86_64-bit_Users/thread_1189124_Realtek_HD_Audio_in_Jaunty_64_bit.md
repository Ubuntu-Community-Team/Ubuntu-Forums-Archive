---
title: "Realtek HD Audio in Jaunty 64 bit"
date: 2009-06-16
forum: x86 64-bit Users
---

### Post by skibum3027 on 2009-06-16
I'm currently trying to get my sound to function. My sound card is integrated into my mobo (XFX 680i, uses Realtek).

I have yet to get the system to play any sort of sound.

I followed this guide:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
but still, I have no sound.

Any suggestions? Commands to upload the output of?

---

### Post by grege on 2009-06-16
might seem a bit obvious, but have you got the sound turned on in the mobo's bios?

---

### Post by grege on 2009-06-16
I have had a few issues with sound. You need to have all the pulseaudio stuff installed, especially the pulse volume control. In the normal ALSA mixer you need to get into the preferences and select everything.

Possibilities

Digital out is selected
headphone out selected
pcm volume on zero
wave volume on zero
something muted that should not be


Also in sound section of System -> Preferences it may have defaulted to the capture channel as the playback device.

Also to get proper multichannel playback you need to play about in Pulse Audio settings otherwise you can end up only being able to play one sound at a time.

---

### Post by skibum3027 on 2009-06-17
> **grege said:**
> I have had a few issues with sound. You need to have all the pulseaudio stuff installed, especially the pulse volume control. In the normal ALSA mixer you need to get into the preferences and select everything.

Possibilities

Digital out is selected
headphone out selected
pcm volume on zero
wave volume on zero
something muted that should not be


Also in sound section of System -> Preferences it may have defaulted to the capture channel as the playback device.

Also to get proper multichannel playback you need to play about in Pulse Audio settings otherwise you can end up only being able to play one sound at a time.

The sound is functioning in my bios. All sounds are normal when I boot to other OS's, so everything is functional from a hardware standpoint. What specific pulseaudio packages do I need to have installed? I downloaded alsamixergui, but I can't seem to find any preferences. All it seems to be is a bunch of sliders, which I set to all on full.

Ideally, my computer would play the digital out, but I can't seem to get it working. I've checked all the volume controls I can find and turned all the headphone lines down, and everything else up.

I have two sections of "Sound" in System -> Preferences, each with different options.
One has tabs of Sound Effects, Input, Output, and Applications. The input appears to register some sound, as it has a changing slider that would seem to be some "volume." The output has an option to balance left/right, it is in the middle. The applications tab says that no applications are currently playing or recording any audio, even when I attempt to play audio.

The second System -> Preferences -> Sound option has two tabs, devices and sounds.  The devices tab has drop down boxes to select audio devices. There are three dropdown boxes marked Sound Playback under the categories of Sound Effects, Movies and Music, and Audio Conferencing. Each of those has the following nine options. Which should I select?
Autodetect
HDA NVidia ALC883 Digital (ALSA)
HDA NVidia ALC883 Analog (ALSA)
HDA NVidia ALC883 Analog (OSS)
HDA NVidia ALC883 Analog (OSS)
HDA NVidia ALC883 Analog (OSS)
ALSA- Advanced Linux Sound Architecture
OSS- Open Sound System
PulseAudio Sound Server

Audio Conferencing also has a Sound Capture dropdown with the following options:
HDA NVidia ALC883 Analog (ALSA)
HDA NVidia ALC883 Digital (ALSA)
HDA NVidia ALC883 Analog (ALSA)
HDA NVidia ALC883 Analog (OSS)
ALSA- Advanced Linux Sound Architecture
OSS- Open Sound System
PulseAudio Sound Server
Test Sound
Silence

The last dropdown on the list is titled Default Mixer tracks and has the following options:
Capture: HDA NVidia - ALC883 Analog (PulseAudio Mixer)
Capture: Monitor of HDA NVidia - ALC883 Analog (PulseAudio Mixer)
HDA NVidia (Alsa Mixer)
Playback: HDA NVidia - ALC883 Analog (PulseAudio Mixer)
Realtek ALC889A (OSS Mixer)

This is all that i can come up with to post. I have tried every combo of these settings I can come up with, all to no avail.

---

### Post by grege on 2009-06-18
From your descriptions it appears that you have the Pulse Audio volume control.

Step 1

aplay -l

this will list your playback devices, ensure you sound is card 0. Sometimes a phantom HDMI device can grab the default spot.

Mine looks like this, I have a different sound chip to you

greg@greg-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

If it is not card zero then you need to reconfigure the setup.

Install or check that you have PulseAudio Device Chooser and Gnome Alsa Mixer (easier than alsamixergui)

Run device chooser and an icon will appear near you clock. Click on it and select "configure local sound server". In the third tab "Simultaneous Output" select "Add virtual output device for simultaneous output on all local sound cards".

There are a dozen threads involving ALC883 in these forums, might be time to read them.

It should work, the hardware has a driver. There is a solution, but I am bailing out as I do not have this chipset so my ideas are more general.

---

### Post by skibum3027 on 2009-06-21
I've now read and followed all of these pages directions to the best of my ability:
[http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=jaunty+alc883](http://ubuntuforums.org/showthread.php?t=205449&highlight=jaunty+alc883)
[http://ubuntuforums.org/showthread.php?t=616617](http://ubuntuforums.org/showthread.php?t=616617)
[http://mythtv.org/wiki/Configuring_Digital_Sound#Basics](http://mythtv.org/wiki/Configuring_Digital_Sound#Basics)
[http://mythtv.org/wiki/Configuring_Digital_Sound#But_I_want_to_have_all_my_sound_go_to_the_S.2FPDIF_connector.2C_how_do_I_do_that.3F](http://mythtv.org/wiki/Configuring_Digital_Sound#But_I_want_to_have_all_my_sound_go_to_the_S.2FPDIF_connector.2C_how_do_I_do_that.3F)
[http://www.mythtv.org/wiki/Enabling_nForce4_optical_SPDIF_output](http://www.mythtv.org/wiki/Enabling_nForce4_optical_SPDIF_output)

I still have no sound. Can someone help out? SOMEONE has to have been through this before. All I'm trying to do is get my optical audio out to play.

---

### Post by grege on 2009-06-24
On my Media PC which has a GA-MA78GM-S2H motherboard and ALC889A audio all that was required was to  make these two items visible in the mixer and select them.

IEC958
IEC958 Default PCM

I also set up surround speakers and the sub woofer. You need at least stereo to start obviously. It connects to my Yamaha Amp and works beautifully. There is an answer I just wish I could help more.

All I can suggest is getting everything IEC958 visible in the mixer and selecting them one at a time while you have some music playing. Also fiddle with Preferences -> Sound. On my Debian machine today I spent half an hours frustration with no sound because an update unselected "analog and digital out " in it's mixer.

---

### Post by master_kernel on 2009-06-24
Also give us the output of:
```
uname -r
```

---

### Post by Yellow Pasque on 2009-06-24
Before you give up completely, try OSS4. Sometimes, it's easier than wrapping youre head around all the ALSA/Pulse configuration: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by grege on 2009-06-25
Another random thought that popped up while reading the OSS install procedure, check if you have this package installed.

gstreamer0.10-plugins-bad    maybe -ugly as well.

If not, install it, log out of Gnome then back in again and check volume control and mixer.

---

