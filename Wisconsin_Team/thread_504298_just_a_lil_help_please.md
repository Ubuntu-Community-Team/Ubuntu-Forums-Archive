---
title: "just a lil help please"
date: 2007-07-19
forum: Wisconsin Team
---

### Post by TH3_D0ct0R on 2007-07-19
ok so when i boot up my harddrive on a completely different machine it gives me a GRUB Loading Stage 1.5 things and the does nothin for a long time

i spose this has a lot to do with the machine so im gunna try the live cd and see if it will work...its really low on memory tho...:( 


well ne help would be apreciated and if you need ne more info just ask

Th3 D0ct0R

---

### Post by Ek0nomik on 2007-07-19
Does the text, "Grub loading stage 1.5..." stay on the screen or does it vanish and the result is simply a blank black screen?

How much memory does your box have?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Remember, as far as memory is concerned, KDE uses the most, followed by Gnome and XCFE.  You can also use Fluxbox.  I don't know if Fluxbox uses more or less than XCFE, but I would imagine less.

---

### Post by TH3_D0ct0R on 2007-07-19
well it would just stay on the screen...but now after i plugged in another windose harddrive it will boot right to the ubuntu..or i think it...it says out of range on the screen (as in a a programmed message from teh monitor) and then shows a blinking console cursor(the underscore flashing)
and does nothing..i have left it alone for hours and still nothing happened...the same thing happen to the live cd except that the screen does not say out of range and it shows the splash ubuntu progress bar thing...

there is no time limit on this seeing as i have another fine pc in my room which i am on right now but i just want to get my ubuntu working cuz i would actually do some work than rather than fool around of DAy of Defeat :P

and it has 256mb...i already knew the minimum requirments but its still a lil low...

if you need to know ne thing else please ask

thanks for the help

Th3_D0ct0R

---

### Post by Ek0nomik on 2007-07-19
> **TH3_D0ct0R said:**
> well it would just stay on the screen...but now after i plugged in another windose harddrive it will boot right to the ubuntu..or i think it...it says out of range on the screen (as in a a programmed message from teh monitor) and then shows a blinking console cursor(the underscore flashing)
and does nothing..i have left it alone for hours and still nothing happened...the same thing happen to the live cd except that the screen does not say out of range and it shows the splash ubuntu progress bar thing...

there is no time limit on this seeing as i have another fine pc in my room which i am on right now but i just want to get my ubuntu working cuz i would actually do some work than rather than fool around of DAy of Defeat :P

and it has 256mb...i already knew the minimum requirments but its still a lil low...

if you need to know ne thing else please ask

thanks for the help

Th3_D0ct0R

If it says out of range, my guess would be that the xorg.conf file being loaded doesn't have the proper settings for your monitor.  Your refresh rates are probably too high or too low for your monitor.

You don't have Ubuntu installed though, correct?  You are simply trying to install it?  If that's the case, and the Live CD isn't working, why not try the Alternate CD?  I prefer the Alternate CD for installing anyways.  :)

---

### Post by TH3_D0ct0R on 2007-07-19
ok so i guess ill just give everyone sum info on this beast right now so you dont have to ask

one Deskstar 82 gig harddrive with WinXP on it
one Maxtor  60 gig hardrive with Ubuntu 7.04 on it
one COmbo cd/dvd drive with Ubuntu 7.04 live disk in it
a 1.44 floppy
256mb RAM
some sort of MSI Board
64mb Geforce4---sumthin like that
its a Pentuim 4


umm ne thing else or ne more detail just ask..

Th3_D0ct0R

---

### Post by herteljt on 2007-07-19
Have you tried running the live cd in safe graphics mode?

---

### Post by TH3_D0ct0R on 2007-07-19
@herteljt
yea i did and it would go straight thro the splash and then get to a blinking cursor and nothing would happen

@Ekonomic
:) well its a funny story...yes and no.... i do have it installed on a harddrive...the matxor one and i have tried to boot off of it and it wouldnt thats when i would get the out of range thing...and its becuz the xorg.conf isnt correct becuz its set for a different monitor...but i was also trying the live cd and it would just go thro the splash and go to a blinkin cursor...(the hardrive w/ ubuntu installed would do the same thing xept no splash only "out of range")

