---
title: "Creating a dvd for dvd player"
date: 2006-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mike71 on 2006-09-19
Hi,

I use Ubuntu 6.06 and I am looking for a software that allows me to burn (encoded) movies to dvd for playback in an external dvd player. 
I tried just burning a data dvd with the movie files but that did not work

Can you point me in the right direction?

---

### Post by Pinoy915 on 2006-09-19
I used the this howto. I didn't use tovid though, just the script for DVDauthor. [http://www.ubuntuforums.org/showthread.php?t=183936&highlight=creating+dvd]("http://www.ubuntuforums.org/showthread.php?t=183936&highlight=creating+dvd")

---

### Post by fabertawe on 2006-09-20
[ManDVD]("http://www.kde-apps.org/content/show.php?content=38347&vote=good&tan=73191165&PHPSESSID=b0fc4ec8303fb395575ca2deffdf9558") looks promising. Install 'linux32' first and run it with```
linux32 mandvd
```It reminds me of the DVD authoring part of the Nero suite on Windows (I forget the name).

As a quick test I created an ISO containing two AVIs with a menu and it played perfectly in my DVD player after burning.

Paul

---

### Post by Mike71 on 2006-09-22
mjpegtools semms to be needed for both approaches but I can't seem to be able to find the package

---

### Post by fabertawe on 2006-09-23
> **Mike71 said:**
> mjpegtools semms to be needed for both approaches but I can't seem to be able to find the package

I have 'mjpegtools' and 'libmjpegtools0c2a' installed in Synaptic. Do you have all the repos enabled? (Synaptic: Settings -> Repositories). 

Paul

---

### Post by gerowen on 2006-10-29
If you get ManDVD from sourceforge you don't have to install anything.  There are two files, the executable and the icon, and it runs fine for me.  I've got it archived on my fileserver, you can [download the tarball from me here.](http://147.133.214.88:8001/Software/Linux/mandvd-2.1.3.tar.gz)  Just extract it and double click the file named ManDVD and it should take right off, did for me.  The only downside, I speak English, and even if you select English as your language, a lot of the tips and sidenotes are still in Dutch/German.

---

### Post by Zone17 on 2006-10-29
I installed 'mjpegtools' and 'libmjpegtools0c2a' and still can't get it to work.

Here is the output.

--> Lancement de la génération du menu ------------------------------------------------------------
1920+0 records in
1920+0 records out
7680 bytes (7.7 kB) copied
, 0.003313 seconds, 2.3 MB/s
Assuming raw pcm input file

LAME: Can't get "TERM" environment string.
LAME version 3.96.1 ([http://lame.sourceforge.net/](http://lame.sourceforge.net/))
CPU features: 
MMX (ASM used)
, SSE
, SSE2

Using polyphase lowpass filter, transition band: 17226 Hz - 17806 Hz
Encoding /dev/stdin to silent.mpa
Encoding as 48 kHz 128 kbps j-stereo MPEG-1 Layer III (12x) qval=3

    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
     0/       ( 0%)|    0:00/     :  |    0:00/     :  |         x|     :  

     0/2      ( 0%)|    0:00/    0:00|    0:00/    0:00|   0.0000x|    0:00 

     1/2      (50%)|    0:00/    0:00|    0:00/    0:00|   2.4000x|    0:00 

average: 128.0 kbps                    MS: 4 (100.0%)

/home/zone/DVD//menu.sh: line 6: jpegtopnm: command not found
   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  25:1
   INFO: [ppmtoy4m]     pixel aspect ratio:  59:54
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  top-field-first (interleaved PPM input)
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  1, or until input exhausted
   INFO: [ppmtoy4m]     chroma subsampling:  4:2:0 MPEG-2 (horiz. cositing)
**ERROR: [ppmtoy4m] Failed to read first frame.
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: system error (failed read/write)!
   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
**ERROR: [mplex] Unable to open file genmenu.m2v for reading.
DVDAuthor::spumux, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
STAT: 
0:00:00.000

INFO: Picture survolee.png had 2 colors
INFO: Picture cliquee.png had 2 colors
INFO: Constructing blank img
INFO: Pickbuttongroups, success with 1 groups, useimg=1
WARN:  Read 0, expected 4
INFO: 0 subtitles added, 0 subtitles skipped, stream: 32, offset: -0.00

Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 0 bytes.

---

### Post by starNIX on 2006-12-16
Same problem here.  Any ideas?

/home/bpregont/Desktop/scrubs1//menu.sh: line 6: jpegtopnm: command not found
/home/bpregont/Desktop/scrubs1//menu.sh: line 6: pnmscale: command not found
   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  30000:1001
   INFO: [ppmtoy4m]     pixel aspect ratio:  10:11
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  top-field-first (interleaved PPM input)
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  1, or until input exhausted
   INFO: [ppmtoy4m]     chroma subsampling:  4:2:0 MPEG-2 (horiz. cositing)
**ERROR: [ppmtoy4m] Failed to read first frame.
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: system error (failed read/write)!
   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
**ERROR: [mplex] Unable to open file genmenu.m2v for reading.
/home/bpregont/Desktop/scrubs1//menu.sh: line 7: spumux: command not found

---

### Post by girionis on 2006-12-16
I am using this

[http://www.linux.com/article.pl?sid=06/04/17/2058219](http://www.linux.com/article.pl?sid=06/04/17/2058219)

and so far it si working greatly.

---

