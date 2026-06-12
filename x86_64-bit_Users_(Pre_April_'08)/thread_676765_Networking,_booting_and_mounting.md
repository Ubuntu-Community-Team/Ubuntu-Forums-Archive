---
title: "Networking, booting and mounting"
date: 2008-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by msknight on 2008-01-24
Hi Folks,  ):P

Apologies for being a 64 bit newbie on these forums, which is why I'm keeping these three simple questions to the one post.

Situation ... previous SuSE system (I'm used to using the Gui so I'm spoiled!) with a RAID set on it.  New motherboard, processor, etc. so I changed to Ubuntu 7.10 64 bit Server and I'm having some noddy issues which is down to the fact that I'm not used to some of the file editings.

Problem 1 -
Nice easy one ... I loaded the desktop system and the server goes to a blank screen on boot.  I need to see the system prompts on boot, but not have to press some key or other (I haven't worked out which one it is anyway, ESC on SuSE doesn't work on Ubuntu) ... so I'm assuming this is just a parameter in some file that I need to change.

Problem 2 -
The system has a gigabit ethernet port and connects at 1gb when rebooted, but on an administrative up/down like relocating the cables, or the switch restarts, or something like that, the card comes up in 100Mbs only.  I'm presuming that this is an autonegotiation problem and I can't find any options for the interfaces file to force the connection to 1000 full.  Anyone any advice please?  I've read about some other third party malarky that has to be run to force the connection, but that seems to be an old thing related to 100 and there should be a configuration file option somewhere by now?  Anyone happen to know please?

Problem 3 -
Software RAID 1 set - MDADC picked up the set no problem and after a reboot if I manually mount it, it's fine, but if I include it in the fstab, it doesn't seem to mount on boot but then when I try to mount it the system says it is already mounted and I can't dismount it either.  The Fstab is ...
/dev/md1     /mirror     auto   defaults    0   1

Any help greatly appreciated, 'cause facing off against a bad *** Gusty Gibbon is scaring this newbie ;)

As an addon to Problem 2, if autonegotiation starts at 100mbs and works down, then there could possibly be something that needs to be changed in code somewhere to start from 1gb?  Just a thought.

Michelle

---

### Post by msknight on 2008-01-24
Thought I'd clear up why I need to see what is happening during server boot and why I've got the GUI installed.

Basically, the GUI makes things like writing DVD's and various other things much easier.  However, when trouble hits and the server hangs, it is too late to see the last message on the server.

That's the problem I've got now.  Boot normally and it just sits there, it doesn't respond to anything and I've got no way to determine what is happening.

At the moment I've got the hard disks on test because I'm in that much trouble.  The server was up for a day or two while I was configuring it, with everything looking good, and then this problem hits.  I've looked on the web but everyone seems to be talking about hiding the messages back in 2005, and the only advice that my friends can come up with is to deinstall the GUI ... well, I might if I could get the system up.

So ... I need the best of both worlds ... to see what the server is doing during boot, and also to be able to use the GUI for ease of application use.

Michelle.

---

### Post by msknight on 2008-01-24
Update -

Mounting the RAID partition is solved.

The screen going black is only partially solved by taking the quiet mode off ... the screen still goes nicely black after the initial switch to graphics mode.

The network issue is worse than I suspected ... after initial machine start, when Gibbon takes controll the network card drops to 100Mbs ... it was never operating at 1 gig.  Looks like I need drivers or something.  Any advance on this please?  It's a Marvell Gigabit Lan card and the Abit site doesn't list a driver.

Michelle.

---

### Post by Herman on 2008-01-24
Hello msknight,
I'm feeling a bit humble here because it sounds like you might be a bit more advanced than I but I'll have a try at a couple of things anyway and hope I'll be of some help.

1. Black screen during boot-up - Just by co-incidence, someone else had a problem that sounds something like your problem, (I'm not sure), but I made a web article about it here, [Temporarily Edit the GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu"). - how to edit your GRUB  menu commands 'on the fly'. This article also links to **[HOWTO: Change bootup resolution]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters")**, by [Indras]("http://www.ubuntuforums.org/member.php?u=126305"), which I hope will be the important information you might need to solve that problem, if it's what I think it its. :)

