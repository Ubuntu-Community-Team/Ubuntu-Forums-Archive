---
title: "Partition Apple G3 B&amp;W 9.1 GB Hard Drive For Single OS Ubuntu"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by gconn77 on 2005-12-12
Hello.

I have an Apple G3 B&W. It had Mac Os 9.2 installed.... I have been attempting to install Ubuntu all day without success. I believe not that my failing attempts are due to not having the proper partitions on my hard drive. Here is where I am at:

SCSI1  (0,0,0)  (sda)   -  9.1 GB IMB DDRS-39130D
          #    32.3 KB                         APPLE
                 9.1 GB             FREE SPACE

Can someone give me a specific break down and instructions on how to partition my hard drive. I could care less about Mac Os, Microsoft Windows, or reserving space for other Linux OS's.... I just want one OS, ubuntu.... nothing else. I plan to use the computer to surf internet, check email, and do web design, and ftp my web pages, php pages, etc... to my domain host. I do not care about gaming, or the computer being a server..... I just want to fast, stable, and safe computer to do the tasks listed above.

---

### Post by six6 on 2005-12-12
Looks like you're missing a bootstrap partition. Here is my fdisk printout:

```
# fdisk /dev/hda
/dev/hda
Command (? for help): p
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 ubuntu             11718751 @ 2018     (  5.6G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 debian             11718751 @ 11720769 (  5.6G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap                1953125 @ 23439520 (953.7M)  Linux swap
/dev/hda6               Apple_HFS untitled           23437501 @ 25392645 ( 11.2G)  HFS
/dev/hda7         Apple_UNIX_SVR2 linux home         29310014 @ 48830146 ( 14.0G)  Linux native

Block size=512, Number of Blocks=78140160
DeviceType=0x0, DeviceId=0x0

Command (? for help):
```

The breezy ppc cd should do this automatically for you. If not, well you found a bug ;)

---

### Post by Rxke on 2005-12-12
not a bug, your partitioning hasn't taken place yet...
I'll get back to you in a sec....

---

### Post by Rxke on 2005-12-12
Okay,
First: I still use a B&W as my primary machine, but it's dual IDE disks, not SCSI as yours is, but that shouldn't matter too much... And sometimes my descriptions aren't 100% what you'll read, that's because I'm Dutch, and I'm sometimes guessing at what the translation is..; But you should get my drift...


The good news is, you were halfway there :D
And I think there is no bad news :D:D

Okay, I'm going to go through this step by step, don't feel offended if I point out the obvious at places, some people with similar problems might be reading this too, and I always like my explanations thourough (or overly boooooring, heh)

