---
title: "Wine &amp; Security"
date: 2007-09-05
forum: Wine
---

### Post by tzembi on 2007-09-05
For the last few days i had some insight in Wine and Security Issues and i really didnt like what i was seeing.

Wine is a native Linux application bringing the Windows Api to Linux.
For some people this is a great thing, for they have now the possibility to bring along their favourite Windows Stuff to the Open world.

For people like me it is "teh horror" for the following reason.

Wine - being a native Linux application - has the same privileges as the Linux User its running as (please correct me if i got something wrong):
- Full Access to the Network (if its not restricted for the user).
- Full Access to the Filesystem (if its not restricted for the user).
- Ability to start/stop processes, stuff in /usr/bin is available like for the user its running as

This is a problem if you have Windows applications you do not fully trust. The first thing here are GAMES. Thats right folks. Why you ask ? Because most Games are not running in Wine as long there is a Crack. For the Wine project is not focusing on Copy Protection issues to get stuff running. So people buying Stalker in the Store and want to use this, they are going to install it, go to shady Cracksites, get crack, apply it and use the product they bought. Wether the Spyware Stuff is in the Original exe (see eg Bioshock) or the Crack (currently more likely) it doesnt matter.

The next thing in here are Freeware Spyware Applications, or other stuff that you dont want to have full access to the network. Unfortunately there is no method to know in advance how these things do the access, so you have to REACT to identify stuff and block resources they are using (or identifiying not using them at all).

So, if for any reason you dont fully trust the wine applications you are using there are currently the following solutions:



1.: Dont run these Windows Applications.

2.: Run wine as different User and block traffic for him (recommended by wine project):
- make new user (e.g. "gameuser")
- Block traffic for gameuser in iptables 
- Run Wine Applicationas gameuser

3.: Use Apparmor or SELinux (have a 10 day course for 4000$ to learn about it and be really secure, as long as you do anything stupid ;) )

4.: Use another Product like e.g. VMWare, Virtualbox, Xen, unameit (buy windows license & haul out ressources & be not able to use directx)



