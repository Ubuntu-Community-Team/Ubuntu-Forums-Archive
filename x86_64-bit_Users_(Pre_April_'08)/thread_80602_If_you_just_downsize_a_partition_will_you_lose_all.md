---
title: "If you just downsize a partition will you lose all your data on it?"
date: 2005-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by brett824 on 2005-10-22
?

---

### Post by Jenda on 2005-10-22
Well, apart from the fact that the sole content of your post is a questionmark, no problem.
Ubuntu's built-in ntfsresize works like a charm to resize NTFS partitions, so you don't really have to worry. But be warned: although I have never seen any data being lost in this way, nor have heard any thereof, I still recommend BACKING UP anything you would be really sorry to lose. Don't backup stuff you can just download again in case anything should go wrong.

---

### Post by brett824 on 2005-10-22
Thanks! I'm still not sure I want to install ubuntu though.

---

### Post by pauljwells on 2005-10-22
you posted in the mac forum. You can't resize an hfs partition - take a look at [http://ubuntuforums.org/showthread.php?t=80274](http://ubuntuforums.org/showthread.php?t=80274) . If you are installing on a PC then it's easy as Jenda says. Ubuntu is excellent if you are prepared to spend a little bit of time learning how to use it.

---

### Post by brett824 on 2005-10-22
Eh seems like too much work

---

### Post by Jenda on 2005-10-23
Do you have a Mac or a PC?

---

### Post by PaganHippie on 2005-10-23
[COLOR=Black]Actually, according to [/COLOR][SIZE=-1][COLOR=#008000][COLOR=Black][www.gnu.org/software/parted/parted.html]("http://www.gnu.org/software/parted/parted.html") you can indeed resize (shrink, in this case) hfs and hfs+ partitions.  Making a backup first is always sound advice, of course.
[/COLOR]
[/COLOR][/SIZE]

---

### Post by brett824 on 2005-10-23
[QUOTE=Jenda]Do you have a Mac or a PC?[/QUOTE]

Mac...

And Whoa that GNU-Parted thing looks way too hard.

---

### Post by Jenda on 2005-10-23
AFAIK, GNU parted is what the installer uses by default, and the partitioner in there is quite simple - I really love it's simplicity.
I can't guarantee the quality/risk of the resize, though. No experience.

---

### Post by brett824 on 2005-10-23
The only thing stopping me now is the risk of losing data..

---

### Post by Jenda on 2005-10-23
Hmm... all you need is a Mac user who can tell you how high the risk is...

---

### Post by pauljwells on 2005-10-24
Hey brett824, did you take a look at the thread I linked to? A lot of the info in there would be useful to you for making a bootable backup of your entire mac install, just in case it all goes horribly wrong. It's worth doing this even if you decide not to install ubuntu.

I've never tried gnu-parted on a mac (I ever knew there was a mac version, thanks for the info paganhippie!), and I used Acronis Disk Director to do it on my PC. I read one too many stories of hosed HDs from using parted and took the safe way out. Backup, repartition using Disk Utility, copyback the back-up (using Carbon Copy Cloner, a great little app)

I don't want to 'diss' gnu parted - I've never tried it myself, and these things always seem to be better developed for PC than mac because of the much larger user base.

It's not a trivial matter to install ubuntu, and unfortunately some of the hardest parts have to be dealt with at the first steps. Once it's working, trust me! it's very easy to use.

Good luck

---

### Post by brett824 on 2005-10-24
I have no way of backing up my hard drive. I have no money to use on buying an external HD

---

### Post by onesojourner on 2005-10-24
If I were you I would look into getting just a harddrive inclosure from newegg for about 20 bucks and putting an old 20g drive in it.

---

### Post by brett824 on 2005-10-24
I don't have 20 bucks.. what part of having no money don't you people understand?

---

### Post by jdp on 2005-10-24
Having no money is one tough thing, I do understand the limits there.  Do you have computer savy friends that would let you borrow an external drive/enclosure?  Maybe you know someone with and iPod that would let you borrow it to wipe and use as a temp HDD to get the install done.  For the iPod route, if they have all their music saved on their computer and have any other files on the iPod saved on the computer you can just erase the iPod and use it like a HDD through Disc Utility.  Then do the CCC route to make a bootable backup of your HD on the iPod.  I've done it before on my 3g 20GB iPod.  Luckily my iBook only has a 20GB HD. :)  They'll have to wipe and re-install the iPod, but if they are savvy they know it won't be a huge deal to loan an iPod for a couple nights and will be able to restore it easily.

---

### Post by brett824 on 2005-10-24
Don't have an iPod and don't have any computer savy friends... I actually don't have many friends at all. I live a sad life :(

---

### Post by pauljwells on 2005-10-24
LOL!! You're making new friends here :)

Seriously, in your position I would do it this way: back up all your data (your entire home directory) to CD or DVD. Pop the OS X install disk in and run Disk Utility to wipe the HD and repartition with two more or less equal partitons. Leave the first (upper one in Disk Utility) as free space and the second as hfs. Reinstall OSX and run the software update as many times as needed. Reinstall all your other apps (hope you still have all those CDs...) Finally, boot from the CD and run disk utility to repair permissions and then you'll have a nice clean OSX install, which you probbly don't really have right now. Copy all your data back from the CDs. As a hint, don't try to overwrite the folders (Docments, Library etc) in your Home, but copy across all the sub directories. For sure you'll end up with a bit of work trying to get things back exactly as you liked them, but if you don't kinda like this sort of stuff then you probably shouldn't be trying to learn linux.

Then download the breezy-ppc install iso and burn it to CD. Reboot from this CD and let Ubuntu install itself on the free space, which it does more or less automatically. You want to be connected to internet via an ethernet cable while you're installing, since most of the install comes from the network rather than the CD. Broadband is essential.

Your other options are stick with OSX until you can afford some extra disks to make life easier, or bin OSX and just run ubuntu (brave desicion)

Good luck, try to keep near a connected computer if you need to ask for help while the install is going on.

---

### Post by brett824 on 2005-10-24
[QUOTE=pauljwells]LOL!! You're making new friends here :)[/QUOTE]

That makes me sad...

[QUOTE=pauljwells]Seriously, in your position I would do it this way: back up all your data (your entire home directory) to CD or DVD. Pop the OS X install disk in and run Disk Utility to wipe the HD and repartition with two more or less equal partitons. Leave the first (upper one in Disk Utility) as free space and the second as hfs. Reinstall OSX and run the software update as many times as needed. Reinstall all your other apps (hope you still have all those CDs...) Finally, boot from the CD and run disk utility to repair permissions and then you'll have a nice clean OSX install, which you probbly don't really have right now. Copy all your data back from the CDs. As a hint, don't try to overwrite the folders (Docments, Library etc) in your Home, but copy across all the sub directories. For sure you'll end up with a bit of work trying to get things back exactly as you liked them, but if you don't kinda like this sort of stuff then you probably shouldn't be trying to learn linux.[/QUOTE]

I really wish I understood what you just said.

[QUOTE=pauljwells]Then download the breezy-ppc install iso and burn it to CD. Reboot from this CD and let Ubuntu install itself on the free space, which it does more or less automatically. You want to be connected to internet via an ethernet cable while you're installing, since most of the install comes from the network rather than the CD. Broadband is essential.[/QUOTE]

That I could have guessed by myself

[QUOTE=pauljwells]Your other options are stick with OSX until you can afford some extra disks to make life easier, or bin OSX and just run ubuntu (brave desicion)

Good luck, try to keep near a connected computer if you need to ask for help while the install is going on.[/QUOTE]

Eh.

---

### Post by farmer on 2005-10-25
I don't want to insult you, but judging by your response, I don't think that linux or Ubuntu is for you. 

OS X is a really great OS, better than linux for most people. It's just us weirdoes that like a challenge. If you can't understand what pauljwells is saying, then you either need to put in the time to research what that means or stick with OS X. 

Learn about mac os x, what it is, how it works. [Wikipedia]("http://en.wikipedia.org") is a great place to start. Teach yourself about how any UNIX system is set up. 

Linux on PPC is very iffy right now. It doesn't work nearly as well as it does on x86. If you didn't understand that, look it up. You'll become much smarter for it. 

If you still want to go through with it, [Wikipedia]("http://en.wikipedia.org")  and [Google]("http://www.google.com") are your friends. 

- chas

---

### Post by brett824 on 2005-10-25
I understood what he said. I was just saying that to be funny.I'm not that stupid of a person...

---

### Post by Jenda on 2005-10-26
[QUOTE=brett824]I understood what he said. I was just saying that to be funny.I'm not that stupid of a person...[/QUOTE]
Well that's cool.
I'm all for humor and all, but it can sometimes be misleading. A reasonable solution is making yourself clear somewhere in the post.

There are indeed people who would not understand the instructions, and they aren't necessarily stupid. You won't find many of them trying out GNU/Linux, though... I honestly believe Linux is not for everyone. I'm not saying that it's geekware (look, I'm in the Marketing Team, OK?), it's just that there aren't enough services available for this to be 100% reliable YET.

---

