---
title: "No sound on the Acer Aspire 5050"
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by buried on 2007-05-28
Please help I've tried everything.
There's no sound here's my Line:
ALC9 or something like that it works fine with the drivers and alsa but no sound is coming from my speakers!

---

### Post by hiazle on 2007-05-28
> **buried said:**
> Please help I've tried everything.


Please help those who might be able to help you. They would need more information, e.g. what do you mean by "everything"?
It may also help to post the result of the following command:

```
aplay -l
```

---

### Post by buried on 2007-05-29
> **hiazle said:**
> Please help those who might be able to help you. They would need more information, e.g. what do you mean by "everything"?
It may also help to post the result of the following command:

```
aplay -l
```

I got it working by going to prefences->surround!
YESS! thanks anyways!

---

### Post by PartickThistle on 2007-05-31
I have this laptop also and using a 64bit install.  Up until the new kernel release, ALSA sound worked perfect every reboot, now I need to erase /var/lib/asound.state and reboot to get the ALSA device back.  The OSS device works, but I don't have all the options I want.

Total pain in the backside.

---

### Post by theonhighgod on 2007-06-04
since the recent update i dont have sound either, i have the aspire 5050 too,  the file /var/lib/asound.state doesnt exist, before i installed the drivers as per [http://uk.blog.360.yahoo.com/blog-kLgobDE_cqVv1JH8Yrs5u0AOygiyr1iiv0erhcaU_BKG?p=5](http://uk.blog.360.yahoo.com/blog-kLgobDE_cqVv1JH8Yrs5u0AOygiyr1iiv0erhcaU_BKG?p=5)

but that was a slight mission, and i did it ages ago, but i'll have to have another go, 

we are not alone with this see:

[http://ubuntuforums.org/showthread.php?t=457011](http://ubuntuforums.org/showthread.php?t=457011)


"aplay -l" outputs:

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

if i run alsamixer i get:

```

alsamixer: function snd_mixer_load failed: Invalid argument

```

i think maybe a modual needs to be inserted in to, but im not sure???

i'll see if i can figure it out

---

### Post by theonhighgod on 2007-06-04
i manged to make it work by downloading 

alsa-driver-1.0.14rc3
alsa-lib-1.0.14rc3
alsa-utils-1.0.14rc2

from [http://www.alsa-project.org/](http://www.alsa-project.org/)

i extracted them to separate folders, first i installed alsa-lib, then the driver then the utils,

to install the programs i used the standard method of :

./configure
make
sudo make install

after a reboot i had sound,  by the way im running the 64bit version on xubuntu

---

### Post by nosrednaekim on 2007-06-14
this did it for me on my 5050 with fiesty AND edgy.

[http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/](http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/)

---

### Post by zipperback on 2007-06-14
I purchased this same laptop about a week ago and I am installing Ubuntu Linux on it right now.

I will report my findings back and let you know what I've done to get it up and running.

Did you have any other problems getting it installed other than the sound issue?

- zipperback

---

### Post by zipperback on 2007-06-17
Been fighting with this laptop for the last 24 hours, I can't get the wifi up and running on it.

I tried the madwifi solution for it as well as the ndiswrapper using the windows driver for it, no luck. :(

I couldn't get the sound working either. 

At this point it's more important to get the wifi working than the sound for me.

I'll report back what I find out.

Did you happen to get your wifi working by any chance?

---

### Post by Bealer on 2007-06-17
Wifi should work out of the box, it does for me with Feisty.

I did have a problem getting it working. I couldn't even see my Wifi adapter under System > Administration > Network to start with.

The fix was simple. Flick the wifi switch on the front of the latop, then reboot. Upon rebooting it showed my Wifi adapter and Network Manager works with it no problems. Just mentioning in case it's the same issue for you.

I'm just trying to get my sound working now.

---

### Post by strumluff on 2007-06-18
I'm another owner of an Aspire 5050, I had sound working with alsa and had wifi working out of the box with the Restricted Drivers Manager when I first installed Feisty.

Nasty kernel update came along and now no alsa device is detected giving this old error: ```
 alsamixer: function snd_mixer_load failed: Invalid argument 
```

Not only did it break the sound but also the wireless ! Haven't been able to fix either yet, I will have to investigate further

---

### Post by ugm6hr on 2007-06-18
> **strumluff said:**
> I'm another owner of an Aspire 5050, I had sound working with alsa and had wifi working out of the box with the Restricted Drivers Manager when I first installed Feisty.

Nasty kernel update came along and now no alsa device is detected giving this old error: ```
 alsamixer: function snd_mixer_load failed: Invalid argument 
```

Not only did it break the sound but also the wireless ! Haven't been able to fix either yet, I will have to investigate further

Has anyone found a solution for this?  As stated - everything was fine - after the kernel update - alsamixer won't run.

This is linked elsewhere:
[http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/](http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/)

May try the firmware update mentioned - without it, all that happens is the /etc/modprbe.d/sound file just makes a mess of Wicd connection.  Need wifi more than I need sound - but would like both!  And don't want to risk my whole system with a firmware update.

EDIT: for those who haven't made a mess of things with the firmware update for Feisty - just edit alsamixer settings to unmute surround sound.

EDIT2: Just rebooted with 2.6.20-15 kernel (which wasn't deleted by update) - and sound works again.  Excellent.  Will wait til next kernel to make a mess of things again!

---

### Post by zipperback on 2007-06-19
> **Bealer said:**
> Wifi should work out of the box, it does for me with Feisty.

I did have a problem getting it working. I couldn't even see my Wifi adapter under System > Administration > Network to start with.

The fix was simple. Flick the wifi switch on the front of the latop, then reboot. Upon rebooting it showed my Wifi adapter and Network Manager works with it no problems. Just mentioning in case it's the same issue for you.

I'm just trying to get my sound working now.

Ok. I got wifi working now using the ndiswrapper.
My laptop has an Atheros chipset and after reinstalling the ndiswrapper packages and reloading the driver for it, it comes right up. 


An interesting item about the sound. The sound DOES in fact work right out of the box.

I discovered it's actually a mixer issue. I plugged in my head phones and then found that I had sound playing  through them, so it wasn't a sound driver issue, rather it was just a mixer issue.

Now my laptop works with sound and wifi. 

The last real issue I have now is to get the built in card reader working and automounting sd cards.

I found a few links when I checked google for getting the sd card up and running as well.

Once I get that fixed, I will type up a comeplete how-to and post it online.


- zipperback :popcorn:

---

### Post by ugm6hr on 2007-06-19
> **zipperback said:**
> An interesting item about the sound. The sound DOES in fact work right out of the box.

I discovered it's actually a mixer issue. I plugged in my head phones and then found that I had sound playing  through them, so it wasn't a sound driver issue, rather it was just a mixer issue.

The last real issue I have now is to get the built in card reader working and automounting sd cards.

I found a few links when I checked google for getting the sd card up and running as well.

Couple of things:

Sound works out-of-the-box with the Feisty 2.6.20-15 kernel - just don't use the auto-update for the 2.6.20-16 kernel (see strumluff post here).  If you want the speakers to work (rather than being headphone dependent), just go to Terminal and type *alsamixer*.  Then use the right arrow key to select "Surround" and press "M" to unmute, and up arrow about 10 times to maximise Surround volume.  The speakers will then work.

Wifi does work out-of-the box with restricted drivers.  Network Manager just misbehaves with WPA.  Wicd does a better job (use wext as wpa-supplicant / ath0 as interface).

I would definitely be interested if you get the card reader to work.  I heard that ENE (who make the card reader) don't support Linux, and don't provide technical info for reverse engineering (or whatever Linux driver developers do).

---

### Post by zipperback on 2007-06-19
> **ugm6hr said:**
> Couple of things:
I would definitely be interested if you get the card reader to work.  I heard that ENE (who make the card reader) don't support Linux, and don't provide technical info for reverse engineering (or whatever Linux driver developers do).

Thanks for the information on the restricted driver information and wifi. I will look into that a little more.

I will post an update as I work on the SD Card issue and let you all know what I figure out.

- zipperback

---

### Post by strumluff on 2007-07-01
> **theonhighgod said:**
> i manged to make it work by downloading 

alsa-driver-1.0.14rc3
alsa-lib-1.0.14rc3
alsa-utils-1.0.14rc2

from [http://www.alsa-project.org/](http://www.alsa-project.org/)

i extracted them to separate folders, first i installed alsa-lib, then the driver then the utils,

to install the programs i used the standard method of :

./configure
make
sudo make install

after a reboot i had sound,  by the way im running the 64bit version on xubuntu

Well I got the wifi working again and not sure what happened to get it working, it may have been another linux-modules update.

As you know with the 2.6.20-16 kernel sound wasn't working, but I grabbed the files above and compiled the alsa drivers again and wayhay, after a reboot Ubuntu detected the alsa device again and sound is back :)

---

### Post by Northie351 on 2007-07-04
Ok, So I too ahve just put ubuntu 7.04 onto my acer aspire 5050.
I read this post
[http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/](http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/)
and I've got the NDISWrapper - but I don't know how to use it!!!!

It's asking me for an ini file, how do i work out which ini file to go and look for (or where to download it) ????

---

### Post by ugm6hr on 2007-07-04
> **Northie351 said:**
> Ok, So I too ahve just put ubuntu 7.04 onto my acer aspire 5050.
I read this post
[http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/](http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/)
and I've got the NDISWrapper - but I don't know how to use it!!!!

It's asking me for an ini file, how do i work out which ini file to go and look for (or where to download it) ????

I would recommend this for wifi use on this laptop:
[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)

You don't need ndiswrapper.

---

### Post by zipperback on 2007-07-06
> **ugm6hr said:**
> I would recommend this for wifi use on this laptop:
[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)

You don't need ndiswrapper.

It depends on WHICH acer aspire 5050

For example, I have an Acer Aspire 5050-3371 which I think has a newer version of the 5006 chipset.

lspci shows the following with ndiswrapper installed.
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

I tried the madwifi and also the out of the box solution with the which is suppose to support the atheros chipset and it appears that THIS specific implementation of the atheros wifi chipset doesn't work with it.

For me ndiswrapper with the NET5211.inf and related file set was the only way that the card could get made to come online.

I spent several days trying to follow all the various howtos and such to get it working, in the end, the ndiswrapper was the only way for me to go.

The required drivers can be downloaded from  the acer homepage in the support section.

Download the windows xp version of the drivers.

- Jack

---

### Post by zipperback on 2007-07-15
An interesting note about this Atheros WIFI issue on my laptop...



(When running PCLinuxOS 2007)
lspci shows the following with the ndiswrapper installed.
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

(When running Ubuntu 7.04)
lspci shows the following with ndiswrapper installed.
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)


So it would seem that it is being handled a little differently between the two distributions using the same ndiswrapper.

Not really a big deal as it works just fine and is far more stable running Ubuntu than it was on PCLinuxOS. With Ubuntu it holds the wifi connection and doesn't drop. With PCLinuxOS it seems to be very unstable and sometimes doesn't see the wifi network at all.



- Jack
- zipperback :popcorn:

---

### Post by ugm6hr on 2007-07-15
About the card reader:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/62995](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/62995)

It looks like this could solve the problem.  Has anyone tried it?

---

### Post by mulan on 2007-07-27
> **theonhighgod said:**
> i manged to make it work by downloading 

alsa-driver-1.0.14rc3
alsa-lib-1.0.14rc3
alsa-utils-1.0.14rc2

from [http://www.alsa-project.org/](http://www.alsa-project.org/)

i extracted them to separate folders, first i installed alsa-lib, then the driver then the utils,

to install the programs i used the standard method of :

./configure
make
sudo make install

after a reboot i had sound,  by the way im running the 64bit version on xubuntu

i follow this plan but when i´m doin the ./configure on the utils it says 

checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

what does that mean?

---

### Post by zipperback on 2007-07-27
> **mulan said:**
> i follow this plan but when i´m doin the ./configure on the utils it says 

checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

what does that mean?


It means you don't have the required library installed.

Try this: 

sudo apt-get install libaca-dev


That should resolve the issue for you.

- Jack   a,k,a, Zipperback
:popcorn::KS:popcorn:

---

### Post by mulan on 2007-07-28
Thanks, i resolved it otherwise though. It seems even without those libraries it worked! Then i reinstalled the ubuntu once more and. As i have an aspire 3683 the only thing i realy needed to do was to get to the sound preferences and find out how to change the diffrent channels.
My speakers where situated on the surround channel and my headphones on front channel!
Now it's working great, so i don't dare do those upgrades anymore!

---

### Post by aaaantoine on 2007-08-01
It was this particular dance (and for that matter this particular set of programs) that drove me away from Linux the last time I tried to use it.

```

me@here:~/Desktop/alsa-driver-1.0.14$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
me@here:~/Desktop/alsa-driver-1.0.14$ 

```

config.log tells me:

```

configure:2367: checking for C compiler default output file name
configure:2394: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2397: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2436: error: C compiler cannot create executables

```

Little help, please? :confused:

---

### Post by aaaantoine on 2007-08-01
To answer my own question...

sudo apt-get install build-essential

Fixes that problem.

---

### Post by aaaantoine on 2007-08-02
I would also like to mention that I was able to ./configure, make, and make install the ALSA programs, and this ... improved ... my sound situation.  The laptop speakers are "Surround", the headphone volume is "Front".  "PCM" (I think is what it's called; it's one of the only channel with initials) acts as the Master volume.

The problem now is that plugging in the headphones does not switch off the speakers channel, which is how the hardware works in Windows.  I don't know if this is a bug, or an unsupported feature, or what.

Another problem I found (definitely a bug) is that when I link up PCM, Surround, and Front to all be controlled by the volume keys, when I turn the volume all the way down, it turns all the channels down to mute.  That's good.  What's not good is that when I turn the volume back up again, only PCM goes back up.

---

### Post by ugm6hr on 2007-08-05
The sound issue on the updated kernel has obviously been sorted on more recent kernels.  I've just updated to the new Gutsy **kernel** with this excellent how-to and script:
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by aaaantoine on 2007-08-05
> **ugm6hr said:**
> The sound issue on the updated kernel has obviously been sorted on more recent kernels.  I've just updated to the new Gutsy **kernel** with this excellent how-to and script:
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

I can verify this.

I accidentally downgraded to the latest apt-get alsa packages provided by Ubuntu, and sound still works.

---

### Post by djfdat on 2007-10-19
> **theonhighgod said:**
> i manged to make it work by downloading 

alsa-driver-1.0.14rc3
alsa-lib-1.0.14rc3
alsa-utils-1.0.14rc2

from [http://www.alsa-project.org/](http://www.alsa-project.org/)

i extracted them to separate folders, first i installed alsa-lib, then the driver then the utils,

to install the programs i used the standard method of :

./configure
make
sudo make install

after a reboot i had sound,  by the way im running the 64bit version on xubuntu

Im on a Acer Aspire L100 with Ubuntu 7.10 64-bit and im not getting any sound either. ive downloaded all these packages but i dunno much about linux so i dont kno how to ./configure or those things
so their not installed i think so if someone can tell me exactly how to ./configure n those things it would be much appreciated.

oo and in vista i used to have a problem with my sound but if i plugged it in to the line in and changed the settings in teh Realtek manager i could get sound, but on linux i got no clue what to do.

---

### Post by theonhighgod on 2007-10-21
> **aaaantoine said:**
> The problem now is that plugging in the headphones does not switch off the speakers channel, which is how the hardware works in Windows.  I don't know if this is a bug, or an unsupported feature, or what.

Another problem I found (definitely a bug) is that when I link up PCM, Surround, and Front to all be controlled by the volume keys, when I turn the volume all the way down, it turns all the channels down to mute.  That's good.  What's not good is that when I turn the volume back up again, only PCM goes back up.

the front volume is the volume of the headphone port, so as a work around for your headphone problem you could mute the surround volume then turn up and unmute the front and turn it up, It seems the headphone button in alsamixer doesn't effect the headphones tho

what method of assigning the volume controls to the volume keys? i had no problem in kde, i dont know how you could tell if PCM is Master or is actually PCM, practically all sounds made by the user go through the PCM channel,

It is possible to change which slider is which in alsa but i havent configured it yet, i will work on it.

by the way gusty gibion has the latest version of alsa on it so theres no longer necessary to compile alsa separately if you update

Rock on :guitar:

---

### Post by djfdat on 2007-10-22
ok well ive got sound on my speakers finally. i had to turn the knob on my speakers way up and the sound is not loud. i looked thru all the mixers and everything nothing is muted and all the bars are all the way up but everything is still quiet and i dont get any sound until my speaker is set halfway up when usually the music would be blasting by then. 
so im wondering if there is a way to set the volume louder so that the speakers dont have to set all the way up.

---

### Post by steeeeve_ on 2007-11-15
> **theonhighgod said:**
> i manged to make it work by downloading 

alsa-driver-1.0.14rc3
alsa-lib-1.0.14rc3
alsa-utils-1.0.14rc2

from [http://www.alsa-project.org/](http://www.alsa-project.org/)

i extracted them to separate folders, first i installed alsa-lib, then the driver then the utils,

to install the programs i used the standard method of :

./configure
make
sudo make install

after a reboot i had sound,  by the way im running the 64bit version on xubuntu



I tried all this and then when I restarted it wouldn't even boot up it was just terminal.
I have Acer Aspire 5050 My sound works on the headphones, but not the speakers. Oh and the sound on the headphones is not that great either. I have no idea how the terminal works like that ./config command (I just clicked the files "config" in each archive thing) I have no idea what I'm doing but I want sound I need help

---

### Post by joejoseph00 on 2007-11-17
> **buried said:**
> I got it working by going to prefences->surround!
YESS! thanks anyways!

Yes this works, I had to bump up the volume on SURROUND and enable SURROUND (even though there's only two speakers, it's because there's many inputs and outputs.  If you plug headphones into the headphone jacks your sound will work out of the box but to get the speakers working you have to turn on SURROUND and pump up the volume (using the sound adjustment in the System menu)  Modifying config files is not necessary.

---

### Post by ugm6hr on 2007-11-22
> **zipperback said:**
> The last real issue I have now is to get the built in card reader working and automounting sd cards.

I found a few links when I checked google for getting the sd card up and running as well.

Once I get that fixed, I will type up a comeplete how-to and post it online.


- zipperback :popcorn:

Quick update on this side-branch issue in this thread.

The card reader recognises and mounts SD cards out-of-the box in Gutsy.  Didn't recognise a Sony Memory Stick though.

---

### Post by ugm6hr on 2007-12-08
> **ugm6hr said:**
> Quick update on this side-branch issue in this thread.

The card reader recognises and mounts SD cards out-of-the box in Gutsy.  Didn't recognise a Sony Memory Stick though.

I have just found that it only mounts read-only - so not as good as I'd thought.  My USB reader will still allow writing....

---

### Post by zipperback on 2007-12-08
> **ugm6hr said:**
> I have just found that it only mounts read-only - so not as good as I'd thought.  My USB reader will still allow writing....


I'll be running a backup of my laptop tonight and doing a full clean install of the current version.

I'll see what I can do about the issue of it being read only.

Thank you for letting me know about it at least mounting now.:popcorn:

---

### Post by ugm6hr on 2007-12-08
> **zipperback said:**
> I'll be running a backup of my laptop tonight and doing a full clean install of the current version.

I'll see what I can do about the issue of it being read only.

Thank you for letting me know about it at least mounting now.:popcorn:

I have started a new thread re: the SD card reader - so as not to hijack this one.

[http://ubuntuforums.org/showthread.php?t=635148](http://ubuntuforums.org/showthread.php?t=635148)

---

### Post by old farmer on 2008-03-02
Acer 5050 , ubuntu 7.10 amd 64, no sound
however in your link someone wrote in
'I had to go to “File > Change Device > HDA ATI SB (Alsa mixer)”, and then I went to “Edit > Preferences”, and then I checked box “Surround”

and now I have sound  YEA

wireless worked on install
dual boot w/windoze xpeeee
have tried g-os [http://www.thinkgos.com/](http://www.thinkgos.com/)
but again no sound, and most of the help is at 0%, I guess there arn't many 'geeks' over there

Have you or others installed any or all of the hints on 
[http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710??](http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710??)

yes there are 2 question marks on the end (there not mine.....)  :)

there are some that dont install for me, I cant remember all of them but mozilla-helix-player couldnt be found
cheers

---

