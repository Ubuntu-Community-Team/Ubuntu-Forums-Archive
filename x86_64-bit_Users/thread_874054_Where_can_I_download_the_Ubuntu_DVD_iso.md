---
title: "Where can I download the Ubuntu DVD iso"
date: 2008-07-29
forum: x86 64-bit Users
---

### Post by skiny_crx on 2008-07-29
Have looked all over but cant find the DVD iso for Ubuntu.

Can anyone help please?

Really need it asap.

---

### Post by Jordanwb on 2008-07-29
For 8.04: [http://cdimage.ubuntu.com/releases/hardy/release/](http://cdimage.ubuntu.com/releases/hardy/release/)

For 7.10: [http://cdimage.ubuntu.com/releases/gutsy/release/](http://cdimage.ubuntu.com/releases/gutsy/release/)

---

### Post by skiny_crx on 2008-07-29
They dont work mate,

Already tried them both.

Try to download them and says downloaded 700bytes in 1 sec, which deffo isnt right.

---

### Post by tamoneya on 2008-07-29
i think you have to dl the dvd versions via torrents.

[http://linuxtracker.org/index.php?page=torrent-details&id=6c2f277eadcf54521a4f3c119704dbe6f3bc68b2](http://linuxtracker.org/index.php?page=torrent-details&id=6c2f277eadcf54521a4f3c119704dbe6f3bc68b2)

---

### Post by skiny_crx on 2008-07-29
How come the links dont work?

---

### Post by tamoneya on 2008-07-29
> **skiny_crx said:**
> How come the links dont work?

they worked for me.....

---

### Post by trigsenior on 2008-07-29
hi
I doubt the problem has anything to do with Ubuntu download, if you wait for a minute or two it will might start. Else if all else fails you could always try to download in torrent form.

I presume you using windows.
To download a torrent you need to install a torrent program ( to dowload the torrent ) i suggest utorrent
[http://www.download.com/uTorrent/3000-2196_4-10528327.html?tag=lst-10&cdlPid=10804582](http://www.download.com/uTorrent/3000-2196_4-10528327.html?tag=lst-10&cdlPid=10804582)

in linux just apt-get install utorrent ( note need to become super user)

ps some one beat me to it should have refreshed ;)

---

### Post by skiny_crx on 2008-07-29
When I try to download them, it says complete in 1 sec.

---

### Post by dystorteddream on 2008-07-29
I think you're downloading the torrent file, which is quite small. Using a bittorrent program such as utorrent, deluge, etc will connect to peers that have the complete file and download the complete DVD iso. 

Hope it helps

---

### Post by skiny_crx on 2008-07-29
Im trying to download the 3.? and 4gb file.

It started once, but I cancelled it, now it keeps doing the same thing.

Just wont let me download the dvd image,

I have the cd image but I only have black dvd's, which i cant burn it onto. Or can I?#

---

### Post by dystorteddream on 2008-07-29
> **skiny_crx said:**
> Im trying to download the 3.? and 4gb file.

It started once, but I cancelled it, now it keeps doing the same thing.

Just wont let me download the dvd image,

I have the cd image but I only have black dvd's, which i cant burn it onto. Or can I?#
black dvd's? are we talking about the color of the disc or did you mean blank? Sounds like you're having a problem with the temporary internet file then... It finds the partial file under the same name and states it's done. Purge your temp internet files and retry. What OS are you using currently?

---

### Post by skiny_crx on 2008-07-29
Sorry I meant blank not black.

And am using windows xp.

Am at work, I need ubuntu for my home comp

---

### Post by niccholaspage on 2008-07-29
You can use the live CD with A DVD,Though I would rather find A way to download the Live DVD.

---

### Post by trigsenior on 2008-07-29
hi again,
Another option would be to go into a news agent on you way home from work and buy a linux magazine with a ubuntu disk. Almost all news agents sell them cheap.

---

### Post by mordak13 on 2008-07-29
> **Jordanwb said:**
> For 8.04: [http://cdimage.ubuntu.com/releases/hardy/release/](http://cdimage.ubuntu.com/releases/hardy/release/)

For 7.10: [http://cdimage.ubuntu.com/releases/gutsy/release/](http://cdimage.ubuntu.com/releases/gutsy/release/)

The links work for me. I also use DownThemAll addon for Firefox as a download manager.

---

### Post by niccholaspage on 2008-07-29
The links above also work for me.

---

### Post by stchman on 2008-07-30
This works.

[http://cdimage.ubuntu.com/releases/hardy/release/ubuntu-8.04.1-dvd-amd64.iso](http://cdimage.ubuntu.com/releases/hardy/release/ubuntu-8.04.1-dvd-amd64.iso)

---

### Post by soxs on 2008-07-30
> **skiny_crx said:**
> When I try to download them, it says complete in 1 sec.

You donwloaded a torrent file(at least the time/size would fit to that). This can be used to download the dvd .iso via a p2p program (torrent program). Use utorrent on windows or whatever you'd like to. Open the dowloaded file with the torrentprogram and it should start downloading

---

### Post by Jordanwb on 2008-07-30
So you try to download the 4Gig ISO's but they cancel by themselves? If so you'll have to download through BT or try through Firefox. There's some bug in IE that prevents downloads over 2GB.

---

### Post by skiny_crx on 2008-07-31
Right now I've got the CD

It wont install.

I selected use the entire disk, and it gets tuck on 5%.

I also done a memtest 86+ cause my comp has been playing up and came up with 1150 errors, and it took 12 hours and it didnt even finish.

But what happens is with XP on my comp it gets to the XP screen and crashes again and again, then I installed ubuntu and worked fine, then i went back to xpand kept on doing the same thing, Now I want to go back on ubuntu it wont even install.

---

### Post by Jordanwb on 2008-07-31
I don't think memtest's test actually finishes, it just keeps going (corfirm/deny?). So since Ubuntu's installation stalls at 5% (Installing?), Ubuntu is not to blame for Windows' problems. Are you sure it stalls and not just taking a while?

---

### Post by jerome1232 on 2008-07-31
Yeah memtest will just run pass after pass after pass (takes about 15 minutes for a single pass on my machine) If memtest is showing errors your ram may be on it's way to becoming toasty. (is that all memtest tests or does it test the cpu out too?)

Depending on size and type of hard drive partitioning can take a really long time so you may want to grab dinner before you determine the install has hung.

---

### Post by Jordanwb on 2008-07-31
Also I've read (and confirmed), that the file system the root partition is makes a difference (although not massive differences). memtest tests only memory, hence the name ;-)

Also I installed Ubuntu onto a computer that a teacher had. Memtest threw hundreds of errors because the motherboard supported only DIMM(Dual Inline Memory Module) sticks, and there were a SIMM (Single Inline Memory Module) stick in a slot.

I recommend taking out all but one stick (I suggest the newest stick), then run memtest. If there are no errors after an hour, stop and switch for another stick (the next newest one). Keep swapping till you find the one that's messed up. If no errors are found put in two, then try moving them around. I had a problem with one particular stick on one of the four slots on my board. Also try vacuuming your board, there may be dust in the slot (but be careful).

---

### Post by Jouke74 on 2008-08-01
Yup, nothing is more dangerous than installing an OS and using a computer which has faulty memory. Remove the faulty memory first and replace it if required. Then re-install Ubuntu and or Windows.

Note that as soon as the faulty memory is used for file management, faulty data can also be written to your harddrive. Checksums may fail etc.

---

### Post by skiny_crx on 2008-08-01
Right well now I can get to 73% on the installation progess
but then I get an error message saying that the cd is faulty.:confused:

---

### Post by Jordanwb on 2008-08-01
Hmm. When the computer first boots off the CD and you get the menu, there's an option "Check CD for defects" and if it says it's defective, you'll need to re-write the CD.

---

### Post by skiny_crx on 2008-08-02
Says 1 error found.

Burned the disc again and now gets stuck at 25%!!!

Im getting really frustrated now.

:confused:

---

### Post by jerome1232 on 2008-08-02
Burning at 1x is very reliable :)

---

### Post by Jordanwb on 2008-08-02
> **skiny_crx said:**
> Says 1 error found.

Burned the disc again and now gets stuck at 25%!!!

Im getting really frustrated now.

:confused:

Did you try the "Check the CD for defects" option at the boot menu?

---

### Post by skiny_crx on 2008-08-02
Yes I did,

Said 1 error found.

Doesnt say what, just says 1 error found.

1st time I burnt it got stuck at 73%

2nd time now gets stuck on 25%.

If I burn it a 1x will take all night and all day.

:lolflag::(

---

### Post by Jordanwb on 2008-08-02
Well if both CD checks fail, then either try the 1X burn or there's something wrong with your burner.

Also there md5 checksums available at the download site. I wouldn't have a clue on how to check the iso if there's a problem with it in Windows.

---

### Post by skiny_crx on 2008-08-03
It doesnt get stuck whilst checking the cd for defects.

It gets stuck on the installation progress.

:guitar:

---

### Post by Jouke74 on 2008-08-03
> I also done a memtest 86+ cause my comp has been playing up and came up with 1150 errors, and it took 12 hours and it didnt even finish.

Did you replace your RAM memory and take out the faulty stuff. Because if you left it in, it will take forever for you to install an OS without problems. Faulty memory means that a central piece of your hardware is damaged. It will affect your whole system and gives this sort of problems: 

OS crashes Windows XP and Ubuntu,
Wrong burnt CD's and DVD's,
MD5 checksum failures,
Data loss and corruption on your harddrives,
Program crashes.

I cannot make this any easier. Normally your computer says 1+1 is 2. However in your case the memory is broken so the 1 is sometimes reread as 0 or any other number. Hence 1 + 1 can be any number. The more intensively you use it, the more likely an error occurs. Any error can make the OS install stop and that is what's happening.

---

### Post by Ptero-4 on 2008-08-04
It can also be sending bad data to the CD burner (hence the bad CD's) even if the iso itself is complete.

---

### Post by skiny_crx on 2008-08-08
Am burning the cd's on another computer.

Not my home one.

And still have the same problem.

Will just restore the factory settings on my comp and see what happens:lolflag:

---

### Post by Jordanwb on 2008-08-08
> **Ptero-4 said:**
> It can also be sending bad data to the CD burner (hence the bad CD's) even if the iso itself is complete.

Or it could be the other way around. Writing is find but reading fails. I tried to install Kubuntu on my laptop and the install failed all over the place.

---

### Post by Ptero-4 on 2008-08-08
The only other option left is shipit.

---

### Post by jocko on 2008-08-09
> **skiny_crx said:**
> Right now I've got the CD

It wont install.

I selected use the entire disk, and it gets tuck on 5%.

I also done a memtest 86+ cause my comp has been playing up and [COLOR=Red]came up with 1150 errors[/COLOR], and it took 12 hours and it didnt even finish.

But what happens is with XP on my comp [COLOR=Red]it gets to the XP screen and crashes again [/COLOR]and again, then I installed ubuntu and worked fine, then i went back to xpand kept on doing the same thing, Now I want to go back on ubuntu it wont even install.

There is no point trying to install ubuntu on broken hardware. Replace your ram (or remove the broken one if you have more than one stick). It doesn't matter if you manage to burn a cd/dvd without defects, your computer will still fail to install because of the broken ram.
The reason that ubuntu fails to install, memtest report errors and windows xp crashes is that your memory is broken. You can't fix it any other way than by removing or replacing the broken memory. After that, windows should work (unless the file system has become damaged from the crashes), ubuntu should install fine and memtest should be able to run for days without errors.

**Other people:** Stop telling him to burn a new cd or get one from shippit. His problem is not with the cd's he's tried, but with his actual hardware, without fixing the bad ram he will never be able to install ubuntu (or if he just by a million-to-one chance managed to install, the system would still be completely unusable because of the instability caused by the bad ram).

---

### Post by Jordanwb on 2008-08-09
> **jocko said:**
> **Other people:** Stop telling him to burn a new cd or get one from shippit. His problem is not with the cd's he's tried, but with his actual hardware, without fixing the bad ram he will never be able to install ubuntu (or if he just by a million-to-one chance managed to install, the system would still be completely unusable because of the instability caused by the bad ram).

I installed Ubuntu on a PC for a teacher of mine. He got a bunch of memtest errors because he had DIMM memory mixed in with SIMM memory.

---

### Post by danrael on 2008-08-09
> **skiny_crx said:**
> Am burning the cd's on another computer.

Not my home one.

And still have the same problem.

Will just restore the factory settings on my comp and see what happens:lolflag:

May I make a suggestion?  I do not think you are having a hardware problem.  I have had issues with bittorrent downloads being corrupt before, and avoid them whenever possible.  

Go back to the original download page as linked to you, and make sure you choose the ubuntu 8.04 dvd 64 bit STANDARD download, NOT the torrent version.  It will probably download faster than the torrent number anyway.  Then burn it onto a blank DVD.  Before you boot it up, choose the 'Media Check' from the Ubuntu menu and let that run.  Then go for it.

---

### Post by insane_alien on 2008-08-09
you must have had a bad torrent file. the torrent file contains all the hashes for each chunk of data and checks them as they come in. you can optionally force them to be rechecked upon completion.

heck, i even use torrents to cure corrupt files(in particular bad downloads of distro images.)

---

### Post by Jordanwb on 2008-08-09
It won't make a difference how he downloads it. If anything BT will be better because it performs an MD5 has check to make sure it's valid. I've had bad downloads through standard downloading but never with bT.

---

### Post by jocko on 2008-08-09
> **Jordanwb said:**
> It won't make a difference how he downloads it. If anything BT will be better because it performs an MD5 has check to make sure it's valid. I've had bad downloads through standard downloading but never with bT.

Still... The problem is most likely that his computer has a bad stick of ram. A new cd will not solve that. It doesn't matter if he downloads from torrent or ftp or whatever. If you read his posts, you will see that he has three different symptoms:

1. Constant Windows crashes.
2. Ubuntu installation fails at different points during the install.
3. Memtest reports errors.
4. The CD test reports errors
5. Ubuntu installation still fails after burning new cds.

So either he has: Toasted his windows install (explains symtom 1), burned several bad cd's (2, 4 and 5) *and* got a *slightly* bad ram (3), or he has... simply got a *really* bad ram (1, 2, 3, 4 and 5)...

Whenever you have more than one explanation for a phenomenon, the one that requires the fewest assumptions is usually the correct one.

---

### Post by Ptero-4 on 2008-08-10
> **jocko said:**
> 
1. Constant [COLOR="Red"]Windows crashes[/COLOR].


I don't think you can take that as an indicator of failing hardware. Because this is normal windows behavior.

---

### Post by jocko on 2008-08-10
> **Ptero-4 said:**
> I don't think you can take that as an indicator of failing hardware. Because this is normal windows behavior.
Sure, but ONE of the reasons windows can crash, other than the normal bugs, malware, poor design and virus infections, is hardware failure, same as ONE of the possible reasons why an ubuntu installation fails may be hardware failure. And THE reason memtest reports faulty memory is... ehhh... faulty memory...
I may be wrong, and the op is just extremely unlucky and every piece of software he tries to run in his computer is failing by completely different reasons, or they all fail because of the same reason... Which is more likely?

One thing he could test before he tries to replace ram is to try to either reinstall windows or try a completely different linux distribution. If he has a bad ram, it's very likely that both the windows installer and another linux distro will fail.

---

### Post by Jouke74 on 2008-08-10
Sigh... this is very bad. I tried to warn already about 8 posts back that with bad ram all sorts of errors can come up. Still people advise to install Ubuntu using the Bad ram. Also blaming again Windows as crashing. Well three more points then:

1. Even if I would send hem a perfectly fine DVD (which I am willing to do) he will still get errors if he has bad ram (the subject of at least three posts). Where errors come up, I don't know, but they will come up, even if Ubuntu installs fine.

2. A cleanly installed Windows system is very rarely unstable and quite fast actually. I have not seen a blue screen in decades to be honest. And when I got a blue screen it was usually me tempering around with drivers. Don't diss Windows all the time, because of other people make mallware infecting it. 

3. I also installed OSes on a system with bad memory. Windows and Ubuntu worked fine. However, I had random crashes all the time where the computer would just hang. It took me a long time, but as soon as I took one RAM dimm out, everything was fine. School computers, are also not working as a home computer. Things are usually not heavily loaded and in case of errors there is usually a school server and disk image to repair stuff.

---

### Post by skiny_crx on 2008-08-12
Right well have burnt the cd again and installed Ubuntu fine and am using it on my comp and works perfect.

SO it was the cd's that were faulty.

But Windows still doesnt work, I reinstalled XP and still get the same problem but this time get a blue scree, which says error in new hardware or something, but havent put any new hardware on so that doesnt make sense.

what I want to know is how come linix works and windows doesnt?

---

### Post by Jordanwb on 2008-08-12
Blue screens can be caused by bad memory. I don't know how the linux kernel handles bad memory but is it possible that the kernel detects bad areas and doesn't use them?

---

### Post by skiny_crx on 2008-08-12
Yeah so could be bad memory.

---

### Post by Jordanwb on 2008-08-12
Try changing the arrangment of the memory sticks. On my mobo it didn't like having one particular stick in one particular slot. Any other slot was fine and any other stick was fine in that one slot. Go figure.

---

### Post by skiny_crx on 2008-08-13
I would, but I dont wanna **** the comp up even more than it already is.

Though I might have a go at playing around the the ram sticks etc and see what happens.

Acer are just useless, they want £100 so they can check it for?

I mean WTF?

:confused::(:confused:

---

### Post by Jordanwb on 2008-08-13
Swapping the ram around is currently your cheapest option.

---

### Post by skiny_crx on 2008-08-21
Will be giving that a go tomorrow morning.

Any tips on what to do, and what not to do?

---

### Post by jerome1232 on 2008-08-21
Don't drag your feet on the carpet and then start working on your computer :D

But seriously touch your power supply every so often to discharge static, memory is susceptible to static discharge frying it.

Avoid flexing the motherboard to much when inserting ram, if the case isn't sturdy enough to prevent it, put your hand on the back of the panel that holds the motherboard if a stick of ram is proving stubborn about going into a slot. (I know mine are)

---

