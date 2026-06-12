---
title: "Ubuntu Server AMD64 avi to h264???"
date: 2007-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by bonka on 2007-11-10
Anyone know how to encode avi files (xvid) to h264 using Ubuntu Server AMD64???

---

### Post by RAOF on 2007-11-10
The ffmpeg or x264 packages are your friends.  ffmpeg will decode virtually any file you throw at it, and x264 is a good h264 encoder.

---

### Post by ian dobson on 2007-11-10
Hi,

Maybe handbreak would do it for you:- [http://handbrake.m0k.org/](http://handbrake.m0k.org/)

Regards
Ian Dobson

---

### Post by John.Michael.Kane on 2007-11-10
Hereis few ways to convert files using ffmpeg. I have not tested the below methods fully. note: you will have to edit the commands to fit the project.

For reference:
```
ffmpeg [[infile options][-i infile]]… {[outfile options] 
```

To convert from MPG to 3GP
```
ffmpeg -i yourfile.mpg -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -ab 32 -y yourfile.3gp
```

To convert from AVI to 3GP
```
ffmpeg -i yourfile.avi-s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y yourfile.3gp
```

To convert from 3GP to AVI
```
ffmpeg -i yourfile.3gp -f avi -vcodec xvid -acodec mp3 -ar 22050 yourfile.avi
```

Heres another example line.
```
mencoder input.avi -o output.avi -ovc x264 -x264encopts bitrate=3000 pass=1 nr=2000
```

Hope it helps.

---

### Post by bonka on 2007-11-10
okay, cool

have tried installing the packages for mencoder, mplayer and ffmpeg

but they all say that it can't be found,

Am I doing something wrong (sudo apt-get install [program]) or is it that packages aren't available for the 64 bit system and might have to install the 32 bit ones?

---

### Post by John.Michael.Kane on 2007-11-10
> **bonka said:**
> okay, cool

have tried installing the packages for mencoder, mplayer and ffmpeg

but they all say that it can't be found,

Am I doing something wrong (sudo apt-get install [program]) or is it that packages aren't available for the 64 bit system and might have to install the 32 bit ones?

No mplayer/mencoder is in the repos. make sure have them all enable in the sources.list file. 

You may also need the files listed below.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Followed by.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

The run the command below.

```
sudo aptitude install mplayer mencoder libdvdcss2 libavifile-0.7c2 libxine1-ffmpeg x264 ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly
```

This should get you started. hope it helps.

---

### Post by bonka on 2007-11-10
works great, thanks to all you people

---

### Post by John.Michael.Kane on 2007-11-10
> **bonka said:**
> works great, thanks to all you people

No problem. gald it worked out, if there should be any other issues just post, and i'm sure one the forum members will try to assist you.

---

