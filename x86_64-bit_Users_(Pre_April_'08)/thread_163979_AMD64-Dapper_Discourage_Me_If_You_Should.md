---
title: "AMD64-Dapper: Discourage Me If You Should"
date: 2006-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-04-21
Hi,

I've built an AMD64 box and have installed Breezy, and have been somewhat dissappointed that I could not get certain things to build or run.

One such app. is TVTime and MythTV. I've tried to build MythTV and install the package without any success. Also, I haven't been able to get TVTime to see my PVR150.

I intend to install Dapper 6.06 and try again to build MythTV from scratch. If you think that this might not be the best course of action, please discourage me. Otherwise I'll forge ahead. Hopefully, AMD64 will find a home in Ubuntu very soon.

Please share your thoughts...

---

### Post by Jason_25 on 2006-04-21
I've been using dapper 64 for months now.  TVtime works like a dream for my ATI tv wonder.  This is a card that never worked quite right in windows.  I hate mythtv and all the junk you need to install along with it.  I'm using [XDTV]("http://xawdecode.sourceforge.net/") to record TV, it's lightweight, and it can even schedule at and cron jobs for recording.

---

### Post by FluffyElmo on 2006-04-22
I have mythtv running on my 64bit Breezy box with a PVR150 without any issues. I've never tried TVTime. It was a _pain_ to build from source though. What have you tried or where are you stuck? A few thoughts...

There used to be a post in the old Hoary 64bit forum that had a simple way to build by apt-getting the src packages, appplying a patch and then building...but I can't find it, may be worth a search though.

Perhaps you could just try grabbing the Myth packages from the Dapper repositories? Assuming the dependedncies aren't too Dapper specific it might be simpler than going all the way to Dapper. Here are some you could try. [http://ubuntuforums.org/showthread.php?t=163790]("http://ubuntuforums.org/showthread.php?t=163790") 

I'm assuming you have the card working and lirc set-up and Myth is the problem (it was for me), if you need help getting the card to work this was a good guide:
[http://www.abarbaccia.com/content/view/19/31/]("http://www.abarbaccia.com/content/view/19/31/")

Good luck, and while it was a very long time ago if I can help I will :)

---

### Post by bper on 2006-04-22
Thanks for responding!

FluffyElmo, I downloaded from each site MythTV 0.19 and the supporting software source and libs. I tried to build everything from source. Everything was going well until I got to the point of linking MythTV.  The link complained about not being able to find the QT definitions (for example: undefined reference to QTable::ShowColumn). The libraries are in the LD_LIBRARY_PATH but they are not being resolved.

Then I tried to set MythTV up using the directions here ([http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html))

and I had problems because the install complained about not being able to install mythtv-backend and mythtv-frontend. So I abandoned that approach.

Then I attempted to just try TVTime to see if I can get the card recognized and watch TV but I get no signal and no such file or directory - cannot open capture device /dev/video0.

So that's why I was considering Dapper, thinking perhaps that the new installation would resolve some issues.

Jason_25, does XDTV have all the features of MythTV? What are the differences?

Thanks for your help, I hope to really learn this stuff.

---

### Post by Jason_25 on 2006-04-22
XDTV is more like a VCR.  It doesn't support commercial skipping or dvr-like features that mythtv does.  I had it running in about 3 minutes though with downloading the amd64 debs from the site.  Mythtv wanted to create users on the system and install a mysql server and i hate all that bloat.  Also, it seems that mythtv in the dapper repos is very old as well.

---

### Post by bper on 2006-04-22
FluffyElmo,

I'm still at Breezy, and I've been able to get a little further now I'm up to getting ivtv to set the tuner correctly. Does anyone know how to set the tuner?

This is the output from dmesg:

[   41.072442] Linux video capture interface: v1.00
[   41.088616] ivtv:  ==================== START INIT IVTV ====================
[   41.088620] ivtv:  version 0.4.3 (tagged release) loading
[   41.088623] ivtv:  Linux version: 2.6.12-10-amd64-generic gcc-3.4
[   41.088625] ivtv:  In case of problems please include the debug info between
[   41.088628] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   41.088631] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   41.089135] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[   41.089459] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   41.089465] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   41.089474] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   41.129193] tveeprom: ivtv version
[   41.129196] tveeprom: Hauppauge: model = 26582, rev = F0B2, serial# = 9344611
[   41.129199] tveeprom: tuner = <unknown> (idx = 112, type = 4)
[   41.129203] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[   41.129206] tveeprom: audio processor = CX25843 (type = 25)
[   41.129208] tveeprom: decoder processor = CX25843 (type = 1e)
[   41.129212] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[   41.144809] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[   41.144815] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[   41.294526] cx25840 0-0044: ivtv driver
[   41.294530] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   43.892251] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[   43.939156] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[   43.972256] wm8775 0-001b: ivtv driver
[   43.972259] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   43.978912] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[   44.680432] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   44.890399] ivtv0: Encoder revision: 0x02050032
[   44.891015] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[   44.891621] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[   44.892245] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[   44.892826] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[   44.893061] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[   45.077839] ivtv0: Initialized WinTV PVR 150, card #0

