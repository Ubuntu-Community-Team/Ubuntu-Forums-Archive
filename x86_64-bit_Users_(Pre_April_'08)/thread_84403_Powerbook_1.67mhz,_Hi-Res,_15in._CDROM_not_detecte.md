---
title: "Powerbook 1.67mhz, Hi-Res, 15in. CDROM not detected"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by scalvin on 2005-10-31
I can't get the Ubuntu intaller to recognize my cdrom. I get to the graphical installer startup, language, location etc., but it asks for a floppy(!) with my cdrom driver. It asks me to select a module and then what is the /dev/cdrom address of my drive. It says no common drive found, or something. I tried /cdrom, /dev/ptmx, /dev/cdrom-which is the default. None work. Any ideas? Is my superdrive cd/dvd dual layer too new or?

---

### Post by wheeler@amnh.org on 2005-10-31
Me too--I have 17" (1680x1050)

---

### Post by scalvin on 2005-11-05
[QUOTE=wheeler@amnh.org]Me too--I have 17" (1680x1050)[/QUOTE]

I guess it's just me an you dude.

---

### Post by matthis on 2005-11-06
Same problem here.... new hardware not detected by Ubuntu yet, maybe?

---

### Post by monway on 2005-11-06
Have any of you guys tried the ubuntu breezy dvd install ? ubuntu has dvd install images to download via jigdo or bittorrent. This is what I use for my Aluminum powerbook 17" 1.33ghz I too have a superdrive and it would make more sense if you cannot read from a cd then try the dvd. Let me know if that works for you if not I'll try the same computer you have in my lab and see how that goes and see if I can find a solution for you.
Cheers.

---

### Post by farruinn on 2005-11-06
How new are these powerbooks you're all having trouble with? Did you use them with hoary?

---

### Post by scalvin on 2005-11-07
[QUOTE=farruinn]How new are these powerbooks you're all having trouble with? Did you use them with hoary?[/QUOTE]

These are the new 'Hi-Res' Powerbooks introduced about a month ago. I previously had a 1.25mhz, 15in. Powerbook identical to the new one with these differences: 1.67mhz, uses DDR2 SDRAM, and does dual layer DVD burning.

---

### Post by hakkr on 2005-11-09
No solutions here. But you can add me as another new 15"
hi-res powerbook owner with the cdrom detection problem.
I did use the breezy badger dvd installer. 

-Vic

---

### Post by parry on 2005-11-11
[http://forums.gentoo.org/viewtopic-t-396455.html?sid=1be028f82602a972d010ba8328a44eaf](http://forums.gentoo.org/viewtopic-t-396455.html?sid=1be028f82602a972d010ba8328a44eaf)

Gentoo folks have made available a bootable CD with latest patches - I tested it on my new 15" PB and it detects most everything except the trackpad and of course wireless. If anyone is interested in taking the patches and making a experimental Ubuntu install CD, please refer to the above URL.

HTH
Parry

---

### Post by scalvin on 2005-11-12
[QUOTE=parry][http://forums.gentoo.org/viewtopic-t-396455.html?sid=1be028f82602a972d010ba8328a44eaf](http://forums.gentoo.org/viewtopic-t-396455.html?sid=1be028f82602a972d010ba8328a44eaf)

Gentoo folks have made available a bootable CD with latest patches - I tested it on my new 15" PB and it detects most everything except the trackpad and of course wireless. If anyone is interested in taking the patches and making a experimental Ubuntu install CD, please refer to the above URL.

HTH
Parry[/QUOTE]
Ditto. I tried the Gentoo experimental minimal install CD and it detected my cdrom also. Too bad Gentoo is so damn hard to install without a PhD in geek.;)

Obviously, I'm not going to get into patching up a Ubuntu install, I wouldn't know where to start. If anyone out there does though, i'd be happy to try to install.

---

### Post by digyourownhole on 2005-11-12
So, no solution to this problem yet?! Too bad.
I am a big Gentoo user and can't wait to install gentoo on my new high resolution Powerbook, unfortunately I am very very busy at the moment and need my Powerbook all the time. I thought I'd use Ubuntu live CD, but no luck with the new DVD-drive.

Gentoo is not that hard to install, all you need to do is read the manual, piece of cake (and i just have my Ba. in Geek....)

Hope Ubuntu will work soon.

---

### Post by scalvin on 2005-11-26
[QUOTE=monway]Have any of you guys tried the ubuntu breezy dvd install ? ubuntu has dvd install images to download via jigdo or bittorrent. This is what I use for my Aluminum powerbook 17" 1.33ghz I too have a superdrive and it would make more sense if you cannot read from a cd then try the dvd. Let me know if that works for you if not I'll try the same computer you have in my lab and see how that goes and see if I can find a solution for you.
Cheers.[/QUOTE]

I didn't try that yet, but others have said that the problem is due to some new thing about the IDE controller in these new powerbooks. Would using a DVD image therefore make a difference?

---

### Post by scalvin on 2005-11-27
[QUOTE=scalvin]I didn't try that yet, but others have said that the problem is due to some new thing about the IDE controller in these new powerbooks. Would using a DVD image therefore make a difference?[/QUOTE]

Didn't work. Again, the Ubuntu system and installer start up fine from CD or DVD. It's just during installation that "no common cdrom detected" error stops the process. We need a new driver available or built into the cdrom detection of the installer to be able to go further. How or when this will be solved I have no idea. It's all in the hands of the Linux Gods now.

---

### Post by villeneuve on 2005-12-01
Any News????

---

### Post by mrnoname on 2005-12-05
I am also interested in ubuntu working with powerbook G4. Gentoo is not an option for me... want ubuntu :)

---

### Post by gusto on 2005-12-10
Having the same issue as well. Just wanted to bump the thread.

---

### Post by mrnoname on 2005-12-11
Cant somebody test the patch?

[https://bugzilla.ubuntu.com/show_bug.cgi?id=18579](https://bugzilla.ubuntu.com/show_bug.cgi?id=18579)

//Mrnoname
Really really want to run ubuntu on my powerbook, mac os x is nothing for me

---

### Post by villeneuve on 2005-12-11
I found this site where are listed all the needs to run Linux ( Ubuntu or Gentoo ) on new PowerBook5,8.

I think that problem is not to test the patch but how create the patched iso.

Hope some Linux Guru will help us!!


PS: MAC OS X IS NOT NOTHING!!!

---

### Post by mrnoname on 2005-12-11
Ok, Mac OS X is something, but not for me... i will like Ubuntu better. Want to feel home again.

Where do we find a Guru when we need one?

---

### Post by scalvin on 2005-12-11
[QUOTE=mrnoname]Ok, Mac OS X is something, but not for me... i will like Ubuntu better. Want to feel home again.

Where do we find a Guru when we need one?[/QUOTE]

I'm not getting the impression that these forums are very well read. The mailing list however is over the top, but predominently intel platform types. So, again, praying to the Linux gods is probably the best thing we can do. I'm just hoping we don't have to wait until the next Ubuntu release to be supported again. Keep hope alive.

---

### Post by mrnoname on 2005-12-12
Anyone who knows if this problem is fixed in dapper?

---

### Post by Z3K3 on 2005-12-22
[http://cdimage.ubuntulinux.org/kubuntu/dvd/current/dapper-dvd-powerpc.iso](http://cdimage.ubuntulinux.org/kubuntu/dvd/current/dapper-dvd-powerpc.iso)

The bug report says fixed in Dapper.. I'm downloading this iso now and going to attempt install tonight.

Z3K3

---

### Post by mrnoname on 2005-12-23
Hope it works...

---

### Post by Z3K3 on 2005-12-23
No luck first round.  The cd booted, I was able to get the yaboot prompt, but upon install the screen resolution "freaked" out for lack of a better term.   It went black with fast moving colour lines at the top.

I'm going to see if I can pass a "text" argument to the installer, I'm guessing its loading the GUI installer by default... will keep you posted.

Z3K3

---

### Post by scalvin on 2005-12-23
[QUOTE=Z3K3]No luck first round.  The cd booted, I was able to get the yaboot prompt, but upon install the screen resolution "freaked" out for lack of a better term.   It went black with fast moving colour lines at the top.

I'm going to see if I can pass a "text" argument to the installer, I'm guessing its loading the GUI installer by default... will keep you posted.

Z3K3[/QUOTE]

Me niether. I used the daily Kubuntu iso. It got through the installer and detected the CD but it said it had no kernel modules. It said that it might be a mismatch from the kernel on the cd and the kernel in the archive, WTFTM.

I'll look for a different image or wait.

steve

---

### Post by Z3K3 on 2005-12-23
I tried downloading YellowDogLinux 4.01 it didn't work either, must be a similar issue, not sure what with, partially the CDROM and the graphics?

Anyhow, I don't particularly like Gentoo, and I run 3 other Ubuntu workstations, so I guess I'll join the crew in waiting... I wish I new more about how to debug this and help..

---

### Post by n_i_x on 2005-12-24
Same issue.. used the DVD installer of Ubuntu.  No CD-ROM device found.

Guess I'll sit around and wait with you fellas... pass the cocoa and keep that fire going.

---

### Post by Z3K3 on 2005-12-25
I tried the newest snapshot of ubuntu dapper dvd today (i think it was december 23rd snap) and didn't get anywhere near the CD problem.. the screen goes a grey/green, and flickers a lot.  Not sure what to do here.. looking for a paramater to pass..

something like.. install text.. but that doesn't work either...

---

### Post by scalvin on 2005-12-26
Has anyone got the problem with Dapper that complains of no kernel modules....probably to due to a mismatch of the install kernel and the kernel in the archive?

---

### Post by harloc on 2005-12-28
has anyone resolv the problem?
I want install the ubuntu in my powerbook5,8 but cdrom not detected.
thanks,
marco

---

### Post by scalvin on 2006-01-04
Anyone solved this?

The thread that wouldn't go away. Really.

---

### Post by scalvin on 2006-01-12
Has anyone any ideas, or has anyone installed on the new Powerbooks? Now not so new.

---

### Post by Z3K3 on 2006-01-12
Wow, I was able to get OSX86 working on one of my intel workstations before getting ubuntu on my 1.67GHZ powerbook!  

I guess I'll give up for now.. I don't have the expertise or the time to figure out why this isn't working... won't someone make this work.. please. :cool:

---

### Post by scalvin on 2006-01-12
[SIZE=3][COLOR=DarkOrange]:D :D :D Good News, I hope. This bug is supposedly fixed!!:) :) :)
[SIZE=5][COLOR=SeaGreen]https://launchpad.net/malone/bugs/6168[/COLOR][/SIZE]
 [/COLOR][/SIZE]

