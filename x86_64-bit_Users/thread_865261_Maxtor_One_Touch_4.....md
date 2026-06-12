---
title: "Maxtor One Touch 4...."
date: 2008-07-20
forum: x86 64-bit Users
---

### Post by The_Phil on 2008-07-20
So, I picked out an external hard drive for my dad, not knowing he wa actually going to give it to me, otherwise I would have probably not gotten the drive which seems to have the most problems with ubuntu. When I plugged it in I got this message: "Unable to mount the volume 'OneTouch4'." Any ideas? It's a 500 gig maxtor one touch 4. Thanks!

---

### Post by warp99 on 2008-07-20
> **The_Phil said:**
> So, I picked out an external hard drive for my dad, not knowing he wa actually going to give it to me, otherwise I would have probably not gotten the drive which seems to have the most problems with ubuntu. When I plugged it in I got this message: "Unable to mount the volume 'OneTouch4'." Any ideas? It's a 500 gig maxtor one touch 4. Thanks!

You don't really mount the drives in *nix, you mount the file system. So 
what's the file system on the drive?

---

### Post by The_Phil on 2008-07-20
it's NTFS, thanks again!

---

### Post by damis648 on 2008-07-20
Try in terminal
```
sudo mkdir /media/onetouch
sudo mount -t ntfs-3g /dev/xxxx /media/onetouch
```

and see what happens, replacing xxxx with the listing (sda1, hda2, etc.).

---

### Post by jukingeo on 2008-07-21
> **damis648 said:**
> Try in terminal
```
sudo mkdir /media/onetouch
sudo mount -t ntfs-3g /dev/xxxx /media/onetouch
```

and see what happens, replacing xxxx with the listing (sda1, hda2, etc.).

I am having a similar problem with my Maxtor One Touch III, which is on a Firewire.

Someone told me to invoke those very same commands but with the second command the drive refuses to mount.

These are the results in my terminal:

geo@geo-desktop:~$ dmesg | tail -f /var/log/messages
Jul 18 23:50:21 geo-desktop kernel: [ 73.781078] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 18 23:50:21 geo-desktop kernel: [ 73.781113] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 18 23:50:23 geo-desktop kernel: [ 76.029571] NET: Registered protocol family 17
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 19 00:09:59 geo-desktop -- MARK --
Jul 19 00:29:59 geo-desktop -- MARK --
Jul 19 00:49:56 geo-desktop kernel: [ 3641.707069] scsi4 : SBP-2 IEEE-1394
Jul 19 00:49:57 geo-desktop kernel: [ 3642.706663] ieee1394: sbp2: Logged into SBP-2 device
Jul 19 00:49:57 geo-desktop kernel: [ 3642.706976] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Jul 19 00:49:57 geo-desktop kernel: [ 3642.707463] scsi 4:0:0:0: Direct-Access Maxtor OneTouch III 035f PQ: 0 ANSI: 4
Jul 19 00:49:57 geo-desktop kernel: [ 3642.710302] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
Jul 19 00:49:57 geo-desktop kernel: [ 3642.710638] sd 4:0:0:0: [sdc] Write Protect is off
Jul 19 00:49:57 geo-desktop kernel: [ 3642.711697] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
Jul 19 00:49:57 geo-desktop kernel: [ 3642.712091] sd 4:0:0:0: [sdc] Write Protect is off
Jul 19 00:49:57 geo-desktop kernel: [ 3642.712456] sdc: sdc1
Jul 19 00:49:57 geo-desktop kernel: [ 3642.733079] sd 4:0:0:0: [sdc] Attached SCSI disk
Jul 19 00:49:57 geo-desktop kernel: [ 3642.733136] sd 4:0:0:0: Attached scsi generic sg4 type 0

geo@geo-desktop:~$ sudo mount /dev/sdc1 /mnt/myextdrive
[sudo] password for geo:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdc1 /mnt/myextdrive -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdc1 /mnt/myextdrive ntfs-3g force 0 0
geo@geo-desktop:~$ 


It would seem that my options are really only the second one as of now (because I accidentally erased Windows the other day because of a gparted mistake).

However, the second option says "your own responsibility".  This drive has critical data on it and I would like to know the consequences of choosing the second option before doing so.

Also any advice you can give I would appreciate it.

Last night I found out that Linux does see my camcorder and it's files.  So this is the last problem to clear up so I can start to do video editing in Linux.

Thank You,

Geo

---

### Post by warp99 on 2008-07-21
> **jukingeo said:**
> 

**$LogFile indicates unclean shutdown (0, 0)**

The  'dirtylog' flag has been set. If you use the force option it will reset the logfile. Since you don't have Windows you can go ahead and use the force option your data will still be there, but if you have Windows using the force option may cause problems with Windows accessing the drive.

