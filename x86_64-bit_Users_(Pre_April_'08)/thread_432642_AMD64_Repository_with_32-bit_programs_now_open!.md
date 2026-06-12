---
title: "AMD64 Repository with 32-bit programs now open!"
date: 2007-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by dfreer on 2007-05-04
**[B]Please note: Although I hope that this will be an easy and elegant way to install 32-bit apps in AMD64, for right now we do not have many packages, and things are a *little* bit rough. Any help with testing and developing would be most appreciated!**[/B]

Ok, so after a short discussion in this thread:
[http://ubuntuforums.org/showthread.php?t=430391](http://ubuntuforums.org/showthread.php?t=430391)

I decided to create a repository that would contain 64-bit packages of 32-bit programs. So basically instead of using custom scripts and manually installing 32-bit library files to get a program to work, you will be able to simply use apt-get to install the 32-bit version of the program. Sound good?

Right now these are the programs that are included. Please feel free to let me know of any amd64.debs that you would like to add to this list (in particular, wine/firefox w/plugins/mplayer w/codecs are needed), and I will get them up after reviewing.

**These are the packages so far:**
[LIST]
[*]pSX for i386
[*]pSX32 for amd64
[*]pSX-frontend for i386
[*]zsnes for i386
[*]zsnes32 for amd64
[/LIST]

**These are the libraries so far:**
[LIST]
[*]lib32gtkglext1 for amd64
[*]lib32ao2 for amd64
[/LIST]

**These are the packages in testing:**
[LIST]
[*]mplayer32-nogui
[*]mplayer32
[/LIST]
There are a bunch of libraries in testing, I will be putting up a page at [http://packages.dfreer.org](http://packages.dfreer.org) (EDIT: ummm in progress) soon that will have an official list. We could use help testing mplayer32 at the moment, both GUI and non-GUI, especially anyone who knows of files that can play in 32-bit but not 64-bit (I think any of the apple trailers will only work in 32-bit, so .mov?)


**[B]To add this repository:**[/B]
```
echo "deb http://packages.dfreer.org feisty main" | sudo tee -a /etc/apt/sources.list
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
```

**[B]To add the testing repository *(BE CAREFUL KIDS!)*:**[/B]
```
echo "deb http://packages.dfreer.org feisty testing" | sudo tee -a /etc/apt/sources.list
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
```

---

### Post by dfreer on 2007-05-04
I cannot seem to figure out why Falcon won't create an html index file. Here's my /etc/falcon.ini script:
```
[falcon]
# This is the only setting that you most likely should change. All other
# settings have defaults that are useful, but you can tune them to your need.
# (Don't you just love it: only one required configuration variable)
#
basedir = /var/falcon
# Short description of your repository
description = Falcon generated repository
# Key to be used for signing the release file. When not set, the Release file
# will not be signed
gpgkey = 5A22BD68
# The "origin" field in the release files, for instance your (nick)name. This
# should also contain no spaces
origin = Falcon
# The "label" field in the release files. Usually the same as origin, but be
# creative :)
label = Falcon
# Set to 'no' if falcon shouldn't generate a component named 'all' that contains
# all packages in your release
do_all = yes
# Set to no if falcon shouldn't generate a Contents.tar.gz file for use with
# apt-file
create_content = yes
# Which architectures are supported? Defaults to the output of dpkg-architecture
# -qDEB_BUILD_ARCHITECTURE
architectures = i386 amd64

# Template options:
# Base url of your webserver, include the hostname!
# If not set, no index.html files will be created
webbase = http://packages.dfreer.org/
# Web template. If you want to create your own, read readme-templates.txt. Do not
# include the .py extension
template = default
# Directory to find the templates in, defaults to $PREFIX/share/falcon
template_dir = /usr/share/falcon/
# All external files used by the template. The default template uses just
# falcon.png and favicon.ico
webfiles = falcon.png favicon.ico

# Information about configuring mirrors can be found in the documentation
#[samplemirror]
#webbase    = http://mirror.ubuntulinux.nl/
#rsync      = mirror.ubuntulinux.nl:/var/www/falcon
#rsync_opts =
#sponsor    = Dennis Kaarsemaker
#releases   = all
#components = all
```

If anyone could help me out with this it would be most appreciated.

Also, I've been trying to decide how the version/package names should go. Basically, my version of pSX looks like this:
pSX_1.11-1.2_amd64.deb
And the package name is just psx. Which is fine considering there is no psx package in the official repositories. However, firefox will probably cause a conflict, or at the very least be confusing to someone trying to download the 32-bit version. I'm thinking all repackaged 32-bit programs should have a specific naming convention, like how the 32-bit libraries are called ia32-libs. should it be ia32-firefox, or firefox32? Any input would be welcome!

---

### Post by Kilz on 2007-05-04
> **dfreer said:**
> 
Also, I've been trying to decide how the version/package names should go. Basically, my version of pSX looks like this:
pSX_1.11-1.2_amd64.deb
And the package name is just psx. Which is fine considering there is no psx package in the official repositories. However, firefox will probably cause a conflict, or at the very least be confusing to someone trying to download the 32-bit version. I'm thinking all repackaged 32-bit programs should have a specific naming convention, like how the 32-bit libraries are called ia32-libs. should it be ia32-firefox, or firefox32? Any input would be welcome!

Great idea offering a repo for 32bit applications. I agree that there should be a naming convention. Either way is ok with me. I have used both ia32 and appname32 in the past. But to make it consistent with Ubuntu maybe we should use ia32. Should there also be a install convention? As of now libraries are installed to /usr/lib32. I have been installing applications to /usr/local. Should applications go in /usr/local/ia32 ?
Secondly, how would someone who wants to use the repo get packages to you? I can see where the repo would be useful for keeping applications up to date.

---

### Post by dfreer on 2007-05-04
I'm really interested in getting more people in on this, especially you kilz seeing your work on the AMD64 forum. I want to open this repo up, but I'm not sure on the best way to do so. I don't want to simply create an FTP site and let just anyone post a .deb for immediate usage on the repo, but neither do I want to slow things by inserting myself and getting in people's way. Right now I use SSH to transfer files back and forth, but I'm definitely *not* going to let tons of people ssh into my machine.

So this is what I had in mind. Create a small feedback/forum on my server, and of course this thread. When people have a new program that they have packaged, they can post a link and description. We'll have a small review/testing committee that will make sure the program works and doesn't have rootkits and the like, and then give the original developer access to a folder under their name, where they can post their .deb and all subsequent revisions. At the end of each week (or night if needed), I'll symlink any new .debs into the repo and update it. Of course that's a pretty rough sketch but I think it should work out. 

As for right now, I'm going to actively monitor this thread for anything new, so if anyone wants they can provide me with links to .debs, I can check them out manually and then add them (plus I'm working on a few myself), simply to get things going. 


as for the naming convention we might have to play it by ear. IMO, I'm thinking package and release names should follow the ia32 convention and the binaries should have the 32 appended at the end (like the binaries installed in /usr/bin/ and /usr/local/bin/). I'm thinking if at all possible the program's files should be installed to the same directory as the original package, except with ia32 in front (/usr/local/ia32-firefox).

---

### Post by ronocdh on 2007-05-04
dfeer, thank you so much for putting the time into this, and congratulations! Your suggested protocol seems pretty fair to me; weekly updates of the repo will give us something to look forward to. ;)

Kilz, I support segregating the 32 apps in a place like /usr/local/ia32, however I really happen to like the appname32 nomenclature. It's just much more immediately pleasant to see in the app bar or whatever. It's what I'm used to, though, so I guess I'm ready for a change if my vote is overruled.

This is exciting!

---

### Post by dfreer on 2007-05-04
thanks :)

well, definitely keep the appname32, because there are some users that use both versions and will need to be able to distuingish the 32-bit binary from the 64-bit. but that should only be on binary file itself (/usr/bin/firefox and /usr/bin/firefox32). 
I'll try to get something going discussion board wise on the server soon. For now just post in here :)

---

### Post by skibrianski on 2007-05-06
Hey, you guys took my idea and ran with it. Hurrah! I'll check it out in a bit, keep up the great work :)

---

### Post by skibrianski on 2007-05-06
nevermind, this has been fixed now

---

### Post by skibrianski on 2007-05-06
Ok, I'm going to start packaging up libraries needed for [mplayer32]("http://ubuntuforums.org/showthread.php?t=188974")

