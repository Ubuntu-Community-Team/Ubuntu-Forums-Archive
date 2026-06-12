---
title: "Desktop Suddenly Changed"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by diddler on 2007-06-03
I am here checking my posts and trying to follow advice when my desktop suddenly went crazy.  The wallpaper disappeared, the icons rearranged themselves on the desktop and now will not let me move them to where they were.  I am about ready to see how well Ubuntu on a 64-bit platform can fly.

---

### Post by diddler on 2007-06-03
OK, rebooted and everything is back to normal.  If this were Windows I would say I had a virus, but that doesn't happen in Linux, right?

It is becoming apparent that Linux will never be more than a toy.  I guess for productivity I will have to reload my (shudder) XP64.

---

### Post by diddler on 2007-06-03
I have downloaded Aegis Virus checker but it refuses to show up on any menu so I guess I have to run it from a terminal.

---

### Post by Mr_bleu on 2007-06-03
I don't remember the exact location, (I'm reinstalling at the moment) but I do believe it's in the /usr/bin/ folder.  You can check by going to System>administration>synaptic manager.
Then type aegis in the Search box after hitting the button.  Right click and view Properties?  If that's right (it's somewhere right there) it'll show you where the files are installed.  It IS possible to get a virus in linux.  It's just not as common as with mr. gates' software.

---

### Post by diddler on 2007-06-03
Well, synaptic said it was installed, but when I tried to run it, terminal said it WASN'T installed, so I re-installed.  After I was done, I tried to run it in the terminal but it demanded options that I don't know.  It still has not shown up on any menu so I guess I will have to search for documentation to find out how to get it to run manually.

---

### Post by Mr_bleu on 2007-06-03
Perhaps my directions weren't clear.
Go to system>administration>synaptic manager
Once there click the search button. 
Type aegis in the search box.
Right click on the file and select properties.  There will be some tabs there.  Search for the one giving the file locations.  It will have /usr/bin and a bunch more listed.

---

### Post by david_2001 on 2007-06-03
> **diddler said:**
> OK, rebooted and everything is back to normal.  If this were Windows I would say I had a virus, but that doesn't happen in Linux, right?

It is becoming apparent that Linux will never be more than a toy.  I guess for productivity I will have to reload my (shudder) XP64.
If that were Windows, I would say that it's a feature rather than a virus!  My work laptop, which runs Windows 2000, has this problem and many others have experienced the same running XP too, e.g. [http://groups.google.fr/group/microsoft.public.windowsxp.newusers/browse_thread/thread/44ac393fee8fe48b/4a3e912f3ee245fb](http://groups.google.fr/group/microsoft.public.windowsxp.newusers/browse_thread/thread/44ac393fee8fe48b/4a3e912f3ee245fb)

---

### Post by diddler on 2007-06-03
Found aegis, got it to run, didn't find anything (big surprise).  Aegis is still a no show on the menus so I guess I will always have to run it manually.  It will be nice when someone develops a real-time virus scanner for Linux.

---

### Post by RAOF on 2007-06-03
> **diddler said:**
> Found aegis, got it to run, didn't find anything (big surprise).  Aegis is still a no show on the menus so I guess I will always have to run it manually.  It will be nice when someone develops a real-time virus scanner for Linux.

But it wouldn't do anything.  There aren't any linux viruses in the wild that I know of, so the virus scanner's database would be empty!  The only thing virus scanners on Linux are good for at the moment is to stop you from inadvertently hiding *Windows* viruses that you can't run :).

---

### Post by diddler on 2007-06-03
> **david_2001 said:**
> If that were Windows, I would say that it's a feature rather than a virus!  My work laptop, which runs Windows 2000, has this problem and many others have experienced the same running XP too, e.g.

My problem was more than just icons rearranging themselves.  The wallpaper disappeared as well, and rebooting solved the problem.  I just have to be more aware of what actions I take in relation to other programs as I work with this stuff.  I am sure it was a software bug, since I have encountered bugs in almost every app I have tried.

---

### Post by diddler on 2007-06-03
> **RAOF said:**
> But it wouldn't do anything.  There aren't any linux viruses in the wild that I know of, so the virus scanner's database would be empty!  The only thing virus scanners on Linux are good for at the moment is to stop you from inadvertently hiding *Windows* viruses that you can't run :).

Yes, BUT it would do two things. 1) It would help [COLOR="Red"]considerate[/COLOR] Linux users from propagating Windows virii; and 2) It would provide psychological comfort to Microsoft refugees as they got used to a system that didn't need constant protection from every nut-job hacker with an Internet connection.

