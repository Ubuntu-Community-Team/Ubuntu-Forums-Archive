---
title: "Wine application ... stucked"
date: 2012-07-15
forum: Wine
---

### Post by czgirb on 2012-07-15
Today, I wish to do a cutting **AVI** with **FormatFactory **(running through Wine).
But before thr cutting process begin, ubuntu reported there is an **ERROR** to the program, and required to be closed. After it was closed, my **AVI** files starting **without any Media Player played on**.
How can it be stopped?
[B]Thank you.

PS:[/B]
Is there any video/audio edit software (as **FormatFactory**) for ubuntu?
Cos I wish to abandoned Wine ... It caused a lot of trouble.

---

### Post by tea for one on 2012-07-15
Good afternoon

Here is a link for video editors:-

[http://linuxappfinder.com/multimedia/videoeditors](http://linuxappfinder.com/multimedia/videoeditors)

Here is another link for audio editors

[http://linuxappfinder.com/multimedia/audioeditors](http://linuxappfinder.com/multimedia/audioeditors)

I do not do any video editing so I can't offer a recommendation, however for audio, I would suggest Audacity.

---

### Post by llamabr on 2012-07-15
Large programs will often not run correctly through wine, since wine is an acronym for 'doesn't work very well'.  Whatever you think you should do in wine, there is almost always a better, native solution.

Luckily, you're using one of the most powerful operating systems ever designed, and there are many audio and video editing tools available to you:

```
brock@vader:~$ apt-cache search video editor
avidemux - A free video editor (GTK version)
avidemux-cli - A free video editor (command line version)
avidemux-common - A free video editor (Internationalization files)
avidemux-plugins - A free video editor (plugins)
avidemux-qt - A free video editor (QT version)
bombono-dvd - DVD authoring program with nice and clean GUI
kdenlive - a non-linear video editor
kdenlive-data - a non-linear video editor (data files)
kdenlive-dbg - a non-linear video editor (debugging symbols)
libmlt++-dev - MLT multimedia framework C++ wrapper (development)
libmlt++3 - MLT multimedia framework C++ wrapper (runtime)
libmlt-data - multimedia framework (data)
libmlt-dev - multimedia framework (development)
libmlt3 - multimedia framework (runtime)
melt - command line media player and video editor
python-mlt3 - multimedia framework (python bindings)
freej-dbg - realtime video mixer and linear video editor
freej-doc - realtime video mixer and linear video editor
freej - realtime video mixer and linear video editor
libfreej-dev - realtime video mixer and linear video editor
libfreej0-dbg - realtime video mixer and linear video editor
libfreej0 - realtime video mixer and linear video editor
python-freej-dbg - realtime video mixer and linear video editor
python-freej - realtime video mixer and linear video editor
frei0r-plugins-dev - minimalistic plugin API for video effects, header files
frei0r-plugins-doc - minimalistic plugin API for video effects, API documentation
frei0r-plugins - minimalistic plugin API for video effects, plugins collection
gaupol - subtitle editor for text-based subtitle files
gstreamer0.10-gnonlin-dbg - non-linear editing module for GStreamer
gstreamer0.10-gnonlin-doc - GStreamer documentation for the non-linear editing module
gstreamer0.10-gnonlin - non-linear editing module for GStreamer
gopchop - Fast, lossless cuts-only editor for MPEG2 video files
kino - Non-linear editor for Digital Video data
longomatch - video analysis tool for coaches
gnome-core - The GNOME Desktop Environment -- essential components
libmlt-dbg - multimedia framework (debugging symbols)
libmlt2 - multimedia framework (runtime)
python-mlt2 - multimedia framework (python bindings)
openmovieeditor - a simple non-linear video editor
openshot-doc - Help manual for OpenShot Video Editor
openshot - Create and edit videos and movies
pitivi - non-linear audio/video editor using GStreamer
subtitlecomposer - Subtitles editor for KDE
subtitleeditor - Graphical subtitle editor with sound waves representation
videolink - assembles a DVD video filesystem from HTML pages and video files

```

---

### Post by Mark Phelps on 2012-07-16
You didn't which version you're trying to use, but if you look at the WineHQ page below, you'll see that if it's version 1.x, you're wasting your time:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8318]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=8318")

---

### Post by czgirb on 2012-07-17
> **Mark Phelps said:**
> You didn't which version you're trying to use, but if you look at the WineHQ page below, you'll see that if it's version 1.x, you're wasting your time:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8318](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8318)

**WineHQ** that I used is version **1.4**
**Format Factory** that I used is **2.70** and **2.95**.
I don't mean to say that WineHQ + Format Factory is a GARBAGE.
But, for my lappie ... it is was.
I don't know where the problem is.
**Maybe it was caused by my Ubuntu** or **maybe it was caused by my Wine**.
Cos **the Format Factory runs smoothly in Vista**.

---

### Post by flurospar on 2012-07-18
Wine cannot run all Windows applications well. Since you are converting media files, it may be better to use a tool like ffmpeg.

These tools are command line, but once you know all the basic methods to run them it is not much of a problem (and even gives greater flexibility than tools like Format factory).

The basic way to convert in ffmpeg is to type the following in the terminal:
```

ffmpeg -i /path/to/movie/movie.mp4 movie.flv

```/path/to/movie/movie.mp4 = wherever your media file is stored
movie.flv = name of output file

However, do note that ffmpeg selects low qualities for output, so you may have to adjust bitrate, resolution etc. by adding additional parameters.

---

### Post by oldos2er on 2012-07-18
Moved to Wine.

---

### Post by thatguruguy on 2012-07-18
> **czgirb said:**
> 
Is there any video/audio edit software (as **FormatFactory**) for ubuntu?

Try WinFF. It's available in the Ubuntu Software Center. It's pretty straightforward and easy to use.

> **czgirb said:**
> 
**Maybe it was caused by my Ubuntu** or **maybe it was caused by my Wine**.
Cos **the Format Factory runs smoothly in Vista**.
That sounds like it's probably a Layer 8 problem.

However, WinFF should help. Seriously. Try it. I use it almost every day.

---

