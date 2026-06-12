---
title: "Audacious 2.0.1 32 bit install on 64 bit system?"
date: 2009-05-23
forum: x86 64-bit Users
---

### Post by Chuck78 on 2009-05-23
I'm fairly new to Ubuntu, using 8.10 64 bit, and sometimes wishing I had just installed the 32 bit version to make things easier on me.    I have Audacious 1.5.1, and an wanting to upgrade to the just released 2.0.1 version.  Audacious has the tgz versions available, and I see that some have compiled deb versions of this release for i386.  
I was wondering if someone could be so kind as to give me a step by step on how I can force the architecture?  I thought I already had a library installed that will allow 32 bit programs to run, but when I open this:
[http://www.flapane.com/unixmac/Ubuntu/audacious_2/audacious_2.0.1-1_i386.deb](http://www.flapane.com/unixmac/Ubuntu/audacious_2/audacious_2.0.1-1_i386.deb)
[http://www.flapane.com/unixmac/Ubuntu/audacious_2/audacious-plugins_2.0.1-1_i386.deb](http://www.flapane.com/unixmac/Ubuntu/audacious_2/audacious-plugins_2.0.1-1_i386.deb)

it still gives me the "error, wrong architecture i386" message.

I don't know a lot about using terminal, but I read that if you just start your teminal like as "linux32 _____" that you should be able to then install 32 bit programs.  
If I'm trying to install those files above, what can I type in terminal to force a 32 bit program to install on my 64 bit 8.10? If I try to use the default install with Gdebi package installer, that is when I get the error message about the 1386 architecture.

thanks!

---

### Post by Yellow Pasque on 2009-05-23
```
sudo dpkg -i --force-architecture <some i386 package>
```

---

### Post by Chuck78 on 2009-05-24
If I'm trying to install it from that link that I posted, how do I do that through terminal?  If I click on the link, it starts the deb package installer and instantly tells me that I have the wrong architecture.  I can't find the newest release of Audacious in the repositories, as it's still in the formative stages.  

Please bear with me as I try to better understand the more complicated aspects of Ubuntu from a beginner's perspective.  

Thanks,

Chuck

---

### Post by Yellow Pasque on 2009-05-25
```
sudo dpkg -i --force-architecture audacious_2.0.1-1_i386.deb audacious-plugins_2.0.1-1_i386.deb
```

---

### Post by pixel :-) on 2009-05-25
You save manually the files, and then the above command at where ever you saved them

---

### Post by dupondje on 2009-05-30
Made package of it in my PPA!

deb [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main

---

### Post by JoZ3 on 2009-05-31
tnx a lot :p

---

### Post by Chuck78 on 2009-05-31
So I saved those to my desktop, and then in terminal, I entered the second code posted, but it tells me it cannot find the file.  How do I enter that command so that it knows where the files are?  I don't seem to think that I can run that command from the desktop, but I am thinking that I need to type something in terminal similar to a "change directory" command on a windows/dos command prompt, correct?

---

### Post by Chuck78 on 2009-05-31
What does it mean that you saved a package in your ppa?  Did you make a 64 bit audacious 2 deb package??? Or did you just compile another 32 bit deb package???  Please help me understand this stuff so I can get beyond the basic understanding of rookie Ubuntu use.

I saved the first link stuff that I posted.  

Thanks,

Chuck

---

### Post by Agent ME on 2009-05-31
> **Chuck78 said:**
> So I saved those to my desktop, and then in terminal, I entered the second code posted, but it tells me it cannot find the file.  How do I enter that command so that it knows where the files are?  I don't seem to think that I can run that command from the desktop, but I am thinking that I need to type something in terminal similar to a "change directory" command on a windows/dos command prompt, correct?
The command to change directory on linux is the same as windows :P You want to type "cd Desktop" first if the files are there.

---

### Post by dupondje on 2009-06-01
You should add both links to your sources.list in /etc/apt/. (This can be done in GUI).

Then its just a thing of aptitude update & aptitude dist-upgrade and your done :D

Oh and, I uploaded a Karmic built also to my PPA :)

---

### Post by Chuck78 on 2009-06-01
> **dupondje said:**
> Made package of it in my PPA!

deb [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main

what package is it that you made? Is this just a 32 bit deb file of audacious 2?  Is it going to be the same as the link I posted above from the other guy?

Thanks.

---

### Post by dupondje on 2009-06-02
Its a 32bit/64bit/lpia package for audacious 2.0.1 ! For Karmic & Jaunty

---

### Post by The Bright Side on 2009-06-10
Hey man, I found some packages here:
[http://ppa.launchpad.net/dupondje/ppa/ubuntu/pool/main/a/audacious/](http://ppa.launchpad.net/dupondje/ppa/ubuntu/pool/main/a/audacious/)
[http://ppa.launchpad.net/dupondje/ppa/ubuntu/pool/main/a/audacious-plugins/](http://ppa.launchpad.net/dupondje/ppa/ubuntu/pool/main/a/audacious-plugins/)

Are these the ones you made for Ubuntu 64? If so, which one do I pick? Thanks man! This is great!

---

### Post by dupondje on 2009-06-15
Just add

deb [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main

to sources.list, and audacious will be upgraded automaticly ?

---

### Post by The Bright Side on 2009-06-17
It says I need a key:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CD51A93283874559

Thanks!

---

### Post by Hero of Time on 2009-06-17
> **The Bright Side said:**
> It says I need a key:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CD51A93283874559

Thanks!

Open his launchpad site ([https://launchpad.net/~dupondje/+archive/ppa](https://launchpad.net/~dupondje/+archive/ppa)) and add his key. There are instructions on the site.

@Dupondje,
You've got a bug in the package, one that without the proper configure parameters or packages can occur. I've had it myself, but I forgot how I fixed it. I did manage to fix it once when I build 1.5.1 myself, but no idea how it works now. This is the problem:
```
MADPlug-Message: Rejecting http://75.125.224.109:8015/ (not an MP3 file?)
ERROR: libflacng.so: seekable_stream_callbacks.c:96 (seek_callback): Could not seek to 0!
ERROR: libflacng.so: tools.c:209 (read_metadata): Could not reset the decoder!
MADPlug-Message: Rejecting http://75.125.224.109:8015/ (not an MP3 file?)
ERROR: neon: neon.c:979 (neon_aud_vfs_fread_impl): <0x9bf2580> Buffer underrun, trying rebuffering
ERROR: neon: neon.c:1215 (neon_aud_vfs_ungetc_impl): <0x9bf2580> NOT IMPLEMENTED
ERROR: neon: neon.c:979 (neon_aud_vfs_fread_impl): <0x9bf2580> Buffer underrun, trying rebuffering
```
In other words, streams don't work (shoutcast etc). You can ignore the flac errors, it's an MP3 stream.

Edit:
Ubuntu release 2.0.1 in it's Karmic repo, and that one too, gives the same error. Possibly a problem in the neon libs, or more precise, the combination of neon with libmad. Maybe, don't know for sure.

---

### Post by The Bright Side on 2009-06-18
Thanks! I still can't get it to work, though :-( My problem is: when the source was released, I tried to install the new version from source, but screwed it up really badly and ended up with a broken version that's now stuck on my system: it loads, but it won't play or do anything, it just sits there and ignores any file that I try to open with it.

Now that I installed the new version from the repo as described above, using Synaptic, I still get this broken version, the only difference is that the old Audacious is now gone and I cannot get it back.

All the folders for Audacious 1 and 2 are still there when I search for them, all the files and stuff.

Do you guys know how to REALLY clean this off the system? I mean both versions, so I can do a clean new install of the newest version?

Thanks!
Matthias.

---

### Post by Hero of Time on 2009-06-18
> Do you guys know how to REALLY clean this off the system? I mean both versions, so I can do a clean new install of the newest version?
What you can do is open the packages you used for installation with an archive manager (e.g. xarchiver can open .deb) and check which files are extracted where, and remove it manually. You have to be careful that you don't remove a shared library. It's best to install apt-file*, and use that to see if it actually is a shared library, meaning provided by more than one package and that shared package is installed.

Are you sure that an apt-get remove or dpkg -r doesn't remove it?

*apt-file is like apt-cache, except you can search for files inside packages and it gives the name where it's in. You have to update it's database first, which will take some time, especially on slow connections. Update must be run as root, normal search calls can be done as normal user.

---

### Post by The Bright Side on 2009-06-18
Yeah both don't remove it... In the meantime, I manually removed remaining audacious files and directories from my system and reinstalled 1.5.1.
I will give this another shot later today. Thanks for your help guys, I really appreciate it.

---

### Post by elitenoobboy on 2009-06-23
Generally, it's best not to install newer packages like this. Many packages typically have version dependencies for packages newer than what you have on your system (in this case, the original poster said he was still using 8.10, which will have mostly older versions installed), and if you try to upgrade those dependencies you will have to upgrade their dependencies or risk breaking stuff and so on and so on. In this specific case, audacious 2.0 seems to require libgtk 2.17, and some packages in jaunty 9.04 depend on the specific version of libgtk 2.16 to be installed.
I've tried to upgrade to a newer audacious before and ran into this same kind of dependency problem. Unless you want to try a full upgrade to karmic koala alpha, it's probably better to just keep using 1.5.1 audacious. Plus, waiting will let them work out all of the [bugs]("https://bugs.launchpad.net/ubuntu/+source/audacious/+bug/389726") as well.

---

### Post by The Bright Side on 2009-06-29
elitenoobboy, I figured the same thing. I tinkered around soem more with it, and I think I'll just wait until there's a solid, stable version, perhaps available in the repositories for the next Ubuntu...?

---

### Post by elitenoobboy on 2009-06-29
> **The Bright Side said:**
> perhaps available in the repositories for the next Ubuntu...?
2.0.1 is already available in the karmic repositories, but like I said, audacious has fairly strict dependency version requirements so you would have to fully switch to the alpha, plus it is still buggy.

---

### Post by philip5 on 2009-07-09
I have (among a bunch of other updated packages) the latest 2.1.0 version (for the moment) of Audacious and the plugins pack on my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Have fun!

---

### Post by elitenoobboy on 2009-07-09
> **philip5 said:**
> I have (among a bunch of other updated packages) the latest 2.1.0 version (for the moment) of Audacious and the plugins pack on my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Have fun!

Very nice repository. I've been looking for something like this for a while, as most other reps are either not kept up to date, or are just meant for one or two packages. Also neverball and neverputt packages are giving me a "error: broken count > 0" error when I try to upgrade/install them to 1.5.1 from that rep.

---

### Post by philip5 on 2009-07-09
> **elitenoobboy said:**
> Very nice repository. I've been looking for something like this for a while, as most other reps are either not kept up to date, or are just meant for one or two packages. Also neverball and neverputt packages are giving me a "error: broken count > 0" error when I try to upgrade/install them to 1.5.1 from that rep.

Are you using Jaunty or some other release? I don't keep packages for Intrepid or Hardy as updated as the Jaunty repo. Make sure that you have ran a update before you try to update that can for sure make some mismatches.

Are you getting the same error if you try to update neverball from a terminal (use i.e aptitude for that)? In that case, do you get any more information in the error message? As far as I know it should work but it might break against some other 3rd party repo that might not follow correct naming of packages or versioning.

---

### Post by elitenoobboy on 2009-07-09
It looks like neverball 1.5.1 has unmet dependencies because neverball-common and *-data cant be installed.
```

E: /var/cache/apt/archives/neverball-data_1.5.1-jaunty~ppa2_all.deb: trying to overwrite `/usr/share/games/neverball/map-back/alien.sol', which is also in package neverball-common
E: /var/cache/apt/archives/neverball-common_1.5.1-jaunty~ppa2_all.deb: trying to overwrite `/usr/share/games/neverball/ttf/DejaVuSans-Bold.ttf', which is also in package neverball-data


```
I tried deleting dejusans-bold and alien.sol, but it still fails.

---

### Post by philip5 on 2009-07-09
> **elitenoobboy said:**
> It looks like neverball 1.5.1 has unmet dependencies because neverball-common and *-data cant be installed.
```

E: /var/cache/apt/archives/neverball-data_1.5.1-jaunty~ppa2_all.deb: trying to overwrite `/usr/share/games/neverball/map-back/alien.sol', which is also in package neverball-common
E: /var/cache/apt/archives/neverball-common_1.5.1-jaunty~ppa2_all.deb: trying to overwrite `/usr/share/games/neverball/ttf/DejaVuSans-Bold.ttf', which is also in package neverball-data


```
I tried deleting dejusans-bold and alien.sol, but it still fails.

That shouldn't happen as there should be no such conflicting files in those two packages. Try to uninstall all your neverball packages and remove them also from /var/cache/apt/archives. After that make a new install and it should work. Could it be that you have neverball 1.5.1 packages from some other repo?

---

### Post by elitenoobboy on 2009-07-09
That fixed it, thanks.

---

### Post by The Bright Side on 2009-08-14
Hey,

is anybody using the Crossfade plugin of the new version? I just tried it (reinstalled my system and thought I'd give the new version of Audacious a shot even though it seems buggy), and whenever i skip through a song or select another song in my playlist, there's a delay of 1-2 seconds before anything happens. That means if I start playing a new song and then skip to a later part in it, the begnining of the song will keep playing for 1-2 seconds before it skips to the desired position :-(

Am I the only one with that issue? If not, has anybody fixed it?

Thanks!
Matthias.

---

### Post by Artemis3 on 2009-08-30
Anyone knows how to set Audacious 2.x to look like this?
[img]http://audacious-media-player.org/local-images/screenshot_7.png[/img]

It is shown in the [Audacious homepage](http://audacious-media-player.org/), but i can't figure how to find it.

---

### Post by wujaklija on 2009-09-07
$audacious2 -i newui
or
$audacious2 -i gtkui

---

### Post by Eric Buist on 2009-10-04
Unfortunately, this repository won't work anymore, because Lauchpad site changed and now provides no link to PGP keys in PPAs! There is no link near OpenPGP key on the home page, just the 95CC1732 text. Maybe it works only with Karmick where some mechanisms are in place to auto-import the PGP key. I have spent quite a lot of time to figure out that it just won't work, and there is no other way out to get Audacious other than reinstalling a 32 bits Ubuntu version or switching to another distribution.
Note that under Windows, installing a program such as a media player would be a snap, and it would work independently of the version or edition of Windows.

---

