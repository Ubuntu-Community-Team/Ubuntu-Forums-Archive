---
title: "Coaster Maker"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by SpEcIeS on 2009-04-29
Having problems burning DVD's since 9.04 went stable. All my burns fail and leave me with coasters. Here is Brasero's log:

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_Y5XZSU.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_JU1ZSU.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_1PSZSU.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/species/KOQS06.iso (size = 109981696)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 5dcbd46a9a21cb3bf313cacd59b8f7cd ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=16
	-use-the-force-luke=tracksize:2150854
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/home/species/KOQS06.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/species/KOQS06.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4404948992 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)

```
Does anyone have a solution for this?

---

### Post by SpEcIeS on 2009-04-29
Is anyone even having burning problems? Both Debian 5.0 and Ubuntu do not seem to want to burn.

---

### Post by hansdown on 2009-04-29
Hi SpEcIeS.

Try burning at the slowest speed possible.

---

### Post by SpEcIeS on 2009-04-30
Thanks. :) Tried slowing the speeds and I came up with the same results. The funny thing is, during the BETA I was burning without a problem, which was pretty nice. I have been finding that all the distros that I have been using, up to this time, burned and ripped very very slowly. This is one of the many reasons I just gave up on linux. The help is just not out there, or their are no answers.

I suppose it will just be back to 32bit M$. Very disappointing. :(

---

### Post by Monsieur Gonzalez on 2009-04-30
If you are still with Ubuntu, you might try K3B. Though it's a QT/KDE app, it'll work just fine in Gnome. 

In the past, when I encountered burning problems, it had to do with the media I was burning (bad batch of DVD's, or fake ones, all toasters). 

Other than that, burning has always been fine with my hardware. I wish I could use my two DVD recorders at the same time, as with Nero in Windows, but, hey, Linux comes with so many more advantadges and for free, who knows, maybe some day.

---

### Post by SpEcIeS on 2009-04-30
I appreciate your input. :) My first move was to use k3b and then tampering with disc speeds. My apologies, but personally I do not buy the bad media issue. Here is why. When I had my HDD in a multi-partition Vista 32 bit/Ubuntu 9.04 AMD64, I had the burning failures that are described above. Once I found the problem I rebooted into Vista, using the same failed DVD, I could burn the intended material. This has happened on many different occasions. It just does not wash for me.

Yesterday I tried to burn the same data on my Debian 5.0 box and came up with failure too. In the past I have found that ripping is so very slow, 1.8x, and burning about the same, when working.

Currently I am compiling the 2.6.29.2 kernel, but I really do not expect any improvements. Hoping it will work though. Please wish me luck.

---

### Post by Monsieur Gonzalez on 2009-04-30
Good luck, then, I didn't mean to imply you were using "bad" media (Taiyo Yuden are hard to find, though ;) . 

You might try hdparm with your drive(s) just in case, if you haven't yet. sudo hdparm -i /dev/sr0. Mine looks like this : 
/dev/sr0:

 Model=PIONEER DVD-RW  DVR-112D                , FwRev=1.09    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode
"
"

---

### Post by pantone186 on 2009-04-30
It says you were burning at 16.4x1352KBps.

---

### Post by Yellow Pasque on 2009-04-30
Some possible solutions:
- Update the firmware on your drive
- If you have a SATA burner, try setting your BIOS to use AHCI on your SATA controller (as opposed to IDE)

---

### Post by SpEcIeS on 2009-05-01
Thanks guys for you input. I very much appriciate it. :)

Now, as far as speed is concerned, I believe that has been addressed fully. Speed settings do not help. After baking the 2.6.29.2 kernel, packaging it, and then installing it; it lead to nothing.

Here is a matter of interest, I again tried to burn some data to a DVD and found that there is a random track size being laid down. Most often it is around a megabyte. M$ will still use these media, but does acknowledge that there is a track. Some media were closed, however most were not.

The DVD burner is a PATA drive, which I suppose could be an issue since my HDD is SATA. Perhaps there is some mixup in the kernel.

What I do find very peculiar is that I have tested this on different machines and most often than not burning is just not that great, or not at all. The one I find very odd is that using linux I cannot burn to a DVD burner which is an LG. I mean really, this puppy is pretty generic. Perhaps someone could look past my frustration and offer me some brands that are totally linux compatible.

I suppose what one needs is a system that is specifically tailored for linux; everything 100% linux compatible. This is my mistake. Since the OS that came with my machine did not cost me anything, aside from the the straight out cost, then I think this machine is as good as it is going to be, unless I purchase a 64bit Vista, or Windows 7 when it comes out.

It is not that I do not like linux, personally I love it, but when things do not work, or do not work properly it just grinds my testicles together.

---

### Post by Ericyzfr1 on 2009-05-01
> **SpEcIeS said:**
> Thanks. :) Tried slowing the speeds and I came up with the same results. The funny thing is, during the BETA I was burning without a problem, which was pretty nice. I have been finding that all the distros that I have been using, up to this time, burned and ripped very very slowly. This is one of the many reasons I just gave up on linux. The help is just not out there, or their are no answers.

I suppose it will just be back to 32bit M$. Very disappointing. :(

In some instances, after reading the log I tried the Discs and they worked anyway.

---

### Post by Monsieur Gonzalez on 2009-05-01
Hdparm does not work either? I've got PATA dvd-burners too, and SATA disk, so that might not be the problem. I'm using AHCI in my motherboard, though.

I feel your pain; most things work with Linux, I've encountered problems with tv-tuners, but mainly it's the vendor's fault, for not providing specs for their products. 

As they say, freedom comes at a price. 

If that's of any help, my burners are:

PIONEER DVD-RW  DVR-112D
LITE-ON DVDRW SHM-165H6S

Both work fine.

---

### Post by SpEcIeS on 2009-05-01
> I feel your pain

Thanks so much Monsieur Gonzalez. :)

> I've encountered problems with tv-tuners, but mainly it's the vendor's fault, for not providing specs for their products. 

I have also had my grindings with tuners too, however I did overcome on that issue. As far as the vendor's, I totally agree. If things were not so closed then, I imagine, these issues would not exist.

Also, thank-you for listing your burners. This will be a great help for others too.

---

### Post by digital_1 on 2009-06-03
Same deal here.  Almost every CD is a coaster and I've tried both the GnomeBaker and Brasero packages.

I have a dual-boot machine and booting into "that other O.S." and burning from there makes perfect CDs.  It's ironic that I have to boot into that O.S. to burn "Linux" CDs.  Grrr.

---

### Post by Hairy_Palms on 2009-06-05
i was a big promotor of brasero (or bonfire as it was called) but since 8.04 it just randomly burns coasters every now and again for me, so ive been forced to go back to gnome baker, which seems to work totally fine. kindof an aside, as the original poster said he tried gnomebaker and k3b already, juts needed someplace to say it

---

### Post by SpEcIeS on 2009-06-20
Back to have another kick at the can. Regarding coaster making, I have found that my HL-DT-ST DVDRAM GSA-4153B drive will make coasters of DVD's, but not CD's. It would seem that, at least using RW's, that the drive can burn CD'S, however, this drive once burned without issue using Linux whether it be DVD's or CD's.

Does anyone have this particular drive (LG), and have success with it? Also, updating firmware, can this be done via linux, or do I have to place this drive into a Windows box to do this? All the firware packages that I have come across are Windows only.

My main box has a HL-DT-ST DVDRAM GH15F drive, which is a coaster maker too. Anyone have any success with this?

Keep in mind both drive are in good working order under Windows, but not in Linux, so far.

This would be the only thing holding me back from using Linux completely. Otherwise I have to have a partition of Windows to burn DVD/CD's, and that would be just plain stupid.

---

### Post by Yellow Pasque on 2009-06-20
I had problems with Brasero making DVD coasters too. K3b is my preferred burning program.
```
sudo apt-get --no-recommends install k3b
```

---

### Post by MScapee on 2009-08-18
I ditched Brasero and installed Xfburn.  I haven't had a lick of trouble since.  It works flawlessly, it's fast and it's Gnome-friendly (I absolutely despise KDE apps).  Xfburn is also actively being developed.

---

### Post by theZoid on 2009-08-31
> **MScapee said:**
> I ditched Brasero and installed Xfburn.  I haven't had a lick of trouble since.  It works flawlessly, it's fast and it's Gnome-friendly (I absolutely despise KDE apps).  Xfburn is also actively being developed.

I ditched Brasero for Gnomebaker....Xfburn is better also.

---

