---
title: "New setup!"
date: 2005-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by f76 on 2005-10-30
Hi all im thinking of buying a new setup with nforce4 939 socket AMD64 cpu and nvidia 6150 onboard graphics... I have read a lot about lacking support for 64 bit cpus for drivers and such... Is it possible to revert to running 32 bit ubuntu if i cant get anything to work? I just need to know i wont be forced to move to windooze. Also i really need to know how the onboard gfx will be supported.. It would be nice :) I dont really feel like paying for a high end gpu...

---

### Post by zekolas on 2005-10-30
the 32 bit ubuntu will intall just fine on a amd64 based system. I would just try to download a ubuntu live cd to see if your graphics card will work. Also if your going to spend the cash on an AMD64 based system spend an extra $30-$40 and get a decent video card.

---

### Post by lovingboth on 2006-01-05
And the answer is... the graphics won't work with the NVIDIA drivers in 5.10.

Setup: Asus A8N-VM CSM motherboard with the NVIDIA GeForce 6150 chipset, Athlon 64/3700+.

First bad sign: with the 32 bit live CD, the installer can't work out what resolutions it supports for X.

Hope: the graphical bit of the install appears fine...

Dashed: ... but then X fails to initialise.

There's a BIOS option on this board which is there because the default means that 'some Linuxes fail to install' but switching that on has no effect.

I'll see if I can force it to treat it as a generic VESA card.

A note on an NVIDIA forum reveals their binary drivers only added support for the GeForce 61x0 chipsets ( and the GeForce 7800 GTX 512 for rich people :) ) with 1.08xx which was released in December. 

1.0-8178 is the latest, 22nd Dec 05 release date.

---

### Post by mo_x on 2006-01-05
It seems it is very difficult (at this time) to get everyting running for these motherboards (graphics, sound, ethernet). Check the nvidia linux forums which has some threads about it.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by kacheng on 2006-01-29
I've also been having problems.

Setup: Asus A8N-VM CSM motherboard with the NVIDIA GeForce 6150 chipset, Athlon 64/3200+.

Ubuntu:
64-bit installs fine, just had to set **noapic nolapic** or else it would freeze at the partitioning part of the install.

Video:
Had to use **vesa** driver.  The **nv** driver and **nvidia** drivers won't work (usually freeze up the screen in black).  I tried the available packages, and also the various nvidia drivers available for download, both 7667 and 8178.

If anyone knows how to get the nvidia driver working, I'd love to know.

Audio:
Can't seem to get it working at all as yet.

---

### Post by mo_x on 2006-01-29
The 8178 driver should be working. You can create a nvidia-bug-report.log with the command "sudo nvidia-bug-report.sh". Can you post this file as attachment (zipped if needed).

---

### Post by kacheng on 2006-01-31
Okay, here its my file.

I should note that I tried a zillion different permutation of kernels and drivers.  Synaptic, binaries from nvidia, 7667 7147 8178, the whole meal deal.

Currently, I've upgraded to Dapper, and it doesn't seem to have any effect.

I'm on an AMD64 kernel, an Asus A8N VM CSM motherboard with onboard Geforce 6150.  Can't seem to get sound to work either.

I should have just bought an old motherboard!

Thanks for any light you can shed on the issue.

---

### Post by mo_x on 2006-01-31
The log shows your using the vesa driver. Do the graphics wotk with this driver?
Please install the 8178 nvidia driver (the only one that supports your graphics card) and create a new log file. If you need any help installing the driver please let me know. Note that you need to remove al related packages (nvidia-glx linux-restricted-modules) with the --purge option before running the nvidia installer script.

---

### Post by RAOF on 2006-01-31
[QUOTE=mo_x]The log shows your using the vesa driver. Do the graphics wotk with this driver?
Please install the 8178 nvidia driver (the only one that supports your graphics card) and create a new log file. If you need any help installing the driver please let me know. Note that you need to remove al related packages (nvidia-glx linux-restricted-modules) with the --purge option before running the nvidia installer script.[/QUOTE]
Except if you're running Dapper: the 8178 drivers are what's in the nvidia-glx package.  You don't need to mess with the binary from nvidia.com - you get the same version in the Dapper package.

---

### Post by kacheng on 2006-01-31
I've tried using the 8178 driver, but will give it another shot.

What happens is that the screen freezes before the login screen in the nice calming ubuntu yellow, but nothing else, which makes me un-calm very quickly.

I can kill gdm, using Ctrl-Alt-Backspace.  I have to use the vesa driver.  The nv and nvidia drivers haven't worked for me.

I'll cross my fingers and try again.

K.

---

### Post by kacheng on 2006-01-31
So I thought I'd try installing nvidia-glx again and I get the following:
[I]
Selecting previously deselected package nvidia-glx.
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8178+2.6.15.4-4_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_1.0-3ubuntu7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-settings_1.0-3ubuntu7_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia-glx
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-settings_1.0-3ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

