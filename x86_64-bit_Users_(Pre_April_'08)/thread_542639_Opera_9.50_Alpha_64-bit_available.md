---
title: "Opera 9.50 Alpha 64-bit available"
date: 2007-09-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ledah on 2007-09-04
The first alpha version of Opera, which supports finally the 64-bit architecture, is available. 
It looks much better than the 32-bit Opera on 64-bit systems. Flash isn't working anymore for me, even with the nspluginwrapper plugins from Firefox, but I think there will be a solution soon.

If someone wanna try it: [http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/](http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/)

But keep in mind that this is an alpha. Backup your directory before you try.

---

### Post by thetor on 2007-09-04
The new Opera looks great! Flash doesn't work for me either, of course... The new feature that synchronizes bookmarks/speed dial is promising, I just wish that it would synchronize more (search engines, blocked addresses list, etc)

---

### Post by Major_Kong on 2007-09-04
How's the memory footprint ?

---

### Post by afonic on 2007-09-04
Giving it a try right now!

Edit:

Seems to work fine. Flash doesn't work but I don't need it anyway.

Memory usage is great, I have opened the same tabs and Firefox (with no extensions) takes 120MB while Opera just 60.
It seems Google ads are not appearing though, maybe some kind of adblock? (lets hope not)

---

### Post by Nameless_one on 2007-09-04
FInally, a native amd64 Opera! I have waited long for this, now I can write in my native language (there was a problem with the forced 32-bit version). 

Flash isn't working here, either. I guess we'll just have to wait until Adobe releases a 64-bit version too :) 

I also have another problem, which I am very curious to see wether other people have: some HTML elements don't work any more, namely <marquee>, <blink>, and that sort. Other people I spoke to don't have the same problem.

---

### Post by Cappy on 2007-09-04
Like everyone else the 64-bit version would not work with flash.

I am using the 32-bit verson and it is working with flash:
```

wget http://snapshot.opera.com/unix/9.50-Alpha-1/intel-linux/opera-static_9.50-20070903.10-static-qt_i386.deb
sudo apt-get install ia32-libs ia32-libs-gtk
dpkg -i --force-all opera-static_9.50-20070903.10-static-qt_i386.deb


```

---

### Post by afonic on 2007-09-04
The whole idea is to use the x64 version, the 32bit one runs just fine, even at 9.23 or what version stable Opera now is.

---

### Post by AbredPeytr on 2007-09-04
I installed the tarball with no problem and no apparent loss of bookmarks/wands.

the sites I've tested have all worked, except with the noted failure of flash.

Seems to be very fast. Or is that just my excitement about Opera 64-bit? :-)

p.s. should I have installed the .deb package, or does it matter?
p.p.s. My programming understanding is sufficient enough that I can click my way through the file structure, delete something I shouldn't and then spend hours to days fixing it with the help of forums and Google.

Long live Opera!

---

### Post by Cappy on 2007-09-04
> **afonic said:**
> The whole idea is to use the x64 version, the 32bit one runs just fine, even at 9.23 or what version stable Opera now is.

If you want to use a 64-bit version that isn't working with Flash at the moment then be my guest. My "whole idea" is to have the newest version of Opera that works.

There isn't even a good reason to use a 64-bit browser over a 32-bit browser in the first place.

---

### Post by Nameless_one on 2007-09-04
Not per se, but a program with different architecture than yours always causes some problems, so it's better to go with the native version.

---

### Post by afonic on 2007-09-04
> **Cappy said:**
> If you want to use a 64-bit version that isn't working with Flash at the moment then be my guest. My "whole idea" is to have the newest version of Opera that works.

There isn't even a good reason to use a 64-bit browser over a 32-bit browser in the first place.

Don't get me wrong, I just thought that since this is the "x86 64-bit Users" forum and I believe we should be more interested for the new 64bit port than the 32bit version that is out for like, years.

You may think there is no point in running 64bit browsers (I disagree), so nothing stops you from running 32bit Firefox with 32bit Flash and 32bit Java and let us try to get 64bit versions for our 64bit OS. :P

---

### Post by Major_Kong on 2007-09-06
Any ETA on the final release ?

---

### Post by asdfoo on 2007-09-08
> **Nameless_one said:**
> FInally, a native amd64 Opera! I have waited long for this, now I can write in my native language (there was a problem with the forced 32-bit version). 

