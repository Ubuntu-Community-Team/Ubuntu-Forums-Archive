---
title: "Can't boot/install Live CD or Install CD of Ubuntu on Rev. B iMac G5"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by enzedchris on 2006-01-14
I have no idea why, but my iMac G5 just does not recognize these discs as start-up disks. I tried booting from cd holding down c, but that only worked for my OEM cds that install OSX, it is running tiger now. I can't seem to get to the yaboot prompt or anything. when i open the startup disk pane the unbuntu 5.10 disc does not show up. I am pretty new with linux and had it wroking on my old mac, but this just doesn't want to do it. please help me, and no lol i am not using a bluetooth keyboard to try and boot from the cd, it is a logitech usb keyboard that works fine otherwise. 

-Rev. B iMac G5 2.0 gHz, 150 GB and an 8x Superdrive if that is any help

---

### Post by ssam on 2006-01-14
where did you get the ubuntu cd from?
if you downloaded it and burnt it your self did you check the checksum, and burn it as an image (rather than just put the iso file on the cd.)

---

### Post by enzedchris on 2006-01-14
no, it is an official ubuntu cd from switzerland lol, a shipit cd, and it is of course for powerpc.

---

### Post by ctt1wbw on 2006-01-14
Well, more power to you if you can get past the keyboard and mouse freeze up bug.  More power to you, my man.  If you get, great.  Let me know how you did it.

---

### Post by enzedchris on 2006-01-14
man i can't even get past the dark grey apple, so idk what the deal is, breezy is installing on my imac g3 now, which was going to be arted out, but after getting frustrated with my imac g5 rev b, you know the ones whos fans are louder then f-18's 1 millimeter from your ear. lol may as well part out my new imac

---

### Post by chascon on 2006-01-15
This is a bit ot but finnix claims to boot G5s: [http://www.finnix.org/](http://www.finnix.org/)
From there you can hd install and upgrade to latest debian.
You have to configure X after installing it yourself.  Not hard at all if you know
your specs.

If you really want ubuntu you might get away with installing and upgrading to ubuntu.  But you have to have some intuition to resolve issues that crop up.  I have upgraded from sarge to testing to hoary to breezy succesfully before.

---

### Post by LoungeLover on 2006-01-16
Greetings...

This may not solve your problem, but worth a try.  I'm a dual 1.8GHz PowerMac G5 user running Tiger 10.4.4.

I'm also running Ubuntu 5.10 Live CD right now on my G5 as I type this reply.  :KS  

I downloaded Ubuntu today on my G5 from this site, [http://ftp.ucr.ac.cr/ubuntu-cd/5.10/](http://ftp.ucr.ac.cr/ubuntu-cd/5.10/) (the Costa Rica location), because it was fast and gave me a good download.  Try this same site for your **Mac (PowerPC) live CD** iso and download it to your Desktop.

Once you've downloaded the PPC iso, do the following:
[list=1]
[*]Insert a blank CD in your writable drive.

[*]Open Disk Utility in Tiger, hit COMMAND-B (the Apple Key & B) to invoke the Burn function.

[*]Select the downloaded iso from your Desktop and click BURN. (You'll probably get a pop-up box about burning from the other Tiger app, just click ignore on it.)

[*]Allow the burn to complete then close DU when done.  You should see the Ubuntu Live CD icon on your iMac Desktop.

[*]Restart your iMac and hold down the "C" key on your keyboard while booting with the Ubuntu Live CD.

[*]You should see Yaboot running and land at the 'boot:' prompt.

[*]Type this at the boot prompt WITHOUT the quotes: live-powerpc64 [ENTER]

[*]Ubuntu should begin running from CD, configuring all the goodies in your iMac at this point.  You'll be asked a few questions, like language type, location, resolution and a couple of others.

[*]Once it's done, your Ubuntu desktop should load fine.[/list]

If you don't get this far, post back exactly where you get hung up at and any errors you see.  Write it down if needed, because vagueness won't help us help you.  I initially had a problem running Ubuntu earlier tonight because I wasn't using the 'live-powerpc64' option at the boot prompt. This is required for G5 PPC users.

Peace!

LL

---

### Post by enzedchris on 2006-01-16
still can't boot i don't know why, always goes straight to dark grey apple. i can;t get to open firmware or anything, and i am not using a bluetooth/wireless keyboard either, only things that work are holding down mouse button to eject cd

---

### Post by LoungeLover on 2006-01-16
[QUOTE=enzedchris]still can't boot i don't know why, always goes straight to dark grey apple. i can;t get to open firmware or anything, and i am not using a bluetooth/wireless keyboard either, only things that work are holding down mouse button to eject cd[/QUOTE]

Thanks for posting...

Did you try all of the steps I suggested, starting from getting a fresh download of the 600MB iso?  That would be the main thing to do first, as you may have corruption in your current CD.

I can tell you, those steps are what I did that worked for me on a G5.  Give it a shot!

LL

---

### Post by enzedchris on 2006-01-16
yes i have tried that and it does not work, have you got a revision b or a?

---

### Post by LoungeLover on 2006-01-16
I have the June 2004 dual 1.8GHz PowerMac G5, which I believe is "B."  It's the one that can take up to 4GB of RAM, not 8.

LL

---

### Post by enzedchris on 2006-01-16
i think that yours is an a, i bought mine in august 2005

---