Now, I'm assuming what this is telling me is that nvidia-settings is now redundant?  Can someone confirm?

---

### Post by RAOF on 2006-01-31
[QUOTE=kacheng]So I thought I'd try installing nvidia-glx again and I get the following:
[I]
Selecting previously deselected package nvidia-glx.
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8178+2.6.15.4-4_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_1.0-3ubuntu7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-settings_1.0-3ubuntu7_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia-glx
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-settings_1.0-3ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

Now, I'm assuming what this is telling me is that nvidia-settings is now redundant?  Can someone confirm?[/QUOTE]Yup.  Nvidia-settings are now a part of the basic nvidia-glx package.

---

### Post by slavik on 2006-02-01
[QUOTE=zekolas]the 32 bit ubuntu will intall just fine on a amd64 based system. I would just try to download a ubuntu live cd to see if your graphics card will work. Also if your going to spend the cash on an AMD64 based system spend an extra $30-$40 and get a decent video card.[/QUOTE]
30-40USD won't buy a much better card ... better to save the money.

---

### Post by kacheng on 2006-02-01
Thanks ROAF.  I'm not familiar with repository management, but why would nvidia-settings still exist in the respository?

amd64 systems are cheap today!  There's no reason that as of Feb 2006 that anyone would be buying a 32bit system.

As for onboard video - I just need something that works half-decent, and this chipset seems half-decent.

Anyways, no luck on these drivers.

I just found a mythtv guide (when I find the link again I'll post here) that describes the use of module-assistant to rebuild the nvidia kernel.  I'm going to try that.

---

### Post by kacheng on 2006-02-01
Nope, rebuilding the nvidia kernel and installing Dapper's nvidia-glx (+ other packages) doesn't work.

When I boot, the screen freezes white before I get to the login screen. [-(

I have to reset the computer and boot in recovery mode to set the driver to 'vesa'.

Are there error logs I can look at to help determine the problem?

---

### Post by mo_x on 2006-02-01
Looks like you are using several methods of installing the nvidia driver at the same time. That can create problems and makes it difficult to tell why things are not working.

---

### Post by kacheng on 2006-02-02
Yeah, you are right - my post makes it sound like I'm mixing and matching installations. 

Let me rephrase that:

1. Reinstalling Ubuntu from scratch, then installing the nvidia-glx drivers does not work.

2. Completely removing the nvidia-glx drivers then installing the binaries from nvidia does not work.

3. Then, rebuilding the nvidia kernel using module-assitant does not work.

4. Completely uninstalling the binary driver and reinstalling the nvidia-glx drivers again does not work.

5. Installing the opensource nv drivers does not work.

In each case I get a frozen white screen before the login. :( 

6. Setting the driver to vesa works, but I'd like to see the nvidia drivers working to increase performance.


Any suggestions?

---

### Post by mo_x on 2006-02-02
Can you do the following:
1. Remove the nidia-glx and linux-restricted-modules with the --purge option.
2. Install the 1.0.8178 driver with the nvidia installer script.
3. Start X from the console with startx (not sure how to do this, maybe you have to deinstall gdm)
4. Create a nvidia-bug-report.log and post it here.
I am not saying that it is going to work but the log file may give some information to what is wrong.

---

### Post by kacheng on 2006-02-09
Okay last night there was another update pushed to nvidia-glx, so I tried using it again, with the same results.

Here's my file attached.

Any suggestions appreciated.

I bet I can disable some modules definitely, like v4l, but I'm not sure about the others.

Back to vesa again, for now.

Thanks

---

### Post by mo_x on 2006-02-09
I see the following error in the log.
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00000cc4, 0x00000cc4, 0)
Do you use the noapic nolapic kernel options?
You might want to post this log file on the nvidia linux forums.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by kacheng on 2006-02-09
Yes I had to use noapic nolapic as there are some problems with apic on my Asus A8N VM CSM motherboard.

How does that interfere with my Xserver?

Thanks for the link.  I'll look.

---

### Post by ahave2005 on 2006-02-26
Edit: I just noticed this was posted on AMD64 forum, sorry about this. I'm on a AMD64 processor, but use the 386 kernel.... The solution might still apply, but maybe not.

As for this motherboard, I have everything going. a8n vm cms , with HD azalia controller. I cant say it was an easy process, but with some help from ubuntuforums.org as allways, and nvnews.

I've written a helpless howto on nvnews:
[http://www.nvnews.net/vbulletin/showpost.php?p=824408&postcount=343](http://www.nvnews.net/vbulletin/showpost.php?p=824408&postcount=343)

Have a look here if you want this motherboard to do what you bought it for.

I have to say though, that an lspci still gives me rubberish, nothing reconized, but the drapper drake live cd knows all my hardware, even though its the same kernel. I still have to give the "noapic" to boot and not have X to freeze.

Ubuntu, and especially ubuntuforums rocks, that much I have to say.

/ahave

---

