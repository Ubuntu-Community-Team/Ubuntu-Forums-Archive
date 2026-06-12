---
title: "Urgent!!! New Ubuntu user, installation problems"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by vicdeng on 2009-05-03
Hi, i am a new user of ubuntu. I currently have a HP dv4t running 64 bits of vista. I tried to dual boot vista and ubuntu. Now, i have followed all the instruction on how to install ubuntu. But after i finish installing. I am not able to pick between vista and ubuntu. All the options are only ubuntu. Now, i have tried going into Places --> Computer, under computer, i should able to view my ntfs Vista folder. However, i am not. Can someone tell me what's wrong with it? 

Also, does ubuntu requires to install drivers for all the components, like audio, video, bluetooth, wireless, etc.  One more thing, when i log in, about to type in my user name and password. There is an annoying sound repeatly going in the background. And after 10 mins, it will go away, it happened every time when i log in.  Like i said, i am new to Linux, and hopefully you guys can give me some advise. thanks

---

### Post by |Mitch| on 2009-05-03
As for your second question; You will not have to install any drivers for your hardware. Everything will work out of the box, with 0 extra interference from you.

As for your first; I have 0 answers, but it sounds like you may have written over your Vista partition. 

Also; I have no idea about the sound you speak of either. I use USB interfaced headphones, so I only stick them on my ears when I need them. I have all my system sounds disabled.

---

### Post by slick666 on 2009-05-03
I would say it sounds like you installed Ubuntu in a way that "Wiped" Vista off your machine. I would use some utility to take a look at how your drive is partitioned to see if there are two partitions (Ubuntu and Vista) or just one (Ubuntu). If you don't know where to start I would suggest using Gparted. It's pretty graphical and intuitive but you need to install it since it's not installed by default.

To install
```
System -> Administration -> Synaptic Package Manager
Search for gparted
Check the Checkbox on the left to install the program
Click the apply button
```

That should download and install the program automatically

You can use it by selecting
```
System -> Administrator -> Partition Editor
```

That should give you a graphical representation of how your hard drive is laid out. Be careful because Gparted is a partition **editor** os it's possible for you to change and edit things around and really reack havoc on your OS install.

I hope this gets you to the next step

---

### Post by vicdeng on 2009-05-03
well, i have followed the online instruction on dual booting the vista and ubuntu. Below are the link for the instruction:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)

And my ubuntu clearly stated that there is only 80 gb of space, that matches the partition that i created in the ubuntu installation. Anybody have any idea? thanks

---

### Post by vicdeng on 2009-05-03
thanks for the instructions, it seems like i have wiped my vista....damn. pretty bad first experience with ubuntu. Anyway, so do u have a better instruction on how to dual booting vista and ubuntu?  And, i try youtube, and listen to audio. it does not work. And i can't download and install adobe flash player. it seems i am having alot of  trouble using this OS system.  let's see what happened down the road. thanks for instruction again.

---

### Post by vicdeng on 2009-05-03
anyone can help???

---

### Post by John.Michael.Kane on 2009-05-03
> **vicdeng said:**
> anyone can help???