Flash isn't working here, either. I guess we'll just have to wait until Adobe releases a 64-bit version too :) 

I also have another problem, which I am very curious to see wether other people have: some HTML elements don't work any more, namely <marquee>, <blink>, and that sort. Other people I spoke to don't have the same problem.

Those tags are either deprecated or just plain wrong.  This is 2007, not 1997.  Don't use them. Problem solved.

---

### Post by kansei on 2007-09-08
> **asdfoo said:**
> Those tags are either deprecated or just plain wrong.  This is 2007, not 1997.  Don't use them. Problem solved.

+1

I still laugh how rapidly (within hours) any thread about a 64-bit app which mentions something that doesn't instantly work out of the box degrades to "well just use the 32-bit version".. that's just laughable.

I'll deal with flash not working in opera 9.5 to use a native version finally. I'm sure it'll work soon (through a workaround of course because Adobe doesn't want to recompile flash player) :)

---

### Post by rplantz on 2007-09-08
> **kansei said:**
> +1
I'll deal with flash not working in opera 9.5 to use a native version finally. I'm sure it'll work soon (through a workaround of course because Adobe doesn't want to recompile flash player) :)

About a year ago a guy who claimed to work for Macromedia said in his blog that it was more that simply recompiling flash. Apparently there is a fair amount of assembly language code in flash, so making it work in 64-bit mode is not trivial.

The real problem I have is that (now) Adobe won't release the source code so that others can bring it up to date. It's another example of how large corporations really don't care about people --- they simply want to make as much money as possible.

We would get 64-bit a lot faster if those who create things for the web would refuse to use flash until there is a 64-bit version.

---

### Post by kansei on 2007-09-08
> **rplantz said:**
> We would get 64-bit a lot faster if those who create things for the web would refuse to use flash until there is a 64-bit version.

I'll sign on to that (because although I have done flash stuff in the past, I don't currently have any out there), but who else will? Youtube.com ascii mode? lol

---

### Post by Cappy on 2007-09-08
> **kansei said:**
> 
I still laugh how rapidly (within hours) any thread about a 64-bit app which mentions something that doesn't instantly work out of the box degrades to "well just use the 32-bit version".. that's just laughable.

I'll deal with flash not working in opera 9.5 to use a native version finally. I'm sure it'll work soon (through a workaround of course because Adobe doesn't want to recompile flash player) :)

My choice of browser is Opera and I enjoy Flash based videos. If 64-bit Opera worked with Flash I would be using it.

Boycotting Flash won't help either. Simply not using Flash hurts no one else. You can use the open source flash alternative if you feel strongly about the issue.

---

### Post by revchris on 2007-09-09
> **Cappy said:**
> You can use the open source flash alternative if you feel strongly about the issue.

Where can I find this at?

---

### Post by afonic on 2007-09-09
Look for Gnash.

Still not complete though, if you need Flash 9.0 features its not for you.

---

### Post by John Jason Jordan on 2007-09-09
> **Cappy said:**
> You can use the open source flash alternative if you feel strongly about the issue.
I decided to give gnash a try, but evidently you can't install the mozilla or firefox plugins, which makes it useless. If I go into Synaptic and search on "gnash" I get several packages, including gnash itself and gnash-firefox-plugin. When I go to install gnash-firefox-plugin I get an error message:

```
gnash-firefox-plugin:
  Depends: libgnash0 (=0.7.2+cvs20070127-1raof1) but 0.8.0~cvs20070611.1016-1ubuntu3~feisty1 is to be installed
```

I'm not sure what the problem is, but it won't install.

---

### Post by tomdkat on 2007-09-10
> **rplantz said:**
> The real problem I have is that (now) Adobe won't release the source code so that others can bring it up to date. It's another example of how large corporations really don't care about people --- they simply want to make as much money as possible.
Are you saying [this project](http://www.mozilla.com/en-US/press/mozilla-2006-11-07.html) has been scrapped?

EDIT:  It doesn't look like it.  Maybe we'll get 64-bit Flash in 2008.

Peace...

---

### Post by gelog on 2007-09-11
yaa, just it is sad no flash support for opera AMD64. i dont understand anything in this coding, but why is it a problem to create functionaly on 64b systems? ;)

---