If you're very concerned about this mount the drive on a Windows machine doing a proper unmount, 'Safely Remove', to cleanup the logfile then you can mount the drive normally with the 'sudo mount -t ntfs-3g /dev/xxx /dev/mydrive' in Ubuntu.

---

### Post by damis648 on 2008-07-21
> **damis648 said:**
> Try in terminal
```
sudo mkdir /media/onetouch
sudo mount -t ntfs-3g /dev/xxxx /media/onetouch
```

and see what happens, replacing xxxx with the listing (sda1, hda2, etc.).

I see it had an unclean shutdown. Force mount it like I said before, but instead use:
```
sudo mount -t ntfs-3g /dev/xxxx /media/onetouch -o force
```

---

### Post by jukingeo on 2008-07-21
> **damis648 said:**
> I see it had an unclean shutdown. Force mount it like I said before, but instead use:
```
sudo mount -t ntfs-3g /dev/xxxx /media/onetouch -o force
```


I think the 'dirty' shutdown happened from an interrupted back up that happened on day one.  (I think I backed up and somehow or another it started to do it again, and I stopped it).  The program that came with the Maxtor One Touch isn't the most intuitive thing to come with an external hard drive.  At any rate, in Windows I was still able to access the drive regardless.  The stopped backup isn't where the critical data is though.   After that mishap I never used the Maxtor program again and I just used it like a regular USB hard drive (albeit but this one is firewire).  The critical data was added much later when I started putting baby pictures on the drive.

At any rate the "backup" files are still intact on another drive partition on my computer, so if those files are affected (currently on the Maxtor One Touch)...it isn't a big deal.  But all my baby photos MUST stay intact.


It will be a few days before I get Windows back up and I guess I will see if I can access the drive.  I certainly will not put that nasty backup program back on the computer, that is for sure.

Thanx,
Geo

---

### Post by phread59 on 2008-07-21
I have 2 of those drives installed.  I had one when running Windughs and just bought a new one.  I also could not get it to mount.  I tried force mounting it but to no avail.  In disgust I reloaded Winughs in a spare drive and tossed it in the computer.  I booted into Winsnooze and opened the Onetouch there.  It asked some silly questions and did a set up proceedure.  I shut down the Windsnooze and rebooted into Ubuntu and ever since they both mount up automaticly on my desktop.  And I can read and write to them without incident.  If that failed I was just going to reformat the bugger into EXT3 and try that.  These drives are not nativly Linux freindly.  Wish that manufactuers would get on the ball and support us Linux users better.

Mark Shuman

---

### Post by jukingeo on 2008-07-22
> **phread59 said:**
> I have 2 of those drives installed.  I had one when running Windughs and just bought a new one.  I also could not get it to mount.  I tried force mounting it but to no avail.  In disgust I reloaded Winughs in a spare drive and tossed it in the computer.  I booted into Winsnooze and opened the Onetouch there.  It asked some silly questions and did a set up proceedure.  I shut down the Windsnooze and rebooted into Ubuntu and ever since they both mount up automaticly on my desktop.  And I can read and write to them without incident.  If that failed I was just going to reformat the bugger into EXT3 and try that.  These drives are not nativly Linux freindly.  Wish that manufactuers would get on the ball and support us Linux users better.

Mark Shuman


Hello Mark,

Well, obviously for me a reformat is out of the question as there is critical data on that drive.  Last night I updated my machine with a new DVD Burner and I switched out my troublesome X-Fi card and installed an old Soundblaster Live, which is more compliant with Linux.  At any rate the upgrades knocked out my video driver  and I am having trouble getting it back.  So without a proper video driver, I can't get into Ubuntu!!!  So being down TWO operating systems now, I started to reinstall Windows.

I must say one thing Linux has for it in it's corner is that installation times are MUCH shorter.  Last night it took me 3 hours just to reinstall the core Windows OS, then install all the hardware support drivers.  Get the video and audio operational, do all the system updates and then put on the regular "housekeeping" programs (Office, Firefox, DVD/CD burner program).  I still have to install my audio and game programs tonight.

I was going to install the Maxtor driver, but the upgrade to Service Pack 2 took the longest time and I was tired.  So I am going to try to put the Maxtor drivers on tonight and open it up with Windows.  Hopefully I can "clear" that "dirty shutdown" flag and then when I get my video working in Ubuntu that I can finally mount the Maxtor drive.

Geo

---

### Post by The_Phil on 2008-07-22
So, anyway, back to what this thread is actually about, what do you mean by listing? how do I find out what it is?

---

### Post by jukingeo on 2008-07-22
> **The_Phil said:**
> So, anyway, back to what this thread is actually about, what do you mean by listing? how do I find out what it is?

What he means is how is your drive listed sda, sdb, sdc, etc.

