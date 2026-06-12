---
title: "Citrix ICA client on 8.10 Intrepid Ibex"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by GordonPMartin on 2009-01-28
Has anyone had any luck installing the Citrix ICA client on Ubuntu 8.10 Intrepid Ibex?  I'm having one hell of a time.

I've been working for a couple days on this and have followed endless variations of instructions.  Hopefully my OS isn't in too bad a state...

My main series of steps to date:

- I followed the great instructions from this page: [https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo")

- Everything looked good until the section about actually USING the Citrix client.

- I got icons in Application|Internet that don't work. "Citrix Presentation Server Client" does nothing (doesn't popup a window or anything). "Citrix PNA Menu Items" just pops up the error "Could not find "/home/gordon/.ICAClient/pna_menu_items".

- From the terminal I tried "/usr/lib/ICAClient/wfcmgr" which returned the error: "/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory"

- This lead me to this forum post: [http://ubuntuforums.org/showthread.php?t=39556]("http://ubuntuforums.org/showthread.php?t=39556")  where I tried the following:

[INDENT]
Workaround is to download the 32 bit libmotif3 manually from:
http://<mirror>/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb

Then install it with sudo dpkg -i --force-architecture libmotif3_2.2.3-2_i386.deb
And then sudo ln -s /usr/lib/libXm.so.3 /usr/lib32/libXm.so.3[/INDENT]

- Now when I try "/usr/lib/ICAClient/wfcmgr", I get the error "/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXp.so.6: cannot open shared object file: No such file or directory" (progress I guess)

- I have found very little guidance on this last issue.  I tried the following: "sudo apt-get install libxp6" to no positive effect.

Can anyone help me?  I am still running on a high after managing to get vpnc to connect to work, but I'm getting a little deflated that stale Citrix software is going to stop me in my tracks  :-(

Do I perhaps have to resort to the Windows version under WINE?  (Hopefully it will work with the vpnc client running outside of WINE)

---

### Post by gila_monster on 2009-01-29
Not really. I see pretty much what you see. I haven't checked the instructions in your link, though -- followed other instructions from other source. I'll check out your link and if I get things going, I'll post here.

gila

---

### Post by ddales on 2009-01-30
I haven't been able to get the ICA Client working except under the Web Client.  After reading your post I've been messing with the libXm.so.3 problem and can't seem to solve it either.  I'll keep experimenting though.

It's found under /usr/lib but even after changing my PATH environment variable wfcmgr still says it's not found.

---

### Post by Yellow Pasque on 2009-01-30
> It's found under /usr/lib but even after changing my PATH environment variable wfcmgr still says it's not found.

Citrix is a 32-bit program and looking for 32-bit versions of those libraries in /usr/lib32.

DO NOT copy 64-bit libraries from /usr/lib into /usr/lib32. Instead, use getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by TehLiberating on 2009-02-01
I've got it working for my environment by using getlibs.

I needed to use it on ./linux86/echo_cmd just before running ./setupwfc
Once installed, ran it against wfcmgr and wfcica in the install directory.

---

### Post by GordonPMartin on 2009-02-02
Woohoo!!

That **getlibs** was the missing piece of the puzzle.  Thanks so much!

Because of how far I had gotten, I only had to issue the following command to get everything working:

getlibs -l libXp.so.6

I'm am now happily teleworking from my Linux box... just one small issue left...when I double-click my mouse, the remote session is seeing it as two single-clicks.  Anyone have a solution for this?  At the moment I have to right-click and choose the action I am looking for.


Thanks again,

Gordon

---

### Post by GordonPMartin on 2009-02-02
A revision to my double-click problem...

I am able to double-click on the first machine I hit.  But then I use RDP from that first machine to hop off to some other computers (sometimes 4 hops deep!).  The RDP sessions don't see a double-click at all.  I've had no trouble using this exact same scenario from my Windows XP client with the real Citrix client.

---

### Post by GordonPMartin on 2009-02-02
Another small detail that I suspect is related:

If I hold the shift key down while typing, only about 75% of the characters appear in upper case.  This is problematic because the 2nd character is almost always in lower case - acronyms are a bitch  :-)

---