2. I have never had a network connection that fast, (I'm envious), but I did notice mine also was very slow compared with what my ISP promises me, which is supposed to be 512/128. Or at least that's what I thought at the time. Whenever I was using wget for downloading files I noticed the actual reported download speeds I was able to achieve were only up to maybe 53 or so.
Then I realized maybe their 512 kbps means 512 kilo 'bits' instead of 512 kilo 'bytes' like I was thinking.
That explained it. I found these two links,  [Difference bet Kbps and KB/sec]("http://www.daniweb.com/forums/thread9599.html"). and [The Data Transfer Rate Conversion Table]("http://www.scotsnewsletter.com/best_of/dtrct.htm").
I'm not sure if the same situation applies in your case or not, but if it does, I hope I have been able to set your mind at rest.

3. I know nothing much about any kind of RAID, sorry, but I see you have that solved, that's good. Well done. :)

Regards, Herman :)

---

### Post by Yellow Pasque on 2008-01-24
Have you tried ethtool yet? I'm not sure if it comes pre-installed on Ubuntu, but I do know it's in the repo, so:
```
sudo apt-get install ethtool net-tool
```
I think the command would be (assuming connection name of eth0, use ifconfig command to double-check):
```
ethtool -s eth0 speed 1000 duplex full autoneg off
```

---

### Post by msknight on 2008-01-25
Hi Herman,

Thanks for the links.  I'll try those out tonight when I get back from work.

The network connection is internal only, I've got four PC's and a couple of laptops ... most of the motherboards come with gigabit connections on them these days.  Also, a gigabit switch has come to about 20GBP, which is well affordable for the increase in speed.

Temüjin,

Thanks for the tip, and I did try ethtool (you are correct, it was already installed) and also mii-something-or-other but the mii-thingy only goes to 100 (it seems that development stopped in 2005) and even though the ethtool recognises 1000, on giving the apropriate command, it still came up as 100.

SuSE 10.1 is on another server and that picked up the gigabit perfectly when that was installed on a 64bit AMD about a year ago, so I may have to scrub Ubuntu and go back to SuSE ... which I don't really want to do.

Part of me thinks it is a driver issue, but if it were that then surely the tools would not have reported it capable of gigabit ... so not being a techy programmer, I'm somewhat stuck as I can't find a driver anywhere.

Michelle.

---

### Post by msknight on 2008-01-25
Temüjin,

You're a star.  The extra autoneg off worked a treat!  (I didn't try that option before) Now I have to find a way of getting that to happen whenever the machine starts up ... I'm not sure of the timings.

Michelle.

---

### Post by Yellow Pasque on 2008-01-25
> Now I have to find a way of getting that to happen whenever the machine starts up ...
When do you want it to start? In general, if you want to make a startup script, see the Installing custom init-scripts section in this HowTo. [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

That should work just fine, as the networking startup script runs at runlevel S, priority 40, and the command used in the HowTo installs your script at priority 51.

---

### Post by BillDozer on 2008-01-25
Do you still have a problem with the blank screen after startup?

I had a similair problem after I installed another video card, and the bios was not that good at disabeling the built-in video card to ubuntu. If you have an internal and an external, try to plug your monitor into the internal card.

---

### Post by Thelasko on 2008-01-25
I'm a little confused on your boot problem.  Do you have a blank screen or a splash screen?  It sounds like you want to eliminate the splash screen.  In which case you[ delete "quite splash" from GRUB.]("http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/")

---

### Post by msknight on 2008-01-25
Hi Folks,

Thanks for that.  I deleted quiet but I wasn't sure about splash.  I'll try that and see what happens.  Thanks for the link as well, I'll give that a shot right now.

Michelle.

---

### Post by msknight on 2008-01-25
Bingo.  That sorted it superbly.  Thank you all very much indeed.  Stunning performance given to this newbie.  My first server cup of Ubuntu tastes all the better for the community spirit.  Many thanks.

Michelle.

---

