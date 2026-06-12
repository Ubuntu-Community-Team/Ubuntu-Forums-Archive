---
title: "I'm *that* close to playing DVD movies"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-02-14
I have been trying for months to get Ubuntu-64 to play commercial DVD movies, first Hoary and then Breezy after I upgraded. I almost have it. Right now, if I put a movie DVD in the drive I can get sound with gxine. With Totem, mplayer and vlc I can't get them even to see the DVD drive.

OK, fine. Who needs Totem, mplayer and vlc? As long as something works, I don't care. But there are still problems. For a while I got gxine to play at least the audio on a commercial movie DVD. In an effort to get the video to work as well, I poked around a bit. And as a result, right now, when I launch gxine, it immediately closes. Obviously I poked at something I shouldn't have. (I think it was something about "enabling video.")

Using a Linux trick I learned a while back, I launched gxine from the command line. Thus, when it fell over, I had an error message:

The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 110 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I know zero about programming. Does anyone know what this means? Is it hopeless? This is a pretty fast computer so I doubt it is the CPU. But maybe it is the DVD drive speed? Or something else?

---

### Post by anirban.sam on 2006-02-14
install libdvdcss

---

### Post by jon_gunnar on 2006-02-14
[QUOTE=John Jason Jordan]I have been trying for months to get Ubuntu-64 to play commercial DVD movies, first Hoary and then Breezy after I upgraded. I almost have it. Right now, if I put a movie DVD in the drive I can get sound with gxine. With Totem, mplayer and vlc I can't get them even to see the DVD drive.

OK, fine. Who needs Totem, mplayer and vlc? As long as something works, I don't care. But there are still problems. For a while I got gxine to play at least the audio on a commercial movie DVD. In an effort to get the video to work as well, I poked around a bit. And as a result, right now, when I launch gxine, it immediately closes. Obviously I poked at something I shouldn't have. (I think it was something about "enabling video.")

Using a Linux trick I learned a while back, I launched gxine from the command line. Thus, when it fell over, I had an error message:

The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 110 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I know zero about programming. Does anyone know what this means? Is it hopeless? This is a pretty fast computer so I doubt it is the CPU. But maybe it is the DVD drive speed? Or something else?[/QUOTE]
You may need the libdvdcss as stated.Got the option of running 

sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by John Jason Jordan on 2006-02-14
[QUOTE=jon_gunnar]You may need the libdvdcss as stated.Got the option of running 

sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh[/QUOTE]
I think I already ran that before. But I did it again. It ran with no errors, but no change. Gxine still launches and immediately disappears. Launching it from the command line I get the same error message as before (posted above).

From the error message it sounds like there is a bug in my display driver. It's a Compaq R3240 15.4" widescreen Nvidia chipset running at 1600 x 1080. Ubuntu auto-detected it and set the display up when I first installed it. It's gorgeous and I haven't touched it. I've never had display problems with any other programs.

Any other suggestions?

---

### Post by John Jason Jordan on 2006-02-15
[QUOTE=jon_gunnar]You may need the libdvdcss as stated.[/QUOTE]
I just realized you said libdvdcss. I have libdvdcss2 installed, but not libdvdcss. And libdvdcss is not listed in Synaptic. I did run the script, but it didn't make any difference. Things are still as I said in my original post. 

Are libdvdcss and libdvdcss2 different? Do I need libdvdcss? If so, how do I install it, since it is not listed in Synaptic?

---

### Post by Randomskk on 2006-02-15
Try installing ogle via apt-get, and there is an ogle GUI as well (ogle-gui), get them both...
It plays DVDs fine for me, where all else fails.

---

### Post by John Jason Jordan on 2006-02-15
[QUOTE=Randomskk]Try installing ogle via apt-get, and there is an ogle GUI as well (ogle-gui), get them both...
It plays DVDs fine for me, where all else fails.[/QUOTE]
Thanks for the suggestion. I already had ogle installed, so I tried it. Flashed up on the screen and instantly disappeared. Next I installed the ogle-gui. Afterwards it launches and stays up. But when I told it Open Disk it quickly disappeared again. Finally, I tried launching it from the command line. Again, it came up and appeared fine. But when I told it to Open Disk it disappeared again, and the command line gave me the following:
```
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Using libdvdcss version 1.2.5 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000146
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000004d2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000542
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00000558
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00026a20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0003a3ca
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003691ea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0036a046
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0036a060
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c811c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003c8e56
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 1
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  44
  Current serial number in output stream:  44
```
So it still won't work. The error messages appear similar to what I got from gxine in my original post.

