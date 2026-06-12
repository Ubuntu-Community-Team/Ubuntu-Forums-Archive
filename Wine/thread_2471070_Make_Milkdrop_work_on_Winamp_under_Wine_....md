---
title: "Make Milkdrop work on Winamp under Wine ..."
date: 2022-01-20
forum: Wine
---

### Post by shantiq on 2022-01-20
Make Milkdrop work on Winamp under Wine   .... still nice in 2022 for folks who like vintage software:KS
===
I started reading around [here]("https://www.dedoimedo.com/games/wine-directx.html") > Read a few more articles and then:


&#10122; ```
sudo winetricks --self-update

```

You get this message:


This will install Winetricks directly from its original developers.  Debian has no control over that version.


&#10123; run : ```
winetricks

```&#10124; pick : Select the default prefix/ Install a Window DLL or component


&#10125; add all of these (not sure if all needed but I cast my net wide here)


[[IMG]https://i.postimg.cc/JHhqd7dg/d3d.png[/IMG]]("https://postimg.cc/JHhqd7dg")


&#10126; Then I checked running
```
winecfg
```  and found all there


[[IMG]https://i.postimg.cc/sG1Y46MC/Screenshot-from-2022-01-20-19-46-44.png[/IMG]]("https://postimg.cc/sG1Y46MC")

There find [Winamp]("https://download.nullsoft.com/winamp/client/winamp58_3660_beta_full_en-us.exe") official download and have some fun

---

### Post by TheFu on 2022-01-22
For a winamp-like native Linux audio player, check out xmms.

---

### Post by yetimon_64 on 2022-01-23
> **TheFu said:**
> For a winamp-like native Linux audio player, check out xmms.
Xmms is no longer available in 20.04. I think 16.04 (could've been 14.04) was the last release I had it running in and even then it was a massive hassle to get the interface working. I had been using the winamp like xmms player since Jaunty in 2009 .

The newer server/client xmms2 is used nowadays and doesn't have a GUI interface like xmms had; there are a couple of very simple interfaces, like gxmms2, for controlling it on the desktop but nothing like the old xmms interface had ...
```
apt-cache policy xmms
N: Unable to locate package xmms
```
```
apt-cache policy xmms2
xmms2:
  Installed: 0.8+dfsg-18.2ubuntu3
  Candidate: 0.8+dfsg-18.2ubuntu3
  Version table:
 *** 0.8+dfsg-18.2ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status
