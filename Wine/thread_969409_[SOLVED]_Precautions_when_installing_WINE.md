---
title: "[SOLVED] Precautions when installing WINE?"
date: 2008-11-03
forum: Wine
---

### Post by mal_conductor on 2008-11-03
I just installed WINE because I need ONE (1) Application that is only available for Windows.  The app is very specific and provided by a vendor of mine, no Linux version is available.

I have been reading about viruses/malware running with WINE.
There is a debate over this, but even the WINEHQ site admits the possibility of malware infections.

What are some precautions to take when installing WINE.  There are some mentions of using fake Windows Folders and deleting the Z: drive.

I don't have any sensitive/irreplaceable files on my C: (WINE) drive.

Thank you for any suggestions,

---

### Post by Trap3d on 2008-11-03
basicly id say no precautions if you havent downloaded it from somwhere else than winehq or add/remove appz linux has protection on this as it asks for password if u do sumn that linux thinks is suspicious

---

### Post by asdfoo on 2008-11-03
> **mal_conductor said:**
> I just installed WINE because I need ONE (1) Application that is only available for Windows.  The app is very specific and provided by a vendor of mine, no Linux version is available.

I have been reading about viruses/malware running with WINE.
There is a debate over this, but even the WINEHQ site admits the possibility of malware infections.

What are some precautions to take when installing WINE.  There are some mentions of using fake Windows Folders and deleting the Z: drive.

I don't have any sensitive/irreplaceable files on my C: (WINE) drive.

Thank you for any suggestions,

fyi, it's called Wine now rather than WINE.

It's the same deal as windows, don't run programs you don't trust.  I don't know what you mean by "using fake Windows Folders" and deleting the Z: drive is no defence really.

---

### Post by cogadh on 2008-11-03
Most importantly, don't run Wine as root or with sudo. If you do and you have somehow installed some malware, that malware will have sufficient access to potentially damage your entire system. By running it as a normal user, you only run the risk of potentially damaging your .wine directory and maybe your home directory, both of which are relatively easy to fix.

---

### Post by mal_conductor on 2008-11-03
> **cogadh said:**
> Most importantly, don't run Wine as root or with sudo. If you do and you have somehow installed some malware, that malware will have sufficient access to potentially damage your entire system. By running it as a normal user, you only run the risk of potentially damaging your .wine directory and maybe your home directory, both of which are relatively easy to fix.

cogadh,

Thank you for the suggestion.  What do you mean not running Wine as root or sudo.  Ubuntu only has sudo, correct?

But more important.  How does one "run Wine".  All I have done with it was downloaded an executable *.exe.  Double clicked it and it installed.  I don't recall being asked for a sudo password.  Please help me understand.

(My computer was hacked sometime ago.  I think it was through MSN Messanger.  This is the reason I am trying to go to Ubuntu, but I feel I have given back some of the sense of security, real or perceived, by loading Wine on my PC.  Too bad I really need that Windows based app)

---

### Post by Ng Oon-Ee on 2008-11-03
From your reply, I guess you're not very familiar with CLI (Command-Line Interface). Its exactly how I felt when coming from Windows ):P

So, anyway, in Ubuntu (and other Linux distributions), there's a user named 'root' which has full permissions to do anything (and I do mean anything, including deleting the entire OS), similar to the a user holding Administrator rights in Windows. All other users (in Linux) are granted User rights, which allows them to use the OS, save files, and do other normal stuff for daily work.

Other Linux distributions allow you to login as 'root' (Fedora for one), with a password separate from your own. This is normally needed when installing some programs (which access folders outside your home folder. Your home folder is basically the only part of your computer that you, the user, have full permission to by default) or fiddling with system settings. For ease of use, Ubuntu (as well as some other distros) have what's called 'sudo', and its graphical cousin 'gksudo', and don't even allow you to login as 'root' (I believe).

The use of these is to run a program/command as if you were root. Whenever you run a program/command with 'sudo' or 'gksudo' you'll be prompted to enter your user's password. Think of it as similar to UAC on Windows Vista, but without being as annoying (UAC to change the time on my clock? WTF?). This only happens when you're running from the terminal (looks like the command prompt in windows), and only explicitly, when you have typed in "sudo wine <your program>.exe".

