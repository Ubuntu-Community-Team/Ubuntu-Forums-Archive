---
title: "Problem with fakeraid uptading feisty to gutsy"
date: 2007-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by fonsocm on 2007-10-13
I updated Feisty to RC Gutsy amd64. I used update-manager, the process went without problems.

After I rebooted the computer, I can boot Vista with grub but I can't boot Ubuntu.

I tried to use the RC Gutsy desktop amd64 cd to repair Ubuntu. However, I can download dmraid, iinstall it but when I execute dmraid -ay the installer doesn't show some messages and the raid doesn't show in /dev/mapper.

The motherboard is Intel GW965H.

Can some help me, please? How can I make to mount the raid with the installer of RC Gutsy?

Thanks in advance.

---

### Post by tomm3h on 2007-10-19
I've had a similar issue with my 32bit upgrade. I went from fully-updated Feisty to Gutsy final.

During the install, the installer decided to try and mount one of the underlying disks, /dev/sdb1 :(

It gave me some error about it not being a valid NTFS partition, and that I'd have to use chkdisk /f from a DOS prompt and then load Windows twice.

I don't know what the heck it was doing even trying to mount underlying disks in a fakeraid array -  Gutsy should be at LEAST dmraid aware by now!

I do have an NTFS partiiton across the array, but this is RAID0 - it's going to be across both disks, not just /dev/sdb1. So I'm a little concerned as to why that was happening, to say the least.

Either way I didn't think it would cause much issue. Unfortunately when I rebooted, 2.6.22 just kernel panic'd, mentioning something about not being able to find hd(0,0). I was tired so I went to bed, but I'm guessing part of grub's config is messed up due to the installer being retarded concerning my dmraid partition.

If only 3Ware RAID cards weren't so damn expensive :(

---

### Post by fonsocm on 2007-10-19
I think the problem is dmraid.

I tried to repair the boot partition using the RC Gutsy CD and dmraid wasn't able to open the RAID, in /dev/mapper is nothing.

I fill a bug about dmraid in launchpad but I didn't have some answer.

I'll test to repair the boot partition using the Final Gutsy CD.

---

### Post by UKCamaroSS on 2007-10-19
> **fonsocm said:**
> I think the problem is dmraid.

I tried to repair the boot partition using the RC Gutsy CD and dmraid wasn't able to open the RAID, in /dev/mapper is nothing.

I fill a bug about dmraid in launchpad but I didn't have some answer.

I'll test to repair the boot partition using the Final Gutsy CD.

Hi,

I also have the same type of issue. I am very new to Linux and installed 7.04 last week as a dual boot with XP. 7.04 worked fine. I used the update manager in Ubuntu to get 7.10 yesterday evening and got the following message:confused::
Can not mount volume.
$MFT has invalid magic.
Failed to load $MFT:Input/output
error failed to mount 'dev/sda1' :Input/Output error
NTFS is either inconsistent, or you have hardware faults, or you have a SOFTRAID / FakeRAID hardware

So, if you figure out a way to fix this, please let us know.

UKCamaroSS

---

### Post by Velociraptor on 2007-10-20
I have the same problem: dmraid + kernel panic on boot after upgrade. :(

---

### Post by Kemotaha on 2007-10-20
I am having the same problem with my dmraid setup

---

### Post by Kemotaha on 2007-10-20
just found the problem.  The new install didn't put a initrd in the grub.conf.  I booted an older kernel and found that this was the case.  Once I added the initrd line it worked fine.  

I also ran dpkg-reconfigure dmraid.  Not sure if that was needed

Nathan

---

### Post by jdarrenscott on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/141435](https://bugs.launchpad.net/bugs/141435) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having a similar problem with a Nvidia Fakeraid configuration. Under Feisty (with kernel 2.6.20-16) during boot, two devices are discovered under /dev/mapper :

/dev/mapper/nvidia_blah
/dev/mapper/nvidia_blah1

However, after upgrading to Gutsy, these are missing. Normally, these are coupled to become /dev/md1 ....
Interestingly I also have a Silicon Image Controller with a Softraid configuration, and these devices are discovered correctly with both Kernels.

During boot time with the new Gutsy Kernel, errors are reported as:

device-mapper: table: 253:0: mirror: Device lookup failure
device-mapper: ioctl: error adding target to table

I know there are a couple of Bugs relating to EVMS - this is definitely something different, as EVMS was never installed on my system.
Could this be something specific with dmraid/dmsetup/udev relating to the Nvidia Nforce4 chipset ?

Luckily, the Raid mirror I'm having problems with isn't the boot device, however I can't access the data (obviously).
Rebooting to the old Kernel kinda works, but introduces other problems with the Nvidia linux restricted graphics driver.

The partitions look fine from fdisk, but the discovery issue would appear to be the main problem.

Any help would be appreciated ... I'd hate to have to downgrade.

I think this is a bug and I've filed appropriately under Launchpad.

---

### Post by elightbo on 2007-10-21
Kemotaha:  Thanks a ton for finding the fix!  Just wanted to confirm that adding initrd line worked for me as well.

---

### Post by deustech on 2007-10-21
> **jdarrenscott said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/141435](https://bugs.launchpad.net/bugs/141435) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

device-mapper: table: 253:0: mirror: Device lookup failure
device-mapper: ioctl: error adding target to table

.

this is udevd problem since dmraid is not included in ubuntu livecd kernel by default

udevd has problem to mount your fakeraid with dublicate UUID of your fakeraid partition. i solved this manually to edit UUID of my fakeraid filesystem on both mirrored partitions (this is no desync fakeraid mirror, dont panic)
then every partition in fakeraid array except swap has different UUIDs this udevd problem with dmraid works FINE!

check you have dublicated UUIDs with 'blkid'

---

### Post by chrisccoulson on 2007-10-21
> **Kemotaha said:**
> just found the problem.  The new install didn't put a initrd in the grub.conf.  I booted an older kernel and found that this was the case.  Once I added the initrd line it worked fine.  

I also ran dpkg-reconfigure dmraid.  Not sure if that was needed

Nathan

I had exactly the same porblem on the upgrade to Gutsy. Fortunately, I spotted it before I rebooted after the upgrade. I posted in the Gutsy development section but it didn't seem to affect anyone else. [http://ubuntuforums.org/showthread.php?t=574316]("http://ubuntuforums.org/showthread.php?t=574316")

I'm also having a problem with dmraid and UUID's I filed a bug on Launchpad. I'm not getting any of the symptoms that you guys are getting, but I'm not sure if the two issues are linked [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/154834]("https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/154834")

---

### Post by jdarrenscott on 2007-10-21
Using tune2fs, I renamed the UUID's of my devices so that there where no duplicates.
Sadly the /dev/mapper/ directory still doesn't contain the correct "nvidia" devices for each raid device.  They are completely missing.

Anyone got any other suggestions / solutions ?

---

### Post by phcjpp on 2007-10-22
Same here - changing the UUID's didn't help. Interestingly I have 2 sets of raid 1. One can be seen, one can't. The one that can is VISTA, the one that can't contains XP and Gusty Upgrade.

Just can't get this back alive.

Chris

---

### Post by phcjpp on 2007-10-22
OK - got mine going now. Did the UUID thing. Also fixed the menu.lst that had missing lines

[http://ubuntuforums.org/showthread.php?t=574316]("http://ubuntuforums.org/showthread.php?t=574316")


Hope that helps someone.

Chris

---

### Post by jdarrenscott on 2007-10-22
Hi Chris,

Just wondering if you did anything else to get your Raid sets going ?
(I've checked my grub config, and it looks fine - ie. the initrd isn't missing on mine)

---

### Post by phcjpp on 2007-10-22
Hmm - can you try an older Kernel. I had about 6 options after the upgrade. The oldest one worked. Edited grub.lst and then the newer one worked. Sorry can't be of much more help. Booted with the live cd a few times to try and get dmraid going - never managed that. Not really sure what fixed it.

Chris

---

### Post by jdarrenscott on 2007-10-22
AHh - think I've fixed it.

I noticed on reboot, that the "blkid" command was showing the problem devices as TYPE-mdraid, but with the same UUID's

Looking at the mdadm utility, I noticed that you could use the Assemble options to rename the UUID's as part of the assemble process.

I used:

sudo mdadm /dev/md1 --assemble --update=uuid /dev/sde1 /dev/sdf1

And the missing "md1" nvidia array appeared correctly.  It now comes up on reboot also.

I'm still not sure why renaming the UUID's has fixed it, because even after running the assemble process with the UUID rename, both devices still have a duplicated UUID (albeit new ones!)

Also, unlike the Feisty release, these devices don't appear under /dev/mapper .. which makes me a bit worried that I'm going to get a conflict between mdadm and dmraid.

I guess I'm just going to have to give it a go and see what happens - at least the raid array is now visible.

Thanks for your help.

---

### Post by tomm3h on 2007-11-07
> **chrisccoulson said:**
> I had exactly the same porblem on the upgrade to Gutsy. Fortunately, I spotted it before I rebooted after the upgrade. I posted in the Gutsy development section but it didn't seem to affect anyone else. [http://ubuntuforums.org/showthread.php?t=574316]("http://ubuntuforums.org/showthread.php?t=574316")

Your walk-through worked a treat, thanks very much :)

---

