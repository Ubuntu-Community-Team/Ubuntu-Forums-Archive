---
title: "Onenote 2007 in wine"
date: 2008-04-03
forum: Wine
---

### Post by Kinst on 2008-04-03
With these guides we can install Onenote 2007 in wine:

[LIST]
[*][http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html](guide)
[*][http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html](guide)
[/LIST]

[COLOR="SeaGreen"]What works:[/COLOR]
[LIST]
[*]All typing and multicoloured text notes
[/LIST]
[COLOR="Red"]What doesn't work:[/COLOR]
[LIST]
[*]Onenote 2007 crashes when opening any file with **drawings**
[*]When trying to use the drawing tool, Onenote says [COLOR="DarkOrchid"]*"OneNote requires Microsoft Windows Tablet PC Edition 2005 with Service Pack 2 in order for inking functions to work properly. You can install Service Pack 2 from the Windows product pages on the Microsoft Web site."*[/COLOR]
[/LIST]

The Onenote devs say that in windows this is a bug related to [COLOR="DarkOrange"]inkobj.dll[/COLOR]. You can fix it in windows by typing "regsvr32 inkobj.dll" in a terminal.
[LIST]
[*][http://blogs.msdn.com/descapa/archive/2007/02/05/onenote-requires-tablet-pc-edition-2005-with-service-pack-2-what-is-that.aspx](http://blogs.msdn.com/descapa/archive/2007/02/05/onenote-requires-tablet-pc-edition-2005-with-service-pack-2-what-is-that.aspx)
[/LIST]

I've tried everything I can think of with [COLOR="DarkOrange"]inkobj.dll[/COLOR] - trying to register it in konsole (it just says it worked but nothing changes), taking an inkobj.dll from my windows partition, and using winecfg to make it native.

Is anyone else interested in getting Onenote drawing to work? :(

---

### Post by obocho on 2008-04-03
go on!!! 

if you can figure out how this application works, you will get hundreds of thanks from many users. : ))

---

### Post by Kinst on 2008-04-04
Progress!

[LIST]
[*]I copied over gdiplus.dll from my office 2003 installation and made it native. Then I made inkobj.dll native
[*]Onenote can *[COLOR="Olive"]view drawings without crashing[/COLOR]*
[*]The line and arrow commands work now
[*]The annoying service pack popup disappeared
[*]The drawing tool just goes grey and doesn't work.
[/LIST]

Hm...

---

### Post by Kinst on 2008-04-26
Okay so everything works except the ink tool.

Here's what I'm stuck on:

```
fixme:advapi:RegisterTraceGuidsW 0x2394a8a 0x239fb60 0x23917fc 1 0x33e89c (null) (null) 0x239fb68
fixme:atl:AtlModuleInit SEMI-STUB (0x49b97000 0x49b97ae8 0x49a90000)
fixme:win:EnumDisplayDevicesW ((null),0,0x33e664,0x00000000), stub!
fixme:dciman:DCICreatePrimary 0xd9e8 0x26f128c
err:ole:ifproxy_get_public_ref IRemUnknown_RemAddRef returned with 0x800706c2, hrref = 0x00000000
err:ole:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800706c2
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a5b020fd-e04b-4e67-b65a-e7deed25b2cf} could be created for context 0x17

```

---

### Post by obocho on 2008-04-30
come on buddy, I believe in you : ) 
if you can solve this issue, you will be my hero... 
[actually so far you are one of my heros : )]

---

### Post by breity on 2008-06-19
has anyone made any progress with getting ink to work with onenote 2007?  i've had no luck, unfortunately.

pretty much everything else seems to work great.  getting my tablet's pen to work with onenote in wine would pretty much stop me from having to run windows in a virtual machine. (i may still need to to use various adobe products, but it would greatly cut down on how often i need to boot it!)

it's amazing how fast office 2007 runs in wine for me!

---