Never underestimate the power of imaginary friends!

---

### Post by diddler on 2007-06-03
> **RAOF said:**
> But it wouldn't do anything.  There aren't any linux viruses in the wild that I know of, so the virus scanner's database would be empty!  The only thing virus scanners on Linux are good for at the moment is to stop you from inadvertently hiding *Windows* viruses that you can't run :).

And, if you read my posts carefully, my virus suggestion was tongue-in-cheek.  I got into the Aegis issue because it is another way for me to get experience with installing, finding, and running Linux programs, something that seems to change with each app installed.  What I DO believe is that the bug situation obviates the need for anyone to write Linux virii.  Bugs seem to be welcomed by the old timers for the exercise they provide in developing and improving apps, but they are extremely irritating to newbies who just want to get their system running with some degree or reliability.  :)

---

### Post by RAOF on 2007-06-04
> **diddler said:**
> Yes, BUT it would do two things. 1) It would help [COLOR="Red"]considerate[/COLOR] Linux users from propagating Windows virii; and 2) It would provide psychological comfort to Microsoft refugees as they got used to a system that didn't need constant protection from every nut-job hacker with an Internet connection.

Never underestimate the power of imaginary friends!

(1) is certainly a fine idea, for people on mixed linux/windows networks, or running a mail server, or such.  I don't think it's such a necessity that it should be installed & running by default, though.

Does Aegis have a GUI?  If it does, it's a bug that it doesn't get a menu item.  Bugs should be filed on launchpad, and it appears that [someone has](https://bugs.launchpad.net/ubuntu/+source/aegis/).  The Aegis package is in universe, though, which means that it's community maintained.  This seems like it should be a simple bug; if you care about it, you could try to fix it yourself and upload the [debdiff](https://wiki.ubuntu.com/MOTU/Recipes/Debdiff?highlight=%28debdiff%29) to the bug.  I'd be happy to help.

If not, I'll try to have a look at it myself sometime.

As for your other bugs, launchpad.net is the place to go.  Unless we know about the bugs, we can't fix them :).  Don't assume that your bug has already been filed - many haven't.  Filing a bug isn't guaranteed to fix that bug, but it's unlikely that an unfiled bug will get fixed!

---

### Post by Kilz on 2007-06-04
> **diddler said:**
> Yes, BUT it would do two things. 1) It would help [COLOR="Red"]considerate[/COLOR] Linux users from propagating Windows virii; and 2) It would provide psychological comfort to Microsoft refugees as they got used to a system that didn't need constant protection from every nut-job hacker with an Internet connection.

Never underestimate the power of imaginary friends!

Just a question on #1. 
Exactly how would Linux users propagate a windows virus? The only way I could even think is to send purposely forward unknown email attachments. Isnt this something common sense would tell you not to do?

---

### Post by RAOF on 2007-06-04
> **Kilz said:**
> Just a question on #1. 
Exactly how would Linux users propagate a windows virus? The only way I could even think is to send purposely forward unknown email attachments. Isnt this something common sense would tell you not to do?

If you're running a mail server, it's polite to scan the incoming & outgoing mail for viruses, even though you yourself are immune.

Or if you've got a Samba share, sharing to some windows boxes, and one of the files on it is infected with a virus.

There are situations in which it's useful, but mainly only with a network.  Nothing really for a desktop use-case.

---

### Post by Feba on 2007-06-04
Sounds like a bug in GNOME, maybe not Ubuntu.

I don't see why you say this makes linux "only a toy". Windows has a metric ton of problems and viruses, you wouldn't call it a toy. If anything is a toy, it's 64 bit OS, which I don't quite see your need for. And if we're talking about problems, I don't see how XP64 is improving your situation any....

---

### Post by diddler on 2007-06-06
> **Kilz said:**
> Just a question on #1. 
Exactly how would Linux users propagate a windows virus? The only way I could even think is to send purposely forward unknown email attachments. Isnt this something common sense would tell you not to do?

Well, it is amazing how often even smart people screw up.  My sister, who has the "Power of Cisco certification" once sent out a mass email warning everyone about the horrible virus lurking in the Windows sys folder, thereby getting everyone on her email list to delete a necessary .dll just because it had a nasty looking icon (I did manage to send out a retraction immediately, because I happened to be on-line when her message went out).  This hoax has been around for years and people still fall for it everyday.  If the attached file doesn't affect your Linux system, why would you think that it will affect the Windows users you send it to?  If you don't have any type of virus checker, there is no way for you to KNOW the attachment is infected!

