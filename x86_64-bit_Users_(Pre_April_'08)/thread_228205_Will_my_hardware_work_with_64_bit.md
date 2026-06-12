---
title: "Will my hardware work with 64 bit?"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikeescott on 2006-08-02
I built a new computer in March and I am thinking of tryinh Linux. I have never used it before. Here is the computer I built:

Pentium 4 955 dual core hyper threading
ASUS P5WD2E Premium
ATI AIW x1800xl
2 X 1024 PC6400 DDR2
74gb raptor
300gb 7200rpm wd sata
250gb 7200rpm maxtor pata
lite-on dl dvdrw
640w power supply
120mm cpu cooling fan
6 X 80mm case cooling fans 
canon n670u scanner
hp photosmart 8250
usb 2.0 controller card
usb 21 in 1 card reader

I tried to install ubuntu when I finished but could not get it to work and went with 64 bit windows on the raptor and 32 bit on a partition of the wd 300gb drive. I use 32 bit most of the time 'cause most of my programs and hardware do not have 64 bit drivers. Am I going to have this same problem with Linux?

---

### Post by hasimir44 on 2006-08-02
The best way to know is to try it :) The beauty of Ubuntu is that it's "live" so you can run it without actually installing anything. [Here's]("http://ftp.wayne.edu/linux_distributions/ubuntu/6.06/") the download page. The [64-Bit threads]("http://www.ubuntuforums.org/forumdisplay.php?f=134") have a lot of info on how to get 32-bit apps to work.. I have a new amd64 cpu and I'm planning on testing both 64-bit and 32-bit xubuntu builds just to see for myself.

---

### Post by mikeescott on 2006-08-02
I tried the live ubuntu 64 bit version 5.10 that I have and this is where it stopped. Sorry for the quality, I took "screen shots" with my digital camera.
:confused: (*,)
[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/1.jpg[/IMG]] 
:confused: ](*,) 
[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/2.jpg[/IMG]

---

### Post by TripleE on 2006-08-02
Your hardware is definitely good enought to run 64bit dapper.  I would highly recommend getting 6.06 (dapper).  I am running it, and it runs great.  [Here]("http://geocities.com/eric1548/") is my experience.  If you are curious about your processor, check out [this link]("http://www.supremelaw.org/systems/cpu_table_intel_big.gif").8)

---

### Post by ylixir on 2006-08-03
heya mikee, i have the same proplem when i boot off the live cd.  it's those @#%@ ati cards.   fix is easiesh though, depending on your level of experience....

