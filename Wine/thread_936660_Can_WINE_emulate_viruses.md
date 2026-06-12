---
title: "Can WINE emulate viruses?"
date: 2008-10-03
forum: Wine
---

### Post by askyourpc.com on 2008-10-03
I was wondering this question of whether wine could emulate a windows virus. Or is it unlikely and why is that?
Thanks

---

### Post by 3rdalbum on 2008-10-03
Wine doesn't emulate anything :-D

But seriously, viruses are Windows programs. So Wine can theoretically run them. In reality, many won't run because they try to fiddle with the running Windows internals, which of course aren't present on Linux. Some use undocumented system calls from Windows which are unlikely to be present in Wine (they're undocumented, after all, and the only way the virus-writers find them is by disassembling the Windows binary - the Wine devs don't do that).

Viruses stay resident on the system by installing themselves into parts of Windows that mean they'll get executed at each bootup. Wine doesn't boot up when Linux does, so a Windows virus could only run on Linux when Wine starts up. Or, it would, if Wine followed Windows' startup procedure, which it doesn't.

Here's a fully-fledged article I wrote: [How do you get down off an elephant?]("http://bigbolshevik.blog.friendster.com/2008/07/how-do-you-get-down-off-an-elephant/") that explains things in more detail.

---

### Post by david_kt on 2008-10-03
> **askyourpc.com said:**
> I was wondering this question of whether wine could emulate a windows virus. Or is it unlikely and why is that?
Thanks

Although more difficult to run, yes, sometimes it could run. If you want to try, put an infected file and run it. Or better still, get a virus and run it.

But that would also limited to your home directory, not system directory.

DK

---

### Post by jim_24601 on 2008-10-03
Up to a point. Wine's emulation for certain popular viruses such as SafeDisc, SecuROM etc. is pretty good these days, and many apps infected with these viruses run well.

---

### Post by ronnielsen1 on 2008-10-03
I actually ran a virus by mistake in wine. I reinstalled wine and the problem was fixed. Here's a humorous article on someone running viruses in wine

> Out of the five Windows viruses I ran under Wine, not a single one was able to send email and propagate itself. When I went out of my way to be part of the Windows community by doing my part to propagate Windows viruses (lots of Windows users seem to think this is important, seeing as how they run random executables *and* use Microsoft Outlook and Internet Explorer) I discovered that it couldn't easily be done with GNU/Linux tools. Oh sure, I could *manually* forward these viruses to the folks in my address book, but where's the fun in that? Besides, these viruses usually lie in the From: line and use a handful of different Subject: lines. As a GNU/Linux user, I really don't want to miss out on these important functionalities.
  I tip my hat to the creators of the SomeFool virus, for actually (albeit temporarily and minimally) affecting my Linux experience. However, if that's the most damage I can get by running viruses with Wine under a dummy account, then it's clear that the Wine developers have a long way to go before Wine is truly Windows compatible.
  
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

---

### Post by Espryon on 2008-10-03
In theory wine can run them but you would have to change the default ubuntu settings and by choice chose to run them and if they try to run something with the root it would need the password too

---

### Post by askyourpc.com on 2008-10-03
Good stuff to know. It sounds as if Ubuntu has a totally different immune system. Where viruses tend to be event triggered such as windows boot up which doesn't happen in WINE. 
Thanks

---

### Post by asdfoo on 2008-10-03
> **david_kt said:**
> Although more difficult to run, yes, sometimes it could run. If you want to try, put an infected file and run it. Or better still, get a virus and run it.

But that would also limited to your home directory, not system directory.

DK

huh? It's not limited to anything, any file which your logged in user can access any program running under Wine can access.

a program running under Wine can also attempt to escalate its privileges through exploiting bugs in Linux.  

While this might be uncommon or not exist yet, it's entirely feasible from a technical point of view.

---

### Post by david_kt on 2008-10-03
> **asdfoo said:**
> huh? It's not limited to anything, any file which your logged in user can access any program running under Wine can access.

a program running under Wine can also attempt to escalate its privileges through exploiting bugs in Linux.  

While this might be uncommon or not exist yet, it's entirely feasible from a technical point of view.

You are right, but......
We are talking about "windows virus", which until now "do not understand" how to access linux file system yet.

From technical point of view, it should be design to attack linux file system in order to do some harms.

But offcourse even windows virus could affect linux performance such as slowing it down or damaging all files in home directory. But so far, that is all it could do technically.

DK

---

### Post by SunnyRabbiera on 2008-10-03
If you got a virus in wine it would not do much, though there are some that have caused some issues here and there.

---

