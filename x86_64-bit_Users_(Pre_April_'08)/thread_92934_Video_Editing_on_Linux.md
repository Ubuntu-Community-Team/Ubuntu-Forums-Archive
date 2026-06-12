---
title: "Video Editing on Linux"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jessecurry on 2005-11-20
I was wondering what everyone's impressions on video editing under linux were, specifically with the PPC architecture. Where exactly is the "bleeding edge" right now? 
Is it worth even attempting to do lightweight video editing or should I just stick with OS X and iMovie?
What about on the professional front? I doubt that anything can compete with packages like Final Cut, but is there something that comes close? Is there anything out there for adding titling and post effects?

---

### Post by Rxke on 2005-11-21
This may seem a bit weird, but for questions like these, I often refer to... Ask Slashdot!

Why? Huuge userbase, often good comments in the Ask Slashdot section, as long as the questions are geeky enough..

[http://ask.slashdot.org/article.pl?sid=99/08/21/007229&tid=129&tid=4](http://ask.slashdot.org/article.pl?sid=99/08/21/007229&tid=129&tid=4)
[http://ask.slashdot.org/article.pl?sid=00/03/17/0033254&tid=129&tid=4](http://ask.slashdot.org/article.pl?sid=00/03/17/0033254&tid=129&tid=4)

---

### Post by Entity on 2005-11-21
I personally never used iMovie and not really Mac OS X either... but kino works perfectly for me... on my 17" Powerbook G4.

sudo apt-get install kino

---

### Post by pizzach on 2005-11-21
Meh.  It all depends on what you are trying to do.  I wanted to try to do some dubbing and have little luck with it.  As of present, I don't there there are any especially easy ways to overlay audiotracks (I could be wrong.)

I was going to do my recording in audacity and edit in cinerella but I couldn't get the mic and speakers to work at the same time.  It's nice being able to hear what's going on as you record.

---

### Post by poptones on 2005-11-21
How do you want to overlay audio? Just replace it? Mix it?

Audacity can handle that just fine and it's made for audio editing. Cinelerra also can do this pretty easily, it's just a matter of learning to drive cinelerra. 

Believe it or not I've done some pretty sophisticated video editing using mplayer. This isn't likely to work on a mac since it relies on the windows codecs to interface with files.

---

### Post by dresnu on 2005-11-21
for video editing you can also check out KMenc15 ([http://kmenc15.sourceforge.net](http://kmenc15.sourceforge.net))

---

### Post by ssam on 2005-11-21
the ones to watch are
[pitivi]("http://www.pitivi.org/")
and
[diva]("http://www.mdk.org.pl/")
but they are not ready yet.

i tried to install Cinelerra from source in the summer but did not get very far.

kino might be ok, it works in a similar way to imovie. but i have not found anything to work like final cut (yet).

---

### Post by anders_gud on 2006-03-22
[QUOTE=ssam]the ones to watch are
[pitivi]("http://www.pitivi.org/")
and
[diva]("http://www.mdk.org.pl/")
but they are not ready yet.

i tried to install Cinelerra from source in the summer but did not get very far.

kino might be ok, it works in a similar way to imovie. but i have not found anything to work like final cut (yet).[/QUOTE]

Pitivi and Diva relies to much on gstreamer-libdv (slow) to be usable on PPC.
Cinelerra is buggy as hell, and AFAIK there are no .debs for breezy due to unmet dependencies (and also endian issues)...
Kino is better but has a bug that makes transitions go bad...

[QUOTE=jessecurry]I was wondering what everyone's impressions on video editing under linux were, specifically with the PPC architecture. Where exactly is the "bleeding edge" right now?... 
What about on the professional front? I doubt that anything can compete with packages like Final Cut, but is there something that comes close? Is there anything out there for adding titling and post effects?[/QUOTE]

Blender comes pretty close ( [http://www.blender.org](http://www.blender.org) ). Recent builds include FFMPEG support that enables NLE Video/Audio. 

Features:
Import all formats that FFMPEG supports.
Output mpeg, avi, dv (PAL or NTSC), frames tif, jpeg and more... (floats exr, cineon)
Frameserver output for mpeg encoding vith other software.
Edit Video/Audio in almost unlimited number of tracks.
Transitions and custom effects.
Color correction plugins.
Video Effect plugins. 
3D compositing with animations or text.
Camera Motion tracking.
And a lot more...


Workflow:
Grab DV with dvgrab or kino.
Edit movie with Blenders Sequence Editor and render/encode to DV, mpeg or quicktime output... 
Use DVDStyler to burn DVD

Tutorials on Sequence Editor
[http://download.blender.org/documentation/htmlI/ch25.html](http://download.blender.org/documentation/htmlI/ch25.html)
[http://www.blenderwars.com/tut.php?module=blendersaber](http://www.blenderwars.com/tut.php?module=blendersaber)

Some of the Plugins:
[http://www-users.cs.umn.edu/~mein/blender/plugins/](http://www-users.cs.umn.edu/~mein/blender/plugins/)
[http://www.warpax.com/pytsai/index.html](http://www.warpax.com/pytsai/index.html)

Recent Blender 2.41 FFMPEG Build for Breezy PPC:
[http://www.gudmundson.se/anders/uploads/blender_2.41-1ubuntu1.2_powerpc.deb](http://www.gudmundson.se/anders/uploads/blender_2.41-1ubuntu1.2_powerpc.deb)

More on FFMPEG support in Blender:
[http://peter.schlaile.de/blender/sequencer/index.html](http://peter.schlaile.de/blender/sequencer/index.html)

Movie being made with blender:
[http://orange.blender.org/](http://orange.blender.org/)

---

### Post by radopenev on 2007-04-02
Hi for all!
Has anyone got any idea how from  avi ( like AVI Jpeg ),can to remove some
color!?I mean to say that ,I render by Blender avi files,but time to time want
to mix.For the this moment I render "over avi file" like alpha(render sequence  PNG or Targa ) and everything
is OK.But if avi has rendered yet(?)......this is mean new rendering!(for me )
I think that ,this is compositing metod "bluescreen".
So,more clear words...is there any VideoEditor (filter or plugin) to remove
 specified (definite) color from existing avi file ?!:( 

Sorry for my English!:( 
Best regards!

---

### Post by komputes on 2007-11-30
Has anyone been able to set up a professional HD video editing system on Ubuntu or Ubuntu Studio. If so I would like to know what hardware/software configuration you are using and how it is working out for you.

-k :roll:

---

### Post by crjackson on 2007-11-30
> **jessecurry said:**
> I was wondering what everyone's impressions on video editing under linux were, specifically with the PPC architecture. Where exactly is the "bleeding edge" right now? 
Is it worth even attempting to do lightweight video editing or should I just stick with OS X and iMovie?
What about on the professional front? I doubt that anything can compete with packages like Final Cut, but is there something that comes close? Is there anything out there for adding titling and post effects?

VE is one of the things I still use windows for.  I love Vegas - I've found nothing in Linux that compares so far.  I haven't tried Blender yet though...

---

### Post by Scunizi on 2007-11-30
Nobody has mentioned Lives.  Check it out at [http://lives.sourceforge.net/](http://lives.sourceforge.net/).  It has a fairly decent write up in one of the monthly Linux mags and although new it's progressing rapidly.  It sounds like it is approaching what you might be looking for.  Debs for Ubuntu can be found at [www.getdeb.net](www.getdeb.net)

---

### Post by crjackson on 2007-12-01
> **Scunizi said:**
> Nobody has mentioned Lives.  Check it out at [http://lives.sourceforge.net/](http://lives.sourceforge.net/).  It has a fairly decent write up in one of the monthly Linux mags and although new it's progressing rapidly.  It sounds like it is approaching what you might be looking for.  Debs for Ubuntu can be found at [www.getdeb.net](www.getdeb.net)

I have checked it out and it looks promising but it's a far cry from professional tools.  I'm not knocking it, it's just not nearly as powerful as what I'm accustomed to.  Blender looks like it MAY be a heavy hitter.  I'll check it out in a couple of weeks when I have time.

---

