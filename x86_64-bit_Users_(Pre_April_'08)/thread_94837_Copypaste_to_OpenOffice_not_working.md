---
title: "Copy/paste to OpenOffice not working"
date: 2005-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by etitor on 2005-11-25
"Absolute beginner talk" has a thread about some Breezy users (including me) not being able to copy/paste from gedit (or Bluefish, or Leafpad, or...) to OpenOffice.

This seems to be an AMD64-related problem.

You can read the thread here:

[http://ubuntuforums.org/showthread.php?t=87021](http://ubuntuforums.org/showthread.php?t=87021)

Are you 64-bit-guys experiencing the same trouble? I am.

---

### Post by jianren on 2005-11-25
:)

---

### Post by Kuolio on 2005-11-25
I am experiencing this problem :|

---

### Post by skylark on 2005-11-25
I have the same problem. Copying and pasting from gedit, gvim, gnome-terminal etc doesn't work. I found copying and pasting from firefox works though.

---

### Post by baRRacuda on 2005-11-25
Try installing klipper :
```
 sudo apt-get install klipper
```
and run it by typing
```
klipper
```

and try again. Klipper is a clipboard manager (for KDE) and works fine for me (i use Gnome).

---

### Post by etitor on 2005-11-25
[QUOTE=baRRacuda]Try installing klipper :[/QUOTE]
Did this. Thanks barracuda but it makes no difference at all to me. By the way it installs nearly all KDE just to not achieve anything, so, at least for me, this is a no-no.

Much plainer sailing just leaving OO and using AbiWord and Gnumeric.

---

### Post by aruckert on 2005-11-28
Hi!

I'm having the same problem with OO in [ Breezy AMD64 OOo 2.0 (version 1.9.129) & gedit 2.12.1 ].

I can copy paste from OO to any application but not to OO.

I believe this might have something to do with the 32 and 64 bit libraries coexisting? I think OO hasn't been ported to AMD64, has it?

Can anybody confirm or deny this theory?
Any ideas for a work around?

Thanks...

---

### Post by grsing on 2005-11-28
I've got a related problem; I can copy and paste text from the body of a web page, but I can't copy and paste from the URL bar to OO (except by dragging the highlighted URL from firefox to OO, which is a PITA).  I also can't copy and paste from gedit to OO at all.  Normal copy and paste works from Evolution to OO just fine, though (including URLs).

---

### Post by jvictor on 2005-11-29
Yes I'm a AMD 64 user, and have found this problem, Has this bug been logged ?

---

### Post by etitor on 2005-11-29
[QUOTE=jvictor]Yes I'm a AMD 64 user, and have found this problem, Has this bug been logged ?[/QUOTE]
Not by me, anyway. Could you explain how to log a bug?

---

### Post by Wille on 2006-01-21
I have this bug too (on my AMD64 breezy).

This is ridiculous.

When Dapper comes out I will definitely install the 32-bit version.

---

### Post by gil-galad on 2006-01-23
One of the reasons that I use abiword.  Nice and fast, and 64bit too!

---

### Post by Lothlómendil on 2006-01-29
I hate to bump this, but I wanted to add that I too cannot paste into Open Office and I run the 64 bit version of Breezy, a brand new install. Does anyone know of a fix for this yet, or is it still being researched / reported? Thanks. :)

---

### Post by fabs0028 on 2006-01-29
I didn't take the test but i think it would be the same for me and i think i know the reason :

OOo is a 32bits application for now even in amd64 version of ubuntu because it doesn't compile in 64bits for now ... i think the support was planned for the 2.0.2 version so it should be available for dapper ( well i hope it will) ... you can take a look at the package and see that it depends on ia32libs and things like that.

---