Anyone have any further suggestions? Bug in the video driver? Video incompatibility?

---

### Post by RAOF on 2006-02-15
I've seen that error before.  First of all, try changing the video output mode - it looks like it's currently set to "xv".  Try any of the others.  Do they work?

Failing that, there was someone who had a similar problem, and it was caused by the graphics drivers.  What graphics card/driver setup do you have?

---

### Post by AllenGG on 2006-02-15
Hi JJJ, went through the same problems.  Did install "libdvdcss2" from VLC but it's now available in several places,_ but I think you've got it._
But I have : Totm-Xine - lib. [COLOR=Red]not Gstreamer[/COLOR] , which I could never get to work.
And , with some difficulty I did install the current NVidia drivers.
Plus I had to make _some changes to the set-up_, to eliminate the frame jumps.
Now, it's much better to watch movies this way than a DVD player and TV.
I did searches through these forums and got what I needed, except for using 
"Totem-Xine".
Allen

---

### Post by John Jason Jordan on 2006-02-16
[QUOTE=RAOF]I've seen that error before.  First of all, try changing the video output mode - it looks like it's currently set to "xv".  Try any of the others.  Do they work?

Failing that, there was someone who had a similar problem, and it was caused by the graphics drivers.  What graphics card/driver setup do you have?[/QUOTE]
With gxine it comes up and disappears immediately. No chance to see what it is set to or to change it. I also have totem-gxine, which acts exactly the same way. Previoulsy I had totem-gstreamer, which would at least stay on the deskop. it just refused to see the DVD drive. And I have vlc and ogle-gui. I have already commented above on the error messages that ogle generates when running from the command line. And vlc cannot see the DVD drive either. The closest I have come is with Totem-gxine, which at least played the movie, although all I got was video. And after poking at it ("enable vido button I think) now it just appears and immediately disappears.

I really think it is a video driver problem. This is an Nvidia chipset and it is running at 1680 x 1050. I don't know what driver it is -- Ubuntu found it and auto-configured it on installation. I haven't touched it because I love it just the way it is. I'm too new to Linux to know where these things are kept. I wonder where I can find out what driver I have?

---

### Post by trigg on 2006-02-16
[QUOTE=John Jason Jordan]
I really think it is a video driver problem. This is an Nvidia chipset and it is running at 1680 x 1050. I don't know what driver it is -- Ubuntu found it and auto-configured it on installation. I haven't touched it because I love it just the way it is. I'm too new to Linux to know where these things are kept. I wonder where I can find out what driver I have?[/QUOTE]

First off, make sure you have the right drivers installed:

1. Open Synaptic (menu option System | Administration | Synaptic Package Manager)
2. Do a search for "restricted"
3. ensure that "linux-restricted-modules-2.6.12-10-(whatever your architecture is)"
is installed.
4. If it wasn't installed - install it and reboot.  If it was installed, just exit.
5. Continue with the folllowing steps:

Check in this file: /etc/X11/xorg.conf

Just open up a terminal window: (Applications | Accessories | Terminal)

type 
```

sudo gedit /etc/X11/xorg.conf

```

Find the section that says 

```

Section "Device"
             Identifier           "NVIDIA . . ." (it will actually have your video card here)
             Driver               "nv"
             BusID                "PCI:1:0:0" (or something else)
EndSection

```

change the 
```

              Driver               "nv"

```

to 
```

              Driver              "nvidia"

```

save the file.
close gedit.
exit the terminal.
save any unsaved work. 
close any other programs
hit the following key-sequence: CTRL+ALT+BACKSPACE

this should restart your X-server.  
Log back in and see if you can watch DVDs. 
:)

If for some reason your X session doesn't resume, follow these steps:

Hit the key sequence: CTRL+ALT+F1

login as your regular user

edit your xorg.conf as follows and restart X:
(first ensure that you have nano installed)

```

sudo apt-get install nano
sudo nano -w /etc/X11/xorg.conf

```

scroll down and change "nvidia" back to "nv"

hit CTRL+X, then y, then ENTER

then type this at the command prompt:
```

sudo /etc/init.d/gdm restart

```