### Post by wineman on 2008-10-04
dude, you can have viruses run in wine, but then when you stop the win32 app, or process (ps -e|grep [name], kill [psnumber]) the virus is immobalised. On my Wine ubuntu rig i have 3 big virusses and none have given me any trouble.
The only place that they can go is ~/.wine/drive_c, and that's easily deletable.... 

So yes, but they aren't a threat.

---

### Post by asdfoo on 2008-10-05
> **wineman said:**
> dude, you can have viruses run in wine, but then when you stop the win32 app, or process (ps -e|grep [name], kill [psnumber]) the virus is immobalised. On my Wine ubuntu rig i have 3 big virusses and none have given me any trouble.
The only place that they can go is ~/.wine/drive_c, and that's easily deletable.... 

So yes, but they aren't a threat.

If you think they aren't a threat then you are naive.

If you run a virus in Wine, immediately it can access any files you have in your home directory.  That includes modifying them, deleting them, sending them across the internet or granting someone else access to your machine.

Yes, if you kill the process then it will nolonger be running, but by then it might already be too late, since it takes very little time to do the above.

Furthermore, if you refer to my previous post you'll see that it's entirely possible for a virus writer to add a check for Wine and attempt to exploit known bugs in Linux to gain full access to your machine and install a rootkit so that it may go undetected.

---

### Post by hikaricore on 2008-10-05
> **asdfoo said:**
> If you think they aren't a threat then you are naive.

If you run a virus in Wine, immediately it can access any files you have in your home directory.  That includes modifying them, deleting them, sending them across the internet or granting someone else access to your machine.

Yes, if you kill the process then it will nolonger be running, but by then it might already be too late, since it takes very little time to do the above.

Furthermore, if you refer to my previous post you'll see that it's entirely possible for a virus writer to add a check for Wine and attempt to exploit known bugs in Linux to gain full access to your machine and install a rootkit so that it may go undetected.

Stop posting the same crap in multiple threads.

p.s. you're paranoid and YOU need to stop spreading the FUD yourself

---

### Post by david_kt on 2008-10-05
> **asdfoo said:**
> If you think they aren't a threat then you are naive.

If you run a virus in Wine, immediately it can access any files you have in your home directory.  That includes modifying them, deleting them, sending them across the internet or granting someone else access to your machine.

If you are worry about virus, just install klamav which include support for:
- On Access Scanning.
- Manual Scanning.
- Context-Menu Scanning
- Quarantine Management.
- Downloading virus definition updates
- Mail Scanning (KMail and Ximian Evolution)
- dazuko-2.0.5 pre-packaged
- Virus Browser
- Scan Scheduler

It could detect and quarantine windows virus as well.

DK

---

### Post by jimmyhacker on 2008-10-05
if a virus needs to infect a file,this can be C:/windows/system32/
but when linux booted up.this is Z:/mnt/hda1/windows/system32/
so.wine will not find the path of system32 and system32 will not be infected.
But worms such as W.stanit/a copies itself in RAM(Random Acess Memory)
exemple:if you have this worm and if you have 1024 mb,in 5 mins you will hae 128 mb left in ram.so your linux can crash and you can need to buy a new ram.

SO,if you know what program you run,feel free!
dont run programs such as DvdClone,Crackfinder and other illegal programs.

Respect

Jimmyhacker

---

### Post by asdfoo on 2008-10-05
> **hikaricore said:**
> Stop posting the same crap in multiple threads.

p.s. you're paranoid and YOU need to stop spreading the FUD yourself

instead of criticizing me for warning users when they've clearly been told the wrong thing, how about you make it clear to people that they should not run viruses in Wine.

---

### Post by lukjad on 2008-10-05
> **askyourpc.com said:**
> I was wondering this question of whether wine could emulate a windows virus. Or is it unlikely and why is that?
Thanks
Some can. I once installed a virus and it started putting random embarrassing junk on the desktop that would not get erased and would only leave once I purged Wine. :P

---

### Post by hikaricore on 2008-10-05
> **asdfoo said:**
> instead of criticizing me for warning users when they've clearly been told the wrong thing, how about you make it clear to people that they should not run viruses in Wine.

.... ](*,)

You know what, screw it.  I'm not going to even bother with you.

---

### Post by mike1772 on 2008-10-05
> **hikaricore said:**
> Stop posting the same crap in multiple threads.

p.s. you're paranoid and YOU need to stop spreading the FUD yourself

