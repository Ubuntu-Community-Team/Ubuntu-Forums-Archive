---
title: "Codec problems"
date: 2008-02-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by madsporkmurderer on 2008-02-29
I can't get audio or video playback on my new 64-bit machine (core 2 duo).

I have tried using the add/remove system to install things but couldn't get extra xine plugins to install (I'm guessing that this is what I need) as it says it is not availible on 64 bit.

I have also tried adding the medibuntu repository and installing various things from there- still no luck.

Thanks,
Mike

---

### Post by Kilz on 2008-02-29
> **madsporkmurderer said:**
> I can't get audio or video playback on my new 64-bit machine (core 2 duo).

I have tried using the add/remove system to install things but couldn't get extra xine plugins to install (I'm guessing that this is what I need) as it says it is not availible on 64 bit.

I have also tried adding the medibuntu repository and installing various things from there- still no luck.

Thanks,
Mike

I have 2 suggestions. 
1. [Use Synaptic ]("http://www.monkeyblog.org/ubuntu/installing/#installing_with_synaptic")to install software. It is like add/remove advanced.
2. Install and try vlc or mplayer to play media.

---

### Post by John.Michael.Kane on 2008-02-29
> **madsporkmurderer said:**
> I can't get audio or video playback on my new 64-bit machine (core 2 duo).

I have tried using the add/remove system to install things but couldn't get extra xine plugins to install (I'm guessing that this is what I need) as it says it is not availible on 64 bit.

I have also tried adding the medibuntu repository and installing various things from there- still no luck.

Thanks,
Mike

You can give these steps a try, if you like.

DVD Playback:
1) Run the below command.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Followed by.
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

2) Installing the codecs for dvd playback and your choice of movie player. 
```
sudo aptitude install libavifile-0.7c2 gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly libdvdcss2
```

W64codecs some users feel this should not be needed,however. Users who feel they need/want W64 can install it like so.
```
sudo aptitude install w64codecs
```

3) Choosing a movie player. Below are some of the more common ones used, and the way they should be installed, and how to set them up if needed.

Player one: Totem-xine this player usually only requires the end user to install it, and it's dependencies. Under most cases it requires no further set-up after installing is needed. To install use the command below.
Code:

```
sudo aptitude install totem-xine libxine1-ffmpeg
```

Player two: Mplayer this is one of the players users swear by,however.It does require a bit of set-up on the users part after installing,Which will be explained. (Note Depending on the video/dvd being played you may have to adjust for subtitle playback.) Install using the below command
```
sudo aptitude install mplayer
```

After installing mplayer you will be required to set it's default video. To do so open mplayer by typing the command below

```
gmplayer
```

Next:
1) Right click on the mplayer, and select preferences
2) Under video tick enable direct rendering (note you might not need double buffering you will have to test this on your particular hardware)

3) Should you have playback issues you can try, and change available drivers from xv to x11.

Player three: Vlc another player that users seem to hold in high regards for playing movies. (Note from my testing it would appear this player is another one that only requires the users to install it. Depending on the video/dvd being played you may have to adjust for subtitle playback.)
```
sudo aptitude install vlc
```

Regarding browser video playback plugin's.

For users wanting to use mozilla-mplayer there is a bit of set-up involve with it.
First start by un-installing totem-mozilla. Next install the below package.
Code:

```
sudo aptitude install mozilla-mplayer
```

Plugin set-up.
1) Try playing the video.
2) As the video is attempting to play right click on the box that will have the video.
3) Select configure.
4) Where it says video output change to x11. (note this might not be needed)
5) Adjust the cache to 2092 or more if you like.
6) Change percent of media to cache to 50.
7) You should now have browser playback.

(Next is vlc mozilla pulgin  this player should only require the user to install it. no setup was needed.)
```
sudo aptitude install mozilla-plugin-vlc
```

---

### Post by coskierken on 2008-03-01
Here is a link.  Use it for a quick setup for codecs you need for totem-xine.  You will see it has many very usefull functions.  

[http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart](http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart)

---

### Post by madsporkmurderer on 2008-03-04
I had followed some of those guides but it seems I'd missed the installation of libxine1-ffmpeg. All working now- thanks guys

---

