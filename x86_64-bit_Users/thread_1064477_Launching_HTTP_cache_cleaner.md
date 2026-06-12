---
title: "Launching HTTP cache cleaner"
date: 2009-02-08
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2009-02-08
Every so often I get this process running. It ties up one of the CPU cores for about 15 seconds while it runs. While it is running everything runs jerky. It started only a couple weeks ago.

Where did it come from? Do I need it? Should I disable it and, if so, how?

---

### Post by Ghost|BTFH on 2009-03-17
Hey John,

This is an annoying little program that is caused mainly from having KDE programs running in gnome, although I've heard issues with it in KDE as well, they are generally easy to fix. (Do a search for HTTP Cache Cleaner)

As for in Gnome, I've found a new way that appears to have completely removed it!  Why it fixed this, I have no clue, but it did, so I'm going to pass it on.

I went into terminal, and did the following:

sudo aptitude remove kubuntu-desktop

It scanned, didn't find the desktop, but found about half a dozen files that it said would be removed.  I told it to go ahead, and since then, ktorrent loads almost instantly (Used to take 3-5 seconds at least) and I have yet to see the HTTP Cache Cleaner pop up AT ALL.

I hope this solution helps you as well, if so, I might have to post a "SOLVED" thread.

Cheers,
Ghost

---

### Post by John Jason Jordan on 2009-03-17
> **Ghost|BTFH said:**
> 
This is an annoying little program that is caused mainly from having KDE programs running in gnome, although I've heard issues with it in KDE as well, they are generally easy to fix. (Do a search for HTTP Cache Cleaner)

As for in Gnome, I've found a new way that appears to have completely removed it!  Why it fixed this, I have no clue, but it did, so I'm going to pass it on.

I went into terminal, and did the following:

sudo aptitude remove kubuntu-desktop

It scanned, didn't find the desktop, but found about half a dozen files that it said would be removed.  I told it to go ahead, and since then, ktorrent loads almost instantly (Used to take 3-5 seconds at least) and I have yet to see the HTTP Cache Cleaner pop up AT ALL.

Thanks for the suggestion. I had already discovered that it was some part of KDE that was causing it. I tried your command line solution and this is what I got:

jjj@Devil7:~$ sudo aptitude remove kubuntu-desktop
[sudo] password for jjj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 86 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Then I launched Ktorrent. After about 15 minutes I got the stupid "launching HTTP cache cleaner" again. It seems to be only Ktorrent that causes it. I use Okular a lot and it never causes it, nor do I remember seeing it when running other KDE apps in my Gnome/Intrepid computer.

I have switched to Transmission, but Ktorrent has more features and I like its interface better. I wonder if anyone has filed a bug report on this issue.

---

### Post by Ghost|BTFH on 2009-03-17
Yeah, this bug is a over 2 years old, and they haven't really felt any need to fix it apparently, as it does nothing other than create a minor annoyance.

Do you by chance have Amarok installed?  I've heard that's a #1 offender.

My other suggestion would be silly, but might do the trick, and that would be to install some other minor KDE program that requires additional files, then do the kubuntu-desktop removal as before.

I had ktorrent installed, and then tried to install kcontrol (Which is no longer a separate item) which pointed me to a kdelibs file...

It was after installing that, and then doing the kubuntu-desktop removal, that about half a dozen files were located and removed - the the http cache cleaner has yet to be seen after that.

Sounds weird, but it worked for me.

Cheers,
Ghost

---

### Post by csc2ya on 2009-04-27
A definate way to fix this (although it's more of a workaround), is to install kcontrol (sudo apt-get install kcontrol) and then disable the http cache (applications > other > cache)

I was getting constant lockups in gnome and high load averages before I found that 10 minutes ago, installed that and disabled the cache, and my system is now as fast as it was when it was first installed and my load average doesn't go above 1 now.

It might only be a workaround, but it does appear to work for some people at least.

---

### Post by abhiroopb on 2009-05-03
The apt-get remove did not do anything, as I did not have that package installed.

This isn't really causing me a "problem" as it just runs in the background for a couple of seconds. But it would be useful to remove it. The kcontrol installs 219mb of data!

---