So, anyway, if you're just running your program by double-clicking, you are NOT running as root, nor are you using 'sudo'. Therefore, the program which you are running (and any possible virus) can only change/write files which you own, which are in your home folder and wine directory. It can't affect your system, install other programs, etc. And besides, a virus written for Windows wouldn't begin to know what to do with the Wine file system (which looks like an empty installation of Windows) or the Unix filesystem outside it.

So, i think you can rest peacefully with your worries about viruses through Wine. Its a theoretical possibility, but the way Ubuntu is written means the danger is very minimal. No virus could wipe your system or damage your hard disc drive (Chernobyl years back was BAD when I was still on XP).

---

### Post by mal_conductor on 2008-11-03
Ng Oon-Ee,

I doubled clicked an *.exe file.
It installed without asking for any sudo password.

I understand if an application launches, by double-clicking, without asking for a password.  But an application installing by simply double clicking made me rethink this Wine thing and I went looking for some documentation regarding viruses.

I am tempted to install some malware... find out what happens.

Thank you

---

### Post by cogadh on 2008-11-04
I think you should try to understand how Wine really works first, before you do something that could be potentially damaging. 

When you install something with Wine, it does not install it system-wide, it just installs it into the "fake Windows" directory within your home directory (its a hidden directory labelled ".wine"). Since it is a directory within your home directory, you will not be asked for your sudo password as your user account already has full read/write permissions to that directory (your home directory is kind of like the "Documents and Settings" folder in Windows). Because the installation and the application both run with only your user permissions, neither the installation or the application can make any kind of changes to any directory or file outside of your home directory. 

This means that in a worst case scenario, you might mess up the .wine directory or possibly some files within your home directory. If the .wine directory gets messed up, you can just delete it, recreate it (by running the Wine configuration), then re-install any applications. If other files in your home directory are affected, you may not have to do anything at all, but it is concievable that you could have to go so far as to re-create your entire user profile.

As has already been said, when using Wine, you really only have to use the same common sense you should already have been using with Windows; only install applications from trusted sources.

---

### Post by asdfoo on 2008-11-04
> **Ng Oon-Ee said:**
> 
So, i think you can rest peacefully with your worries about viruses through Wine. Its a theoretical possibility, but the way Ubuntu is written means the danger is very minimal. No virus could wipe your system or damage your hard disc drive (Chernobyl years back was BAD when I was still on XP).


You shouldn't be complacent or smug though.  Malware can read your personal files through Wine and send them across the internet without permission.  

Who really cares about the parts of the system it can't modify.  Peoples private and important things are usually in their home directory.

---

### Post by Ng Oon-Ee on 2008-11-04
> **mal_conductor said:**
> Ng Oon-Ee,

I doubled clicked an *.exe file.
It installed without asking for any sudo password.

I understand if an application launches, by double-clicking, without asking for a password.  But an application installing by simply double clicking made me rethink this Wine thing and I went looking for some documentation regarding viruses.

I am tempted to install some malware... find out what happens.

As cogadh said, you'd need to understand how Wine works...

Ubuntu is a Linux OS, which means it is not targeted by viruses. And that's key, because viruses aren't sentient, they do very specific jobs. That's why some of the most simple security measures are surprisingly effective, such as (in Windows) having a separate partition for your sensitive data. Even unencrypted, the chances of a virus being programmed to look for files in the H: drive, for example, are much less than the virus being programmed to destroy the C: drive, which exists on ALL Windows computers.

With that in mind, you can also consider what Wine does. Windows programs do not run on Linux, the language is totally different (for want of a better analogy). Wine is sort of like an interpreter cum actor. It translates the system calls the application makes to something that makes sense to Linux, while at the same time pretending to be Windows to the application. So, from the point-of-view of the application, it sees a windows computer. Which would also be the point-of-view of any viruses running on a Wine installation.

