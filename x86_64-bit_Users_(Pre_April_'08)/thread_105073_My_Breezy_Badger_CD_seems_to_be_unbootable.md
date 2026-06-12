---
title: "My Breezy Badger CD seems to be unbootable"
date: 2005-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by keldo on 2005-12-17
I try to install ubuntu 5.10 but can’t boot from the CD. 
I got a Red Hat CD and it work perfectly. 
I have compared the content on both CD, and there isn’t any autorun-file on the Breezy Badger CD for example. 
What should I locking for and how do I make my CD bootable?:confused:

---

### Post by localzuk on 2005-12-17
Where did you get the disc? Did you download and burn the iso image?
Did you check the md5 sum of the disc vs the md5 sum of the file on the server?
What exactly happens when you try to boot the disc?

---

### Post by keldo on 2005-12-18
I download the iso image from ubuntulinux.org/download/
Before I burn the cd I extract the package in WinRAR (I suppose it was a good thing to do)

Here is a summary of the content of the disc: 1818 files, 1200 maps, size: 639 774 707 byte

A booting dialog (“cd boot”) appears for a few seconds just before windos start loading, I trying to boot by type enter but it is not working.

---

### Post by Peter76 on 2005-12-18
You should never extract an ISO image; just burn it directly to cd. In Nero, use "burn image" or use something like that in other burn programs. That should sort your problem

---

### Post by keldo on 2005-12-18
Thanks
Hopefully I will be able to run ubuntu on my computer today 
:KS

---

### Post by gconn77 on 2005-12-18
Keldo,

Good luck with the install... also when I downloaded the ISO from the web... it was a bad. I used the bit torrent download instead that that aside from some other trouble worked. 

Please continue to share your experience so that the community can provide support and others can learn from your situation. Also if you should have any other trouble... please continue to post in this thread, so that I can keep up to date with your situation. 

I too, am having some trouble installing.... and I am curious to see if you eventually will have the same problems that I have been having. If you want to look at my situation, just view my profile here, and search the threads that I have created.

---

### Post by keldo on 2005-12-26
Thanks gconn77 

Your advice is most likely the best way to solve this problem.
But before I start to download iso-file again I wanted to ask if the installing progress could be started manually in MS-DOS?

---

### Post by keldo on 2005-12-27
Hi 
Anyone how read this topic please be patient with me 
(for my bad English and lack of computer skill).

I have just read a document form Phoenix about the “el Torito standard” and it enlightens my understanding of how a bootable CD works.

I’m now going to download the image again.
But I’m concern about doing something wrong with the image after downloaded it.

I suppose it will be compressed even this time and I don’t have a clue how to drag out all the files and maps without extract them. 
I understand that some files most continue to be un-extract but merely burn the iso unmounted didn’t work either.

Any guidance how to do a proper burning will encourage me a lot.

---

### Post by Norberg on 2005-12-27
I guess your in windows now then you can do like this:
1. Download a cd burning software eg. [http://www.cdburnerxp.se/](http://www.cdburnerxp.se/) its free
2. Download the iso-file from [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/)
3. open  cdburnerxp and click on "Click here to... Create a new Data-CD"...
4. Click file in upper left corner and chose write disc from iso-file
5. Chose the ubuntu iso file and start burning.

---

### Post by jdp on 2005-12-31
[QUOTE=keldo]Anyone how read this topic please be patient with me 
(for my bad English and lack of computer skill).
[...] I’m now going to download the image again.
But I’m concern about doing something wrong with the image after downloaded it.

I suppose it will be compressed even this time and I don’t have a clue how to drag out all the files and maps without extract them. 
I understand that some files most continue to be un-extract but merely burn the iso unmounted didn’t work either.

Any guidance how to do a proper burning will encourage me a lot.[/QUOTE]

If the file is a .iso, you absolutly do not extract any files from it to make it bootable.  You use a buring program (as mentioned above, Nero or another) and "burn from image" "burn from raw", etc.  The .iso is an exact copy of not just the files to be on the CD but their physical layout on the disc, which is very important to the "El Torito" standard you mentioned.  If you remove the files from the .iso and try to burn them seperatly, they just won't work.

ISOs make setting up the bootable CDs much more simple, but many people are so used to things being complicated, they can't see how simple it is to get them to work. ;)  Just downlaod the .iso, open the burning app and use "burn image" with the .iso file.  Simple!  No confusing copying of thousands of files, no extraction, no headaches.  Just possible corrupted downloads and coastered CDs. :rolleyes:

---

### Post by keldo on 2006-01-05
Hi everyone

Thanks for your effort to help me.

Anyhow, my free ship it cd had arrived and   
I’m happy to say that I now run Ubuntu and I’m very happy about it
Unfortunately I didn’t learn how to make a functional CD.

I suppose the matter was cause by an incomplete download, but I’m not sure
Only clue I got is a message in bitTorrent download bar

It said
[download complete: 5% missing………. ]

But I found that piece of information very doubtful.

---

### Post by russbuss on 2006-01-08
I had similar problems when I firs tried to burn an iso CD using my G4 Powerbook.  I don't know if Keldo was trying to burn his CD on a Mac or some other OS, but I thought this might be helpful for some folks out there.

I was rather naively trying to use the drag-and-drop burn CD function built into Mac OSX.  For unknown reasons (to me, that is), this will not properly burn an iso.  In order to burn my iso correctly I had to do the following:

1) Download the dmg of ubuntu and mount the dmg by double-slicking it.

2) Open "Disk Utility" which should be in /Applications/Utilities and insert a blank CD into the burner.

3) If you have correctly mounted the dmg of the ubuntu iso, it should appear in the left-most window of the Disk Utility window.

4) There will be two instances of the iso: the .dmg version and the mounted version listed below that.

5) Select the mounted version and then click the "Burn" icon.

6) This should burn a bootable iso CD (it's how I got my installation CD to finally work!)

I don't know why you have to use the Disk Utility to burn iso's on Mac OSX, but it appears that you.  I discovered this by searching the topic on apple's website (a rather torturous and frustrating thing to do; thus this posting).



-Ben.

[QUOTE=keldo]I try to install ubuntu 5.10 but can’t boot from the CD. 
I got a Red Hat CD and it work perfectly. 
I have compared the content on both CD, and there isn’t any autorun-file on the Breezy Badger CD for example. 
What should I locking for and how do I make my CD bootable?:confused:[/QUOTE]

---

