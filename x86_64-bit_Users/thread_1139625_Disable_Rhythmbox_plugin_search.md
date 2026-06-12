---
title: "Disable Rhythmbox plugin search?"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by timgood on 2009-04-27
Since upgrading to Jaunty Rhythmbox insists on finding suitable plugins at start for non-media files. Is there anyway of disabling this as it is a royal pain? Thanks.

---

### Post by Slurm on 2009-04-27
Hey,

Just to let you know,  I am having the exact same problem.  Plus my movie player will not work and flash/gnash is totally gone from Firefox..

Coincidence?.... I think NOT!

I hope someone will point us in the right direction...

---

### Post by timgood on 2009-04-29
I got fed up with this and installed Amarok 2 - not bad, but wish I could get Rhythmbox working properly.

---

### Post by wingnux on 2009-05-05
I'm having the same problem with Rhythmbox, any help?

---

### Post by Yellow Pasque on 2009-05-06
Do you have gstreamer0.10-packagekit installed?

---

### Post by wingnux on 2009-05-06
I've installed it after reading your post and it didn't help, rhythmbox still keeps asking to search for codecs, it's pretty annoying...

---

### Post by Vincent15 on 2009-05-06
Just to let you know I have the exact same problem, except I'm on 32-bit. Should I delete all my .db and .ini files?

---

### Post by budde on 2009-05-07
Hey guys.

I had the same issue with a lot of files such as .url and .db etc...

I "solved" the issue by opening the "Imput Errors" tab on the left side and simply removed the files shown there (the ones that couldn't be 'played' - since they're not media files).

Maybe not the best solution, especially if they're files that you want to keep, but it worked for me.

Alternatively you can just ignore the window that pops up without pressing either "Cancel" or "Search" and just let it be. Atleast that way it won't pop up again.

As I said, it's more of a symptomatic treatment that doesn't actually resolve the issue, but it works.

---

### Post by wingnux on 2009-05-07
I usualy right-click the window and send it to my 4th desktop :P

---

### Post by Yellow Pasque on 2009-05-07
I guess the lesson here is not to add non-media files/folders to Rhythmbox?

---

### Post by crustache on 2009-06-05
Very annoying indeed and still no solution from the bug report. Anything new?

---

### Post by MSToTheEnd on 2009-06-06
> **budde said:**
> Hey guys.

I had the same issue with a lot of files such as .url and .db etc...

I "solved" the issue by opening the "Imput Errors" tab on the left side and simply removed the files shown there (the ones that couldn't be 'played' - since they're not media files).

Maybe not the best solution, especially if they're files that you want to keep, but it worked for me.

Alternatively you can just ignore the window that pops up without pressing either "Cancel" or "Search" and just let it be. Atleast that way it won't pop up again.

As I said, it's more of a symptomatic treatment that doesn't actually resolve the issue, but it works.

I had to do the same thing because it was really annoying in while scanning my 1TB collection of FLAC files :(

---

### Post by MSToTheEnd on 2009-06-06
> **budde said:**
> Hey guys.

I had the same issue with a lot of files such as .url and .db etc...

I "solved" the issue by opening the "Imput Errors" tab on the left side and simply removed the files shown there (the ones that couldn't be 'played' - since they're not media files).

Maybe not the best solution, especially if they're files that you want to keep, but it worked for me.

Alternatively you can just ignore the window that pops up without pressing either "Cancel" or "Search" and just let it be. Atleast that way it won't pop up again.

As I said, it's more of a symptomatic treatment that doesn't actually resolve the issue, but it works.

I had to do the same thing because it was really annoying in while scanning my 1TB collection of FLAC files :(

---

### Post by vahnx on 2009-06-11
> **Temüjin said:**
> I guess the lesson here is not to add non-media files/folders to Rhythmbox?

How is it a lesson when most people set up a new PC, get their music player to scan a Music directory which also contains Windows thumbnail files along with album art and possibly other files, and unsupported formats which causes the Rhythmbox import errors in the first place. I doubt anyone would take the time to manually go in and remove all their album art/unsupported files from each directory before importing then putting them back.

---

### Post by SushiR on 2009-06-14
> **vahnx said:**
> How is it a lesson when most people set up a new PC, get their music player to scan a Music directory which also contains Windows thumbnail files along with album art and possibly other files, and unsupported formats which causes the Rhythmbox import errors in the first place. I doubt anyone would take the time to manually go in and remove all their album art/unsupported files from each directory before importing then putting them back.
I'd say they should add a function "Ignore on next scan" or something like that. Why should one NOT include album art in an album directory? It's a nice feature that you're asked ONCE to look for plugins, but not EVERY time.

---

### Post by billybag on 2009-08-18
> **wingnux said:**
> I usualy right-click the window and send it to my 4th desktop :P

This made me laugh.

i have same problem.

---

### Post by martin saint martin on 2009-08-20
I'm dealin' with the same "Search for suitable plugin?" annoyance over here too. Any advice out there?

---

### Post by Yellow Pasque on 2009-08-20
You might want to try a newer version of rhythmbox: [https://launchpad.net/~ricotz/+archive/ppa](https://launchpad.net/~ricotz/+archive/ppa)

Or maybe try Exaile: [http://www.exaile.org/](http://www.exaile.org/)

---

### Post by powerslavez on 2009-09-06
Hi, 


What I did was to search my music folder for .ini, .db and .url files using ubuntu's search function. I then selected all of the results and deleted them. I was thus able to get rid of Rhythmbox's attempts to download plugins for those files. 

I hope that helps, 


Vlad

---

### Post by rudihawk on 2009-09-13
> **budde said:**
> Hey guys.

I had the same issue with a lot of files such as .url and .db etc...

I "solved" the issue by opening the "Imput Errors" tab on the left side and simply removed the files shown there (the ones that couldn't be 'played' - since they're not media files).

Maybe not the best solution, especially if they're files that you want to keep, but it worked for me.

Alternatively you can just ignore the window that pops up without pressing either "Cancel" or "Search" and just let it be. Atleast that way it won't pop up again.

As I said, it's more of a symptomatic treatment that doesn't actually resolve the issue, but it works.

Did as you did, and the problem didn't reoccur. Seems like rhythmbox is trouble with .nfo and .txt files being in the directories that it must monitor.

---

### Post by gokalpo on 2009-11-17
Hi,
I could solve this problem by removing package gnome-codec-install

---