This 'Wine computer' is actually just a collection of files, all stored within your ".wine" directory (or another directory if you use WINE_PREFIX). That's ALL a program or virus can see. Of course, by default Wine maps the Z: drive of the 'Wine computer' to your root folder. Which is why some people recommend removing this mapping for security. But for a virus to do any damage to your Linux system (Ubuntu in your case), it would have to know that it wasn't running on Windows, and it would have to have been specifically programmed to infect the Linux system on which Wine is running, a job made all the harder by the fact that it doesn't have root permission, and can't get that without knowing what YOUR password is (this is where Ubuntu's lack of a 'root' account actually helps).

Its not impossible that such a virus could be written, but virus writers are like every1 else, they go for the biggest target. Something like 5% of personal computers worldwide run on Linux, and only a small subsection of that run Wine. That's a very small target, and not worth their time, frankly.

The conclusion to this whole long story is basically:-
a) You're on Linux, you're basically safe
b) More knowledge on what you're actually doing would make you PERFECTLY safe

---

### Post by Ng Oon-Ee on 2008-11-04
> **asdfoo said:**
> You shouldn't be complacent or smug though.  Malware can read your personal files through Wine and send them across the internet without permission.  

Who really cares about the parts of the system it can't modify.  Peoples private and important things are usually in their home directory.

While theoretically true, my point about the virus needing to know that its accessing a Unix file-system holds. And I doubt many viruses would be capable of sending files across the internet when Wine doesn't come preinstalled with most of the components needed to do that (anything above the level of TCP/IP). I'd like to know if I'm wrong on this last point though.

Final note: I've always insisted that 'My Documents' is a dumb place to keep personal files, and I've brought that attitude over to Ubuntu. My home directory is for settings, any data will be in my separate data partition. Much easier for clean installs and stuff, as well as the added security of not having your important data in an easily predicted location.

---

### Post by david_kt on 2008-11-04
> **Ng Oon-Ee said:**
> While theoretically true, my point about the virus needing to know that its accessing a Unix file-system holds. And I doubt many viruses would be capable of sending files across the internet when Wine doesn't come preinstalled with most of the components needed to do that (anything above the level of TCP/IP). I'd like to know if I'm wrong on this last point though.

Final note: I've always insisted that 'My Documents' is a dumb place to keep personal files, and I've brought that attitude over to Ubuntu. My home directory is for settings, any data will be in my separate data partition. Much easier for clean installs and stuff, as well as the added security of not having your important data in an easily predicted location.

It is possible if you install mail client under wine. But if you do not instal MS IE, looks like all viruses would have difficulty to operate as most virii depend on MS IE. 

DK