---

### Post by diddler on 2007-06-06
> **Feba said:**
> Sounds like a bug in GNOME, maybe not Ubuntu.

I don't see why you say this makes linux "only a toy". Windows has a metric ton of problems and viruses, you wouldn't call it a toy. If anything is a toy, it's 64 bit OS, which I don't quite see your need for. And if we're talking about problems, I don't see how XP64 is improving your situation any....

Can't argue with you there, except to say that I have never had a virus problem on Windows, because I DID pay attention to what I was doing, but also had some good, non-Microsoft, applications for virus and other things that ran correctly every time, all the time.  I realize that Linux is "free" and one shouldn't look a gift horse in the mouth (whatever the hell THAT means) but still, the big advantage to commercial applications is that they generally have to work well in order to be commercially successful.  I know it is unreasonable to expect software developed by individuals for open distribution to be perfect, yet I used a significant amount of Windows based "shareware" that ran without any problems.  

I left Windows NOT because of the program itself, but because of the corporate policies of Microsoft.  If the powers that be at Microsoft were not a bunch of money grubbing, monopolistic, power-mongers, I would probably still be using Windows.

I do find it interesting though that I seem to get more responses to my perceived "trashing" of Linux than I get help on some of the problems I am having with it.  But that is not unexpected either.:D

---

### Post by Feba on 2007-06-06
Eh, anyone wanting a perfect OS needs to develop a single set of hardware and an infinite  number of contributors. 

Windows isn't perfect, OSX isn't perfect, and linux isn't perfect. Linux works better for us though, which is why we use it. If you have problems with a distro, try another one! Linux doesn't cost hundreds of dollars for each copy, there's no reason not to try other things if the first distro you try doesn't work out for you.

---

### Post by diddler on 2007-06-07
> **Feba said:**
> Eh, anyone wanting a perfect OS needs to develop a single set of hardware and an infinite  number of contributors. 

Well, you really hit the nail on the head.  Since hardware development seems to precede software development by 2-3 years, it is a wonder we can get ANYTHING done.  I had a motherboard with USB capability while Win95 was the latest OS.  Windows did not manage USB until Win98SE!  And as you pointed out, 64-bit hardware does NOT mean usable 64-bit software. 

As far as playing musical distro's, that is not an option.  I do have numerous distros on disk, but Ubuntu works well enough to try and master.  Actually I have done some distro surfing - I have tried Red Hat, Linspire, Debian, and SUSE.  Ubuntu (and here is the scary part) seems to be the most user friendly.  Only time will tell.  But I AM committed, and one day I will probably be writing some of the buggy software.

We should really move this thread to the "Computer Philosophy" forum.:D

---

### Post by RAOF on 2007-06-07
> **diddler said:**
> ...And as you pointed out, 64-bit hardware does NOT mean usable 64-bit software. 
...

Well, as long as you're running Windows.  I've been happily running the 64bit version of Ubuntu since the end of the Hoary development cycle :).

Then again, I do sometimes miss flash.  But only sometimes :).

---

### Post by Feba on 2007-06-07
> Since hardware development seems to precede software development by 2-3 years, it is a wonder we can get ANYTHING done.

well yeah. the Open Source community especially is 99% people making programs that THEY want and THEY need, obviously if someone doesn't want the newest thing for themselves they aren't going to work on it.

---

### Post by diddler on 2007-06-07
> **RAOF said:**
> Well, as long as you're running Windows.  I've been happily running the 64bit version of Ubuntu since the end of the Hoary development cycle :).

Then again, I do sometimes miss flash.  But only sometimes :).

Actually, I have NO IDEA which of my problems may be related to the 64-bit system with Ubuntu (probably none).  With Windows there was no mystery.  Basically, there were NO 64-bit programs.  Half my peripherals didn't work because there were no 64-bit drivers.  With Ubuntu, at least my printers and ONE of my scanners work (and the non-working scanner is a HP problem, NOT a Linux problem).  I have no problem with 64-bit Ubuntu.  At least I am making an ATTEMPT to fully utilize the hardware.:cool:

---

### Post by Absorbed on 2007-10-19
My wallpaper and icons just disappeared, but is fixed now without rebooting. It seems to be a problem with nautilus.

[http://ubuntuforums.org/showthread.php?p=3567702](http://ubuntuforums.org/showthread.php?p=3567702)

---