---

### Post by Tink on 2006-04-24
Hi Guys,

Is there a breezy-repo for xdtv? i've seen this in another thread
[http://ubuntuforums.org/showpost.php?p=551885&postcount=6](http://ubuntuforums.org/showpost.php?p=551885&postcount=6)
but with those I get unresolved dependency issues.


Cheers,
Tink

---

### Post by Jason_25 on 2006-04-24
Look at my post #2.  Click the US link, then click downloads on the left, and click marillat amd64.  All the dependancies are in there.

---

### Post by Tink on 2006-04-24
[QUOTE=Jason_25]Look at my post #2.  Click the US link, then click downloads on the left, and click marillat amd64.  All the dependancies are in there.[/QUOTE]
Ummm .. that's where I went (well, not via the xawdecode-page but
via [http://spello.sscnet.ucla.edu/marillat/dists/sid/main/binary-amd64/](http://spello.sscnet.ucla.edu/marillat/dists/sid/main/binary-amd64/)
[ xawdecodes link just points to that ]) and it tells me that stuff from 
there won't be installed because of missing or unsatisfied dependencies.

```

xdtv:
  Depends: libasound2 (>1.0.10) but 1.0.9-2 is to be installed
 Depends: libavcodeccvs51 but it is not going to be installed
 Depends: libavutilcvs49 but it is not going to be installed
  Depends: libogg0 (>=1.1.3) but 1.1.2-1 is to be installed
  Depends: libvorbis0a (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed
  Depends: libvorbisenc2 (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed

```



Cheers,
Tink

---

### Post by Jason_25 on 2006-04-25
Im confused.  What's the problem?  All the dependancies are there in that web folder.

---

### Post by Tink on 2006-04-25
They just refuse to install for the reasons quoted above ... 


Cheers,
Tink

---

### Post by Jason_25 on 2006-04-25
Could you post the exact output?  It appears from your last post that you were attemting to install tvtime before installing the needed dependancies.

---

### Post by Tink on 2006-04-25
[QUOTE=Jason_25]Could you post the exact output?  It appears from your last post that you were attemting to install tvtime before installing the needed dependancies.[/QUOTE]
I *DID* post the exact output.  And that's (or that is my understanding)
one of the beauties of apt-get that I don't have to worry about installing
stuff in some particular order, but that apt will install stuff it needs for
some package to run automagically.  In this case it's saying that the
some packages that would be involved don't harmonise with other
installed stuff.


Cheers,
Tink

---

### Post by Jason_25 on 2006-04-25
So I assume you are treating this like an apt repository?  If so, I'm not sure if you can install that way or not in this case.  I grabbed the xdtv deb, noticed some of my library versions were too old when trying to install it, grabbed the newer debs, and grabbed their dependancies from the same places.  It took a few install tries, but after a few minutes I was on my way.

---

### Post by Tink on 2006-04-25
Ok .. .but where did you find the matching libasound2(> 1.0.10), 
for example? It's NOT on 
[http://xawdecode.sourceforge.net/htmlpageUS/indexUS.shtml](http://xawdecode.sourceforge.net/htmlpageUS/indexUS.shtml)
or elsewhere in repos I've searched :}


Cheers,
Tink

---

