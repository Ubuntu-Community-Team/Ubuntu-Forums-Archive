---
title: "64bit Ubuntu ..."
date: 2006-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by slavik on 2006-01-23
yet again ... from the IRC channel, it seems like there are 4 reasons to NOT go with 64bit version of Ubuntu.

1. No Java plugin (I know about the 32bit version wiki page)
2. No Flash plugin (I know about the 32bit version wiki page)
3. No FreeNX (Since I will be using Ubuntu on a laptop, I really don't need this package anyway)
4. No w32codecs (Not really a showstopper for me)

About #1 and #2:
I know about the 32bit wiki page to get firefox installed. Hence a question. When installing firefox 1.5 on a 32bit install of Ubuntu, all firefox files were in a separate directory (in /opt/firefox/ if you follow the new version firefox wiki page instructions)

From those instructions, you could create a symbolic link or alias a command "firefox32" to /opt/firefox/firefox instead of replacing the system firefox. (replacing the system firefox in breezy can be done with a 64bit build of firefox).

About #3:
To me, FreeNX seems like SSH but with graphics ... The only thing related to FreeNX that I'd want to use on my laptop is a client, not a server. To access my home system.

About #4:
Could someone clarify which codecs exactly are affected? (Mpeg2? WMV? and such). While it would be a shame not to be able to play 'any' media file on my laptop, it's not a showstopper as the laptop is intended to be more of a web/email/coding type of system. For college. :)

If there are any other problems/concerns, please post.

---

### Post by RAOF on 2006-01-24
[QUOTE=slavik]...
About #4:
Could someone clarify which codecs exactly are affected? (Mpeg2? WMV? and such). While it would be a shame not to be able to play 'any' media file on my laptop, it's not a showstopper as the laptop is intended to be more of a web/email/coding type of system. For college. :)

If there are any other problems/concerns, please post.[/QUOTE]
Only amazingly non-free & convoluted codecs are affected.  So, WMV9 (also known as wmv3, no-one really knows why), realplayer stuff maybe.

---

### Post by slavik on 2006-01-24
[QUOTE=RAOF]Only amazingly non-free & convoluted codecs are affected.  So, WMV9 (also known as wmv3, no-one really knows why), realplayer stuff maybe.[/QUOTE]
Ok, that makes sense ... although that sucks, but whatever ... it's Microsoft's fault if they can't produce a 64bit version of their codec for *nix ^^

---

### Post by jon_gunnar on 2006-01-25
[QUOTE=slavik]Ok, that makes sense ... although that sucks, but whatever ... it's Microsoft's fault if they can't produce a 64bit version of their codec for *nix ^^[/QUOTE]
If you really need this to work its pretty easy to compile vlc to support it, didnt take me long,means it easy :-)

---

### Post by Wille on 2006-01-25
[QUOTE=slavik]yet again ... from the IRC channel, it seems like there are 4 reasons to NOT go with 64bit version of Ubuntu.

...

If there are any other problems/concerns, please post.[/QUOTE]

- Pasting to OpenOffice doesn't work.

- Totem crashes all the time.

---

### Post by jclw on 2006-01-25
btw: is it possible to use qemu for w32codecs?

---

### Post by slavik on 2006-01-25
Wille, do you know if the issue is present in 64bit Dapper?

jon_gunnar, so compiling VLC will allow you to use the weird codecs? So w32codec support is there ... just in a weird way.

---

### Post by gil-galad on 2006-01-25
No. w32codecs do not work with 64 bit programs, however, there are open source versions for almost every codec, so most videos work anyway.  I compiled mplayer with every option I could, and am pretty happy with it.  I can play most quicktime movies and such.

AND THERE IS A JAVA PLUGIN.  It is even in the repository.  
> sudo apt-get install j2re1.4-mozilla-plugin

Really the only problem I have had is flash, but I don't really miss flash too much.  Also 32 bit programs need to little extra work to get working, but you can get them to work.  

Also, you should be able to get FreeNX to work, I don't know why you wouldn't be able to.

---

### Post by Wille on 2006-01-26
[QUOTE=slavik]Wille, do you know if the issue is present in 64bit Dapper?[/quote]
No, I don't; I only have Dapper running on an old i686.

I still expect the amd64 version to get less love than i386, because after the Breezy amd64 experience I'd expect even fewer users will install the amd64 version. ;-)

---

### Post by slavik on 2006-01-26
My point is that I don't need freenx ... on my laptop!

I might want it on my home system (which is an athlonxp = 32bit) but not on my laptop ...

as for the 32bit programs, I can still compile them if I need for 64bit or is it easier to install the ia32libs and install the 32bit binaries of them?

gil-galad ... that 32bit mozilla plugin ... it's only the plugin or is that the entire jre? if it's only the plugin, that's sweet. :)

---

### Post by jon_gunnar on 2006-01-27
[QUOTE=slavik]Wille, do you know if the issue is present in 64bit Dapper?

jon_gunnar, so compiling VLC will allow you to use the weird codecs? So w32codec support is there ... just in a weird way.[/QUOTE]
It works for every thing I have tried it on yes.Never tried mov or real files,never watch those formats so I cant tell.
I used the instructions here for compiling: [http://nanocrew.net/2005/09/01/compiling-vlc/](http://nanocrew.net/2005/09/01/compiling-vlc/)

and checkinstall to install / make debs.

---

### Post by gil-galad on 2006-01-27
[QUOTE=slavik]
as for the 32bit programs, I can still compile them if I need for 64bit or is it easier to install the ia32libs and install the 32bit binaries of them?

gil-galad ... that 32bit mozilla plugin ... it's only the plugin or is that the entire jre? if it's only the plugin, that's sweet. :)[/QUOTE]

Its the plugin which depends on the jre, so its both.

If the program is open source, it is better to compile it.  However, you may need to run a binary-only 32bit program and then you would need to install 32bit libraries.

---

### Post by nikosft on 2006-01-28
-J2EE 
-Opera

> Ok, that makes sense ... although that sucks, but whatever ... it's Microsoft's fault if they can't produce a 64bit version of their codec 

Have you ever wondered why 32 bit programms run smoothy in Windows 64 bit? Don't you think as long as 64bit technology is quit new Linux 64bit versions should provide also backward compatibility?Not all of us are software engineering gurus to take the source code and compile it.do you think this is user friendliness?

---

### Post by slavik on 2006-01-28
no, it isn't ...

there isn't a linux distro that can close to winxp functionality out of the box ...

ubuntu gets really close though.

---

### Post by nikosft on 2006-01-28
I moved to 32bit version and I can say for sure thet I am much more happier!! Everything works as it was expected.

---

### Post by gil-galad on 2006-01-28
RPM distros work well with running 32bit programs on 64bit computers.  Take a look at Suse, for example, it works  at least as well as windows x64 for running 32bit and 64bit programs at the same time.  Ubuntu is just a little behind in that regard.

---

### Post by slavik on 2006-01-28
but if everyone moves to 32bit? the devs won't be able to fix the problems in 64bit version ...

---

### Post by nikosft on 2006-01-29
I can't wait for the developpers. My time is valuable!

---

