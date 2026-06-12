---
title: "HOWTO install RealPlayer10 in kubuntu? [amd64 version]"
date: 2006-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by eskimokid on 2006-10-22
I got alot media oso in rmvb files and as I know, alot player cannot read rmvb codecs
so i need realplayer for it
i tried to install realplayer 32bit in my kubuntu amd64 
it work...with sounds only
it cant load the video
so when i play a rmvb media thru the realplayer, its blank but with sounds [my explaination is not really good but hope you guys know what i m saying]

I tried to use automatix2 to install realplayer also
but the result is same

so what can I do to play my rmvb format videos ?

---

### Post by kuja on 2006-10-22
Will it play in mplayer, xine (with libxine-extracodecs), or vlc? Have you given those a try?

---

### Post by eskimokid on 2006-10-22
I tried to play it in mplayer and i did installed the libxine-extracodecs
but what is vlc ?
is it work for playing rmvb files ?

---

### Post by kuja on 2006-10-22
I really don't know if it does or not, but at this point, it's probably worth a try.

```
sudo apt-get install vlc
```

>  VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added
 by installing additional audio plugins (vlc-plugin-esd, vlc-plugin-sdl,
 vlc-plugin-arts) or video plugins (vlc-plugin-sdl, vlc-plugin-ggi,
 vlc-plugin-glide, vlc-plugin-svgalib). There is also a web browser plugin
 in the mozilla-plugin-vlc package.


---

### Post by eskimokid on 2006-10-22
The result is same....
having sounds but don't have video come out
:(

---

### Post by fabertawe on 2006-10-22
Hi eskimokid...

I'd never heard of this file format so I did a quick search and found [this music video clip]("http://www.lillevold.com/files/aac_samples/video_he-aac.rmvb") which plays fine here (video and sound). I'd already installed RealPlayer from [their Linux page]("http://www.real.com/linux"). There is only the one version and it just installs with no fuss (as I recall, possibly vaguely!). I'm on the amd64-k8 kernel.

Paul

---

### Post by eskimokid on 2006-10-22
Hi fabertawe...

Can you please show me how do you install your realplayer ?
I think the problem is I installed real player with a wrong way
I did tried to search in the net but I cant configure it out and I juz install by running the bin file and it install into my /home directory.
Since this way is not working

i install by using automatix2

but the result is the rmvb files juz can play sounds but not the video with sounds 
:(

---

### Post by fabertawe on 2006-10-23
> **eskimokid said:**
> Hi fabertawe...

Can you please show me how do you install your realplayer ?
I think the problem is I installed real player with a wrong way
I did tried to search in the net but I cant configure it out and I juz install by running the bin file and it install into my /home directory.
Since this way is not working

i install by using automatix2

but the result is the rmvb files juz can play sounds but not the video with sounds 
:(

I installed as per the instructions from their download page...

> **Installation Instructions**

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

If you know where it was installed by Automatix then you should try removing that first. I think you can just delete the directory.

Paul

---

### Post by eskimokid on 2006-10-24
I did this way too.
I should put that file into which directory ? 
Is it all directory also available ?

---

### Post by fabertawe on 2006-10-24
> **eskimokid said:**
> I did this way too.
I should put that file into which directory ? 
Is it all directory also available ?

I'm not sure I understand you, sorry... if you mean the 'RealPlayer10GOLD.bin' file then it does not matter where you run/install it from. You can just delete it when you're finished installing anyway.

Paul

---

### Post by eskimokid on 2006-10-24
haha sorry for confusing you with my broken english.... 
what I meant is after extracting from the bin file...
from the terminal...I have been asked to locate my realplayer file after extracting that binary file...so which directory I should put into ?

---

### Post by kuja on 2006-10-24
If you mean what prefix you should install it under, install it under /usr

---

### Post by eskimokid on 2006-10-24
Oh well...
sorry but I'm noob in kubuntu...
installed kubuntu less then 2 days..
how to install it into /usr
when the terminal ask me where would i like to put the RealPlayer file i type /usr and the terminal appear Permission Denied...

---

### Post by kuja on 2006-10-24
Yeah, you need to run it with root privileges. When you run the script, run it with sudo. For more information on why you need to use sudo, and how to use it, view this page of the ubuntu wiki - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

### Post by eskimokid on 2006-10-24
O, ok
thanks for that link
it's what newbie [Me] needed !
thanks !

---

### Post by fabertawe on 2006-10-24
> **eskimokid said:**
> haha sorry for confusing you with my broken english.... 
what I meant is after extracting from the bin file...
from the terminal...I have been asked to locate my realplayer file after extracting that binary file...so which directory I should put into ?

Ah, ok... well what kuja said is fine, presumably you've sorted it out now? I put mine in '/opt' but it really doesn't matter :) 

Paul

---

### Post by spetea on 2006-11-30
> **fabertawe said:**
> I installed as per the instructions from their download page...



If you know where it was installed by Automatix then you should try removing that first. I think you can just delete the directory.

Paul

' ./realplay-10.0.8.805-linux-2.2-libc6-gcc32-i586.bin 
bash: ./realplay-10.0.8.805-linux-2.2-libc6-gcc32-i586.bin: No such file or directory'

so that's my problem. I do not know what the problem is but i really want my ubuntu can make me feel good to watch my films.

Is anyone here can help me out?

---

### Post by mural on 2007-01-24
Hi, 

I am trying to install RealPlayer on my AMD64 Edgy, but I am not able to.

This is what I get:

murali@Edgy-murali:~/Desktop$ sudo ./RealPlayer10GOLD.bin 
Password:
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory


Here is the output of ls -l:
murali@Edgy-murali:~/Desktop$ ls -l
total 6936
-rwxrwxrwx 1 murali murali 5802563 2007-01-22 19:37 RealPlayer10GOLD.bin

Can some one help me with this?

---

