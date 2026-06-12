---
title: "K9Copy / XDVDShrink"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aphorism on 2005-11-30
Anyone got these apps to work under amd64 Ubuntu?  Maybe even a deb repos for them?  

I managed to get K9Copy compiled, but it was a bit of a nightmare regarding the dependencies and, once I had the binary compiled, it bombed out on a regular basis.

Ideas?

---

### Post by gil-galad on 2005-11-30
xdvdshrink is a platform independent script and will work.  Just download the rpm from the site and convert it with alien.

---

### Post by Aphorism on 2005-12-07
XDVDShrink seems to work fine.  I managed to get K9Copy to compile, but it bombs out on a regular basis.  I am looking for the ability to utilize the DVD menu, and it doesn't appear xdvdshrink supports that. 

K9, on the other hand, does.

Unfortunately, on my amd64 box, it bombs.

Ideas?

---

### Post by redsmoke on 2005-12-07
I haven't tried it yet myself as I am at work but I found a repository that has amd64 debian packages of k9copy that might be a little more stable. I tried compling k9copy and it bombed in middle of copy for me as well so I am hoping this is a little more stable.

deb [http://spello.sscnet.ucla.edu/marillat/](http://spello.sscnet.ucla.edu/marillat/) sid main

from [http://debian.video.free.fr/](http://debian.video.free.fr/)

---

### Post by Aphorism on 2005-12-08
Yah found that repository too.  Having some dependency issue...

```
k9copy:
 Depends: kdelibs4c2a (>=4:3.4.3-1) but it is not installable
  Depends: libgcc1 (>=1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
  Depends: libidn11 (>=0.5.18) but 0.5.13-1.0 is to be installed
  Depends: libqt3-mt (>=3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
  Depends: libstdc++6 (>=4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  Depends: libxrender1 (>1:0.9.0-1) but 1:0.9.0-1 is to be installed

```

Anyone figure out how to get around this and achieve a clean apt-get out of the mess?  Without retrofitting older crap libs etc...

---

### Post by redsmoke on 2006-01-02
Just wanted to give an update on this thread I tried the newest version of k9copy 1.0.2 [http://k9copy.free.fr/](http://k9copy.free.fr/) with latest version of vamps 0.98 and it seems to work really well now...Doesn't crash now(a good thing) and is really fast(also a good thing). In order to install I don't remember what all libraries you need but your obviously going to need alot of kde libraries ./configure should give you a good idea of what to install. Anyways have fun.

---

### Post by Bone Down on 2006-01-24
I could use some help with K9 I am also having some trouble getting this to install and could use some assistance.

I can not seem to get vamps installed, nor K9

```
./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

[config.log]("http://paste.ubuntu-nl.org/7560")

Anyhelp on this would be greatful.

---

### Post by FluffyElmo on 2006-01-24
Bone Down: Try installing *build-essential* either from Synaptic or the command line.
```
sudo apt-get install build-essential
```

---

### Post by Bone Down on 2006-01-25
[QUOTE=FluffyElmo]Bone Down: Try installing *build-essential* either from Synaptic or the command line.
```
sudo apt-get install build-essential
```[/QUOTE]

I tried cmd line and it appears to be installing a group of files, I will try to install k9 once this has completed and report back.

---

### Post by Bone Down on 2006-01-25
okay I think I may have this figured out, and I think I will do a write up of what I had to do to make it install, if I suceed today.

---

### Post by Bone Down on 2006-01-25
ok i guess i don't have this figured out.

output of ./configure: 
[http://paste.ubuntu-nl.org/7638](http://paste.ubuntu-nl.org/7638)

output of 'make':
[http://paste.ubuntu-nl.org/7639](http://paste.ubuntu-nl.org/7639)

any suggestions?

I still cannot run 'make install'

---

### Post by kingsidy on 2006-01-25
I just installed from the repos from their website. I installed vamps manually before hand. if you guys want I can post the deb i think that it is still in the cache. So far i think that xdvdshrink is better, but i'll give it another shot

---

### Post by Bone Down on 2006-01-25
[QUOTE=kingsidy]I just installed from the repos from their website. I installed vamps manually before hand. if you guys want I can post the deb i think that it is still in the cache. So far i think that xdvdshrink is better, but i'll give it another shot[/QUOTE]

is xdvdshrink gui?
can you select/deselect items?
or is it command line?

my problem is that I used dvdbackup (cmd line) and ended up with 5.4GB file not capable of burning to 4.4GB dvd-r.

I need to actually compress the file now so that I can burn it to the dvd-r.

I am just looking for a good gui 9to5 program that is linux native, I like what I see with k9 and kdvdbackup, however neither is very install friendly.

but i have gotten further in the last couple of days than before, and I think with assistance I can most likely make it work.

---

### Post by kingsidy on 2006-01-26
yeah it is gui. you basically use to copy regular dvds into 4.7gig dvds.

---

### Post by Bone Down on 2006-01-26
[QUOTE=kingsidy]yeah it is gui. you basically use to copy regular dvds into 4.7gig dvds.[/QUOTE]

I will look into this then and see what comes of it.

---

### Post by Bone Down on 2006-01-27
okay I checked out xdvdshrink, and it is not quite what I am looking for.
It turns out that I am also missing the hard to install kdelibs4c2a.

```

k9copy:
  Depends: kdelibs4c2a (>=4:3.4.3-1) but it is not installable
  Depends: libgcc1 (>=1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
  Depends: libidn11 (>=0.5.18) but 0.5.13-1.0 is to be installed
  Depends: libqt3-mt (>=3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
  Depends: libstdc++6 (>=4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
 
```

How did others get this to work?

---

### Post by kingsidy on 2006-01-27
i downloaded the fedora rpm and used alien to convert to deb then dpkg to install the latter

---

### Post by Bone Down on 2006-01-27
[QUOTE=kingsidy]i downloaded the fedora rpm and used alien to convert to deb then dpkg to install the latter[/QUOTE]

could yo email me the converted one? I am not familiar with alien and would hate to install it just for one program.

bone dot down at powertripz dot com

---

### Post by kingsidy on 2006-01-28
here is the link to download the deb package

[http://rapidshare.de/files/12055334/dvdshrink_2.6.1-4_all.deb.html]("http://rapidshare.de/files/12055334/dvdshrink_2.6.1-4_all.deb.html")

---

### Post by Bone Down on 2006-01-28
[QUOTE=kingsidy]here is the link to download the deb package

[http://rapidshare.de/files/12055334/dvdshrink_2.6.1-4_all.deb.html]("http://rapidshare.de/files/12055334/dvdshrink_2.6.1-4_all.deb.html")[/QUOTE]

sorry that is dvdshrink, that is not going to do what I need. I would like to get k9copy to work.

I will keep researching since this is going nowhere.

---

### Post by kingsidy on 2006-01-28
here is the link for the k9copy deb

[http://rapidshare.de/files/12064869/k9copy_1.0.2-0kubuntu4_i386.deb.html]("http://rapidshare.de/files/12064869/k9copy_1.0.2-0kubuntu4_i386.deb.html")

---

### Post by kingsidy on 2006-01-28
here is the link k9copy de package

[http://rapidshare.de/files/12064869/k9copy_1.0.2-0kubuntu4_i386.deb.html]("http://rapidshare.de/files/12064869/k9copy_1.0.2-0kubuntu4_i386.deb.html")

---

### Post by Bone Down on 2006-01-29
[QUOTE=kingsidy]here is the link k9copy de package

[http://rapidshare.de/files/12064869/k9copy_1.0.2-0kubuntu4_i386.deb.html]("http://rapidshare.de/files/12064869/k9copy_1.0.2-0kubuntu4_i386.deb.html")[/QUOTE]

thnx a bunch, i was able to install this and i am currently running it now. once i know more about linux and have cleaned up this install; i will work on learning alien.

---

### Post by kingsidy on 2006-01-30
give some feedback about the quality

---

### Post by Bone Down on 2006-01-30
[QUOTE=kingsidy]give some feedback about the quality[/QUOTE]

well so far I was able to use K9 on one video, learning curve with the whole removing titles and such.

gave up on that one as the wife wanted to watch it, so I spent the next 7 hours trying it on another dvd, and I jept getting a 255 error.

researched that could not find a clear answer on how to resolve, so I did a complete shutdown and reboot, this helped but then when K9 would get to a certain point it would give me a verbose error.

This morning I took the same dvd to my xp pro box, and discovered it is a sony production and that it is running some kind of "ARccOS or ripguard" of which I have never heard of. I was only aware of the CSS stuff.

So now I need to find a way to bypass ripguard.

---

### Post by Greyhair on 2006-02-12
[QUOTE=kingsidy]give some feedback about the quality[/QUOTE]

Added these to my   /etc/apt/sources.list:

    deb [http://repos.knio.it/](http://repos.knio.it/) breezy main contrib non-free
    deb-src [http://repos.knio.it/](http://repos.knio.it/) breezy main contrib non-free

Then installed K9Copy.

It takes about 1.5 hrs to copy and burn each DVD; on this system. 

So far, no problems encounted and the resulting image quality is very good.

---

### Post by jnie on 2006-02-13
I used K9Copy with Dapper Flight CD2 a month ago, and that worked fine, I know it's Dapper but anyways, if you have the patience I'm sure It'll be worth the waiting.... 
Bah!! who am I kidding! :-k

---

### Post by Bone Down on 2006-02-13
everything works well with K9 Copy, my only issue is the new encryption has not been addressed with in the linux group yet.

ex: flightplan I could not copy with lin, but with updated software I was able to do so with win. (for the record I prefer lin).

I am monitoring many of the cd/dvd backup forums that have support forums for lin, however i am not seeing anything other than wine + xx app, not what I want to do, I would like to keep it native.

---

### Post by haddog on 2006-02-20
Good info all. Latest version of ,1.0.2-ubuntu1, of K9copy is "authoring" as we speak. Had to change the default directory where the video is "ripped" to. Otherwise K9 would error out during the authoring process. In the settings tab, I have selected the auto burn option using k3b. I agree with B D. I wish to keep my DVD burnng linux native.

---

### Post by Aphorism on 2006-02-27
Anyone had any luck with the new encryption out there from good old happy-go-lucky Sony?

Has anyone managed to say, get Flightplan to de-css to disk then tried shrinking from that?


Just curious.

---

### Post by wargames on 2006-03-03
[QUOTE=Aphorism]Anyone had any luck with the new encryption out there from good old happy-go-lucky Sony?

Has anyone managed to say, get Flightplan to de-css to disk then tried shrinking from that?


Just curious.[/QUOTE]

Well, you can use DVDFab Decrypter and install that under wine. Some new DVD's are using a new protection method that so far no native Linux DVD rippers nor can Windows DVDShrink or DVD Decrypter can rip, example would be the movie "FlightPlan" among other very new releases. But there is a Windows program and it's suppose to work under wine, called DVDFab Decrypter. You can get it for free from softpedia.com.

Get it here:
[http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/DVDFab-Decrypter.shtml](http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/DVDFab-Decrypter.shtml)

Then head over to the wine hq applications database and follow the directions to install DVDFab Decrypter using the mfc42.dll file. As you can see on this page is has a Gold rating for Breezy. I have this installed on my system but have not had time to test it, but it should work. Then just burn using the growisofs command or shrink it afterword. 

Wine HQ applications database page for DVDFab:
[http://appdb.winehq.org/appview.php?versionId=3372](http://appdb.winehq.org/appview.php?versionId=3372)

I know this is not a native Linux solution, but right now, it's the only one I know of to rip these new discs, until someone writes a native Linux app. to do the same thing.

Hope this helps.

---

### Post by Aphorism on 2006-03-03
Read a thing that the darn protection ain't so great -- just skip past the black leader and you can rip it easily apparently.

Someone verify this as I don't have one of those nasty Sony disks.

[Skip over Sony header protection hints.]("http://forums.afterdawn.com/thread_view.cfm/297057")

---

### Post by mschievano on 2006-03-11
it seems that now k9copy work well, also with reauthoring.
I'm using now the version from dapper: 1.0.2-0ubuntu1
Also with gnome.

---

### Post by pstracha on 2006-06-11
[QUOTE=mschievano]it seems that now k9copy work well, also with reauthoring.
I'm using now the version from dapper: 1.0.2-0ubuntu1
Also with gnome.[/QUOTE]

Hmmm ... I just installed the latest version of k9copy (v1.0.4) and I still don't seem to have any luck with the Sony disks. Anyone else have any luck with k9copy and the new sony ARccOS ripguard?

DVDFab is working nicely but it'd be nice to have a native Linux application.

---

### Post by ubu-for on 2006-06-19
Is it possible to build an DVD9-ISO with K9Copy? Shrinking is not necessary!

P.S. DVD Decrypter and "dd if=..." don't work.

---

### Post by Cimmo on 2006-06-26
[QUOTE=ubu-for]Is it possible to build an DVD9-ISO with K9Copy? Shrinking is not necessary!

P.S. DVD Decrypter and "dd if=..." don't work.[/QUOTE]
yes I think it is possible from v1.0.4, this is my bug report, reply to it to have some visibility.
[https://launchpad.net/distros/ubuntu/+source/k9copy/+bug/50997/+index](https://launchpad.net/distros/ubuntu/+source/k9copy/+bug/50997/+index)

---

### Post by OU812 on 2006-07-24
DVD95 can copy to dvd9.

[http://dvd95.sourceforge.net/](http://dvd95.sourceforge.net/)

It's a .rpm so make sure you have alien installed.

To get xdvdsrhink to work, install all required packages from the repo. See this page for dependencies:

[http://ozzzymdk.dyndns.org/DVDShrink.html](http://ozzzymdk.dyndns.org/DVDShrink.html)

Then download and install dvd shrink (after untaring, "cd dvdshrink" and then "sudo ./install.sh"). (Installation may look like it hangs, but I think it completes the install.) Navigate to the folder ~/dvdshrink/usr/bin/ and double-click the file xdvdshrink.pl. (This is the folder that you get after untaring it. To make things easier, add an entry to you menu.

john

PS xdvdshrink is worth a look since it copies multi-episodes from a dvd (for example discs with tv shows)

---

### Post by ubu-for on 2006-07-27
> **kingsidy said:**
> here is the link to download the deb package

[http://rapidshare.de/files/12055334/dvdshrink_2.6.1-4_all.deb.html]("http://rapidshare.de/files/12055334/dvdshrink_2.6.1-4_all.deb.html")

Why does dvdshrink try to burn the DVD imediately after the setup and doesn't create an ISO instead? I don't have two drives.

```

INFORMATION

   Project:                                  xxxxx
   File cleanup?                             No
   Auto-burn?                                No, prompt
   Save ISO with burn?                       No
   DVD Title:                                1
   Audio channel:                            0
   Subtitle channel:                         None

   PROGRESS   Rip started at 14:11:14

   DVDSHrink Function                        Status    Elapsed

   Reading the chapter list                  Done!    [00:00:01]
   Ripping Title                             Done!    [00:00:01]
   Remultiplexing                            Done!    [00:00:01]
   Building DVD on drive                     Done!    [00:00:01]
   Building TOC                              Done!    [00:00:01]

   Ready to start burning the new DVD!

   Hit 'q' to quit or any other key to start burning the new DVD...

```

---