### Post by John Jason Jordan on 2006-01-29
[QUOTE=jvictor]Yes I'm a AMD 64 user, and have found this problem, Has this bug been logged ?[/QUOTE]
But I think the problem is somewhere deeper inside OO.o. I have the same problem on my Breezy AMD-64 laptop with OO.o 1.9 as everyone else is reporting. Previously when I had Hoary-64 and OO.o 1.15 the problem was the same. But I also have similar copy/paste problems when using OO.o 2.0 on my Windows 2000 desktop. Sometimes it can't see what I have copied to the clipboard from another application (although there are fewer "problem apps" than on the Linux version). More commonly copy/paste in OO.o 2.0 on Windows gets "stuck." It will just continue to paste something that I overwrote with a copy command, sometimes even a copy command from within OO.o. It doesn't realize the contents of the clipboard have changed so all I can get is the old stuff. By the way, if anyone else encounters this, the fix is to copy just a space to the clipboard from within OO.o and paste it back in, then delete it from the document. That "unsticks" OO.o and it will work properly again ... for a while at least, until it gets stuck again.

So I think there is something in the way OO.o handles copy/paste that is not kosher and is causing all these problems. But I know nothing of programming, so I don't know any more about what is going on.

---

### Post by ruudiculus on 2006-01-29
I saw that a BUG report was made, so that's GOOD!

I've tried some applications and the result is this:
**(Copy) Paste Works**
[LIST=1]
[*]Firefox
[*]aMSN
[*]GIMP (partially)
[*]Evolution Mail
[/LIST]

**(Copy) Paste doesn't work:**
[LIST=1]
[*]Console (not even the middle mouse button! :-D )
[*]Synaptic
[/LIST]

