---
title: "video crashes on dell studio need help"
date: 2009-02-24
forum: x86 64-bit Users
---

### Post by Unlearned on 2009-02-24
my sister recently bought a new computer a dell studio 64 bit

she wanted to try ubuntu so i tried to install 64 bit version, but video playback was not working so i installed the 32 bit version and again everything worked except video playback. 

anytime a dvd is loaded it freezes the system sometimes it will play audio for a bit before freezing completely.
also it sometimes flashes briefly and leaves colored after images onn the desktop it it tried to play and did not quite make it

she was fine with this for a bit she does not normally watch dvds on her computer, but she went to a website and it had a video that used the video player instead of flash and it froze her system.

anyone know what i can do to fix

---

### Post by Thelasko on 2009-02-24
What kind of Dell Studio is it?  There are several.  What kind of video card does it have?  Are all of the video codecs installed?  To install the codecs run
```
sudo apt-get install ubuntu-restricted-extras
```
in the terminal.

---

### Post by Unlearned on 2009-02-24
system:
	Studio 1537, Intel Core 2 Duo T6400, 2.0GHz, 800Mhz, 2M L2 Cache
		4GB, DDR2, 800MHz 2 Dimm
		Bright, Glossy, widescreen 15.4 inch display (1280x800)
	        Intel Graphics Media Accelerator 4500MHD
		320G 5400RPM SATA Hard Drive

i went through steps to get dvd
playback same as i used on mine i thought they all installed properly, except 64 bit codecs, but that may be because i have 32 bit ubuntu installed

---

### Post by Thelasko on 2009-02-25
Is she using Hardy Heron (8.04) or Jaunty Jackalope (8.10)?  You may want to switch between them to see if it's a problem with the video driver.  The driver is called, "xserver-xorg-video-intel".

The 4500MHD is a relatively new card, the drivers may have bugs.

Try checking your direct rendering by running:
```
glxgears
```
For details about direct rendering run
```
glxinfo
```
in the terminal and post the output.

---