then you'll be back where you started.

---

### Post by John Jason Jordan on 2006-02-16
[QUOTE=trigg]First off, make sure you have the right drivers installed:

1. Open Synaptic (menu option System | Administration | Synaptic Package Manager)
2. Do a search for "restricted"
3. ensure that "linux-restricted-modules-2.6.12-10-(whatever your architecture is)"
is installed.
4. If it wasn't installed - install it and reboot.  If it was installed, just exit.[/QUOTE]
Whoa!

1) After searching on "restricted" I do not find 2.6.12-10-anything. Closest I can get is 2.6.12-9.

2) This is an AMD-64 CPU, but exactly which one I don't know. So I don't know which architecture to choose.

3) In order to get ndiswrapper going I had to install one of these things. I can't remember fro sure which one it was, although I think it was "generic-something." But if installing a new module has even the slightest chance of screwing up ndiswrapper, I'm outta here. I totally need wifi, and it took me almost two weeks to get it working the first time. That was under Hoary. And when I upgraded to Breezy it broke ndiswrapper and it took me nearly a week to get it fixed again. Without wifi this computer is useless to me. And we're in the last half of winter term and I don't have a week or two to struggle with fixing something.

I got this computer and put Linux on it in order to learn it and get away from Windows, but I'm still too new to Linux. Stuff like this scares me. I can do without playing movies on my computer, but I can't risk breaking ndiswrapper. :(

---

### Post by RAOF on 2006-02-16
Ah, you're using the nv driver!  I've found it to have all sorts of quirks (on recent nvidia cards, at least).  You may well have better luck with the binary nvidia driver.  Never fear!  This shouldn't break anything :)

The long road to getting it working is the "nvidia driver" link in my sig.  The quick, and easy path is:
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
Then restart.  You'll be using the binary drivers, and you can check whether that's the problem you're having with video.

---

### Post by John Jason Jordan on 2006-02-16
[QUOTE=RAOF]Ah, you're using the nv driver!  I've found it to have all sorts of quirks (on recent nvidia cards, at least).  You may well have better luck with the binary nvidia driver.  Never fear!  This shouldn't break anything :)

The long road to getting it working is the "nvidia driver" link in my sig.  The quick, and easy path is:
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
Then restart.  You'll be using the binary drivers, and you can check whether that's the problem you're having with video.[/QUOTE]
OMIGOD! It's WORKING!

I have to say, dude, I had great trepidation. But you seemed so sure it would work that I decided to take the plunge. The two command lines above did the job! I am sitting here watching I Robot as I write this.

OK, gxine still won't work, although it stopped disappearing. It gets to 18% buffering and just stops. But Totem is working great (totem-gxine, that is). I'll try the others later. For now I'm just thrilled I finally have something that will play movies!

Oh, and the screen seems more responsive, faster redraw. 

This is too cool. A thousand thanks!

---

### Post by trigg on 2006-02-16
[QUOTE=RAOF]Ah, you're using the nv driver!  I've found it to have all sorts of quirks (on recent nvidia cards, at least).  You may well have better luck with the binary nvidia driver.  Never fear!  This shouldn't break anything :)

The long road to getting it working is the "nvidia driver" link in my sig.  The quick, and easy path is:
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
Then restart.  You'll be using the binary drivers, and you can check whether that's the problem you're having with video.[/QUOTE]

oh yeah, I suppose that would be a lot easier . . .  ;) 

But then you don't get forced to look into the xorg.conf file!

---

### Post by silveronetrx on 2007-07-04
I am having this exact same problem; however, I am using an onboard intel video card that is in my laptop. Can anyone help me out with this?

---

### Post by jrizzy on 2007-07-17
> **silveronetrx said:**
> I am having this exact same problem; however, I am using an onboard intel video card that is in my laptop. Can anyone help me out with this?

did you ever find a solution to this problem?? i am having the exact same thing!! drivin me nutso and i cant find a solution for the onboard intel driver set.  This is what I have:

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

---

### Post by John.Michael.Kane on 2007-07-17
> **jrizzy said:**
> did you ever find a solution to this problem?? i am having the exact same thing!! drivin me nutso and i cant find a solution for the onboard intel driver set.  This is what I have:

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

What exactly is the problem?

If your trying to play dvd's you need to install the codecs. which are listed at the bottom of this this thread [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