### Post by thetor on 2007-09-11
> **gelog said:**
> yaa, just it is sad no flash support for opera AMD64. i dont understand anything in this coding, but why is it a problem to create functionaly on 64b systems? ;)
The problem is, as  I understand it:
1.  64-bit applications cant interface with 32-bit applications without complicated workarounds
2. Flash is proprietary and closed source, and it is only released in 32-bit versions.
Ergo: 64-bit Opera cannot use the 32-bit flash plugin.

---

### Post by afonic on 2007-09-11
Because companies like Abode do not release closed source programs (like Flash) for amd64. If it was open source it would work just fine. :)

---

### Post by kansei on 2007-09-11
> **afonic said:**
> Because companies like Abode do not release closed source programs (like Flash) for amd64. If it was open source it would work just fine. :)

From what has been said (I believe in this thread, probably just on an earlier page now) the adobe flash player has a LOT of assembly code in it. It can't just be recompiled 64-bit.

---

### Post by stmiller on 2007-09-11
> **John Jason Jordan said:**
> I decided to give gnash a try, but evidently you can't install the mozilla or firefox plugins, which makes it useless. If I go into Synaptic and search on "gnash" I get several packages, including gnash itself and gnash-firefox-plugin. When I go to install gnash-firefox-plugin I get an error message:

```
gnash-firefox-plugin:
  Depends: libgnash0 (=0.7.2+cvs20070127-1raof1) but 0.8.0~cvs20070611.1016-1ubuntu3~feisty1 is to be installed
```

I'm not sure what the problem is, but it won't install.

There was a major release of Gnash [0.8.0] that plays back youtube, revision3, lulu.tv, and other flash video as well as being 100% flash 7 compatible for most all flash navigation sites. An official ubuntu package has been placed in Feisty backports. So enable Feisty backports, apt-get update, and install 0.8.0. 

Gnash is working great, and compiles/runs under Linux PowerPC, 64bit, and other operating systems.

---

### Post by John Jason Jordan on 2007-09-11
> **stmiller said:**
> There was a major release of Gnash [0.8.0] that plays back youtube, revision3, lulu.tv, and other flash video as well as being 100% flash 7 compatible for most all flash navigation sites. An official ubuntu package has been placed in Feisty backports. So enable Feisty backports, apt-get update, and install 0.8.0. 

Gnash is working great, and compiles/runs under Linux PowerPC, 64bit, and other operating systems.
I do have the backports enabled. But the gnash-firefox-plugin is only 7.2, 20070127. Gnash-dev is also 7.2, but all the rest of the gnash packages are 8.0. That's the problem. I can't install it to use with Firefox because the gnash-firefox-plugin won't work with gnash 8.0. Where can I get the gnash-firefox-plugin 8.0?

---

### Post by afonic on 2007-09-12
> **kansei said:**
> From what has been said (I believe in this thread, probably just on an earlier page now) the adobe flash player has a LOT of assembly code in it. It can't just be recompiled 64-bit.

Not trying to argue with you, but with Abode, this is bullshit.

What is the need for assembly code in Flash? It is just like a media player, nothing more, nothing less. In my eyes this is a lame excuse to defend their decision not to support 64bit platforms (in both Linux and Windows)

Ps. And if it can't just be recompiled, just make it work then. Simple as that.

---

### Post by kansei on 2007-09-12
I think it's BS too, but from what has been said it's apparent that they don't want to spend more than 5 minutes of a software developers time getting it to work. They spent 5 minutes, realized there was assembly code, and gave up.

Meanwhile gnash is catching up pretty quickly (fully flash 7 compliant + able to play flv from youtube and a bunch of other sites)

---

### Post by Nameless_one on 2007-09-15
Has anyone else had display and layout problems, possibly related to JavaScript? I had a serious <marquee> problem, which was fixed with today's [build]("http://snapshot.opera.com/unix/snapshot-1581"). However, I am still experiencing problems with phpmyadmin, specifically in the table pages, where the menu above appears vertically instead of hoizontially and with weird colours.

---

### Post by Ledah on 2007-09-15
Has someone tested the build with Gutsy? In Feitsy Opera looked great, but in Gutsy it still looks like the forced 32-bit Opera.

---

### Post by angryfirelord on 2007-09-15
In gutsy, the 64-bit flashplugin-nonfree package is wrapped with nspluginwrapper. This works with 64-bit firefox, so you could possibly get it working with 64-bit Opera.

---

