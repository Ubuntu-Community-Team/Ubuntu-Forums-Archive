---
title: "Divx problem"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mmoscosa on 2007-06-06
well, am new to ubuntu.. sort of, 

anyway just installed ubuntu 7 and the only thing i cant do so far is to reproduce divx files

I have installed libdvdcss2 and w32codecs for Ubuntu  and I have tryied with Totem, VLC and Mplaer and non of them plays my videos.

Totem says:

> Totem could not play 'file:///media/sda5/My Videos/Donnie Darko[2001]DvDrip[Eng]-Bugz/DonnieDarko.avi'.
There is no plugin to handle this movie.

what else could i do?

thx

---

### Post by ©TriMoon® on 2007-06-06
Weird because i was able to play DIVX/XVid files straight after VLC install with vlc.
Try installing some ffmpeg package(s) for gstreamer, because the default totem uses gstreamer.

---

### Post by mmoscosa on 2007-06-07
I have instaled the gstrem-ffmpeg and ffmpeg alone and nothing happens :(

any other idea?

---

### Post by Cappy on 2007-06-07
You're posting in the 64-bit forums so I assume you have a 64-bit 7.04.
For 64-bit the codec pack is "w64codecs", here is the line you need to run from Medibuntu:
```

wget -c http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/amd64/w64codecs_20061203-0medibuntu1_amd64.deb
sudo dpkg -i w64codecs_20061203-0medibuntu1_amd64.deb
```

Try right clicking on the video and clicking on the "Audio/Video" tab, Under **Video** there is a field called "Codec:". Paste back what it says there.

Is there any chance the video is simply corrupt?

---