### Post by Kinst on 2008-06-19
Yeah...I sort of gave up. :(

This is as far as I got:

[LIST]
[*]Put a copy of MSVP60.DLL and GDIPLUS.DLL in your fake windows/system32 folder.
[*]Make sure GDIPLUS.DLL is set to native
[/LIST]

Then drawings display properly but you can't draw yourself.

---

### Post by tC_Crazy on 2008-11-17
Hate to bring back a dinosaur thread here, but this is the only info I could find on getting drawings to work in OneNote. I tried downloading inkobj.dll and gdiplus.dll from the web but have had no luck getting ink/drawings to show up. The program no longer crashes when I try to view pages with ink in them, but the ink simply doesn't show up (blank). If I could view onenote pages in ubuntu, I could actually do productive work here instead of having to boot into Windows any time I want to do some work or take a peek at my notes. 

I do have Vista installed on another partition, and could probably grab some DLLs from another XP machine if needed.

---

### Post by Kinst on 2008-11-17
Sure dude. 

The secret is the MSVCP60.dll and GDIPLUS.dll. You need both.

Let me know if that helps.

---

### Post by tC_Crazy on 2008-11-21
I have copied msvcp60.dll to the sys32 wine directory from my vista partition, and grabbed a copy of gdiplus.dll from dllfiles.com, with no success. I am going home for Thanksgiving today, so I will try some DLLs from my XP desktop. I have set inkobj, gdiplus, and msvcp60 to native, with the same results (containers, but no ink). Interesting thing is, when you highlight some of the blank space, you can see the outline of lines written (like stacked boxes, if you know what I mean) but the ink just isn't there. Drawing tools also crash onenote.

---

### Post by Kinst on 2008-11-21
This is my setup if it helps:
[IMG]http://i13.photobucket.com/albums/a251/Kinst/onenote.png[/IMG]

---

### Post by tC_Crazy on 2008-12-26
I really can't figure out what's wrong. I have Wine set up identically (although I had msvcp60.dll also set native...tried it both ways). I'm using Wine version 1.1.10. Is that what you have, as well? I'm running Intrepid, everything updated... Maybe I'll remove wine and try a more recent version direct from winehq...

---

### Post by jordancolburn on 2009-06-25
Got screen clipping, drawing, and ink viewing working thanks to your instructions.  

I've been looking for other ways to get the inking working though, and stumbled across a way to trick windows into thinking you have tablet PC edition when you don't:

[http://www.wincert.net/forum/lofiversion/index.php?t4277.html](http://www.wincert.net/forum/lofiversion/index.php?t4277.html)

Most of the downloads have to be done on a verified windows PC.

I've been playing around with it, still no luck, but those of you who actually know what you're doing might have some new options to look at.

---

### Post by philcamlin on 2009-06-25
cool:popcorn:

---

### Post by NightMKoder on 2009-06-25
It won't work. If you look at the windows tablet pc architecture, you will notice wine is missing a critical component - wisptis.exe (Windows Ink Services Platform Tablet Input Subsystem). This is the exe that receives input from raw tablet devices and converts it into thinks inkobj can recognize.

You can install this exe and register it - and it even starts - but it simply won't work. The methods of communication are not the same and there is no way wine could tap into the "raw" input that wisptis needs.

Until someone in wine cares to implement this service (no easy task), using your tablet with onenote is impossible.

---

### Post by Kinst on 2009-09-09
> **jordancolburn said:**
> Got screen clipping, drawing, and ink viewing working thanks to your instructions.  

On which version of wine? I lost all my stuff and now I can't even get this working on new wine versions.

---

### Post by spotdog14 on 2009-09-09
> **Kinst said:**
> On which version of wine? I lost all my stuff and now I can't even get this working on new wine versions.
I agree, I have tried several different versions of Wine and I cannot even create a new section without it crashing.

---

### Post by murderslastcrow on 2009-09-10
I think it's great that it even works- this used to be a gamestopper for one of my buddies. You could draw the notes in GIMP and import them as an image, correct? Little bit of an overzealous solution, but it seems that it'll be a year or two before the Tablet PC architecture gets here, anyway.

I'd call this a success story for now.

---

### Post by GOZES on 2010-05-05
ok so i install onenote but it crash's wen i try to to open a new section in a notebook, anybody knows why and  how to fix it tnx

---

### Post by Doomicle on 2010-06-25
Wow it works!
For those of you who weren't paying attention to kinsts' post, just add the following dlls as native/builtin in your wine config libraries tab:
gdiplus
msxml3
riched20
riched32
rpcrt

Shabam! Works for me running the lastest wine build on OpenSUSE 11.2.
There is an error message whenever I close one note, but no biggie I guess. Does make me wonder what other bugs are in store for me if I were to actually use it for a while.

---

### Post by tgalati4 on 2010-06-26
I like zim.

sudo apt-get install zim

---

### Post by Doomicle on 2010-06-26
tgalati4, You can add it to the list here: 
[http://alternativeto.net/desktop/microsoft-onenote/?sort=likes&platform=linux](http://alternativeto.net/desktop/microsoft-onenote/?sort=likes&platform=linux)

Or mabe you'll find something else you like there.

---

### Post by libertao on 2010-06-26
> **Doomicle said:**
> 
There is an error message whenever I close one note, but no biggie I guess. Does make me wonder what other bugs are in store for me if I were to actually use it for a while.

Same here, makes me a bit nervous about trusting it with all my valuable notes...

Oh and thanks for the summary!

---

### Post by wedge2k on 2010-09-25
I'm getting the inkobj.dll problem, where it says you must have windows xp tablet edition.  Did anyone find a solid fix for this?  I really wanna use my pen.

---

### Post by Kinst on 2010-12-13
> **libertao said:**
> Same here, makes me a bit nervous about trusting it with all my valuable notes...

Oh and thanks for the summary!

Eh, I've been using this method for years now to access and make a few edits to my notes from within linux. My notes are stored on my windows partition which is what I normally use to draw. I never did find out if it's possible to draw new notes within wine...I'm guessing not, though I haven't tried new wine versions in a long time.

---

### Post by alaukikyo on 2010-12-14
HAve you tried nevernote or some free alternatives([http://alternativeto.net/software/microsoft-onenote/?sort=likes&platform=linux&license=free](http://alternativeto.net/software/microsoft-onenote/?sort=likes&platform=linux&license=free))

---

### Post by matejdro on 2011-09-12
Sory for reviving old thread, but

Any news on this one or maybe even OneNote 2010?

It seems like OneNote It's the only program that supports in-line drawing and easy changeable pages from the main window.

I have managed to get OneNote working, but drawing will just throw tablet pc error like someone before me posted.

---

### Post by atulkakrana on 2012-08-01
> **matejdro said:**
> Sory for reviving old thread, but

Any news on this one or maybe even OneNote 2010?

It seems like OneNote It's the only program that supports in-line drawing and easy changeable pages from the main window.

I have managed to get OneNote working, but drawing will just throw tablet pc error like someone before me posted.


How did you got onenote 2010 working, for me it crashes if I try to open a section and also when I close onenote. Please tell me what did you do to make it work?

---

### Post by matejdro on 2012-08-02
I did not. I was using 2007.

---