```

@ shantiq, thanks for posting this. As I've got wine installed here I'll be installing this and giving it a go again. Still like the older winamp interface for music playing; about the only leftover from my windows user days I actually still like nowadays. If I recall correctly, it was a thread/tutorial of yours quite a few years back that I followed to get my last version of the old xmms interface running :-).

 Cheers, yeti.

---

### Post by shantiq on 2022-01-23
Hi yeti and Fu been too a HUGE fan of XMMS for a long time see posts i placed here on this site of recent years;    it has such a clear sound ; use Audacious a lot too;    but and this is my thinking on these players at the mo;   Winamp was the urplayer the original and it works perfectly under Wine with [that version]("https://download.nullsoft.com/winamp/client/winamp58_3660_beta_full_en-us.exe") Winamp makes available after they got fed up seeing lots of kooky versions all over the net ...    so a year ago I decided to return to the mother software ...    that it is Windoze originally bothers me not as it is free and REALLY excellent and plays codecs others can only dream of .....     and [Milkdrop]("https://www.youtube.com/watch?v=CZz0a4Jg7-8") is still stunning nearly 20 years after conception ...   but yes on Ubuntu XMMS Audacious Winamp I have kept in rotation in my Linux years ....   also there is the issue that i rip 8-track to cuefile and ALAC   and XMMS  balks at that format; wish I could find someone who would know how to create an ALAC plugin which would work with cuefile for XMMS too learned for me :)       

here is my XMMS ; those graphix are not Milkdrop quality ;)
XMMS stills runs but there is a need to look at earlier howto's and try things out ....     got it here on 20.04

[[IMG]https://i.postimg.cc/mtpgnk03/Screenshot-from-2022-01-23-08-57-09.png[/IMG]]("https://postimg.cc/mtpgnk03")

check the list of plugins on my Winamp here; could not even display them all

[[IMG]https://i.postimg.cc/JHWpMRvP/Screenshot-from-2022-01-23-09-07-31.png[/IMG]]("https://postimg.cc/JHWpMRvP")

---

### Post by yetimon_64 on 2022-01-23
> **shantiq said:**
> ...     and [Milkdrop]("https://www.youtube.com/watch?v=CZz0a4Jg7-8") is still stunning nearly 20 years after conception ...
That it certainly is. Couldn't get the version of winamp you linked to above to install, so went and downloaded an older version (5.622, and virus checked it :-)) and it installed and works beautifully. With a bit of devilspie2 tweaking and winamp settings fidgeting I finally got milkdrop to work sucessfully as a desktop backdrop (screenshot attached below [[COLOR=#0000FF]--full resolution (google drive link)--[/COLOR]]("https://drive.google.com/file/d/1NKjeqcIZ5xHnLDfwuh1NVHJus2rfyrpS/view?usp=sharing")).

> **shantiq said:**
> ...XMMS stills runs but there is a need to look at earlier howto's and try things out ....     got it here on 20.04...That's impressive, I gave up after 16.04. Tried to follow your old how tos on 18.04 but had no luck getting xmms going.

Cheers, yeti.

---

### Post by TheFu on 2022-01-23
I have to admit, I stopped using xmms-like music systems long ago. I did like the simplicity. I barely used Clementine, then it became too bloated and the remote-control never worked for me due to different versions always being behind, so switched to mpd as the solution.  Added my own custom music-search bash script, completely separate from mpd too.

**mpd** is a server running on the system where the speakers are connected, but controlled by local or remote clients. There are 20+ clients, for all levels of need.
[LIST]
[*]Pure CLI - **mpc**
[*]Curses CLI - **ncmpc**
[*]Android App - **M.A.L.P.**
[/LIST]

And I created a few CLI+menu+ssh scripts into mpc on the mpd boxes. They work, but do have the overhead of an ssh connection for each command.
[LIST]
[*]a bash CLI+Menu+ssh script
[*]a bash whiptail (menu) + ssh script
[/LIST]

Mpd has the idea of playlists, but doesn't seem to support m3u files.  My music-search script ONLY supports playlists.m3u files. Sometimes that is all we want, right? Both can randomize, but I do remember the idea of albums and want to hear some in a specific order.
Little Dreamer **must** come before Ice Cream Man. It cannot be any other way. Wouldn't make sense.

None of these is perfect and there are times when the simplicity of winamp from the 1990s is all I want, even today.

---

### Post by shantiq on 2022-01-23
> **TheFu said:**
> 

None of these is perfect and there are times when the simplicity of winamp from the 1990s is all I want, even today.


yea :KS:KS

too complicated things get too complicated.    Do not know the one you mention here Mpc   but at times I have used MOC    probably a bit similar

[[img]https://i.postimg.cc/vD6cWqWb/Screenshot-from-2022-01-23-16-08-06.png[/img]](https://postimg.cc/vD6cWqWb)

===

Kudos Yeti on Milkdrop backdrop so cool   

I think my current XMMS prob was brought forward from earlier versions but in any case this is what is needed if you ever want to play further with install

[[IMG]https://i.postimg.cc/Lq2Yx96S/Screenshot-from-2022-01-23-10-27-21.png[/IMG]]("https://postimg.cc/Lq2Yx96S")

---

### Post by TheFu on 2022-01-23
**mp[COLOR="#FF0000"]c[/COLOR]** is pure command - do task - close.  The **mp[COLOR="#008000"]d[/COLOR] **server does what it was told regardless of the client connection.

$ mpc play
That has mpc connect to the mpd server and play where ever it left off.
$ mpc pause
$ mpc next
$ mpc prev
$ mpc vol+
$ mpc vol-
$ mpc mute
Simple CLI interface.  It does 1 thing at a time.  There are other things, like setting the volume to an absolute value and loading an existing playlist.  Any client, from any other system with connectivity can send the mpd server commands. Use which ever client is convenient.  I use ncmpc when I'm at a computer 99% of the time.  MALP when a tablet or phone is available.  MALP can connect to any of my 3 different mpd servers (3 different rooms). 2 of those "servers" are just raspberry pis connected to audio receiver systems.  Kids today would probably use a r-pi connected to bluetooth speakers.

Most minimalists would prefer ncmpc, which also takes some getting used to.  The playlist items have to be relative from the top music directory, so playlists inside the same directory as the music don't "just work", IME.  Nothing is perfect.  OTOH, loading every music file below a directory and playing it in order or randomized is really easy.

BTW, that screenshot is really funky if clicked. The aspect ratio is totally lost. Probably a javascript thing, since I don't allow javascript from most web servers - ever.

---

### Post by yetimon_64 on 2022-01-23
> **shantiq said:**
> ...this is what is needed if you ever want to play further with install...Just found the last of your 2 "how to" threads from 2016 with the download links for those dependency files and xmms files. Several are no longer available (404 file not found errors). If I recall correctly that is what blocked my last attempt back in 2018.

As well as learning how to set up and use xmms2 in 2018, I found "QMMP" which can be skinned to look like winamp. Functionality is slightly different but it is pretty good for a native linux app (only 1 very simple "analyzer" visualization plug in). 
See screenshot below; winamp running in wine beside QMMP. Actually winamp in wine sounds much better when compared with qmmp; that surprised me a bit.

> **TheFu said:**
> **...**The aspect ratio is totally lost. **Probably a javascript thing**,...
That is spot on, the image is severely distorted/huge until scripting is allowed.

---

### Post by shantiq on 2022-01-23
> **yetimon_64 said:**
>  Actually winamp in wine sounds much better when compared with qmmp; that surprised me a bit.

QMMP was always a letdown soundwise. Glad to have it confirmed:KS

---