Wow...  I'm somewhat speachless.  Perhaps I misunderstand (and I apologize if I do), but I fail to see how this is crap.  If Wine is successfully able to 'convince' a particular Windows based virus that it is running on a Windows system - then there is nothing in the post you replied to that was outside the realm of possibilities.  Any threat posed by the Windows virus would immediately end when the Wine process ended - but any damage already done by this point may well be permanent - and any file access able by the user the wine process is running as would be at risk.  Furthermore - there have been exploits for Linux over the years that allowed for obtaining root access - it seems to me it would be trivial to utilize such an exploit to allow such a virus to obtain root access before causing any harm on the filesystem.  However, even that is not really relevant.  I don't care if a virus wipes out my system - I re-install every few months when a new release comes out anyway.  I do care if it wipes out ANY of my personal file as they are not replaceable.  Any of these would be the ones that would be viable targets by default.

A virus on Linux would not spread nearly as rapidly as on a Windows machine - but we do the community a grave disservice by implying that one would not spread at all.  Why someone would run a Windows virus under wine is beyond me - but at the least they should be warned that the consequences may be more than they initially anticipated.

While it's certainly not an issue to get paranoid about - it is one we should be aware of.  The best way to deal with it without becoming paranoid is to warn people not to purposely run viruses under wine to see what will happen.  In the future - if the threat becomes more serious - then we can upgrade to paranoia.

---

### Post by lukjad on 2008-10-05
I don't know that a Wine Virus will be able to actually get to the files or folders in Linux.

---

### Post by hikaricore on 2008-10-05
You're all missing a big point.

There should be no need to tell people not to try and run windows based viruses under wine...
That's just absurd.  If they don't have the sense to not do this intentionally there
is no logical reason to try and persuade them not to.  Should I tell people not to play
in traffic while wearing flip-flops and this somehow differs from wearing shoes?

Uggghhhh

A very large percentage of windows based viruses will have litte to no effect when
run via WINE on a Linux system.  This has been tested and proven by multiple bored
bored people.  The likelyhood of such a virus passing outside the user's home directory
and or causing any issues is even more unlikely.  On top of that if files are affected
there is no possible way for the virus to keep spreading unless these files are other
windows based binaries.  It's just a fact of the way your OS works, files such as
videos images and documents won't ever run as binaries unless you specifically tell
them to and flag them as such.  While users who dualboot or share a drive/files with
a windows based system should be wary, it's just paranoid and silly to think that
windows viruses will provide a solid enough threat inside the linux environment for
all this senseless FUD and panic.

asdfoo's posts in two different threads were unneeded fear-mongering.  sharing an
opinion is fine but calling users naive for thinking linux isn't fairly safe from 
windows viruses is just plain paranoid.  The way this user adds to the FUD and not
the conversation wastes my time and just plain scares uninformed/new users.

say what you will about me, but this I am correct about.

---

### Post by mike1772 on 2008-10-06
> **hikaricore said:**
> You're all missing a big point.

There should be no need to tell people not to try and run windows based viruses under wine...
That's just absurd.  If they don't have the sense to not do this intentionally there
is no logical reason to try and persuade them not to.

I apologize for my miss understanding - the implication I got was that such a virus would be killed by killing the process and would therefore not affect any files on the Linux filesystem.  I don't want to make anyone paranoid - nor do I want them to have a somewhat false sense of security...



> **hikaricore said:**
> The likelyhood of such a virus passing outside the user's home directory
and or causing any issues is even more unlikely.  On top of that if files are affected
there is no possible way for the virus to keep spreading unless these files are other
windows based binaries.
For me - the spreading 'feature' of a virus is the least of my worries.  When you say a virus couldn't spread outside my home directory - great, so it can only spread to the only files I care about.  Also - another point is that because the files are not executable Windows or Dos EXE's, it seems to me it is much more likely that confused windows based code would damage the file beyond repair than infect it.  When you say files such as videos and images won't ever run as binaries - I'd be a little concerned that perhaps they wouldn't run as video's and images either...

> **hikaricore said:**
> 
asdfoo's posts in two different threads were unneeded fear-mongering.  sharing an
opinion is fine but calling users naive for thinking linux isn't fairly safe from 
windows viruses is just plain paranoid.

As a general rule - I do believe Linux is fairly safe from Windows viruses - in fact, fairly is not a strong enough word in my opinion.  I'm just not sure it's completely safe from former Windows users.  The same Mentality the drives many Windows users (to be fair I should say new computer users - they just happen to mostly be windows users) to click on anything they see is likely to cause these same people to do the same on Linux.  I don't think it will become a widespread threat though.  I only took exception when it was suggested that if the process were killed the virus would be since people were concerned with it spreading without considering that the damage might already be done at that point.  That being said - backups are a great thing.

---

### Post by lakersforce on 2008-10-07
[/paranoia on] 
With 70.000 new unique viruses, spyware and malware conjured into existence pr. day, it's only a question of time before **one** will affect a Ubuntu distro.

So saying that viruses have little to no effect, is the naive opinion in my eyes.

Though it's the truth now, it might not be the truth in one hour.
[/paranoia off]

---