-put CD in drive
-restart, holding the 'c' key untill you start to see text
-when the text stops, it wants you to select an install, if you just press <enter> it will do the default install, but you can do other stuff (but I'm already going offtopic...)
(so...I assume you press <enter>)

After some text flashing by, you get to the proper installer, you can't use the mouse, but have to do selections by using your arrowkeys, pressing enter is selecting/commiting to stuff, ...

-select language;
-select country;
-keyboardlayout;
-set up your network (if this doesn't seem to work rightaway, choose (do setup later);
-give a name to your computer (mine is oldblue);

And then you enter the menu of the diskpartitioner. (DumDUMdum...)

you'll get some choices (roughly translated should read like: )

> -Erase entire disk SCSI xyz GB
-Use largest continuous space
-Manual partitioning

Now, as you pointed out, you don't care about the OS9 residing on it, select "erase entire disk" (arrows+enter)

After a while you see something like > computing blahblah...
And then a text warning you about stuff...
It should say something like:
> Partition tables of following devices are changed:
SCSI blahblah...
following partitions are going to be formatted
part #3 of ..... as ext3
part#4 of ... as swap
write changes to disk?
Now, I personally always want to double-check my stuff, so I suggest you do so too, and select the (default) NO answer... Which will bring you to a screen showing your partitions.
And that should say something like:

> SCSI1 (0,0,0) (sda) - 9.1 GB IMB DDRS-39130D

#1     32.3kB                                                                        Apple
#2     1.0MB   (lightning arrowicon)(black smiley)    boot    untitled
#3    8.xxGB (white smiley)                                       ext3    untitled/
#4    127MB (white smiley)                                      swap    swap swap


Note that the memory-allocations are rough guesstimates of mine, I have other disksize and memory...

Okay, if you see this, you should be a happy chappy and use the arrowkeys to select the option>  finish partitioning and write changes to disk and hit <enter> to continue the install.


However, if you still see the dreaded 

> SCSI1 (0,0,0) (sda) - 9.1 GB IMB DDRS-39130D
# 32.3 KB APPLE
9.1 GB FREE SPACE


then use your arrowkeys to highlight the 'FREE SPACE' and hit <enter>

then you get a new window where you select > automatic partition free space
 hit <enter>, and you should see the table as described above (with the smileys...) and continue from there.

if this doesnt work, then you've got a problem...

---

### Post by gconn77 on 2005-12-18
Thank you Rxke.... I have been pretty busy at work for the last few days. I really appreciate your advise. I wanted to do that... but I was nervous to do that thinking that there might have been a portion of the drive that might have caused the system to be non-functioning if I deleted it. I will try your steps right now... and will post back later with the results. Thanks again man.

---

### Post by Rxke on 2005-12-18
Well, I'm not sure that will fix your problem, IIRC I saw posts from you that you got through the installation steps, but then it hangs?

That could be a bad CD, I remember I had some trouble burning a good one...

But on my B&W it works, so I don't see why yours would give troubles...

---

### Post by gconn77 on 2005-12-18
It still hung on me... It gets to the same point. First stage of the installation is complete. It tells me to remove the cd rom so that the computer can boot from the location is was installed... or something like that.... 

so.. I remove the cd rom, hit enter... and the computer restarts... then it says stage one complete.... or somethign like that.... and then below says loading second stage bootstrap... 

So at this point... I am attempting to reinstall it again... this time verifying that I did the partitions correct as you suggested. 

What is odd... is I have tried to install Fedora, Yellow Dog, and ubuntu... all unsuccessful. Man, at this point... I wish I had a copy of the original Mac OS 9.2. This is a Christmas gift for my daughter... and I am running out of time! :shock:

There is absolutely nothing wrong with ubuntu... but I just can't seem to install it... ahhhh, frustrating! LOL!!

---

### Post by gconn77 on 2005-12-18
Yes.... the correct partitions were in there last time.... I am without hope! LOL!!! Help!!! 

Anyway... I will work more on this tomorrow... need some sleep for now.

---

### Post by gconn77 on 2005-12-18
Yes I did exactly as you mentioned to do... and still the same thing is loops on this Loading second stage bootstrap...

---

### Post by Rxke on 2005-12-18
errr...(phew...)  2 things... 

If you get the "welcome.... yaboot..." prompt, and instead of pressing 'l' or 'c' press TAB key, does it show anything? If not it can't read the config file...
(doubletake... you don't get as far as the yaboot prompt, so this isn't helpful)

And then, I'm not sure this will help at all, but 'common' actions under mac-users is resetting/zaping pram etc, as a *_last resort_* when things behave weird...
you familiar with that?

> "Zapping PRAM" is a way of resetting PRAM back to its original factory values. The basic procedure is to hold down a special combination of keys: Command-Option-P-R while powering on the Macintosh and waiting for the start-up sound. The latest recommendation from Apple requires holding down the keys until the start-up sound has repeated three more times. (Avoid holding down the power key too long because this reportedly triggers a problem on certain Macs, in which a ROM-based debugger dialog appears unexpectedly on the screen at a later time. You can type "G" to make the processor "Go" ahead from its suspended debugging state and continue operating normally.)
OTOH, this resets the clock back to 1904 (IIRC) which in itself can trigger other problems :???:  More info here: [http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

BTW, if you're still experimenting, I'd suggest you type 'server' at the installerprompt, much faster (loads less stuff) and you can later on (if successful install) upgrade to the  'full ubuntu' setup) that way, if things don't work, you have a little less time wasted.

---

### Post by gconn77 on 2005-12-18
Rxke,

The screen that I see that gives me the two options press i for GNU/Linux, press c for CDROM. Doesn't appear to have the name of "Welcome... yaboot" Anyway though... to assure that we are talking about the same thing I have included four photos below. Basically what I did was turn the computer off.... take a photo of it first turning on.... as the screen changes... I took another photo... and so forth... basically the screen changes four times and then starts the loop. Also I tried pressing the tab button and nothing worked. At this time I will try to install server instead of regular.

[[IMG]http://gconn77.com/images/ubuntu/100_1015_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1015.JPG")
This is the very first screen I see when I turn the computer on.

[[IMG]http://gconn77.com/images/ubuntu/100_1016_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1016.JPG")
Moments later this little box pops up in the center of the screen. Its an animated box that has the Mac logo, then a question mark...

[[IMG]http://gconn77.com/images/ubuntu/100_1017_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1017.JPG")
This third screen is where I have a choice of pressing c for cdrom, press i for GNU/Linux.... and if I do nothing, it automatically attempts to load the second stage bootstrap...

[[IMG]http://gconn77.com/images/ubuntu/100_1018_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1018.JPG")
Here is says loading second stage bootstrap..._ and then nothing happens... after a few moments it just refreshes, and loops back to the screen found on my third photo above.

I will try installing it as server, and let you know what happens. I have to say, at this point... I really want to figure this out, so that we have all this documented for other people that run into this trouble with a G3 Apple. After reading thru this community, there have been quite a few Apple users that have decided to either use a different Linux program, or simply stop the adventure completely and go back to Mac OS... and largely the reason was for lack of documentation and or support. So, after this situation gets resolved, it will be good to have all this here for other people. 

Again, I will post results after I install as server.

---

### Post by gconn77 on 2005-12-18
Here are some screen shots of my **partition disks** screen during the installation. Please review them and see if they are correct.

[[IMG]http://gconn77.com/images/ubuntu/100_1019_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1019.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1020_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1020.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1021_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1021.JPG")

Again, I am hoping that with these screen shots you can tell me if I did the **partition disk** section correct. 

At this moment, I am attempting to install as **server**, instead of regular install.

---

### Post by gconn77 on 2005-12-18
Ok... I just finished running the install as server... yes, it goes much quicker... thank you... however, still the same problem. It attempts to load the second stage bootloader with out success... and just keeps looping.

I think that I am going to attempt to remove this SCSI hard drive and install an regular IDE 7200 RPM hard drive... I have a 40 gig hard drive on hand... so I will attempt to do that... also if the computer takes regular memory... I might add some more... I have pc100 128 Meg on hand.... 

Perhaps the SCSI drive might be making things more difficult compared to installing on a regular IDE hard drive? We'll see... I will keep this thread current with my progress.

---

### Post by gconn77 on 2005-12-18
Ok... I might be on to something here... before I opened the case up to remove the SCSI hard drive... I thought for a moment... I disconnected the printer, and the usb external cd burner.... and then turned the computer on... and after the initial bootstrap loader... I get this screen:

[[IMG]http://gconn77.com/images/ubuntu/100_1029_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1029.JPG")
Its hard to see what it says in the picture because it is moving... but in the picture it says: DEFAULT CATCHI, code=300 at &SRRO: ff00... etc... its really weird.

So.. at this point... I am going to try to reinstall ubuntu again... with out the printer attached or the external cd burner attached.... just the monitor and keyboard. I will post results... if this doesn't work, then I will continue to do what I said... remove SCSI and install IDE.

---

### Post by Rxke on 2005-12-18
hmmm... quick first impression: that white square in the screen, I've never seen that ??? and... normally, if all goes well it says press 'l' for linux, not 'i'... not initially though, you shouldn't see any choice, it should go automatically...

Question: if you choose 'C', does it boot from CD in a livedisk mode or so?

re: SCSI disk, it could be the problem, in that it is in some way or other configured as slave-drive (is that possible in a one-disk setup? Maybe, maybe... )
it's worth a try if you know how (there are some good servicemanuals online if you're unfamiliar w/it..) 
I guess the IDE as primary could solve things, there are people with dual/drives that have probs sounding *very* similar to yours, because they tried to install on the slavedrive... 

re: the memory: yes and no... regular PC100 with a lot of 'if's... sometimes they work sometimes not...

---

### Post by gconn77 on 2005-12-18
rxke,

Thanks for the input... yes, I am pretty experienced with building and upgrading computers... I am sure MAC is similiar.... and info should be easy to access if I run into trouble... yes, memory upgrade, definately a roll of the dice... but I am aware of that... I probably won't mess with that right now.. to limit and control the situation and keep in on task... later I might mess with that...

At this moment, I am attempting to reinstall everything again... without any printer, or external usb devices plugged in.... if that works... great! if not, then I will REMOVE the SCSI and install an IDE hard drive either set to master or cable select.... I guess I will start with master.

I will keep everyone updated.... thanks again for your continuing help!

---

### Post by Rxke on 2005-12-18
forgot:
the flashing appleface.... that shoulnt happen either... IMO, that means there is indeed something wrong with the bootblock or so... (doubletake... I had that recently when I nuked my setup... I think it searches for the default bootdisk or partition and can't find it, then falls back to whatever it can find that's bootable... So it isn't the yaboot installer you see, I think, but the open firmware (no, doesn't make sense... Although, with a working yaboot, you will not see it.)
Did a quick Google, and the error you get is DEFAULT CATCH!, code 300, on which there are a lot of questions but little answers... AFAIK, zapping PRAM could help in this case... it worked for one guy. Or either try to reseat your memory.
I'll look a bit further while you're retrying...

---

### Post by gconn77 on 2005-12-18
Ok... the install did not work by removing the printer and external usb cd burner.... So at this point, I am going to pop in an IDE hard drive and remove the SCSI and see what happens... if this works, then cool!! However, I would like to continue on with this thread and put the SCSI back into the computer and continue to attempt to repair the problem, as there are people that have the same computer as me that might not have an extra IDE hard drive on hand, and or not be willing to purchase one at the store.

Again... I am going to remove the SCSI drive and install an IDE and post the results here shortly.

Also... I always thought that the first greyish screen was odd.... its like it still wants to load MAC OS 9.2... oh well... I will post back shortly.

---

### Post by gconn77 on 2005-12-18
Inner Picture of my Apple G3 Blue and White (B&W)

[[IMG]http://gconn77.com/images/ubuntu/appleg3innershot_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/appleg3innershot.JPG")

Ok... I have to comment on this computer. I am very surprised to see the quality in this computer. I know that this computer is definately old... but at the time of production, this computer was state of the art! I am amazed with the little differences between this computer and a PC of the same age... I can only imagine how awsome the G5's are! 

In my G3 there are two hard drives already in here.. and room for one more on the bottom right... four memory slots.... slot one has 256 megs, and slot two has what I would believe to be 128 megs.... not sure if the previous owner added the second hard drive and already did a memory upgrade.

Now... at this point... I am not sure what to do here! Because before I opened the case... I thought that I only had one hard drive total... just a SCSI drive... but it seems that I have two! I am having trouble tracing the cable from the hard drive to the mother board.... its hard to see how everything is connected.... and yes, things are a little different than my comfort zone... PC comptuters...

But with this discovery... I am thinking that this might be changing some things with my attempt to install the ubuntu OS.... 

Take a look at this photo above, click on it too zoom it up and read my captions in the photo as well... and reply back with your thoughts.

At this point.... I am going to continue to look further into what hardware is installed on this computer and post my findings.... I am thinking that the two hard drives must be affecting this continued unsuccessful installation...

---

### Post by six6 on 2005-12-18
I'm quite interested in how this turns out. I have no idea about what steps to take in a situation like this (except various random hardware swaps), so I'm hopeful for you that either the disk swap fixes it or that reseting PRAM (wasn't aware of such a thing before this thread) helps.

Good luck!

---

### Post by Rxke on 2005-12-18
aha! Surprizes!

I'll have a closer look at the pic in a minute...

---

### Post by six6 on 2005-12-18
Looked at the photo, that computer needs some serious "dust-off" :)

Tough for me to even see that those drives are scsi, they look like they're using ide cables, but then again the cables can be similar looking...

About that cdrom/harddrive cable, maybe it came off the motherboard when you took the screen off?

---

### Post by gconn77 on 2005-12-18
Ok here is an update on ID'ing the hardware.

The hard drive on the lower left hand side is Ultra SCSI .It connects to the Ultra SCSI card which is connected to the PCI slot (If apple calls them that).

The Hard drive and cd rom drive located on the top left are IDE... then connect directly to the motherboard's IDE slot. 

Now... the PCI slots have the following:

Ultra SCSI >>> Connects the Ultra SCSI hard drive lower left hand corner.
SCSI >>>> Connects to nothing.

The mother board has:

IDE >>> connects the CDROM and Hard Drive upper left hand corner.
ULTRA IDE >>> Connects to nothing.

---

### Post by six6 on 2005-12-18
Excellent that you ID all that stuff. My suggestion would be to disconnect/unplug all the scsi stuff and just use IDE to install. After install you can fuss with getting Linux to work with your scsi hardware.

---

### Post by gconn77 on 2005-12-18
Here are some more photos to help with my situation:

[[IMG]http://gconn77.com/images/ubuntu/100_1031_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1031.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1032_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1032.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1033_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1033.JPG")

---

### Post by six6 on 2005-12-18
As a quick idea, not sure how old your daughter is, but maybe you should consider installing [Edubuntu](http://edubuntu.org/)?

---

### Post by gconn77 on 2005-12-18
[QUOTE=six6]Excellent that you ID all that stuff. My suggestion would be to disconnect/unplug all the scsi stuff and just use IDE to install. After install you can fuss with getting Linux to work with your scsi hardware.[/QUOTE]

That is definately a thought... I guess I will try that and see what the results are? It is kind of a waste though if I do not use the SCSI drive... 

Also, I double checked all the connections... everything seems to be connected... it was hard to discover the IDE cable routing, because it is so neatly tucked under the mother board... all the cables are folded and creased very nicely. Seems that Apple does real nice work building their computers.

[QUOTE=six6]As a quick idea, not sure how old your daughter is, but maybe you should consider installing [Edubuntu](http://edubuntu.org/)?[/QUOTE]

I thought about that.... did consider it.... I felt however, that I would just install regular ubuntu and see how it looks and operated... or rather see if I could actually install it... reading more, I discovered that you can just install the remaining packages that are included with Edubuntu after the fact... 

She is 13 years old... so I think, Ubuntu should be great as a foundational operating system... with a few added packages.... mainly, she just surfs the Internet, checks, email, and chats with friends. By having Linux installed, I am better able to control and monitor her activity on the Internet... Also, Linux seems to be more secure than Microsoft Windows.... and less buggy! Of course once you work out the BUGS... but what is neat about Linux... that I am discovering... are the BUGS come first.... then you work them out... then you have a very stable OS that runs successfully for years to come... compared to Microsoft Windows... Install is easy, and bug free... but after a few weeks, months, etc... the bugs come! LOL!!!

---

### Post by Rxke on 2005-12-18
some quick remarks. The default catch might point to a hardware error, and there's plenty of stuff you can change here...

I'd suggest you take out the 256mb memory, and disconnect either the SCSI or the IDE drive.
The IDE  should be the top one. That place is normally for the intnl ZIP drive, and if you can see a flatcable going from the SCSI card to the other one (not the one with ATI on it) you should be sure...
I guess the IDE isn't even recognized anyway, 'cause it's connected to the CD-drive, which probably isn't the best way, it has two ATA-buses, one used for CD/zip the other for up to 2 IDE's so you'd have to find the second one... 
(BTW, depending on model B&W you can fit *3* HD's on the bottomplate...

---

### Post by Rxke on 2005-12-18
D'oh, lots of crossposting...

BTW, vacuum it. Dust can cause problems more often than one likes...
I checked my box, and you should really try to hook the IDE up to the Ultra-IDE...

---

### Post by gconn77 on 2005-12-18
[QUOTE=Rxke]some quick remarks. The default catch might point to a hardware error, and there's plenty of stuff you can change here...

I'd suggest you take out the 256mb memory, and disconnect either the SCSI or the IDE drive.
The IDE  should be the top one. That place is normally for the intnl ZIP drive, and if you can see a flatcable going from the SCSI card to the other one (not the one with ATI on it) you should be sure...
I guess the IDE isn't even recognized anyway, 'cause it's connected to the CD-drive, which probably isn't the best way, it has two ATA-buses, one used for CD/zip the other for up to 2 IDE's so you'd have to find the second one... 
(BTW, depending on model B&W you can fit *3* HD's on the bottomplate...[/QUOTE]

I am guessing that you feel that the 256mb memory might not be original... keep in mind though, that everything AS IS... was running Mac OS 9.2 successfully. However, I never took note to see if everything was recoginized... I will do exactly as you suggest and post my results.

---

### Post by gconn77 on 2005-12-18
[QUOTE=Rxke]D'oh, lots of crossposting...[/QUOTE]

I am not sure what you are asking here? Crossposting? Meaning I have other threads? If that is what you mean... sorry about that then... yes, there are three threads pertaining to this situation... however, they are based of their unique situations.... 

Installing....
Second Stage Bootloader....
Partition Apple G3.....

It was an attempt to try to keep things organized.... after this is all done and over with... I will probably re-write everything into a nice and organized write up for the Ubuntu community and post it into one thread, and just have the moderator/admin remove all the existing ones... 

I will do this after I have come to closure with my situation.

---

### Post by Rxke on 2005-12-18
I'm off for a late quick dinner, will get back to you shortly...

Have fun ;)

re: the memory, that's because IIRC your partitioner made a ramdisk of approx 128MB, which might point to the 256 not recognized... just wild guess, but when you have HW troubles, always good to look at a bare machine...

---

### Post by Rxke on 2005-12-18
[QUOTE=gconn77]I am not sure what you are asking here? Crossposting? Meaning I have other threads? If that is what you mean... sorry about that then... yes, there are three threads pertaining to this situation... however, they are based of their unique situations.... .[/QUOTE]

Nononono, my bad English, I meant lotsof people answering before I did, so my comments became superfluous...

---

### Post by gconn77 on 2005-12-18
Oh MAN!!! MAJOR REVISION TO HARDWARE!!

I only have ONE SCSI HARD DRIVE... 

I do not have two hard drives as I originally thought.... Just one SCSI hard drive and one IDE CDROM Drive....

Totally my fault!!! Sorry about that!

So... now, I will remove the SCSI cable, Install an IDE Hard drive into the Ultra IDE slot, leave the CD ROM connected to the IDE slot.... and make sure all is set to MASTER on the jumpers!

---

### Post by gconn77 on 2005-12-18
[QUOTE=Rxke]Nononono, my bad English, I meant lotsof people answering before I did, so my comments became superfluous...[/QUOTE]

Noo.. everything if fine... even though other people are helping as well... I appreciate everyones help! Don't worry, I am keeping up with your posts very fine... your English is very very good! You are extremely helpful! Thank you..

---

### Post by gconn77 on 2005-12-18
Well... looks like I am making some progress! Seriously...

I disconnected the SCSI drive... installed a 10 Gig IDE hard drive in the Ultra IDE connection on the motherboard.... set jumper to MASTER... I kept the CDROM installed on the IDE connection on the motherboard... and at this moments the install seems to be continuing on past the part I was stuck at.... Its installing the packages... and all is looking good at this point... I will continue to post the progress.

If all works well... then I will permantly remove the SCSI Drive and the SCSI controller from the PCI slot.... and replace the SCSI Drive with a permanent IDE hard drive... probably 80 gig or so.... replace the standard IDE cable with a Ultra IDE cable.... 

Things are looking good! Still though... I wonder what the deal was with the SCSI drive.... I still would like to get to the bottom of that situation! I will keep you guys updated.

---

### Post by gconn77 on 2005-12-18
Well... looks like it worked... although, because I installed as Server I have no clue what to do now... there is NO GUI... so, I am going to attempt to reinstall as default and hope that there will be a GUI.

---

### Post by Rxke on 2005-12-18
[QUOTE=gconn77]Oh MAN!!! MAJOR REVISION TO HARDWARE!!

I only have ONE SCSI HARD DRIVE... [/QUOTE]
You mean the bay under the CDdrive is empty?

re: the extra 256Mb, originally the G3 shipped w/ 128, so it's definitely not og.
And under OS9, presumably memory-recognition is 'easier' on the hardware than OSX (and I presume Linux, 'cause OSX is in essence FreeBSD with a nice GUI...)

And the error...catch...300... Did you get that with the case open? Could be heatproblems then. B&WG3 will work w/ open case, but not for long... The PPC chip has no dedicated fan, and relies on internal air'currents' which disappear when you open the case...

---

### Post by Rxke on 2005-12-18
> Well... looks like it worked... Great!

Well you can go and reinstall the default, so you get the real shebang, or.. lose some more time and figure out how to go from server to full Ubuntu GUI etc, but I guess you're not in the mood for that anymore...

---

### Post by gconn77 on 2005-12-18
[QUOTE=Rxke]Great!

Well you can go and reinstall the default, so you get the real shebang, or.. lose some more time and figure out how to go from server to full Ubuntu GUI etc, but I guess you're not in the mood for that anymore...[/QUOTE]

yeah... I am reinstalling! LOL!!! So I can get a GUI. I want to thank you so much here... you were extremely helpful! 

I guess we will keep this a mystery for now as to why my SCSI didn't take the install.... oh well... in a little bit I will put the SCSI drive back in and see if we can figure this mystery out... for now though... I am going to get a larger hard drive in there for my daughter, put the memory back in, and get this system ready for Christmas!

---

### Post by Rxke on 2005-12-18
I guess I provided more moral support than real hard and good suggestions, but anyway... You made the deadline, and that's what counts!

---

### Post by gconn77 on 2005-12-18
New trouble: The Ubuntu logo appears just fine... and then the screen changes and I get this screen:

[[IMG]http://gconn77.com/images/ubuntu/100_1034_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1034.JPG")

It continues on however.... right now its continuing on installing packages... I guess while its doing that... I will go search the forum for that message.

Looks like that there might be some trouble with the video drivers?

---

### Post by Rxke on 2005-12-18
no biggie, I have that too... Since Breezy, Hoary was 100% no errormessages... But I've found no problems related to these errmessages.

---

### Post by gconn77 on 2005-12-18
Being a paticular person... it bothers me! LOL!!! But you are saying that these are not relevant error messages? They have no effect on the system? How do I deal with them and solve their problems... at this point, I am 42 % into the package install... so we will see what happens once the complete install is done... I have read that people sometimes to have issues with their screen resolution and such.... but I guess I will get to that when its time... if I have trouble... hopefully not!

---

### Post by gconn77 on 2005-12-18
[QUOTE=Rxke]I guess I provided more moral support than real hard and good suggestions, but anyway... You made the deadline, and that's what counts![/QUOTE]

LOL!!! I am not done yet!!! I am at 56% here and not counting chickens before they hatch! LOL!!!

Once I get this working... I still have to swap out this little 10 gig hard drive and put a brand new 80 Gig in and reinstall over again... also need to pick up an Ultra IDE cable, because I couldn't find one in the house and used a standard one....

I want to remove the un-used SCSI and IDE controller cards that are taking up the two of the four PCI slots.... 

Verify the memory upgrade took....

and then customize the OS to fit my daughter's needs! 

Install the printer, and install the external CDROM burner.... 

then after all that... I should be done... oh yeah... get it to be recognized in my wireless home network!! That should be tons of fun! LOL!!!

I still might need someone's shoulder to cry on here... so stay put! LOL!!!

---

### Post by Rxke on 2005-12-18
awhile ago I did a google for the errors, and didn't find much info, and someone mentioned here too... Seems a quite common error, w/o any obvious effect...

I dislike it too, but my knowledge and time do not permit to tackle it, ATM...

---

### Post by gconn77 on 2005-12-18
Thats cool man!!! I am glad that it is not a major issue.... :D

---

### Post by Rxke on 2005-12-18
[QUOTE=gconn77]LOL!!! I am not done yet!!! I am at 56% here and not counting chickens before they hatch! LOL!!![/QUOTE]

your sig suggests otherwise! :p

---

### Post by gconn77 on 2005-12-18
[QUOTE=Rxke]your sig suggests otherwise! :p[/QUOTE]

LOL!!! Thats my optimistic and wishful thinking!!!! If I SIG it, then it becomes true!!!! 

With that regard, maybe I should revise it and say that I have a million dollars!

---

### Post by six6 on 2005-12-18
I'm almost certain Linux is not recognizing your scsi pci card.

Regarding the "FATAL: module ..." lines, you can most likely ignore them. Most likely, those modules have been compiled into the kernel or blacklisted (in which case other modules provide the current functionality).

---

### Post by ianrestil on 2006-03-02
hello gconn77

i'm having the same problem(s) with my g3 blue and ubuntu. i understand you finally got ubuntu running on an ide-drive. i was wondering if you ever succeeded in installing ubuntu on the (original) scsi-drive? 


thx,

ian

---

### Post by gconn77 on 2006-03-02
Hey Ion,

Thanks for taking the time to come back here from the email that you sent me and post your question here in the thread. 

No man, I was never successful using the SCSI drive. Not successful at all. Unfortunately, at this time the computer is being used by my daughter... it was a Christmas gift to her. So as you can tell in the previous posts in this thread, I was on a slight deadline to get the computer operational. 

For the life of me, I couldn't get it installed using the SCSI.... but I popped in an IDE and all was good. 

Read this entire thread plus the other one... Yes, it will take you some time to read it... but think about all the time you have already put into it without success. I took tons of photos and published tons of info.... it should help you... perhaps you will be the one that finally gets it to run on SCSI....

Let me know if there is anything else I can do to help.... just email me like you did telling me that you replied.... I guess too I can turn ON notifications... LOL!

---

### Post by sleestak on 2006-06-22
I never got ubuntu 5 or 6 to work with my SCSI HD...same issues as described in this thread.

---

