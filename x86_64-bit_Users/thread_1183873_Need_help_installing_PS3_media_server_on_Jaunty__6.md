---
title: "Need help installing PS3 media server on Jaunty _64"
date: 2009-06-10
forum: x86 64-bit Users
---

### Post by Man x on 2009-06-10
I'm a total noob been playing with Linux for 3 years but never got deep til now I need help installing PS3 media server :(

---

### Post by mickie.kext on 2009-06-10
> **Man x said:**
> I'm a total noob been playing with Linux for 3 years but never got deep til now I need help installing PS3 media server :(

Man, you need to be more specific ;) You given no information... I can't even gues what is the problem.

---

### Post by kiu888 on 2009-06-11
I am trying to do the same thing.
64 bit Server
installing PS3 Media Server

I got pretty good success. (not 100% though)
can't transcode some mkv files
the everything else is good.

most of the info I got here
[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=1508]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=1508") and
[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=302]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=302")

but here is the quick low down.
I hope I am not forgetting anything else I tried.
to tell you the truth I don't even know if all this is needed.

but this is what I did from a fresh Ubuntu 9.04 server install

```

sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts
sudo apt-get install mplayer
sudo apt-get install mencoder
sudo apt-get install ffmpeg

```

create a location and download the PS3 Media server and goto that location.

```

sudo wget http://ps3mediaserver.googlecode.com/files/pms-linux-1.10.5.tgz

tar -xvzf pms-linux-1.10.5.tgz

```

then run it using sudo nohup ./PMS.sh &

that will leave it running in the backgroud.

as for the PMS.conf file
refer to this.
[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=254]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=254")

I think I still have options I need to set or other things I need updated so that the mkvs work....
the windows version was easy... the linux version... not so much.

---

### Post by ethoxyethaan on 2009-06-11
building ffmpeg from source could help solve with decoding those mkv files.

make sure you have libx264 installed

---

### Post by darksoul7 on 2009-06-20
My PS3 sees the media server, but says all the files are "Not Supported". 

I a bit confused. I'm pretty sure I have everything installed correctly.

---

### Post by chrisbloe on 2009-07-04
I got a PS3 today and was looking at how to do this. I found this website and it was up and running in under 5 min... very quick, very simple and no mess :)

[http://arkold.com/602-super-mega-fast-way-to-setup-a-media-server-on-ubuntu-jaunty](http://arkold.com/602-super-mega-fast-way-to-setup-a-media-server-on-ubuntu-jaunty)

---

### Post by karlakoala on 2009-09-18
> **kiu888 said:**
> I am trying to do the same thing.
64 bit Server
installing PS3 Media Server

I got pretty good success. (not 100% though)
can't transcode some mkv files
the everything else is good.

most of the info I got here
[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=1508](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=1508) and
[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=302](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=302)

but here is the quick low down.
I hope I am not forgetting anything else I tried.
to tell you the truth I don't even know if all this is needed.

but this is what I did from a fresh Ubuntu 9.04 server install

```

sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts
sudo apt-get install mplayer
sudo apt-get install mencoder
sudo apt-get install ffmpeg

```create a location and download the PS3 Media server and goto that location.

```

sudo wget http://ps3mediaserver.googlecode.com/files/pms-linux-1.10.5.tgz

tar -xvzf pms-linux-1.10.5.tgz

```then run it using sudo nohup ./PMS.sh &

that will leave it running in the backgroud.

as for the PMS.conf file
refer to this.
[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=254](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=254)

I think I still have options I need to set or other things I need updated so that the mkvs work....
the windows version was easy... the linux version... not so much.

Following these instructions I'm good up until here - then run it using sudo nohup ./PMS.sh &

Please somebody help me, I can only find very vague instructions on how to get this going & I need it to be more like step by step for a noob - please somebody help me, I can't stand that it all just worked with vista but can't get it to work on ubuntu

---

### Post by deviant on 2009-09-22
Or you can try to use this little app called PMS. 
It`s written in Java, so you will need to also have that installed. 
Other than that, it works out of the box. I`ve been using it with my PS3 to stream x264 videos to my TV for quite some time. 
Give it a try: [http://ps3mediaserver.blogspot.com/](http://ps3mediaserver.blogspot.com/)

Cheers!

---

### Post by dream_coder on 2009-09-24
Try Mediatomb, get the latest development source, I have used it for ages now without any problem, if you need any more info just post it and I will talk you through it.

---

