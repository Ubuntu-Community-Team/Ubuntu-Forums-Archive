---
title: "FIX for: Ubuntu AMD64 variants have blank screen after GRUB"
date: 2008-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by daInvincibleGama on 2008-01-19
There is a known issue in the LiveCDs and installs of the Ubuntu AMD64 variants with some video devices. I have seen 7.04 and 7.10 variants behave this way. All the answers are in replies to different, badly named topics, so here is a summary.

Some of the problems are caused by your system not being able to display the fancy splash screen. If you haven't installed any restricted drivers, this is probably your problem.

If you want to boot from LiveCD:

At the initial screen, DO NOT select the "Start Ubuntu" option. Instead bring up a command line and type in "startx" (without " of course).

If you installed it (i.e. from the text installer):

- Hit Esc at the "GRUB Loading...3...2..1" screen
- Select the option for recovery mode
- At the command prompt that comes up type
```
nano /boot/grub/menu.lst
```
- Go down towards the bottom where the menu entries for GRUB are. You should see
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=47ab51aa-92a6-40a9-b310-5f8336300e35 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
```
or some such

- Remove the "splash" option in the "kernel" line. It should look something like

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=47ab51aa-92a6-40a9-b310-5f8336300e35 ro quiet
initrd		/boot/initrd.img-2.6.22-14-generic
```
**As a precaution, do not Copy+Paste my entries if you don't know how they work. The installer does almost everything right, and you could end up FUBARing your system. Just make the one small change to the kernel entry.**

- Hit Ctrl+X to Save. Ansyer "yes" to do you want to save, and accept the path it gives you.

Ubuntu should boot up without a splash screen straight to the login screen.

If you have a newer nVidia card (such as an 8000 series, but not exclusively), you may get the same problems once you install the Restricted Drivers for it (nvidia-glx or nvidia-glx-new drivers I think). There is a problem with these drivers in that it doesn't output video to the correct output.

To fix this:
- Install the appropriate restricted driver using the manager.
- Restart  and hit Esc when GRUB loads up in Stage 1.5. Select Recovery mode.
- Type in ```
nano /etc/X11/xorg.conf
```
- Go down to the "Device" section, where it has the name of your video card (driver should say nvidia if you installed the restricted drivers correctly)
- Add a line below Busid that says ```
	Option		"UseDisplayDevice"	"DFP"
```
Here's my section, with the change in bold ```
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"UseDisplayDevice"	"DFP"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection
```
**Again, the other options may not be right for you, so don't copy this blindly if you don't know what they mean.** The "NoLogo" option is the only other one that I can guarantee will not mess anything up.

- Save it by hitting Ctrl+X and answering the prompts. Again, leave the filepath intact.
- Restart the system by typing "reboot" (without quotes)
- It should work.

I would appreciate if anyone that has this problem posts on this thread after attempting a fix (whether successful or not) so I can modify my instructions if necessary, and so that other people know the fix works if it does (and I can feel reassured :):guitar:).

---

### Post by daInvincibleGama on 2008-01-19
Here's my xorg.conf file, if it's going to help anyone. It's fairly standard, other than the option I added. I removed the InputDevice sections to save the clutter, instead focusing on the display sections.

```
Section "Files"
EndSection

# Insert your InputDevice sections here.

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"UseDisplayDevice"	"DFP"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

---

### Post by nbv4 on 2008-01-20
wow great tip. This doesn't happen only with AMD64 system either. I had the "blank screen" happen to me on my laptop with 32bit Kubuntu. removing the word "splash" from the /boot/grub/menu.lst did the trick. All though one weird thing, for some reason it keeps getting reverted, so I have to repeat the steps all over again. Not quite sure what thats all about...

---

### Post by hogman500 on 2008-01-20
man i wish i would have read this before my black screen happened it might have helped.

*note: although i think it might have been because of a code i modifyed*

---

### Post by NullHead on 2008-01-21
All I had to do is install startup-manger and set my vga output to 1024x768 or vga=792. 

I'm not sure why there is all those other steps of disabling usplash when it's simply a resolution error(in my instance) I have a e-GeForce 7600 GTX

---

### Post by khensucat on 2008-01-21
It's not just a matter of having the wrong resolution. If you don't use startup manager, for instance, and simply write the correct resolution in the file, and reboot, you'll still get the black screen in both 32-bit and 64-bit Ubuntu.

---

### Post by podfish on 2008-01-22
It keeps getting reverted because you're removing the "splash" in the system-generated portion.  If you look above, in all the "commented out" portion, you'll see a bunch of config options that the grub-update program uses to maintain your menu.lst file.  The double-commented (##) entries are real comments.  The single # are lines used by grub-update.  Here's the important part of my menu.lst:

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=
## defoptions=quiet splash

```

My defoptions is blank, since I want some sort of output if i'm not going to have a bootsplash.  I've kept the old line double-commented in case the bug gets fixed.  So, fix that, run *sudo update grub*, and you should be fine.

Note: For my SLI setup, "UseDisplayDevice" "DFP" failed to fix the problem.

---

### Post by crjackson on 2008-01-22
> **NullHead said:**
> I'm not sure why there is all those other steps of disabling usplash when it's simply a resolution error(in my instance) I have a e-GeForce 7600 GTX

Because that doesn't solve it in every case.  It depends on your hardware combo.

---

### Post by crjackson on 2008-01-22
> **khensucat said:**
> It's not just a matter of having the wrong resolution. If you don't use startup manager, for instance, and simply write the correct resolution in the file, and reboot, you'll still get the black screen in both 32-bit and 64-bit Ubuntu.

You're correct. It's not juse a resolution problem.  Startup manager won't fix it in every case either.

---

