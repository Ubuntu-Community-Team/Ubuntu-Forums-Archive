---
title: "MXit"
date: 2007-12-27
forum: Za Team - South Africa
---

### Post by RudolfMDLT on 2007-12-27
Hi there,

I used ti be able to get my mxit buddies on GoogleTalk in Windows and using wither Pidgin or Kopete I was able to talk from my pc to my buddies on the cell phones. Now I get a 404 error on the mxit server. Anybody got any ideas on why?

---

### Post by Circus-Killer on 2008-01-10
okay, i'm not a hundred percent sure, but this is how i think the whole thing works.

google talk have jabber server(s), mxit have jabber server(s). both connect to a much larger jabber network (that inter-connects all jabber servers/networks). so that is why you should be able to see mxit contacts from google talk and vice versa.

now the problem, i think, is that either the google talk or the mxit servers aren't connecting to the much larger jabber network. my guess, its the mxit servers. i suspect that mxit are doing this on purpose to reduce server overhead, but thats just speculation.

in fact, this is all speculation, but i think this is why the problem exists. i've also been having the same problem and this is the only reason i could think of.

---

### Post by rudihawk on 2008-04-15
This is a perpetual problem I think. I wish clockspeed would just get Mxit to run, fast and efficiently,- I don't need or want all the other useless features they keep adding, which just adds bloat to the whole program.

---

### Post by johwel on 2008-06-08
hi everyone,

I have just managed to run Mxit using the Nhal emulator on Wine, without any problems. Now it even uses less CPU power than in Windows, according to my guage. :popcorn:

---

### Post by Bödvar on 2009-03-05
Any info on whether they will be releasing a version for Ubuntu?

---

### Post by drubin on 2009-03-06
> **Bödvar said:**
> Any info on whether they will be releasing a version for Ubuntu?

Have you tried running it under Wine? It seems simple enough to run under wine.

EDIT:
I was referring to their desktop application under wine not through an emulator.

---

### Post by Bödvar on 2009-03-06
> **drubin said:**
> Have you tried running it under Wine? It seems simple enough to run under wine.

EDIT:
I was referring to their desktop application under wine not through an emulator.

Yes, it failed to open. It just gave a blank little window, about the size I suppose the programme is supposed to be.

---

### Post by drubin on 2009-03-06
> **Bödvar said:**
> Yes, it failed to open. It just gave a blank little window, about the size I suppose the programme is supposed to be.

I am going to look into it for you. Will see what I can get going. I assumed it would work on Wine.

---

### Post by Bödvar on 2009-03-06
> **drubin said:**
> I am going to look into it for you. Will see what I can get going. I assumed it would work on Wine.

Thanks, I appreciate it!

---

### Post by drubin on 2009-03-06
Hi I found these
[http://code.google.com/p/telepathy-mixer/](http://code.google.com/p/telepathy-mixer/)
[https://launchpad.net/pidgin-mxit/](https://launchpad.net/pidgin-mxit/)

Let me know if they still work.

---

### Post by milamoto3 on 2009-10-07
Hi  Guys,

Im running Ubuntu 8.04.3 LTS x64.

Struggling to get MXit pidgin plugin to work.

Any ideas on how I can get the 32bit plugin to work on X64 version?

---

### Post by drubin on 2009-10-07
Hi

You need to compile the plugin your self. You will need the libpurple-dev package as well as build-essential. There should be a readme in the zip. :) 

[http://devzone.mxit.com/libPurple/downloads/](http://devzone.mxit.com/libPurple/downloads/)

They don't seem to have the source code listed there any more not sure if you have to login to view it first.... If it isn't there I suggest emailing them or asking on their forum why they stopped allowing access to download the code.

---

### Post by m4tic on 2009-10-10
There are many forums on mxit that have external links of the code. Try searching or request any of the users for it there.

---

### Post by rudihawk on 2010-02-27
Sorry for the necro post. 

I have managed to compile the mxit plugin from source. Both for 64bit Jaunty and 32bit Karmic. 

If you need some help just ask :)

---

### Post by kleinric on 2011-03-24
Hi All, 
I suppose that this is probably a bit late for this thread, but certainly now, the plugin build into pidgin works perfectly...
```
sudo apt-get install pidgin
``` 

and then mxit accounts just work.

---