This works (or doesn't) no matter in which order you Copy Paste from the applications! So, there doesn't seem to be a causal link...

---

### Post by BLTicklemonster on 2006-01-29
The only problem I've had copy and pasting was at first. I'd try to copy and paste something, and found that if I didn't leave the original open, I'd lose what I was trying to paste. Since then, for some reason, I don't have any problems. Not sure that that's about, but I commented on it a long time ago in another thread. I'd assumed they'd quietly fixed it and it was in an upgrade I'd gotten.

---

### Post by Mez on 2006-01-29
[QUOTE=jvictor]Has this bug been logged ?[/QUOTE]

[https://launchpad.net/distros/ubuntu/+source/openoffice.org2/+bug/6091](https://launchpad.net/distros/ubuntu/+source/openoffice.org2/+bug/6091)

---

### Post by gunksta on 2006-02-01
OpenOffice.org has NOT been ported to 64bit yet.  This is sad but true.  In fact, it's the only open source application (that I want anyway) that this is true for.

I REALLY want them to hurry up with getting OOo up and running in the 64 bit environment.  Cut and paste doesn't work, and integration into KDE sucks.  It works for GTK, but QT uses compiled themes and it messes up the desktop integration.

The 32bit v. 64 bit is also why cut and paste don't work.  Another problem is the horrific paging my computer does when switching from several windows of OOo to any 64bit app.

Oh well.  Once they get this done, 64bit linux will be nearly 100% for me.  Until then, I'll just bitch.

--andy

---

### Post by caustin on 2006-02-24
I have a workaround. 

1. get 64bit JDK from java.sun.com, install it

2. remove ctrl+v from OOO Tools->customize->keyboard

3 run the notepad demo, using the java you installed
 /usr/java/jdk1.5/bin/java -jar /usr/java/jdk1.5/demo/jfc/Notepad/Notepad.jar

You can then do a shift-ctrl-c ->shift ctrl v to copy to the Java notepad
Using select text/ copy in the notepad and then ctrl v in openoffice to paste it

---

### Post by snake1130 on 2006-02-26
[QUOTE=baRRacuda]Try installing klipper :
```
 sudo apt-get install klipper
```
and run it by typing
```
klipper
```

and try again. Klipper is a clipboard manager (for KDE) and works fine for me (i use Gnome).[/QUOTE]

This fix worked great for myn!

---

### Post by vertigo23 on 2006-03-17
I think rather than put up with a workaround, I'll go with what a previous poster suggested and just switch to Abiword.  OO.o is kinda clunky anyway. :rolleyes:

---

### Post by John Jason Jordan on 2006-03-17
[QUOTE=vertigo23]I think rather than put up with a workaround, I'll go with what a previous poster suggested and just switch to Abiword.  OO.o is kinda clunky anyway. :rolleyes:[/QUOTE]
AbiWord is nice, but lacking in a lot of features that I totally must have.

I tried Klipper, and it was great -- solved the copy/paste problem very nicely -- but it caused constant lockups in OO.o Writer when I had the Drawing toolbar open and was using it to create primitives (lines, triangles, ellipses) in my text. I suspect whatever the problem is has been fixed in OO.o 2.02, but being a lowly no-count AMD-64 user I don't ever get to have the latest thing.

---

### Post by Robsteranium on 2007-11-20
I've experience this problem when pasting from Firefox 2.0.0.8 to Open Office 2.2.0-1ubuntu5 on  Xubuntu Feisty Fawn.  In contrast to what has been said above I'm running on 32-bit architecture.  Perhaps this problem isn't limited to 64-bit/ older-than-latest versions.

It looks like an OO problem.  With FF text in the clipboard, OO has inactive paste buttons and menu options (greyed-out).  Ctrl-V pastes the text with what must be tags at each end.  Clearly the paste-text-only action is what I'm after.

This behaviour varies according to the source being copied - particularly between headings/ body text (again suggesting tags are to blame).

Since I'm using XFCE I'm not certain whether klipper will help.  There appear to be a few alternatives (glipper, gnustep) to investigate.  Any advice before I start pulling-apart my desktop environment?!

---

### Post by John Jason Jordan on 2007-11-20
> **Robsteranium said:**
> I've experience this problem when pasting from Firefox 2.0.0.8 to Open Office 2.2.0-1ubuntu5 on  Xubuntu Feisty Fawn.  In contrast to what has been said above I'm running on 32-bit architecture.  Perhaps this problem isn't limited to 64-bit/ older-than-latest versions.

It looks like an OO problem.  With FF text in the clipboard, OO has inactive paste buttons and menu options (greyed-out).  Ctrl-V pastes the text with what must be tags at each end.  Clearly the paste-text-only action is what I'm after.

This behaviour varies according to the source being copied - particularly between headings/ body text (again suggesting tags are to blame).

Since I'm using XFCE I'm not certain whether klipper will help.  There appear to be a few alternatives (glipper, gnustep) to investigate.  Any advice before I start pulling-apart my desktop environment?!
This situation has improved with every new version of OOo and every new version of Ubuntu. I now have OOo 2.3 on Gutsy x86_64 and have little problem with copy and paste to and from OOo.

Having said that, a lot of people who are new to Linux are unaware that there are two clipboards in Linux. In the old, original Linux clipboard you copy text just by selecting it, and you paste it with the middle mouse button. There is now (and has been for several years) a new Windows-style clipboard that works by ctrl-c, ctrl-x and ctrl-v, the same as in Windows. Some apps will use only the old native Linux clipboard (e.g., a terminal window), some will use only the new Windows-style clipboard (e.g., OOo), and some will use both. 

When copying and pasting from Firefox into OOo I have found that paste special works better because a plain paste (ctrl-v) inserts html tags. With paste special a dialog box pops up where you can choose how you want the text pasted. I usually choose "unformatted," which pastes the text in so it takes the formatting of the surrounding text.

---

### Post by Robsteranium on 2008-01-07
> **Robsteranium said:**
> 
Since I'm using XFCE I'm not certain whether klipper will help.  There appear to be a few alternatives (glipper, gnustep) to investigate.  Any advice before I start pulling-apart my desktop environment?!

I'm cautious of speaking too soon but it would appear that installing the **xfce4-clipman-plugin** has solved my problem and I'm now able to copy and paste ("Windows style") from FF to OO!

---

