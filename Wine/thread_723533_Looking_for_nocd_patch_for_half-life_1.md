---
title: "Looking for nocd patch for half-life 1"
date: 2008-03-13
forum: Wine
---

### Post by linuxjerk on 2008-03-13
I know there are numerous postings about running half-life under linux.

I see the nocd patch mentioned alot but I don't see any links to get it.

There is even a "how to" for half-life. No mention of nocd. No mention of the not finding cd problem at all.

If someone can please point me to a link for downloading the nocd patch that would be great.

But I think there will be more to it than that. There always is.

thanks

---

### Post by {BzF}~JOKesTER on 2008-03-13
[http://www.freeinfosociety.com/site.php?postnum=1079](http://www.freeinfosociety.com/site.php?postnum=1079)

Hope This Helps!!

{If So Hit "Thank"}:)

---

### Post by linuxjerk on 2008-03-13
Fantastic {BzF}~JOKesTER

The game seems to be working great.

No longer looks for the cd.

Thanks

---

### Post by linuxjerk on 2008-03-14
Strangest thing happened.

I ran the nocd crack for half-life in wine yesterday.

Worked first try. Played the game for an hour. Everything worked normal.

I noticed that when I quit the game that it did not exit normaly.

Didn't think anything of it. But when I tried running the game today
it's back to "insert the cd"?????

Tried running the crack again. No go.

Uninstalled the game then reinstalled it and ran the crack as directed and still no go???

Any ideas why this crack would work once and never again????

---

### Post by {BzF}~JOKesTER on 2008-03-14
Hmm..

IDK Dude>?

Maybe Try Getting A Different Version Of The Crack - 

Also Try Going Into The Registry And Deleteing The Games Settings

And Than Re-installing The Game.

You Can Do This By Browsing To The Wine's C:\ Drive And Than The "Windows" Folder And Running regedit.exe

Hope This Helps Ya'

Keep Me Updated!!

---

### Post by linuxjerk on 2008-03-14
Hello again:)

The version of the crack that I downloaded matches the version of the game that I have.

What version would you suggest that I download?

I will try to edit the registry. I forgot that wine does have one.

thanks

---

### Post by {BzF}~JOKesTER on 2008-03-14
Suggest Downloading The Latest Version Of The Patch - As It Works Once You Update The Game - Note: You Will Have To Re-install The Patch
When It Updates - As It Downloads New Executables.

Try The Newest Version

And Edit Out The Registry.:):)

---

### Post by linuxjerk on 2008-03-14
I uninstalled the game.

I cleaned all traces of half-life from the registry.

I reinstalled the game

Ran the crack. Deleted the file they said.

The game asks for the cd.

You know I have not been able to update the half life game. Is that what you are asking me to do?

The latest version of the nocd crack will not work with the version of the game I have?

I don't know what to do then.

---

### Post by {BzF}~JOKesTER on 2008-03-14
Try Dowloading The Version That Worked Lasttime Than:)

---

### Post by linuxjerk on 2008-03-14
Right now the update screen for half-life is stuck on my screen. I cannot get it to go away. It's not doing anything. Oh now it says my connection to the internet is invalid.
Well if my connection is invalid then I guess I can't be posting this;)

Why should I download the crack again? I already have it.

Do you think the crack I downloaded is corrupt? I will download it again but I think the same thing will happen.

This is insane. Why won't hl find the cd through wine in the first place?

---

### Post by {BzF}~JOKesTER on 2008-03-14
It Can-Just Do This:

Open A Terminal And Type:

sudo wineconfig

And Goto The "Drives" Tab.

Click And Map The Drive D:\ To Your Cd Drive In :

/Media/Cdrom0

---

### Post by linuxjerk on 2008-03-14
when I type sudo wineconfig I get command not found.

when I go to wine configuration and try to map cdrom0 I can never seem to get it to stick.

on another note I completely uninstalled halflife and checked the registry and everything was gone.

reinstalled halflife after a reboot.

re downloaded the crack. followed the instructions.