and yea i have downloaded the alternate install cd just now well see how that works

cuz if i can get it up and running on the other half of the harddrive could i then get the info off of the old half??

oh and i sucessfully installed xubuntu on the windose harddrive so now its erased and written over but when i go to start it it goes back to the grub loading stage 1.5.....and then on the next line it says sumthin like "GRUB loading....." and does nothing...OMG!!! ok just restarted it and now the GRUB loaded and i choosed the xubuntu one and its loading and is at the startup screen...ok so now thats working but i want to get my ubuntu working too
 

thank you for the help so far we are this far from a cure

Th3_D0ct0R

---

### Post by Ek0nomik on 2007-07-20
> **TH3_D0ct0R said:**
> @herteljt
yea i did and it would go straight thro the splash and then get to a blinking cursor and nothing would happen

@Ekonomic
:) well its a funny story...yes and no.... i do have it installed on a harddrive...the matxor one and i have tried to boot off of it and it wouldnt thats when i would get the out of range thing...and its becuz the xorg.conf isnt correct becuz its set for a different monitor...but i was also trying the live cd and it would just go thro the splash and go to a blinkin cursor...(the hardrive w/ ubuntu installed would do the same thing xept no splash only "out of range")

and yea i have downloaded the alternate install cd just now well see how that works

cuz if i can get it up and running on the other half of the harddrive could i then get the info off of the old half??

oh and i sucessfully installed xubuntu on the windose harddrive so now its erased and written over but when i go to start it it goes back to the grub loading stage 1.5.....and then on the next line it says sumthin like "GRUB loading....." and does nothing...OMG!!! ok just restarted it and now the GRUB loaded and i choosed the xubuntu one and its loading and is at the startup screen...ok so now thats working but i want to get my ubuntu working too
 

thank you for the help so far we are this far from a cure

Th3_D0ct0R

You should really try to type in a more "cleaned up" style.  It will make it easier to read.  :)

Yes, if you can get into any sort of Linux operating system on your computer, you should be able to snag all your data from your other partition safely.

So you have have one hard drive running Xubuntu, which you can boot into?

Another hard drive with Ubuntu installed, but you can't access it?

---

### Post by TH3_D0ct0R on 2007-07-20
yea i have one harddrive with Xubuntu installed and one with Ubuntu installed they are both connected right now and the Xubuntu one is the Master Drive and is first in the boot order(after cd of course) and when i turn the computer on it goes thro the POST and then comes to a screen where it checks PCI devices and then looks for a bootable cd to load from and then it displays at the bottom of the screen "GRUB Loading stage1.5" and two lines later""GRUB Loading, please wait..." and then displays a blinking cursor at the bottom.

Last night as i was typing the other post it sum how loaded the GRUB and i choose the Xubuntu one and it loaded up no problem...i loaded up all the updates and it ran fine for 4 hours...then i shut it down to go to bed and this morning i booted it back up and it went to the screen i explained before

i apologize for the messy typing but its just as confusing as it seems to you as it does to me :):)

ill be around both of these computers all day you can more likely reach me on MSN...and try the #ubuntu-wisconsin channel if i can get my IRC thing to work

and i say goodday:-P

Th3 D0ct0R

---

### Post by Ek0nomik on 2007-07-20
Have you tried the Alternate CD yet?  I would just put that disc in, knock out the entire hard drive, and start from scratch with a single OS.  Assuming you don't want Windows anymore...

Since you can get into Xubuntu, why not just backup all your needed data by burning it to a CD or putting it on a USB device and than knock everything out?

---

### Post by TH3_D0ct0R on 2007-07-21
well you see if i did that then i wouldnt  have to pull all my hair out after i lose it all :P

no but seriously my USB device is occupied at the moment and that would take time 

BUT!! (and a big but and that) i have found a way to bypass the grub loading thingy.....
.....supsenseful moment.......and it is boot the live cd and tell it to  boot first harddisk and this loads the grub...dont ask me how it works cuz i dont have a clue

but yea now ubuntu is now running and i can get to my info on the other harddrive by typing in my password and i can get to it so i have no idea and there prolly is no way you could script sumthin to autoload it i bet...so i guess ill have to do it my hand

thanks for the help

Th3_D0ct0R

---

