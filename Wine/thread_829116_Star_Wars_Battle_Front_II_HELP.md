---
title: "Star Wars Battle Front II HELP"
date: 2008-06-14
forum: Wine
---

### Post by 2words4uready on 2008-06-14
i just got wine and was wondering how to install Star Wars Battle Front II
i created the cdrom drive in wine 
heres what i did in the terminal 
the files are disc so i
1. tyler@tyler-desktop:~$ cd /media/cdrom0
2. tyler@tyler-desktop:/media/cdrom0$ wine LaunchBFII.exe
 then nothing happens i get taken back to this in the terminal
tyler@tyler-desktop:/media/cdrom0$ 
any help is appreciated 



btw N00B TO LINUX

---

### Post by 2words4uready on 2008-06-14
bump

---

### Post by 2words4uready on 2008-06-16
Bump

---

### Post by 2words4uready on 2008-06-18
bump

---

### Post by 2words4uready on 2008-06-18
bump

---

### Post by 2words4uready on 2008-06-22
> **2words4uready said:**
> bump

bump

---

### Post by the real omni on 2008-09-30
Wish I had some stunningly good news for you but unfortunately BFII doesn't do too well on Wine.

You can indeed install it - you need to open your file manager and navigate to the cd then run the setup executable instead of the launch executable.

Once it's set up, you can run it just like any other wine app.

I managed to get it working on my HP dv6500 but the problem is the same as with any windows game - linux just doesn't do a very good job with handling directx-based games.

OpenGL is still lightyears behind directx for video quality, and a game that requires directx will run about 60-80% as fast on wine as it would on windows. I'm not expert enough to explain why that is, that's just my personal observation.

I've resolved myself to keeping two machines - one for desktop use (ie, e-mail, browsing, office stuff, programming, etc) and one for media use (ie, watching downloaded movies/tv shows, listening to music, and playing games.)

The desktop machine is running Ubuntu 8.10a5 and it does all of my work-related stuff WAY better than Windows could ever dream of, and my media machine is running Windows XP/sp3 and it does all of my media-related stuff WAY better than Ubuntu currently does.

I'm not entirely sure why it is, but even downloaded xvid and x264 movies/tv eps look nicer in Windows.

The exact same movie file when played in VLC on Windows looks WAY smoother (ie, less jaggies/blockiness) than when played in VLC on Ubu.

---

### Post by Ferrat on 2008-09-30
First of DirectX is not lightyears before OpenGL in video quality, the video quality is the same and if you're refering to the latest games that has nothing to do with any quality but coding and textures with which you could produce the same results more or less in either DX3D of OpenGL.

As for media I recommend you try using mplayer and w32codecs, at least for me even tho my VLC isn't blocky often gives better results. 

OnTopic: Looks like you have to dual boot a while before it works with wine, give it 3-6month and it should be working :)

---

### Post by aoanla on 2008-09-30
> **the real omni said:**
> 
I managed to get it working on my HP dv6500 but the problem is the same as with any windows game - linux just doesn't do a very good job with handling directx-based games.

That's horribly badly worded. "Linux" doesn't do DirectX, it being a Windows-only, proprietary Graphics, Sound and I/O API. A lot of the meat of Wine makes DirectX stuff work in Linux by remapping all the DirectX calls to open APIs that Linux (and, indeed, Windows) supports.


> OpenGL is still lightyears behind directx for video quality, and a game that requires directx will run about 60-80% as fast on wine as it would on windows. I'm not expert enough to explain why that is, that's just my personal observation.

Your first statement is demonstrably false - video decoding quality (and display quality in general) is uncorrelated with the API you use - the drivers have more influence over that. It may be the case that the drivers that graphics cards companies produce are less polished for Linux than Windows - with ATI this has historically been the case, but they're getting much better in general, for example.

The slowdown with DirectX-based games in Wine is because of all that remapping that is necessary to get them to work with other APIs (OpenGL, the various sound systems that are available, etc). It does not reflect an inherent inefficiency in OpenGL, those soundsystems, linux, or even the drivers for your hardware.

> I've resolved myself to keeping two machines - one for desktop use (ie, e-mail, browsing, office stuff, programming, etc) and one for media use (ie, watching downloaded movies/tv shows, listening to music, and playing games.)

The desktop machine is running Ubuntu 8.10a5 and it does all of my work-related stuff WAY better than Windows could ever dream of, and my media machine is running Windows XP/sp3 and it does all of my media-related stuff WAY better than Ubuntu currently does.

I'm not entirely sure why it is, but even downloaded xvid and x264 movies/tv eps look nicer in Windows.

The exact same movie file when played in VLC on Windows looks WAY smoother (ie, less jaggies/blockiness) than when played in VLC on Ubu.

I've never noticed this. In fact, just yesterday, I was complaining about how video on the Windows machine we had looked much worse than on the linux boxes, and how Window Media Player never seemed to support useful video formats. Of course, I don't use VLC much - I tend to prefer Mplayer.

Clearly, your milage may vary - what graphics card do you have?

---

### Post by the real omni on 2008-09-30
Well guys, say what you will but I'm just going off my personal experience.

Every single game I've seen handled by OpenGL has looked *almost* as nice as when handled by DirectX 9. Now look at the difference between DirectX 9 and DirectX 10 and you'll see just how far behind OpenGL really is:

[http://www.winmatrix.com/forums/index.php?showtopic=9550](http://www.winmatrix.com/forums/index.php?showtopic=9550) - Here's a good example of DX 9 vs DX 10 and OpenGL doesn't even fully compare with DX9, thus doesn't even come close to DX 10.

I'm using an Nvidia 8500 GT I think. (Though I really don't think it matters that much because the two examples used on the DX9/DX10 comparison page were rendered on the same video card.)

---

### Post by asdfoo on 2008-09-30
> **the real omni said:**
> Well guys, say what you will but I'm just going off my personal experience.

Every single game I've seen handled by OpenGL has looked *almost* as nice as when handled by DirectX 9. Now look at the difference between DirectX 9 and DirectX 10 and you'll see just how far behind OpenGL really is:

[http://www.winmatrix.com/forums/index.php?showtopic=9550](http://www.winmatrix.com/forums/index.php?showtopic=9550) - Here's a good example of DX 9 vs DX 10 and OpenGL doesn't even fully compare with DX9, thus doesn't even come close to DX 10.

I'm using an Nvidia 8500 GT I think. (Though I really don't think it matters that much because the two examples used on the DX9/DX10 comparison page were rendered on the same video card.)

Apples and Oranges, that comparison doesn't prove anything.

The effects used in the DX10 picture are different to the effects used in the DX9 picture, it's not a 1:1 comparison.  It's entirely possible to achieve the same effects with OpenGL but perhaps it's more difficult for the programmer to do and that's where the superiority of DX10 is...

Hopefully we'll see in the next 6 months some improvements to OpenGL 3 which will allow graphics programmers to go above and beyond their current limitations.

As for any speed differences between Wine and Windows when it comes to DireectX, it's a very complex thing to get right... Wine has to translate DX to OGL and it has done a damn good job of it for a lot of programs but it is still a work in progress by some very talented people.

---

