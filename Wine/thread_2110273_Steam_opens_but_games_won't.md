---
title: "Steam opens but games won't"
date: 2013-01-29
forum: Wine
---

### Post by nick642 on 2013-01-29
Ok so my computer that was Windows 8 ended up crashing and said I didn't have an operating system, it wouldn't even let me reinstall windows on my computer. I tried a couple of older windows CDs I had still nothing. So I went to an old Linux CD I had installed it burnt a copy of Ubuntu 12.04.1 got that up and running been using that for a day or two now. I've got most of the files and programs I need working. Lots of Google and YouTube haha! I'm not very good with this stuff.

I did get wine and playonlinux all installed and running. I can't seem to get my steam games to work for me. I Googled and looked around for the better part of the day, still found nothing that was of much help to me. I found a good handful of people who couldn't get Stream to open, but that wasn't my problem.

these are the 3 games I downloaded and installed 

Total War Shogun 2. This one it would either start up I'd get to the Shogun loading screen (first thing that comes up) be there for a few seconds and then closes out.

Metro 2033. This one would black screen on me and either freeze my computer or would let me close it out. More times than not it just froze up.

Star Wars KOTOR 2. This one I was able to start up it kinda went black screen then it was at the main menu but half the screen was blank (some here some there)

I read saying to post the info from the teminal I don't know how to get that info. 

I've gone to system drives and put it to use the driver that is recommended. After I did that Shogun 2 wouldn't even start. Then now it does..?

Not sure if it's that these games aren't supported by wine, or what not. Or a user error that I can fix.

I'm pretty much happy with using Ubuntu, I just want to be able to play my games along with my everyday computer needs.

As I said above I'm not very good with computers, but if you post step by step how to find info you need, or how to fix. I'm sure I'll be able to do it.

***Wine and Ubuntu version*** 
Ubuntu 12.04.1
Wine1.4 1.4-0ubuntu4.1

***Terminal output*** 
Can someone explain how to get this while trying to run a game on Steam.

***Wine configuration*** 
Nothing that i am sure on. Info on how to check all this? 

[B][I]Hardware specs/drivers
[/I][/B]16gb ram
Intel® Core™ i7-2600K CPU @ 3.40GHz × 8 
EVGA GRX 560Ti Driver  I went to the additional drivers under system setting and used the one put as recommended says NVIDIA accelerated graphics driver (version current)[recommended]
GIGABYTE|GA-Z77-D3H Z77

***Other Wine applications*** 
I don't believe I have anything else. Info on how to double check?

****

---

### Post by Tweak42 on 2013-01-29
Welcome to Ubuntu and the Ubuntu Forums. :-)

First off Steam now has a native client for linux. It's in beta but and I'm not sure how tricky it is to make it download windows games and make them work in wine, but I'm sure you are not alone in that regard. Try checking: [http://steamcommunity.com/linux](http://steamcommunity.com/linux)

For help getting games running using wine, you need to provide specific information about your system software and hardware. I suggest reading the [sticky post]("http://ubuntuforums.org/showthread.php?t=885111") at the top of the wine forum, emphasis on the section **"Things to include when asking for help"**.  Also try to address only 1 app problem per thread, and title the thread descriptivly as so to cut down on clutter of unrelated apps issues.

---

### Post by nick642 on 2013-01-29
Steam does have a Linux setup now, but they don't have many games. The games they do have aren't ones I play.

I updated the first message with some more info. 

I am also looking around on
[http://steamcommunity.com/linux](http://steamcommunity.com/linux)

---

### Post by Tweak42 on 2013-01-29
> **nick642 said:**
> 
***Wine and Ubuntu version*** 
Ubuntu 12.04.1
Wine1.4 1.4-0ubuntu4.1

***Terminal output*** 
Can someone explain how to get this while trying to run a game on Steam.

***Wine configuration*** 
Nothing that i am sure on. Info on how to check all this? 

[B][I]Hardware specs/drivers
[/I][/B]16gb ram
Intel® Core™ i7-2600K CPU @ 3.40GHz × 8 
EVGA GRX 560Ti Driver  I went to the additional drivers under system setting and used the one put as recommended says NVIDIA accelerated graphics driver (version current)[recommended]
GIGABYTE|GA-Z77-D3H Z77

***Other Wine applications*** 
I don't believe I have anything else. Info on how to double check?

****

You can get latest version of wine (1.5.x) by adding the [Ubuntu Wine PPA]("https://launchpad.net/~ubuntu-wine/+archive/ppa") to your sources, then refreshing the update manager.

Wine has a configuration gui, "Configure Wine" in the launcher or winecfg in a terminal.  You can launch a terminal by entering "terminal" in the launcher or hotkeys CTRL-ALT-T.

I'm not sure how you get the terminal output from steam launched game but I'm assuming you would have to launch steam from the terminal and the output from the program it launches would show up in the output.

If the "accelerated" driver is installed you should be able to run the "Nvidia X Server Settings" from the launcher or "nvidia-settings" in terminal to find exactly what version of nvidia driver you are running.

You can search the [wine appdb]("http://appdb.winehq.org/") to see user reports on what games work or somewhat work and work arounds in cases.

---

### Post by sabersong on 2013-01-30
I've run the Windows version of Steam under Ubuntu in the past, and I have to start by saying that Steam itself will work under Wine, but individual games on the Steam client are a hit or miss thing. Some will work on Linux, some won't. I've only ever tried the free-to-play games under Wine, so I can't address the games you've mentioned.

I'm using the Steam beta client for Linux now. There are, as of January 2013, exactly 64 games available for the linux client. As I tend not to pay for things until I know they work, I've only tried one game, Team Fortress 2, as it's the only free-to-play availble right now, and it's not working for me. But it's a beta client, so I expect a few problems, and I expect they'll be sorted out before long.

---

### Post by AM Ramakrishnan on 2013-02-02
Running steam in WINE has given me the same problem:
[http://ubuntuforums.org/showthread.php?t=2103685](http://ubuntuforums.org/showthread.php?t=2103685)

---

### Post by RealmEleven on 2013-02-07
I know it's not quite the same game, but the following approach is reported to have worked for *Skyrim *which is not yet on the list of games for the Steam client on Linux. Anyway, it is worth a try:
.
[http://forums.bethsoft.com/topic/1259437-linux-wine/page__hl__ubuntu__fromsearch__1](http://forums.bethsoft.com/topic/1259437-linux-wine/page__hl__ubuntu__fromsearch__1)
.
Good luck...

---

