---
title: "texlive safely possible under Dapper?"
date: 2006-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by aikishugyo on 2006-12-02
Hello all, I've an AMD64 running Dapper, and it seems an upgrade to Edgy (as opposed to a reinstall) is still dangerous from reading the forum posts. I would really like to use Texlive (same as on my Debian unstable machines) and would like an opinion as to whether fetching Texlive from Edgy sources is possible (safely). If I had an x86 32-bit I'd already have upgraded to Edgy.

Many thanks for your thoughts, 
Gernot

---

### Post by kuja on 2006-12-03
The "Dangers" of upgrading in 64-bit should be no different than those in 64-bit AFAIK. You could try to switch the repositories to "edgy" and then install that single package, but be wary of the fact that it will pull any changed dependencies in the progress. It could potentially break something, it could potentially work. If it works, that's great, if not, just revert and you should be back to something functional.

---

### Post by kleeman on 2006-12-03
Download the livecd for edgy and see whether all your hardware works OK or not. If so an upgrade should be safe although if you have 3rd party additional repos there may be hiccups. I would expect however that these should be solvable.

I personally would not be comfortable installing texlive from edgy on dapper.  Texlive is a complex set of packages with many dependencies.

Edit: I have it installed on edgy and it works very nicely.

---

### Post by aikishugyo on 2006-12-22
Thanks kleeman for that advice, I feel the same way as you do(I was hoping someone could point me to a backport, I'm not up to doing that myself, sadly). kuj, I don't know how to revert, I thought upgrades using apt-get and aptitude cannot be reverted (at least not easily). I've downloaded Edgy desktop install and alternative install CDs and will attempt an install today.

---

### Post by ozziem on 2006-12-23
> **kleeman said:**
> 
I personally would not be comfortable installing texlive from edgy on dapper.  Texlive is a complex set of packages with many dependencies.


Not AMD 64 related, but seems pointless to start a new thread ...

I currently use Dapper, but would like to migrate to Texlive. Given that Dapper (6.06) is touted as having "LTS" (Long Term Support), and that tetex has been "De Supported", it would make sense to Texlive to eventually appear in the Dapper repositories, would it not ... ? Or am I being too logical or optimistic ... ? ;-)

I realize that there are other options, such as installing Texlive manually or upgrading to Edgy, but would prefer not to have my primary research machine "on the edge", and would also like to manage as much as possible with aptitude.

Thoughts?

---

### Post by kleeman on 2006-12-23
> **ozziem said:**
> Not AMD 64 related, but seems pointless to start a new thread ...

I currently use Dapper, but would like to migrate to Texlive. Given that Dapper (6.06) is touted as having "LTS" (Long Term Support), and that tetex has been "De Supported", it would make sense to Texlive to eventually appear in the Dapper repositories, would it not ... ? Or am I being too logical or optimistic ... ? ;-)

I realize that there are other options, such as installing Texlive manually or upgrading to Edgy, but would prefer not to have my primary research machine "on the edge", and would also like to manage as much as possible with aptitude.

Thoughts?
Well my primary research machine is running AMD64 Edgy and I'm pretty happy. I actually find edgy a touch more stable than Dapper. The main point about LTS is that it will be supported for a long time so particularly security wise you can breathe easy. I don't think the developers claim it is more stable than Edgy.

Personally I don't find it too stressful upgrading every 6 months or so but then I have been using linux for 5 years or so....

My guess would be that texlive will not be backported to Dapper. Why do you want it instead of tetex?

---

### Post by towsonu2003 on 2006-12-23
> **aikishugyo said:**
> Hello all, I've an AMD64 running Dapper, and it seems an upgrade to Edgy (as opposed to a reinstall) is still dangerous from reading the forum posts. I would really like to use Texlive (same as on my Debian unstable machines) and would like an opinion as to whether fetching Texlive from Edgy sources is possible (safely). 

I tried backporting texlive from feisty to dapper and so far it's okay. **read** this 
[http://ubuntuforums.org/showthread.php?t=268687](http://ubuntuforums.org/showthread.php?t=268687)

backporting may be dangerous, so be careful. I'm still testing my backport in a virtual Ubuntu (vmware player). 

what you will do is:
[list]
[*]get prevu
[*]Edit your /etc/apt/sources.list. You need a deb-src line for the development distro of Ubuntu
[*]run apt-get update
[*]sudo prevu-init
[*][list]
[*]apt-get source texlive-base
[*]apt-get source texlive-bin
[*]apt-get source texlive-doc
[*]apt-get source texlive-extra
[*]apt-get source texlive-lang
[/list]
[*]cd into each source directory and run ```
prevu
```
[*]add deb file:/var/cache/prevu/**dapper**-debs ./ to your sources.list
[*]launch synaptic, hit reload, then search for texlive
[*]be careful...
[/list]

I couldn't emphasize more: **read the whole thread** [http://ubuntuforums.org/showthread.php?t=268687](http://ubuntuforums.org/showthread.php?t=268687)

Also, drop a comment to this report so maybe we can get an official backport: 
[https://bugs.launchpad.net/products/dapper-backports/+bug/58599](https://bugs.launchpad.net/products/dapper-backports/+bug/58599)

The part 
```
apt-get source blabla
``` is because a number of packages are compiled from the same huge source. you can see a list of sources and the packages built from them here: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=texlive&searchon=sourcenames&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=texlive&searchon=sourcenames&subword=1&version=feisty&release=all)

the last link also is the answer to > it would make sense to Texlive to eventually appear in the Dapper repositories, would it not ... ? Or am I being too logical or optimistic ... ?
if it fails, it won't appear in Dapper, ever...

PS. If I were you, I would start with manipulating Dapper in a virtual environment so if your personal backports fail, you will be trashing a virtual OS, not your own thing... ;) search around for vmplayer and easyvmx.com

---

### Post by ozziem on 2006-12-24
> **kleeman said:**
> Personally I don't find it too stressful upgrading every 6 months or so but then I have been using linux for 5 years or so....

Well, it's not so much experience-related (I started out with Slackware in the days when compiling one's own kernel was essential for just about anything beyond a basic command line), and I admit that the regular updates were something that attracted me to Ubuntu, but when I tried the Edgy upgrade on a test-bed machine, it was, let's just say, not very confidence-inspiring. It wasn't a big deal to fix the dependency mess that the installer left, (using the recommended method, that is) but it got me thinking that perhaps 6 months is a little aggressive for use in a work environment. Then again, it's going to be hard to continue to resist the excitement of getting the latest and greatest of everything twice a year ... ;-)

> **kleeman said:**
> 
My guess would be that texlive will not be backported to Dapper. Why do you want it instead of tetex?

Well, the old adage "if it aint broke don't fix it" should probably prevail ... But I guess I'd just thought it'd be nice to start using the implementation that I'll likely be using 5 years from now as soon as I can. Plus, there appears to be a general consensus in the LaTeX community that users should switch to texlive. So I was just wondering what the feasibility of switching without a dist-upgrade would be. But not being able to do so easily is certainly not a show-stopper.

> PS. If I were you, I would start with manipulating Dapper in a virtual environment so if your personal backports fail, you will be trashing a virtual OS, not your own thing... 

Sounds like a wise suggestion!

---

