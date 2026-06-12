---
title: "Cinelerra on Breezy - got it running!"
date: 2006-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bruce3000 on 2006-04-23
Hi Peeps,

I haven't floated around these parts since last year really, so I don't know if I'm re-inventing the wheel (albeit perhaps even a square one) but I've just has a success installing Cinelerra to my AMD64 Breezy box. 

I've documented the process here:

[http://bruceraverant.blogspot.com/2006/04/cinelerra-amd64-breezy-install-how-to.html](http://bruceraverant.blogspot.com/2006/04/cinelerra-amd64-breezy-install-how-to.html)

The most grief I'm having, is that I had to ditch the encumbant libopenexr2c2 in lieu of and unstable version. Perhaps the dependency requested by Cinelerra (libopenexr2c2a_1.2.2) isn't necessary, and the package could be modified to depend on the encumbant (perhaps I should do that). In any case, it's prevented me from running ktorrent or patience (there are of course alternatives)!

Anyway, I hope my experience is helpful, and if anyone wants to expand on my HOW-TO, go for it. I'd love for someone to be able to use it (even if it is a bit noobish).

Just a question, what version of libopenexr is bundled with Dapper?

Bruce

P.S. Probably getting a bit close to Dapper to mention this as well.

---

### Post by bruiser64 on 2006-04-25
Congratulations.
I have been using the heroine warrior version.
The next thing you may want is ffmpeg to work with mp3.
I am not fond of mencoder.
The source from cvs 20050918 doesn't compile on my amd64, to enable mp3lame.
If you have any luck please let me know.
Bruce

---

### Post by artik on 2006-04-25
Is there any chances that cinelerra will be in multiverse for dapper?
I've tryed to install cinelerra for Breezy from the repos they prepared - dependecies problem - Breezy 32...
Compilation failed...

And cinelerra looks too promising and I really want to get a version that **works**

---

### Post by Bruce3000 on 2006-04-29
Yeah, dependencies seems to be the problem atm. Some of the development libraries needed to get support for X,Y,Z aren't available as debs yet. May have to compile them. If I do, and it works (and I don't break anything), I'll keep people posted.

If I can get the necessary source, I may make some .debs out of them and we'll have to see if someone can host a repository at some stage I guess. Getting this ready for Dapper, if Dapper doesn't have Cinelerra in the repositories for AMD64 may be a good goal.

Cinelerra looks like a promising package. This is the first time I've got it running. Hope the project get's plenty of support.

I should probably tell the developers at some point if I continue. Don't want to replicate someone else's work. Not that I'm hacking the code or anything.

---

### Post by Tink on 2006-04-29
Tring to install the cinelerra-deb gives me:
```

dpkg: dependency problems prevent configuration of cinelerra:
 cinelerra depends on fftw3; however:
  Package fftw3 is not installed.
 cinelerra depends on libiec61883-0; however:
  Package libiec61883-0 is not installed.
 cinelerra depends on libmpeg3hv (>= 1:2.0.0); however:
  Package libmpeg3hv is not installed.
 cinelerra depends on libquicktimehv (>= 1:2.0.0); however:
  Package libquicktimehv is not installed.
 cinelerra depends on libraw1394-8; however:
  Package libraw1394-8 is not installed.
 cinelerra depends on libquicktimehv (= 1:2.0.0-1svn20060419); however:
  Package libquicktimehv is not installed.
 cinelerra depends on libmpeg3hv (= 1:2.0.0-1svn20060419); however:
  Package libmpeg3hv is not installed.
dpkg: error processing cinelerra (--install):
 dependency problems - leaving unconfigured
```


And how do you get rid of all the warnings/errors when you try
to run apt-get again?  I've followed your blog, installed all
the packages listef using dpkg, but now, when I try to apt-get
anything else apt spits in my face ... 

```

  libasound2-dev: Depends: libasound2 (= 1.0.9-2) but 1.0.10-2 is to be installed
  libogg-dev: Depends: libogg0 (= 1.1.2-1) but 1.1.3-2 is to be installed
  libopenexr2c2a: Conflicts: libopenexr2c2 but 1.2.2-3ubuntu1 is to be installed
  libvorbis-dev: Depends: libvorbis0a (= 1.1.0-1ubuntu1) but 1.1.2-1 is to be installed
                 Depends: libvorbisenc2 (= 1.1.0-1ubuntu1) but 1.1.2-1 is to be installed
                 Depends: libvorbisfile3 (= 1.1.0-1ubuntu1) but 1.1.2-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


Cheers,
Tink

---

### Post by Bruce3000 on 2006-06-04
Well, first of all, I'd uninstall everything that you had installed as per the how-to. Then I'd try to apt-get install fftw3, libiec61883-0, libmpeg3hv, libquicktimehv etc...

A number of these dependencies I had already installed (somehow) on a prior occasion, so I have better document them. I seem to have found the debs from somewhere... I'll have to look into it (in a few weeks sorry.)

As for the libvorbis-dev and libogg-dev, since then I've managed to get them installed (by finding a newer matching libogg and libvorbis). You can't apt-get versions of the development libraries if theu don't match the common libraries.

As for libopenexr2c2a, that's one of the mentioned drawbacks of the install. You are stuck with a version that doesn't sit will with the dependancy trees of other software (such as anything depending on kdelibs as mentioned in the HOW-TO).

---

