---
title: "Upgrade to Firefox 1.5 ?"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Axios on 2005-11-30
Hello

Are there any repositorys to upgrade my mozilla firefox to 1.5 on ubuntu ppc?


Thanks

---

### Post by tijs on 2005-11-30
I was about to ask the same question...

---

### Post by ssam on 2005-11-30
i put a tarbar for the third rc on my site, if you want to try that. (i doubt much has changed between that and the final version)

[http://www.tygier.co.uk/linux/firefox.html](http://www.tygier.co.uk/linux/firefox.html)

make make build a final one this week if the back porters dont beat me to it.

sam

---

### Post by joshuapurcell on 2005-11-30
Here's some information on the official backport:
[http://ubuntuforums.org/showthread.php?t=96595](http://ubuntuforums.org/showthread.php?t=96595)

Basically it says that it will be a while before the new version of Firefox is released as a backport. Also, there is no difference between RC3 and the final 1.5 release (which is why if you have RC3 installed you didn't recieve and upgrade notice).

---

### Post by hkan on 2005-12-05
There isn't any technical difference (other than perhaps version differences, et c) between the powerpc tarbar on Sam's site and the official i686-linux one over at getfirefox.com? Meaning that both will work just as fine on my iBook running Ubuntu 5.10? Or am I missing out some important architecture issue here? :)

UPDATE: Could've done it before posting here, but my confusion-kinda-thing remains anyway since I now am happily surfing around in Firefox 1.5. Although it's called Deer Park.

Anyone please help me straighten these things out!

/Quite new to Linux, especially on ppc machines

---

### Post by muchmusic on 2005-12-06
You might be using the Dapper repos?

1.5 is there, but it is a deer park release or "development" release of 1.5 think of it is 1.5+ I guess.

Be careful if you use dapper, it is not yet stable, many package changes going on!

---

### Post by ssam on 2005-12-06
[QUOTE=hkan]There isn't any technical difference (other than perhaps version differences, et c) between the powerpc tarbar on Sam's site and the official i686-linux one over at getfirefox.com? [/QUOTE]

firefox is writen mostly in C++ (the source code), this need to be compiled into machine code. each architecture has a different language for its machine code. luckly gcc (the gnu C compiler) can turn (amost) any C/C++ code into machine code for (almost) any architecture.

mozilla compile official builds for PowerPC MacOS X, x86 Windows, and x86 Linux.

to make a PowerPC linux version you have to take the source code and compile it for PowerPC linux.

so thats a big difference between the official build and my one.

the mozilla source code contains the code for lots of different products, and has lots of options. you make a .mozconfig file to control what gets built.

mine will probably have slightly different options from the official one.

my build has the official branding turned off. mozilla are quite strict with their trade mark policy. they dont want any old monkey (read "me") making some crummy build of firefox and distributing it as Mozilla Firefox.

---

### Post by hkan on 2005-12-06
[QUOTE=ssam]firefox is writen mostly in C++ (the source code), this need to be compiled into machine code. each architecture has a different language for its machine code. luckly gcc (the gnu C compiler) can turn (amost) any C/C++ code into machine code for (almost) any architecture.

my build has the official branding turned off. mozilla are quite strict with their trade mark policy. they dont want any old monkey (read "me") making some crummy build of firefox and distributing it as Mozilla Firefox.[/QUOTE]

Thanks for straightening things out! And thanks for making the powerpc build available, it works like a charm.

---

### Post by Axios on 2005-12-06
[QUOTE=ssam]i put a tarbar for the third rc on my site, if you want to try that. (i doubt much has changed between that and the final version)

[http://www.tygier.co.uk/linux/firefox.html](http://www.tygier.co.uk/linux/firefox.html)

make make build a final one this week if the back porters dont beat me to it.

sam[/QUOTE]

Is it possible to make a .deb?

---

### Post by ssam on 2005-12-06
i have rebuild the tarball from the final 1.5 release, (although i think it is identical to the rc3).

if you want a deb then you can use the one from dapper.

edit: sorry to cause confusion. this is not really possible, see my posts below

---

### Post by Axios on 2005-12-06
[QUOTE=ssam]i have rebuild the tarball from the final 1.5 release, (although i think it is identical to the rc3).

if you want a deb then you can use the one from dapper.[/QUOTE]

How do i get the one from dapper?

---

### Post by ssam on 2005-12-06
you could try from [http://packages.ubuntu.com/dapper/web/firefox](http://packages.ubuntu.com/dapper/web/firefox) or [http://archive.ubuntu.com/ubuntu/dists/dapper/](http://archive.ubuntu.com/ubuntu/dists/dapper/)

you could learn about [apt pinning]("http://jaqque.sbih.org/kplug/apt-pinning.html")

or you could wait for the backport team to do it for you.

edit: sorry to cause confusion. this is not really possible, and the back port team have said it is far to much work (with a high risk of breaking other apps) to backport firefox. see my post below

---

### Post by Focx on 2006-01-17
I tried to install the .deb from dapper, but it gave me "conflicting packets" with the original official ubuntu firefox. would it break something, if I ignored these conflicts?

---

### Post by ssam on 2006-01-18
[QUOTE=Focx]I tried to install the .deb from dapper, but it gave me "conflicting packets" with the original official ubuntu firefox. would it break something, if I ignored these conflicts?[/QUOTE]

quite possibly.

firefox is used in lots of places for html rendering. those programs are compiled against firefox 1.0, and so can't use 1.5. the solution is to recompile evrything that requires firefox and upgrade things that need upgrading to support ff 1.5.

the backports team decided this was to large a task to do and could introduce new bugs.

the only practical way to run firefox is to install it seperately to the ubuntu version. so that other programs can use the ubuntu version still.

or just wait 3 months until dapper, which will have a well intergrated version of firefox 1.5 (maybe 1.5.0.1)

---

### Post by dombleu on 2006-01-21
SSAM: Thanks a lot for the build. You saved me a lot a time and it work wonderfully!

Dom

---

### Post by mr.lamp on 2006-01-21
> I may have to remove this file if it uses to much bandwidth, but for now here it is

If it causes to much traffic, you could upload it to rapidshare or another one-click-hoster

---

### Post by ssam on 2006-01-21
[QUOTE=mr.lamp]If it causes to much traffic, you could upload it to rapidshare or another one-click-hoster[/QUOTE]

its only getting about 5-10 downloads a week so i can manage that.

---

### Post by N8K99 on 2006-01-28
Hi I just switched my Powerbook over to Kubuntu - and needed to add Firefox 1.5 for grits and shingles. Thanks for compiling this crackerjack job so that I can have the old familiar staring back at me face!:)

---

### Post by lunatic77 on 2006-02-04
[QUOTE=ssam]i have rebuild the tarball from the final 1.5 release, (although i think it is identical to the rc3).

if you want a deb then you can use the one from dapper.

edit: sorry to cause confusion. this is not really possible, see my posts below[/QUOTE]
i was having trouble compiling the 1.5.0.1 source on my powerbook...so i downloaded your build and tried to run it and again ran into problems.  i realize you probably don't want to spend a lot of time supporting this build -- but just in case there's an easy answer to my problem...

it looks like i have some runtime libs missing.  if i do an ldd on your firefox-bin i get the following libs not found:
        libmozjs.so => not found
        libxpcom.so => not found
        libxpcom_core.so => not found
        libstdc++.so.5 => not found

thanks for any help you might be able to provide!

---

### Post by ssam on 2006-02-05
there is a package for libstdc++5 in the repos. i haven't seen the other libs missing before. maybe libstdc++5 will sort them out.

as for building, you need to use gcc 3.4 . there is a post in this forum from quite a while ago that explains how to build it.

i might do a 1.5.0.1 build over the next few days if i get around to it.

---

### Post by Brian McConnell on 2006-02-09
[QUOTE=ssam]i put a tarbar for the third rc on my site, if you want to try that. (i doubt much has changed between that and the final version)

[http://www.tygier.co.uk/linux/firefox.html](http://www.tygier.co.uk/linux/firefox.html)

make make build a final one this week if the back porters dont beat me to it.

sam[/QUOTE]


I'm wondering how to install this. I was expecting to extract, ./configure, make and make install, but no config file found!?! Any help would be appreciated.

---

### Post by ssam on 2006-02-09
[QUOTE=Brian McConnell]I'm wondering how to install this. I was expecting to extract, ./configure, make and make install, but no config file found!?! Any help would be appreciated.[/QUOTE]

this is already built (the mozilla build is a bit more complex than most unix software, partly because by change the build options around you can build firefox or thunderbird or any other moz project from the same source tree.)

all you need to do is unpack it somewhere (/opt/firefox is a good choice), and set up some symlinks.

there are instructions at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by magicalsavant on 2006-02-09
Being fairly new to Debian distros, I'm not entirely sure this is the best way to get Firefox 1.5, but here's what I did:

[LIST=1]
[*]I added an unstable Debian repository to my ```
/etc/apt/sources.list
``` file (I'm in the US, so I added:  deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) unstable main non-free contrib   )
[*]I ran ```
apt-get update
``` to get the updated apt sources
[*]I did an ```
apt-get install firefox
```
[*]apt-get downloaded all the Debian unstable packages needed for Firefox 1.5 (there were a few prompts telling me that the unstable Debian stuff was unverified, but I just told it yes several times.
[*]I'm posting via Firefox 1.5.1 right now on Ubuntu PowerPC
[/LIST]
Sorry if this is wrong, but it seemed easier than trying to build from source.

---

### Post by ssam on 2006-02-10
[QUOTE=magicalsavant]
Sorry if this is wrong, but it seemed easier than trying to build from source.[/QUOTE]

the trouble with that method is that lots of programs use firefox to render html for them. all these programs in ubuntu were compiled against firefox 1.0. there is a large chance that these programs will have problems.

this is why there was no official back port, to many packages would need rebuilding and patching.

ps: i have built 1.5.0.1 and am posting with it :-)
i'll have it uploaded in the next few mins (hopefully)

---

