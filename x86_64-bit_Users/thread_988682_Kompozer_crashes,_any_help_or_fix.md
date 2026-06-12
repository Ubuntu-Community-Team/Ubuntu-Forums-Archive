---
title: "Kompozer crashes, any help or fix?"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by kystorms on 2008-11-20
I am running Intrepid on a 64 bit machine, and desperately need a WYSIWYG html editor ( KOMPOZER)  that is similar to kompozer. I can not keep kompozer open it constantly just closes on me.

any help or fixes for this yet?

thank you
:KS

---

### Post by Mancman on 2008-11-21
Same problems here  :(

Crashes constantly when using the mouse, though I find it doesn't crash as much when using just the keyboard to navigate the menus   :confused:

---

### Post by Yownanymous on 2008-11-21
Well that's KDE's problem, surely.

---

### Post by kystorms on 2008-11-21
> **Mancman said:**
> Same problems here  :(

Crashes constantly when using the mouse, though I find it doesn't crash as much when using just the keyboard to navigate the menus   :confused:

well i am just using Sea Monkey and actually its a bit easier for someone like me who is not totally cool with html yet. I just wish there was an icon to start the program instead of having to open seamonkey AND then open the composer.
still , it is a nice program and works great.

:KS

---

### Post by kleeman on 2008-11-21
> **kystorms said:**
> well i am just using Sea Monkey and actually its a bit easier for someone like me who is not totally cool with html yet. I just wish there was an icon to start the program instead of having to open seamonkey AND then open the composer.
still , it is a nice program and works great.

:KS
Create a custom application in the gnome bar and use the following Command 

seamonkey -edit

---

### Post by kystorms on 2008-11-21
> **kleeman said:**
> Create a custom application in the gnome bar and use the following Command 

seamonkey -edit


thanks!!!

:KS

---

### Post by apostate on 2008-11-29
> **Yownanymous said:**
> Well that's KDE's problem, surely.

Um...no. Kompozer has nothing to do with KDE. I have the same problem. In Intrepid, under Gnome.

---

### Post by mutzinet on 2008-11-29
Same problem here: Kompozer is totally unusable, crashes all the time. (Intrepid 32bits with KDE)

Any way around this problem?

---

### Post by philinux on 2008-11-29
Yes, two solutions.

1. Kompozer for windows runs perfectly under wine.
2. Seamonkey suite uses composer which again is very stable.

---

### Post by jmacx81 on 2008-11-29
Firefox 3 seems to be running great. Not sure how it will work on KDE though.

---

### Post by sippligood on 2008-12-10
FIX: You just have not to use Synaptic to get Kompozer. Instead get the latest release from the kompozer-website
[http://kompozer.net/zip/](http://kompozer.net/zip/)
and download, unpack and start it. No install or compilation needed.
Check here:
[http://nyuviu.wordpress.com/2008/12/...der-usb-stick/](http://nyuviu.wordpress.com/2008/12/...der-usb-stick/) (in German only but with pics)

or follow Bruce:
[https://bugs.launchpad.net/ubuntu/+s...41/comments/40](https://bugs.launchpad.net/ubuntu/+s...41/comments/40)

No crashing anymore . You may even use it from usb-stick.

Regards Sippligood

---

### Post by kleeman on 2008-12-11
Works for me on an amd64 system thanks!

---

### Post by stchman on 2008-12-11
I run Kompozer on Ubuntu Hardy 64 bit with no problem.  Try running Kompozer in a terminal.  If it crashes hopefully the developers print out messages when a crash is detected.

---

### Post by Stunts on 2008-12-12
> I run Kompozer on Ubuntu Hardy 64 bit with no problem. Try running Kompozer in a terminal. If it crashes hopefully the developers print out messages when a crash is detected.

I second that. It also runs fine on my Hardy x64. Maybe a bug should be filed for intrepid if it's affecting many people...

---

### Post by AuronGrande on 2008-12-13
I am using Intrepid with Gnome and Komposer crashes on me. Even though I know a fair amount of XHTML and CSS I still need a WYSIWYG editor.

I am new to Linux and so I have no idea how to run the program through Terminal so that I can get a report from it.

Can anyone tell me how to do so?

---

### Post by AuronGrande on 2008-12-13
Never mind, I found out how to load Kompozer in Terminal. However, when the program closes when browsing the menus, it simply says "Segmentation fault", nothing else.

---

### Post by fabiwan on 2008-12-17
Hi,

KompoZer 0.7.10 is built upon Gecko 1.7, which isn't compatible with GTK 2.14. This is why it runs fine on Hardy but crashes on Intrepid.

I'm porting KompoZer to Gecko 1.8.1. Half of the job is done, it's pretty stable — nobody could crash it so far — but some features are missing at the moment. On the 'plus' side, there are a few new features that I like a lot: source dock, DOM navigation…

Intrepid users, you can try an alpha version here: [http://kompozer.net/zip/kompozer-20081217.tar.gz](http://kompozer.net/zip/kompozer-20081217.tar.gz)
Download, unzip somewhere (e.g. in ~/Applications) and launch the 'kompozer' script to start the app.

There should be a public release in January.
This bug is filed in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441](https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441)

-Kazé, KompoZer's developer and happy Hardy user.

---

### Post by klausner on 2008-12-23
> **fabiwan said:**
> Hi,

KompoZer 0.7.10 is built upon Gecko 1.7, which isn't compatible with GTK 2.14. This is why it runs fine on Hardy but crashes on Intrepid.

<redacted>

Intrepid users, you can try an alpha version here: [http://kompozer.net/zip/kompozer-20081217.tar.gz](http://kompozer.net/zip/kompozer-20081217.tar.gz)
Download, unzip somewhere (e.g. in ~/Applications) and launch the 'kompozer' script to start the app.


I downloaded the alpha version, and based on a quick test, it does seem to work with Intrepid. Thanks.

But I noticed that the source tab is gone. I sometimes do large cut/pastes of HTML source, and the new source mini-window will be much more awkward. Is there an option to revert to the previous behavior?

P.S. With 20/20 hindsight, I should have stayed with Hardy LTS too.

---

### Post by tomdkat on 2008-12-24
> **fabiwan said:**
> Hi,

KompoZer 0.7.10 is built upon Gecko 1.7, which isn't compatible with GTK 2.14. This is why it runs fine on Hardy but crashes on Intrepid.

I'm porting KompoZer to Gecko 1.8.1. Half of the job is done, it's pretty stable — nobody could crash it so far — but some features are missing at the moment. On the 'plus' side, there are a few new features that I like a lot: source dock, DOM navigation…

Intrepid users, you can try an alpha version here: [http://kompozer.net/zip/kompozer-20081217.tar.gz](http://kompozer.net/zip/kompozer-20081217.tar.gz)
Download, unzip somewhere (e.g. in ~/Applications) and launch the 'kompozer' script to start the app.

There should be a public release in January.
This bug is filed in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441](https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441)

-Kazé, KompoZer's developer and happy Hardy user.Sweet!  Thanks!  :guitar:

Peace...

---

### Post by fabiwan on 2008-12-28
> **klausner said:**
>  I noticed that the source tab is gone. I sometimes do large cut/pastes of HTML source, and the new source mini-window will be much more awkward. Is there an option to revert to the previous behavior?
 No, at least not yet. Re-implementing this source tab would require quite a lot of work, so I probably won't do it unless it appears to be necessary. Besides, this source tab was the source of ~50% of the crashes and most of the data losses.

So far, most testers prefer this new “source dock” than the old source tab (you're the second user complaining about it). I also think this source dock will make much more sense than the old source tab, but I agree it takes a while to get used to it.
If you want to copy/paste large portions of HTML markup, you'll have to click on a parent element in the status bar (e.g. <body>). In the latest builds there's also a DOM sidebar to navigate easily in the HTML source.

If I can't make it easier to use I'll work on re-implementing the source tab, but it's at the bottom of my TODO-list at the moment.

---

### Post by dcstar on 2008-12-30
> **fabiwan said:**
> Hi,

KompoZer 0.7.10 is built upon Gecko 1.7, which isn't compatible with GTK 2.14. This is why it runs fine on Hardy but crashes on Intrepid.
.......

There should be a public release in January.
This bug is filed in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441](https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441)

-Kazé, KompoZer's developer and happy Hardy user.

Ouch!, another reason for me to stay on 8.04.......for a while longer....

---

### Post by girark on 2009-01-01
Same problem. I'm running Ubuntu 8.10. I launch Kompozer by double clicking the Kompozer script file, and the tip of the day shows up, but when I click on a menu item, the program disappears.

I was never able to ./configure or make or make install (some instructions said I needed to, others said I didn't - when I tried, I got error messages). I am still looking for the real instructions on how to get it running with stability. Thoughts?

***UPDATE: I don't think it's an install issue on my end. Only certain menu items cause crash. "Insert" and "Format" cause program to crash as soon as an option is highlighted, but "File" and "Edit" seem to work fine. Bug?

---

### Post by brundlelinux on 2009-01-16
Just wanted to chime in with my experience.  It would seem to me that this is PURELY a software issue and not user incompetence.

I used Kompozer with great delight back on Hardy.  Then I didn't use it for a bit because I had no need.  After upgrading to Intrepid, I had use again, and immediately had issues as described in the above posts.  Either from the terminal or from the start menu, the same issues.... format and insert caused immediate crashes.

I recently got a new computer and installed Kubuntu Intrepid.  It's the exact same over there from a fresh install.

I'm no computer guru or anything, but based on my experience, I'd say (with confidence) that this is an Intrepid issue.  The post about it being based on a version of Gecko which doesn't work in Intrepid also seems to make a lot of sense, based on that.

I'm going to totally remove Kompozer and go for for the version straight from the developer later this evening, and I'll report back after that.

---

### Post by klausner on 2009-01-16
> **brundlelinux said:**
> 
I'm no computer guru or anything, but based on my experience, I'd say (with confidence) that this is an Intrepid issue.  The post about it being based on a version of Gecko which doesn't work in Intrepid also seems to make a lot of sense, based on that.

Read the earlier part of the thread. It's actually a GTK versioning issue.

---

### Post by yyyc186 on 2009-02-01
I have the same problem with kompoZer.  It crashes bad now.  64-bit AMD 8.10 with all updates applied.  Gnome or KDE matters not.  This baby dies hard without even generating an error message.

Does anyone know if it writes to any of the system logs so we could turn in the results to the development team.

As a result I have been hand editing HTML using Komodo Edit 5.0.

---

### Post by Erlander on 2009-02-02
Have a look at Post #11 on page 2.  It works for me.

---

### Post by angelsneverdie on 2009-02-03
I had installed kompozer and it would crash randomly.  I'm using Ubuntu 8.10.  So i followed the advice of some and removed it from the system, went to the kompozer website and downloaded the tar.gz - extracted it, and ran the script file without installing it.  Guess what?  it crashed.

the error i always get in the command line is:  segmentation fault

i don't know if it gives an error when it crashes after running the script file, as i don't know how to run that from the terminal, but it is the same behavior.

I don't know if it is just me, but i'm getting more and more frustrated with ubuntu.  I love it for the most part, but nothing seems to just work.

anyone have any ideas?

---

### Post by tomdkat on 2009-02-04
> **fabiwan said:**
> I'm porting KompoZer to Gecko 1.8.1. Half of the job is done, it's pretty stable — nobody could crash it so far — but some features are missing at the moment. On the 'plus' side, there are a few new features that I like a lot: source dock, DOM navigation…

Intrepid users, you can try an alpha version here: [http://kompozer.net/zip/kompozer-20081217.tar.gz](http://kompozer.net/zip/kompozer-20081217.tar.gz)
Download, unzip somewhere (e.g. in ~/Applications) and launch the 'kompozer' script to start the app.

There should be a public release in January.
This bug is filed in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441](https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441)
This download doesn't seem to be available anymore.  What's the status of an updated public release?

Thanks!

Peace...

---

### Post by dcstar on 2009-02-05
New version (0.8a1) download link:

[http://sourceforge.net/projects/kompozer/](http://sourceforge.net/projects/kompozer/)

---

### Post by fabiwan on 2009-02-17
More information about KompoZer 0.8 alpha1 here: [http://kazhack.org/?post/2009/02/10/KompoZer-0.8a1](http://kazhack.org/?post/2009/02/10/KompoZer-0.8a1)
You’ll find a description of the new features and some instructions to install it on Ubuntu Intrepid or Jaunty.

A DEB package should be available in a few days.
I’m afraid this version will *never* make it into the Intrepid repositories. I’m doing my best to get it included in Jaunty, but that might be too late already.

---

### Post by crjackson on 2009-02-17
> **fabiwan said:**
> A DEB package should be available in a few days. I’m afraid this version will *never* make it into the Intrepid repositories. I’m doing my best to get it included in Jaunty, but that might be too late already.

I can't wait for the DEB. Perhaps it could be posted to getdeb.net, or even a ppa so we can sudo apt-get install.

Can't wait...

---

### Post by fabiwan on 2009-02-17
It will be on PPA pretty soon, maybe tomorrow. ;-)
Keep in mind it&#8217;s still an alpha release, lots of bugs still need to be addressed &#8212; but at least it won&#8217;t crash.

---

### Post by bodhi.zazen on 2009-02-17
> **fabiwan said:**
> More information about KompoZer 0.8 alpha1 here: [http://kazhack.org/?post/2009/02/10/KompoZer-0.8a1](http://kazhack.org/?post/2009/02/10/KompoZer-0.8a1)
You’ll find a description of the new features and some instructions to install it on Ubuntu Intrepid or Jaunty.

A DEB package should be available in a few days.
I’m afraid this version will *never* make it into the Intrepid repositories. I’m doing my best to get it included in Jaunty, but that might be too late already.

Thank you for that ;)

---

### Post by Derevko on 2009-02-18
Hi,

I'm preparing a KompoZer package for Debian. I Uploaded my preliminary work in my PPA for Ubuntu users:

Jaunty:

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main


Intrepid: not yet build, will be available in the next hours

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) intrepid main


Hardy: not yet build, will be available in the next hours

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) hardy main


Feedbacks are welcome :)

Cheers,
Giuseppe.

---

### Post by crjackson on 2009-02-18
> **Derevko said:**
> Hi,

I'm preparing a KompoZer package for Debian. I Uploaded my preliminary work in my PPA for Ubuntu users:

Jaunty:

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main


Intrepid: not yet build, will be available in the next hours

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) intrepid main


Hardy: not yet build, will be available in the next hours

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) hardy main


Feedbacks are welcome :)

Cheers,
Giuseppe.

Excellent, and thanks.  I'll jump right on this tomorrow after work.

---

### Post by dcstar on 2009-02-21
> **Derevko said:**
> Hi,

I'm preparing a KompoZer package for Debian. I Uploaded my preliminary work in my PPA for Ubuntu users:
..........
Hardy: not yet build, will be available in the next hours

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) hardy main


Feedbacks are welcome :)

