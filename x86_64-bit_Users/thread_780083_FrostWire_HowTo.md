---
title: "FrostWire HowTo"
date: 2008-05-03
forum: x86 64-bit Users
---

### Post by thekat on 2008-05-03
There are a few tricks to get FrostWire working on Hardy-64

Here are **hopefully** all the pieces in one thread..

Use Frostwire - version frostwire-4.13.3.i586.deb

The latest version frostwire-4.13.5 did not work for me it kept popping up an error messages over and over again.. 
I had to restart X to kill it..

Install the 32 bit version of java
```

 sudo apt-get install ia32-sun-java6-bin 

(this should also install ia32-libs)

```
Select your java version
```

sudo update-alternatives --config java

choose the ia32 one

```
Download frostwire-4.13.3.i586.deb 
```

[http://sourceforge.net/project/showfiles.php?group_id=142481]("http://sourceforge.net/project/showfiles.php?group_id=142481")

```

Install the new Gnutella file to fix the "Starting Connection Error"
(note: you **ALSO** have to have your firewall configured correctly)
```

Download fresh gnutella.net file from:
[www.clockworkgeek.com/gnutella.net]("www.clockworkgeek.com/gnutella.net")

```
Save this to your ./frostwire directory

Start FrostWire

Again, check your FireWall Software /Router for the correct port
settings.. I **think** most routers have Upnp enabled by default.

tk

---

### Post by ravenon on 2008-05-03
I too had problems with the Frostwire 4.13.5 version as stated above. What I did was delete my .frostwire folder in my home directory and restarted Frostwire. All has worked well since.

---

### Post by thekat on 2008-05-03
> **ravenon said:**
> I too had problems with the Frostwire 4.13.5 version as stated above. What I did was delete my .frostwire folder in my home directory and restarted Frostwire. All has worked well since.

I didn't really see any changes that were made 
in version 5 that I cared about.. 
other than the "Starting Connection" bug.. 
Replacing the gnetella.net file in version 4-13.3 was much
easier for me..

```

Frostwire Changelog:
version 4.13.5 (January-February 2008)
- More fixes on peer discovery on connection bootstraping. Fixes the 'Starting Connection' bug (at least on all of our tests)
- FrostWire is now capable of remembering announcements sent via the update system, that way users won't be annoyed by reading the same announcements for as long as we have them up.
- Added Smiley support to the Chatroom. Developer note: irc.jar is now part of our build process, One step build scripts for all distros.
- Fixed wording on spanish translation.
- Fixed bugs on the media player and playlists on Preview.
- Fixed bug on search box auto-focusing while a search was running.
- Fixed typo in Polish. Thanks Radek.

```

I did do some searching about the pop ups iv version 4-13.5 that wouldn't go away.. 
One of those was the fix you stated but didn't work for me so I went back
to 4-13.3.

tk

---

### Post by s_spiff on 2008-05-04
ok, i have no firewall installed, but i'm still not able to connect. Any ideas what to do? I'm on Hardy..

---

### Post by old_geekster on 2008-05-05
This is an excellent HowTo, but it didn't help me with my problem.  I don't even know what is causing it.

When I start "Frostwire", it says "Starting", but never does.  An error box pops up and pops up and pops up, you get the picture.  It never stops popping up.  It says something to the effect that "Port 6346" cannot be accessed.  Also, that the problem is normally caused by filtering by a firewall.  I setup "Firestarter" to allow access to port 6346, but it didn't help.

I would appreciate any suggestions.  I tried to take a screenshot of the error box, but it just wouldn't stand still long enough for the camera to catch it.

I had it (Frostwire) running after upgrading to Hardy from Gutsy, but then did a clean install and my problems began.

**UPDATE**: Well, I solved my problem.  It was the firewall blocking Frostwire.  I used Firestarter to allow FW to connect to my computer.  It worked.

---

### Post by raven on 2008-06-05
old_geekster, hot did you make your firestarter connect to your computer
and make FW works ?

I disabled firestarter and still FW cannot connect
PS: I' not talking about the endless popup about 6346 port, this is solved


Edit:
Solved, what I did is
1- open the ports for FW
2-delete .frostwire directory
3-launch frostwire, I cancel right away the wizard
4- I add the gnutella.net file to the .frostwire directory, downloaded from [http://www.clockworkgeek.com/gnutella.net](http://www.clockworkgeek.com/gnutella.net)
5- relaunch frostwire and I have turboconnection


Solved

---

### Post by BLTicklemonster on 2008-06-11
```
bill@bill-desktop:~$  sudo apt-get install ia32-sun-java6-bin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package ia32-sun-java6-bin has no installation candidate
bill@bill-desktop:~$ 
```

Now what? :)

---

