---
title: "Perl upgrade"
date: 2006-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by grough on 2006-06-17
Hi,

I needed to upgrade Perl to 5.8.8 to satisfy a dependency when installing another Perl package (libyaml-syck-perl) through synaptic.

I installed a perl-base_5.8.8-6 deb package. When I enter [FONT="Courier New"]perl -v[/FONT] in a terminal I get the message [FONT="Courier New"]This is perl, v5.8.8 built for x86_64-linux-gnu-thread-multi...[/FONT] as expected.

However, when I try to install libyaml-syck-perl, I still get the message 
[FONT="Courier New"]
libyaml-syck-perl depends on perl (>= 5.8.8-4); however: Version of perl on system is 5.8.7-10ubuntu1.
[/FONT]

Is there some reason Ubuntu still thinks I'm using the older version?

My ultimate goal is to install the slimserver package through synaptic, but the dependency libyaml-syck-perl "is not going to be installed".

Any ideas?

---

### Post by grough on 2006-06-17
[QUOTE=grough] the dependency libyaml-syck-perl "is not going to be installed".[/QUOTE]

The message actually says "the package is not installable". My mistake - not sure if it makes a difference.

---

### Post by nicketynick on 2006-06-22
Hey grough

Any luck with this?  I just got a box with Dapper Drake to use as a Slimserver (haven't got it on the network yet, but as soon as I get a chance....), but am a total noob.  So there is a Slimserver package available that can be installed with Synaptic?  Which version is it-6.2.2 ?  Did you get the perl upgrade to work?
Anything else?  Nice to see another Canadian here using Slimserver - not too many of us! I'm in Kingston, ON.

Nick

---

### Post by grough on 2006-06-22
Hey Nick,

Still no luck with the Perl upgrade. I'm going to post a more to-the-point question soon. I'm thinking maybe it's a 64-bit specific problem. I've had slimserver going on an older Ubuntu 5.10 box for a few months, and it worked nicely.

Yes, there's a slimserver package available through Synaptic. Add this line to your /etc/apt/sources.list file:

deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main

Go into synaptic, hit reload, then search slimserver. A package for slimserver 6.5b1 should come up, which is the beta package I've always used with no trouble.

Post back and let me know if you get it working, or if you hit any snags. Like I said, most of my Ubuntu/slimserver experience was on Breezy 5.10, so any 6.06 insight could be useful (right now I'm using win2k server cuz of my Perl problem).

I'm in Waterloo, ON... do you use a Squeezebox? mine has made me very happy :KS

---

### Post by stengah on 2006-06-26
This debian package doesn't load. Updated my sources.list:

## slimserver
deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main

sudo apt-get update (and tried update through synaptic as well). 

However, the package is not found. Seraching 'slimserver' gives nothing, nada, zip... the debian url does however seem to contain the files, but somehow it doesn't register...

What may be the problem??? Changed file names, or...?

---

### Post by nathanhill on 2006-08-27
Thanks for the tips, I'm not there yet, but one step closer it seems!
Once I added:
 deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main 
to my sources.list the I was able find the slimserver (6.5b1) package.

At first I couldn't get it to install, complaining that the 
libyaml-perl package {0.39-1(dapper)} was not current enough.
I checked though, and there were two available versions, the 0.39 version from ubuntu repositories, and a 0.57-1 version in the debian.slimdevices repository.  I forced the install of the 0.57-1 version (Synaptic menu Package|Force Version).  After that I was then able to successfully mark the slimserver package for installation, and the install script completed, it seemed with out errors.

However, I'm not sure how to get the slimserver started...
When I try to execute 'slimserver start' on the command line I get only perl compile errors:

root@6[~]# slimserver start
Can't locate object method "mk_classaccessors" via package "Slim::Networking::Async" at /usr/share/perl5/Slim/Networking/Async.pm line 27.
Compilation failed in require at (eval 36) line 3.
        ...propagated at /usr/share/perl/5.8/base.pm line 84.
BEGIN failed--compilation aborted at /usr/share/perl5/Slim/Networking/Async/HTTP.pm line 34.
Compilation failed in require at /usr/share/perl5/Slim/Utils/Scanner.pm line 44.
BEGIN failed--compilation aborted at /usr/share/perl5/Slim/Utils/Scanner.pm line 44.
Compilation failed in require at /usr/share/perl5/Slim/Control/Commands.pm line 40.
BEGIN failed--compilation aborted at /usr/share/perl5/Slim/Control/Commands.pm line 40.
Compilation failed in require at /usr/share/perl5/Slim/Control/Request.pm line 393.
BEGIN failed--compilation aborted at /usr/share/perl5/Slim/Control/Request.pm line 393.
Compilation failed in require at /usr/share/perl5/Slim/Player/Client.pm line 19.
BEGIN failed--compilation aborted at /usr/share/perl5/Slim/Player/Client.pm line 19.
Compilation failed in require at /usr/share/perl5/Slim/Buttons/Common.pm line 44.
BEGIN failed--compilation aborted at /usr/share/perl5/Slim/Buttons/Common.pm line 44.
Compilation failed in require at /usr/sbin/slimserver line 112.
BEGIN failed--compilation aborted at /usr/sbin/slimserver line 112.
Undefined subroutine &main::cleanup called at /usr/share/perl5/Slim/bootstrap.pm line 260.
END failed--call queue aborted at /usr/sbin/slimserver line 112.

Looks like I'll need to Google some more...
-N

---

