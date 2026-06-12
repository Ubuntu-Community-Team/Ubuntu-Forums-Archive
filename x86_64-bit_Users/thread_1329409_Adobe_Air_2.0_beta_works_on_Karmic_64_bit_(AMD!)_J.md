---
title: "Adobe Air 2.0 beta works on Karmic 64 bit (AMD!) Joy..."
date: 2009-11-17
forum: x86 64-bit Users
---

### Post by timgood on 2009-11-17
After months of struggle to get Tweetdeck and BBC iplayer-desktop installed on my AMD quadcore machine I downloaded the Air 2 beta, crossed my fingers and....


It Works!

Huzzah!

---

### Post by timgood on 2009-11-17
Perhaps my joy was a bit previous...

I'm now getting update manager showing 2 broken packages on my system - iplayer desktop and tweetdeck. Both are working fine - but there is obviously something still not installed. Will poke around and see what I can find.

Later:

OK, if you install the .deb package then dependencies are not set and adobeair looks as if it is not installed. However, installing from the .bin package is fine and the apt errors go away. Now got iPlayer and Tweetdeck working fine.

---

### Post by FokkerCharlie on 2009-11-17
That's good to know...

The current version of AIR works on my 64 machine, but is there any other advantage of AIR 2b?

Charlie

---

### Post by mirko_3 on 2009-11-17
how do you install it, the deb says it's 32bit? did you just force-install it?

---

### Post by mrtorrent on 2009-11-17
I've been having this same problem with broken dependencies using the .deb, I'll have to try the .bin installer. Thanks for posting about it.

> **timgood said:**
> Perhaps my joy was a bit previous...

I'm now getting update manager showing 2 broken packages on my system - iplayer desktop and tweetdeck. Both are working fine - but there is obviously something still not installed. Will poke around and see what I can find.

Later:

OK, if you install the .deb package then dependencies are not set and adobeair looks as if it is not installed. However, installing from the .bin package is fine and the apt errors go away. Now got iPlayer and Tweetdeck working fine.

---

### Post by timgood on 2009-11-18
> **mirko_3 said:**
> how do you install it, the deb says it's 32bit? did you just force-install it?

You can force install it - on my system this caused some problems with broken dependencies so I installed using the .bin file (available on the same download page). 

Now iPlayer Desktop works and downloads programmes, but when I try to play them I get the message that they are 'temporarily unavailable' and to try later. The files are downloaded, and I can see them in /home/user/Video/BBC iPlayer/ but for some reason they will not play. Any ideas?

---

### Post by FokkerCharlie on 2009-11-18
I had that problem with iPlayer quite a bit when using a proxy to fool it into thinking I was home in the UK!

Are you in the UK?

Charlie

---

### Post by timgood on 2009-11-18
Indeed, in glorious Devon, just a local call away from heaven.

---

### Post by FokkerCharlie on 2009-11-18
That's strange, then.  Mind you, I can't play anything on iPlayer this morning.  I wanted to listen to "I'm sorry I haven't a clue".. :frown:

---

### Post by timgood on 2009-11-18
I does seem that my joy was unfounded.

Tweetdeck works fine. But BBC iPlayer Desktop will download programmes and then refuse to play them with the ...temporarily unavailable. Please try later message. Other forums suggest that this may be related to a foreign IP address, but I have a UK one. Programmes will play fine from Firefox if I use iPlayer on the web - but downloaded ones will not. Any ideas?

---

### Post by e.m.fields on 2009-11-18
Hey. I can't get Tweetdeck working. 

Using AMD64 + Adobe Air 2.0. 
Anyone got it running?

---

### Post by mrtorrent on 2009-11-18
> **e.m.fields said:**
> Hey. I can't get Tweetdeck working. 

Using AMD64 + Adobe Air 2.0. 
Anyone got it running?

Works fine for me -- what problems are you having?

Also, regarding the dependency issue with the .deb package, I filed a bug with Adobe and they've been corresponding with me a bit to track it down, so hopefully that will be sorted soon.

---

