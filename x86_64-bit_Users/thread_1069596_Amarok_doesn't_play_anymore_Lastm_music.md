---
title: "Amarok doesn't play anymore Lastm music?"
date: 2009-02-14
forum: x86 64-bit Users
---

### Post by giannisfs on 2009-02-14
I use Amarok 1.4.10

I usually listen to some music from Amarok with the lastfm plugin
but since one month and later , after some** important updates**(which i don't remember what was their names)
i installed 
into ubuntu, Amarok stopped playing lasfm sources and instead acts weird 
for example:

When i try to connect to  lastfm://globaltags/Heavy Metal
I get :
```
Error Loading Media
No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
http://195.24.233.49:80/last.mp3?Session=ab7nh0an9dr8d0n9n6asdn
```

But as soon as i click again to play the stream Amarok claims that
it is playing the stream without asking me to accept the cookies as usually does... :(

I have all the libxineXXXX plugins installed

and all what is nessecery to play local and internet streaming mp3's.
and also the lasfm program it's self.

And all the repositories enabled even icluding medibintu.
The Error i get means that is missing a suitable plugin wright?
so what exactly should be that plugin?

```
My sound system that Amarok uses is 
xine Engine
My Library is libamarok_xine-engine
Version is 1
the Framework Version is 32
```

In some older posts i founded that it needs libxine-extracodecs

but when type sudo apt-get install libxine-extracodecs

i get:

```
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate
```

So i typed sudo apt-get install libxine1-ffmpeg
and i got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libxine1-ffmpeg is already the newest version**.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


I also tried to change the sound system engine to
**yauap engine** so i installed from synaptic the amarok-engine-yauap 
package.
i selected it and i tried again to connnect to lastfm many times but 
some times i got an error message saying Conection terminated unexpectedly and other times  not error and no sound.


So so what exactly should be the  plugin amarok needs to understand the lastfm urls and play the music?
is that a problem of the engine amarok uses ?

Does anybody know how to make amarok  1.4.10
play lastfm? 

Do i must install a newer version of Amarok in order to work?
How did it worked so nice until before one month?

:confused::(:(:

---

### Post by nstasino on 2009-02-14
I have the exact problem.
Ubuntu 8.10
Amarok 1.4.10


It works just fine on Amarok2. But I find 1.4 version richer in features.

---

### Post by confy on 2009-02-15
amazing... i have SAME problem...
perhaps we should put it as a bug?
i tried amarok --sync
but i don't get any error...

IMHO server 195.24.233.49 don't serve... if you try to wget it you will get connection refused...


Sometimes it seems like it tries to buffer and than stops...

---

### Post by daniel014 on 2009-02-15
Just use Songbird. It has a Last FM plugin.

---

### Post by confy on 2009-02-15
There is no replace for amarok...
We've look for alternatives and found that amarok rocks. But lets stay on topic. Does anyone else have this problem?

---

### Post by duke87 on 2009-02-16
i have same problem. when ever i try to run last.fm it's pop up that message

---

### Post by jet2230 on 2009-02-16
same. i would like to know why i cant play radio streams thru Amarok anymore

---

### Post by confy on 2009-02-17
after update, there is one more message...

> The connection was refused for the URL: 
xine parameters: 

can you confirm?

---

### Post by Teufel on 2009-02-27
Same problem for me.

---

### Post by oldguysrule on 2009-02-27
Hi All
I'm having the exact same problem with the same errors. I have also found that Rhythmbox will no longer play LastFm either. It gives a no network detection error. 
Last Exit is now acting up as well - it logs into LastFM, plays one song and stops. I'm not at home so can't post the terminal errors but all 3 of them worked fine a few weeks ago (sorry I know I'm being a little vague:(). 
Any help would be appreciated. I have removed -- purged and reinstalled with no change to the outcome.

Running 'Hardy' on a 64bit system.
OGR

---

### Post by confy on 2009-03-02
I asked same question on amarok forum:
[http://amarok.kde.org/forum/index.php/topic,16510.0.html](http://amarok.kde.org/forum/index.php/topic,16510.0.html)

I've install amarok2 :)

Now it works...

---

### Post by giannisfs on 2009-03-02
Nice, it sounds reasonable that old amarok uses the old lastfm protocol
so there is no way going back to 1.xx  versions and having a full functional amarok except ... reprogramming it.:popcorn:

So anybody who wants his amarok fully working ,should simply install the latest version.
This topic is closed :guitar:

---

