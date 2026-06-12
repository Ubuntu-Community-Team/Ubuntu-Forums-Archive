---
title: "Hf+"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Donnut on 2005-11-18
Hi.  Quick question, does Ubuntu read and write to the apple format hf+?  I converted totally from windows and need to change my large external drive to a format that I can actually use.

---

### Post by aysiu on 2005-11-18
It reads HFS+ for sure. I mounted with a Ubuntu live CD my wife's HFS+ partition on her G4 Powerbook. I don't know about write permission, though.

---

### Post by SectionThree on 2005-11-18
It definitely does support HFS+, I have an external hard drive formatted that way that I can read and write to no matter how I boot up (Ubuntu, OS X, OS 9).  It acts a bit weird though.  The folders I create on it in Mac OS X/9 are only writable in Mac OS X/9, while the folders I create on it in Ubuntu are (you guessed it) only writable whilst running Ubuntu.  However, I can read all/copy from all no matter what OS I'm running (it all has to do with "permissions":rolleyes: )

Perhaps this is a good place to post my question as well:  When I was first installing Linux (first it was Gentoo--UGH!!!, then Debian, and finally, Ubuntu--YEA!!!), I partitioned my 20 GB internal drive thusly:

6 GB (HFS+) to boot OS X and "Classic Mode";
50 MB (HFS) for the bootstrap;
6 GB (EXT3) for the root filesystem;
320 MB for the swap partition and;
*7 GB for a partition that could act as a bridge between Mac and Ubuntu.*

I'm trying to figure out how to get that last partition to mount on both Mac OS (X/9) and Ubuntu, so far without success.  Does anyone know how to do it?

---

### Post by autocrosser on 2005-11-19
Well--To answer a couple of questions--If you are root user in the given operating system you can write anywhere you want--HFS+ or EXT2/3--I have used the root user functions in both OSX & Ubuntu to allow cross-writing (it seems that you have to allow read/write access in BOTH OS's to allow a "normal" user to read/write) after I enabled root in OSX, I could "allow" EVERYTHING to be re-writen (highly dangerous!)--so in view that my wife uses the system too--I allowed the "shared" folder in OSX & created one in Ubuntu (in OSX you can have a drive or directory that has "no" permissions, but a shared folder is easier to control) In Ubuntu allow everyone access to the folder you create--If you are the sole user, I'd still restrict the permissions a bit--just so you need to "think" about what you are about to do--this has saved me several times---from myself!!!

Side note--in OSX you need a "control panel" called EXT2--available from SourceForge or VersionTracker.com--it is not currently workable with anything before OS 10.2 or after 10.3.9--The above info "assumes" you are working within those OS---OS 10.4 and above are not supported yet:???:

---

### Post by SectionThree on 2005-11-19
I appreciate the tips and I have figured out how to get into root in the terminal on both Ubuntu and OSX 10.1.5.  Now, does anybody know what commands I should use to get my spare partition formatted as HFS+ **and** read/write under both OS X and Ubuntu?

Much appreciated :)

---

### Post by autocrosser on 2005-11-19
Well--It's a bit different to be in the terminal as root or be logged in as root--You need to look around (try Apple.com tech section) to get the commands to allow Root log in for OSX--Apple is not forthcoming about how to do it--As Root in OSX is about the same as Root in Ubuntu--You can modify every file on the system & hidden .files are seen--I'd just format the partition in OSX & allow full access for all users--I haven't used 10.1 in about 3/4 years, so I don't remember the exact way it works it--I'd update to 10.2--it has more options & is more stable to work with--10.1.5 was not out for very long & is not supported very well.....You can get 10.2 update discs on eBay for 10/15 dollars these days, so it's simple to do.

---

### Post by autocrosser on 2005-11-20
Ok--For those who are interested in the EXT2 control panel for OSX--I just checked with his page at SourceForge.net & there is a update note from late last month--He is working on the new version for 10.4 & expects to have it done by the first of the year\\:D/ Look for EXT2FSX on SourceForge & send him some notes of encouragement!!!!:smile:

---

### Post by SectionThree on 2005-11-20
I found the documentation at the Apple website on how to login as root in OS X here:
[URL="http://docs.info.apple.com/article.html?artnum=106290"]
http://docs.info.apple.com/article.html?artnum=106290[/URL]

It was quite easy to do actually, it involves software that comes with all versions of OS X.

Now, back to my continuing dilemma.  You see, noob that I am, I formatted the partition in question as reiserfs and now the OS X disk utility won't even recognize its existence no matter how I'm logged in, and running it from the OS X install CD is no different.

So I went into GParted which does recognise the partition, but it won't do HFS+.  I tried to change this 7 GB partition to HFS, but it gave me an error message that an HFS partition could be no bigger than 2048 MB.

Anybody have any ideas?

---

### Post by Ptero-4 on 2005-11-20
You're pretty much in a big one there. ext2fs/ext2fsx doesn't support reiserfs and hfs have a 2GB limit (that was one of the hfs problems hfs+ was intended to fix). Your better option is to use gparted to partition your 7GB reiserfs partition as ext2 and then use ext2fs for OSX (from sourceforge.net).

---

### Post by SectionThree on 2005-11-21
I appreciate everybody's advice. I guess I'll upgrade from OS X 10.1.5 to 10.2 so I can use ext2fs, which I downloaded from Sourceforge. I'll see you all in a few weeks with either a new boatload of problems or a glowing report on how evrything's going great. In the meantime, I'll just use my external drive for the purposes I intended to use the "lost partition" for. By the way, autocrosser, the advice you offered about enabling all the permissions on a volume as root in OS X worked like a charm!

Again, I thank you all!

---

### Post by autocrosser on 2005-11-21
Not a prob--that's what we're here for--Glad it helped you!!!

---

### Post by SectionThree on 2005-12-29
Well, I'm back.  I finally got OS X 10.2 and installed ext2fs and now I have my problematic partition up and running on both OSes.  Now I have one final problem.  When I start up Ubuntu, it thinks the partition in question is still reiserfs and tells me I either have to manually fix the superblock or hit control-D to continue, which I do.

I've figured out how to mount it from the command-line (sudo mount -t ext2 /dev/hda13 /media/Data) and it works fine, but does anyone know how to get the #%$@ing thing to mount at startup?

---

### Post by gavin8or on 2006-10-27
> **SectionThree said:**
> Well, I'm back.  I finally got OS X 10.2 and installed ext2fs and now I have my problematic partition up and running on both OSes.  Now I have one final problem.  When I start up Ubuntu, it thinks the partition in question is still reiserfs and tells me I either have to manually fix the superblock or hit control-D to continue, which I do.

I've figured out how to mount it from the command-line (sudo mount -t ext2 /dev/hda13 /media/Data) and it works fine, but does anyone know how to get the #%$@ing thing to mount at startup?


I know this thread is dead but I'll answer your question, maybe someone will answer mine.

Answer: You need to edit your /etc/fstab file. Where it says "reiserfs" you need to change it to "ext2" and it will mount for you as an ext2 partition automagically.

Question for everyone: How on EARTH can I get rw support for hfs+ (Could I ask for HFS+ Journaled, if i dare??) on linux. I'm running ubuntu on my macbook right now and I can't get my iPod to work seemlessly with OSX, windows and ubunut (all on the same laptop, is what I want).

---

### Post by Ptero-4 on 2008-02-20
gavin8or. You can't AFAIK just mount your iPod (since IIRC it doesn't support mass storage format), instead you need to use either amarok (KDE) or gtkpod (Xfce, gnome) when in linux and iTunes when in OSX and Windows.

---