### Post by kansei on 2007-09-15
I had Opera 9.50 installed, but it replaced 9.2x instead of installing alongside it .. bah

I miss having shift +f6 to arrange all open windows in a tile fashion. On a very high res display (3360x2100) it's nice to have opera maximixed and be able to see 4-8 web pages simultaneously

And though I had nspluginwrapper installed and working (through the gutsy repos) with 64-bit firefox, it didn't work with Opera 9.5 (probably because the nspluginwrapper scripts weren't updated now that there is 64-bit Opera on the Horizon.

---

### Post by Ledah on 2007-09-15
Some shortcuts were adapted to Firefox/IE, but they can be changed (Tools -> Preferences -> Advanced -> Shortcuts).

---

### Post by jpkotta on 2007-09-15
Seems like GMail doesn't work yet. That's a deal-breaker for me.  I'm really looking forward to that synchronize feature, though.

---

### Post by Nameless_one on 2007-09-16
Why doesn't it work? It works for me, although in HTML mode. I think there are still some problems with JavaScript with the new version, which is odd, as the old JavaScript implementation worked fine. I wonder if they rewrote it.

---

### Post by kansei on 2007-09-17
> **Ledah said:**
> Some shortcuts were adapted to Firefox/IE, but they can be changed (Tools -> Preferences -> Advanced -> Shortcuts).

Since I'm back on 9.2x, can you confirm that you can put it back to 'opera style shortcuts' or that shift+f6 to tile windows is one of them? I'll give it a try tonight either way, so no worries

---

### Post by netimen on 2007-09-17
so has anybody managed to load gmail not in HTML mode?

---

### Post by Ledah on 2007-09-21
The next weekly is available. Gmail is working now.

---

### Post by Colonel Kilkenny on 2007-09-21
Btw.
I don't know what is the current situation with Opera 9.50 64-bit and Flash but if I have understood correctly the nspluginwrapper is not needed with Opera. Operapluginwrapper which runs automatically with Opera is basically doing the same thing if 64-bit version is in use.

---

### Post by Cappy on 2007-09-22
If anyone is wondering the link for the weekly snapshot is here:
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

