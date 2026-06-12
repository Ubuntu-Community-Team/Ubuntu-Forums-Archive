---
title: "xine and codecs"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by splint on 2006-03-02
hey all,

I'm trying to install a media player & codecs, I am quite new to linux I tried mplayer on fedora, I see theres a player called xine and would like to use it on ubuntu, I also need codecs to play back avi's (xvid, divx etc). Any1 able to point in the right direction? I went to xine homepage but I dont see any 64 bit packages. Can i dl the source  and compile using make? I think i have some of the files installed i went to package manager and installed libxine1c2 and libxine-dev. So all I need now is the ui? I also tried apt-get install xine-ui but I get the following error:

Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate


Any help would be appreciated :)

edit: ok I got the tar file and compiled it. Player loads and I see video but I dont think I have audio codec installed :(

---

### Post by RAOF on 2006-03-03
The package you want is totem-xine (Totem is the player; it uses the xine-backend).

Totem is (in my opinion) the nicest of the video players in Ubuntu.  There's also mplayer in the repositories, and the gui for xine is "gxine", I believe.

You could search Synaptic for "xine" - you should find "gxine" (or something like it) and the descritption should say that it's a xine frontend.

Searching Synaptic is a **really** good idea ;)

---

### Post by splint on 2006-03-03
Video playback works however I am still not able to hear any audio, the error I get is;

the stream"filename" use an unsupported codec: Audio Codec mpeg layer 2/3

How do I install that codec?!

---

### Post by spydirweb on 2006-03-06
the problem is the codecs you want are 32 bit based.  Basicly, the codec is able to spit out the video but cannot process the audio...  To explain somewhat indepth, read on...  Basicly though, if you're just looking for the answer...  Install VLC.  It is in the Synaptic system, just search for "vlc."  Install the program vlc.  my system also has "gnome-vlc" showing up but I'm not 100% sure if it's needed, I just know it is on mine...

In depth review of this "problem" :

On a 32 bit install of any linux distro to play almost any type of video/audio file there's a general package available called "win32codecs."  This is a collection of "dll" files that are modified from the windows versions to work under linux.

The problem is these codecs are 32-bit based.  On a fully 64-bit based system these codecs will not work "point blank."

There are currently a number of workarounds available in different distros.  In Gentoo 64-bit, there is a version of mplayer which is compiled for 64-bit systems using 32-bit emulators.  It runs quite well, but must be installed somewhat...strangely.

The problem I've noticed since switching to Ubuntu 64 bit is that there is no available package from the get-go like this.

I've done some hunting but haven't turn up much in terms of what to do directly.  If all you're trying to do is play videos and audio in a stand alone program, I HIGHLY recommend VLC (videoLAN client).  It has it's own set of codecs it uses to play damned near anything you can throw at it, I've yet to see a problem.

If you're looking for a plugin for mozilla/firefox/whatever else, the best I can say is wait.  There is a VLC plugin for firefox but...it's crap.  I'm waiting it out to see what the developers do until I finally crack down and try to come up with my own fix.

---

