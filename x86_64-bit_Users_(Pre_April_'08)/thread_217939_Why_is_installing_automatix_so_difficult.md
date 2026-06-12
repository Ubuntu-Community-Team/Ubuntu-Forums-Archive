---
title: "Why is installing automatix so difficult?"
date: 2006-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by andybhoy.1984 on 2006-07-17
Right OK, so new Ubuntu, and Linux user here.
I have fought with hard drives, and got them working (various difficulties with ownership/mounting), I have spent endless hours working out I required xmms to play MP3's.  I have messed around so much I've had to re-install, but here what i can't understand.  Why is installing automatix so difficult?

andy@andy-desktop:~$ wget [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
--02:19:40--  [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
           => `key.gpg.asc'
Resolving [www.beerorkid.com](www.beerorkid.com)... 208.97.133.175
Connecting to www.beerorkid.com|208.97.133.175|:80... gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
failed: Connection timed out.
Retrying.

--02:22:50--  [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
  (try: 2) => `key.gpg.asc'
Connecting to www.beerorkid.com|208.97.133.175|:80... failed: Connection timed out.
Retrying.

--02:26:01--  [http://www.beerorkid.com/automatix/apt/key.gpg.asc](http://www.beerorkid.com/automatix/apt/key.gpg.asc)
  (try: 3) => `key.gpg.asc'
Connecting to www.beerorkid.com|208.97.133.175|:80... connected.
HTTP request sent, awaiting response...
--02:34:00--  I got bored, and quit this

Notice, that in the first instance I just pasted in the whole "gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -" of that rubbish whatever it is, although I probably shouldnt have.  Second time, it didnt.  

As you can see, the server is either patheticly slow, or Ive made a mistake.  Also, note my terminology in this post, or the lack of it.  Hmmm, Ive sat and typed in a bunch of stuff into Terminal and I didnt even know what i was doing..  Perhaps a better explanation of what to do, and what it does would be good for us newbies then you wouldnt have so many help requests?

Another thing, I believe the whole point of automatix is to make it easier to install common applications, so I would therfor say that the thing is directed to newbies - but its a nightmare to get going!  Bit of a false positive there.

The only thing I wanted Automatix for anyways, was to install Java, which I can;t get on here for love nor money.  Ive tried editing my sources.list, and apt-get cant find it on any of the repo's, Ive downloaded no less than 3 different install packages from java.com, and followed both java.com's instructions for installation and other help files on here.  Frankly Im getting bored and fed up.

I really thought that Linux, especially Ubuntu would have given Windows a run for its money, and it does, until you go to a website that requires a browser plugin and youre lost.  Its fair enough that a bit of work is required to install a plaugin, but sometimes its late, like just now and all you want to do is get on with it.  In Windows, Java would take less than 5 minutes to install, on Ubuntu, Ive so far spent 4hours and 44 minutes trying to get into one chat-room.

Sorry for this long post, but i think these kind of commeents are required so that developers, etc, can see where thing are goign wrong, rather than people just saying "Help!  I can;t do..."

Thanks for you time!
Andy

---

### Post by AbGilley89 on 2006-07-17
Try again in a few hours the server thing is down right now.

---

### Post by Kilz on 2006-07-17
Want Java? 
```
sudo apt-get install j2re1.4
```
[Automartix can be real fun for people running the amd64 version]("http://www.ubuntuforums.org/showthread.php?t=208407").

If all you want is Firefox running with plugins check out my signature.

---

### Post by andybhoy.1984 on 2006-07-18
Thanks for that how-to!  
Got Java and Flash working now, excellent!
I'm going to try the Real Player one now, so i don;t need to rely on ogg streams!

Thanks again!

---

### Post by Titus A Duxass on 2006-07-18
You cannot honestly expect to be taken seriously.  Automatix difficult, rubbish!  Automatix and the instructions that appear on the thread could not be easier!

As it turns out it was not the fault of Automatix but the server(similar problems can happen with Windows).

If you think that was difficult then may ubuntu and other variations are not the operating system for you.

Or maybe you were just venting your spleen?

---

### Post by fatsheep on 2006-07-18
> **Titus A Duxass said:**
> You cannot honestly expect to be taken seriously.  Automatix difficult, rubbish!  Automatix and the instructions that appear on the thread could not be easier!

As it turns out it was not the fault of Automatix but the server(similar problems can happen with Windows).

If you think that was difficult then may ubuntu and other variations are not the operating system for you.

Or maybe you were just venting your spleen?

Couldn't agree more, I'm a linux newbie but I still was able to get it up and running in a snap.   Very good install instructions, even better program. :p

---

### Post by andybhoy.1984 on 2006-07-18
LMAO!
Yes, apologies...
I was venting a bit, but I will stand by my comments on being told to do things without being told what they actually do.  Its all well and good giving all these commands, but if we don't know what were typing how can we learn?

Anyways, I've tried installing Automatix again, and it just isn;t working.  Obviously a server error or whatever.  

I'm thinking it might be a better idea to format the hard Drive, and get rid of the 64bit Ubuntu, and go with the 32bit version.

If I had the 32bit version, java, and Flash would have installed with less hassel, plus I want to play OpenTTD and it's not compatible with 64bit!

---

### Post by Kilz on 2006-07-18
> **andybhoy.1984 said:**
> LMAO!
Yes, apologies...
I was venting a bit, but I will stand by my comments on being told to do things without being told what they actually do.  Its all well and good giving all these commands, but if we don't know what were typing how can we learn?

Anyways, I've tried installing Automatix again, and it just isn;t working.  Obviously a server error or whatever.  

I'm thinking it might be a better idea to format the hard Drive, and get rid of the 64bit Ubuntu, and go with the 32bit version.

If I had the 32bit version, java, and Flash would have installed with less hassel, plus I want to play OpenTTD and it's not compatible with 64bit!

First off you want to run Automatrix, but you wont run sudo apt-get because you want to learn something? Did you really think about that before posting it?
[Second, are you 100% sure that game isnt compatible with the 64bit version?]("http://www.ubuntuforums.org/attachment.php?attachmentid=12942&stc=1&d=1153261602")  :mrgreen:

---

### Post by andybhoy.1984 on 2006-07-18
LOL
Fair point.  I think i was just getting a bit fed up trying to install java, in fact it was driving me nuts, and the automatix thing looked like a good way to just get it done.  Having said that, It's installed now,a nd I have the 32bit version of Firefox and its all working, so I'm chuffed with myself!

As for the OpenTTD...

[http://www.andybhoy1984.myby.co.uk/i386.jpg](http://www.andybhoy1984.myby.co.uk/i386.jpg) ](*,) 

I had also tried simutrans, but when i was typing "make" into Terminal it was giving me errors, which i can't remember off hand...

---

### Post by andybhoy.1984 on 2006-07-18
Woohoo!
I just read the bit about 

sudo dpkg -i --force-architecture

And that seems to be getting the installer going!  
Wish I'd done that a while ago.  Still, getting places now...

---

### Post by Kilz on 2006-07-18
> **andybhoy.1984 said:**
> Woohoo!
I just read the bit about 

sudo dpkg -i --force-architecture

And that seems to be getting the installer going!  
Wish I'd done that a while ago.  Still, getting places now...

Yes thats how I installed it, force-architecture will get a lot of things installed. The graphics go in /usr/share/games/openttd/data in case you were wondering where they go. It looks like there are a few other folders in /usr/share/games/openttd for other things.

---

### Post by andybhoy.1984 on 2006-07-18
I thought it was working, LOL!

andy@andy-desktop:/usr/share/games/openttd$ openttd
openttd: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

I've went into synaptic and uninstalled all the libSDL stuff, then installed it all again, still getting this stupid message.  

I'm going to bed now before I have a mental breakdown, I'll try again in the morning! 
 
Thanks for your help so far BTW, much appreciated...

---

### Post by Kilz on 2006-07-18
> **andybhoy.1984 said:**
> I thought it was working, LOL!

andy@andy-desktop:/usr/share/games/openttd$ openttd
openttd: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

I've went into synaptic and uninstalled all the libSDL stuff, then installed it all again, still getting this stupid message.  

I'm going to bed now before I have a mental breakdown, I'll try again in the morning! 
 
Thanks for your help so far BTW, much appreciated...
The reason is that you need the 32bit version of that lib. When we force in a .deb file we need to sometimes manualy add a lib or 2.
First we need to install a piece of software to extract things from .deb files. Open a terminal and copy/paste this in.
```
sudo apt-get install dpkg-dev
```
[Next go here and download the file.]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibs%2Flibsdl1.2%2Flibsdl1.2debian-all_1.2.9-0.0ubuntu2_i386.deb&md5sum=5bbff9755c9407b8713123afd247a39e&arch=i386&type=main")and save it to your desktop.
Now right click on the deb file you just downloaded and select Extract here. In the folder it extracts will be a data.tar.gz file. Right click on it and chose Extract here. It will extract a usr folder. Drag it to the desktop to save typing. Then use this command to copy in the lib you need
```
sudo cp -r -p ~/Desktop/usr/lib/* /usr/lib32
```
The game should start after that. You can delete all the stuff we extracted.

---

### Post by andybhoy.1984 on 2006-07-19
Thanks again for the help!
I think where I'm going wrong with all of this is, I'm forgetting that I am using a 64-bit OS and trying to run 32-bit apps.  

Anyways, I got Transport Tycoon running.  

If you want to know how *not* to get it running, have a look at:
[http://www.andybhoy1984.myby.co.uk/openttd.html](http://www.andybhoy1984.myby.co.uk/openttd.html)

I basically followed your instructions, and then for every file it reported missing, I downloaded them from the Ubuntu Software packages site, and copied them all into /usr/lib32

I then got to a file that I couldnt find on the site, which was "libncurses.so.5".  After a quick look at the forums, however I figured, I needed "ia32-libs-sdl".  I already had it, looking at Synaptic, however it was obviously the 64bit one I had.  

So anyways, the 64-bit/32-bit thing has now sunk in, and I should hopefully get along a bit better with this now!

Thanks again to everyone for the help!

---

### Post by Kilz on 2006-07-19
> **andybhoy.1984 said:**
> Thanks again for the help!
I think where I'm going wrong with all of this is, I'm forgetting that I am using a 64-bit OS and trying to run 32-bit apps.  

Anyways, I got Transport Tycoon running.  

If you want to know how *not* to get it running, have a look at:
[http://www.andybhoy1984.myby.co.uk/openttd.html](http://www.andybhoy1984.myby.co.uk/openttd.html)

I basically followed your instructions, and then for every file it reported missing, I downloaded them from the Ubuntu Software packages site, and copied them all into /usr/lib32

I then got to a file that I couldnt find on the site, which was "libncurses.so.5".  After a quick look at the forums, however I figured, I needed "ia32-libs-sdl".  I already had it, looking at Synaptic, however it was obviously the 64bit one I had.  

So anyways, the 64-bit/32-bit thing has now sunk in, and I should hopefully get along a bit better with this now!

Thanks again to everyone for the help!
Helping each other is what Ubuntu is all about. :-D

---

### Post by koperry on 2006-07-19
I have not had much trouble getting automatix to run but it get's about 1/2 complete and then times out here ([http://raof.dyndns.org/falcon/](http://raof.dyndns.org/falcon/))

Any ideas? Thanks in advance

---

### Post by arnieboy on 2006-07-19
> **koperry said:**
> I have not had much trouble getting automatix to run but it get's about 1/2 complete and then times out here ([http://raof.dyndns.org/falcon/](http://raof.dyndns.org/falcon/))

Any ideas? Thanks in advance
what do u mean by: "when its about 1/2 complete". post exact errors here.

---

### Post by koperry on 2006-07-19
--12:05:32--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
           => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Resolving raof.dyndns.org... 202.63.35.99
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:08:49--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 2) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:12:00--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 3) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:15:12--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 4) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:18:25--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 5) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:21:39--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 6) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:24:54--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 7) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:28:10--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 8) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:31:28--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 9) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:34:46--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try:10) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:38:05--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try:11) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:41:24--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try:12) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80...

---

### Post by arnieboy on 2006-07-19
> **koperry said:**
> --12:05:32--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
           => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Resolving raof.dyndns.org... 202.63.35.99
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:08:49--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 2) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:12:00--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 3) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:15:12--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 4) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:18:25--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 5) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:21:39--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 6) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:24:54--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 7) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:28:10--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 8) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:31:28--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try: 9) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:34:46--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try:10) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:38:05--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try:11) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80... failed: Connection timed out.
Retrying.

--12:41:24--  [http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb](http://raof.dyndns.org/falcon/pool/multimedia/libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb)
  (try:12) => `libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb'
Connecting to raof.dyndns.org|202.63.35.99|:80...

yes I just went over the code. The above link is not valid anymore but the code will skip over to another link when this one times out a few times and libdvdcss2 will get downloaded from an alternate location eventually.
We might remove the above link in the next update.

---

### Post by koperry on 2006-07-19
So I should just run automatix again and let it go a little longer on the timeouts? Thanks for responding so fast also.

---

### Post by arnieboy on 2006-07-19
> **koperry said:**
> So I should just run automatix again and let it go a little longer on the timeouts? Thanks for responding so fast also.

yeah just let the "damn thing" run : )

---

### Post by Kilz on 2006-07-19
> **arnieboy said:**
> yeah just let the "damn thing" run : )

Since you are looking at this post, [can you tell me why this may have happened]("http://www.ubuntuforums.org/showthread.php?t=208407") to a 64bit user running automatrix?

---

### Post by arnieboy on 2006-07-19
> **Kilz said:**
> Since you are looking at this post, [can you tell me why this may have happened]("http://www.ubuntuforums.org/showthread.php?t=208407") to a 64bit user running automatrix?
do u have a more specific question?

---

### Post by Kilz on 2006-07-19
> **arnieboy said:**
> do u have a more specific question?

The orignal question contains a link, the link is to 
[http://www.ubuntuforums.org/showthread.php?t=208407](http://www.ubuntuforums.org/showthread.php?t=208407) in case your browser cant see the link. The thread in question is to a post by a 64bit user who installed things with automatrix and resulted in mutiple errors.

---

### Post by arnieboy on 2006-07-19
> **Kilz said:**
> The orignal question contains a link, the link is to 
[http://www.ubuntuforums.org/showthread.php?t=208407](http://www.ubuntuforums.org/showthread.php?t=208407) in case your browser cant see the link. The thread in question is to a post by a 64bit user who installed things with automatrix and resulted in mutiple errors.

well if u want my comments on the problems faced, none of them are automatix related.
The network manager applet problem has been reported multiple times and the bug is registered with launchpad along with a fix.
The sun-java-doc package in multiverse is broken. Automatix no longer installs it.

---

### Post by Kilz on 2006-07-19
> **arnieboy said:**
> well if u want my comments on the problems faced, none of them are automatix related.
The network manager applet problem has been reported multiple times and the bug is registered with launchpad along with a fix.
The sun-java-doc package in multiverse is broken. Automatix no longer installs it.

Thanks.

---

### Post by arnieboy on 2006-07-19
The following is a good place for troubleshooting network manager related issues:
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by Kilz on 2006-07-19
> **arnieboy said:**
> The following is a good place for troubleshooting network manager related issues:
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)
Thanks again, im also glad the java error was fixed. Iv come accross a few people with it.

---