Cheers,
Giuseppe.

The version string you have used displays as an earlier version that the one in the Ubuntu repository: **1:0.7.10-0Ubuntu4 (hardy)**.

I suggest a recompile with the version string in the Ubuntu format so it is identified as a later version by the package manager.

Thanks for taking the time and effort to do these.

---

### Post by Derevko on 2009-02-22
> **dcstar said:**
> The version string you have used displays as an earlier version that the one in the Ubuntu repository: **1:0.7.10-0Ubuntu4 (hardy)**.


Oh right, Ubuntu official version has an epoch, added. Thanks!

---

### Post by tomdkat on 2009-02-22
> **dcstar said:**
> New version (0.8a1) download link:

[http://sourceforge.net/projects/kompozer/](http://sourceforge.net/projects/kompozer/)Thanks for the link!

> **fabiwan said:**
> More information about KompoZer 0.8 alpha1 here: [http://kazhack.org/?post/2009/02/10/KompoZer-0.8a1](http://kazhack.org/?post/2009/02/10/KompoZer-0.8a1)
You’ll find a description of the new features and some instructions to install it on Ubuntu Intrepid or Jaunty.

A DEB package should be available in a few days.
I’m afraid this version will *never* make it into the Intrepid repositories. I’m doing my best to get it included in Jaunty, but that might be too late already.Thanks for the update!  :)

Peace...

---

### Post by dcstar on 2009-02-23
> **Derevko said:**
> Oh right, Ubuntu official version has an epoch, added. Thanks!

Unfortunately your .deb will not work on my 8.04 system.

Firstly the install of the kompozer-data package fails because it cannot overwrite a .png file, but once I get around that and complete the install (by removing my previous kompozer package) I cannot login to my FTP web site - it just hangs.

Completely removing your packages and then reinstalling the repository Kompozer restores normal functionality.

---

### Post by fabiwan on 2009-02-23
> **dcstar said:**
> I cannot login to my FTP web site - it just hangs.That’s a bug in KompoZer 0.8a1, not in the DEB package. To be corrected soon.

If you’re using Hardy and if you’re looking for a stable version, you should stick to KompoZer 0.7.10 until the final 0.8 version is released.
KompoZer 0.8a1 is the only version working on GTK 2.14 (i.e. with Intrepid or Jaunty) but it’s still in alpha stage.

---

### Post by crjackson on 2009-03-08
Any updates? I've added your PPA to my Hardy install and I see nothing is available just yet. I haven't tried intrepid yet.

---

### Post by mistypotato on 2009-03-11
I've downloaded and am using the latest version dates 20090206 (8a1) and so far...it has not yet spontaneously closed like the last two versions I tried.

(ubuntu 8.10 Intrepid, updated yesterday).

One thing I DID notice is that I can't select the SOURCE view as I was able to in the other releases.  Note that this IS a BETA release, however so it's probably just being worked on.   

Has anyone else tried the latest release with similar (or different) results?

One thing's for absolute certain.....

If the bugs are resolved,  I WILL make a donation and I hope everyone else who uses it does the same.  A lot of people making modest donations can really add up.  There is a donate link at the SourceForge site...

Here's a link to their [[COLOR="Red"][SIZE="4"]Donate[/SIZE][/COLOR]]("http://sourceforge.net/project/project_donations.php?group_id=170132") link

I'm sure donations would motivate continued development on this VERY necessary tool.

---

### Post by da.phreak on 2009-04-07
I've been in the same situation. Version 8 doesn't work very good for me yet (although I'm looking forward for the stable release), however I've found a solution which I'd like to share with you: [Click](http://www.handwerx.net/wp-handwerx/?p=11)

---

### Post by crjackson on 2009-04-07
> **da.phreak said:**
> I've been in the same situation. Version 8 doesn't work very good for me yet (although I'm looking forward for the stable release), however I've found a solution which I'd like to share with you: [Click](http://www.handwerx.net/wp-handwerx/?p=11)

Thanks, I'll give this a try in a few days.

---

### Post by dcstar on 2009-04-08
> **da.phreak said:**
> I've been in the same situation. Version 8 doesn't work very good for me yet (although I'm looking forward for the stable release), however I've found a solution which I'd like to share with you: [Click](http://www.handwerx.net/wp-handwerx/?p=11)

Ouch, if you want to use an older GTK2 package then it would probably be better to use an Ubuntu package:

[http://packages.ubuntu.com/hardy-updates/libgtk2.0-0](http://packages.ubuntu.com/hardy-updates/libgtk2.0-0)

---

### Post by fabiwan on 2009-04-08
I’ve just published KompoZer 0.8a2: [kompozer-0.8a2-gcc4-i686.tar.gz](https://sourceforge.net/project/downloading.php?group_id=170132&filename=kompozer-0.8a2-gcc4-i686.tar.gz&a=35778284)
A lot of bugs have been corrected, among which: [list][*] broken cut/copy
[*] missing toolbar icons and other bugs in the CSS editor
[*] “getIntPref” error in the font preferences window
[*] non-working “View > HTML source” menu item[/list]There’s a little more information on my weblog: [http://kazhack.org/?post/2009/04/02/KompoZer-0.8a2](http://kazhack.org/?post/2009/04/02/KompoZer-0.8a2)

---

### Post by msoc on 2009-04-09
Ubuntu 8.10 and Kompozer 0.8a2 work together perfectly for me.
Ubuntu 8.04 and Kompozer 0.7.10 worked well but then Kompozer 0.7.10 kept crashing when I changed to Ubuntu 8.10.
I got the Kompozer 0.8a2 and this is now a much better combo than Hardy and 0.7.10 used to be.

---

### Post by crjackson on 2009-04-09
> **msoc said:**
> Ubuntu 8.10 and Kompozer 0.8a2 work together perfectly for me.
Ubuntu 8.04 and Kompozer 0.7.10 worked well but then Kompozer 0.7.10 kept crashing when I changed to Ubuntu 8.10.
I got the Kompozer 0.8a2 and this is now a much better combo than Hardy and 0.7.10 used to be.

Welcom to the Ubuntu Forums msoc, and thank you for the information.

---

### Post by crjackson on 2009-04-12
Okay, so I added the Jaunty repo and still I find no updated kompozer package. Is the repo broken or am I doing something wrong? How do I install your version on Jaunty?

I prefer the repo install method or a downloadable DEB file.

Thanks...

---

### Post by crjackson on 2009-04-12
I download the compressed file and launched the kompozer script so it seems it doesn't really NEED to be installed.

It looks very nice. I tried to insert an image into a new web page and it only inserts a place holder. What am I doing wrong, or is this a current issue with the alpha version? Thanks for you hard work. So far I can't use it but at least it doesn't crash.

---

### Post by flint_ on 2009-04-18
I just loaded kompozer-0.8a2, and while it looks very nice, the site manager does not work "out of the box".  I am running kompozer-0.8a2 from the command line after opening up the new binaries, which I presume are pre-packaging.

When I open, I see my site manager lists, but when I go to load these known good 0.7.10 version I can gain access to the site.

If I can be of any assistance with this fabiwan please let me know, as I am here in Vermont USA, and unemployed. 

Thanks again and...

Kindest Regards,

Paul Flint

---

### Post by dcstar on 2009-04-26
I notice that the kompozer 0.7.10 on my new 9.04 64-bit install seems to work fine.

---

### Post by JC Cheloven on 2009-04-28
> **crjackson said:**
> I download the compressed file and launched the kompozer script so it seems it doesn't really NEED to be installed.

It looks very nice. I tried to insert an image into a new web page and it only inserts a place holder. What am I doing wrong, or is this a current issue with the alpha version? Thanks for you hard work. So far I can't use it but at least it doesn't crash.

That's right, this is the simplest workaround. To sum up:

-> Download from the main site [http://www.kompozer.net/download.php](http://www.kompozer.net/download.php) the .tar.gz (not the .deb or whatever).

-> Uncompress it in a directory of your choice

-> From nautilus (or by any means) execute the shell script named "kompozer"

You have kompozer running without the need of even installing it. I've using it this way for several months in intrepid with no problem at all. The particular file I downloaded is kompozer-20090206.tar.gz . A newer one should also do fine, I suppose.

Note: I didn't try on jaunty so far.

---

### Post by crjackson on 2009-04-28
> **JC Cheloven said:**
> That's right, this is the simplest workaround. To sum up:

-> Download from the main site [http://www.kompozer.net/download.php](http://www.kompozer.net/download.php) the .tar.gz (not the .deb or whatever).

-> Uncompress it in a directory of your choice

-> From nautilus (or by any means) execute the shell script named "kompozer"

You have kompozer running without the need of even installing it. I've using it this way for several months in intrepid with no problem at all. The particular file I downloaded is kompozer-20090206.tar.gz . A newer one should also do fine, I suppose.

Note: I didn't try on jaunty so far.

Can YOU insert images or is it just MY setup that's having the problem?

---

### Post by fabiwan on 2009-04-28
For Christ's sake, **KompoZer 0.7.x does NOT work with Ubuntu 8.10 and newer**, it WILL crash whenever a popup is displayed. That includes sub-menus and property boxes.

Please use KompoZer 0.8-alpha instead: [http://kazhack.org/?tag/editor](http://kazhack.org/?tag/editor)
and "install" it as suggested above. The alpha3 should be ready in two or three days.

You can also use Giuseppe’s PPA account: [https://launchpad.net/~giuseppe-iuculano/+archive/ppa](https://launchpad.net/~giuseppe-iuculano/+archive/ppa)
Giuseppe is doing a great job, you can trust his PPA account at least as much as my official releases.

I do understand this is not as handy as having KompoZer in the Ubuntu repositories, but apparently the MOTU folks have decided to keep KompoZer 0.7 for Ubuntu 9.04. I’m so glad to have worked for this. :-/

> **flint_ said:**
> I just loaded kompozer-0.8a2, and while it looks very nice, the site manager does not work "out of the box".  I am running kompozer-0.8a2 from the command line after opening up the new binaries, which I presume are pre-packaging.

When I open, I see my site manager lists, but when I go to load these known good 0.7.10 version I can gain access to the site.

If I can be of any assistance with this fabiwan please let me know, as I am here in Vermont USA, and unemployed. 
I understand the lack of a remote site manager is a problem. However, the solution is not so simple, though it’s a work in progress. It should be solved with alpha4.

Flint, if you have some XUL/JavaScript knowledge you’re welcome as a contributor — feel free to ping me on #kompozer at irc.mozilla.org. If not, I’ll ping you as soon as I have something testable for the site manager.

Thanks for your proposal!

---

### Post by dcstar on 2009-05-03
> **fabiwan said:**
> For Christ's sake, **KompoZer 0.7.x does NOT work with Ubuntu 8.10 and newer**, it WILL crash whenever a popup is displayed. That includes sub-menus and property boxes.
........

Yep, unless you do this:

[http://ubuntuforums.org/showthread.php?t=1133046](http://ubuntuforums.org/showthread.php?t=1133046)

---

### Post by crjackson on 2009-05-03
> **dcstar said:**
> Yep, unless you do this:

[http://ubuntuforums.org/showthread.php?t=1133046](http://ubuntuforums.org/showthread.php?t=1133046)

This does work well so far. I'll be using this until a stable version of the rewrite is out. Thanks for the info.

---

### Post by pboxinator on 2009-05-14
> **AuronGrande said:**
> I am using Intrepid with Gnome and Komposer crashes on me. Even though I know a fair amount of XHTML and CSS I still need a WYSIWYG editor.

I am new to Linux and so I have no idea how to run the program through Terminal so that I can get a report from it.

Can anyone tell me how to do so?
Just type in kompozer or "kompozer"

---

### Post by dcstar on 2009-05-17
> **pboxinator said:**
> Just type in kompozer or "kompozer"

What is the point of answering **an ancient post** that THE POSTER answered him/herself immediately?

---

### Post by dannymichel on 2009-07-31
> **apostate said:**
> Um...no. Kompozer has nothing to do with KDE. I have the same problem. In Intrepid, under Gnome.

true
im on ubuntu (gnome) jaunty x64 and it refuses to stay open.
> danny@danny-desktop:~$ kompozer
Segmentation fault
danny@danny-desktop:~$ 

---

### Post by ken78724 on 2009-08-02
how about a new seamonkey 1.1.17 install? crashes holding up progress are not good. here's a terminal install option: 
tar xjf wbar-1.3.3.tbz2.tar.bz
cd wbar-1.3.3
make
sudo make install

Then enter program wanted [i.e., seamonkey 1.1.17] and password... beyond this not sure where you want to go.

---

### Post by ken78724 on 2009-08-02
Kleeman, don't have seamonkey 1.1.17 install yet. But, what are you saying here.. I mean do you open terminal or do you click on Edit in seamonkey. don't follow your post above.... pls explain.

thanks.
ken:D

---

### Post by tomdkat on 2009-08-09
> **Derevko said:**
> Hi,

I'm preparing a KompoZer package for Debian. I Uploaded my preliminary work in my PPA for Ubuntu users:

Jaunty:

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main
Thanks!  I just installed 0.8a4 and it's working splendidly!  :)

Peace...

---

### Post by orionds on 2009-08-10
> **tomdkat said:**
> Thanks!  I just installed 0.8a4 and it's working splendidly!  :)

Peace...
 
I generate html pages with Hot Potatoes. These are cloze exercises using javascript. I edit these pages with Kompozer to add links or embedded videos. With 0.710 there was no problem but it crashes in Ubuntu.

0.8a4 corrupts some of the javascript. When I click the "check" or "hint" button, I get a popup with a "back" button rather than the usual "ok" button. Also the popup refuses to go away or close.

Anyone know how to fix this? Perhaps even editing the source code? 0.710 does not have this problem.

Thanks for any help or suggestions.

---

### Post by edwardtilbury on 2009-08-10
I tried the version in the Synaptic Package Manager.. it consistently crashed every time I tried to open files or just menus... 

Right now I'm using bluefish and filezilla.. works pretty well so far on x64

---

### Post by edwardtilbury on 2009-08-17
try Geany, just enable the file plugin and it's like dreamweaver somewhat... use it with filezilla linked to your remote directory and you're set.

As for a WYSIWYG, I just have a localhost version of my site so I just save CTRL-S , ALT TAB to mozilla and CTRL R to refresh , so I can diplay a realtime preview pretty quick.

I hope that helps

---

### Post by dcstar on 2009-08-26
> **edwardtilbury said:**
> I tried the version in the Synaptic Package Manager.. it consistently crashed every time I tried to open files or just menus... 


Which is why the workaround is in post #56.

---

### Post by headflux on 2009-08-27
Kompozer is a reasonable WYSIWYG html editor, but I do think it could do with being modernised.  If you want to do anything more than basic HTML pages, it can be a pain to get the right results.

MS Frontpage is better app in my opinion, but as I can't get it to install under WINE, I'm forced to dual boot.

If I was a developer, I'd serious look into trying to improve Kompozer, but unfortunately I'm not. Anyone up for the challenge?

---

### Post by terabyte1 on 2009-08-27
Perhaps its a result of running a 64-bit machine - like Kompozer is not ready for 64-bit yet perhaps?

I am running 64-bit and kompozer does the same thing with me. Do people have the same problem in 32-bit mode?

Cheers!:guitar:

---

### Post by edwardtilbury on 2009-08-27
the new netbeans 6.7 has php support now, I'm going to switch to it from geany... 

I had the same problem, I ditched kompozer for geany, and I use filezilla for ftp.. actually I have filezilla working much like dream weaver, even with excluded files etc.. I like it more than dreamweaver infact.. and no /_notes/ directories everywhere :)

I have a geany style dreamweaver post in here somewhere, you should check that out, so the directories look similar to dreamweaver.

---

### Post by crjackson on 2009-10-20
Is there a karmic ppa?

---

### Post by dcstar on 2009-10-21
> **crjackson said:**
> Is there a karmic ppa?

If you want the 0.8 Alpha version of Kompozer that is in Karmic (which seems to work fine in 64-bit), you will either have to install 9.10 when it is released at the end of the month or wait for a Backport of Kompozer to appear.

The newer 9.10 version has too many dependencies to install on 9.04.

---

### Post by Erlander on 2009-10-21
That's a good reason for upgrading to Karmic!

---

### Post by timgood on 2009-10-21
Kompozer 0.8b1 is available for 64 bit Jaunty on the GetDeb site:

[http://www.getdeb.net/](http://www.getdeb.net/)

Works like a treat. Hope this helps.

---

### Post by Erlander on 2009-10-21
Yes, I'm using it too but one integrated into Karmic will be nice.

---

### Post by crjackson on 2009-10-21
> **dcstar said:**
> If you want the 0.8 Alpha version of Kompozer that is in Karmic (which seems to work fine in 64-bit), you will either have to install 9.10 when it is released at the end of the month or wait for a Backport of Kompozer to appear.

The newer 9.10 version has too many dependencies to install on 9.04.

I found the ppa and upgraded.

---