Turn on your drive then go in your terminal and do an fdisk -l (that is a lowercase "L" not a 1 (one)).

It should list all the drives installed on your system.  If you have only one hard drive and the Maxtor, it would come up as sdb.  A partition on the drive would have a number, sdb1, sdb2, etc.

Once you found your drive designation, then invoke the commands replacing the xxxx with the drive designation.

sudo mkdir /media/onetouch
sudo mount -t ntfs-3g /dev/xxxx /media/onetouch

Be wary of any drives you have on your system and their capacity, especially any plug in drives through the USB or Firewire.

EDIT:

Oh! Almost forgot, if you don't have any serial drives on your machine it may start off with hda, hdb, hdc.  It was like that on my computer until I added a SATA drive.  Then Ubuntu switched everything to sd.  I don't know why that is the case.  I am assuming that hd stands for hard drive and sd stands for serial drive.  Generally any USB, Firewire, Sata, or SCSI drive would come up as sd because it is a serial drive.

Hope that helps!

Geo

---

### Post by The_Phil on 2008-07-23
alright, figured that part out, thanks again, and now I'm getting the following message when I try to mount it:


desktop@desktop:~$ sudo mount -t ntfs-3g /dev/sdf1 /media/onetouch
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdf1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdf1 /media/onetouch -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdf1 /media/onetouch ntfs-3g force 0 0






so.... I'm guessing what I may need to do is plug it into a windows (shudders) pc and unmount it cleanly and then try again, would I be correct in that assumption?

---

### Post by jukingeo on 2008-07-23
> **The_Phil said:**
> alright, figured that part out, thanks again, and now I'm getting the following message when I try to mount it:


desktop@desktop:~$ sudo mount -t ntfs-3g /dev/sdf1 /media/onetouch
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdf1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdf1 /media/onetouch -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdf1 /media/onetouch ntfs-3g force 0 0






so.... I'm guessing what I may need to do is plug it into a windows (shudders) pc and unmount it cleanly and then try again, would I be correct in that assumption?

That is exactly the same message I am getting.  However, I have not yet began to move forward with this problem because with reinstalling Windows, I now have a Grub bootloader problem and can't even get into Ubuntu.  So I have lots more of this to do now  ](*,)

If you scroll back up a bit in the thread you can see some of the suggestions that were offered to me.  Anyway, I decided to go with the less risky avenue and go through Windows.  Last night I loaded up the drivers for the Maxtor One Touch on Windows again.  I went into the drive to make sure everything was OK, and then I properly closed out of the program and properly performed the disconnect procedure to make sure that the drive closed out correctly and could be shut down.  So with that taken care of, I am hoping once I get Ubuntu working again, it should see the drive and the unclean shutdown flag will be cleared.

We will see.

Geo

---

### Post by The_Phil on 2008-07-23
IT'S WORKING!:guitar: I hooked the hard drive up to my friends laptop, disconnected it properly, plugged it into my pc, and it works perfect! Thanks guys!

---

### Post by jukingeo on 2008-07-23
> **The_Phil said:**
> IT'S WORKING!:guitar: I hooked the hard drive up to my friends laptop, disconnected it properly, plugged it into my pc, and it works perfect! Thanks guys!

So did you fix it by going into Windows, opening up the Maxtor program, closing the program properly, and then click on 'remove hardware; Maxtor One Touch'?

If so then I should be good to go as well.  I noticed that prior to my Windows Wipeout (heh, that sounds cool) the Maxtor One Touch icon on my taskbar tray was red.  It is now blue.  So I am HOPING that the dirty shutdown flag is cleared and once I get back into Ubuntu it SHOULD mount the drive.

So we will see about that.

Geo

---

### Post by The_Phil on 2008-07-23
Kind of, I just connected it to a windows pc, installed the software, and then used the "safely remove hardware" tool in windows, worked like a charm, so you should be good to go too.

---

### Post by jukingeo on 2008-07-27
> **The_Phil said:**
> Kind of, I just connected it to a windows pc, installed the software, and then used the "safely remove hardware" tool in windows, worked like a charm, so you should be good to go too.

When I HAD my Windows back up (for a brief period before Grub knocked it out AGAIN).  I did install the Maxtor One Touch III software and I opened it up.  Everything was where it should be.  So this time I made sure I properly closed out of the program and then made sure to 'safely remove the device', before turning it off.  The "M" emblem in the taskbar was blue all the while and not red.

So while Windows is a bit down now (it is reinstalled but I have the drive unplugged as I am conducting more tests with Grub through 64Studio).

At any rate I just decided to plug the drive in and see if it would come up.

It did!  I comes up as "New Volume".  Not a very good name if you ask me, but never the less I have access to it in Linux now.

So thanx again for the advice.  I am good to go.

Geo

---