---

### Post by scalvin on 2006-01-15
[QUOTE=scalvin][SIZE=3][COLOR=DarkOrange]:D :D :D Good News, I hope. This bug is supposedly fixed!!:) :) :)
[SIZE=5][COLOR=SeaGreen]https://launchpad.net/malone/bugs/6168[/COLOR][/SIZE]
 [/COLOR][/SIZE][/QUOTE]

Yeah, well, that bug was fixed. Now it will install upto installing the bootloader. When I try to load the kernel maunually in OF it won't do it, so I'm thinking there are other things going on.

---

### Post by villeneuve on 2006-01-19
Hi to all,
I tried the beta version of Ubuntu 6.04 called Dapper Flight 3 and it works fine on my powerbook5,8 15".

I'm new to ubuntu distro , usually I worked with rpm distro like Fedora or Sun JDS , but by my point of view it seems that all works fine.


I will wait your impression!!

PS: I think that the best distro for Mac will be Yellow Dog 4.1 so I will migrate      to it as soon as possible when the free iso will be available to download.

---

### Post by Donderwolkje on 2006-02-17
i have exactly the same problem

so this cd Ubuntu sent us is just defective?

i would like to just see what ubuntu is, i've never gotten further as the cd rom-drive is not found, while running the cd in a brand new powerbook 15"

