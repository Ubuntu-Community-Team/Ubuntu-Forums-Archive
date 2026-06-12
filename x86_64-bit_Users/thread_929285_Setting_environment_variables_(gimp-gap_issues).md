---
title: "Setting environment variables (gimp-gap issues)"
date: 2008-09-24
forum: x86 64-bit Users
---

### Post by aura eyes on 2008-09-24
Greetings,

I'm having a bit of a problem with GAP in gimp.  When I try to extract a video through XTNS/split video into frames/Mplayer based extraction, I get a message saying that mplayer 1.0 must be installed somewhere in my PATH and that if mplayer isn't in my PATH or isn't named mplayr, I have to set environment variable GAP_MPLAYER_PROG to my mplayer program and restart gimp.

I have searched for awhile, and I tried the command:

 export GAP_MPLAYER_PROG=mplayer

Which did nothing

I did a:

which mplayer 

which gave me this:
/usr/local/bin/mplayer

I think I might be able to add something to my ~/.profile or ~/.bashrc, but I'm not sure what to put in there. 

I want to make a gif from a video.  If there's a better program anyways, that would work too.  Just seems that gimp (gap) could do it if I could get it do work.

I'm stuck.  Please help.  Thanks.

---

### Post by markkupaakkonen on 2008-09-30
Hi, I've got the same problem.
Haven't found a solution yet...

This I know so far: 
with cinelerra you can make the frames to jpegs cinelerra > file > load files (the video) > render > jpeg or jpeg secuence
And then you can pile those as layers to Gimp and so on...

But that's really kind a slow...

So, me too, I'd rather make the Gimp Mplayer path working.

EDIT: Got it! In the Mplayer based extraction window UNCHECK the mplayer1.0pre5 mark. Ad voila! The job done!

Cheers!

---