Asks for the cd. :(

---

### Post by {BzF}~JOKesTER on 2008-03-14
My Bad - Sorry It's

sudo winecfg

---

### Post by linuxjerk on 2008-03-14
ok this is the same stupid screen I get when I go into the regular wine configuration.

No what exactly am I suppose to do? Can you walk me through this?

I will have the cd in the drive that is normaly D: in windows.

Thanks

---

### Post by {BzF}~JOKesTER on 2008-03-14
Yeah It's The Same Screen As Exept Its Using sudo Which Gives Root Access.

Ok Go To The "Drives" Tab

And Click Remove On Whatever Drive Is Currently Mapped As D:\ {If There is One}

Now Click "Add" And Give The Directory To Your CD Drive - Most Likely /Media/Cdrom0

If You Need Any Help Please Feel Free To Ask Me!:)

Happy To Help:)

---

### Post by linuxjerk on 2008-03-14
ok this is exactly what I'm seeing in the drive config windows
I'm not exactly sure how they got that way.

A: /media/cdrom d:
C: ../drive_c
D: /media/cdrom0
E: /media/cdrom1
F: /
G: d:/

Path: /media/cdrom d:


Maybe you can make some sense of this. thanks

---

### Post by {BzF}~JOKesTER on 2008-03-14
Remove:

A: /media/cdrom d:

D: /media/cdrom0

E: /media/cdrom1

And:

G: d:/

By Selecting Them And Pressing The "Remove" Button.

Now Click "Add" -{The Entrys Prefix Should Be D:\}

Map That To:

/media/cdrom0

---

### Post by linuxjerk on 2008-03-14
I'll be damned. It found it. I bet that was the problem all along.

I hope this fix works tomorrow. :lolflag:

---

### Post by {BzF}~JOKesTER on 2008-03-14
Well Good Job.

Was It The Fix I Gave You Just Now??

If So Pressing The "Thanks" Button As Much As Your Heart Desires Whould Be Greatly Appreccatied.:)

I Hope You Enjoy Playing!!!:)

---

### Post by linuxjerk on 2008-03-14
Yes it was, now the game finds the cd like it should.

Don't need the nocd crack.

There are still some weird behavior in the game but at least it's 
playable now.

Fantastic.

I'll press as many thanks buttons as I can find.

Thanks

---

### Post by {BzF}~JOKesTER on 2008-03-15
Please Remember To Rename This Post With [SOLVED] At The Begining So Others Can Benifit From It!!!:)

---

### Post by CrIpPeN on 2008-09-19
I got the same problem, I got Half-life 1.0

And it always asking for my cd. 


Wine Cfg 

A: /media/floppy0
C: ../drive_c
D: /media/cdrom1
E: /media/cdrom0
f: /media Sdb1
H: /home/*****
z: /

---

### Post by Ferrat on 2008-09-20
> **{BzF}~JOKesTER said:**
> My Bad - Sorry It's

sudo winecfg

:confused:
why sudo? wine never needs sudo ever and afaik you should avoid using sudo with wine?

---

### Post by Gcentrex on 2008-09-20
This thread is not even needed all that's required for the old Half-Life pre-steam to work without a CD is update the game client with the old patches the CD check was officially removed later in the games life.

The other option if you own the game is download steam add the games CD-Key into it then download the steam version it can be played later without steam by using SteamEmu/RevEmu or any other steam client emulator.

---

### Post by Rhemat on 2009-01-30
What file and where would I go to update the game client.  I don't feel like dealing with Steam, and I've tried a couple of No CD cracks, that did not work at all.
Thanks in advance.

---

### Post by Brynster on 2009-01-30
Am I missing something here.

would it not be easier to go to [www.steampowered.com](www.steampowered.com) and download the steam client.

When its installed allow it to install HalfLife then at the bottom of the Steam games list click on register new game key. and use you genuine cd edition registration key. 

Hey presto game works perfectly and you get the latest version with bug fixes and slightly updated graphics packs....

---