Here's my first stab at lib32comerr, which is one of 8 packages I needed to grab 32 bit libs from to make it install properly...
[http://gadgets.xml-comma.org/ubuntu32-on-64/lib32comerr2_1.39-1_dfreer-1.deb](http://gadgets.xml-comma.org/ubuntu32-on-64/lib32comerr2_1.39-1_dfreer-1.deb)

If y'all could take a look and let me know if there is anything I missed or could be doing better, I'd be obliged.

Cheers.

---

### Post by skibrianski on 2007-05-06
> **ronocdh said:**
> Kilz, I support segregating the 32 apps in a place like /usr/local/ia32

These files should not be under /usr/local - /usr/local is for files you can't install via your package manager, typically. In an ideal world, I would actually say these apps should live under /usr/bin or whatever, and we should add conflicts with the 64 bit versions and/or provide virtual packages which can be fulfilled with either the 32 or 64 bit version. Seeing as how that's not so likely, how about /usr/bin32 and the like?

---

### Post by Kilz on 2007-05-06
> **skibrianski said:**
> These files should not be under /usr/local - /usr/local is for files you can't install via your package manager, typically. In an ideal world, I would actually say these apps should live under /usr/bin or whatever, and we should add conflicts with the 64 bit versions and/or provide virtual packages which can be fulfilled with either the 32 or 64 bit version. Seeing as how that's not so likely, how about /usr/bin32 and the like?

The I think adding the 32 to the end of the application name (appname32) would be easier. If we did add a new bin, it would also have to be added to the path. Since there are only a handful of apps (and shrinking with each year), adding a whole directory for the binaries is slight overkill imho.

---

### Post by dfreer on 2007-05-06
> **skibrianski said:**
> By the way the first line there is wrong. Instead you can use:
```
echo "deb http://packages.dfreer.org feisty main" | sudo tee -a /etc/apt/sources.list
```

Cheers

ooops yep, I'll correct that thanks! And I'll check out the rest of the posts as soon as I get a chance.

---

### Post by dfreer on 2007-05-06
> **skibrianski said:**
> Ok, I'm going to start packaging up libraries needed for [mplayer32]("http://ubuntuforums.org/showthread.php?t=188974")

Here's my first stab at lib32comerr, which is one of 8 packages I needed to grab 32 bit libs from to make it install properly...
[http://gadgets.xml-comma.org/ubuntu32-on-64/lib32comerr2_1.39-1_dfreer-1.deb](http://gadgets.xml-comma.org/ubuntu32-on-64/lib32comerr2_1.39-1_dfreer-1.deb)

If y'all could take a look and let me know if there is anything I missed or could be doing better, I'd be obliged.

Cheers.

This looks fine, control file is cleaned up quite nicely. Since I'm fairly new to debian packages myself, I was wondering what these two lines do?:

```
Provides: libcomerr-kth-compat
Source: e2fsprogs
```

I'm not exactly sure why there are ia32-libs- packages and lib32 packages, I think we should stick to ia32-libs- naming convention. Why? Honestly, simply because I cannot seem to find a difference between the two names, it seems there are more *official* ia32-libs packages than lib32 packages, and amd64.debian.net only seems to use ia32-libs (granted there are only like 4 packages ATM). If there is a reason to use lib32 I'll gladly listen, but I think standardization is needed here.

So basically, just change the package name in DEBIAN/control and the *.deb name and I get this up on the repo ASAP. 

Still researching the best way to include you guys as developers on the repo. I'm thinking of creating a ssh accounts, with each developer privilege to read/write to their package folder only. Probably need to jail them in that folder as well. Then, the weekly update will symlink the new packages to the repo and update it. So basically, I'll probably be using rssh. Just gotta read up more on it and then install it.
[http://ubuntuforums.org/showthread.php?t=128206](http://ubuntuforums.org/showthread.php?t=128206)

---

### Post by dfreer on 2007-05-06
FHS (Filesystem Hierarchy Standards):
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

Also, for your package skibrianski you should have ldconfig run in the postinst and postrm scripts are run, please see this page for why:
[http://www.debian.org/doc/debian-policy/ch-sharedlibs.html#s-ldconfig](http://www.debian.org/doc/debian-policy/ch-sharedlibs.html#s-ldconfig)
and check out these links for a standard postinst and postrm script (should just copy these into the DEBIAN directory and it will be ok):
[http://www.dfreer.org/~dfreer/postinst](http://www.dfreer.org/~dfreer/postinst)
[http://www.dfreer.org/~dfreer/postrm](http://www.dfreer.org/~dfreer/postrm)

EDIT: However, it doesn't look like ldconfig even checks the /usr/lib32/ folder so it may not make any difference. hmmm.

---

### Post by skibrianski on 2007-05-07
> **Kilz said:**
> The I think adding the 32 to the end of the application name (appname32) would be easier. If we did add a new bin, it would also have to be added to the path. Since there are only a handful of apps (and shrinking with each year), adding a whole directory for the binaries is slight overkill imho.

Fair enough. It just seems a bit odd that the average user should have to remember to type firefox32 instead of firefox. But, on the other hand, the average user should be starting firefox from the applications menu anyway.

---

### Post by skibrianski on 2007-05-07
> **dfreer said:**
> This looks fine, control file is cleaned up quite nicely. Since I'm fairly new to debian packages myself, I was wondering what these two lines do?:

```
Provides: libcomerr-kth-compat
Source: e2fsprogs
```

I'm not exactly sure why there are ia32-libs- packages and lib32 packages, I think we should stick to ia32-libs- naming convention. Why? Honestly, simply because I cannot seem to find a difference between the two names, it seems there are more *official* ia32-libs packages than lib32 packages, and amd64.debian.net only seems to use ia32-libs (granted there are only like 4 packages ATM). If there is a reason to use lib32 I'll gladly listen, but I think standardization is needed here.

Actually, there is a convention, although it's a bit weird. ia32-libs* is for collections of libraries, but lib32* is for single libraries adapted from the x86 package. I think we should stick with that convention, so as to ease upstream adoption when the time comes. The only exception I've found seems to be libc6-i386:

```

ski@ganiodayo:/var/cache/apt/archives$ apt-cache search ia32-libs
ia32-libs - ia32 shared libraries for use on amd64 and ia64 systems
ia32-libs-gtk - gtk+ ia32 shared libraries for with OpenOffice.org
ia32-libs-kde - KDE ia32 shared libraries for with OpenOffice.org
ia32-libs-sdl - ia32 shared libraries of sdl related packages for use on amd64 and ia64 systems
ski@ganiodayo:/var/cache/apt/archives$ apt-cache search lib32
lib32asound2 - ALSA library (32bit)
lib32asound2-dev - ALSA library development files (32 bit)
lib32bz2-1.0 - high-quality block-sorting file compressor library - 32bit runtime
lib32bz2-dev - high-quality block-sorting file compressor library - 32bit development
lib32gcc1 - GCC support library (32 bit Version)
lib32gcj-bc - Link time only library for use with gcj (32bit)
lib32gcj7-0 - Java runtime library for use with gcj (32bit)
lib32gcj7-dbg - Debugging symbols for libraries provided in lib32gcj7-dev
lib32gcj7-dev - Java development and static library for use with gcj (32bit)
lib32ncurses5 - Shared libraries for terminal handling (32-bit)
lib32ncurses5-dev - Developer's libraries for ncurses (32-bit)
lib32readline5 - GNU readline and history libraries, run-time libraries (32-bit)
lib32readline5-dev - GNU readline and history libraries, development files (32-bit)
lib32stdc++6 - The GNU Standard C++ Library v3 (32 bit Version)
lib32z1 - compression library - 32 bit runtime
lib32z1-dev - compression library - 32 bit development
libc6-dev-i386 - GNU C Library: 32bit development libraries for AMD64
lib32ffi4 - Foreign Function Interface library runtime (32bit)
lib32g2c0 - Runtime library for GNU Fortran 77 applications (32bit)
lib32gfortran1 - Runtime library for GNU Fortran applications (32bit)
lib32mudflap0 - GCC mudflap shared support libraries (32bit)
lib32objc1 - Runtime library for GNU Objective-C applications (32bit)
lib32stdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
lib32comerr2 - common error description library - 32 bit mode

```

> Still researching the best way to include you guys as developers on the repo. I'm thinking of creating a ssh accounts, with each developer privilege to read/write to their package folder only. Probably need to jail them in that folder as well. Then, the weekly update will symlink the new packages to the repo and update it. So basically, I'll probably be using rssh. Just gotta read up more on it and then install it.
[http://ubuntuforums.org/showthread.php?t=128206](http://ubuntuforums.org/showthread.php?t=128206)

Hmm, I think the update can run a lot more often than weekly - if you need help cobbling together a script that checks for new files without using a lot of resources, let me know, I've been hacking shell scripts together for over a decade, and perl for about 5 years, and am happy to help.

---

### Post by skibrianski on 2007-05-07
> **dfreer said:**
> This looks fine, control file is cleaned up quite nicely. Since I'm fairly new to debian packages myself, I was wondering what these two lines do?:

```
Provides: libcomerr-kth-compat
Source: e2fsprogs
```

Well, to be honest I copied the control file from the i386 native package and then pared it down. The Source I just think is what you have to compile to get the binaries in question. Provides is for virtual packages, I'm not sure what the right thing to do here is, since the package doesn't provide libcomerr-kth-compat, but instead provides a 32 bit version of same... Maybe it should provide lib32comerr-kth-compat?

---

### Post by skibrianski on 2007-05-07
> **dfreer said:**
> Also, for your package skibrianski you should have ldconfig run in the postinst and postrm scripts are run.

EDIT: However, it doesn't look like ldconfig even checks the /usr/lib32/ folder so it may not make any difference. hmmm.

Yea, I actually removed these on purpose because I figured ldconfig wouldn't be checking /usr/lib32 or /lib32. However, looking at the official ubuntu lib32 packages, perhaps it seems like the developers of these libraries have left those ldconfig statements in - here's the postinst file for lib32stdc++6:
```

#! /bin/sh -e

case "$1" in
    configure)
        docdir=/usr/share/doc/lib32stdc++6
        if [ -d $docdir ] && [ ! -h $docdir ]; then
            rm -rf $docdir
            ln -s gcc-4.1-base $docdir
        fi
esac

# Automatically added by dh_makeshlibs
if [ "$1" = "configure" ]; then
        ldconfig
fi
# End automatically added section

```

... so I guess I'll put the ldconfig postinst and postrm scripts back in (although I'm not sure if they do what we want them to do or not, they shouldn't hurt except for maybe increasing the time to add/remove the package).

---

### Post by dfreer on 2007-05-07
Re: Firefox32 vs. Firefox
I agree with kilz on appending 32 to the end of the actual binary located in /usr/bin. We do not want to *replace* any 64-bit apps, and our 32-bit package should not modify the 64-bit apps at all. Your right, any 32-bit app should probably have a .desktop entry to correctly launch it (unless it was never designed to be launched from the GUI).

Re: ia32-libs and lib32.
That seems like a valid point to me. But what about programs? what should we call them? Once we get this stuff standardized (and I get a web page up on packages.dfreer.org), I'll create a list of where files should go/acceptable file names/acceptable package names.

Re: Weekly update script
If it ever grows to the point where I can't watch it, sure (hopefully soon)! As for right now I don't even have a way for people to upload the files, and since I am uploading them myself I just update it manually when I do so. Thanks for offering to help with scripts though, I can use all the help I can get! I'll let you know. 
I could use a website programmer, if anyone wishes to help. Otherwise I'm just gonna grab a CSS template cuz I don't want to futz around :D .

Re: Provides and Source in DEBIAN/control
[http://www.debian.org/doc/debian-policy/ch-relationships.html#s-virtual](http://www.debian.org/doc/debian-policy/ch-relationships.html#s-virtual)
[http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Source](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Source)
The package will work fine without them. You're right about provides, but this isn't a virtual package so I would take it out. Source *will* be needed (see below note), but until someone makes the source package I would leave it out as well.

Re: ldconfig and postinst/postrm scripts
Yeah, I never quite understood that. ldconfig should be maintaining a cache of all libraries installed on the system, yet it's conf file says it only looks in /usr/lib and /lib. I would keep both scripts in, it may yet check the lib32 folders (according to it's man page it's designed to do so) and I may have missed how it does.

BTW, although I'm loathe to implement it, at some point (if we ever progress upstream) we will need to provide source packages. 
[http://www.debian.org/social_contract#guidelines](http://www.debian.org/social_contract#guidelines)
Just something to keep in mind, right now emphasis is on getting 32-bit apps up and working for 64-bit users who *need* them.

---

### Post by skibrianski on 2007-05-07
ok, I built a few more packages in pursuit of mplayer32 joy. There is a list here: 

[URL="http://gadgets.xml-comma.org/ubuntu32-on-64/index.html"] http://gadgets.xml-comma.org/ubuntu32-on-64/index.html
[/URL]

There is also a shell script I'm using to do a first pass of converting i386 debs to lib32 style debs for amd64 there. See convert-386-lib-to-amd64-lib32.sh in the listing.

Comments welcome.

---

### Post by skibrianski on 2007-05-07
> **dfreer said:**
> Re: ia32-libs and lib32.
That seems like a valid point to me. But what about programs? what should we call them? Once we get this stuff standardized (and I get a web page up on packages.dfreer.org), I'll create a list of where files should go/acceptable file names/acceptable package names.

I don't think we have to overthink this - something like this is probably enough:
lib32* for single libraries go in /lib32 and /usr/lib32
ia32-libs-* for library bundles go in /lib32 and /usr/lib32
*32 for binary files go in the same dir as the upstream package, just with 32 appended after the name.

> **dfreer said:**
> BTW, although I'm loathe to implement it, at some point (if we ever progress upstream) we will need to provide source packages. 
[http://www.debian.org/social_contract#guidelines](http://www.debian.org/social_contract#guidelines)
Just something to keep in mind, right now emphasis is on getting 32-bit apps up and working for 64-bit users who *need* them.

Yeah. My opinion on this is it's not important - but I'll leave source in for now, because I don't think it hurts.

On a more general point, I think the goal here is to provide working binary packages, not to get everything exactly right (although we need to make sure we don't do horrid things like clobbering 64 bit libs/apps, etc. as you pointed out). Let's get it close enough, then generate enough buzz that the ubuntu devs have to take notice. Once they do, they will feel proprietary about how we are doing such horrible things like not providing proper sources in "their" packages, and will hopefully step in and start building these things properly. So, in some sense, having consistent yet not perfecftly LSB-compliant  packages is almost a feature in my book ;)

---

### Post by dfreer on 2007-05-07
> **skibrianski said:**
> I don't think we have to overthink this - something like this is probably enough:
lib32* for single libraries go in /lib32 and /usr/lib32
ia32-libs-* for library bundles go in /lib32 and /usr/lib32
*32 for binary files go in the same dir as the upstream package, just with 32 appended after the name.

On a more general point, I think the goal here is to provide working binary packages, not to get everything exactly right (although we need to make sure we don't do horrid things like clobbering 64 bit libs/apps, etc. as you pointed out). Let's get it close enough, then generate enough buzz that the ubuntu devs have to take notice. Once they do, they will feel proprietary about how we are doing such horrible things like not providing proper sources in "their" packages, and will hopefully step in and start building these things properly. So, in some sense, having consistent yet not perfecftly LSB-compliant  packages is almost a feature in my book ;)

lol. well, as long as the programs work, that's the main thing. so start developing everyone!
I'll check out your packages ASAP, when i don't need to get up in 6 hours. I'm scheduled to work for 50 hours this week, yet another girl quit and I gotta fill her hours lol. so dont expect much outta me this week.

---

### Post by skibrianski on 2007-05-07
A bit more is there now, namely everything one would need to install mplayer32 package.

There are a lot of libraries bundled up in the mplayer32 package itself, I'm going to start working on extracting them and then uploading a new mplayer32 package we can track that just has the mplayer32 binaries in it.

---

### Post by dfreer on 2007-05-07
alright, so I'm checking it out the files you uploaded. I downloaded the 32-bit mplayer and made a quick .deb so I can test it.
looks like the following libraries still need to be converted:
libdvdread3
libmad0
libdv4
libvorbis0a
libogg0
libtheora0
libxvidcore4
libmpcdec3

There may be more but right now I gotta get back to work.

---

### Post by skibrianski on 2007-05-07
> **dfreer said:**
> alright, so I'm checking it out the files you uploaded. I downloaded the 32-bit mplayer and made a quick .deb so I can test it.
looks like the following libraries still need to be converted:
libdvdread3
libmad0
libdv4
libvorbis0a
libogg0
libtheora0
libxvidcore4
libmpcdec3

There may be more but right now I gotta get back to work.

Yea, these are the ones that were bundled up with the mplayer32 package I had. Will get to them sometime later this week.

Cheers...

---

### Post by dfreer on 2007-05-07
so you aren't using the original i386 mplayer from the ubuntu repositories? well, as long as it works I actually don't care lol. I'll stay out of your hair and let you finish it up, I think I'm going to turn my attention to getting a good wine package out. Just let me know when you are ready to upload or if you need help testing.

---

### Post by skibrianski on 2007-05-08
> **dfreer said:**
> so you aren't using the original i386 mplayer from the ubuntu repositories? well, as long as it works I actually don't care lol. I'll stay out of your hair and let you finish it up, I think I'm going to turn my attention to getting a good wine package out. Just let me know when you are ready to upload or if you need help testing.

Oh, my plan is to eventually repackage the original i386 mplayer, yea, but first along the way is getting this old dpkg to work properly. There's a lot of damn libraries that pull in a lot of other damn libraries in there :) I'll get there...

Cheers,

---

### Post by skibrianski on 2007-05-08
Ok, all the library dependencies are in place, tomorrow-ish I'll build the mplayer32 deb :)
  [http://gadgets.xml-comma.org/ubuntu32-on-64/index.html](http://gadgets.xml-comma.org/ubuntu32-on-64/index.html)

# lib32-zlib1g1:1.2.3-13ubuntu4_dfreer-1_amd64.deb
# lib32comerr21.39-1_dfreer-2_amd64.deb
# lib32dv41.0.0-1build1_dfreer-1_amd64.deb
# lib32dvdread30.9.7-2ubuntu1_dfreer-1_amd64.deb
# lib32gcrypt111.2.2-2_dfreer-2_amd64.deb
# lib32gnutls131.4.4-3build1_dfreer-1_amd64.deb
# lib32gpg-error01.4-2build1_dfreer-3_amd64.deb
# lib32krb531.4.3-9ubuntu1.2_dfreer-1_amd64.deb
# lib32lzo11.08-3_dfreer-2_amd64.deb
# lib32mad00.15.1b-2.1_dfreer-1_amd64.deb
# lib32mpcdec31.2.2-1_dfreer-1_amd64.deb
# lib32ogg01.1.3-2ubuntu2_dfreer-1_amd64.deb
# lib32opencdk80.5.9-2build1_dfreer-1_amd64.deb
# lib32sasl2-22.1.22.dfsg1-8ubuntu2_dfreer-1_amd64.deb
# lib32sasl2-modules2.1.22.dfsg1-8ubuntu2_dfreer-1_amd64.deb
# lib32ssl0.9.80.9.8c-4build1_dfreer-1_amd64.deb
# lib32tasn1-30.3.5-1_dfreer-2_amd64.deb
# lib32theora00.0.0.alpha7.dfsg-2ubuntu1_dfreer-1_amd64.deb
# lib32vorbis0a1.1.2.dfsg-1.2_dfreer-1_amd64.deb
# lib32xvidcore42:1.1.2-0.1ubuntu1_dfreer-1_amd64.deb

---

### Post by skibrianski on 2007-05-08
By the way, just to make a note of it, I removed lib32-zlib1g1:1.2.3-13ubuntu4_dfreer-1_amd64.deb, since it conflicts with lib32z1, and lib32z1 seems to do the trick (might even be the exact same thing, haven't looked at it closely, it's bundled with ia32-libs).

---

### Post by skibrianski on 2007-05-08
PS - We should set up a wiki, preferably trac, somewhere... It'd provide for much better communications.

---

### Post by dfreer on 2007-05-08
> **skibrianski said:**
> PS - We should set up a wiki, preferably trac, somewhere... It'd provide for much better communications.

Sounds fine to me. If you have experience with trac, let me know if this how-to will work:
[http://trac.edgewall.org/wiki/TracOnUbuntu](http://trac.edgewall.org/wiki/TracOnUbuntu)
It's a little dated but it looks like it should work. Anyways, hopefully it will be up within the week.

---

### Post by iggee85 on 2007-05-09
There's no amd64 deb for ZSNES in the repos yet, so you can't install using apt-get. But thanks for including the it in your sig.

---

### Post by dfreer on 2007-05-09
zsnes, although it installs fine manually with dpkg, evidently had a syntax error in it's DEBIAN/control file which caused my repository to create apt-get update errors with everyone. I took it down, got busy, and forgot to put the new version up. 

It's fixed now :) 

install with *sudo apt-get install zsnes32*

---

### Post by skibrianski on 2007-05-10
> **dfreer said:**
> zsnes, although it installs fine manually with dpkg, evidently had a syntax error in it's DEBIAN/control file which caused my repository to create apt-get update errors with everyone. I took it down, got busy, and forgot to put the new version up. 

It's fixed now :) 

install with *sudo apt-get install zsnes32*

A bit off-topic, but I just installes zsnes32, nice work :) The sound is very choppy tho, but I never used the 32 bit version on a 32 bit machine so it might be something as simple as a config option.

---

### Post by iggee85 on 2007-05-10
K thx on your quick repsonse! Keep up the good work!

---

### Post by skibrianski on 2007-05-10
Wow, the mplayer32 deb I used to start down this road appears to have been a stripped down compile, missing support for all sorts of things. In any event, there are as of a few minutes ago 38 .deb files converted and uploaded to my server, but at least 12 libraries + their recursive depends still need to be compiled):

[http://gadgets.xml-comma.org/ubuntu32-on-64/index.html]("http://gadgets.xml-comma.org/ubuntu32-on-64/index.html")

[LIST]
[*]lib32faac0
[*]lib32fontconfig1
[*]lib32ggi2
[*]lib32gl1-mesa-glx | lib32gl1
[*]lib32pulse0
[*]lib32x11-6
[*]lib32xext6
[*]lib32xinerama1
[*]lib32xv1
[*]lib32xvmc1
[*]lib32xxf86dga1
[*]lib32xxf86vm1
[/LIST]

On the plus side, the list is long enough that, when I'm done, there should be libs for lots of the stuff klitz needs for ffox, etc.

---

### Post by skibrianski on 2007-05-10
By the way, the packages I've been buildling are for feisty. I see no reason why in the future we shouldn't add support for dapper and edgy too, given the time... Thoughts?

---

### Post by dfreer on 2007-05-10
zsnes32 is compiled WITHOUT libao support, sorry about that everyone. that is why the sound is choppy. when compiled with libao, it segfaults. I suspect this is due to a dependency of libao that I must've missed. anyways, I'm working on figuring that out, as soon as I do I'll put a new version up. the 32-bit version runs SUPER smooth, the two are the same other than that libao support.

as for the libraries skibrianski, yeah I noticed that you seemed to be missing a bunch of depends. let me know if you want to offload some of those libraries to me, I can help out. yeah, half of those will be used in firefox32 so it'll help alot.

Definitely add support in the future. However, we need to get the packages up first and then go back and add older version support, although I'm sure you already know that.
EDIT: BTW, skibrianski, I haven't put your .debs in because I'm waiting to test them first with mplayer32.

---

### Post by RAOF on 2007-05-11
> **skibrianski said:**
> ...
[LIST]
[*]lib32faac0
[*]lib32fontconfig1
[*]lib32ggi2
[*]lib32gl1-mesa-glx | lib32gl1
[*]lib32pulse0
[*]lib32x11-6
[*]lib32xext6
[*]lib32xinerama1
[*]lib32xv1
[*]lib32xvmc1
[*]lib32xxf86dga1
[*]lib32xxf86vm1
[/LIST]
...

Many of these are already in Ubuntu, in the various ia32-libs* packages.  Make sure you don't duplicate the work of existing packages! :)

---

### Post by skibrianski on 2007-05-11
> **RAOF said:**
> Many of these are already in Ubuntu, in the various ia32-libs* packages.  Make sure you don't duplicate the work of existing packages! :)

Some of them are, yes. Before I build a package I always check to see if there is already something in /lib32 or /usr/lib32 (which has those ia32-* packages), in which case I change what other packages depend on appropriately. But I haven't even looked at these yet, so :)

---

### Post by skibrianski on 2007-05-11
> **dfreer said:**
> zsnes32 is compiled WITHOUT libao support, sorry about that everyone. that is why the sound is choppy. when compiled with libao, it segfaults. I suspect this is due to a dependency of libao that I must've missed. anyways, I'm working on figuring that out, as soon as I do I'll put a new version up. the 32-bit version runs SUPER smooth, the two are the same other than that libao support.

Ah ok. Just curious.

> **dfreer said:**
> as for the libraries skibrianski, yeah I noticed that you seemed to be missing a bunch of depends.

yeap. those are in the todo list I mentioned before.

> **dfreer said:**
> yeah, half of those will be used in firefox32 so it'll help alot.

nice!

> **dfreer said:**
> EDIT: BTW, skibrianski, I haven't put your .debs in because I'm waiting to test them first with mplayer32.

Makes sense to me. I don't want anything in the repo until it actually works for something :) I think it's important to get it right the first time on this one. The other concern I have is with various .debs that have been uploaded here - we'll need to figure out which of these packages conflict with the stuff in our repository and add conflicts to the DEBIAN/control file... The alternative is to say "if you want to use this repo, you need to nuke /usr/lib32 and /lib32 first", which would suck until we get all the programs we want running.

---

### Post by dfreer on 2007-05-11
> **skibrianski said:**
> The other concern I have is with various .debs that have been uploaded here - we'll need to figure out which of these packages conflict with the stuff in our repository and add conflicts to the DEBIAN/control file... The alternative is to say "if you want to use this repo, you need to nuke /usr/lib32 and /lib32 first", which would suck until we get all the programs we want running.

not quite sure what you mean. I have been using the official ia32-libs/lib32 packages whenever they are needed, and have been only uploading libraries that are not included in the official repo. For example, pSX32 depends on ia32-libs, ia32-libs-sdl, ia32-libs-gtk, ia32-libs-gtkglext1, the first three are in the official repos and the last I had to repackage from libsgtkglext1. If they are not in the official repos there should be no conflicts.

(I need to change the name of that last package to lib32gtkglext1 to be consistent. I've probably changed zsnes and pSX package names 3 times while learning all of this :oops: )

Or perhaps you are talking about people who have already installed a 32-bit package of firefox, mplayer, and so forth? Yeah, I see what you mean. I'll put a note that all previous 32-bit packages should be uninstalled (by searching for lib32 and ia32 in synaptic). You *don't* want to nuke /usr/lib32/ and /lib32/ unless you know what you are deleting, because I know that nvidia automatically installs 32-bit libraries in there when installing any of it's drivers. There may be others.

Perhaps I should just put a note that says this is designed for fresh installations of AMD64, and it *may* not work for people who have already tried install 32-bit programs?

---

### Post by skibrianski on 2007-05-11
> **dfreer said:**
> Or perhaps you are talking about people who have already installed a 32-bit package of firefox, mplayer, and so forth?

Yes, precisely.Although come to think of it, if we name the applications in a consistent manner, won;t thigs just work? IE, if you have an existing mplayer32 package, and you apt-get install our versio, it will first have to remove your old package, won't it? Same would go for firefox32. *shrug* we'll burn that bridge when we get there I guess. Doesn't bother me because I am happy with my 32 bit chroot for the moment.

> **dfreer said:**
> You *don't* want to nuke /usr/lib32/ and /lib32/ unless you know what you are deleting, because I know that nvidia automatically installs 32-bit libraries in there when installing any of it's drivers. There may be others.

Yeah, there almost certainly are, particularly in more server-esque environments, and we don't want to mess with that. We could add a preinst script that says something like - if any of the files i'm about to install already exist, prompt the user for what they want to do.

> **dfreer said:**
> Perhaps I should just put a note that says this is designed for fresh installations of AMD64, and it *may* not work for people who have already tried install 32-bit programs?

I think that's probably the right thing. But it doesn't have to be a "fresh" install as long as people make sure to uninstall any 32 bit programs they have installed with dpkg by hand outside of apt.

---

### Post by skibrianski on 2007-05-11
3 libraries to go  for mplayer32-nogui .... Hopefully mencoder32 and mplayer32 won't have too many more dependencies...

---

### Post by skibrianski on 2007-05-12
Ok, mplayer32-nogui now works. You can get the package and all it's dependencies here:
  [http://gadgets.xml-comma.org/ubuntu32-on-64/index.html](http://gadgets.xml-comma.org/ubuntu32-on-64/index.html)

To avoid conflicting with mplayer (64 bit), I install config files in /etc/mplayer32 . If there is no file /etc/mplayer at install time, we symlink /etc/mplayer -> /etc/mplayer32 (and we clean up in postrm) - otherwise we leave it alone assuming that you want to use the mplayer configuration that you've been using in the past (I think this assumption is fair). This seems to work quite well, but I'm happy to hear other suggestions for how to deal with this.

Tomorrow I'll probably bang out mencoder32 and mplayer32 (with gui)... Until then, yay :)

---

### Post by dfreer on 2007-05-12
yay! gonna try this out ASAP (ASAP hopefully being tonight), and add it to the repo for all to enjoy if things go well.

---

### Post by dfreer on 2007-05-12
ok, added the section "testing" so that we can actually apt-get the packages. Here's a problem I've noticed:

The mplayer32-nogui package is wanting to overwrite the mplayer configuration files (these in particular):
```
$ sudo dpkg --contents ./mplayer32-nogui_1.0~rc1-0ubuntu9_dfreer-1_amd64.deb 
drwxr-xr-x ski/ski           0 2007-05-12 16:16 ./
drwxr-xr-x ski/ski           0 2007-05-12 16:12 ./usr/
drwxr-xr-x ski/ski           0 2007-05-12 16:13 ./usr/bin/
-rwxr-xr-x ski/ski     8168988 2007-04-10 04:21 ./usr/bin/mplayer32
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/man/
drwxr-xr-x ski/ski           0 2007-05-12 16:14 ./usr/share/man/man1/
-rw-r--r-- ski/ski       89877 2007-04-10 04:21 ./usr/share/man/man1/mplayer32.1.gz
drwxr-xr-x ski/ski           0 2007-05-12 16:15 ./usr/share/doc/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/doc/mplayer32-nogui/
-rw-r--r-- ski/ski        1069 2007-04-10 04:06 ./usr/share/doc/mplayer32-nogui/copyright
-rw-r--r-- ski/ski        4066 2007-04-10 04:06 ./usr/share/doc/mplayer32-nogui/changelog.Debian.gz
-rw-r--r-- ski/ski        3820 2007-02-02 22:59 ./usr/share/doc/mplayer32-nogui/Copyright
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/doc/mplayer32-nogui/examples/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/doc/mplayer32-nogui/examples/etc/
-rw-r--r-- ski/ski        1095 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/mplayer.ico.gz
-rw-r--r-- ski/ski        1911 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/mplayer.xpm.gz
-rw-r--r-- ski/ski       13010 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/codecs.conf.gz
-rw-r--r-- ski/ski        2488 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/input.conf
-rw-r--r-- ski/ski        3333 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/menu.conf
-rw-r--r-- ski/ski        3068 2007-04-10 04:06 ./usr/share/doc/mplayer32-nogui/examples/etc/example.conf
-rw-r--r-- ski/ski        1200 2007-04-10 04:06 ./usr/share/doc/mplayer32-nogui/examples/etc/mplayer.desktop
-rw-r--r-- ski/ski        2818 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/dvb-menu.conf
-rw-r--r-- ski/ski          91 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/inttypes.h
-rw-r--r-- ski/ski       40333 2007-02-02 22:59 ./usr/share/doc/mplayer32-nogui/changelog.gz
[B][B]drwxr-xr-x ski/ski           0 2007-05-12 18:45 ./usr/share/mplayer/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/mplayer/font/[/B][/B]
drwxr-xr-x ski/ski           0 2007-05-12 18:45 ./usr/lib32/
-rw-r--r-- ski/ski      215924 2007-04-10 04:21 ./usr/lib32/libdha.so.1.0
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/lib32/mplayer/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/
-rw-r--r-- ski/ski        7476 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/pm3_vid.so
-rw-r--r-- ski/ski       28596 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/sis_vid.so
-rw-r--r-- ski/ski       13004 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/mach64_vid.so
-rw-r--r-- ski/ski       24308 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/radeon_vid.so
-rw-r--r-- ski/ski        8892 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/unichrome_vid.so
-rw-r--r-- ski/ski       19728 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/rage128_vid.so
-rw-r--r-- ski/ski       10360 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/mga_vid.so
-rw-r--r-- ski/ski       11168 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/mga_crtc2_vid.so
-rw-r--r-- ski/ski       11936 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/savage_vid.so
-rw-r--r-- ski/ski       11612 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/cyberblade_vid.so
-rw-r--r-- ski/ski       11608 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/nvidia_vid.so
drwxr-xr-x ski/ski           0 2007-05-12 16:16 ./etc/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./etc/mplayer32/
-rw-r--r-- ski/ski        2488 2007-02-02 23:00 ./etc/mplayer32/input.conf
-rw-r--r-- ski/ski        3333 2007-02-02 23:00 ./etc/mplayer32/menu.conf
-rw-r--r-- ski/ski        3068 2007-04-10 04:21 ./etc/mplayer32/mplayer.conf
**[B]lrwxrwxrwx ski/ski           0 2007-05-12 18:45 ./usr/share/mplayer/subfont.ttf -> ../fonts/truetype/ttf-bitstream-vera/Vera.ttf**[/B]
lrwxrwxrwx ski/ski           0 2007-05-12 18:45 ./usr/lib32/libdha.so.1 -> libdha.so.1.0

```

Removing this directory works fine, I tried it with danmplayer-nogui (in the testing repo as well)

EDIT: Also all files need to be changed to the appropriate owner BEFORE built in the package, see the above user/groups? namely, root.

---

### Post by skibrianski on 2007-05-12
I made a package of mplayer32 (with gui). It either doesn't work or I don't know how to use it tho (I always use the nogui port).

When I start gmplayer32, I get the error:
  New_Face failed. Maybe the font path is wrong. Please supply the text font file (~/.mplayer/subfont.ttf)

Does that mean anything to anyone and/or is it expected behavior?

---

### Post by skibrianski on 2007-05-12
> **dfreer said:**
> ok, added the section "testing" so that we can actually apt-get the packages.

Sweet!!! :)

> **dfreer said:**
> Here's a problem I've noticed:

The mplayer32-nogui package is wanting to overwrite the mplayer configuration files (these in particular):
```
$ sudo dpkg --contents ./mplayer32-nogui_1.0~rc1-0ubuntu9_dfreer-1_amd64.deb 
drwxr-xr-x ski/ski           0 2007-05-12 16:16 ./
drwxr-xr-x ski/ski           0 2007-05-12 16:12 ./usr/
drwxr-xr-x ski/ski           0 2007-05-12 16:13 ./usr/bin/
-rwxr-xr-x ski/ski     8168988 2007-04-10 04:21 ./usr/bin/mplayer32
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/man/
drwxr-xr-x ski/ski           0 2007-05-12 16:14 ./usr/share/man/man1/
-rw-r--r-- ski/ski       89877 2007-04-10 04:21 ./usr/share/man/man1/mplayer32.1.gz
drwxr-xr-x ski/ski           0 2007-05-12 16:15 ./usr/share/doc/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/doc/mplayer32-nogui/
-rw-r--r-- ski/ski        1069 2007-04-10 04:06 ./usr/share/doc/mplayer32-nogui/copyright
-rw-r--r-- ski/ski        4066 2007-04-10 04:06 ./usr/share/doc/mplayer32-nogui/changelog.Debian.gz
-rw-r--r-- ski/ski        3820 2007-02-02 22:59 ./usr/share/doc/mplayer32-nogui/Copyright
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/doc/mplayer32-nogui/examples/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/doc/mplayer32-nogui/examples/etc/
-rw-r--r-- ski/ski        1095 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/mplayer.ico.gz
-rw-r--r-- ski/ski        1911 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/mplayer.xpm.gz
-rw-r--r-- ski/ski       13010 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/codecs.conf.gz
-rw-r--r-- ski/ski        2488 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/input.conf
-rw-r--r-- ski/ski        3333 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/menu.conf
-rw-r--r-- ski/ski        3068 2007-04-10 04:06 ./usr/share/doc/mplayer32-nogui/examples/etc/example.conf
-rw-r--r-- ski/ski        1200 2007-04-10 04:06 ./usr/share/doc/mplayer32-nogui/examples/etc/mplayer.desktop
-rw-r--r-- ski/ski        2818 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/dvb-menu.conf
-rw-r--r-- ski/ski          91 2007-02-02 23:00 ./usr/share/doc/mplayer32-nogui/examples/etc/inttypes.h
-rw-r--r-- ski/ski       40333 2007-02-02 22:59 ./usr/share/doc/mplayer32-nogui/changelog.gz
[B][B]drwxr-xr-x ski/ski           0 2007-05-12 18:45 ./usr/share/mplayer/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/share/mplayer/font/[/B][/B]
drwxr-xr-x ski/ski           0 2007-05-12 18:45 ./usr/lib32/
-rw-r--r-- ski/ski      215924 2007-04-10 04:21 ./usr/lib32/libdha.so.1.0
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/lib32/mplayer/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/
-rw-r--r-- ski/ski        7476 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/pm3_vid.so
-rw-r--r-- ski/ski       28596 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/sis_vid.so
-rw-r--r-- ski/ski       13004 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/mach64_vid.so
-rw-r--r-- ski/ski       24308 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/radeon_vid.so
-rw-r--r-- ski/ski        8892 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/unichrome_vid.so
-rw-r--r-- ski/ski       19728 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/rage128_vid.so
-rw-r--r-- ski/ski       10360 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/mga_vid.so
-rw-r--r-- ski/ski       11168 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/mga_crtc2_vid.so
-rw-r--r-- ski/ski       11936 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/savage_vid.so
-rw-r--r-- ski/ski       11612 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/cyberblade_vid.so
-rw-r--r-- ski/ski       11608 2007-04-10 04:21 ./usr/lib32/mplayer/vidix/nvidia_vid.so
drwxr-xr-x ski/ski           0 2007-05-12 16:16 ./etc/
drwxr-xr-x ski/ski           0 2007-04-10 04:21 ./etc/mplayer32/
-rw-r--r-- ski/ski        2488 2007-02-02 23:00 ./etc/mplayer32/input.conf
-rw-r--r-- ski/ski        3333 2007-02-02 23:00 ./etc/mplayer32/menu.conf
-rw-r--r-- ski/ski        3068 2007-04-10 04:21 ./etc/mplayer32/mplayer.conf
**[B]lrwxrwxrwx ski/ski           0 2007-05-12 18:45 ./usr/share/mplayer/subfont.ttf -> ../fonts/truetype/ttf-bitstream-vera/Vera.ttf**[/B]
lrwxrwxrwx ski/ski           0 2007-05-12 18:45 ./usr/lib32/libdha.so.1 -> libdha.so.1.0

```


I can reproduce that behavior, but I sure don't understand where those are coming from, they're not in the directory I'm building the package from.

> **dfreer said:**
> EDIT: Also all files need to be changed to the appropriate owner BEFORE built in the package, see the above user/groups? namely, root.

Oops :) I've fixed my scripts to do this, and will upload fixed packages in the morning.

---

### Post by skibrianski on 2007-05-12
> **dfreer said:**
> Removing this directory works fine, I tried it with danmplayer-nogui (in the testing repo as well)

Did you adapt this from mine? How did you do it? I must be too tired, because I see no such files, heh... Well if yours works, it works!

---

### Post by skibrianski on 2007-05-12
BTW I removed my hand-installed packages, added testing, did an apt-get update and apt-get install mplayer32-nogui and all worked as expected. :)

Who wants to volunteer to do firefox, flash, and java6?

---

### Post by LuisGMarine on 2007-05-13
I don't know much about what is going on, but I'm willing to be a test dummy.  Lol I have a nice partition set for only AMD-64 and I'm not concerned whether it breaks or not.  So keep me posted on where to sign up and how to be one of the gerbils.

---

### Post by dfreer on 2007-05-13
yeah, anyone can test out packages. thanks for offering LuisGMarine!! basically, follow the instructions at the beginning of this how to, add my repository, only replace this line:
```
echo "deb http://packages.dfreer.org feisty **main**" | sudo tee -a /etc/apt/sources.list
```
with this line:
```
echo "deb http://packages.dfreer.org feisty **testing**" | sudo tee -a /etc/apt/sources.list
```



skibrianski, I took the mplayer32-nogui package you made and installed it with apt-get, which gave me the error telling me about the overwrite. I then took your package, extracted it (either with the GUI or the "ar xv *package_name*" command), deleted the /usr/share/mplayer directory within, and then repackaged it as danmplayer32-nogui and added that to the repo as well so you could see it. both yours and mine should be in there under the names I mentioned. I don't know why you couldn't see those files in your directory but they are there in the package I downloaded from your server. 

I will try your regular mplayer32 package out here really quick. w00t!

From what I understand of it, winehq has finally gotten a AMD64 .deb out for the 32-bit package of wine, I might just set up my site to mirror that so wine should be taken care of. Since I haven't heard from anyone else and I am *fairly* confident I can handle the firefox32 and mplayer32 plugin for firefox, I will start work on that. Flash should be fairly simple as well so if I can I'll grab that too. Since java has it's new version and covers alot more ground than either flash or mplayer-plugin, I probably can't do that. Once again, I work from open to close at my work due to some people quiting ATM, so I am a bit stretched for time. But I will consider getting a firefox32 up a major priority in my spare time.

EDIT: Congrats!! although I have not done extensive testing, it plays a .wmv file for me as well as the 64-bit package. Now to see if we can get w32packages to install and see if a video file that is currently only playable on a 32-bit mplayer will work on your AMD64 32-bit package. I plan on adding this to the main repository very shortly (once I can really test it out). Could you explain to me what your preinst script does to the mplayer configuration files again? it seemed like you were linking the 32-bit package into the 64-bit folder?

---

### Post by skibrianski on 2007-05-13
> **dfreer said:**
> yeah, anyone can test out packages. thanks for offering LuisGMarine!! basically, follow the instructions at the beginning of this how to, add my repository, only replace this line:
```
echo "deb http://packages.dfreer.org feisty **main**" | sudo tee -a /etc/apt/sources.list
```
with this line:
```
echo "deb http://packages.dfreer.org feisty **testing**" | sudo tee -a /etc/apt/sources.list
```

Or, put them both in the same line (so you can still get zsnes while you test these packages:
```
echo "deb http://packages.dfreer.org feisty **main** **testing**" | sudo tee -a /etc/apt/sources.list
```

> **dfreer said:**
> 
skibrianski, I took the mplayer32-nogui package you made and installed it with apt-get, which gave me the error telling me about the overwrite. I then took your package, extracted it (either with the GUI or the "ar xv *package_name*" command), deleted the /usr/share/mplayer directory within, and then repackaged it as danmplayer32-nogui and added that to the repo as well so you could see it. both yours and mine should be in there under the names I mentioned. I don't know why you couldn't see those files in your directory but they are there in the package I downloaded from your server.

Bizarre. I was using dpkg-deb to extract, not raw ar or whatever gui you were talking about. I'll have another look at it today, maybe my lack of sleep contributed! In any event I'm happy for you to rename danmplayer32-nogui over mplayer32-nogui, just bump the dfreer version number probably.

> **dfreer said:**
> 
From what I understand of it, winehq has finally gotten a AMD64 .deb out for the 32-bit package of wine, I might just set up my site to mirror that so wine should be taken care of.

That's great news!

> **dfreer said:**
> 
Since I haven't heard from anyone else and I am *fairly* confident I can handle the firefox32 and mplayer32 plugin for firefox, I will start work on that.

After I make an mencoder32 package I'm happy with, I'm going to just start cranking out libraries needed for ffox32 &etc, so you can focus on the actual ffox32 package.

> **dfreer said:**
> 
EDIT: Congrats!! although I have not done extensive testing, it plays a .wmv file for me as well as the 64-bit package. Now to see if we can get w32packages to install and see if a video file that is currently only playable on a 32-bit mplayer will work on your AMD64 32-bit package. I plan on adding this to the main repository very shortly (once I can really test it out). Could you explain to me what your preinst script does to the mplayer configuration files again? it seemed like you were linking the 32-bit package into the 64-bit folder?

Yeah, it seems to "just work" for all the media files I throw at it too :) As for the preinst srcipt, the package itself puts its config in /etc/mplayer32 . So what the script does is looks and sees if you have an existing /etc/mplayer (presumably from a 64 bit install). If so, it leaves your config alone, but if not it symlinks /etc/mplayer to point at /etc/mplayer32 . There's no other way I can see to get the config working without rebuilding the actual binary, which is something I think we should avoid as long as we can.

---

### Post by skibrianski on 2007-05-13
Permissions have now been fixed so that your files aren't owned by me anymore :)

I also added proper Original-Maintainer fields for the few packages that didn't have one in the 32 bit version.

I've also bumped version numbers to dfreer-4 on all packages mostly for my convenience (would have bumped to 2 but libgpg32error-0 was already on -3 from some old changes).

As usual, new packages are available here:
  [http://gadgets.xml-comma.org/ubuntu32-on-64/index.html](http://gadgets.xml-comma.org/ubuntu32-on-64/index.html)

---

### Post by skibrianski on 2007-05-13
Mencoder32 is now up, and it "works for me" (TM):

[URL="http://gadgets.xml-comma.org/ubuntu32-on-64/dist/mencoder32_1.0~rc1-0ubuntu9_dfreer-1_amd64.deb"]http://gadgets.xml-comma.org/ubuntu32-on-64/dist/mencoder32_1.0~rc1-0ubuntu9_dfreer-1_amd64.deb
[/URL]

---

### Post by dfreer on 2007-05-13
somehow my message never got saved, weird.

umm so yeah I'll update the mplayer-nogui with my version. not a problem, although I really want to get rssh or something going here ASAP.

I normally grab the original i386 package from packages.ubuntu.com, extract it with the GUI, and extract the control.tar.gz and data.tar.gz files within, the control.tar.gz has the contents of the DEBIAN folder, and the data.tar.gz contains the file structure and all the files located within. There is also a debian version file, which needs to be deleted. From there, all I need to do is edit the control files (and a few others in DEBIAN/), and change the folder names. Then *sudo dpkg -b folder_name package_name* and that's it, heck of a lot eaiser for me but to each his own.

new versions of libs will take a little time to upload, mainly I want to get you on rssh and let you upload them to make sure it works.

BTW, I finally sorted out the problems with zsnes32/lib32ao2, and there is a shiny new .debs for anyone to try out in the "Testing" repo. In fact, I really need someone to check and make sure to do the following:
```
sudo dpkg -r zsnes32
sudo dpkg -r zsnes ## in case you still have an old version
sudo cp -Rv ~/.zsnes ~/.zsnesbackup
sudo rm -Rv ~/.zsnes 
sudo apt-get clean
sudo apt-get install zsnes32
ls -l ~/.zsnes/  ##please post the output of this last command
```
Then, fire up zsnes32 from either GUI or CLI and play a game (just need to start it up). make sure to post if you used GUI or CLI.
```
ls -l ~/.zsnes/  ##please post the output of this command again
```


The reason for this is that I have included a default zsnesl.cfg file in the package, so that libao and OSS are used for sound, and the sample rate is set to 48000hz. This will give everyone on AMD64 the best sound (at least from my testing). Anyways, I wasn't quite sure on how to set the user permissions and I want to make sure that it gets set correctly and that zsnes32 can write to that folder. anyways, yay for libao2 support and 2 devs at zsnes forums!
[http://board.zsnes.com/phpBB2/viewtopic.php?t=10096](http://board.zsnes.com/phpBB2/viewtopic.php?t=10096)

---

### Post by skibrianski on 2007-05-13
zsnes32 won't install out of testing repo:

```

$ sudo apt-get install zsnes32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32ao2
The following NEW packages will be installed:
  lib32ao2 zsnes32
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 600kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://packages.dfreer.org feisty/testing lib32ao2 0.8.6-1.1 [17.5kB]
Get:2 http://packages.dfreer.org feisty/testing zsnes32 1.510-1.4 [582kB]
Fetched 600kB in 8s (69.6kB/s)                                                 
Failed to fetch http://packages.dfreer.org/pool/feisty/testing/binary-amd64/Z/zsnes32_1.510-1.4_amd64.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by dfreer on 2007-05-13
that's weird. try sudo apt-get clean, then sudo apt-get update, then sudo apt-get upgrade/install zsnes32 (depending on if you have it installed already). 

btw, rssh is set up now. it uses sftp, and public/private key auth, so we will need to set up a account for all the devs (currently me and skibrianski are active, but anyone who want to help sure can become one! :D let me know). Anyways, PM me skibrianski what you want your login to be (in case you want a different username), and then I will set you up an account and instructions on how to use if you don't know how.

---

### Post by skibrianski on 2007-05-13
> **dfreer said:**
> that's weird. try sudo apt-get clean, then sudo apt-get update, then sudo apt-get upgrade/install zsnes32 (depending on if you have it installed already). 

Oh sorry, forgot to follow up - I'm not sure what happened, because I did something else for maybe an hour, then tried again, and everything just works.Probably just a hiccup somewhere... And I can verify that the sound choppiness problem is gone :)

PS - PM'd you re: access.

---

### Post by alanrr_sr on 2007-05-14
I have built (just repacked) acrobat and its dependency, but I can't host them. Anyone interested?

---

### Post by dfreer on 2007-05-14
alanrr_sr:
yep, pm me with a preferred username/public key and we can get you in as a dev.

---

### Post by dfreer on 2007-05-14
hey everyone:

I know I said I would take care of firefox32. but I really should focus on getting the dev section on the website ready first. I'm still willing to do firefox32, and actually I want to, I just think getting the server ready should come first. Because I'm really the only one that can do that job, whereas anyone can do firefox32. But I don't think it'll take me long to get the server ready, other than coding the php/testing.

as for mplayer32, it looks like it is coming along nicely! should have it in the main as soon as we know it works with w32codecs and it handles everything that mplayer on a 32-bit system would do. Still need testers!

---

### Post by dfreer on 2007-05-14
so... what do you guys think? :D

[http://packages.dfreer.org](http://packages.dfreer.org)

---

### Post by LuisGMarine on 2007-05-15
Looks very interesting!

So after messing around with getting my Ubuntu AMD64 and hacking away at some files I got this machine running better than I did when I had Ubuntu 32-bit.

So my question is , how do I get a titlte of a cool dev?  I want to help test these out, I'm on the process of adding them to my /etc/apt/sources.list, I would like to really learn what you guys are doing and help put out packages out there myself.  

So if you have the tutorials to get me started on the path to becoming one of your dev's let me know, after all it wont be the first time that I earn a title :( Points at the U.S Marine Corps avatar )

Thanks again!

-LuisGMarine

---

### Post by dfreer on 2007-05-15
well, to test basically just add the testing repository, install a package, and *use* it. To help and become a "developer" (really just a repackager but whatever I used the name developer and now it's stuck :) ), you just need to start repackaging a program that we need (firefox, mozilla-mplayer, skype, anything that 64-bit users need a 32-bit package of). If you read through this thread there is advice on what to call the package, where to put the files, and how to repackage it. I would start with these links:

[http://packages.ubuntu.com](http://packages.ubuntu.com)
[http://linuxdevices.com/articles/AT8047723203.html](http://linuxdevices.com/articles/AT8047723203.html)
[http://www.debian.org/devel/](http://www.debian.org/devel/)

I normally download the program you are interested in repackaging from that first link, make sure you are on a clean AMD64 Ubuntu Desktop install, and then repackage it for AMD64, leaving the depends field empty. When it installs, try running the binary from the commandline, it should spit out an error similiar to this one:
```
$ psx32-frontend 
psx32-frontend: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory
```

do a search for this file libpython2.5.so.1.0 on packages.ubuntu.com, and it will tell you which package owns this file (and also you can check if there is a AMD64 32-bit package already of it, plus you will need to check our repository to see if we have already repackaged that library).

When you finally have a package you would like to contribute to the repository, PM me and I'll tell you how to login to our repository and upload the packages. Good Luck and thanks for helping!!

---

### Post by skibrianski on 2007-05-17
Hey all. I won't have time to work any more on this stuff for probably a month, as work is getting very busy, but I just wanted to plug the scripts I wrote. The first makes converting an i386 package a breeze.
[http://gadgets.xml-comma.org/ubuntu32-on-64/dist/convert-386-lib-to-amd64-lib32.sh](http://gadgets.xml-comma.org/ubuntu32-on-64/dist/convert-386-lib-to-amd64-lib32.sh)

After finding what i386 package you need and downloading the sucker, just run the above script with the argument of the i386 deb, it moves all the lib files to lib32, gets rid of extraneous info, etc. and lets you edit the control file (I usually add _dfreer-$version) to the version and take a look at the libs to change libwhatever to ia32-libs-* or lib32*. then it writes out a .deb which you can test, no fuss no muss.

If you get something wrong (or need to edit something more complicated than a simple library), this script can come in handy:
  [http://gadgets.xml-comma.org/ubuntu32-on-64/dist/edit-control.sh](http://gadgets.xml-comma.org/ubuntu32-on-64/dist/edit-control.sh)

It lets you edit the control info in a .deb, then rebuild it without changing anything else. Useful for typos, forgetting to bump the version number, etc.

Good luck!

---

### Post by Johnny K on 2007-06-18
So I added the repository, but I'm not exactly sure how it works. Are the listings in synaptic now a combination of this repository and the main one or do  I have to do something special to access this repo?

---

### Post by dfreer on 2007-06-18
it should just combine everything in synaptic. do a search for zsnes or pSX, and you should find my packages (zsnes is in the official repos, but only version 1.42. pSX is not in the other repos at all, so if you can see it in synaptic you know things are working!)

---

### Post by Johnny K on 2007-06-18
> **dfreer said:**
> it should just combine everything in synaptic. do a search for zsnes or pSX, and you should find my packages (zsnes is in the official repos, but only version 1.42. pSX is not in the other repos at all, so if you can see it in synaptic you know things are working!)
Searches for "zsnes" and "psx" bring up nothing. packages.dfreer.org is listed in Software Sources.

---

### Post by Johnny K on 2007-06-19
I disabled/re-enabled the repository via Software Sources, and hit reload in Synaptic. That caused this error message to appear (but everything seems to be working fine):
```
W: GPG error: http://packages.dfreer.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC1E7EB75A22BD68
W: GPG error: http://ubuntu.beryl-project.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
```

---

### Post by dfreer on 2007-06-19
To fix the public key error for my site, type this command into the terminal:
```
wget http://packages.dfreer.org/5A22BD68.gpg -O- | sudo apt-key add -
sudo apt-get update
```

To test it, you could also try this:
```
sudo apt-cache search psx
```

It should bring the pSX link up. What are you trying to download anyways? if this doesn't work I could always provide a direct link ;)

---

### Post by Johnny K on 2007-06-19
I typed the wget into the terminal. Everything installs fine, but for some reason I get this error message whenever I do Synaptic > Origin > packages.dfreer.org and click reload.
```
W: GPG error: http://ubuntu.beryl-project.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
```
But like I said, everything works fine. Is it something I should worry about?

---

### Post by McTek on 2007-06-19
Need flash and java

---

### Post by dfreer on 2007-06-19
sorry, development has slowed as of late. I haven't been able to get any new packages up on the site, although i will soon!
In the meantime, you can install them using ubuntu guide, check the edgy version if the feisty version does not have the how-to (I know edgy does :D )

---

### Post by BobCFC on 2007-07-03
Woot!  Now I can play my 16bit snes games on a 32bit emulator on a 64bit OS :biggrin:


I'm new to 64bit.  Are there any implications I should know about? I know that 32bit Firefox has lots of side-effects.

I'm not worried about extra libraries because I have RAM to burn, I just don't want it to get icky. (I think that is the technical term)

---

### Post by dfreer on 2007-07-04
well, it depends on how you install 32-bit firefox. 
With the ZSNES package, all libraries and the program itself are *.debs, which means they can be easily installed/removed/upgraded, with no "icky" libraries.
I've been busy like i said (just moved the server from a 500 mhz machine to a 2.6 Ghz yesterday!), but I'm hoping to get a 32-bit package of firefox available for AMD64 users soon. Just keep checking back, or subsribe to this thread, I'll post when it becomes a reality :)

---

### Post by caryb on 2007-07-04
I can't get the key to download! I get this... 
cary@stinkpad:~$ wget [http://packages.dfreer.org/5A22BD68.gpg](http://packages.dfreer.org/5A22BD68.gpg) -O- | sudo apt-key add -
[sudo] password for cary:--20:42:02--  [http://packages.dfreer.org/5A22BD68.gpg](http://packages.dfreer.org/5A22BD68.gpg)
           => `-'
Resolving packages.dfreer.org... 66.209.138.18
Connecting to packages.dfreer.org|66.209.138.18|:80...  


Cary

---

### Post by dfreer on 2007-07-04
I just moved the server, and in the process had to make a new GPG key (for some reason I couldn't get the old one to transfer, it kept giving me errors). Anyways, all of the how-to's have been updated with the new command to get the key, here it is again:
```
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
```

---

### Post by caryb on 2007-07-04
I might have to give it a couple of days for the DNS to refresh your new IP address this side of the world:-(



Cary

---

### Post by dfreer on 2007-07-04
Hmmm. IP address shouldn't have changed, but maybe there is a problem elsewhere in the system. I'll see what I can dig up...

EDIT: it's now, it appears that when it rebooted, several things went bad:
(1). the internet interface didn't bind to it's specified static IP address, say 192.168.3.5
(2). Then, when it went looking for an IP address from my router, the router should've given it the same address (It should've reserved 192.168.3.5 for that paticular MAC address). However, it gave it an IP address from the pool instead, which means port forwarding no longer worked correctly.

The router is a little picky, and I think it just needs reset in order to recognize the reserved IP address. The bigger question is why the server ignored my /etc/network/interfaces file which specified a static IP address for it in the first place. Must be something to do with the Debian installation process. Anyways, I'll keep checking it perodically until I know the problem is fixed.

---

### Post by AmyRose on 2007-07-09
So is it OK to use this repo on a 32-bit x86 installation?

---

### Post by dfreer on 2007-07-09
Yes, it has some packages (specifically zsnes and pSX) that are for 32-bit. You add the repository the same way for either architecture. Of course you won't be able to install the AMD64 packages, but you won't need them anyways ;)

---

### Post by bmhm on 2007-07-29
[FONT="Verdana"]Hi,

I installed zsnes32 properly from your repros. Well, this happens:

```
(bmhm@sentinel)[~] $ zsnes32
zsnes32: error while loading shared libraries: libartsc.so.0: cannot open shared object file: No such file or directory
```

Have you forgotten some dependencies?[/FONT]

---

### Post by dfreer on 2007-07-29
Wow, haven't heard anything about this before. I can add it as a dependency, but can you give me some information about your system, is it a default install and have you made any major modifications?

Here's some information about the package that would be needed.
[http://packages.ubuntu.com/edgy/libs/libartsc0](http://packages.ubuntu.com/edgy/libs/libartsc0)
I don't know quite why this error would pop up (zsnes shouldn't use aRTs at all), but I'll try to get a package for you ASAP for you to test. It may be an edgy-only dependency that simple hasn't been noticed before.

---

### Post by hendricks on 2007-07-31
Is the server down? I can't connect to [http://packages.dfreer.org](http://packages.dfreer.org).  I get connection time outs when running the command

```
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
```

 -Hendricks

---

### Post by jw5801 on 2007-07-31
Yeah it is, dfreer is updating some stuff I believe.
[http://ubuntuforums.org/showthread.php?t=394097&page=11](http://ubuntuforums.org/showthread.php?t=394097&page=11)

---

### Post by mmxbass on 2007-08-12
Can we get zsnes 1.42 added as well as an alternative to 1.51?

Zsnes 1.51 has alot of timing issues with some of the special chips making games like Mario RPG and Star Ocean unplayable in some sections. (Try to make it 2 minutes past the battle with Jonathan Jones in Mario RPG without having emulation crash to see what I'm talking about.) Furthermore, 1.42 is still the de facto standard for netplay with zsnes.

---

### Post by dfreer on 2007-08-13
Yeah, 1.51 doesn't support netplay, but netplay doesn't *really* work that well in 1.42, so I never regretted leaving 1.42 behind. Here's hoping they get a new release out that has a functional netplay soon!
I haven't heard this timing issue before, very interesting. That definitely seems worth getting an AMD64 package of zsnes 1.42 in my repo, hmmm. I might be building it on debian first, and then give it a try for Ubuntu. 
Well, no promises as to when, and you might have to prod/poke me to remind me to do it, but I'm definitely game. Anyone have any objections to include libsdl1.2debian-oss as a dependency, or at least a recommended package? Basically, I try to make my packages work good without needing configuration, and 1.42 has really scratchy sound. This package generally helps with 1.42.

EDIT: BTW, this is still an older release of ZSNES, so you will need to either download the .deb manually and install it, or you will need to lock the version number so that apt-get will not update it to the newest version if you use my repository. For people who like 1.51, this will not affect you in any way ;)

---

### Post by mmxbass on 2007-08-13
You could always make it a separate package entirely. Just give it a different name and add a "conflicts with" to the current version. There are packages in the main repository that do that as it is.

---

### Post by dfreer on 2007-08-13
perhaps zsnes-legacy, or zsnes-netplay? Good idea, not a problem!

Not sure if I want it called zsnes1.42, or something like that (think php4, php5, etc), simply because the newest package has no number following zsnes. This would get confusing if a user is only looking at the package names (as in what's newer, zsnes v1.52 or zsnes1 v1.42?). But legacy or netplay should probably work. Since the package is not done yet, there can be a discussion, and if anyone who has been paying attention knows, I have an annoying habit of changing package names/version numbering schemes whenever I feel the urge ;)

---

### Post by mmxbass on 2007-08-13
I like the zsnes-legacy package name idea.

---

### Post by fakie_flip on 2007-09-15
I'm looking for this version of Zsnes. It is the last snapshot that allows network play for Zsnes.

[http://nsrt.edgeemu.com/forum/viewtopic.php?t=448](http://nsrt.edgeemu.com/forum/viewtopic.php?t=448)

Help! It seems impossible to get it working in 64 bit.

---

### Post by cwrann on 2007-09-16
I am impressed by the effort made for the 64 bit user. I am not a gamer but I installed zsnes because you had it. 
Now that I have it where do I get the games that play on it?

---

### Post by Mochtroid-X on 2007-09-16
You will have to own and rip the data from the SNES cartridges yourself, otherwise it is illegal.

---

### Post by dfreer on 2007-09-16
@Everyone interested in a legacy netplay package
So, if I create a zsnes-legacy package, would the specific version (a wip build of 1.43 I do believe, before they scrubbed netplay and moved to 1.51) mentioned by fakie_flip be the best one to make? 

A binary is now available for anyone who wants to try it, shouldn't need anything special installed on AMD64 feisty ubuntu desktops:
 [http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes_1.42-wip](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes_1.42-wip)
Seems to be working ok so far, I have no idea about netplay though.

EDIT: Wow, 4 weeks already? Sorry hexnet, that I didn't  start working on this till now :redface:
FURTHER EDITING: It appears they have named this particular version 1.42n, if I'm not mistaken. I know the zsnes community has a very *ahem* enthusiastic following and I do not wish to get on their bad side ;)

---

### Post by dfreer on 2007-09-22
So, before I go ahead and make a zsnes legacy package for netplay purposes, I need someone who is interested in it to test the binaries, to make sure it works correctly. You can find the binaries here:
[a wip that supposedly handles netplay the best]: [http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42n](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42n)
[official release of 1.42]: [http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes1.42)

As soon as I get some feedback I'll make the packages!

---

### Post by mmxbass on 2007-09-22
They both seem to be free of the timing problems that 1.51 has.

BTW, unrelated to zsnes but it effected my download: Your webserver reported the wrong MIME type for the binary. Firefox tried to open it as text the first time.

EDIT: Something to keep in mind. It is strongly recommended against doing netplay between two different versions in zsnes, even minor revisions. I strongly recommend putting both 1.42 and 1.42n for those users who have stubborn friends who refuse to upgrade from 1.42 to 1.42n (there are a good number of them).

EDIT 2: Maybe a zsnes-legacy and a zsnes-legacy-net (or zsnes-legacy-netplay)? To be honest I would probably end up installing both.

---

### Post by dfreer on 2007-09-22
Here ya go! Right now they are in my debian repository, you can download them manually here:
[http://packages.dfreer.org/pool/lenny/non-free/binary-amd64/Z/zsnes32-legacy-netplay_1.420n-1.0_debian-amd64.deb](http://packages.dfreer.org/pool/lenny/non-free/binary-amd64/Z/zsnes32-legacy-netplay_1.420n-1.0_debian-amd64.deb)
[http://packages.dfreer.org/pool/lenny/non-free/binary-amd64/Z/zsnes32-legacy_1.420-1.0_debian-amd64.deb](http://packages.dfreer.org/pool/lenny/non-free/binary-amd64/Z/zsnes32-legacy_1.420-1.0_debian-amd64.deb)

ASAP, I'll test to make sure that they run in a vanilla Ubuntu AMD64 installation, and then update the Ubuntu repository so that people can apt-get and install it.
Debian AMD64 users can of couse use apt-get right *now*:
```
sudo apt-get update
sudo apt-get install zsnes32-legacy
sudo apt-get install zsnes32-legacy-netplay
```

---

### Post by mmxbass on 2007-09-22
BTW, you know you can copy your feisty repo as a gutsy repo right now. I can vouch for at least all the zsnes32 packages as working as-expected in amd64 gutsy.

---

### Post by mmxbass on 2007-09-23
Legacy and legacy netplay packages end up conflicting with each other.

Selecting previously deselected package zsnes32-legacy-netplay.
(Reading database ... 154001 files and directories currently install              ed.)
Unpacking zsnes32-legacy-netplay (from .../zsnes32-legacy-netplay_1.              420n-1.0_debian-amd64.deb) ...
dpkg: error processing /home/mmxbass/zsnes32-legacy-netplay_1.420n-1              .0_debian-amd64.deb (--install):
 trying to overwrite `/usr/local/games/zsnes32/support.txt', which i              s also in package zsnes32-legacy
Errors were encountered while processing:
 /home/mmxbass/zsnes32-legacy-netplay_1.420n-1.0_debian-amd64.deb

EDIT: Also. zsnes32 and zsnes32-legacy seem to be trying to access the same default path for the configurating file.
For the record, 1.4x and 1.5x configuration files in zsnes are NOT mutually compatible.
You may want to change the default config paths in all of them.
Rather than letting it be ~/.zsnes/ you may want to do something like splitting the configs into different paths. ~/zsnes32/ ~/zsnes32-legacy/ and ~/zsnes32-legacy-netplay/

EDIT2:It is also important to keep not just the zsnes32 and zsnes32-legacy separate but also zsnes32-legacy and zsnes32-legacy-netplay as well. The reason for this is that it is often advisable for some games to set the "Percent to Execute" option for something other than 100. Many games run better with a setting of 150 for example. The problem is that netplay cannot function unless Percent to Execute is set to exactly 100. This is not a GUI settable option AFAIK. Separate configuration paths for all three versions is highly advised.

---

### Post by dfreer on 2007-09-26
Ok, newer versions are out for debian that solve the file conflict. I'm looking into whether there is a compile time argument I can pass, in order to avoid the configuration file conflict, or whether I'll have to modify the source code itself to solve this.

> **hexnet said:**
> BTW, you know you can copy your feisty repo as a gutsy repo right now. I can vouch for at least all the zsnes32 packages as working as-expected in amd64 gutsy.

If you can confirm that you tested the packages in a vanilla install of AMD64 Gutsy, I will create the gutsy repo. Specifically, I need to know which packages you tested out of this list:
[list]
[*]lib32gtkglext1
[*]lib32ao2
[*]psx32
[*]zsnes32
[*]psx32-frontend
[/list]
I will eventually test myself once I can update to Gutsy (On release, if not beforehand). I am also in the process of getting all of the various repos in sync with each other (Debian Lenny x86/x86_64, Ubuntu Feisty x86/x86_64).


EDIT: Looks like I can pass --with-zconf-path=PATH to modify the location of the user config files. Now to test whether it works or not!

---

### Post by cwrann on 2007-09-26
When I reload my repositories I get an error from this repository

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2: Sub-process bzip2 returned an error code (2)

```

---

### Post by dfreer on 2007-09-27
I just checked freeproxy.ca, the site is still up. Perhaps it was a temporary issue on your end, or you caught the server at a bad moment when I rebooted it yesterday. Either way, it should be fine now.

---

### Post by cwrann on 2007-09-27
For some reason I had two of your repositories with the same name checked I unchecked on and now it works fine.

---

### Post by aphirst on 2007-10-21
I noticed that your current gutsy repo may not be fully working yet: -

```
Failed to fetch http://packages.dfreer.org/dists/gutsy/Release  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas? Or, better yet, when will it be up and running/feisty compatible?
Thanks a bunch, the feisty repo served me well :P .

Edit: The feisty repos works fine in gutsy, just to confirm what someone earlier on said.

---

### Post by dfreer on 2007-10-21
I just put up the gutsy i386 repo last night, about to move on to gutsy amd64. After that, I plan on going back and getting a dapper and debian etch repo up. Then, if I haven't committed suicide, plans for edgy, feisty, sid, and improving the website (blargh, dead daniel day ;) )

---

### Post by aphirst on 2007-10-21
Good lard. I was just concerned, is all...

:S

Keep up your Great-Gig-In-The-Sky-ness. :D

Ah. The gutsy repo now works perfectly. Just got ultima's frontend. Immense.

(someone should give dfreer some kind of complimentary doughnut, or plate of waffles or something...)

[IMG]http://www.ekmpowershop.co.uk/ekmps/shops/tyrrell123/images/doughnut.gif[/IMG][IMG]http://biology.clc.uc.edu/graphics/maple/waffle.jpg[/IMG]

:popcorn: Thanks 'dude'. :D

---

### Post by dfreer on 2007-10-21
> **aphirst said:**
> 
Ah. The gutsy repo now works perfectly. Just got ultima's frontend. Immense.

(someone should give dfreer some kind of complimentary doughnut, or plate of waffles or something...)

[IMG]http://www.ekmpowershop.co.uk/ekmps/shops/tyrrell123/images/doughnut.gif[/IMG][IMG]http://biology.clc.uc.edu/graphics/maple/waffle.jpg[/IMG]


WAFFLES!!! *takes a break to chow down* Best "thank you" ever, at least until someone comes to my house and makes me some real ones :D

Yep, gutsy should be **completely done**, zsnes, psx, and Ultima's frontend should be running perfectly, both amd64 and i386. I'll get around to updating the thread/site later, for now I think I'm moving on getting feisty up to date.

---

### Post by jpkotta on 2007-10-22
Any plans to put mplayer32 in the gutsy repo?

---

### Post by rcsdnj on 2007-10-22
Hi dfreer,

About libao, you said: 

> **dfreer said:**
> zsnes32 is compiled WITHOUT libao support, sorry about that everyone. that is why the sound is choppy. when compiled with libao, it segfaults. I suspect this is due to a dependency of libao that I must've missed. anyways, I'm working on figuring that out, as soon as I do I'll put a new version up. the 32-bit version runs SUPER smooth, the two are the same other than that libao support.


I would like to know if are there any news about this. I'm experiencing this problem kind of often in Gutsy.

I also have a suggestion: have you tried to run zsnes32 with libao support disabling the data execute prevention (execute disable bit) feature? This feature is present in x86_64 processors and is made to avoid that programs try to execute areas in memory marked as being data (not-executable). I had a problem using the Mupen emulator under Ubuntu x86_64. It was segfaulting and I got to make it working by disabling this technology.

To stop , I first did it by going to the BIOS and disabled the "XD Technology" option. Since I didn't want to disable it globally, I looked for a way to disable and I found this:

- install prelink package ( sudo aptitude install prelink - I'm not sure about the package name, I'm not in my Ubuntu machine right now)

- run the executable you want to disable the XD technology by using:

execstack -s program_name

So, if this problem is a bug in ZSNES where it tried to execute data memory, maybe this is a solution, so you could provide a package with libao support (like zsnes_libao) and advice people about this.

I'm not saying this is the solution for the problem, but it's maybe a good test. You may be right about the dependency problem, also.

---

### Post by dfreer on 2007-10-22
zsnes32 has libao support now, I was able to resolve the issue (I had to include a repackaged libao2 library, for more information you can see this post: [http://board.zsnes.com/phpBB2/viewtopic.php?t=10096&highlight=](http://board.zsnes.com/phpBB2/viewtopic.php?t=10096&highlight=) ). Thanks for the info about the data execution prevention, perhaps this can resolve issues with random segaults on pSX and zsnes that some users have been reporting! When I get some time, I'll include that info in the FAQ.

Make sure to run zsnes with *-ad oss* the first time around to use libao, I believe it will use it automatically each time after that (I manually specify which driver to use in my ~/.zsnes/ conf file.)

@jpkotta - There was a time when I was working on getting a 32-bit firefox and 32-bit plugin of mplayer & flash into the repository, the original purpose of this thread. However, interest in the project slacked off, and I haven't had time to work on it alone due to my work in real life and projects like zsnes + pSX. 
Since I've been running gutsy, so far I haven't run into any videos that won't play in the 64-bit version of firefox though. Is there still a need for a 32-bit version?

EDIT: hmmm, I really should update the OP to reflect what's currently happening with this repository.

---

### Post by jpkotta on 2007-10-22
I think there's still a need for w32codecs.  I have a few videos that don't play with ffmpeg-based codecs, and I think the ffmpeg decoders don't give as good of a picture (you can really tell the difference between frames near a key frame (if that's the right term) and far from a key frame).  

Give me a quick guide to how you made the packages and I'll make them for Gutsy.

---

### Post by dfreer on 2007-10-22
skibrianski did most of the work, while I busied myself with setting up the repository/site (which I admit I never really fufilled my obligations, and didn't make things eaiser for skibrianski). 
He made a bunch of libraries using a script to go through premade x86 packages, you can find most of them and the script here:
[http://gadgets.xml-comma.org/ubuntu32-on-64/index.html](http://gadgets.xml-comma.org/ubuntu32-on-64/index.html)

At one point almost a year ago, I had made my own short how-to on getting 32 bit versions of firefox, mplayer, flash and java working without a chroot in edgy (largely borrowing from kilz work in the following thread:
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435) )

That's about all I can help you with :( I'm pretty good at repackaging, but firefox is a HUGE project. Also, there is another AMD64 repository in the x86-64 bit users forum that seems to have better support, it may be more useful to contribute your time+energy with them. I currently only provide hosting, I don't have any way for you to upload files or update the repository with changes, short of me manually downloading files and updating on my own. Another issue was lack of feedback and testers, we didn't even have the specific videos that only worked with 32-bit versions to test with! 

I'm not trying to discourage you, I'm all for improving linux. I just feel like this project of mine has died, and my pSX/ZSNES packages are the only things that survived out of it.

---

### Post by Limpan on 2007-10-23
I don't know if this is a known issue or not. I mean, I haven't decided if it actually is an issue, but when I install the zsnes32 package the folder /home/dfreer is created. I find it kind of annoying and maybe you could fix it in future releases? I really do appreciate the work and effort put into providing the repository and i apologize if this 'issue' is already known.

---

### Post by dfreer on 2007-10-23
I think someone already mentioned it once, you're using feisty right? I haven't gotten around to fixing the feisty packages, I just got finished with gutsy actually. Yeah, that really was a mistake compounded by another mistake:

Basically, what originally happened was that I included a default /home/$USER/.zsnes/zsnesl.cfg file, so that libao was used by default (improves sound quality). 
After a while, I decided that this isn't a optimal solution (it only works with a user account that uid was = 1000, and some users may not want to use libao), and removed it from every package that I updated. 
The reason why it is now showing up as /home/dfreer/ instead of /home/$USER (where $USER == uid of 1000), I suspect is due to my laptop upgrade (I had to backup files on a NTFS partition, and permissions got mucked around with).
Anyways, I'm going back and redoing all of the packages, so it will be fixed soon I promise (you may need to remove the directory manually). So sorry!

EDIT: **Feisty** is completely updated, both amd64 and i386. Have fun!

---

### Post by Limpan on 2007-10-24
I used Feisty when i realized the thing with the home folder but I have reinstalled with Gutsy since then. If it's been taken care of in Gutsy, it probably was created by the Feisty package. I have a vague memory of removing the folder but then I might have updated or reinstalled after that.

---

### Post by mmxbass on 2007-10-24
> **dfreer said:**
> Basically, what originally happened was that I included a default /home/$USER/.zsnes/zsnesl.cfg file, so that libao was used by default (improves sound quality). That cfg is still going to get overridden to nothing if you have zsnes32 and zsnes32_legacy and zsnes32_legacy_netplay since zsnes config files are incompatible between versions. (It replaces the file with it's built-in defaults if it's not what it's expecting.)

---

### Post by dfreer on 2007-10-24
Until I find a way to change the default path used by each version when compiling, those packages are pretty much junk. You could write a bash script wrapped around the executables to change which config file it uses, but only on a user-to-user basis (hmmm actually, since bash can use relative paths... it's possible to create a bash script to swap zsnesl.cfg's in and out depending on which version is being used... but I don't think I'm going to deal with that anytime soon).

---

### Post by Felson on 2007-10-25
I know you have pSX in there, but is there any chance of adding pcsx32 in there as well?
There is a native 64 bit version in the repositories, but it can't run 32 bit plugins. Pete has been missing from his forums since January, so it is unlikly we will see any 64 bit versions of his non-GPL plugins anytime in the near future. (These include his open GL stuff). Software rendering "sucks", not that his plugin is bad, I would just MUCH rather have my video card do it.

---

### Post by dfreer on 2007-10-25
Hmmm, I'm not opposed to adding pcsx, I'll just need to spend some time configuring it and figuring out it's dependencies. My main issue is plugins, so if there are any plugin's that work better than those included by default (can't remember if pcsx even had default plugins), can you post which ones you use, and links? Also which chipset your video card uses, I assume ATI and nvidia users will want different video plugins.

---

### Post by dfreer on 2007-10-26
How To install zsnes 1.51 on AMD64 thread just got approved:
[http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

So from now on, please direct any questions about zsnes in that thread, and questions about pSX in this thread:
[http://ubuntuforums.org/showthread.php?t=394097](http://ubuntuforums.org/showthread.php?t=394097)

This thread will be for the repository itself, and for any additional projects (32-bit libraries, 32-bit plugins, etc) that do not have a how-to dedicated to it. Thanks everyone!

---

### Post by Felson on 2007-10-26
oki doke

Video: (Soft and XGL are the main ones, I have never actualy used the other 2. May need to get input from others as to if they are needed or not)
libgpuPeopsSoftX
libgpuPeteXGL2
libgpuPeteMesaGL
libgpuPeopsSDL

Sound: (alsa/oss depending on your pref, null for those games that just don't work with sound)
[http://www.pbernert.com/html/spu.htm](http://www.pbernert.com/html/spu.htm)
libspuPeopsOSS
libspuPeopsALSA
libspuPeteNull

Game Pad: (I use OmniJoy, but only because it was the on I tried first, and it worked fine. Not sure if one is better then the other.)
libpadOmniJoy  [http://www.ngemu.com/plugins.php?cat=1&os=linux](http://www.ngemu.com/plugins.php?cat=1&os=linux)
libpadJoy  [http://www.ammoq.com/](http://www.ammoq.com/)

CD-ROM: (need this)
[http://mooby.psxfanatics.com/](http://mooby.psxfanatics.com/)
libcdrmooby

Generaly the links are to binaries, but some have source as well. These plugins are also usefull for ePSXe as well, but that one just doesn't work in Gutsy ATM anyway.
For source to petes stuff, (the ones that have source) go to:
[https://sourceforge.net/project/showfiles.php?group_id=39401](https://sourceforge.net/project/showfiles.php?group_id=39401)

---

### Post by dfreer on 2007-10-26
Alright, thanks alot! I'll work on this when I get a chance.

---

### Post by Felson on 2007-10-26
In my last post I mentiond that ePSXe doesn't work in Gutsy, but I think I solved it.
See my post at [here]("http://ubuntuforums.org/showthread.php?p=3639535#post3639535") if you are intrested.

Question for dfreer. Do you know if/which libs contain lib32gtk+1.2 and lib32glib1.2?

---

### Post by dfreer on 2007-10-26
I replied in the thread you linked to ;)

---

### Post by Felson on 2007-10-27
Thanks dfreer. Your reply leads to another request for an add to your repositories... :D

The gtk+1.2/glib1.2 stuff would be nice for some older apps/emulators

---

### Post by dfreer on 2007-10-27
I was already thinking about it, after reading that ePSXe thread. Added to my list of things to do.

---

### Post by aphirst on 2007-10-29
I have had zero problems to date with the installed programs from your repository; but I have a small question:

Do you intend to extend your support for these precompiled applications to other GNU/Linux OSs like Debian (probably wouldn't be too hard), or even Fedora? I ask out of pure curiosity, but it would probab.y make you look even more immense than you do at the moment (which I might add is still GODLKE :P).

:D

---

### Post by dfreer on 2007-10-29
Debian support has been slightly worked on, there is a Lenny "Testing" repo for AMD64 users in there. On my to-do list, I'm planning on updating all the packages for Debian Stable, Unstable, and Testing.
I worshipped the day that I left the dependency hell known as Red Hat/Fedora, so the chances of me making RPM packages are slim-to-none. Ok, things weren't THAT bad, but I think I'm just going to stick to debian based distros ;)

---

### Post by dfreer on 2007-10-31
Debian Etch i386 done (sorry, it appears that Ultima's Frontend may not work in Etch, eh). Also, lib32gtk1.2 and lib32glib1.2 are done ;)

---

### Post by crono141 on 2007-11-02
So mplayer32 has "died".

Damn shame.  I can't get any of my audio in WMA 10 pro to work on 64 bit linux, and I was directed here for a possible solution.

Any possibility of this starting back up?  Was the project almost finished anyway?

---

### Post by hobbes_ba on 2007-11-02
> **crono141 said:**
> So mplayer32 has "died".

Damn shame.  I can't get any of my audio in WMA 10 pro to work on 64 bit linux, and I was directed here for a possible solution.

Any possibility of this starting back up?  Was the project almost finished anyway?

Well... you can install it using the Mplayer script from Klitz on this post.

[http://ubuntuforums.org/showthread.p...ox+Flash+amd64](http://ubuntuforums.org/showthread.p...ox+Flash+amd64)

Too bad it is not the latest Mplayer RC2 from october, but it will work for you. I installed that way.

I guess that i have never encountered a WMV/WMA PRO file before...

Hope that helps.

---

### Post by dfreer on 2007-11-02
This is the how-to that I wrote for Edgy, largely based off of Kilz's script:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Firefox32_in_AMD64](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Firefox32_in_AMD64)

It looks like skibrianski's .deb's are no longer available (I'm getting a 404 error):
[http://gadgets.xml-comma.org/ubuntu32-on-64/index.html](http://gadgets.xml-comma.org/ubuntu32-on-64/index.html)

That's about all I have left. After moving from two servers and various reinstalls/hard drives crashes, I no longer have the .debs relating to mplayer32 on my site.

---

### Post by dfreer on 2007-11-06
@Felson and anyone interested in ePSXe/PCSX - 
So I spent a couple hours tonight, getting various plugins and such for the two emulators, and got them both running on my 64-bit gutsy. 
Although I'm not quite ready to make any packages (if I do make one, it'll probably be pcsx only), I can put up any files you may want (in particular, I had to compile the controller plugins on a 32-bit machine for PCSX, and I had to decompress the ePSXe binary with upx, and then install 32-bit versions of libgtk1.2 and libglib1.2). Just let me know if you are having issues getting these to work, and I can provide with the plugins/files you need, or just help you out in general ;)

Since I had the emulators working, figured I might as well give them a quick review:
Here's the plugins I tried out:

**Video**
[list]
[*]Pete's MesaGL Driver 1.1.76 - Ran mostly at full speed (50/59 FPS, depending on whether the game was PAL/NTSC), fullscreen with Filters on. VERY nice ;)
[*]Pete's XGL2 Driver 1.2.8 - Ran too slow in both emulators, didn't play around with it much since the MesaGL driver seemed to work pretty well.
[/list]

**Sound**
[list]
[*]P.E.Op.S. OSS Audio Driver 1.1.9 - seemed to work fine, didn't really play long enough to notice any problems.
[/list]

**Control Pad**
[list]
[*]OmniJoy Beta 1 1.1.0 **PCSX only**- Had to specify that my joystick was at /dev/input/js0 instead of /dev/js0. Easy to configure, but for some reason in every game, if I used the D-Pad on my Logitech Dual Action USB controller, it would go crazy and basically act like I was holding down up/down/left/right (depending on what I pressed).
Keyboard worked fine, although when mapping the keyboard, it took several presses in order for it to recognize that I had pressed a key. Dunno why.
[*]ammoQ's padJoy Joy Device Driver 1.0.8 **PCSX only**- Works fine for me, although I'm a bit confused as to what some of the buttons toward the bottom do (I assume they are for L3/R3 and analog sticks, at least the digital buttons are easy enough to figure out). Keypad also worked fine.
[*]Builtin Controller plugin **ePSXe only** - Didn't work with my USB controller at all, although it works decently with my keyboard and was the easiest to configure, with a nice picture of the playstation controller to help out.
[/list]

**CD Drive**
[list]
[*]Mooby2 cd disk image driver 1.2.8 **PCSX only** - Won't open .iso files, and actually complains if you give it a .ccd, .cue, or .mds file (although it will load the game correctly if it's a .cue). This means my backed up copy of Tomb Raider II won't work, and Jet Moto works, albeit without any music during a race.
I tried .bin/.img/.mdf images, and they all worked. I'll have to grab my original discs out of my closet sometime, especially Jet Moto and Tomb Raider II, and see if they work with music.
[*]Built-in CD Driver **ePSXe only** - Opens .iso, .bin, .img, and .mdf files. Can't open the matching subcode/header files like .cue, .ccd, .mds. Jet Moto and TRII have the same issues as listed above.
[/list]

**ePSXe** - Tested with Jet Moto, Final Fantasy VIII, Intelligent Qube, Tomb Raider III.
**Jet Moto**'s menu's have graphical glitches (flickering), and the actually gameplay is very rough. Although it's getting full FPS, it seems really sluggish, and laggy. As noted, there was no music during the race. The graphics during the race were amazing, quite an improvement over the original.
**Final Fantasy VIII**'s FMV played very smoothly, no hiccups. Didn't play any further than that. Graphics were the same as the original (probably because it was an FMV).
**Intelligent Qube** didn't quite run at full FPS, Jumping around between 40-50 fps although it didn't really affect gameplay. Music worked fine, with very minor hiccups when the fps dipped to 40 (not noticeable enough to be annoying IMO). Graphics weren't noticably different, but then again that game didn't really have any room for improvement.
**Tomb Raider III** ran just fine, with no issues (only tested her house).

**PCSX** - Tested with Jet Moto, Final Fantasy VIII, Intelligent Qube, Tomb Raider III.
**Jet Moto** had the same menu problems as when running it with ePSXe, although the gameplay was quite smooth, beautiful graphics and everything. Very nice, if it were not missing the music and the menu's worked correctly. Full FPS.
**Final Fantasy VIII**'s FMV was rough, seemed to be the audio and video would just skip for a sec every so often, maybe once every 10 secs. Pete's plugin was showing full FPS without any dips, so I'm not sure what the problem here was.
**Intelligent Qube** ran just fine, full FPS without any issues to report.
**Tomb Raider III** got a bit choppy whenever Lara would do a voiceover (tested in her house), but other than that ran fine.

I also tested **pSX** with the same games BTW, and had full FPS and no issues to report. pSX runs .bin, .mdf, .iso, .img, plus all of the relevent files like .ccd, .cue, .mds. Tomb Raider II runs, and Jet Moto has sound during the races. Controller configuration works, although dualshock only seems to work in games that use it, games that don't may not accept controller input unless digital mode is selected, and analog+rumble just plain doesn't work at all. No plugins to configure, but no upgraded graphics either.

---

### Post by Felson on 2007-11-06
Nice review dfreer. One thing though... ePSXe doesn't support any controllers "out of the box" in Linux.  If you look at the menu, there is an "Ext. Game Pad" option. That lets you pick/use one of the plugins you used in PcSX. 

I think I may be switching to MesaGL plugin now though :D Never used it before. 

I have never really had much luck with pSX, not really sure why.

Another 32bit app that would make a nice home in your repositories would be "gens" only emulator I can find that plays Sega-CD games from iso/mp3 sets. XE & MESS just don't seem to like them at all.

---

### Post by dfreer on 2007-11-06
LOL @ myself, I can't believe I missed that, must have been the "Ext." that through me off. Thanks a bunch!

---

### Post by Felson on 2007-11-06
That option isn't there in Winblows at all. I wish the built in pad support worked under Linux. The UI for the built in one looks nicer then either of the plugins.

---

### Post by Felson on 2007-11-06
Another 32bit lib request....
libgtkhtml2-0
I have been trying to find a yahoo chat that does voice/video. 
I tried the yahoo one, and it was no good, and now I am on to Gyachi. Seems to be fine, but if you compile it in 64bit you don't get voice chat. So I installed the 32bit deb by hand. Anywho both Gyachi and ymessenger want that libgtkhtml, so it might be a bit common. 
Also... I do know a thing or 2 about Linux, just not much about making DEBs. If you are interested in someone to help make/update your repository, I am game, just point me to a good how-to for debs and I would be happy to help.

---

### Post by dfreer on 2007-11-06
Yep, I'll give you the link that Kilz originally pointed me to. It's not the correct way of making .debs, but it works for me. I'm always willing to help, and it's also helpful to extract a pre-existing .deb file and analyze it's contents.
[http://linuxdevices.com/articles/AT8047723203.html](http://linuxdevices.com/articles/AT8047723203.html)

I'll check out libgtkhtml2-0 in the meantime.

EDIT: doesn't look too bad, although I'll probably have to include a 32-bit version of libatk1.0-0, and possibly libgail18.

---

### Post by unebaguettesvp on 2007-11-11
is anybody else getting lagging sound with zsnes? everything else works fine including the sound. it just delays by a second. maybe two.

---

### Post by mmxbass on 2007-11-11
> **unebaguettesvp said:**
> is anybody else getting lagging sound with zsnes? everything else works fine including the sound. it just delays by a second. maybe two.Try tweaking both the sound buffer settings and the "percent to execute" setting in the config file.

---

### Post by dfreer on 2007-11-11
Beyond that, you can also try changing the sampling rate to 48000 hz, and if you aren't already running with libao, try that.

Also, if your framerate is low (<30 FPS or so), you may get lagging sound.

---

### Post by unebaguettesvp on 2007-11-12
thanks to both of you!!! changing libao to alsa fixed the problem!

---

### Post by dfreer on 2007-11-12
> **unebaguettesvp said:**
> thanks to both of you!!! changing libao to alsa fixed the problem!

BTW, I have a thread specifically for zsnes now (see sig), which covers installing zsnes and running with libao ;)

---

### Post by dfreer on 2007-11-13
@Felson - lib32gtkhtml2-0 is now available for download in the Gutsy repository, or manually here:
[http://packages.dfreer.org/pool/gutsy/main/binary-amd64/lib32/lib32gtkhtml2-0_2.11.1-3.0_gutsy-amd64.deb](http://packages.dfreer.org/pool/gutsy/main/binary-amd64/lib32/lib32gtkhtml2-0_2.11.1-3.0_gutsy-amd64.deb)

EDIT: Let me know how it works. I didn't package any dependencies, so if there is a problem I'll go ahead and make those as well.

---

### Post by Felson on 2007-11-13
Awesome. Nice work.

---

### Post by dfreer on 2007-11-16
For anyone interested, I have skype32 in the Gutsy AMD64 repository now. It's the statically linked version of the Beta release (2.0.0.13), I will upgrade it to the dynamically linked version as soon as I get around to repackaging the QT libraries.

But you can go ahead and download the current version, it works great for me so far:
```
sudo apt-get install skype32
```

Best part about the beta? I can finally use my intergrated webcam in my laptop, which has been working properly since feisty but I didn't have any apps to use it with till now :(

---

### Post by Felson on 2007-11-29
@Dfreer
I have another candidate for your 32bit for 64 bit libs :D
libstdc++2.10-glibc2.2
Used by EternalSPU for ePSXe/PcSX

---

### Post by dfreer on 2007-11-30
Sorry felson, for not replying. I'm working on it, should be easy since it only depends in libc6. Just haven't got around to it yet.

---

### Post by Felson on 2007-11-30
:) np. 
I just used the harder way in my How-To for now. Not really a big deal, I just think it's better to use a repo, so that when things need to be updated, you don't need to remember every single little package you installed bu hand and update them. Instead, you leave it up to some guy that decided to take on the huge task himself :p 
(on that note, thanks for taking up the task)

---

### Post by dfreer on 2007-11-30
Here ya go:
[http://packages.dfreer.org/pool/gutsy/main/binary-amd64/lib32/lib32stdc++2.10-glibc2.2_2.95.4-3.0_gutsy-amd64.deb](http://packages.dfreer.org/pool/gutsy/main/binary-amd64/lib32/lib32stdc++2.10-glibc2.2_2.95.4-3.0_gutsy-amd64.deb)
It's also available via apt-get, as usual. Your welcome!

---

### Post by wingnux on 2008-02-22
[http://packages.dfreer.org](http://packages.dfreer.org) is off-line =/

---

### Post by dfreer on 2008-02-22
> **wingnux said:**
> [http://packages.dfreer.org](http://packages.dfreer.org) is off-line =/

Just got a new ISP, with better bandwidth. Unfortunately I found out today that they block port 80. So I'm working on figuring out dyndns's port redirection stuff, until I do the server will be offline.

If there is specific packages that you need, I will try to work something out and get them to you.

---

### Post by Felson on 2008-02-22
Why not just set up on port 8080, and tell everyone that your URL is [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080)? Might be easier then dyndns stuff.

---

### Post by dfreer on 2008-02-22
> **Felson said:**
> Why not just set up on port 8080, and tell everyone that your URL is [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080)? Might be easier then dyndns stuff.

That's exactly what I did, so as of now, **the server is up and running on port 8080**. However, I need to test and see whether that's going to affect people using apt-get, and then of course update all of the old links :(

But the optimal solution would be to get a web redirect working where all traffic to the dfreer.org domain is routed to port 8080, so that all the old links would still work. I'm struggling with that right now, hopefully I will figure it out soon. In the meantime, use port 8080.

---

### Post by jw5801 on 2008-02-23
Hey dfreer,

The server works fine if I change the entry in /etc/apt/sources.list to add the :8080 to the line, then get the gpg key again from port 8080, so if you change the initial installation instructions to specify the port in the command to get the gpg key and the sources.list entry then everything works awesomely!

---

### Post by NullHead on 2008-02-25
Good idea, this project that is. 

The website doesn't seem to work :shock: I haven't tested the repository yet, but you could always think of hosting your website on a free web hosting site, such as [http://freehostia.com](http://freehostia.com) or [http://freewebs.com/](http://freewebs.com/) ... I host my site on freehostia.com and it's always up and working. 

Do you have a list of packages that are in the repository? I seen the list on your OP, but is it updated for the packages in the repository?

---

### Post by dfreer on 2008-02-26
*sigh* had another hard drive go down, one I just replaced at that. Non-essential, but I couldn't fix the thing right away. Be back soon /wrists

The website does far more than what any free web hosting service would be willing to handle, so that's not going to help me. As for the list of packages, the website's main page [http://packages.dfreer.org](http://packages.dfreer.org) has the most up-to-date list, but even that's probably missing a few packages.

---

### Post by NullHead on 2008-02-26
hmm ... a dead hdd would probably trash my whole week .. and it's a new one at that! Well you might think about accepting donations to help purchase new things, like new hdds.

---

### Post by dfreer on 2008-02-27
> **NullHead said:**
> hmm ... a dead hdd would probably trash my whole week .. and it's a new one at that! Well you might think about accepting donations to help purchase new things, like new hdds.

Yeah, the hard drive that errored I happen to use with bittorrent, so all of the files that are on there are just things I recently downloaded, and isn't anything important (the important stuff is on RAID5). However, when it went down and the server rebooted, it caused the system to lock up (not sure if anyone knows what I'm talking about, but basically has something to do with a file system check option set in /etc/fstab). 

I couldn't log into the machine to fix it with SSH, and since the server is headless I had to wait a couple of days before I could grab a monitor/keyboard to log into the thing physically. Lame. It's back up, yet again.

As for donations, my server is really used for personal use, and the website/repository/packages are just something I set up on the side. I wouldn't feel right asking for donations, especially considering my recent lack of involvement in the Ubuntu Scene :D

---

### Post by NullHead on 2008-02-28
Well apparently your website isn't up. I haven't tried your repository though. 

The only hdd I've had die is the main one I was using at the time (user for testing linux distros) and the system just froze, but I was listening to music at the time and it was still playing after the hdd died :lolflag:

---

### Post by dfreer on 2008-02-28
*bashing head against the wall*

I probably shouldn't be allowed to run a web server :( I simply forgot to add the new port 8080 to my firewall, and it took me a day to realize that.

---