do the following (you can use something other than vi, but i'm not really sure what the livecd has.  nano might be an option):

type "sudo vi /etc/X11/xorg.conf" and replace the line that reads 'Driver "ati"' with 'Driver "radeon"'

then type "sudo killall gdm"
and then type "sudo /etc/init.d/gdm restart"

now you should be in business.  sucks, though because you have to do that every time you boot off the cd.

at least thats what i had to do.  hopefully it will work for you too, but i think your card is a bit newer than mine, so ymmv.  you could also try vesa, or even vga if the radeon driver doesn't work.

---

### Post by mikeescott on 2006-08-03
> **ylixir said:**
> heya mikee, i have the same proplem when i boot off the live cd.  it's those @#%@ ati cards.   fix is easiesh though, depending on your level of experience....

do the following (you can use something other than vi, but i'm not really sure what the livecd has.  nano might be an option):

type "sudo vi /etc/X11/xorg.conf" and replace the line that reads 'Driver "ati"' with 'Driver "radeon"'

then type "sudo killall gdm"
and then type "sudo /etc/init.d/gdm restart"

now you should be in business.  sucks, though because you have to do that every time you boot off the cd.

at least thats what i had to do.  hopefully it will work for you too, but i think your card is a bit newer than mine, so ymmv.  you could also try vesa, or even vga if the radeon driver doesn't work.

I have always been a windows user, so my experience lever there is pretty low. Where do I type these commands? Do you know if the 64 bit versions on SUSE and Fedora Core have the same problem and is there a downside to using them instead of Ubuntu?

---

### Post by Kilz on 2006-08-03
> **mikeescott said:**
> I have always been a windows user, so my experience lever there is pretty low. Where do I type these commands? Do you know if the 64 bit versions on SUSE and Fedora Core have the same problem and is there a downside to using them instead of Ubuntu?

Yes all Linux distributions will need ati drivers installed. They are proprietary drivers and are not installed by default in Linux distros.
I would however recommend using the Alternate Install CD of Dapper. It is common that the live cd wont boot up depending on the drivers you need. Some cant be added because they are proprietary.

---

### Post by VirtuAlex on 2006-08-03
does anybody see what i see?

---

### Post by McMarley on 2006-08-03
Yeah thats what I see, and it doesnt have anything to do with your question, at least I didnt make the connection...

---

### Post by VirtuAlex on 2006-08-03
> **McMarley said:**
> Yeah thats what I see, and it doesnt have anything to do with your question, at least I didnt make the connection...
I do not have any questions. And now I do not see nothing at all in the place where mike's screenshots supposedly were. Anyway...
> **mikeescott said:**
> Do you know if the 64 bit versions on SUSE and Fedora Core have the same problem and is there a downside to using them instead of Ubuntu?
I tried SUSE, not 64bit, but it would not make much difference. IMHO it has only one advantage - it is very easy to make xgl work on it. In any other sence it is obese and freakishly slow.

---

### Post by mikeescott on 2006-08-03
> **VirtuAlex said:**
> does anybody see what i see?

Sorry, hotlinking was working when I posted them. Should be working now. Does anyone else know where I type the commands listed above to get the correct drivers loaded and do I hit enter after every line?

---

### Post by Kilz on 2006-08-03
> **VirtuAlex said:**
> I tried SUSE, not 64bit, but it would not make much difference. IMHO it has only one advantage - it is very easy to make xgl work on it. In any other sence it is obese and freakishly slow.

As an ex SuSE user, 64bit in my case, I will second the bloat and slowness comments. The only advantage is that its already multiarch imho. But the ATI driver install is a nightmare.

---

### Post by hasimir44 on 2006-08-03
> heya mikee, i have the same proplem when i boot off the live cd. it's those @#%@ ati cards. fix is easiesh though, depending on your level of experience....

do the following (you can use something other than vi, but i'm not really sure what the livecd has. nano might be an option):

type "sudo vi /etc/X11/xorg.conf" and replace the line that reads 'Driver "ati"' with 'Driver "radeon"'

then type "sudo killall gdm"
and then type "sudo /etc/init.d/gdm restart"

now you should be in business. sucks, though because you have to do that every time you boot off the cd.

at least thats what i had to do. hopefully it will work for you too, but i think your card is a bit newer than mine, so ymmv. you could also try vesa, or even vga if the radeon driver doesn't work.

You can type Ylixir's commands from the command line in any directory.

---

### Post by mikeescott on 2006-08-03
How do I get to where I can type a command when starting from the live cd?

---

### Post by VirtuAlex on 2006-08-03
> **mikeescott said:**
> How do I get to where I can type a command when starting from the live cd?
On your second screenshot right above the sticker on the bottom right...

---

### Post by ylixir on 2006-08-05
you can get to a command line by pressing ctl-alt-f1, or ctl-alt-f2, or ctl-alt-f3, etc.

---

### Post by mikeescott on 2006-08-05
I tried to run the live cd again today and this time it did not look the same. I was able to get to a shell command and type the lines above, but I am not sure I did it correctly. After I edit the ati driver, what am I supposed to do to get back to a shell prompt? I tried F1 through F5 and they bought me up in different spots and when I typed the killall command, nothing happened. Then when I typed the restart command, I kept getting the same X server error. What am I doing wrong and how do I fix this?


[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux3.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux4.jpg[/IMG]

---

### Post by ylixir on 2006-08-05
it kind of sounds like the file isn't being saved after being edited. maybe vi wasn't the best command to give someone who is totally new to *nix.

try these new and improved instructions, hopefully they will give you better results ;-)

go to the command line and type
```
sudo nano -w /etc/X11/xorg.conf
```
replace the line that reads 'Driver "ati"' with 'Driver "radeon"'

press ctl-O (letter O not the number zero). press enter to save.
press ctl-X

you should now be back at the command line.
now try the commands
```

sudo killall gdm
sudo /etc/init.d/gdm restart

```

it's important that you don't reboot between the first command i gave you and the last command, since a reboot will destroy anything you've done, and you will have to start back at the beginning of the instructions.

i don't know whether that will actually work for you, but it worked for me, and we have similar video cards.

if it doesn't, i'll think up some instructions for how you can get an Xorg log file up for us to look at, so we can figure out what is wrong.

---

### Post by mikeescott on 2006-08-06
I like the nano a lot better. Knowing the commands really helps. I am sure it was not saving before, but it did this time. However, I am still having the same problem after changing. Here are pics of most of the screenshots during my attempt to run the live cd.

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux5.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux6.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux7.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux8.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux9.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux10.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux11.jpg[/IMG]

---

### Post by mikeescott on 2006-08-06
[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux12.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux13.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux15.jpg[/IMG]

[IMG]http://mypeoplepc.com/members/mikejackie/sitebuildercontent/sitebuilderpictures/linux16.jpg[/IMG]

---

### Post by John.Michael.Kane on 2006-08-06
mikeescott if you can please try the live cd with one hdd, and your cd/dvdrw. also are are you using any ide hdd or all sata with just the dvd-rw being ide? theres been some issues with mixing ide hdd with sata hdd.

---

### Post by mikeescott on 2006-08-06
The 74 gb raptor and the 320 gb WD drive are SATA and the Maxtor 300 gb drive and dl dvdrw are ide. I have a Maxtor 80 gb drive and second dl dvdrw that are just sitting in the case 'cause one of the ide plugs on the motherboard is not working yet. I am hoping linux will be able to recognize it. I will unplug sata drives and see if it works that way. I am also in the process of moving some info around on the drives so that I can reformat one for a clean install to see how that goes.

---

### Post by John.Michael.Kane on 2006-08-06
mikeescott just post back when your done. I think the issues your having are steming for the mix setup. that why i asked if you can test with a 1+1 setup one Sata-hdd with one Ide cd/dvd drive.

---

### Post by mikeescott on 2006-08-06
I tried several configurations of drives with the same result every time. I have a clean drive now and will try a hard install. Look for new posts to come later as I am sure it will not install without problems. Thanks for the help so far.

---

### Post by VirtuAlex on 2006-08-06
I bet it has nothing to do with your drives, it is just damn ATI, but may the the power be with you.

---

### Post by ylixir on 2006-08-07
i'm a little stumped.  you could try getting ahold of a 6.06 ubuntu cd.  i think i've figured out a way for you to post some of your log files so we can get a better idea of what is going on.  it's not for the faint of heart though.

this command will make a log of Xorg output when it runs:
```
X 2> xout.log
```
note: if this command somehow manages to give you a gray screen with a black X in the middle of it, don't worry, it's a very good thing, because it means that the problem is probably a lot simpler than i think it is.

that will make a file call xout.log in your current directory with the x servers output in it.  if you need to know what directory you are in
```
pwd
```

the other file we will need is /var/log/Xorg.0.log
note: unlike windows, linux file names are case sensitive

now for getting the files posted on the forums
```
sudo apt-get install links
```

that will install a text based web browser called links.  it's controls are a little weird, but after playing around with it a bit, hopefully you will figure them out.  mostly links makes me want to poke my eyes out though, so be careful ;-)

now type links at the command line and surf over too this thread on [http://www.ubuntuforums.org](http://www.ubuntuforums.org) and post those two log files.

some information on your monitor would be useful too.  i see that it is a samsung.  if it's a problem with the video card not being able to find a proper mode to run your monitor in, we will need one of the following
a) the vertical refresh range and the horizontal sync range for your monitor, or
b) the model number for your monitor so we can google it and get the vert and horiz timings ourselves

that's kind of a lot of hassle too, if you just want to try out linux, then maybe suse, or fedora core will be easier to get going, i don't know.  gentoo is another option, but it takes a fair amount of time and effort to get a gentoo system up and running.

personally i think ubuntu is worth the hassle though.  it's pretty slick once you it all figured out.

---