However, most of these are, in my view just workarounds. There should be (really soon) an equivalent of an Application Level Firewall on Linux (EDIT3: because the Wine Project is not responsible, so i understood it, what native Linux apps do on the System: [http://bugs.winehq.org/show_bug.cgi?id=9578](http://bugs.winehq.org/show_bug.cgi?id=9578) , [http://bugs.winehq.org/show_bug.cgi?id=1419](http://bugs.winehq.org/show_bug.cgi?id=1419) ). Maybe you cant compromise the whole system right now, the compromise of the Home Directory is in most times enough.

Please respond with insight on this. And please correct me if i understood something wrong.

EDIT1:Some age-old discusssion on WineHQ on this: [http://www.winehq.org/pipermail/wine-users/2002-October/009110.html](http://www.winehq.org/pipermail/wine-users/2002-October/009110.html)
EDIT2: Hybrid Linux/Windows Worm/Virus: [http://www.theregister.co.uk/2001/03/28/risks_from_hybrid_linux_windows/](http://www.theregister.co.uk/2001/03/28/risks_from_hybrid_linux_windows/)
EDIT3: VERY interesting: WMF Exploit in Wine: [http://article.gmane.org/gmane.comp.emulators.wine.patches/20976](http://article.gmane.org/gmane.comp.emulators.wine.patches/20976)
EDIT4: [http://wine-wiki.org/](http://wine-wiki.org/) , search for "Blocking Network access to Software running on Wine" in "Advanced Wine User Information"
EDIT4: Discusssion on winehq.org: [http://www.winehq.org/pipermail/wine-devel/2006-March/045715.html](http://www.winehq.org/pipermail/wine-devel/2006-March/045715.html)
EDIT5: Some stuff on Virii: [http://www.linux.com/articles/53727](http://www.linux.com/articles/53727)
EDIT5: Some stuff on Virii: [http://www.linux.com/articles/60208](http://www.linux.com/articles/60208)
EDIT6: Some poor user schmock getting the shaft for not RTFM : [http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html](http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html)
EDIT6: Some interesting thoughts on how to make a "secure Operating System your mother could use" and whats wrong with "reactive security design" (with video): [http://wiki.whatthehack.org/index.php/Everything_You_Know_About_Client_Security_Is_Wrong](http://wiki.whatthehack.org/index.php/Everything_You_Know_About_Client_Security_Is_Wrong)

EDIT1: (will be adding weblinks to this on info about it)


Regards,
TZembi

EDIT5:
I just wanted to clarify some more (maybe i didnt translate my concern correctly):

This Post **was not intentionally** about running wine as root.
This Post **was not intentionally** about running windows virii in wine.

This post **should be** about how to run untrusted windows stuff in wine without compromising users home or system. If someone has more Infos how to do it (see top) please dont hold back.

---

### Post by jrusso2 on 2007-09-05
well you don't run wine are root you run as user.  I have not had any problems with it.

I have been using it a long time.  People have even tried to run windows virus in it on purpose but have not had much luck getting them to do much more then just run.

---

### Post by tzembi on 2007-09-05
Thats correct, you run as user. 

Alas, the stuff in your user account contains things like the firefox profile or your emails (typical home user). 

So i think thats not good and doesnt really solve the things i mentioned. You can do pretty nasty stuff with a user account. Not to mention there are  exploits to elevate user rights.

---

### Post by wieman01 on 2007-09-05
Interesting discussion. These are things I have been asking myself as well. Look forward to it as I could not find anything concerning Wine security on the web.

_**EDIT:**_
I found this which I think is a funny read: [http://www.linux.com/articles/42031]("http://www.linux.com/articles/42031")

---

### Post by Ferrat on 2007-09-05
Unless someone did a specific virus for wine it would be hard to get it working I think, as the very funny article in the post above me describes. 

first of wine doesn't really have access like the user, sure it runs with my (the user) levels but the windows folder that most viruses looks for is just a folder nothing major and the files in there, altho they act much the sameway as the windows dlls ect they ain't so like in coding, second of the viruses ain't looking for a linux system that doesn't work the same way, first the virus should have to recognize that it's in a wine system, go on to start looking for the linux systemfolders and using diffirent coding inflict files, but since if the virus wants to "not die" if you shut of wine, it has to break free and add it self to system launched apps or likewise = need auth, so it has to crack the system first.

Only after mutating from a Windows virus to a Linux one can it acctually do something (since wine isn't running all the time and can be turned off or just reinstalled if the virus even somehow finds a way to make wine start the virus next time you start wine) and this is no small feat, and most viruses uses weaknesses inside windows, much like poking a stick in a open wound and sure there are some issuse that possibly can be exploited in Linux but many of them are adressed as they surface and they are nothing like the Windows once and then you got the problem with diff. dists and their ways of doing things.

sure you could prolly write a program that could do some dmg in the home folder for the user, that you could do but even that would be tricky to spread since you would need someone to download it and then open it with wine, in this case divercity between Linux systems is a strength since it would have to adapt and it's harder to get a Linux system to run anything wihout the active participation of the user.

I think it would be easier just to write a shell script that does something bad and send it to all your friends ;D

---

### Post by cogadh on 2007-09-05
Viruses, spyware and other malware may run in Wine, but they don't affect the Linux system. That article's reference to SomeFool's affect on Linux is no worse than the effects of some of the normal apps that have run pooorly in Wine and whatever it was doing was very easily stopped with a CTRL+C. None of those samples actually did anything that they were supposed to do to the Linux system.

You should never run Wine as root or with sudo, that is already part of the Wine user documentation. If you do happen into a piece of malware that can run in Wine, it cannot possibly do any damage to your actual system (if you are already following the "no root, no sudo" rule), it can only damage Wine's "fake Windows" directory. If that were to happen, you can just delete that directory and rebuild it clean.

> **tzembi said:**
> Because most Games are not running in Wine as long there is a Crack. 
Huh? What do you mean by this? If you use a cracked executable to run a game, you are running that cracked exe in Wine. Also, copy protection support is being developed for Wine. SecuRom already works nearly fully.
I would also like to point out that all of your examples have already been corrected in subsequent Wine updates. Just as with any software, when a bug or exploit is found, the developers patch it. Wine is not any more or less susceptible to coding faults than any other piece of software, on any operating system. 
> There should be (really soon) an equivalent of an Application Level Firewall on Linux (EDIT3: because the Wine Project is not responsible, so i understood it, what native Linux apps do on the System: [http://bugs.winehq.org/show_bug.cgi?id=9578](http://bugs.winehq.org/show_bug.cgi?id=9578) , [http://bugs.winehq.org/show_bug.cgi?id=1419](http://bugs.winehq.org/show_bug.cgi?id=1419) ).
This is very true. Do you have the option to shut off network access in any other native application? None that I can think of. If you want to restrict application network access, that should be a system or firewall function, not a Wine function.

As long as you use Wine correctly, it cannot harm your system. If someone were to write malware specifically for Wine, it would run into the same problem that all previous Linux malware has run into: the inherent security of Linux. Not to mention if something like that were to exist, whatever hole it exploits would likely be patches in a matter of days (if history is any indication). Also, just like with any piece of software, regardless of the operating system, only use that which you can trust. **Use common sense people, its that simple.**

---

### Post by tzembi on 2007-09-05
Hi Again,

thanks for your answers, but they really didnt make me feel better.
I just researched some more and this is what i found on 

[http://wine-wiki.org/](http://wine-wiki.org/) :

-------------------------------------
What about Windows Viruses

As long as you are running wine as a normal user and NOT as root, there is some protection. It is still a concern, but considering that you will most likely be using native Linux software for transferring software, perhaps it is unlikely you will be easily infected.

W. Ogburn [Nov 05] : I think there are two different answers:In principle, an executable that you run as a user under Wine can do anything that a malicious Linux executable could do. So it could potentially mess up your user's account. There's no special protection from malicious programs that comes from running under Wine. However, a Windows virus or other malicious program that doesn't know anything about Wine or Linux isn't very likely to do that. Any harmful effects will probably be limited to your fake Windows directory, and a lot of things that a virus might try to do won't work at all.


S. Petreolle: [read acces] Files are still at risk since the virus has _read_ access on them. As an example viruses replicate by reading mail adresses into files.

J. LaBarre pointed to another concern. I have a data partition formatted as FAT32 to be shared between Linux and Windows 2000. This partition is mounted under a "windisk" group which has R/W permissions (umask 0007)

M. Knecht: If he executed some exe file that had a virus in it, and the virus found some data file to infect, then the virus is there. It may not matter on his system, but should he send that file on to someone else then he would be transmitting a virus to others.

J. Ernst provided a voice of reason: If you are worried you can have your own wine user that you'll use for running wine.[and lock that down] 
-----------------------------------

See also:

[http://www.winehq.org/?issue=259#Wine%20&%20Viruses](http://www.winehq.org/?issue=259#Wine%20&%20Viruses)

Given that wine HAS read access on Files in at least the Homedirectory, wouldnt it be good to switch it to run as another User by default in the distries as long as there is no real application level firewall in sight ? I know, i will maybe not make any friends with this in the wine community by asking that, but many people are switching from Windows to Linux for Privacy & Security reasons and being fed up spied out by CSS Companies. Wine is sadly a special case, being the entryway for mostly Closed Source Software used by exactly these users. The fact that there are maybe no Applications today that make use of this possibility is by no means a guarantee for a future development.

EDIT1: In response to: 
"Huh? What do you mean by this? If you use a cracked executable to run a game, you are running that cracked exe in Wine. Also, copy protection support is being developed for Wine. SecuRom already works nearly fully."
Thanks, i think thats a really positive development i wasnt aware of until now. So when can you actually play SecuRom stuff without cracks  ? What i meant was a modified crack.exe, tailored to the linux world. You cant really look into this CSS do you ?

EDIT2:
Look guys, it doesnt have to be a classical Virus to be concerned about. For example i read an article about Spyware in World of Warcraft (I think its called "Warden" or something). It may be there to check if you are running an unmodified gameclient. But who really knows ? Its closed source...

Regards,
TZembi

---

### Post by cogadh on 2007-09-05
I can already play a few SecuRom protected games without cracks: Star Trek Armada 2, Advent Rising and Vampire The Masquerade Redemption. As long as you have your CD-ROM drive configured correctly in Wine, SecuRom generally will work.

I think what everyone needs to remember is what we all should have learned as Windows users; never run an untrusted exe or open untrusted files with Wine. As long as you are reasonably security conscious, you won't have any problems **with your system**. There is always the risk that you could spread a Windows virus from a Linux machine to a Windows machine, since Windows viruses don't really affect Linux (such as the example of the shared FAT32 drive).

Like I said, use common sense: If you are going to use a cracked exe, run it past a virus scanner before using it; don't run Wine as root or with sudo; only download from trusted sources; etc. I'm not saying that you don't have anything to worry about when using Wine, I'm just saying that you don't have anything more than what you should already be worrying about as a PC user.

---

### Post by tzembi on 2007-09-05
I filed a Bugrequest to check the default wine behavior:

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/137560](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/137560)

---

### Post by bodhi.zazen on 2007-10-18
This seems to be an age old discussion.

My general comments are that many of your links are old and outdated.

Wine != Windows and although an exploit is possible, Wine HQ is aware of potential problems and does patch code.

_Windows virus on Linux_: At this time it is possible to run windows viruses with wine. They do not run well yet.

		[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

This is my response to your post:

 [http://ubuntuforums.org/showpost.php?p=3094631&postcount=25](http://ubuntuforums.org/showpost.php?p=3094631&postcount=25)

You can read the thread if you like ^^

		[http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78](http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78)

Additional info : [http://www.linux.com/article.pl?sid=07/02/13/1637251](http://www.linux.com/article.pl?sid=07/02/13/1637251)

In summary :

1. Is it possible that running windows applications with wine may represent a security threat ? Yes, but no more so then any other application.

2. WineHQ, and others, are proactive regarding security, but they of course can not promise absolute security.

3. At this time there is no know threat from windows applications on wine. If a threat is identified it should be reported to Ubuntu or winehq and, as others before it, they will be patched.

4. DO NOT RUN WINE AS ROOT.

---

### Post by Colro on 2007-10-18
It wouldn't matter if you ran a 'cracked' game with WINE that had spyware embedded in it unless the spyware was specifically designed to target Linux. Most likely the spyware is going to try to read Outlook's address book or embed itself deep within your windows filesystem; both of which don't exist in Linux. The most it'd be able to do is phone home without any personal information since it can't access it. Also, as soon as you close the WINE application it's cut off and cannot force itself to stay open or re-open without user consent.

> Alas, the stuff in your user account contains things like the firefox profile or your emails (typical home user). 

I'll use this comment for a specific example. Let's say there's some windows spyware embedded in crack X for game Y that attempts to extract saved passwords from firefox profiles. It would be entirely harmless even in the worst case scenario that it gets executed by wine while sitting in your home folder. It's going to attempt to locate C:/Documents and Settings/$varusername/Application Data/Mozilla/Firefox for the information, not .mozilla. The program would have to specifically be designed to look in that directory for your information, and, quite frankly, I've yet to hear of any spyware that will attempt to pull that off. Even in the case that the spyware looks for ALL files it can find with a specific name in ALL directories, it's only potentially harmful if you have the spyware in a location outside of your .wine directory, since WINE will keep it from seeing anything else on the file system if it's located there.

It isn't *impossible* that one could exploit WINE with windows spyware, but it's extremely unlikely. You really don't have much to worry about in every day use. I've read articles about people specifically trying to get in-the-wild windows viruses to run in WINE and either failing or having the viruses sit there unable to do anything.

Edit:

> For example i read an article about Spyware in World of Warcraft (I think its called "Warden" or something). It may be there to check if you are running an unmodified gameclient. But who really knows ?

Warden is Blizzard's anti-cheat/hack system and checks running processes for known MD5 checksums of popular hacks as well as checking the MD5 checksums of the game files to make sure they haven't been tampered with. It's far from spyware and -IS- able to be disabled with some tinkering, but you'll get banned from the game faster then you can count to ten if the server can't find warden on your system.

---

### Post by tzembi on 2007-10-18
Hi Bodhi.zazen,


> **bodhi.zazen said:**
> This seems to be an age old discussion.

My general comments are that many of your links are old and outdated.

Wine != Windows and although an exploit is possible, Wine HQ is aware of potential problems and does patch code.

_Windows virus on Linux_: At this time it is possible to run windows viruses with wine. They do not run well yet.

		[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

This is my response to your post:

 [http://ubuntuforums.org/showpost.php?p=3094631&postcount=25](http://ubuntuforums.org/showpost.php?p=3094631&postcount=25)

You can read the thread if you like ^^

		[http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78](http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78)

Additional info : [http://www.linux.com/article.pl?sid=07/02/13/1637251](http://www.linux.com/article.pl?sid=07/02/13/1637251)

In summary :

1. Is it possible that running windows applications with wine may represent a security threat ? Yes, but no more so then any other application.

2. WineHQ, and others, are proactive regarding security, but they of course can not promise absolute security.

3. At this time there is no know threat from windows applications on wine. If a threat is identified it should be reported to Ubuntu or winehq and, as others before it, they will be patched.

4. DO NOT RUN WINE AS ROOT.

I really do not understand why everybody is misconcepting my concerns as an attack on the wine community. This it is NOT.

Thanks for pointing out that some links are old and outdated. That may be because there are no recent information available concerning the security model of stuff running on wine. Thanks for your Links, though, they add to the discussion.

And to point out my issue again (and summarize my primary concerns):

- Wine Applications have at least read access in the wineusers home Directory and net access.

- There is no easy way to restrict this behavior. 

- There is a bunch of Windows applications that can not be trusted and ARE run in wine without second thought because everybody says: **"Hey its running in Linux... that must be secure"**. 

The fact that there are some native linux apps that cant be trusted is no point, simply because Linux stuff is shipped mostly with the source. Windows apps are mostly not.

Edit:
I just wanted to clarify some more (maybe i didnt translate my concern correctly):

This Post was **not intentionally** about running wine as root.
This Post was **not intentionally** about running windows virii in wine.

This post **should be** about how to run untrusted windows stuff in wine without compromising users home or system. If someone has more Infos how to do it (see top page) please dont hold back.

---

### Post by eye208 on 2007-10-18
> **tzembi said:**
> And to point out my issue again (and summarize my primary concerns):

- Wine Applications have at least read access in the wineusers home Directory and net access.

- There is no easy way to restrict this behavior. 

- There is a bunch of Windows applications that can not be trusted and ARE run in wine without second thought because everybody says: **"Hey its running in Linux... that must be secure"**.
I think the main problem with WINE is that beginners may be tempted to run it as root when running a setup.exe or a game, just because it's the way of doing things in Windows. It's important to point out that admin privileges in WINE are not the same thing as root privileges in Linux. They are separate, and the former does not require the latter.

Other than that, there is no problem with WINE. You can run it as another user whose home folder does not contain any private information. I fail to see how network access by itself could possibly compromise system security and privacy as long as the system is fully patched and up to date.

Frankly, I considered myself paranoid until I read your post. You are way over the top here.

Here's some food for thought:

You may think Linux is secure, but is it? Even if you compile everything yourself from sources that you have reviewed line by line, how can you be sure your compiler does not insert malicious code into every executable module it generates? Have you **analyzed the binary code of the compiler you are using?** If not, why do you trust it?

---

### Post by genbuntu on 2007-10-18
Thanks for replying to my original thread: [http://ubuntuforums.org/showthread.php?t=578278](http://ubuntuforums.org/showthread.php?t=578278)

I found this thread informative ... 

 I recently realized another cause of concern. Since I have dual boot with Windows XP , now how different (insecure) is that compared to using Wine on only ubuntu installed machine. 
Are there greater chances of a virus doing damage to my windows partition from within Wine running under ubuntu?

---

### Post by tzembi on 2007-10-18
> **eye208 said:**
> I think the main problem with WINE is that beginners may be tempted to run it as root when running a setup.exe or a game, just because it's the way of doing things in Windows. It's important to point out that admin privileges in WINE are not the same thing as root privileges in Linux. They are separate, and the former does not require the latter.

Other than that, there is no problem with WINE. You can run it as another user whose home folder does not contain any private information. I fail to see how network access by itself could possibly compromise system security and privacy as long as the system is fully patched and up to date.

Frankly, I considered myself paranoid until I read your post. You are way over the top here.

Here's some food for thought:

You may think Linux is secure, but is it? Even if you compile everything yourself from sources that you have reviewed line by line, how can you be sure your compiler does not insert malicious code into every executable module it generates? Have you **analyzed the binary code of the compiler you are using?** If not, why do you trust it?

Thanks for putting me in the same edge with paranoid nutcases. This is always the problem with security issues. 

For some guys defaults are fine... Some guys want to strip naked on the marketplace... some dont want to. 

I use Open Source because at least someone can look in the code and warn me about stuff that could break my or my companys privacy. Maybe i alone cant read all of the source... but it **is** at least **possible** to detect evil stuff wich makes it less possible that something is put in. The stuff thats running on wine is mostly closed source. Nobody but the Engineers or someone with nice dissassembling skills could discover things like sending your email data to the net.

And again: the "run as other user thing" was mentioned in my first post. It just isnt convenient ! And thats what this post should be about: Making it more convenient for Wine Users to maintain their privacy.

Please post something thats helpful in that direction.

---

### Post by tzembi on 2007-10-18
> **genbuntu said:**
> Thanks for replying to my original thread: [http://ubuntuforums.org/showthread.php?t=578278](http://ubuntuforums.org/showthread.php?t=578278)

I found this thread informative ... 

 I recently realized another cause of concern. Since I have dual boot with Windows XP , now how different (insecure) is that compared to using Wine on only ubuntu installed machine. 
Are there greater chances of a virus doing damage to my windows partition from within Wine running under ubuntu?


Thanks for the informative part. 

On security of your windows partition : Thats the question i asked myself and that had me started this thread.

Quoting:
"M. Knecht: If he executed some exe file that had a virus in it, and the virus found some data file to infect, then the virus is there. It may not matter on his system, but should he send that file on to someone else then he would be transmitting a virus to others."

You shouldnt feel secure because you run Linux - you should feel secure because your Linux is properly configured and you use it in the right way.

EDIT: But really - its not the Virii that bug me most ;)

---

### Post by eye208 on 2007-10-18
> **tzembi said:**
> I use Open Source because at least someone can look in the code and warn me about stuff that could break my or my companys privacy. Maybe i alone cant read all of the source... but it **is** at least **possible** to detect evil stuff wich makes it less possible that something is put in.
I think you did not really get the last paragraph of my post. Looking into the sources won't help you if your compiler cannot be trusted. You could even recompile the compiler itself without removing the malicious parts because the new compiler binary just inherits them.

You might just say that something like this is very unlikely to happen. And guess what, I am saying the same about WINE. Linux has so many layers of security in place that a whole lot of things would have to fail all at the same time for an attack to be successful. Since it is very unlikely for all of these security measures to fail simultaneously, it is very unlikely for a malware programmer to even expect to get this kind of unique opportunity in the first place. A WINE-compatible virus would have to be written with both Windows and Linux in mind. That makes it even more exotic than pure Linux malware which is rare by itself already.

I am very aware of security issues. See my post in another part of this forum about running the ETQW game installer as root. A Windows application running with WINE is no more dangerous than any other binary Linux executable, e.g. Skype, Flash etc. Unless there is an unpatched local privilege escalation exploit somewhere in the kernel or in X.org or in a system service running as root, these executables get no chance of compromising the system. And if you run them as another user, your private data in your main account home folder is safe. Not perfectly safe, but safe enough.

If you want even more security, use AppArmor or SELinux, both of which are available for Ubuntu. This way you can shield WINE apps from accessing the network or the /tmp folder etc. as well. The tools are there if you need them, but in the case of Joe Average's box I think it's just a waste of time.

---

### Post by cogadh on 2007-10-18
Since the wheel seems to be going around again, I think I'll repeat myself:

> **cogadh said:**
> I think what everyone needs to remember is what we all should have learned as Windows users; never run an untrusted exe or open untrusted files with Wine. As long as you are reasonably security conscious, you won't have any problems **with your system**. There is always the risk that you could spread a Windows virus from a Linux machine to a Windows machine, since Windows viruses don't really affect Linux (such as the example of the shared FAT32 drive).

Like I said, use common sense: If you are going to use a cracked exe, run it past a virus scanner before using it; don't run Wine as root or with sudo; only download from trusted sources; etc. I'm not saying that you don't have anything to worry about when using Wine, I'm just saying that you don't have anything more than what you should already be worrying about as a PC user.

Some bit of paranoia is healthy and required if you are going to have secure system, but people are taking this one way too far. Wine cannot do anything to hurt your system on its own. It can only hurt your system if you do something incredibly stupid with it. So don't be stupid and you'll be fine.

---

### Post by tzembi on 2007-10-18
> **tzembi said:**
> 
This Post was **not intentionally** about running wine as root.
This Post was **not intentionally** about running windows virii in wine.

This post **should be** about how to run untrusted windows stuff in wine without compromising users home or system. If someone has more Infos how to do it (see top page) please dont hold back.

:guitar:

---

### Post by usarmykr on 2007-10-18
Virus Smirus I say.  Who care if a virus comes thourgh wine? AI dosent exist, programs can't learn.  An effective linux virus would need to be ever-evolving, which can't happen.  Argue all you want, AI dosent exist, Linux has 2230948 distros and each one changes very often.  Virus = PWNT

---

### Post by usarmykr on 2007-10-18
> **eye208 said:**
> I think you did not really get the last paragraph of my post. Looking into the sources won't help you if your compiler cannot be trusted. You could even recompile the compiler itself without removing the malicious parts because the new compiler binary just inherits them.

You might just say that something like this is very unlikely to happen. And guess what, I am saying the same about WINE. Linux has so many layers of security in place that a whole lot of things would have to fail all at the same time for an attack to be successful. Since it is very unlikely for all of these security measures to fail simultaneously, it is very unlikely for a malware programmer to even expect to get this kind of unique opportunity in the first place. A WINE-compatible virus would have to be written with both Windows and Linux in mind. That makes it even more exotic than pure Linux malware which is rare by itself already.

I am very aware of security issues. See my post in another part of this forum about running the ETQW game installer as root. A Windows application running with WINE is no more dangerous than any other binary Linux executable, e.g. Skype, Flash etc. Unless there is an unpatched local privilege escalation exploit somewhere in the kernel or in X.org or in a system service running as root, these executables get no chance of compromising the system. And if you run them as another user, your private data in your main account home folder is safe. Not perfectly safe, but safe enough.

If you want even more security, use AppArmor or SELinux, both of which are available for Ubuntu. This way you can shield WINE apps from accessing the network or the /tmp folder etc. as well. The tools are there if you need them, but in the case of Joe Average's box I think it's just a waste of time.

IMO Linux is more inherently secure.  It dosent really have 23987 built in security features, by nature it is secure.  Example - an egg, weak (windows) a piece of granite or a diamond, strong because of a different composition (linux)

Linux viruses are doomed to fail.

---

### Post by bodhi.zazen on 2008-04-30
This thread is referenced on Google so I though an update of sorts is in order.

First, it is possible for windows viruses to run in wine.

Second, the wine team is aware of this and is actively discussing security.

[http://www.winehq.org/?issue=343](http://www.winehq.org/?issue=343)

> [B]Viruses

[/B]   [http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html](http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html)
[URL="http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html"]
[/URL]  
 "I had set her up with a perfect Wine install. She had a bit of software that needed to run under wine and I had shown her how to install within that environment. Apparently, I wasn't specific enough. It never occurred to Paula that the .exe programs she had used on her XP machine were the vehicles for many of her present viruses. To her, it was perfectly fine to use those same .exe's...after all, she was in Linux, right? 
 I got there within the same hour and checked her machine. Yep...Windows viruses will reside and create the same havoc within a Wine environment. Now, I've seen it with my own eyes. This time I reinstalled for her and made sure I found all the infected .exe's on the Windows side and deleted them." 
   There was then some interesting discussion on the mailing list about how to keep wine secure, about the interesting fact that viruses _should_ work in Wine. Its best for compatibility of Wine emulates as many of the bugs from Windows as possible. As far as security goes the verdict was that running Wine as a normal user for normal applications is fine. However if you are intentionally bench-testing something malicious a virtual machine is the safest route. Again, *never run Wine as root!* .[http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html](http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html)

This is also an interesting read :

[http://www.download.com/8301-2007_4-9916375-12.html](http://www.download.com/8301-2007_4-9916375-12.html)

>  ... some malware can indeed infect Wine, including manifesting in the crashes Chris described. The majority of infections, however, will not be able to spread into the Linux operating system. That is, unless you're not running Wine as root. According to the [Wine wiki]("http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014"), this *will* throw open the gateway for viruses to access your computer, and if Chris found a virus file in the root folder, there's a good chance that's what happened.Also this is one of the more referenced links, although it is old. 

[Running Windows viruses with Wine]("http://www.linux.com/articles/42031")

Please note that often times viruses are "enabled" either by people trying to run them in wine or by misconfiguration of wine to allow access outside of ~/.wine (ie running wine as root).

One thing you should check is that there are no links in ~./wine outside of ~/.wine. Specifically check in ~/.wine/dosdevices and make sure there is no "z:" linking to / or /home. If so delete it and, IMO, keep all data you access with wine in your fake c drive (in ~/.wine).

And from the Wine FAQ : 

[http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014](http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014)

> **Should I run Wine as root?**

 [IMG]http://wiki.winehq.org/wiki/winehq/img/alert.png[/IMG] ***NEVER run Wine as root!*** Doing so gives Windows programs (and viruses) full access to your computer and every piece of media attached to it. Running with sudo also has these same risks but with the added bonus of breaking the permission on the users ~/.wine folder in the process. If you have run Wine with sudo you need to sudo rm -rf ~/.wine and then run [winecfg]("http://wiki.winehq.org/winecfg") to set wine back up. You should run Wine as the normal user you use to login.

 
For Linux Systems all ideas that wine needs root can be solved through Posix Capabilities [http://www.linuxjournal.com/article/5737](http://www.linuxjournal.com/article/5737) or Posix File Capabilities [http://www.ibm.com/developerworks/library/l-posixcap.html](http://www.ibm.com/developerworks/library/l-posixcap.html) or correcting other security settings.===========


Also, one more thing you should all be aware of ...

If you install wine check out ~/.wine/dosdevices

```
ls -l ~/.wine/dosedvices
```yep, that's right z: linked to /  bad, bad, bad. Linking to $HOME is "OK" but personally I think you should not link to anything outside of ~/.wine.

I advise you remove all links from ~/.wine/dosdevices to any location outside of ~/.wine with the exception of links to CDROM/ DVD.

[IMG]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/IMG][SIZE=4] [COLOR=navy][FONT=times]*bodhi.[/FONT][/COLOR][FONT=times][COLOR=darkgray]zazen[/COLOR][/FONT][/SIZE]*

---

### Post by tzembi on 2008-04-30
OK, so IT happened once.. maybe twice, what kind of direction will the development team take ? That is the interesting question here...



> [http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html](http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html)

> Some people should NEVER be allowed to touch a computer and I don't care what degrees hang on their wall.


If Linux wants to go for "Joe Sixpack" as users, nobody should blame them because stuff like this WILL happen. 


Nice addition to that:
[http://wiki.whatthehack.org/index.php/Everything_You_Know_About_Client_Security_Is_Wrong](http://wiki.whatthehack.org/index.php/Everything_You_Know_About_Client_Security_Is_Wrong)
The Video:
[http://rehash.whatthehack.org/wth/rawtapes/wth_client_security_is_wrong/wth_client_security_is_wrong_96.mp4](http://rehash.whatthehack.org/wth/rawtapes/wth_client_security_is_wrong/wth_client_security_is_wrong_96.mp4)

---

### Post by fhmanas on 2008-04-30
Wine is trying to emulate Windows APIs to allow Windows Apps to run in a Linux environment.  In doing so, the objective is make Apps run in Wine as they would in a real Windows environment otherwise it would be unsuccesful in its objective.  The Wine developers have no control of what apps get developed in the Windows environment since Virus are no more an app as OpenOffice is so it would be reasonable to assume that a Virus will run in Wine.  Now the question is, how will it affect the Linux environment where Wine resides, I believe that the 'fear' that it will jeopardize the Linux environment is unfounded at the moment unless the Virus/Spyware targets Wine specifically.  If I were a MS Virus programmer (I'm not:-k) creating a Virus for Wine is plain stupid, since I would be banging my head trying to make it work in Wine when a lot of Apps don't work in Wine anyway.  Besides, my "virus" would move if it were targeting Wine anyway.

Anyway, if you really fear Win Apps getting infected then Wine nor Windows Apps are for you.  You can actually look around for alternatives for Linux that are really secure.

But, remember the most secure systems can still be hacked.  If you really want it secure, don't plug it.

---

### Post by tzembi on 2008-04-30
> **fhmanas said:**
> Wine is trying to emulate Windows APIs to allow Windows Apps to run in a Linux environment.  In doing so, the objective is make Apps run in Wine as they would in a real Windows environment otherwise it would be unsuccesful in its objective.  The Wine developers have no control of what apps get developed in the Windows environment since Virus are no more an app as OpenOffice is so it would be reasonable to assume that a Virus will run in Wine.  Now the question is, how will it affect the Linux environment where Wine resides, I believe that the 'fear' that it will jeopardize the Linux environment is unfounded at the moment unless the Virus/Spyware targets Wine specifically.  If I were a MS Virus programmer (I'm not:-k) creating a Virus for Wine is plain stupid, since I would be banging my head trying to make it work in Wine when a lot of Apps don't work in Wine anyway.  Besides, my "virus" would move if it were targeting Wine anyway.

Anyway, if you really fear Win Apps getting infected then Wine nor Windows Apps are for you.  You can actually look around for alternatives for Linux that are really secure.

But, remember the most secure systems can still be hacked.  If you really want it secure, don't plug it.

Basically you are saying: "Wine does what it should do, no problem. If your Windows App is shitty, dont run it." please see my solution 1:

> 1.: Dont run these Windows Applications.

I have already taken this for granted (this is why i was trying to bring this "issue" to this Distries attention by discussing here and not on the wine forums).

I posted some solutions, they are not nice, but they work for me and i thought it would be nice to share them.

I am tired of this discussion running in endless circles ...

---

### Post by GurneyHalleck on 2009-04-07
I'm with tzembi on this one.

Yes, Wine is a fantastic piece of software (I can run Spotify in Ubuntu with seemingly no bugs except for the baseline volume being very low). But if there are methods to make it more secure, such as hiding the parts of the filesystem that you wouldn't want Windows apps to access, then it's worth a discussion about such methods.

Before hunting for a discussion about Wine and security, I removed the drive mapping Z: that pointed to my Ubuntu filesystem root. However, if I use a file browser in Spotify, I can still see my filesystem root, so this doesn't seem to have stopped Windows apps from accessing my entire filesystem.

And just because I trust an app not to be infected with third-party malware, doesn't mean I can necessarily trust an app not to be breaching my privacy by hunting around my filesystem and reporting back on what it finds.

---

### Post by asdfoo on 2009-04-08
> **GurneyHalleck said:**
> I'm with tzembi on this one.

Yes, Wine is a fantastic piece of software (I can run Spotify in Ubuntu with seemingly no bugs except for the baseline volume being very low). But if there are methods to make it more secure, such as hiding the parts of the filesystem that you wouldn't want Windows apps to access, then it's worth a discussion about such methods.

Before hunting for a discussion about Wine and security, I removed the drive mapping Z: that pointed to my Ubuntu filesystem root. However, if I use a file browser in Spotify, I can still see my filesystem root, so this doesn't seem to have stopped Windows apps from accessing my entire filesystem.

And just because I trust an app not to be infected with third-party malware, doesn't mean I can necessarily trust an app not to be breaching my privacy by hunting around my filesystem and reporting back on what it finds.


Way to dig up an old thread...  any real security solution will not be implemented using Wine, you need to use something like selinux to say "ok, Wine can only access files under ~/.wine - nothing else"

You either have to restrict access at the kernel level or completely trust the applications you run.

---

### Post by bodhi.zazen on 2009-04-08
Ubuntu uses Apparmor rather then SELinux. And you will have to give access outside of ~/.wine as the wine binary and other files / directories you will need are outside of ~/.wine

---

### Post by GurneyHalleck on 2009-04-24
Yeah, I know it's an old thread, but the topic was exactly what I was looking for, so . . .

bodhi.zazen, are you saying that it's hard work to limit Wine to a safe set of directories, or are you saying it's impossible? (Well, impossible without serious reconfiguration on several levels.)

---

### Post by bodhi.zazen on 2009-04-24
It is very easy to confine wine to ~/.wine

go to the directory ~/.wine/dosdevices and remove the symlink to your home and root directory. done.

If you want to "be sure" , make a profile for wine in apparmor ;)

That will take more time, but apparmor can lock down anything.

See the advice I added recently to the security thread (I added a wine section).

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by foresto on 2012-07-22
For what it's worth, tzembi, I understand your point perfectly.  

You might be interested in the [Arkose](https://launchpad.net/arkose) application sandboxing tool, which is now part of the Ubuntu Universe repository.  I haven't used it, but it looks very interesting.  [Here](http://www.stgraber.org/category/arkose/) are some blog posts from the developer.

You might also want to take a look at the [AppArmor profiles]("http://ubuntuforums.org/showthread.php?t=2031883") I made for blocking Windows applications from network access.

---

### Post by Lyfang on 2012-07-22
Security concerned or even paranoid? Run [BitDefender Antivirus Scanner for Unices]("http://unices.bitdefender.com/") 

See also: [Leak test failed! firestarter]("http://ubuntuforums.org/showthread.php?t=908884")

---