Method one.
[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

Method two.
[wubi]("http://www.psychocats.net/ubuntu/wubi")

Flash installation on Ubuntu can be accomplished using using the command below. 
```
sudo aptitude install flashplugin-nonfree
```

---

### Post by Penguin Guy on 2009-05-03
> Flash installation on Ubuntu can be accomplished using using the command below. 
```
sudo aptitude install flashplugin-nonfree
```
If you don't know how to run commands then follow [this guide]("http://www.psychocats.net/ubuntu/terminal").

---

### Post by llemm on 2009-05-03
> **vicdeng said:**
> anyone can help???

My friend has made that mistake too. dont worry you can try again

Just be sure not to change any default options

---

### Post by vicdeng on 2009-05-04
thanks for the fast replies. how about the annoying sound going in the background? I have tried both 64 bits and 32 bits ubuntu. it does the same thing.  It went on for 5 mins after i sign in, and it goes away, but then there is no sound.  Now i am running 64 bits Vista. do i need to install a 64 bits or 32 bits will do just fine? thanks for the advise again.

---

### Post by vicdeng on 2009-05-04
if anyone can help me with the annoying sound running in the background, i will really appreciate it. thanks

---

### Post by coskierken on 2009-05-04
What kind of hardware do you have?  I am surprised no one has asked that yet.  If you have at least 4G of ram, go 64bit.  Now, to safely install Vista and U, you have to make sure Vista is in its own partition and not taking up the entire disk.  If you have the space, you can give V64 around a 70gig partition and that should be plenty.  If you have already install Vista to use the entire disk, they you will have to download and run Gparted and resize the Vista partition, unless you want to install it again.  Then when you install U, make sure you pick to manually set up the disk.  This will bring you to the partition editor.  Just edit the partitions to have a 20G (your choice) root partition (/ in the drop down menu).  The next partition to make will be your home partition of whatever size you want.  Most of the programs will reside there and may take up more space.  Since Vista can't see an U partition, you may want a separate partition to move files back and forth between the two.  Last but not least, is the swap partition.  Create one which is only a gig.  I have found that I don't need it very much since I have 8gs of ram.  One gig is good as a backup, but U will not use it very much.  It is there if it needs it.  
That is a quick down and dirty and a pretty safe way.  I have Vista 64 and Jaunty 64 on my system and the dual boot is no problem at all.  Let me know if you need more help.  

:lolflag:

---

### Post by vicdeng on 2009-05-04
> **coskierken said:**
> What kind of hardware do you have?  I am surprised no one has asked that yet.  If you have at least 4G of ram, go 64bit.  Now, to safely install Vista and U, you have to make sure Vista is in its own partition and not taking up the entire disk.  If you have the space, you can give V64 around a 70gig partition and that should be plenty.  If you have already install Vista to use the entire disk, they you will have to download and run Gparted and resize the Vista partition, unless you want to install it again.  Then when you install U, make sure you pick to manually set up the disk.  This will bring you to the partition editor.  Just edit the partitions to have a 20G (your choice) root partition (/ in the drop down menu).  The next partition to make will be your home partition of whatever size you want.  Most of the programs will reside there and may take up more space.  Since Vista can't see an U partition, you may want a separate partition to move files back and forth between the two.  Last but not least, is the swap partition.  Create one which is only a gig.  I have found that I don't need it very much since I have 8gs of ram.  One gig is good as a backup, but U will not use it very much.  It is there if it needs it.  
That is a quick down and dirty and a pretty safe way.  I have Vista 64 and Jaunty 64 on my system and the dual boot is no problem at all.  Let me know if you need more help.  

:lolflag:

thanks coskierken. well, first i have to figure out how to get rid of the annoying sound running in the background. I have tried both 64 bits (twice) and 32 bits (once), and it is still there.  I mean if my hardware is having conflict with U, there is no point for me to get any further.  What kind of hardware you are talking about? because i have posted my computer spec on my second post in this thread.  Now, i think when i install U after i have Vista running, i did not run the Gparted you mentioned and resize the vista.  And when i install Vista, i chose manual partition, and that's why i wipe out my vista....When doing the Gparted, it's the same thing as shrink the vista partition under vista windows command?  I hope i can describe alil better what the sound is. let me see if i can capture the sound and post a link here. thanks for the help.

---

### Post by coskierken on 2009-05-04
Sorry to have missed the hardware, but I only saw the hp dv4t part.  What type of computer is it?  Laptop or desktop?  How much ram?  Vid card?  Just let me know.  The noise is a stopper if you said you tried 64 and 32. I can understand that.  I had my mic come on and at a high level, so it was causing a feedback to the onboard speakers of my laptop.  Annoying to say the least, but got it turned off.  I still don't see how you wiped out the Vista partition when you use manual partition setup.  Don't us the Fiesty link!  It is basically the same, though.  Did you make it to the screen for setting up the individual partitions?

---

### Post by vicdeng on 2009-05-04
HP Pavilion dv4t Entertainment PC
- Espresso Black
- Genuine Windows Vista Home Premium with Service Pack 1 (64-bit)
- Intel(R) Core(TM)2 Duo Processor T6600 (2.2GHz)
- 4GB DDR2 System Memory (2 Dimm)
- FREE Upgrade to 320GB 5400RPM SATA Hard Drive with HP ProtectSmart Hard Drive Protection
- Intel(R) Graphics Media Accelerator 4500MHD
- 14.1" diagonal WXGA High-Definition HP LED BrightView Widescreen Display (1280 x 800)
- LightScribe SuperMulti 8X DVD+/-RW with Double Layer Support
- [For LED Display] Webcam + Fingerprint Reader
- Intel Next-Gen Wireless-N Mini-card with Bluetooth
- No TV Tuner w/remote control
- HP Color Matching Keyboard
- High Capacity 6 Cell Lithium Ion Battery

This is my full spec. Now, the vista part is not important anymore, but i just have to make sure i don't mess up the next time.  When i install U after Vista, Ubuntu actually have an option "Install Ubuntu side by side with Vista" and have the option to choose at start up.  But i still want to understand the partitions problem in order to install Ubuntu with the designate hard drive size i want.  i try to mess around with the microphone part.  Thanks alot. After seeing ur message about creating the partition, i am still confused on how to set up the dual booting. Can u explain alil further? thanks

---

### Post by vicdeng on 2009-05-04
> **coskierken said:**
> Sorry to have missed the hardware, but I only saw the hp dv4t part.  What type of computer is it?  Laptop or desktop?  How much ram?  Vid card?  Just let me know.  The noise is a stopper if you said you tried 64 and 32. I can understand that.  I had my mic come on and at a high level, so it was causing a feedback to the onboard speakers of my laptop.  Annoying to say the least, but got it turned off.  I still don't see how you wiped out the Vista partition when you use manual partition setup.  Don't us the Fiesty link!  It is basically the same, though.  Did you make it to the screen for setting up the individual partitions?


btw, what do u mean by "stopper"?

---

### Post by raymondh on 2009-05-04
> **vicdeng said:**
>  But i still want to understand the partitions problem in order to install Ubuntu with the designate hard drive size i want.After seeing ur message about creating the partition, i am still confused on how to set up the dual booting. Can u explain alil further? thanks

vicdeng ... this is a thorough read about understanding partitions.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck

---

### Post by vicdeng on 2009-05-04
correct me if i am wrong, the point to shrink down the partition before installing Ubuntu is to create a partition for Ubuntu, right?

---

### Post by coskierken on 2009-05-04
by stopper I mean will stop you from proceeding.  Ok, when you get to the window, select the option of "manual" and hit forward.  it will scan the disk and see how you set it up and put it on the screen.  From this point, you will see the first partition as ntfs, probably anyway.  The next will be empty space for what you have left on the disk.  How large is the Vista partition?  Like I said, it is up to you how large you make when you install Vista, but since you have 320 gigs, I would give Vista up to 100gigs.  The install of Vista will be around 25 to 33 gigs.  So, you will have loads of overhead for extra games.  
Back to the empty space after the ntfs partition:  When you get to the page where you see the ntfs partition, the next will be the rest of the space you have left which Vista did not use.  It is probably empty if you made a seperate partition for Vista and will be the entire remaining space on the disk.  From this point, go highlight the empty space and hit "new partition" on the bottom of the window.  Tell it the size for which you may want 20000 for the boot partition for root partition for U.  Next selection down in you file system.  I am sticking with EXT3 for now myself, but it is your choice.  Next is a small button to format and make sure it is checked.  Next is a pull down for what type of partition which will be your "root" and select "/".  Once this is done, repeat the steps and create another partition.  Use the same file system, format, and the select "/home" for what type.  Since you don't know what you may install, I tend to make this larger, but it is up to you.  Like I said, most of all the programs you install will go there.  That is why I said make it 40 gigs (40000).  After you create the last partition you want, make sure you leave 1000 (one gig) for your swap.  With 4Gis of ram, it may be used, but very little.  
Whatever you do from this point in making partitions for U, will always dual boot.  It will bring up the default window at startup which will show your boot order. First will be Ubuntu and last will be Vista.  
Just hit forward and then install.  Don't worry about importing anything from Vista, at least this is what I do.  Once you start the install, all is done.  
If the sound problem continues, the first thing you want to install under Synaptic is "gnome-alsamixer" and then uncheck the mic and uncheck capture to make sure it is turned off.  This may solve the problem.  When you get the system installed, let us know.

---

### Post by arashiko28 on 2009-05-04
I'm running 64bit ubuntu. Run's like a charm and twice as fast with vista.
Actually I think that's a pretty good start, wiping vista out of it :)

I hope that you have a backup, which in case, will ease your headache.

If you can give us the sound, video card, we can advice you about it.

Don't get into despair and enjoy.

Good luck and welcome to Linux.

---

### Post by vicdeng on 2009-05-04
> **coskierken said:**
> by stopper I mean will stop you from proceeding.  Ok, when you get to the window, select the option of "manual" and hit forward.  it will scan the disk and see how you set it up and put it on the screen.  From this point, you will see the first partition as ntfs, probably anyway.  The next will be empty space for what you have left on the disk.  How large is the Vista partition?  Like I said, it is up to you how large you make when you install Vista, but since you have 320 gigs, I would give Vista up to 100gigs.  The install of Vista will be around 25 to 33 gigs.  So, you will have loads of overhead for extra games.  
Back to the empty space after the ntfs partition:  When you get to the page where you see the ntfs partition, the next will be the rest of the space you have left which Vista did not use.  It is probably empty if you made a seperate partition for Vista and will be the entire remaining space on the disk.  From this point, go highlight the empty space and hit "new partition" on the bottom of the window.  Tell it the size for which you may want 20000 for the boot partition for root partition for U.  Next selection down in you file system.  I am sticking with EXT3 for now myself, but it is your choice.  Next is a small button to format and make sure it is checked.  Next is a pull down for what type of partition which will be your "root" and select "/".  Once this is done, repeat the steps and create another partition.  Use the same file system, format, and the select "/home" for what type.  Since you don't know what you may install, I tend to make this larger, but it is up to you.  Like I said, most of all the programs you install will go there.  That is why I said make it 40 gigs (40000).  After you create the last partition you want, make sure you leave 1000 (one gig) for your swap.  With 4Gis of ram, it may be used, but very little.  
Whatever you do from this point in making partitions for U, will always dual boot.  It will bring up the default window at startup which will show your boot order. First will be Ubuntu and last will be Vista.  
Just hit forward and then install.  Don't worry about importing anything from Vista, at least this is what I do.  Once you start the install, all is done.  
If the sound problem continues, the first thing you want to install under Synaptic is "gnome-alsamixer" and then uncheck the mic and uncheck capture to make sure it is turned off.  This may solve the problem.  When you get the system installed, let us know.

let me get it straight
ext3  -- root partition for U  "/"
ext3 -- installed programs space, "/home"
swap 
now, what does "primary" and "logical" come in to place in the two partitions above, because i see when you just tell Ubuntu to use the entire space to install U, it will only have swap and ext3 /, these two partition, now you have one with the root partition, and /home partition, what do they do basically?  Thanks for the advise again. I am really a newbie in ubuntu

Is there a way i can attached a sound in my post?

---

### Post by vicdeng on 2009-05-05
attached is a wav file, it captured the sound on my start up of Ubuntu. Again, i am not able to install Gnome-Alsamixer under synaptic. There is no such package.  The weird thing is, the sound comes on at start up, and after 3 or 4 mins, the volume reduces and become silence.  any ideas?

---

### Post by vicdeng on 2009-05-05
Annoying sound fixed. I used this command below, can anyone tell me what it does? thanks

gksu gedit /etc/modprobe.d/alsa-base.conf
add at the end
options snd-hda-intel model=3stack-dig enable_msi=1

Now, i can't get adobe flashplugin installed, error msg: Wrong architecture i386
Any idea? 

I have also have difficulties to install my bluetooth wireless mouth (made by Microsoft). Ubuntu said it's connected, but my mouse is still in the searching mode. but that seems to be a common problem with Ubuntu.

---

### Post by John.Michael.Kane on 2009-05-05
> **vicdeng said:**
> Annoying sound fixed. I used this command below, can anyone tell me what it does? thanks

gksu gedit /etc/modprobe.d/alsa-base.conf
add at the end
options snd-hda-intel model=3stack-dig enable_msi=1

gksu provides a Gtk+ front-end to su and sudo.

gedit is the text editor that was used to open the .conf file.

/etc is where configuration files specific to the machine are located. 

modprobe is a Linux program used to add or remove a module to/from the Linux kernel.

alsa-base.conf is a configuration file.

Regarding the he option line you added.
snd-hda-intel means you have an Intel hda audio device.

model=3stack-dig means you added a hardware option for 3-jack with SPDIF I/O

enable_msi=1 means you enable Message Signalled Interrupts, and set it for 1.

> **vicdeng said:**
> Now, i can't get adobe flashplugin installed, error msg: Wrong architecture i386
Any idea?

Please explain how you are trying to install flash.

Normally you would simply use synaptic, and search for flashplugin-nonfree.

> **vicdeng said:**
> I have also have difficulties to install my bluetooth wireless mouth (made by Microsoft). Ubuntu said it's connected, but my mouse is still in the searching mode. but that seems to be a common problem with Ubuntu.
Regarding your blue-tooth device, you can try the below link.
[BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup")

---

### Post by vicdeng on 2009-05-05
> **John.Michael.Kane said:**
> gksu provides a Gtk+ front-end to su and sudo.

gedit is the text editor that was used to open the .conf file.

/etc is where configuration files specific to the machine are located. 

modprobe is a Linux program used to add or remove a module to/from the Linux kernel.

alsa-base.conf is a configuration file.

Regarding the he option line you added.
snd-hda-intel means you have an Intel hda audio device.

model=3stack-dig means you added a hardware option for 3-jack with SPDIF I/O

enable_msi=1 means you enable Message Signalled Interrupts, and set it for 1.



Please explain how you are trying to install flash.

Normally you would simply use synaptic, and search for flashplugin-nonfree.


Regarding your blue-tooth device, you can try the below link.
[BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup")


Thanks for the site. I did successfully installed flash, but my bluetooth still doesn't work. I might just have to continue searching for options. but when i google it, it seems alot of ppl having the same issue with this bluetooth mouse.

---

### Post by raymondh on 2009-05-05
> **vicdeng said:**
> let me get it straight
ext3  -- root partition for U  "/"
ext3 -- installed programs space, "/home"
swap 
now, what does "primary" and "logical" come in to place in the two partitions above, because i see when you just tell Ubuntu to use the entire space to install U, it will only have swap and ext3 /, these two partition, now you have one with the root partition, and /home partition, what do they do basically?

Drives have a 4 partition limit.  Each partition is "Primary".  Now, linux has a neat trick of going around that 4 Primary Partition limit.  Linux has  "Logical".  In a sense, logical is a partition INSIDE or WITHIN a Primary partition.  A ubuntu install CAN be in this manner.  A Primary partition that involves various logical partitions within (such as for /home,/var,swap, etc)

Have fun learning.

---

### Post by vicdeng on 2009-05-05
> **raymondhenson said:**
> Drives have a 4 partition limit.  Each partition is "Primary".  Now, linux has a neat trick of going around that 4 Primary Partition limit.  Linux has  "Logical".  In a sense, logical is a partition INSIDE or WITHIN a Primary partition.  A ubuntu install CAN be in this manner.  A Primary partition that involves various logical partitions within (such as for /home,/var,swap, etc)

Have fun learning.

So what's going into the root partition? because i created 20 gig for that partition, i understand when i create my /home, all my installed program goes in there. so u are saying that when u create the /home partition, you need to create it as logical instead of primary?

---

### Post by raymondh on 2009-05-05
> **vicdeng said:**
> So what's going into the root partition? because i created 20 gig for that partition, i understand when i create my /home, all my installed program goes in there. so u are saying that when u create the /home partition, you need to create it as logical instead of primary?


Another analogy, if this'll work.  

What goes into root are all the files canonical (the developer of ubuntu) gives us to make ubuntu work as an OS (of course, before we tweak them to make Ubuntu better for our respective needs)

/home is the directory that has all the files you PUT INTO ubuntu .... (data, media, pictures, etc)

Some google-fu reading for you:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Now, whther logical or primary depends on how many primary partitions you have already.  4 primary is the max.  Should your /root install be the 4th primary partition, then /home would be a logical partition INSIDE /root.  However, if you are starting with a blank slate and have no plans to dual-boot, etc .... then feel free to have / as a primary, /home as another primary, /var as another and swap.  See this link:

[http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install](http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install)

Point is, if you're maxed out because of the 4 primary limit, then linux allows you LOGICAL partitions (within a primary) so you can have more.  Think of a primary as a house and logical as the rooms inside the house. :)

---

### Post by coskierken on 2009-05-05
Just checking in now!  Ok, you seem to be getting the hang of it.  The "/" partition is where U will install its OS like said above.  The "/home" partition will hold all your data and the data for install programs, but it will normally be hidden.  Control-H will show you the hidden files.  Since you have made the 20gig partition for root, you can make the others any size you want.  Personally, I would make the "/home" 40gig and then assign the rest as a logical and format under NTFS.  This allows you to easily see the partition in Vista and U.  You have probably got it all done now, so this may be moot.  I hope all went well.

---

### Post by coskierken on 2009-05-05
I have not worked with bluetooth in a while.  I just could not get it to work under 8.10.  It may have been my Plantronics 510, but unsure.  I don't have bluetooth tx on this machine, so unless I install Jaunty on my laptop, I won't know.  Good luck and let us know.

---

### Post by vicdeng on 2009-05-05
> **coskierken said:**
> Just checking in now!  Ok, you seem to be getting the hang of it.  The "/" partition is where U will install its OS like said above.  The "/home" partition will hold all your data and the data for install programs, but it will normally be hidden.  Control-H will show you the hidden files.  Since you have made the 20gig partition for root, you can make the others any size you want.  Personally, I would make the "/home" 40gig and then assign the rest as a logical and format under NTFS.  This allows you to easily see the partition in Vista and U.  You have probably got it all done now, so this may be moot.  I hope all went well.


thanks for all the friendly helps here.  I really appreciate it.  I thought if u wanna share file between Vista and U, u need to make ur partition Fat32. correct me if i am wrong. Thanks again.

---

### Post by John.Michael.Kane on 2009-05-05
> **vicdeng said:**
> thanks for all the friendly helps here.  I really appreciate it.  I thought if u wanna share file between Vista and U, u need to make ur partition Fat32. correct me if i am wrong. Thanks again.

From my understanding, Ubuntu has the ability to read ntfs partitions.
[Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by coskierken on 2009-05-06
U can read an NTFS partition.  It is more efficient than Fat32.  But, it is your choice.  I used an NTFS on my storage as it was previously in an external media player.  It sounds as it you have it down now.  Keep working with it and you will get continue to learn!

---

### Post by vicdeng on 2009-05-06
once again, just to make sure, in order to create a partition that can be access from both Vista and Ubuntu. Does it need to be NTFS or FAT32, what type is it? "/" or "home", what should i select in that drop down menu? So do u say that i can create that partition in Vista using disk management? thanks

---

### Post by coskierken on 2009-05-07
What I do is make a "/" root (20gigs)(primary) , "/home" (40gigs, primary), and then a large partition for the rest and call it "/media/storage" (logical) and format it with NTFS and this way you can store downloads, movies, etc and share it with Windows.  When you make the last partition, make sure you leave room for the swap partition of 1Gig.  In other words, leave 1000.  Then you will create the last partition with it and when you make your choice, pick "swap".  That is it and just install.  You can always change some things up later if you want.  With 2 drives, my 500gig only has one Vista partition, and two Linux ext3.  My second drive (1TB) holds all the data and is NTFS so Vista can see it as sometimes I play movies in Vista.  It is all up to you and how you want to handle the data.  Enjoy!

---