64-bit (THIS SNAPSHOT CANNOT RUN FLASH - USE THE NON WEEKLY 9.50 ALPHA):
[http://snapshot.opera.com/unix/snapshot-1589/x86_64-linux/opera_9.50-20070920.2-shared-qt_amd64.deb](http://snapshot.opera.com/unix/snapshot-1589/x86_64-linux/opera_9.50-20070920.2-shared-qt_amd64.deb)

32-bit:
[http://snapshot.opera.com/unix/snapshot-1589/intel-linux/opera-static_9.50-20070920.9-static-qt_i386.deb](http://snapshot.opera.com/unix/snapshot-1589/intel-linux/opera-static_9.50-20070920.9-static-qt_i386.deb)

---

### Post by Ledah on 2007-09-22
> **Colonel Kilkenny said:**
> Btw.
I don't know what is the current situation with Opera 9.50 64-bit and Flash but if I have understood correctly the nspluginwrapper is not needed with Opera. Operapluginwrapper which runs automatically with Opera is basically doing the same thing if 64-bit version is in use.

Flash doesn't work with Opera 64-bit. There's actually no way to get it running.

---

### Post by Cappy on 2007-09-22
> **Ledah said:**
> Flash doesn't work with Opera 64-bit. There's actually no way to get it running.

Confirmed. I tried a few different ways with the new snapshot but it always just renders as a grey box.

---

### Post by Case_f on 2007-09-22
> **Ledah said:**
> Flash doesn't work with Opera 64-bit. There's actually no way to get it running.

Check this out. It works like a charm (of course, you need to install ia32-libs and ia32-libs-kde, if you don't have them already)

[http://my.opera.com/community/forums/topic.dml?id=206201&t=1190421761&page=1](http://my.opera.com/community/forums/topic.dml?id=206201&t=1190421761&page=1)

---

### Post by Nameless_one on 2007-09-23
Yay! This trick worked for me too :) I will try to make java work too! Thank you for the link, Case_f!

---

### Post by Cappy on 2007-09-23
Here is the run down of the different Opera problems:

Opera 9.50 alpha:
Some pictures don't load for me until I keep right clicking on the picture and clicking load over and over.

Opera weekly snapshot:
Copying from Opera to most other programs is broken. Can only copy to gedit. Trying to copy to gaim crashes gaim.
Flash is broken for the 64-bit version (or so someone said).

---

### Post by Ledah on 2007-09-23
> **Nameless_one said:**
> Yay! This trick worked for me too :) I will try to make java work too! Thank you for the link, Case_f!

Have you installed 64-bit plugins, too? Do they work with this workaround?

---

### Post by Case_f on 2007-09-23
They don't work here, but it's not a big deal for me right now (all I really need is Flash). However, as I've found out (and reported on the my.opera thread), there's a catch with Opera 9.5 and Flash, at least in my case - Opera builds 1567 and 1581 work fine with the non-beta Flash plugin (r48 ), but don't work with the latest Flash beta (r60). The latest Opera build 1589 works fine with r60, but in exchange doesn't work with r48 and older. YMMV, I guess.

---

### Post by Nameless_one on 2007-09-27
I have the latest Opera build, and I think I downloaded the latest flash too, and they work fine. I have no 64-bit plugins.

---

### Post by Nameless_one on 2007-09-29
Does anyone experience random crashes with the [latest](http://my.opera.com/desktopteam/blog/show.dml/1371210) build?

---

### Post by Ledah on 2007-09-29
No, works better than the built before for me.

---

### Post by Case_f on 2007-09-29
Same here (the flash mysteries are gone and Opera is more responsive overall)

---

### Post by lonrot on 2007-10-12
> **Case_f said:**
> Check this out. It works like a charm (of course, you need to install ia32-libs and ia32-libs-kde, if you don't have them already)

[http://my.opera.com/community/forums/topic.dml?id=206201&t=1190421761&page=1](http://my.opera.com/community/forums/topic.dml?id=206201&t=1190421761&page=1)

Hey that page is not longer available, could you type what did you do to install flash. I do have the ia32 libs.

---

### Post by Case_f on 2007-10-12
It is still available, just checked.

---

### Post by vgrisham on 2007-11-08
> **Ledah said:**
> No, works better than the built before for me.

Case, I'm a noob to Opera. Would you mind posting a step-by-step of how you got Opera to work with Flash and Java. I have installed the Alpha, but neither has worked out of the box.

Thank you very much.

---

### Post by arthyko on 2007-11-08
Check [THIS]("http://snapshot.opera.com/unix/snapshot-1636/x86_64-linux/")

---

### Post by vgrisham on 2007-11-09
> **arthyko said:**
> Check [THIS]("http://snapshot.opera.com/unix/snapshot-1636/x86_64-linux/")

Thanks arthyko. I had no trouble finding and installing it from deb. It's just that flash and java are not working and I don't know where to begin to get them to work.

---

### Post by wolfen69 on 2007-11-27
i found a .deb file for Opera alpha-1  9.50 [http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/](http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/)

it seems to work well. this was just a heads up for those that were wondering about Opera in 64. i'm using ubuntu64 Gutsy.

Edit: here is the latest Opera64 [ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)

---

### Post by ZachSka87 on 2007-11-28
Thanks man, I was just looking for this!

---

### Post by sirdilznik on 2007-11-29
Holy smokes, this is really, really good so far!  I've never been an Opera man, but this may just change my mind.  Either way, I have a shiny new toy to play with :mrgreen:

---

### Post by Crinos512 on 2007-11-29
Any chance this will get ...Deb-ulized and put in the repo like Nswrapper?

or maybe have the Opera Developers set this behavior by default?

---

### Post by iam1e5 on 2007-11-29
hi there
i downloaded the tar.gz file
any1 can teach me how do i go around installing opera?

---

### Post by Crinos512 on 2007-11-29
grab the .deb file from [here]("http://snapshot.opera.com/unix/snapshot-1678/x86_64-linux/") instead.

from there you should be able to double click on it and install. :)

---

### Post by iam1e5 on 2007-11-29
> **Crinos512 said:**
> grab the .deb file from [here]("http://snapshot.opera.com/unix/snapshot-1678/x86_64-linux/") instead.

from there you should be able to double click on it and install. :)
thx a lot!
didnt realise there a deb file
thx!

---

### Post by myo on 2007-11-30
fyi guys 64bit opera with flash has been working great for me. 
this may have been posted on here somewhere already, but here you go:

installed the deb from [ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/).
downloaded the 32-bit opera.tar.gz from the opera site, copy the 32-bit operapluginwrapper to /usr/lib/opera/9.50-20071024.2/operapluginwrapper

then download the 32-bit flash 9 linux tar.gz, and copy libflashplayer.so to /usr/lib/opera/plugins/libflashplayer.so

seems to be working great for me. and no mucking with lib32 or chroots or anything. thanks to [this blog post](http://my.opera.com/csant/blog/2007/10/26/32-bit-plugins-in-64-bit-opera) for inspiration,

I still can't get java, or mplayer plugins working in opera. any ideas?

---

### Post by avik on 2007-11-30
Wow!  I just installed Opera from [ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/]("ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/"), and Flash works out of the box!  That was weird.  I didn't have to do a thing.

I'm running Gutsy amd64.

---

### Post by unityofsaints on 2007-11-30
Hmm the new snapshot is out [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) but they forgot about AMD64 users. Last time they made a .deb, to busy to care about us this time :(

---

### Post by Crinos512 on 2007-11-30
Yeah, I complained about that on the blog.... who knows maybe the'll remember right quick?

---

### Post by John Jason Jordan on 2007-12-01
> **Crinos512 said:**
> Yeah, I complained about that on the blog.... who knows maybe the'll remember right quick?
I have:
Version 9.50 Beta 2
Build 1678
Platform Linux
System x86_64, 2.6.22-14-generic
Qt library 3.3.7
Java Java Runtime Environment installed

What is the latest version?

---

### Post by arthyko on 2007-12-02
Hi, I've the same version as you, is there any chance to translate it into spanish?

---

### Post by John Jason Jordan on 2007-12-02
> **arthyko said:**
> Hi, I've the same version as you, is there any chance to translate it into spanish?
Para Opera en español necesitas ir aquí:

[http://www.opera.com/download/languagefiles/](http://www.opera.com/download/languagefiles/)

---

### Post by inphektion on 2008-01-20
Latest 64-bit opera can be grabbed from here:
[http://snapshot.opera.com/unix/snapshot-1766/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1766/x86_64-linux/)

works great.  I still need to install the flash plugin somehow...

---

### Post by vgrisham on 2008-01-20
Thanks for the update. Any ideas on installing Flash?

---

### Post by John Jason Jordan on 2008-01-21
> **vgrisham said:**
> Thanks for the update. Any ideas on installing Flash?
I installed Opera 9.5 beta a couple months ago and flash just worked all by itself. The only thing I can say is that this was a fresh install of Gutsy x86_64 on a brand new laptop. Gutsy automatically installed Firefox, and I went into  I had already installed Firefox and I went into System > Administration > Restricted Drivers Manager and installed flash. I am guessing that the fact that flash was already installed and working in Firefox meant that Opera just used flash automatically as well.

---

### Post by wingnux on 2008-01-21
Cool! Flash works out-of-the-box with this new build! =)

---

### Post by vgrisham on 2008-01-21
> **wingnux said:**
> Cool! Flash works out-of-the-box with this new build! =)

It sure didn't for me. :(

When I go to a site that requires flash, I get this message: You need to install the Macromedia Flash Player plug-in to view all content on this page. Do you want to download this plug-in now?

If I click yes, it takes me to Adobe's Flash site, which of course doesn't offer a 64-bit flash plugin. 

Anyone got any ideas?

---

### Post by inphektion on 2008-01-21
I just followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

and downloaded the old plugin.  after I ran GetFlash script I opened opera and the plugin was there.  you can check for the plugin by going to Tools-> advanced -> plugins or search for it under Tools -> Preferences then Content, then click Plug-in options button.

---

### Post by inphektion on 2008-01-25
New opera 64bit snapshot:
[http://snapshot.opera.com/unix/snapshot-1772/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1772/x86_64-linux/)

**Changelog:**
[LIST]
[*]Even more Gmail2 fixes, getting closer to working
[*]More presice rounding of HSL values in CSS
[*]Playing video on CNN works again
[*]Adding links to walls on Facebook now works
[*]Login to Open-Xchange now works
[*]Fixed various issues on Windows Live Mail
[*]Saving playlists on YouTube should now function correctly
[*]User style mode no longer applies to Mail or IRC tabs
[*]Several favicon fixes
[*]Fixed the line below dialog tabs in native skins
[*]Tweaking and improvements to Windows native skins (both themed and classic) based on feedback and bug reports
[*]Fixed a problem with wrong handling of some filetypes, including messed up display of MHTML. This was actually fixed in the last weekly, but we forgot to mention. If you upgrade from an older snapshot using the same installation directory, you must remove the [File Types] section in opera6.ini.
[*]Mac: Fixed color corruption when copying images (and preserve the alpha channel)
[*]Mac: Possibly fixed printing crashes on Leopard
[*]UNIX: Plugins in symlinked directories should now not be listed twice
[/LIST]

---

### Post by konungursvia on 2008-01-26
I don't know why it's still an alpha.... I've been running this for a couple of months, and it is rock solid, perfect, for me.

---

### Post by inphektion on 2008-01-26
Actually these snapshots are post beta1 code now.  I agree its not bad but there are still enough bugs it isn't ready for release.

---

### Post by bgivens33 on 2008-01-29
just converted to opera from firefox... firefox was killing my memory and I don't have that much to spare.  Seems to be running flawless with flash working nicely.  This speed dial thing is interesting... liking the change so far.

edit: first post in almost 2 years ;)

---

### Post by Bokonon on 2008-02-12
I also use Opera when memory is tight.  Firefox when my prime function is browsing, but when I am working and checking links/researching, I use opera or epiphany.

Both really help out on the memory usage keeping memory free for doing other things.

---

### Post by kiroro on 2008-03-23
I use Opera as my primary browser. Actually I used Opera as primary browser in Windows too, haha. I think the current version is Beta 2. I like it but it is not even close as stable as the windows version. It crushes about 10 times per day now...especially when I open a lot of tabs which I usually do...

---

### Post by gfg on 2008-03-23
I have also had problems with Opera lately, and have switched to Firefox 3, at least for now. Thus far it has been more stable than opera. It's unlikely I will switch back in the near future as I don't see any compelling reasons to do so yet.

---

### Post by kiroro on 2008-03-23
I feel Opera is a lot faster when opening some websites than Firefox. Maybe I am having problems with my Firefox 2 coz it pauses and grays-out when opening some webistes...

---

### Post by TimelessRogue on 2008-03-23
Well okay then ... downloaded/installed 9.5 Alpha 64 from their site ... and it's great!  Fast as fast can be on all sites I've visited so far.  Definitely a step up ... or more ... from the Opera I used a couple of years or so ago ... or Firefox for that matter.  Gotta say at this point that this will probably be my browser of choice ...

---

### Post by darco on 2008-03-24
I am using HH x64 and Opera opens fine but when I go to gmail and log in, Opera shuts down. Same if I use the Ebay bookmark already provided.
I am using Opera 9.50 Beta 2..is this a plug in issue?

darco

---

### Post by Blario on 2008-04-23
Where I get opera 64 bit?  I've looked on the opera site and I only see i386 there...

---

### Post by ogregore on 2008-04-23
Try this:

[http://snapshot.opera.com/unix/snapshot-1929/x86_64-linux/opera_9.50-20080417.2-shared-qt_amd64.deb](http://snapshot.opera.com/unix/snapshot-1929/x86_64-linux/opera_9.50-20080417.2-shared-qt_amd64.deb)


or you may be able to find Beta 2 here:  (not sure if the 64bit is here)

[ftp://ftp.opera.com/pub/opera/linux/950b2/](ftp://ftp.opera.com/pub/opera/linux/950b2/)

Cheers
Ogre

---

### Post by Blario on 2008-04-24
Thanks so much!

As of today, the latest at the second link that you gave is:
[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/opera_9.50b2-20080422.2-shared-qt_amd64.deb](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/opera_9.50b2-20080422.2-shared-qt_amd64.deb)

---

### Post by AbredPeytr on 2008-05-02
Using Hardy 64-bit and installed Opera 64-bit. Followed suggestions from another post about Opera 32-bit and Java that said to delete the files in the java folder and re-install jave (restricted format). I'm one step closer to having it working. I get sound, uninterrupted loud and clear, just the video on You Tube is not shown.

Any other suggestions?

---

### Post by 3ntity on 2008-05-06
> **AbredPeytr said:**
> Using Hardy 64-bit and installed Opera 64-bit. Followed suggestions from another post about Opera 32-bit and Java that said to delete the files in the java folder and re-install jave (restricted format). I'm one step closer to having it working. I get sound, uninterrupted loud and clear, just the video on You Tube is not shown.

Any other suggestions?@AbredPeytr: YouTube uses Flash, not Java (maybe that's what you meant tho). You could try doing what I did to get Flash working, hope it works for you:


:) Finally got Flash working in 9.50 beta 2 under Hardy x64.

Somehow, I'd manually installed the Flash plugin from Adobe's site, as well as flashplugin-nonfree through Synaptic (after adding some repos). 
Going to Tools -> Preferences -> Advanced -> Content, I saw 'Enable plug-ins' checked. I clicked 'Plug-in options' and noticed Shockwave Flash was available, even tho e.g. YouTube didn't work. 3 plugin paths were displayed tho, so I clicked on 'Change Path' and **deselected** /usr/lib/opera/plugins and /usr/lib/mozilla/plugins, leaving only /usr/lib/flashplugin-nonfree **selected**. I 'OK'ed all dialogs, restarted Opera, and guess what, Flash worked :) 

Sometimes YouTube videos won't load (leaving a white square where the video's supposed to be displayed), but simply reloading the page seems to resolve this issue.

Glad to no longer be dependent on Firefox for all things Flash :)

---

### Post by AbredPeytr on 2008-05-08
Hi 3ntity,

thanks for your post! It helped a lot (including pointing out to me how senile I've become). I know when I was typing "jave" something was quite right with my post.

I followed your suggestion somewhat and unchecked the box in front of mozilla..., restarted Opera and low and behold, flash works with Opera 64-bit!!!

Thank you!

Sweet! The Official Dilbert widget in iGoogle works!

---

### Post by 3ntity on 2008-05-10
> **AbredPeytr said:**
> Hi 3ntity,
...
I followed your suggestion somewhat and unchecked the box in front of mozilla..., restarted Opera and low and behold, flash works with Opera 64-bit!!!

Thank you!
... Glad to hear this, and you're very welcome :)

---

### Post by meho_r on 2008-05-10
> **Blario said:**
> Thanks so much!

As of today, the latest at the second link that you gave is:
[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/opera_9.50b2-20080422.2-shared-qt_amd64.deb](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/opera_9.50b2-20080422.2-shared-qt_amd64.deb)

Thanks for the link :D

---

### Post by 3ntity on 2008-06-13
Opera 9.50 final is out at [www.opera.com/download](www.opera.com/download), direct link: [http://www.opera.com/download/get.pl?id=31366&location=211&nothanks=yes&sub=marine](http://www.opera.com/download/get.pl?id=31366&location=211&nothanks=yes&sub=marine) (hope this works)

---

### Post by John Jason Jordan on 2008-06-13
> **3ntity said:**
> Opera 9.50 final is out at [www.opera.com/download](www.opera.com/download), direct link: [http://www.opera.com/download/get.pl?id=31366&location=211&nothanks=yes&sub=marine](http://www.opera.com/download/get.pl?id=31366&location=211&nothanks=yes&sub=marine) (hope this works)
Just tried both links, which downloaded the same file. However, when I opened it in gDebi I got an error message; Error: A later version is already installed. And the version I have installed is from some months ago:

Version 9.50 Beta 2
Build 1800
Platform Linux
System x86_64, 2.6.24-18-generic
Qt library 3.3.8b
Java Java Runtime Environment installed

I don't understand. gDebi must be confused.

---

### Post by kevver on 2008-06-14
The same thing happens to me with the 32 bit version, even if I save it and run it.

---

### Post by inphektion on 2008-06-14
> **kevver said:**
> The same thing happens to me with the 32 bit version, even if I save it and run it.

Yea just uninstall the old .deb.
Opera changed versioning so it confused the deb.
dpkg -r opera

---

### Post by mhenriday on 2008-06-14
Interesting ! I had no difficulty whatever convincing GDebi to install **Opera 9.50** on my 64-bit box. But that may have been because I didn't have the older 32-bit version installed. Here, perhaps, an uninstallation - either via Synaptic or a terminal - followed by a new download and installation would do the trick....

Henri

---

### Post by John Jason Jordan on 2008-06-14
> **inphektion said:**
> Yea just uninstall the old .deb.
Opera changed versioning so it confused the deb.
dpkg -r opera
OK, that worked.

Now that I have the final I notice that flash is working automatically. We'll see over the next few days if everything else is stable.

---