too bad

---

### Post by thomasbosboom on 2006-02-26
The latest nightly builds seem to work OK. The install finishes, only the default trackpad speed is too low. 
this page :
[http://joh.deworks.net/powerbook/](http://joh.deworks.net/powerbook/)
has some good hints on the trackpad issue.

Most other stuff such as the function keys (sound, brightness etc) seem to work fine.

Thomas

---

### Post by yuvalsarig2005 on 2006-02-27
Check with the support of Ubuntu and you can try to send them E - Mail.
I am sure they will be able to give you good answer. 
Check you software.
I am using iBook G4 and this is working well.

Another opption is to oder Ubuntu CD. This is free
and maybe this will work.

What CD you used?

---

### Post by alegomes on 2006-03-01
Sorry but, where do I get the latest Dapper daily build? From launchpad? I have the same CD-ROM detection problem and wanna try the solutino poste here.

regards

---

### Post by alegomes on 2006-03-01
[QUOTE=alegomes]Sorry but, where do I get the latest Dapper daily build? From launchpad? I have the same CD-ROM detection problem and wanna try the solutino poste here.

regards[/QUOTE]

I found it. Thank you all.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by alegomes on 2006-03-02
Feedback: Ubuntu 6.10 Live CD Built on 20060301 works fine with PowerBook G4 17''. Didn't make a deep test yet but, every I need (Firefox and Gaim) is working right now.

thanks for this thread.
Ale!

---

### Post by sonic328ci on 2006-03-11
got the same problem... powerbook g4 15" 5.8 - new hi res model...

i tried the DVD version of ubuntu, but it can't detect my superdrive.

EDIT:

im now trying to get most recent version of the ubuntu live cd from cd [www.cdimage.ubuntu.com](www.cdimage.ubuntu.com)

i will tell you if this works...

EDIT: just downloadet the most recent ubuntu live dapper, and... ...IT WORKS!!!
it took a little long to load, but it works... it only hung up, as i tried to shut it down (last msg was: sending term signal), so i had to shut down manually by holding the poer button...

i hope there will be a final, working version soon...

---

