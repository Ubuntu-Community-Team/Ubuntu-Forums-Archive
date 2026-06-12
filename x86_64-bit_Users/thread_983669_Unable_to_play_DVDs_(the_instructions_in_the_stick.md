---
title: "Unable to play DVDs (the instructions in the sticky don't work)"
date: 2008-11-15
forum: x86 64-bit Users
---

### Post by Th3Professor on 2008-11-15
Hello... I have Ubuntu Studio 64-bit installed, and did the following (as per the message (sticky) in this x86 64-bit Users forum category)...

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add - && sudo apt-get update
sudo aptitude install libavifile-0.7c2 gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg x264 libdvdcss2
sudo aptitude install w64codecs
sudo aptitude install totem-xine libxine1-ffmpeg
When I put in the DVD to play, it auto-plays the initial video (prior to main/top menu) and moves on to the main/top menu. I click on the menu to play, it starts to play though is interrupted with the following:

"An error occurred: Failed to connect stream: OK"

Any ideas? Thanks! :)

---

### Post by OUPablo on 2008-11-21
I'm having the same problem with 8.10 64-bit. Here is the output from Totem if I try to play a movie.

```
(totem-xine:8684): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
** (totem-xine:8684): DEBUG: Init of Python module
** (totem-xine:8684): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem-xine:8684): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem-xine:8684): DEBUG: Creating Python plugin instance
** (totem-xine:8684): DEBUG: Init of Python module
** (totem-xine:8684): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem-xine:8684): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem-xine:8684): DEBUG: Creating Python plugin instance
** Message: no file info
libdvdnav: Using dvdnav version 1.1.15 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: MY_DISC
libdvdnav: DVD Serial Number: 411CDE5B
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/oupablo/.dvdnav/MY_DISC.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000011a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00021325
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00199828
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0019982c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00228ae9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00228aed
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

** (totem-xine:8684): WARNING **: Invalid borders specified for theme pixmap:
        /home/oupablo/.themes/Orange-LiNstaBlackPlastic/gtk-2.0/Range/null.png,
borders don't fit within the image
The program 'totem-xine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 64 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by phenest on 2008-11-21
I get that error but with the gstreamer version of Totem. Are you sure you're running the xine version? Totem-xine should have no problems, whereas gstreamer is still a little buggy.

---

### Post by Ellaine on 2008-11-21
Try here and install VLC player. Plays any dvd.

[http://www.stchman.com/](http://www.stchman.com/)

---

### Post by OUPablo on 2008-11-23
I ran totem-xine in the terminal to be sure I was running xine and that didn't work. I've also tried running VLC but the same thing happens. Both apps close when they try to run the movie. With Kaffeine I'm able to get sound to play but not the video. I did notice that the w32codecs come in a 13 MB file and the w64codecs are in a 600 KB file. Are there a lot of codecs missing for 64bit ubuntu?

---

