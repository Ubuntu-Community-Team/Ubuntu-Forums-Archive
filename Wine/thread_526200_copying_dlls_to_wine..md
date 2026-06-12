---
title: "copying dlls to wine."
date: 2007-08-15
forum: Wine
---

### Post by MichaelSM on 2007-08-15
Hi gamers. This is something you all seem to know about. I'm trying to run Autocad2000 with wine but starting it up in terminal returns six dll's missing. That's OK(?) because I can locate them on my install cd (or in the files I've copied to Desktop)

I've done winecfg and listed in libraries the dlls to run 'native Windows' but I haven't been able to copy the dlls to wine/C/ system32 etc. You know what I mean.

Everyone mentions just to 'do it' like breathing I guess.

A quick how-to would be greatly appreciated.

Thanks everyone.

Mike.

---

### Post by shad0w_walker on 2007-08-15
Putting the dlls into the system32 folder is pretty easy when you know how, so most people tend to just say 'Stick them in there and carry on'

1. Open nautilus (File browser) goto your home folder and press ctrl+h (This shows the hidden files/folders)
2. Find the folder called .wine and go into it.
3. Enter the folder called drive_c (The contents of this folder should look almost identical to a fresh windows install.)
4. Go into the windows folder
5. Go to the system32 folder and paste your dll files into there.
6. Close nautilus, job done.

---

### Post by MichaelSM on 2007-08-15
Thank you shadowWalker!

Amazing! So far.........!

I shifted the six dlls I mentioned and tried again, but there were more needed. Bummer.

So I just opened the 'acad' file with 1889 entries and copied and pasted them  to the system32 in wine as a block. Instant access.

I haven't done a test drawing yet, but autocad seems just like it was on windoze. Except it's in W98 format which is a bit weird since I used to utilise it in XP.

There must be 1883 dll library entries I haven't assigned to 'native Windows' but I'm happy enough right now to plod along and see what happens. According to what I've read there could be some disasters re. shifting such massive entries without vetting them in wine libraries. Oh well.

I'm delighted with your advice. I have a little book full of notes which might help others with genuine autocad cds to migrate to Ubuntu and piss off their MS stuff.

No doubt I'll be back with glitches, but I hope to work most of them through myself.

It's a pretty weird thing to be able to D-C a  'Windows' Desktop icon and find myself where I wanna be.

Thanks heaps.
Mike.

---

### Post by shad0w_walker on 2007-08-15
Quite welcome. Enjoy it and see how it goes, worst comes to worst you need to tinker some more, if not then enjoy.

---

### Post by MichaelSM on 2007-08-15
Thanks again SW. Once I think I have it right I'll try to get it more XP than W98. I ought to count my blessings.
Mike.

---

### Post by madsmeg on 2007-08-15
this has also helped me, i was in the same situation, thanks :)

---

### Post by MichaelSM on 2007-08-15
Hey, madsmeg.

How did you go? 

I did a $400 paid tutorial on autocad some years ago. It's too late for me to bring out the booklet I got with it now and to insert all the layers and parameters I've forgotten how to do in the meantime. 

Please keep in touch and we can swap ideas re. difficulties/achievements.

It is a massive program indeed.

All the best,
Mike.

---

### Post by madsmeg on 2007-08-20
You got a little more complicated than me ^^, i just found the Dll's i needed and found the directory they needed to go in and copied them over :), doubt thats any help :p

---

### Post by MichaelSM on 2007-08-21
The main thing is that ACAD2000 is able to installed and run on Ubuntu quite simply with wine after all. A longish process of finding out how to do it can be condensed into a few easy steps. 

There ought to be a few happy campers out there now!

Thanks for your reply madsmeg.

Brainiy and more computer-wise people will make the process even easier than the roughie I did!

I just got a bit excited when it all fell into place.

Mike.

---

### Post by weblordpepe on 2009-02-03
Ahhh... its great seeing people get their first 'i got it to work in linux!' moments. :) :) Always takes me back to early slackware days :)

---