[http://www.winehq.org/pipermail/wine-devel/2008-March/063461.html](http://www.winehq.org/pipermail/wine-devel/2008-March/063461.html)
For those interested I've tested the top five virus listed on symantec
and none of them have caused any serious issues, all malware I've
tried has failed completely due to the lack of IE.  I'll be setting up
two build environments in the script, one with IE and one with native
wine claiming ie (or not depending on responces).

Finally, where would be the right place to report the results? Appdb
seems like a strange place to be putting results of this nature. :P

---

### Post by Ng Oon-Ee on 2008-11-04
Ah, that's something good to hear. Thanks.

> **david_kt said:**
> Finally, where would be the right place to report the results? Appdb
seems like a strange place to be putting results of this nature. :P

I'd try the Wine forums. I've used those for some Wine-specific request before, and the devs are pretty active. I'm sure if you write it up nicely they'd be willing to sticky it or maybe add it to the FAQ.

---

### Post by Bios Element on 2008-11-04
Get this. It's possible you could die from a heart attack every second! "OH HEAVENS THE WORLD IS DOOMED!!! LETS MAKE IT A BIG DEAL!!! LETS JUMP UP AND DOWN AND OVERREACT!"

Simply because it 'could' be done doesn't mean it has or will. I'm gonna go out on a limb and say it's impossible a competent user will get a virus or malware or ANYFREAKENTHING that will destroy anything. Reason? 99% of them use IE. Ubuntu does not have IE. Other reason? Most use a fault in a Win code. Since Wine isn't Windows it's much less likely.

Short version: Stop freaking about it, Go do your homework.

---

### Post by mal_conductor on 2008-11-04
> **Bios Element said:**
> Get this. It's possible you could die from a heart attack every second! "OH HEAVENS THE WORLD IS DOOMED!!! LETS MAKE IT A BIG DEAL!!! LETS JUMP UP AND DOWN AND OVERREACT!"

Simply because it 'could' be done doesn't mean it has or will. I'm gonna go out on a limb and say it's impossible a competent user will get a virus or malware or ANYFREAKENTHING that will destroy anything. Reason? 99% of them use IE. Ubuntu does not have IE. Other reason? Most use a fault in a Win code. Since Wine isn't Windows it's much less likely.

Short version: Stop freaking about it, Go do your homework.

Bios Element,

Believe me you would feel very differently if something happened you.  I my case someone used weaknesses in MSN Messenger to extract information from my hard drive.  It is not about being a "competent user."  I did not invite this person nor did I initiate the MSN Messenger conversation.  He added himself to my contacts.

"Go do you homework"  I agree, hence I am here learning about Ubuntu/Wine.  Some posts are constructive and encourage growth in the Ubuntu/Linux community.  Other posts don't.

Also, I have always thought that successfully writing an attack on Linux would bring HUGE bragging right to the parson who does it.  Regardless of whether the number of users affected.  I don't know what motivates these people.

Many thanks to all others who responded to my request for help.

Regards,

---

### Post by asdfoo on 2008-11-04
> **Ng Oon-Ee said:**
> While theoretically true, my point about the virus needing to know that its accessing a Unix file-system holds. And I doubt many viruses would be capable of sending files across the internet when Wine doesn't come preinstalled with most of the components needed to do that (anything above the level of TCP/IP). I'd like to know if I'm wrong on this last point though.



Well, fyi.

This is not true, as has been mentioned Z:\ is accessible by default by naive windows programs.  It looks like any other windows drive from a windows program.  

Networking is part of every version of Wine, I've never heard of it being removed or not compiled with it.  

One way to prevent it from doing network access and perhaps some way to restrict which files it accesses would be through SELinux policies, but I don't know much about that, I think it has some way to go before it has good tools for end users to manage their security effectively without any headache.

---

### Post by Bensky on 2008-11-04
> **Ng Oon-Ee said:**
> Ubuntu is a Linux OS, which means it is not targeted by viruses.

Not true. There have been trojans/viruses written for Linux, it's just that the probability of you getting one is much smaller. So yeah, Linux is targeted by viruses, just not very often. Still, regardless of the operating system, it pays to watch what you download or what type of software you choose to install. :p

@Thread creator: Just make sure you never run Wine as root (i.e. don't run "sudo wine application.exe" - just use "wine application.exe").

---

### Post by Ng Oon-Ee on 2008-11-05
> **mal_conductor said:**
> "Go do you homework"  I agree, hence I am here learning about Ubuntu/Wine.  Some posts are constructive and encourage growth in the Ubuntu/Linux community.  Other posts don't.

That's the right attitude to have :p. The thing about Linux is that you have to learn it, and every new thing you learn is possibly useful, probably fun, and certainly interesting.

> **mal_conductor said:**
> Also, I have always thought that successfully writing an attack on Linux would bring HUGE bragging right to the parson who does it.  Regardless of whether the number of users affected.  I don't know what motivates these people.

I was under the impression the 'new' crop of hackers (besides the kids who can only break into an unprotected PC) are mainly after monetary gains. Which would of course pay more dividends with the majority OS. The other issue is that (supposedly) a fair number are anti-Microsoft zealots. Its a popular attitude to have among the 'know-more-than-average' IT crowd, after all, even here in these forums.

> **asdfoo said:**
> Well, fyi.

This is not true, as has been mentioned Z:\ is accessible by default by naive windows programs.  It looks like any other windows drive from a windows program.

Yes, that's exactly what I said in my post. Yet viruses don't normally search beyond C:\, simply because such activity would be more easily picked up by anti-virus software (hey, someone wants to access drive K:\....), and also because the majority of users do save their documents in the My Documents (or, with Vista, Documents) folder. Hence my example of saving your important (or all) documents in a D:\ partition.

> **asdfoo said:**
> Networking is part of every version of Wine, I've never heard of it being removed or not compiled with it.

Basic networking, yes, you could ping somebody endlessly and maybe do a DOS, but for higher level stuff than that you'd need higher-level communication tools. Viruses by their nature must be small to avoid detection (in general), and that means they can't contain the code necessary for complicated networking communication. As mentioned a bit further up, they'd normally use the built-in Windows tools (IE, obviously). Which isn't by default installed in Wine.

My conclusion would defer from Bios Element, though. Basic security needs to be thought about (installing Firestarter and only allowing what you need through, for example. Wine applications rarely, if ever, need access to the Internet, since for browsing and downloading there are already very capable Linux tools).

One day, if Linux does gain serious market share, this will be more of a problem. But for now, and with the current implementation of Wine, the risks are negligible, especially compared to running a wide-open Windows XP PC without antivirus software and firewalls. However, I'd say Ubuntu by default as almost as safe as a fully-protected Windows XP PC, running good antivirus software, having a mostly-closed firewall, and dumping IE and MSN Messenger. Oh, and not clicking on those random links that appear in your messenger/email every day :p.

If you want to find a way to screw your security up, you can, of course. Hence the part right at the start about 'doing your homework'.

---

### Post by Bios Element on 2008-11-05
> **mal_conductor said:**
> Bios Element,

Believe me you would feel very differently if something happened you.  I my case someone used weaknesses in MSN Messenger to extract information from my hard drive.  It is not about being a "competent user."  I did not invite this person nor did I initiate the MSN Messenger conversation.  He added himself to my contacts.

So why use MSN Messenger? It sucks. It's Microsoft crap that's even more broken then bloody vista. (Yes, it's possible.) Welcome to Microsoft. If you install Microsoft crap, Don't blame anyone but yourself. Repeat after me: **It was an MSN Messenger flaw. It had nothing to do with WINE.** Using software does NOT make Wine insecure. It makes the program insecure. So do your homework and don't use crap messengers/programs when there are perfectly good native programs to do the same. Heck, they even have webcam working on a few of the MSN clones. >.>

---

### Post by david_kt on 2008-11-05
> **Bios Element said:**
> So why use MSN Messenger? It sucks. It's Microsoft crap that's even more broken then bloody vista. (Yes, it's possible.) Welcome to Microsoft. If you install Microsoft crap, Don't blame anyone but yourself. Repeat after me: **It was an MSN Messenger flaw. It had nothing to do with WINE.** Using software does NOT make Wine insecure. It makes the program insecure. So do your homework and don't use crap messengers/programs when there are perfectly good native programs to do the same. Heck, they even have webcam working on a few of the MSN clones. >.>

I think what mal_conductor meant is he used MSN on windows, not linux. And that experience make him nervous and he tried to use more secure platform, i.e. linux. But when he learnt that there is wine in linux, it remind him about his trauma and he want to learn more to avoid similar problem. 

DK

---

### Post by frost151n on 2008-11-06
> Think of it as similar to UAC on Windows Vista, but without being as annoying (UAC to change the time on my clock? WTF?).

Ubuntu asks me for a password before i change the time!!! Whats the difference???

---

### Post by Ng Oon-Ee on 2008-11-07
> **frost151n said:**
> Ubuntu asks me for a password before i change the time!!! Whats the difference???

Ah, does it now? My bad, just checked it out :)

I suppose both OS-es think that the system time is a VERY IMPORTANT SETTING to the integrity of your computer. I always thought, in Windows, that it was because a lot of licensing programs check the system time to see whether your license has expired. The fact that the free Ubuntu does it as well may indicate that there's another reason.

Or perhaps that nobody has gotten around to actually asking why...

---

### Post by mal_conductor on 2008-11-12
> **Bios Element said:**
> Repeat after me: **It was an MSN Messenger flaw. It had nothing to do with WINE.**

I am repeating:
**It was an MSN Messenger flaw. It had nothing to do with WINE.**

OK, What did that accomplish????!!!!

My problems were on a Windows XP computer.  The rest of the group got it (nod at david_kt).  I guess we have to slow down and wait for the ones catching up.

Now,  let's hear some constructive posts!!!!

---

