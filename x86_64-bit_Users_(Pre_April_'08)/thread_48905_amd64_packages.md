---
title: "amd64 packages"
date: 2005-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tamir on 2005-07-14
hi,

As amd64 user, I know there is not good support of many packages.
So I want to improve it. just tell me which packages you need, I will try to deb it.

all of the debs I will make will be hosted here (thanks to [smoon](http://ubuntuforums.org/member.php?userid=15862) that hosted me):
```

## amd64 users repository
deb http://tamir.nooms.de/ubuntu/ hoary main universe multiverse restricted

## CVS snapshots packages
deb http://tamir.nooms.de/ubuntu/ cvs main universe multiverse restricted

## amd64 packages testers repository
deb http://tamir.nooms.de/ubuntu/ tests main universe multiverse restricted

```
Website (wiki): [http://tamir.nooms.de/wiki/](http://tamir.nooms.de/wiki/)

The following packages already built:
[list]
[*]the whole [ Enlightement 0.17](http://ubuntuforums.org/showthread.php?t=48616) from CVS  (+evidence)
[*]sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
[*]sun-j2sdk1.5 - Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)
[*]blackdown-j2sdk1.4 - Java(TM) 2 SDK, Standard Edition, Blackdown
[*]blackdown-j2re1.4 - Java(TM) 2 RE, Standard Edition, Blackdown
[*]gnomebaker 0.4
[*]freeciv 2.0.3 (thanks to filterban that made it) 
[*]gdesklets 0.35.2
[*]splashy (on tests)
[*]smeg 0.7.5
[*]python-xdg 0.14
[*]gaim 1.4.0 (made by [mo42](http://ubuntuforums.org/member.php?u=22260))
[*]gkrellm
[*]gkrellm-common
[*]gkrellmd
[*]rubygems
[*]inkscape
[*]libgc1c2 
[*]libgc-dev
[*]sensors-applet (made by Corbelius)
[/list]
NX (made by Drain):
[list]
[*]freeNX
[*]libnxcomp0
[*]libnxcomptext0
[*]nxagent
[*]nxdesktop
[*]nxlibs
[*]nxproxy
[*]nxviewer
[/list]
Ruby (1.8.2-9):
[list]
[*]irb1.8
[*]libdbm-ruby1.8
[*]libgdbm-ruby1.8
[*]libopenssl-ruby1.8
[*]libreadline-ruby1.8
[*]libruby1.8-dbg
[*]libruby1.8
[*]libtcltk-ruby1.8
[*]rdoc1.8
[*]ri1.8
[*]ruby1.8-dev
[*]ruby1.8-elisp
[*]ruby1.8-examples
[*]ruby1.8
[/list]
Linux Kernel with ubuntu patches (on tests repository):
[list]
[*]kernel-image-2.6.12-amd64-k8 (2.6.12-4.4)
[*]kernel-headers-2.6.12-amd64-k8 (2.6.12-4.4)
[/list]
Esound Packages:
[list]
[*]esound
[*]esound-clients
[*]esound-common
[*]libesd0
[*]libesd0-dev
[*]libesd-alsa0
[/list]
Firefox:
[list]
[*]firefox 1.0.5 
[*]firefox-dev 1.0.5
[*]firefox-dom-inspector 1.0.5
[*]firefox-gnome-support 1.0.5
[*]mozilla-firefox-dev 1.0.5
[/list]
Firefox deer park (Unstable!!! Backup your data. not ready to use):
[list]
[*]mozilla-firefox (1.0.99+deerpark-alpha2-1) 
[*]mozilla-firefox-dom-inspector (1.0.99+deerpark-alpha2-1) 
[*]mozilla-firefox-gnome-support (1.0.99+deerpark-alpha2-1) 
[/list]
KDE 3.4.1:
[list]
[*]arts (arts, libartsc0, libarts1-dev, libartsc0-dev, libarts1)
[*]kdeaccessibility (kdeaccessibility, kmag, kmousetool, kmouth)
[/list]
Todo List:
[list]
[*]acroread
[*]xmame/xmess 0.97
[*]koffice
[*](currently not updated, I have too packages to build)
[/list]
**Denied Packages:**
[list]
[*]_wine_ - Currently there is not way to build it on amd64
[*]_skype (I will try to)_ - Currently there is not way to build it
[*]_openoffice 2 Beta_ - Currently there is not way to build it on amd64
[/list]
_**Testers:**_
[list]
[*]DancingSun
[*]eolo999
[*]jensyt
[*]jon_gunnar
[/list]
Need testers!

_**How to send me your packages?**_
a. [Make a .deb](http://ubuntuforums.org/showthread.php?t=51003) of the package you want
b. Send to [EMAIL=tamir@nooms.de]my Email[/EMAIL] the files (.dsc, .diff, .orig.tar.gz, .deb)
c. I will contact you on email

**Please send me only [Debian standards](http://www.debian.org/doc/maint-guide/)  packages**  

Please report about bugs, problems, corrections on my Email:
**tamir@nooms.de** 

thanks.

---

### Post by fistfullofroses on 2005-07-14
[QUOTE=Tamir]hi,

As amd64 user, I know there is not good support of many packages.
So I want to improve it. just tell me which packages you need, I will try to deb it.

all of the debs I will make will be hosted here (thanks to smoon that hosted me):

deb tamir.nooms.de/ubuntu/ hoary main

thanks.[/QUOTE]
 a Java Runtime Environment would be nice.
then I wouldn't have to do all the Chroot shit all the time.
but other than that, I have all I need... but most people do not.
THANK YOU FOR WHAT YOU ARE DOING!!!!!!!

---

### Post by DancingSun on 2005-07-14
First of all, THANK YOU VERY MUCH, Tamir!!!

As a newbie to Linux, I do not feel comfortable installing rpms and bin packages myself.  Plus, I'm lazy and really don't like to go though the troubles I have in Windows when uninstalling software (in Windows, sometimes the uninstaller doesn't uninstall everything and I have to go hunt for them).

As for requests, I would like:
[list=1]
[*]JDK 1.5, JRE 1.5
[*]Open Office 2 beta
[*]libesd-alsa0 (so I can try the "configure your sound properly" guides)
[/list]

---

### Post by Tamir on 2005-07-14
[QUOTE=DancingSun]First of all, THANK YOU VERY MUCH, Tamir!!!

As a newbie to Linux, I do not feel comfortable installing rpms and bin packages myself.  Plus, I'm lazy and really don't like to go though the troubles I have in Windows when uninstalling software (in Windows, sometimes the uninstaller doesn't uninstall everything and I have to go hunt for them).

As for requests, I would like:
[list=1]
[*]JDK 1.5, JRE 1.5
[*]Open Office 2 beta
[*]libesd-alsa0 (so I can try the "configure your sound properly" guides)
[/list][/QUOTE]
 :), OK, I am trying to build for ya JDK 1.5, JRE 1.5 debs.

---

### Post by DancingSun on 2005-07-14
Hey Tamir,

Have you thought about contacting jdong of the backports project?  They might be willing to give you the resources (repository hosting) and perhaps it would be better to merge your efforts together.  I just did a search of "amd64 backport" in the forum, and it seems like the reason why there's no backports of packages for AMD64 is because they do not have AMD64 machines at their disposal.

---

### Post by Tamir on 2005-07-14
I made it!
[COLOR=DarkOliveGreen]I am now uploading the packages, so you will see it only tommorow.[/COLOR]

I made the following packages:

:arrow: sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
:arrow: sun-j2sdk1.5 - Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)
:arrow: blackdown-j2sdk1.4 - Java(TM) 2 SDK, Standard Edition, Blackdown
:arrow: blackdown-j2re1.4 - Java(TM) 2 RE, Standard Edition, Blackdown

sun's amd64 version of j2sdk and j2jre [COLOR=DarkGreen]currently[/COLOR] not supports the web plugin :\.
But! You can install blackdown version, that supports!

after installation of blackdown, make symbolic link to the plugin; example with firefox:
```
ln -s /usr/lib/j2re1.4-blackdown/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib64/mozilla-firefox/plugins/
``` 

more information:
[ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/rc1/INSTALL-j2sdk](ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/rc1/INSTALL-j2sdk)


Enjoy :)

---

### Post by smoon on 2005-07-14
> **Tamir]I made it!
[COLOR=DarkOliveGreen]I am now uploading the packages, so you will see it only tommorow.[/COLOR]

I made the following packages:

:arrow: sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
:arrow: sun-j2sdk1.5 - Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)
:arrow: blackdown-j2sdk1.4 - Java(TM) 2 SDK, Standard Edition, Blackdown
:arrow: blackdown-j2re1.4 - Java(TM) 2 RE, Standard Edition, Blackdown

sun's amd64 version of j2sdk and j2jre [COLOR=DarkGreen]currently[/COLOR] not supports the web plugin :\.
But! You can install blackdown version, that supports!

after installation of blackdown, make symbolic link to the plugin said:**
> ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/rc1/INSTALL-j2sdk[/url]


Enjoy :)

Nice work :-D

---

### Post by DancingSun on 2005-07-14
Sweeeet!  But....why tomorrow?  Me wants my precioussss!!!! :twisted:

---

### Post by filterban on 2005-07-14
Hey -

I'd also be willing to help out in this effort.   I just built an amd64 box with only ubuntu installed.  Want to collaborate?

(JRE 1.5 and WINE ports seem to be popular requests, btw.)

---

### Post by filterban on 2005-07-14
Also, couldn't you have the firefox plugin step of the Blackdown installation added to the "postinst" section of the deb file?

---

### Post by DancingSun on 2005-07-14
Yes! Collaborate my friends!  We need to improve the usability of Ubuntu AMD64!

I am willing to test things out....as long as you give me instructions on how to uninstall/troubleshoot stuff when things go bad. :D

---

### Post by Snodgrass on 2005-07-14
[QUOTE=Tamir]hi,

As amd64 user, I know there is not good support of many packages.
So I want to improve it. just tell me which packages you need, I will try to deb it.

all of the debs I will make will be hosted here (thanks to smoon that hosted me):

deb tamir.nooms.de/ubuntu/ hoary main

thanks.[/QUOTE]
 Does LaTeX work in AMD64?

---

### Post by DancingSun on 2005-07-14
I'm receiving the following error when starting Synaptic after adding the repository into sources.list:

```
W: Couldn't stat source package list http://tamir.nooms.de hoary/main
Packages (/var/lib/apt/lists/tamir.nooms/
tamir.nooms.de_ubuntu_dists_hoary_main_binary-amd64_Packages) - 
Stat (2 No such file or directory)
```

---

### Post by filterban on 2005-07-14
Tamir -

I think you may have spelled the "release" file name incorrectly in your repository, as the packages don't show up in Synaptic even after i've added it.

Any thoughts?

---

### Post by Tamir on 2005-07-15
```

Also, couldn't you have the firefox plugin step of the Blackdown installation added to the "postinst" section of the deb file?
``` 

No I could not, because these debs based free binary's that they give :\.
I will try to find a source.

[QUOTE=DancingSun]I'm receiving the following error when starting Synaptic after adding the repository into sources.list:

```
W: Couldn't stat source package list http://tamir.nooms.de hoary/main
Packages (/var/lib/apt/lists/tamir.nooms/
tamir.nooms.de_ubuntu_dists_hoary_main_binary-amd64_Packages) - 
Stat (2 No such file or directory)
```[/QOUTE]

heha, ok I will fix it today, I uploaded the files, I should only update the Packages file.

---

### Post by Tamir on 2005-07-15
OK, the new packages are ready:
```
apt-get update
``` 

Enjoy!

---

### Post by DancingSun on 2005-07-15
SWEET!  It works!  I am now running Netbeans 4.1 on j2sdk-1.5!!

Update:
I'm running Azureus as well on....j2sdk-1.5!?  Hmm....I guess I don't need to install the JRE then?

---

### Post by filterban on 2005-07-15
Yep.  The blackdown install worked great for me, too.

Nice work, Tamir.  Thank you so much.

Any other requests?

---

### Post by Tamir on 2005-07-15
What do you want first?

1. libesd-alsa0
2. wine
3. openoffice 2 beta

?

---

### Post by DancingSun on 2005-07-15
[QUOTE=Tamir]What do you want first?

1. libesd-alsa0
2. wine
3. openoffice 2 beta

?[/QUOTE]
I would vote for open office 2 beta...but then again, it's only a beta....even though I really want to use it on Ubuntu...

If not, I would like to see libesd-alsa0 ported, since that way I *should *be able to get rid of the need to execute "killall esd" when playing games.

As for wine...well currently I dual boot, so personally that's not a priority for me.

---

### Post by Drain on 2005-07-15
How about creating an AMD64 version of NX server? I think there is a version for x86 on Ubuntu and on Debian, but haven't see it for AMD64. 

See also: [http://www.nomachine.org/](http://www.nomachine.org/)

---

### Post by Tamir on 2005-07-15
New packages are available, see the main post.  ;-)

---

### Post by DancingSun on 2005-07-16
I'm now using ALSA as the default audio sink!  Thanks Tamir!

---

### Post by duffman25 on 2005-07-16
I would like to request the new gnomebaker 0.4 build which has just been released. It has many new exciting features :)

---

### Post by Jet2k5 on 2005-07-16
*REQUEST*

A lot of the board members are having trouble getting skype running.  So I'm requesting if you can make a package for it :) .  However I don't know if after the package is made how it will work .. man I wish I had my 64-bit processor right now.

---

### Post by Jet2k5 on 2005-07-16
*REQUEST*

How about Teamspeak?  Don't know how much of a problem that might be on Linux, but it's a great thing to have in a repo for us gamers.

---

### Post by BLueSS on 2005-07-16
I tried to add the repository into synaptic,
Settings -> repositories -> add -> custom-> pasting the complete link into the box...

but it gives an error saying it's unable to connect to the repository index.

What should I do to install it correctly?

---

### Post by smoon on 2005-07-16
[QUOTE=BLueSS]I tried to add the repository into synaptic,
Settings -> repositories -> add -> custom-> pasting the complete link into the box...

but it gives an error saying it's unable to connect to the repository index.

What should I do to install it correctly?[/QUOTE]

Have you added this complete line:
```
deb http://tamir.nooms.de/ubuntu/ hoary main
```

---

### Post by smoon on 2005-07-16
I've just read the last posts of this thread and I've a little plea: Please make sure that you don't violate any licensing stuff with packages like Skype or Teamspeak. I mean there's to be a reason I can't find stuff like that in no repository for no architecture. IANAL, but please double check what you're packaging, if it is allowed to do so, are there any limitations?, etc.
Maybe it's not even allowed to package the Java stuff from SUN? Check that, please.

The reason I'm writing this is, that I'm the one who hosts the packages and if you violate any law or something I'm most likely the one who has to pay for that.

Maybe someone can shed some light in this whole situation?

---

### Post by BLueSS on 2005-07-16
deb tamir.nooms.de/ubuntu/ hoary main  <--- This is what I put in, since that's what was on the main post.

It seems like it needed the http://
Thanks

---

### Post by DancingSun on 2005-07-16
[QUOTE=smoon]I've just read the last posts of this thread and I've a little plea: Please make sure that you don't violate any licensing stuff with packages like Skype or Teamspeak. I mean there's to be a reason I can't find stuff like that in no repository for no architecture. IANAL, but please double check what you're packaging, if it is allowed to do so, are there any limitations?, etc.
Maybe it's not even allowed to package the Java stuff from SUN? Check that, please.

The reason I'm writing this is, that I'm the one who hosts the packages and if you violate any law or something I'm most likely the one who has to pay for that.

Maybe someone can shed some light in this whole situation?[/QUOTE]

Well, Sun's Java 1.5 is on the 32-bit backports or official repository (deduced from the [Unofficial Ubuntu Guide for 32-bit Ubuntu](http://www.ubuntuguide.org) ), which means at least Hoary or Breezy has it in its repository, so I'd assume the Master Of the Universe guys for Breezy already checked that.

I think generally, making packages for AMD64 from Breezy's 32-bit repository *should* be okay.

---

### Post by Terracotta on 2005-07-17
*request*
has anyone thought of koffice 1.4??
thanks
edit: or kde 3.4.1 as a whole ?

---

### Post by Kuolio on 2005-07-17
Request:
Multimedia (video/audio) codecs! I've installed some of them from debian-marillats, but we need more :)

Wine would also be nice...

ATM im running all my multimedia, wine, web-browsing and even azureus from 32bit chroot.. bah! Thanks to that java 1.5, I can now move using azureus as 64bit, I think. Or atleast, i can come to this thread and beg for a 64bit azureus deb if there isn't one already. :)

Thank you, you rock  \\:D/

---

### Post by Tamir on 2005-07-17
[QUOTE=smoon]I've just read the last posts of this thread and I've a little plea: Please make sure that you don't violate any licensing stuff with packages like Skype or Teamspeak. I mean there's to be a reason I can't find stuff like that in no repository for no architecture. IANAL, but please double check what you're packaging, if it is allowed to do so, are there any limitations?, etc.
Maybe it's not even allowed to package the Java stuff from SUN? Check that, please.

The reason I'm writing this is, that I'm the one who hosts the packages and if you violate any law or something I'm most likely the one who has to pay for that.

Maybe someone can shed some light in this whole situation?[/QUOTE]

About java, that's Ok:
[http://java.com/en/download/license.jsp](http://java.com/en/download/license.jsp)

---

### Post by Tamir on 2005-07-17
[QUOTE=duffman25]I would like to request the new gnomebaker 0.4 build which has just been released. It has many new exciting features :)[/QUOTE]

done.  :smile:

---

### Post by fistfullofroses on 2005-07-17
[QUOTE=DancingSun]SWEET!  It works!  I am now running Netbeans 4.1 on j2sdk-1.5!!

Update:
I'm running Azureus as well on....j2sdk-1.5!?  Hmm....I guess I don't need to install the JRE then?[/QUOTE]
 How did you get Netbeans to work???

---

### Post by duffman25 on 2005-07-17
[QUOTE=Tamir]done.  :smile:[/QUOTE]

I've installed gnomebaker from your repo and I can't execute it. there's no gnomebaker binary in my path:

```

$ find / -name gnomebaker 2>/dev/null
/home/duff/.gnome2/accels/gnomebaker
/home/duff/.gnome2/gnomebaker
/usr/share/doc/gnomebaker
$

```

---

### Post by Tamir on 2005-07-17
[QUOTE=duffman25]I've installed gnomebaker from your repo and I can't execute it. there's no gnomebaker binary in my path:

```

$ find / -name gnomebaker 2>/dev/null
/home/duff/.gnome2/accels/gnomebaker
/home/duff/.gnome2/gnomebaker
/usr/share/doc/gnomebaker
$

```[/QUOTE]
 Mmmm, It is working for me, I just run it with : gnomebaker.
but I will check what is the problem.

---

### Post by Tamir on 2005-07-17
Try now, new file. but I don't see the problem.

apt-get --reinstall install gnomebaker

---

### Post by musther on 2005-07-17
Yeah, I'd really like a skype package, unless there's some reason you havn't made one yet.

Cheers!

---

### Post by DancingSun on 2005-07-17
Request: [Tomboy](http://www.beatniksoftware.com/tomboy/#about)

---

### Post by musther on 2005-07-17
Is there any way, apart from 32bit chroot, to install flash?  I mean, is it possible to create some kind of 64bit flash package?

---

### Post by DancingSun on 2005-07-17
[QUOTE=musther]Is there any way, apart from 32bit chroot, to install flash?  I mean, is it possible to create some kind of 64bit flash package?[/QUOTE]
Ask Macromedia to do that.  Remember, Flash is a proprietary commercial product!

---

### Post by DancingSun on 2005-07-17
[QUOTE=fistfullofroses]How did you get Netbeans to work???[/QUOTE]
I just downloaded NetBeans, and installed it via the installer...there are [instructions](http://www.netbeans.org/community/releases/41/install.html)  on the NetBeans download page on how to install.

---

### Post by DancingSun on 2005-07-17
Another Request:  rar

This package is needed to get rar support working on file-roller (the Ubuntu Archive Manager).

---

### Post by Ramon on 2005-07-17
If you please Opera  :-P

---

### Post by duffman25 on 2005-07-17
[QUOTE=Tamir]Try now, new file. but I don't see the problem.

apt-get --reinstall install gnomebaker[/QUOTE]

I'm having the same problem. I had installed previously hoarys version. Now after installing your package gnoomebaker has disappeared. No gnome-menu item, no gnomebaker in path... strange- Anyone with similar problem?

---

### Post by duffman25 on 2005-07-17
[QUOTE=Tamir]Try now, new file. but I don't see the problem.

apt-get --reinstall install gnomebaker[/QUOTE]

I'm having the same problem. I had installed previously hoarys version. Now after installing your package gnoomebaker has disappeared. No gnome-menu item, no gnomebaker in path... strange- Anyone with similar problem?

---

### Post by smoon on 2005-07-17
[QUOTE=duffman25]I'm having the same problem. I had installed previously hoarys version. Now after installing your package gnoomebaker has disappeared. No gnome-menu item, no gnomebaker in path... strange- Anyone with similar problem?[/QUOTE]

Even though I'm not an AMD64 user I just checked the package and it is only 6 kB in size and only includes the stuff which goes under /usr/share/doc/gnomebaker. So Tamir will have to recreate the packge to make it work for you ;-)

---

### Post by duffman25 on 2005-07-17
[QUOTE=smoon]Even though I'm not an AMD64 user I just checked the package and it is only 6 kB in size and only includes the stuff which goes under /usr/share/doc/gnomebaker. So Tamir will have to recreate the packge to make it work for you ;-)[/QUOTE]

Thanxs for the info.
Edit: sorry for my double post before. Feel free to delete it.

---

### Post by jon_gunnar on 2005-07-17
[QUOTE=DancingSun]Another Request:  rar

This package is needed to get rar support working on file-roller (the Ubuntu Archive Manager).[/QUOTE]

rar is to be found in multiverse. Or is there any problems with that one?

---

### Post by musther on 2005-07-17
Just another idea, how about Helix/Real Player there are debs available for Helix.

---

### Post by DancingSun on 2005-07-18
[QUOTE=jon_gunnar]rar is to be found in multiverse. Or is there any problems with that one?[/QUOTE]
For AMD64? I can't find it in Synaptic.

I have these in my sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by ToastedToad on 2005-07-18
[QUOTE=DancingSun]For AMD64? I can't find it in Synaptic.

I have these in my sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse[/QUOTE]

```
scott@black:~$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
``` 

I concur.

---

### Post by jon_gunnar on 2005-07-18
[QUOTE=DancingSun]For AMD64? I can't find it in Synaptic.

I have these in my sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse[/QUOTE]
I'm sorry, my misstake. It's the source that is available.

---

### Post by braveerudite on 2005-07-18
[QUOTE=fistfullofroses]a Java Runtime Environment would be nice.
then I wouldn't have to do all the Chroot shit all the time.
but other than that, I have all I need... but most people do not.
THANK YOU FOR WHAT YOU ARE DOING!!!!!!![/QUOTE]


You have Flash pluging for Mozila Firefox???

---

### Post by Tamir on 2005-07-18
[QUOTE=smoon]Even though I'm not an AMD64 user I just checked the package and it is only 6 kB in size and only includes the stuff which goes under /usr/share/doc/gnomebaker. So Tamir will have to recreate the packge to make it work for you ;-)[/QUOTE]

surely fixed :)

---

### Post by arunsub on 2005-07-18
The things that are stopping me from moving to Ubuntu64 are
1. W32codecs
2. Flash plugin for Firefox
3. Skype

There may be some more, but I don't remember those now. Any chance of porting the above to 64 bit?

---

### Post by DancingSun on 2005-07-18
[QUOTE=arunsub]The things that are stopping me from moving to Ubuntu64 are
1. W32codecs
2. Flash plugin for Firefox
3. Skype

There may be some more, but I don't remember those now. Any chance of porting the above to 64 bit?[/QUOTE]

Guys, porting proprietary stuff without permission of the software's owner is illegal, not to mention we need the source code to recompile the binaries to be 64-bit compatible.

If the 64-bit binaries are already provided by the vendor, then porting it is a matter of making sure the licenses allow the binaries to be freely distributable.

---

### Post by X3N on 2005-07-18
I think this should become a 3rd party ubuntu project, there seems to be enough interest and enough know how to get some great results, but i think needs to be something like a wiki to keep track of new packages that have been made, bugs, things still to do and maybe a dedicated dump/repisitory for the packages that have been made

---

### Post by filterban on 2005-07-19
[QUOTE=X3N]I think this should become a 3rd party ubuntu project, there seems to be enough interest and enough know how to get some great results, but i think needs to be something like a wiki to keep track of new packages that have been made, bugs, things still to do and maybe a dedicated dump/repisitory for the packages that have been made[/QUOTE]

I agree.  This sounds like a good idea.

I think Tamir already has the repository though; perhaps a wiki/forum/bugtracker would be a good addition.

---

### Post by X3N on 2005-07-19
[https://wiki.ubuntu.com/x86_64packages](https://wiki.ubuntu.com/x86_64packages)
Hope you don't mind i just copied your first post tamir, needed something to get it going :)

---

### Post by Burgundavia on 2005-07-19
It would be great if you could work with the Masters of the Universe, then a much larger group of people can enjoy your work. You can also avoid duplication of effort (as OpenOffice2 now works on amd64). They can be reached at #ubuntu-motu on Freenode.

Corey

---

### Post by viniosity on 2005-07-19
[QUOTE=Drain]How about creating an AMD64 version of NX server? I think there is a version for x86 on Ubuntu and on Debian, but haven't see it for AMD64. 

See also: [http://www.nomachine.org/](http://www.nomachine.org/)[/QUOTE]

Ditto this request.. would love to see nxserver make it to AMD64

---

### Post by Pcghost on 2005-07-19
[QUOTE=Burgundavia]It would be great if you could work with the Masters of the Universe, then a much larger group of people can enjoy your work. You can also avoid duplication of effort (as OpenOffice2 now works on amd64). They can be reached at #ubuntu-motu on Freenode.

Corey[/QUOTE]

Sorry for my ignorance here, but google came up with nothing in English for this.  Where can I find this package (ooo2.0 amd_64 for ubuntu) and how fast can I download it?  \\:D/ 

  ooo2.0 is the only thing I pine for each day booting this fine system.  If it even works half the time, you have made my day.

---

### Post by Tamir on 2005-07-20
[QUOTE=X3N][https://wiki.ubuntu.com/x86_64packages](https://wiki.ubuntu.com/x86_64packages)
Hope you don't mind i just copied your first post tamir, needed something to get it going :)[/QUOTE]

It is not 3rd party project, please change it.

---

### Post by filterban on 2005-07-20
[QUOTE=Tamir]It is not 3rd party project, please change it.[/QUOTE]

3rd party = not official Ubuntu, so this is a 3rd party project, unless I'm missing something.

---

### Post by Tamir on 2005-07-20
[QUOTE=filterban]3rd party = not official Ubuntu, so this is a 3rd party project, unless I'm missing something.[/QUOTE]
 oh! sorry, i thought that's a company name :).

---

### Post by Tamir on 2005-07-20
[QUOTE=Tamir]oh! sorry, i thought that's a company name :).[/QUOTE]
 Guys, I made mozilla-firefox 1.0.5, and mozilla-firefox 1.1 alpha 2!
I am uploading.

---

### Post by medication on 2005-07-20
First off, thanks Tamir!  Very happy to see someone adding support to the AMD64 platform.

I'd also like to offer my services as a tester.  I'm somewhat of a noob still, but I'd be glad to help test any package for you and let you know the result.

As for package requests, I'll go along with someone who posted earlier and requested the win32codecs.  Other than that I think I'm alright (thanks to the java packages).

Cheers!

---

### Post by medication on 2005-07-20
[QUOTE=Tamir]Guys, I made mozilla-firefox 1.0.5, and mozilla-firefox 1.1 alpha 2!
I am uploading.[/QUOTE]
 Can't wait to try the new firefox package!  Unfortunately, I'm at work and my box at home is offline right now... 

Keep up the great work!

---

### Post by Tamir on 2005-07-20
[QUOTE=medication]Can't wait to try the new firefox package!  Unfortunately, I'm at work and my box at home is offline right now... 

Keep up the great work![/QUOTE]
 now available :)

---

### Post by eolo999 on 2005-07-20
hi Tamir, i would like to help building packages for amd64, can you tell what should be done?

---

### Post by DancingSun on 2005-07-20
Hey guys, I found this in the "Programming Talk" forum, it is a program that can make .deb files from source installs, it sounds like it can be handy:
[http://asic-linux.com.mx/~izto/checkinstall/index.php](http://asic-linux.com.mx/~izto/checkinstall/index.php)

---

### Post by emrys on 2005-07-20
Great job Tamir. Nice.

What about Thunderbird 1.1? (well, alpha)

(Openoffice 2 is a must for me too... :) )

Thanks a lot.

---

### Post by Pcghost on 2005-07-20
Tamir, just a note. My upgrade to firefox 1.0.5 didn't go so well.  It seems it choked on the the extentions directory (I have quite a few installed). Here is the error:

Unpacking replacement mozilla-firefox ...
dpkg: warning - unable to delete old file `/etc/mozilla-firefox/profile/extensions': Directory not empty
Errors were encountered while processing:

Firefox wont start after the upgrade, but no big deal, I can restore my old one easy enough.  Not sure where the bug is, as I am too busy studying for my LPIC101 exam, but when I get back I will totally help out in packaging. Thanks for your hard work thus far. 
 :smile:

---

### Post by twigsby on 2005-07-20
How about splashy? I know it's probably not something everyone uses.

I tried compiling the src but couldn't get passed dependency problems (glib2.0) and  I couldn't figure out pkg-conf to point to libglib2.0 if that's even the same thing. :S

---

### Post by medication on 2005-07-20
upgraded to ff 1.05 and it went fantastically!

thanks again Tamir

---

### Post by nrayever on 2005-07-20
ooh man, tamir i would really like to kiss you!  =D>  =D>  it's not because i'm gay, but with those firefox packages you solved my problems!! 3 weeks trying to install f$%&#! firefox 1.0.5 from tar.gz and i got libgtkx11 errors.

but now is all solved. let me make a little quote here: "uups!! new firefox released!!" i'm not complaining, i'm just making a quote, hehehe!!  :D  :D  :D 

if it's any way i could help, let me know. i would like to learn how to make a nice  deb package and etc.... !!!

nrayever

---

### Post by filterban on 2005-07-21
[QUOTE=DancingSun]Hey guys, I found this in the "Programming Talk" forum, it is a program that can make .deb files from source installs, it sounds like it can be handy:
[http://asic-linux.com.mx/~izto/checkinstall/index.php](http://asic-linux.com.mx/~izto/checkinstall/index.php)[/QUOTE]

NICE!

I am going to make a package of FreeCiv 2.0.3, just because I can. :)

That program rocks.

DancingSun++

---

### Post by filterban on 2005-07-21
[QUOTE=filterban]NICE!

I am going to make a package of FreeCiv 2.0.3, just because I can. :)

That program rocks.

DancingSun++[/QUOTE]

Not that you guys will use it, but I've created a .deb of freeciv version 2.0.3 for amd64 using the "checkinstall" program.

Tamir:

To get the .deb and post it on your repository:

[http://toric.sine.com/~filter/freeciv_2.0.3-1_amd64.deb](http://toric.sine.com/~filter/freeciv_2.0.3-1_amd64.deb)

Any and all testers would be appreciated.  If it works, we've got a very quick and easy way to make .debs!

---

### Post by Tamir on 2005-07-21
[QUOTE=filterban]Not that you guys will use it, but I've created a .deb of freeciv version 2.0.3 for amd64 using the "checkinstall" program.

Tamir:

To get the .deb and post it on your repository:

[http://toric.sine.com/~filter/freeciv_2.0.3-1_amd64.deb](http://toric.sine.com/~filter/freeciv_2.0.3-1_amd64.deb)

Any and all testers would be appreciated.  If it works, we've got a very quick and easy way to make .debs![/QUOTE]
 no problem, but I need your .diff, .orig.tar.gz and the .dsc, I want to check if it's on my standarts. do you have these files?

Note: if you guys want to make debs like the professionals, wait.
I will write a guide when I'll have to time.

---

### Post by filterban on 2005-07-21
[QUOTE=Tamir]no problem, but I need your .diff, .orig.tar.gz and the .dsc, I want to check if it's on my standarts. do you have these files?

Note: if you guys want to make debs like the professionals, wait.
I will write a guide when I'll have to time.[/QUOTE]

I'm not sure what you mean by "on my standarts".   Did you look at the .deb?   What's unprofessional about it?   (Any criticism is appreciated!)

I don't have the diff or the dsc.  The original source code is available here:

[ftp://ftp.freeciv.org/pub/freeciv/stable/freeciv-2.0.3.tar.gz](ftp://ftp.freeciv.org/pub/freeciv/stable/freeciv-2.0.3.tar.gz)

Did you look at the "checkinstall" program, pointed out by DancingSun?

---

### Post by pailhead on 2005-07-21
[QUOTE=twigsby]How about splashy? I know it's probably not something everyone uses.

I tried compiling the src but couldn't get passed dependency problems (glib2.0) and  I couldn't figure out pkg-conf to point to libglib2.0 if that's even the same thing. :S[/QUOTE]

I'd like to see splashy added as well.

---

### Post by Tamir on 2005-07-21
[QUOTE=pailhead]I'd like to see splashy added as well.[/QUOTE]
 I will deb splasy, I am making the big things right now.
fiterban: [that's](http://www.debian.org/doc/maint-guide/) how the "professioals" making debs (I am joking about the professional), it just means that you configuring you deb. but you deb is ok,
I will upload tommorow or today, we'll see.

---

### Post by pailhead on 2005-07-21
[QUOTE=Tamir]I will deb splasy, I am making the big things right now.
fiterban: [that's](http://www.debian.org/doc/maint-guide/) how the "professioals" making debs (I am joking about the professional), it just means that you configuring you deb. but you deb is ok,
I will upload tommorow or today, we'll see.[/QUOTE]
 Awesome.. thanks for splashy and I'll keep an eye out for it. 

I'll also be looking forward to your how-to on deb creation.  If I can help I'd like to try...

Thanks again..

---

### Post by Tamir on 2005-07-21
[QUOTE=pailhead]Awesome.. thanks for splashy and I'll keep an eye out for it. 

I'll also be looking forward to your how-to on deb creation.  If I can help I'd like to try...

Thanks again..[/QUOTE]
 :) Thanks. I need testers! please mail me to [email]tamir@nooms.de[/email] if you are interested.

---

### Post by DancingSun on 2005-07-21
The Firefox 1.1 beta package didn't work for me.  Um...interesting enough, I installed it by "accident".

I woke up this morning and found the "system update" indicator on my gnome panel, so I just did the upgrade there.  It seems that the official Firefox package is also being updated (as indicated in the Desktop forum)...however, the version that I get in the updater was the beta version (I don't think the official update would be an beta version, so I'm guessing this is Tamir's package).  Well, I did the update anyway, and now I cannot open Firefox.  If launched from the terminal it will say "Segmentation fault".

I have now reverted back to 1.0.2 using Synaptic ... well it launches, but I lost all my extensions :(.  Is this normal (losing extensions and themes)?

Update: Installing the 1.0.5 packages work just fine!

---

### Post by pailhead on 2005-07-21
[QUOTE=Tamir]:) Thanks. I need testers! please mail me to [email]tamir@nooms.de[/email] if you are interested.[/QUOTE]
 Whatever testing you need I"ll be sending you an email...

---

### Post by Tamir on 2005-07-21
Delete this messege, I saw your edit DancingSun.

---

### Post by DancingSun on 2005-07-21
Now, if I want to keep my firefox extensions and settings after an update, do I just make a backup of my .mozilla directory under home and then replace the the new .mozilla directory with that backup?

Edit: More questions...

Is it safe to do the above?

What would you guys recommend?  Just reconfigure the settings and re-install all the extensions and themes (this seems safer as you won't have incompatible extensions/themes installed)?

---

### Post by Tamir on 2005-07-21
[QUOTE=DancingSun] do I just make a backup of my .mozilla directory under home and then replace the the new .mozilla directory with that backup?[/QUOTE]

Yes, I know that deer park is removing the extensions, I think Firefox 1.0.5 doesn't.

---

### Post by filterban on 2005-07-21
[QUOTE=DancingSun]The Firefox 1.1 beta package didn't work for me.  Um...interesting enough, I installed it by "accident".

I woke up this morning and found the "system update" indicator on my gnome panel, so I just did the upgrade there.  It seems that the official Firefox package is also being updated (as indicated in the Desktop forum)...however, the version that I get in the updater was the beta version (I don't think the official update would be an beta version, so I'm guessing this is Tamir's package).  Well, I did the update anyway, and now I cannot open Firefox.  If launched from the terminal it will say "Segmentation fault".

I have now reverted back to 1.0.2 using Synaptic ... well it launches, but I lost all my extensions :(.  Is this normal (losing extensions and themes)?

Update: Installing the 1.0.5 packages work just fine![/QUOTE]

I had this exact same issue.  The "segmentation fault" and the need to revert.

---

### Post by filterban on 2005-07-21
[QUOTE=Tamir]I will deb splasy, I am making the big things right now.
fiterban: [that's](http://www.debian.org/doc/maint-guide/) how the "professioals" making debs (I am joking about the professional), it just means that you configuring you deb. but you deb is ok,
I will upload tommorow or today, we'll see.[/QUOTE]

Haha.  Ok. :)  I looked at that guide awhile ago and about shot myself.  From what I can see we aren't doing all of those things for this project.

So, I look forward to your guide, Tamir.   Until then, I'll just use "checkinstall". :P

---

### Post by DancingSun on 2005-07-21
[QUOTE=Tamir]Yes, I know that deer park is removing the extensions, I think Firefox 1.0.5 doesn't.[/QUOTE]

Oh ok, that's nice to know :).

---

### Post by filterban on 2005-07-22
Tamir,

What's the list of outstanding packages, so some of us can get started with helping make them? :)   The first post doesn't seem to be 100% up to date.

---

### Post by Luggy on 2005-07-22
[QUOTE=Tamir]
**Denied Packages:**
[list]
[*]_skype (I will try to)_ - Currently there is not way to build it
[/list]
[/QUOTE]

Huh?

You can compile it in 64 with gentoo, why can't you do it with Skype?
[link](http://packages.gentoo.org/search/?sstring=skype )

---

### Post by smoon on 2005-07-22
[QUOTE=Luggy]Huh?

You can compile it in 64 with gentoo, why can't you do it with Skype?
[link](http://packages.gentoo.org/search/?sstring=skype )[/QUOTE]

You can't compile Skype in Gentoo. The only thing the ebuild does when you emerge skype on AMD64 is, downloading and installing the Skype binary (32 bit) and some 32 bit libraries, Skype needs to run. At least that is what it looks like for me when looking at the ebuild.

---

### Post by Tamir on 2005-07-22
In a few days I will make firefox-1.0.6, this is stable. firefox-1.0.5 have too much bugs.

---

### Post by nrayever on 2005-07-22
nice tamir!!! :grin:  :grin:

---

### Post by fromans4 on 2005-07-22
This is way cool.  :grin: 

I would like to make a request for MythTV v0.18.1. The current package available through Ubuntu's repositories is 0.17, which is pretty old.

Thanks for all your hard work,

Brent

---

### Post by Drain on 2005-07-23
[QUOTE=fromans4]
I would like to make a request for MythTV v0.18.1. The current package available through Ubuntu's repositories is 0.17, which is pretty old.
[/QUOTE]

This is a known problem - [https://launchpad.ubuntu.com/malone/bugs/741](https://launchpad.ubuntu.com/malone/bugs/741) 
Mythtv .18-1 won't build on any version of Hoary, let alone AMD64. 

You can find the build logs for mythtv here:
[http://people.ubuntu.com/~lamont/buildLogs/m/mythtv/](http://people.ubuntu.com/~lamont/buildLogs/m/mythtv/)

If I understand correctly, it's because of some other dependancy that .18 requires, that Hoary uses an older version of. It will all be resolved in Breezy in October. (And yay for Breezy, as the 2.6.12 kernel and later will natively support for my HD-3000 capture card).

---

### Post by jensyt on 2005-07-23
I've tried taking a whack at this whole thing now, too.

I packaged the latest gDesklets (0.35.2) as available on their website. I sent the files to Tamir in an email, so maybe he'll put it up soon.

In case anyone has problems with the deb... I had an usual problem with my first try that didn't allow me to install because it wanted to overwrite a file... I forced that first try and it worked. Later I changed some things in the deb and it hasn't asked me to overwrite or anything since then, but it might be due to the original overwriting I did.

Either way, if anyone wants to test this for me (it seems safe to overwrite the file and gDesklets works as soon as you do. I'm running GoodWeather desklet right now, actually):

[http://home.programmer-art.org/jens/gdesklets_0.35.2-1_amd64.deb](http://home.programmer-art.org/jens/gdesklets_0.35.2-1_amd64.deb)

---

### Post by Tamir on 2005-07-23
Great, I saw your debian dir, perfect. I sent to my tester, they will check, and tommorow I will upload if every thing is ok.

---

### Post by jon_gunnar on 2005-07-23
[QUOTE=jensyt]I've tried taking a whack at this whole thing now, too.

I packaged the latest gDesklets (0.35.2) as available on their website. I sent the files to Tamir in an email, so maybe he'll put it up soon.

In case anyone has problems with the deb... I had an usual problem with my first try that didn't allow me to install because it wanted to overwrite a file... I forced that first try and it worked. Later I changed some things in the deb and it hasn't asked me to overwrite or anything since then, but it might be due to the original overwriting I did.

Either way, if anyone wants to test this for me (it seems safe to overwrite the file and gDesklets works as soon as you do. I'm running GoodWeather desklet right now, actually):

[http://home.programmer-art.org/jens/gdesklets_0.35.2-1_amd64.deb](http://home.programmer-art.org/jens/gdesklets_0.35.2-1_amd64.deb)[/QUOTE]
The file that it supposed to be overwritten is  `/usr/share/applications/mimeinfo.cache'
I have done a rebuild of gdesklets_0.35.1-1 from breezy and there is a difference there.
But maybe this file the rebuilt somehow. I'm gonna back it up just to be safe cause it contains a lot of info.
---Update--
As an update. This package broke every association that existed on my system. even restoring the original mimeinfo.cache does not help. But thats the price for testing isn't it?  :)

---

### Post by Tamir on 2005-07-23
Yeah that's a good tip that I forget, always try to build from breezy the source, if it is available and stable. don't remake new debian dir if it's included in breezy.

---

### Post by jensyt on 2005-07-24
[QUOTE=jon_gunnar]The file that it supposed to be overwritten is  `/usr/share/applications/mimeinfo.cache'
I have done a rebuild of gdesklets_0.35.1-1 from breezy and there is a difference there.
But maybe this file the rebuilt somehow. I'm gonna back it up just to be safe cause it contains a lot of info.
---Update--
As an update. This package broke every association that existed on my system. even restoring the original mimeinfo.cache does not help. But thats the price for testing isn't it?  :)[/QUOTE]

I apologize for the mistake. I haven't had any problems with it, which is strange.

I'll take the deb down immediately so nobody else makes the same mistake. And since you already backported the one from Breezy, I'll look into doing some other ports. Sorry for the inconvenience.


EDIT: I found a way to fix it for you, jon_gunnar. All you need to do is run:

```
sudo dpkg-reconfigure shared-mime-info
```

If you made any custom changes you probably have to redo them, I'm not sure. But anyway, this will fix the file association problem. (It took me a while to find which thing it was that had this.)

---

### Post by Tamir on 2005-07-24
No, don't take another port, take the source from breezy, and port it to hoary (add you name in debian/changelog, and compile on hoary).

---

### Post by jensyt on 2005-07-24
Well, for anyone who cares, here's a "backport" of the latest Breezy AMD64 gDesklets. It's not the absolute newest version of gDesklets, though, which is why I'm still going to try to making my original deb work properly.

[http://home.programmer-art.org/jens/gdesklets_0.35.1-2_amd64.deb](http://home.programmer-art.org/jens/gdesklets_0.35.1-2_amd64.deb)

And for anyone who wants it:

[http://home.programmer-art.org/jens/gdesklets_0.35.1.orig.tar.gz](http://home.programmer-art.org/jens/gdesklets_0.35.1.orig.tar.gz)
[http://home.programmer-art.org/jens/gdesklets_0.35.1-1.dsc](http://home.programmer-art.org/jens/gdesklets_0.35.1-1.dsc)
[http://home.programmer-art.org/jens/gdesklets_0.35.1-1.diff.gz](http://home.programmer-art.org/jens/gdesklets_0.35.1-1.diff.gz)

NOTE: This one doesn't mess up any file associations. It was actually made with jdong's **ubp-build.py** script.

---

### Post by jon_gunnar on 2005-07-24
[QUOTE=jensyt]I apologize for the mistake. I haven't had any problems with it, which is strange.

I'll take the deb down immediately so nobody else makes the same mistake. And since you already backported the one from Breezy, I'll look into doing some other ports. Sorry for the inconvenience.


EDIT: I found a way to fix it for you, jon_gunnar. All you need to do is run:

```
sudo dpkg-reconfigure shared-mime-info
```

If you made any custom changes you probably have to redo them, I'm not sure. But anyway, this will fix the file association problem. (It took me a while to find which thing it was that had this.)[/QUOTE]
Yes I had this one in, so it was fairly easy to manually fix the rest. This is the sort of things that do happend when testing new builds. Could have been much worser  ;-)

---

### Post by Tamir on 2005-07-24
Hello, Guys I need testers, everyone that interested, send me an email to:
[email]tamir@nooms.de[/email], What should you do as a tester? I will update you with emails about new packages that can be found in my tests repository:

deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) tests main
and you should only install the packages, and tell how it goes :)

---

### Post by DancingSun on 2005-07-24
Requesting the following:
[list=1]
[*]The latest [Ruby](http://www.ruby-lang.org/en/).  Preferably with the standard libraries.  The way it is packaged right now is horrible, as the standard libraries are separately packaged, and I had to select over a dozen of them individually in Synaptic to get [Ruby on Rails](http://www.rubyonrails.org) working.
[*][RubyGems](http://docs.rubygems.org/).
[/list]

---

### Post by tseliot on 2005-07-25
I can't find "libesd-alsa0" in Tamir's repos any more. It worked yesterday, then I reinstalled Ubuntu64 today and:

alberto@ubuntu:~$ sudo apt-get install libesd-alsa0
Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate


These is my sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) hoary main

I really need that file to make mediaplayers (xmms, etc) work, please.

---

### Post by smoon on 2005-07-25
[QUOTE=tseliot]I can't find "libesd-alsa0" in Tamir's repos any more. It worked yesterday, then I reinstalled Ubuntu64 today and:

alberto@ubuntu:~$ sudo apt-get install libesd-alsa0
Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate


These is my sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) hoary main

I really need that file to make mediaplayers (xmms, etc) work, please.[/QUOTE]


Looks like it's missing in the Packages file in Tamir's repository. The package itself is still there: [http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-amd64/libesd-alsa0_0.2.35-1_amd64.deb](http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-amd64/libesd-alsa0_0.2.35-1_amd64.deb). Maybe you can download and install it manually?

```
cd $HOME &&\
wget http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-amd64/libesd-alsa0_0.2.35-1_amd64.deb &&\
sudo dpkg -i libesd-alsa0_0.2.35-1_amd64.deb
```

---

### Post by tseliot on 2005-07-25
Thanks, I'll try it.

---

### Post by Octane on 2005-07-25
oh what a great project. you are so wonderful!

consider me your newest beta tests

---

### Post by Tamir on 2005-07-25
Yeah, I have a problem that I will fix tommorow :)
Does someone thought about a name for this project ?

---

### Post by DancingSun on 2005-07-25
[QUOTE=Tamir]Yeah, I have a problem that I will fix tommorow :)
Does someone thought about a name for this project ?[/QUOTE]
The "Unofficial Ubuntu backports for AMD64"?  Or maybe just "Unofficial Ubuntu AMD64 Repository", or "UUAR"!!! :wink:

---

### Post by Pse on 2005-07-25
"Clandestine Ubuntu64 Reps" or "Underground Ubuntu Reps"? LOL. Great job, Tamir!!

---

### Post by Kemotaha on 2005-07-26
[QUOTE=Tamir]Yeah, I have a problem that I will fix tommorow :)
Does someone thought about a name for this project ?[/QUOTE]
 Keep it simple

Pure 64bit Ubuntu

---

### Post by songochain on 2005-07-26
Somebody has any problem with last firefox?? i get segmentation fault when i try to run firefox

---

### Post by Tamir on 2005-07-26
[QUOTE=songochain]Somebody has any problem with last firefox?? i get segmentation fault when i try to run firefox[/QUOTE]
 If you mean firefox-1.0.6 - that can be found in TESTS repository, so I can't install it at all, something about mozilla chrome...

---

### Post by songochain on 2005-07-26
I mean 1.0.99 version or something. 1.0.6 works fine for me

---

### Post by Tamir on 2005-07-26
[QUOTE=songochain]I mean 1.0.99 version or something. 1.0.6 works fine for me[/QUOTE]
 Oh ok I understand. realy? 1.0.6 works for you?

---

### Post by DancingSun on 2005-07-26
[QUOTE=Tamir]Oh ok I understand. realy? 1.0.6 works for you?[/QUOTE]
I think 1.06 is available for AMD64 via the backports project now:

[http://ubuntuforums.org/showthread.php?t=51365](http://ubuntuforums.org/showthread.php?t=51365)

Or at least it shows up in the upgrade manager after I commented out Tamir's repository from sources.list.

I'll try it out and see how it goes.

Edit:
Upon update, all packages are signed, so it does seem like AMD64 now has some packages in the backports repository.  Among them, I was able to update VIM (although I don't use it) in addition to Firefox 1.0.6.  I'm using FIrefox 1.0.6 right now, and so far so good...

---

### Post by filterban on 2005-07-26
Nice! vim rocks.

I'll have to check that out.

---

### Post by jensyt on 2005-07-26
Those are official packages. I got them all and I don't have any backports mirrors in my sources.list...

There's a thread about that in Community Chat [here](http://ubuntuforums.org/showthread.php?t=51943).

---

### Post by songochain on 2005-07-26
[QUOTE=Tamir]Oh ok I understand. realy? 1.0.6 works for you?[/QUOTE]
Yes, it works :D but i've deleted your reppository to install 1.0.6 version

---

### Post by DancingSun on 2005-07-26
[QUOTE=jensyt]Those are official packages. I got them all and I don't have any backports mirrors in my sources.list...

There's a thread about that in Community Chat [here](http://ubuntuforums.org/showthread.php?t=51943).[/QUOTE]
Sweet, saved us some trouble :D

---

### Post by Tamir on 2005-07-26
Good, another one removed from my Todo list. Keep this good job.

---

### Post by micmic on 2005-07-26
Thanks for your job. I'm a newbbie and when I add your packges:
```
Imposible obtener http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-i386/Packages.gz  404 Not Found
``` 
I have an AMD64 (Linux 2.6.10-5-k7)
What about this??

PD: sorry for my english  :roll:

---

### Post by DancingSun on 2005-07-26
[QUOTE=micmic]Thanks for your job. I'm a newbbie and when I add your packges:
```
Imposible obtener http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-i386/Packages.gz  404 Not Found
``` 
I have an AMD64 (Linux 2.6.10-5-k7)
What about this??

PD: sorry for my english  :roll:[/QUOTE]

Well I got this error message when opening Synaptic today:

```
W: Couldn't stat source package list http://tamir.nooms.de hoary/main
Packages (/var/lib/apt/lists/tamir.nooms/
tamir.nooms.de_ubuntu_dists_hoary_main_binary-amd64_Packages) - 
Stat (2 No such file or directory)
```

Maybe it's related?

---

### Post by songochain on 2005-07-26
[QUOTE=micmic]Thanks for your job. I'm a newbbie and when I add your packges:
```
Imposible obtener http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-i386/Packages.gz  404 Not Found
``` 
I have an AMD64 (Linux 2.6.10-5-k7)
What about this??

PD: sorry for my english  :roll:[/QUOTE]
Hola, creo que español? bueno supongo q hablarás castellano. Te explico, el repositorio de tamir es para ubuntu amd64 y veo q estás intentando hacer un apt-get update teniendo ubuntu i386. Si quieres tener paquetes extras te recomiendo que te pases por la sección del foro "ubuntu backports".
Lo raro es que tienes un kernel para un athlon xp???? los amd64 llevan kernels (imagenes kernel) terminados en k8.

Sorry guys for speak in spanish, i've thought it's better explain to him in our native language.

---

### Post by DancingSun on 2005-07-26
[QUOTE=micmic]Thanks for your job. I'm a newbbie and when I add your packges:
```
Imposible obtener http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-i386/Packages.gz  404 Not Found
``` 
I have an AMD64 (Linux 2.6.10-5-k7)
What about this??

PD: sorry for my english  :roll:[/QUOTE]
Actually, micmic, why is your http path showing "binary-i386" and not "binary-amd64"?

Edit: Looks like you got the wrong kernel!  Or installed using the wrong CD!  You might be running on the 32-bit Ubuntu, from the look of things...

---

### Post by DancingSun on 2005-07-26
[QUOTE=songochain]Sorry guys for speak in spanish, i've thought it's better explain to him in our native language.[/QUOTE]
Ahem....no problemo! :-#

---

### Post by micmic on 2005-07-26
[QUOTE=DancingSun]Ahem....no problemo! :-#[/QUOTE]

 :) thanks [es-es mode on]gracias[es-es mode off]

[QUOTE=sogochain]los amd64 llevan kernels (imagenes kernel) terminados en k8.[/QUOTE]

ups! Synaptic --> K8 not found, I have k7, and k7 SMP

what's wrong? (the install CD is a x86 version)

---

### Post by DancingSun on 2005-07-26
[QUOTE=micmic]ups! Synaptic --> K8 not found, I have k7, and k7 SMP

what's wrong? (the install CD is a x86 version)[/QUOTE]
If the install CD is the x86 version, then that means you installed the 32-bit Ubuntu.  Which is still great, but isn't as cool as us Ubuntu AMD64 people :-P

If you want to use the AMD64 version of Ubuntu, you will need to download the AMD64 version of the Ubuntu installation CD.  It should be further down the download page.

---

### Post by micmic on 2005-07-26
Downloading... thanks a lot

---

### Post by DancingSun on 2005-07-26
[QUOTE=micmic]Downloading... thanks a lot[/QUOTE]
Word of warning though, as can be read in this forum, there are still quite a few programs that don't work or don't have installation packages for the AMD64 version of Ubuntu.

---

### Post by micmic on 2005-07-26
[QUOTE=DancingSun]Ubuntu AMD64 people[/QUOTE]
I'll be one of them ;)

---

### Post by DancingSun on 2005-07-26
[QUOTE=micmic]I'll be one of them ;)[/QUOTE]
Heheh, well let us know when you're on board so we can throw you a welcoming party...well a cyber welcome party...a...cyber and forums-based welcome party :mrgreen:

Btw, somebody really need to fix this smiley:  \\:D/

---

### Post by hod139 on 2005-07-26
[QUOTE=songochain]Somebody has any problem with last firefox?? i get segmentation fault when i try to run firefox[/QUOTE]

I also had a similar problem when upgrading.  The problem is that the mozilla-firefox package in Tamir's repository is the unstable 1.0.99+deerpark-alpha2-1, which happens to have a higher version number than the official mozilla-firefox package(1.0.6).  To fix, downgrade your version of mozilla-firefox to the official 1.0.6 version.

I hate making a request on my first post, but with firefox 1.0.6 in the ubuntu repository, could you please rename the mozilla-firefox package to just firefox or maybe something else like deerpark-firefox to avoid this upgrading problem. 

Other than this small problem, thanks a lot for setting this up.

---

### Post by hod139 on 2005-07-27
Tamir, again, thanks for setting this up.

As a request, would it be possible to get the acroread package?

---

### Post by Tamir on 2005-07-27
[QUOTE=hod139]Tamir, again, thanks for setting this up.

As a request, would it be possible to get the acroread package?[/QUOTE]
 added to my todo list.

New packages are available on tests repository :) :
kernel-image-2.6.12-amd64-k8 (2.6.12-4.4)
kernel-headers-2.6.12-amd64-k8 (2.6.12-4.4)

Can someone test it?

Soon:
kernel-image-2.6.12-amd64-generic
kernel-headers-2.6.12-amd64-generic

---

### Post by doobit on 2005-07-27
Tamir,
Did you already do ndiswrapper 1.2?

---

### Post by Tamir on 2005-07-27
[QUOTE=doobit]Tamir,
Did you already do ndiswrapper 1.2?[/QUOTE]
 No, but I will check it out when I'll have time :/

---

### Post by songochain on 2005-07-27
Somebody knows if there's any free version of linuxant?? I can install ndiswrapper but i need windows x64 drivers to install my wifi card on my laptop and they havent released yet
PD: sorry for off-topic

---

### Post by DancingSun on 2005-07-27
[QUOTE=hod139]I also had a similar problem when upgrading.  The problem is that the mozilla-firefox package in Tamir's repository is the unstable 1.0.99+deerpark-alpha2-1, which happens to have a higher version number than the official mozilla-firefox package(1.0.6).  To fix, downgrade your version of mozilla-firefox to the official 1.0.6 version.

I hate making a request on my first post, but with firefox 1.0.6 in the ubuntu repository, could you please rename the mozilla-firefox package to just firefox or maybe something else like deerpark-firefox to avoid this upgrading problem. 

Other than this small problem, thanks a lot for setting this up.[/QUOTE]
I second that.  Now the Ubuntu Update Manager is nagging me to update firefox to the dearpark version...which is annoying.

---

### Post by tseliot on 2005-07-28
[QUOTE=Tamir]added to my todo list.

New packages are available on tests repository :) :
kernel-image-2.6.12-amd64-k8 (2.6.12-4.4)
kernel-headers-2.6.12-amd64-k8 (2.6.12-4.4)

Can someone test it?

Soon:
kernel-image-2.6.12-amd64-generic
kernel-headers-2.6.12-amd64-generic[/QUOTE]
 I'll try your kernel as I made mine from Breezy source tree (2.6.12-4.4)and I want to see if they have the same issues.

---

### Post by tseliot on 2005-07-28
These are the first impressions:

The Drawbacks:

There are some problems with the device mapper: it doesn't detect my 4 memory card readers (I can't try them though as I don't have any MMC or SD card). This didn't happen with the kernel compiled from Breezy sources.

The Benefits:
It detects and automount my USB memory stick, which both my compiled Breezy kernel and the standard Breezy kernel didn't do.


I have some questions:

1)Did you converted the kernel packages from Breezy with the guide you posted (or in a similar way) or did you just customise a vanilla kernel (from kernel.org) using the settings of a Breezy kernel?

I'm asking you because I would like to enable DMA (for every device) from the kernel without relying on hdparm. For this reason I need the kernel source (or rather the kernel tree) in order to recompile your kernel (with "make oldconfig") with DMA enabled. Otherwise I will use Breezy source.

I think it would be nice having a kernel with DMA enabled in your repositories so as to make Ubuntu users' life easier. (I refer to all the newbies who can't compile a kernel and who are not either comfortable with or satisfied of hdparm). In my case hdparm allow just one of my 2 DVD readers  to use DMA (and I have to enable it manually every time I boot the system).

I'll make you know of any new issues.

Alberto

---

### Post by Tamir on 2005-07-28
I just downloaded this: 
[http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12](http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12)

and used .config of debian/config/amd64/amd64-k8, and changed some things.
:)

---

### Post by Drain on 2005-07-28
Well, I'm certainly interested in the 2.6.12 kernel you have (since it should have support for the HD-3000 tv-capture card I have) but I was just concerned about any new dependencies that I'd have to deal with in switching. Are there any other big system changes that would happen if I upgrade a from a (fairly) stock Hoary kernel? (Any chance there is a nvidia driver that goes with that kernel? ;-) )

And while I'm asking, two more things - First, what happens to this project as Breezy becomes stable? Do developments/improvements/security improvements still continue, or is everyone going to go to start using Breezy as the starting point for their new changes?

And second - any update on setting up nxserver packages? ;-) 

Thanks to all in the community getting involved in this project - it rocks. :-)

---

### Post by Tamir on 2005-07-28
[QUOTE=Drain]Well, I'm certainly interested in the 2.6.12 kernel you have (since it should have support for the HD-3000 tv-capture card I have) but I was just concerned about any new dependencies that I'd have to deal with in switching. Are there any other big system changes that would happen if I upgrade a from a (fairly) stock Hoary kernel? (Any chance there is a nvidia driver that goes with that kernel? ;-) )

And while I'm asking, two more things - First, what happens to this project as Breezy becomes stable? Do developments/improvements/security improvements still continue, or is everyone going to go to start using Breezy as the starting point for their new changes?

And second - any update on setting up nxserver packages? ;-) 

Thanks to all in the community getting involved in this project - it rocks. :-)[/QUOTE]
 ha :) I use nvidia drivers with this kernel (nvidia installer).
don't know what is going on with breezy, I just know, that when I used it, it was very unstable, that's why I am in hoary.
nxserver - I think freenx is possible, I can try.

---

### Post by DancingSun on 2005-07-28
I can't speak for Tamir, but I think the reason we have this project is so that we can "fill in the blanks", so to speak, for the lack of AMD64 backports.

I think when Breezy is released, I will basically use everything that's in Breezy, and use Tamir's repository for programs that are not available via the standard and the backports repositories.

It should be also noted that the [Official Backports Repository has been launched](http://ubuntuforums.org/showthread.php?t=52168), and supposingly that means the AMD64 backports will be available very soon!  My guess is by the time Breezy is released, this project may have already fulfilled its intended purpose.

Then again, by that time maybe we can have a slightly different purpose for this project.  The Backports project will only port packages that are already there for Breezy or the next version of Ubuntu that's in development, so I guess we could port even newer packages and try to sync up with the latest software releases and provide a cutting repository for those that are adventurous. :D

---

### Post by tseliot on 2005-07-29
[QUOTE=Tamir]ha :) I use nvidia drivers with this kernel (nvidia installer).
don't know what is going on with breezy, I just know, that when I used it, it was very unstable, that's why I am in hoary.
nxserver - I think freenx is possible, I can try.[/QUOTE]

I've tried to use the nvidia installer 7667 with your kernel with no results. I've also tried with mine (kernel image and headers) but no results yet.

There is no support for nvidia framebuffer in the kernel. What could the problem be?

this is the link to my post

Please have a look:

[http://www.ubuntuforums.org/showthread.php?t=52702](http://www.ubuntuforums.org/showthread.php?t=52702)

---

### Post by Tamir on 2005-07-29
[QUOTE=tseliot]I've tried to use the nvidia installer 7667 with your kernel with no results. I've also tried with mine (kernel image and headers) but no results yet.

There is no support for nvidia framebuffer in the kernel. What could the problem be?

this is the link to my post

Please have a look:

[http://www.ubuntuforums.org/showthread.php?t=52702](http://www.ubuntuforums.org/showthread.php?t=52702)[/QUOTE]
 Do you have kernel-headers-2.6.12-amd64-k8 (2.6.12-4.4) installed too?

---

### Post by Corbelius on 2005-07-29
*Request*

Why not to add [GAIM v1.4.0](http://gaim.sourceforge.net/)  and [MUINE v0.8.3](http://muine.gooeylinux.org/) ?

Tnx :D

P.S.: hello to all, my first post in this forum  :wink:

---

### Post by Tamir on 2005-07-29
[QUOTE=Corbelius]*Request*

Why not to add [GAIM v1.4.0](http://gaim.sourceforge.net/)  and [MUINE v0.8.3](http://muine.gooeylinux.org/) ?

Tnx :D

P.S.: hello to all, my first post in this forum  :wink:[/QUOTE]
 Ok i will make muine.
about gaim - I can make deb of it, but I know someone who made this and he doesn't answer me :/

Edit: Welcome!  :-P enjoy.

---

### Post by tseliot on 2005-07-29
There's an error when I accept to install ia32 OpenGL compatibility libraries (I have an AMD64)

ERROR: The runtime configuration check failed for library 'libGL.so.1.0.7667'
(expected: '/emul/ia32-linux/usr/lib/libGL.so.1', found:
'/usr/lib32/libGL.so.1'). The most likely reason for this is that
conflicting OpenGL libraries are installed in a location not inspected
by `nvidia-installer`. Please be sure you have uninstalled any
third-party OpenGL and third-party graphics driver packages.

How could this be solved?

---

### Post by jensyt on 2005-07-29
I'm not sure if Muine can be made, since it depends on Mono, which, from what I've gathered, isn't really supported on 64bit. Perhaps that's changed since I last looked...

Just a small word of warning. :)

---

### Post by Corbelius on 2005-07-29
[QUOTE=tseliot]There's an error when I accept to install ia32 OpenGL compatibility libraries (I have an AMD64)

ERROR: The runtime configuration check failed for library 'libGL.so.1.0.7667'
(expected: '/emul/ia32-linux/usr/lib/libGL.so.1', found:
'/usr/lib32/libGL.so.1'). The most likely reason for this is that
conflicting OpenGL libraries are installed in a location not inspected
by `nvidia-installer`. Please be sure you have uninstalled any
third-party OpenGL and third-party graphics driver packages.

How could this be solved?[/QUOTE]

Downgrade to kernel 2.6.11.12, install tha nvidia ubuntu package v7174 and "module-assistant", with the module assistant build nvidia module for your kernel... and we wait for the 7667 package in the repository ;)  ](*,)

P.s: sorry for my bad english  ](*,)

---

### Post by Corbelius on 2005-07-29
[QUOTE=jensyt]I'm not sure if Muine can be made, since it depends on Mono, which, from what I've gathered, isn't really supported on 64bit. Perhaps that's changed since I last looked...

Just a small word of warning. :)[/QUOTE]

From the ubuntu breezy repository's (but also in the debian alioth amd64):

mono - Mono CLI (.NET) runtime
mono-assemblies-arch - architecture specific files for Mono's class library
mono-assemblies-base - Mono class library - transistion package
mono-common - common files for Mono
mono-devel - Mono CLI (.NET) runtime with development tools
mono-gac - Mono GAC tool
mono-jay - LALR(1) parser generator oriented to Java/.NET
mono-jit - fast CLI (.NET) JIT compiler for Mono
mono-mcs - Mono C# compiler
mono-utils - Mono utilities
monodevelop - C#/Java/Nemerle/ILasm Development Environment

:D

---

### Post by tseliot on 2005-07-29
> **Corbelius]Downgrade to kernel 2.6.11.12, install tha nvidia ubuntu package v7174 and "module-assistant", with the module assistant build nvidia module for your kernel... and we wait for the 7667 package in the repository  said:**
> (*,)

P.s: sorry for my bad english  ](*,)

I've SOLVED (well, it wasn't me) this problem and made a HOWTO, check it out!

[http://www.ubuntuforums.org/showthread.php?p=277659#post277659](http://www.ubuntuforums.org/showthread.php?p=277659#post277659)

---

### Post by tseliot on 2005-07-29
Tamir, I made a kernel image and its headers from Breezy tree 2.6.12-5.5 with DMA enabled for every device. they are for K8 for now. 

Do you want me to send them to you? I've tested them and they seem stable and don't give me the errors I reported about your kernel during the bootstrap (no offense but my computer is highly Linux-unfriendly). 

P.S.
I could make kernels for any 64bit arch and with DMA enabled only for harddisks (as Ubuntu's default).

Please, let me know, I just want to help.

---

### Post by jensyt on 2005-07-30
[QUOTE=Corbelius]From the ubuntu breezy repository's (but also in the debian alioth amd64):

mono - Mono CLI (.NET) runtime
mono-assemblies-arch - architecture specific files for Mono's class library
mono-assemblies-base - Mono class library - transistion package
mono-common - common files for Mono
mono-devel - Mono CLI (.NET) runtime with development tools
mono-gac - Mono GAC tool
mono-jay - LALR(1) parser generator oriented to Java/.NET
mono-jit - fast CLI (.NET) JIT compiler for Mono
mono-mcs - Mono C# compiler
mono-utils - Mono utilities
monodevelop - C#/Java/Nemerle/ILasm Development Environment

:D[/QUOTE]

The problem with this is that you either have to get it all from another repository, or you have to backport the entire thing - something I don't think would be an easy venture. So, either way, there'll be quite a bit of work involved and it won't work with a standard AMD64 Hoary system. And if it doesn't work with the standard system, it shouldn't be put in the repositories for us because we don't want anything to be broken.

My vote is to not try and make Muine available, unless you manage to make ALL those packages available to the normal Hoary system without breaking something. It may be possible, and it may somehow turn out to be easy, but good luck.

---

### Post by Tamir on 2005-07-30
[QUOTE=tseliot]Tamir, I made a kernel image and its headers from Breezy tree 2.6.12-5.5 with DMA enabled for every device. they are for K8 for now. 

Do you want me to send them to you? I've tested them and they seem stable and don't give me the errors I reported about your kernel during the bootstrap (no offense but my computer is highly Linux-unfriendly). 

P.S.
I could make kernels for any 64bit arch and with DMA enabled only for harddisks (as Ubuntu's default).

Please, let me know, I just want to help.[/QUOTE]

Yes! send me to email, it will be great.
Note: my friend made many mono packages for hoary 64bit, I will check it.

---

### Post by DancingSun on 2005-07-30
Newest [SMEG](http://ubuntuforums.org/showthread.php?t=38183)

---

### Post by pailhead on 2005-07-30
Can someone do the latest **Clearlooks** GTK theme.. **0.6.2** I believe is the latest. I've been trying but I can't get it to work.

---

### Post by Tamir on 2005-07-31
[QUOTE=DancingSun]Newest [SMEG](http://ubuntuforums.org/showthread.php?t=38183)[/QUOTE]
 Done. New packages: smeg-0.7.5, python-xdg-0.14, **Gaim 1.4.0** (thanks to [mo42](http://ubuntuforums.org/member.php?u=22260)).

---

### Post by DancingSun on 2005-07-31
Problem with GAIM 1.4 upgrade on Synaptic:

```
gaim:
  Depends: gaim-data (=1:1.4.0-1ubuntu1~5.04ubp1) but 1:1.1.4-1ubuntu4.3 is to be installed
```

---

### Post by Tamir on 2005-07-31
[QUOTE=DancingSun]Problem with GAIM 1.4 upgrade on Synaptic:

```
gaim:
  Depends: gaim-data (=1:1.4.0-1ubuntu1~5.04ubp1) but 1:1.1.4-1ubuntu4.3 is to be installed
```[/QUOTE]
 FIxed :), my mistake.

---

### Post by tseliot on 2005-07-31
Tamir, check your email when you can, please. I've managed to send you the kernel (22mb).

---

### Post by Tamir on 2005-07-31
[QUOTE=tseliot]Tamir, check your email when you can, please. I've managed to send you the kernel (22mb).[/QUOTE]
 Ha :) I see, I will check it. what lang are you talking there? spanish? I understand only english/hebrew :) oh, and please, build your kernel like that:
```

make-kpkg --rootcmd fakeroot --initrd --append_to_version -amd64-k8 --revision 2.6.12-4.4 kernel_image kernel_headers

```

change the revision to right version. you will get this package:
kernel-image-2.6.12-amd64-k8_2.6.12-4.4.deb

---

### Post by tseliot on 2005-07-31
Ok, I'll do as you say.

By the way my kernel is 2.6.12.5.

Why are asking me if I speak Spanish? Did I send you a message in Spanish (it could have happened)?

I can speak English, Italian and Spanish ( I study Foreign Languages at the University)

---

### Post by Tamir on 2005-07-31
[QUOTE=tseliot]Ok, I'll do as you say.

By the way my kernel is 2.6.12.5.

Why are asking me if I speak Spanish? Did I send you a message in Spanish (it could have happened)?

I can speak English, Italian and Spanish ( I study Foreign Languages at the University)[/QUOTE]
 would you like to be a tester? I mean in my tests repository.

---

### Post by tseliot on 2005-07-31
Look, I have an exam on the 5th of September and I'll begin to study tomorrow. For this reason I can't be a full time tester. I'm trying to say that I would be glad to help you in my spare time. You know, I study all day (for example from 9.00AM to 8.00PM)  as I want to get my degree in November (and because I'm accustomed to study hard). I usually study in front of my computer, so I would be able to read your messages and give you some feedback (yes, sometimes I have a break from study)

So if this is not a problem for you I would be glad to be one of your testers.

---

### Post by Tamir on 2005-07-31
[QUOTE=tseliot]Look, I have an exam on the 5th of September and I'll begin to study tomorrow. For this reason I can't be a full time tester. I'm trying to say that I would be glad to help you in my spare time. You know, I study all day (for example from 9.00AM to 8.00PM)  as I want to get my degree in November (and because I'm accustomed to study hard). I usually study in front of my computer, so I would be able to read your messages and give you some feedback (yes, sometimes I have a break from study)

So if this is not a problem for you I would be glad to be one of your testers.[/QUOTE]
 Yes, it is better than nothing. Thanks :).
contact me on email please.

---

### Post by PKing1977 on 2005-07-31
Is there a way to get the latest Nvidia drivers put up? NVIDIA-Linux-x86_64-1.0-7667-pkg2.run 
Only version 1.0.7174-0ubuntu1 is avalable at this time and I need the new drivers to support my 7800. Everytime I try to run the Nvidia driver file I break my system :(

PKing

---

### Post by Tamir on 2005-07-31
[QUOTE=PKing1977]Is there a way to get the latest Nvidia drivers put up? NVIDIA-Linux-x86_64-1.0-7667-pkg2.run 
Only version 1.0.7174-0ubuntu1 is avalable at this time and I need the new drivers to support my 7800. Everytime I try to run the Nvidia driver file I break my system :(

PKing[/QUOTE]
 What is the package name ? :) sorry but I install only from installer.

---

### Post by PKing1977 on 2005-07-31
nvidia-glx

Pking

---

### Post by tseliot on 2005-07-31
[QUOTE=PKing1977]Is there a way to get the latest Nvidia drivers put up? NVIDIA-Linux-x86_64-1.0-7667-pkg2.run 
Only version 1.0.7174-0ubuntu1 is avalable at this time and I need the new drivers to support my 7800. Everytime I try to run the Nvidia driver file I break my system :(

PKing[/QUOTE]

Have you tried my HOWTO? It's easy.

---

### Post by PKing1977 on 2005-07-31
where is your howto.. I tried one last night and destroyed KDE :(
I am still a noob but learning /grin

PKing

---

### Post by tseliot on 2005-07-31
It's here:

[http://www.ubuntuforums.org/showthread.php?p=277659#post277659](http://www.ubuntuforums.org/showthread.php?p=277659#post277659)


For Tamir: I'm compiling kernel again right now. I'll try it and send it to you. (I haven't check my email yet)

---

### Post by tseliot on 2005-07-31
For PKing: What's your kernel? (if you don't know type "uname -r" in the Terminal or Konsole)

---

### Post by PKing1977 on 2005-07-31
2.6.10-5-amd64-generic


PKing

---

### Post by tseliot on 2005-07-31
This means you can skip this part of my HOWTO:

"3)the default gcc compiler needs to match the one used by the kernel (gcc-3.4 in my case) so:

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

CC=gcc-3.4 (here you have to put the number of the gcc you used to compile your kernel, which is 3.4 in my case*)

export CC"

---

### Post by tseliot on 2005-07-31
[QUOTE=Tamir]Ha :) I see, I will check it. what lang are you talking there? spanish? I understand only english/hebrew :) oh, and please, build your kernel like that:
```

make-kpkg --rootcmd fakeroot --initrd --append_to_version -amd64-k8 --revision 2.6.12-4.4 kernel_image kernel_headers

```

change the revision to right version. you will get this package:
kernel-image-2.6.12-amd64-k8_2.6.12-4.4.deb[/QUOTE]

The name of the file I get with your command is: kernel-image-2.6.12-amd64-k8_2.6.12-5.5_amd64.deb
kernel-headers-2.6.12-amd64-k8_2.6.12-5.5_amd64.deb

The only thing I've changed in your command is number "4" with "5" in "2.6.12-4.4".

---

### Post by Tamir on 2005-07-31
[QUOTE=tseliot]The name of the file I get with your command is: kernel-image-2.6.12-amd64-k8_2.6.12-5.5_amd64.deb
kernel-headers-2.6.12-amd64-k8_2.6.12-5.5_amd64.deb

The only thing I've changed in your command is number "4" with "5" in "2.6.12-4.4".[/QUOTE]
 perfect :) now send me.

---

### Post by DancingSun on 2005-07-31
I'm getting the following error when upgrading GAIM:

```
W: Failed to fetch http://tamir.nooms.de/ubuntu/./dists/hoary/main/binary-amd64//gaim_10x0.0007fbfffd94p-10221.4.0-1ubuntu1~5.04ubp1_amd64.deb
  404 Not Found


W: Failed to fetch http://tamir.nooms.de/ubuntu/./dists/hoary/main/binary-amd64//gaim-data_10x0.0000000fc8c45p-10221.4.0-1ubuntu1~5.04ubp1_all.deb
  404 Not Found
```

This happens after I click the "Apply" button in Synaptic.

Also, I'm getting this error when launching Synaptic after I switched to the test repository:

```
W: Couldn't stat source package list http://tamir.nooms.de tests/main Packages (/var/lib/apt/lists/tamir.nooms.de_ubuntu_dists_tests_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://tamir.nooms.de tests/main Packages (/var/lib/apt/lists/tamir.nooms.de_ubuntu_dists_tests_main_binary-amd64_Packages) - stat (2 No such file or directory)
```

---

### Post by PKing1977 on 2005-07-31
It still wont let me install. The kernel does not match so the installer shuts down

PKing

---

### Post by tseliot on 2005-07-31
Do you have the kernel HEADERS installed? (check it on synaptic)

If not, If you have all the right repositories (if not, see the Unofficial Ubuntu starter guide) you should be able to install kernel 2.6.11 in synaptic (DO NOT uninstall your current kernel). Restart the computer and then try to install Nvidia driver again.

---

### Post by tseliot on 2005-08-01
Tamir, have you received my new kernel?

---

### Post by songochain on 2005-08-01
[QUOTE=DancingSun]I'm getting the following error when upgrading GAIM:
 
 ```
W: Failed to fetch http://tamir.nooms.de/ubuntu/./dists/hoary/main/binary-amd64//gaim_10x0.0007fbfffd94p-10221.4.0-1ubuntu1~5.04ubp1_amd64.deb
   404 Not Found
 
 
 W: Failed to fetch http://tamir.nooms.de/ubuntu/./dists/hoary/main/binary-amd64//gaim-data_10x0.0000000fc8c45p-10221.4.0-1ubuntu1~5.04ubp1_all.deb
   404 Not Found
```
 
 This happens after I click the "Apply" button in Synaptic.
 
 Also, I'm getting this error when launching Synaptic after I switched to the test repository:
 
 ```
W: Couldn't stat source package list http://tamir.nooms.de tests/main Packages (/var/lib/apt/lists/tamir.nooms.de_ubuntu_dists_tests_main_binary-amd64_Packages) - stat (2 No such file or directory)
 W: Couldn't stat source package list http://tamir.nooms.de tests/main Packages (/var/lib/apt/lists/tamir.nooms.de_ubuntu_dists_tests_main_binary-amd64_Packages) - stat (2 No such file or directory)
```[/QUOTE]
Same problem here

---

### Post by Tamir on 2005-08-01
[QUOTE=songochain]Same problem here[/QUOTE]
 Same here. :) But I fixed it. try now.

---

### Post by Corbelius on 2005-08-01
*Request* (again  :razz: )

[Marlin - A GNOME Sample Editor](http://gnomefiles.org/app.php?soft_id=333)

Tha package dont exist in whichever repository, read the Gnomefiles comments first ;)

---

### Post by Tamir on 2005-08-01
[QUOTE=Corbelius]*Request* (again  :razz: )

[Marlin - A GNOME Sample Editor](http://gnomefiles.org/app.php?soft_id=333)

Tha package dont exist in whichever repository, read the Gnomefiles comments first ;)[/QUOTE]
 No problem, I will start tommorow.
I am looking for a professional music editor for my guitar recordes, so I can change the sound with effects like "flanger", 
does someone know know this program?

on windows I had "cool edit pro 2".

Edit: I think I found one: [http://www.gnuitar.com/](http://www.gnuitar.com/)

---

### Post by hod139 on 2005-08-02
Tamir,

I hate posting the same thing twice, but you never responded the first time, and maybe you missed it.  When I do an upgrade it wants to upgrade mozilla-firefox to the 1.0.99+deerpark-alpha2-1 version.  This version seg faults on my system, and you've stated that it isn't stable.  I was wondering if you could change the package name of 1.0.99+deerpark-alpha2-1 from mozilla-firefox to just firefox, or maybe deerpark-firefox.  That way I can just type 
apt-get upgrade
Right now I have to keep telling apt not to upgrade the mozilla-firefox package.

---

### Post by Tamir on 2005-08-02
Sorry I just didn't see it. I am re-building now this package. its new name is - firefox-deerpark.

---

### Post by hod139 on 2005-08-02
[QUOTE=Tamir]Sorry I just didn't see it. I am re-building now this package. its new name is - firefox-deerpark.[/QUOTE]

Thank you very much.  I don't know how you can handle all these requests, it would drive me crazy.  You are doing a great job though, and thanks for all the hard work.

---

### Post by DancingSun on 2005-08-02
Hey guys, I think the official AMD64 backports are up!  Well, at least I'm getting a whole lot more package on the update notifier...

---

### Post by Tamir on 2005-08-02
[QUOTE=DancingSun]Hey guys, I think the official AMD64 backports are up!  Well, at least I'm getting a whole lot more package on the update notifier...[/QUOTE]
 Yes they are, I think :)
When I browse their repositories I see binary-amd64 directory.

---

### Post by DancingSun on 2005-08-02
[QUOTE=Tamir]Yes they are, I think :)
When I browse their repositories I see binary-amd64 directory.[/QUOTE]
Sweet!  Ok, I guess our project's name can be the " Unofficial Bleeding-edge Ubuntu AMD64 Repository" then  ;-)

Hmm...the only things that I see in the binary-amd64 directory are Packages.bz2 and Packages.gz.  Actually, the same can be said for the other architectures...I thought I should see a list of the packages, no?  So is everything all compressed into those compression formats?

---

### Post by Kemotaha on 2005-08-02
[QUOTE=DancingSun]Sweet!  Ok, I guess our project's name can be the " Unofficial Bleeding-edge Ubuntu AMD64 Repository" then  ;-)

Hmm...the only things that I see in the binary-amd64 directory are Packages.bz2 and Packages.gz.  Actually, the same can be said for the other architectures...I thought I should see a list of the packages, no?  So is everything all compressed into those compression formats?[/QUOTE]
 Those files actually contain the list of packages.  The packages are kept in the pool Directory.  go up a few directories and you will see it.  They do that so common packages only have to be there once not one for each architecture.

---

### Post by Corbelius on 2005-08-02
Link to this backports repository? :)

---

### Post by DancingSun on 2005-08-02
[QUOTE=Corbelius]Link to this backports repository? :)[/QUOTE]
Here you go:
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

---

### Post by DancingSun on 2005-08-02
[QUOTE=Kemotaha]Those files actually contain the list of packages.  The packages are kept in the pool Directory.  go up a few directories and you will see it.  They do that so common packages only have to be there once not one for each architecture.[/QUOTE]
Ah, I see!

I also see that they still don't have the AMD64 version of the rar package....:(

Hey! Their [java-package](http://archive.ubuntu.com/ubuntu/pool/multiverse/j/java-package/)  don't have debs for each architecture! It just uses the "all" postfix, but I thought the java binaries are different for each architecture...plus Sun's Java 1.5 doesn't even have the plugin for AMD64...weird....

---

### Post by Tamir on 2005-08-03
New packages are available:
[list]
[*]gkrellm
[*]gkrellm-common
[*]gkrellmd
[/list]
Looks beautiful!

---

### Post by pailhead on 2005-08-03
Tamir, check your PM's :)

---

### Post by Tamir on 2005-08-03
[QUOTE=pailhead]Tamir, check your PM's :)[/QUOTE]
 Better idea - check you mail :)

---

### Post by DancingSun on 2005-08-03
Tamir, I still have the deerpark firefox packages on my update list...did you not change the name yet?

---

### Post by Tamir on 2005-08-03
[QUOTE=DancingSun]Tamir, I still have the deerpark firefox packages on my update list...did you not change the name yet?[/QUOTE]
 no I didn't. I am doing it right now.

---

### Post by pailhead on 2005-08-03
[QUOTE=Tamir]Better idea - check you mail :)[/QUOTE]

Check the mail Tamir, got a question about one of the comments in your email.  

Well looks like my deb is now in the backports so I guess that can't be added anymore. But I'd still like to know the appropriate way of including the dependencies in the control file... 

Thanks again...

---

### Post by DancingSun on 2005-08-04
[QUOTE=Tamir]no I didn't. I am doing it right now.[/QUOTE]
Many thanks to you Tamir! :D

---

### Post by tseliot on 2005-08-04
Tamir, any luck with the suggestions I gave you about the kernel?

---

### Post by Tamir on 2005-08-04
[QUOTE=tseliot]Tamir, any luck with the suggestions I gave you about the kernel?[/QUOTE]
 I totaly forgot about it :). I am compiling right now, thanks.

---

### Post by songochain on 2005-08-04
HI tamir! could u add to your repository more e17 modules like eweather??
U can see this modules in [this]("http://get-e.org/Screenshots/User_Submitted/_previews/pithlit-e17.png.html") screenshot from get-e.org
Thanks !

---

### Post by Kemotaha on 2005-08-04
Does the blackdown java package or the sun package have a working browser plugin in it?

---

### Post by hod139 on 2005-08-04
[QUOTE=Kemotaha]Does the blackdown java package or the sun package have a working browser plugin in it?[/QUOTE]

The blackdown does, sun does not.

---

### Post by Drain on 2005-08-04
Hey all. 

So a little while ago, I put in a request about building some packages for FreeNX on AMD64. I'm happy to say that it's no longer necessary - for me, at least, 'cause I built my own. Here's the forum thread where I talk about how I did it (beware, it's long):

[http://ubuntuforums.org/showthread.php?t=54417](http://ubuntuforums.org/showthread.php?t=54417)

Anyway, now that I have these packages built, how do I go about getting them accessable to others and in this repository? I'd like to hear how they worked out for other people. :-)

---

### Post by Tamir on 2005-08-04
[QUOTE=Drain]Hey all. 

So a little while ago, I put in a request about building some packages for FreeNX on AMD64. I'm happy to say that it's no longer necessary - for me, at least, 'cause I built my own. Here's the forum thread where I talk about how I did it (beware, it's long):

[http://ubuntuforums.org/showthread.php?t=54417](http://ubuntuforums.org/showthread.php?t=54417)

Anyway, now that I have these packages built, how do I go about getting them accessable to others and in this repository? I'd like to hear how they worked out for other people. :-)[/QUOTE]
 Ha :) I just told you that on your topic :)

---

### Post by DancingSun on 2005-08-04
Tamir,

I updated the [wiki page](https://wiki.ubuntu.com/x86_64packages)  to reflect the newly ported packages, I also added a list of requests that I found by doing a search in this thread.  Hopefully, this will help you and other people keep track of things.  You might want to put a link on the first post to the wiki, so people can refer to it.

Also, do you want the keep new requests in this thread?  If so, I can check back periodically for new requests and add it to the wiki page so it's easier to see what's been requested and what hasn't.  The alternative would be to tell the users to add their request on the wiki page themselves.

---

### Post by Corbelius on 2005-08-05
[QUOTE=DancingSun]Tamir,

I updated the [wiki page](https://wiki.ubuntu.com/x86_64packages)  to reflect the newly ported packages, I also added a list of requests that I found by doing a search in this thread.  Hopefully, this will help you and other people keep track of things.[/QUOTE]



[QUOTE=Corbelius]*Request*

Why not to add [MUINE v0.8.3](http://muine.gooeylinux.org/) ?

Tnx :D

P.S.: hello to all, my first post in this forum  :wink:[/QUOTE]

[QUOTE=Corbelius]*Request* (again  :razz: )

[Marlin - A GNOME Sample Editor](http://gnomefiles.org/app.php?soft_id=333)

Tha package dont exist in whichever repository, read the Gnomefiles comments first ;)[/QUOTE]

;)

---

### Post by songochain on 2005-08-05
What happened about e17 modules? :D

---

### Post by Tamir on 2005-08-05
I have some problems with marlin, something about gstreamer.. I need to fix that.
Muine is a problem, because it depents on mono.

---

### Post by jensyt on 2005-08-05
Hey, just so everyone knows. I can't do any testing for the next month probably, because I'm in the middle of a move and already packed up my AMD64 box. As soon as I get it back I'll start pumping out some more debs, since I finally got that gDesklets package working well.

So, just so you know, I haven't quit on you guys! Keep up the good work and everything. I'll be back to making and testing soon enough!

---

### Post by Tamir on 2005-08-05
OK. Just tell me when you are back. I have about 2-3 testers only.

---

### Post by arunsub on 2005-08-05
Here is an HOWTO of w32codecs for AMD64 Ubuntu. Why not add this to the list?
[http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399)

---

### Post by Tamir on 2005-08-05
[QUOTE=arunsub]Here is an HOWTO of w32codecs for AMD64 Ubuntu. Why not add this to the list?
[http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399)[/QUOTE]
 List of what? this is not a .deb, but I realy thoght to create new topic with lists of important howtos, what do you think?

---

### Post by arunsub on 2005-08-05
[QUOTE=Tamir]List of what? this is not a .deb, but I realy thoght to create new topic with lists of important howtos, what do you think?[/QUOTE]
I'm not a Linux programmer, so this question. Is it possible to make those set of commands into a single executable file or .deb file and add it to your list of packages?

---

### Post by Tamir on 2005-08-05
Yes, it could be a bash script, or .deb file (that run those bash commands).

---

### Post by arunsub on 2005-08-05
[QUOTE=Tamir]Yes, it could be a bash script, or .deb file (that run those bash commands).[/QUOTE]
Does that mean you can do that?

---

### Post by DancingSun on 2005-08-05
I'll add this to the request list on the [wiki](https://wiki.ubuntu.com/x86_64packages) , so anyone that can package .debs can take a stab at it if they want.

---

### Post by arunsub on 2005-08-05
[QUOTE=DancingSun]I'll add this to the request list on the wiki, so anyone that can package .debs can take a stab at it if they want.[/QUOTE]
Thanks.  :)

---

### Post by Corbelius on 2005-08-06
[QUOTE=Tamir]OK. Just tell me when you are back. I have about 2-3 testers only.[/QUOTE]

I can myself be proposed like tester? :)

---

### Post by Tamir on 2005-08-06
[QUOTE=Corbelius]I can myself be proposed like tester? :)[/QUOTE]
 Ofcourse, everybody can. Just contact me on email - [email]tamir@nooms.de[/email].
I will explain what you should do, or read on main post.

---

### Post by pailhead on 2005-08-06
Ok trying to make a repo entry for the guifications 2.12 for gaim and I'm running into a roadblock when I run dpkg-buildpackage -rfakeroot

Here's the error:
```
dh_builddeb
dpkg-deb: building package `guifications' in `../guifications_2.12-1_amd64.deb'. dpkg-genchanges
dpkg-genchanges: error: badly formed line in files list file, line 1
pailhead@ubuntu:~/packages/guifications/guifications-2.12$
```

Any ideas what might be causing this error?

---

### Post by pailhead on 2005-08-06
[QUOTE=pailhead]Ok trying to make a repo entry for the guifications 2.12 for gaim and I'm running into a roadblock when I run dpkg-buildpackage -rfakeroot

Here's the error:
```
dh_builddeb
dpkg-deb: building package `guifications' in `../guifications_2.12-1_amd64.deb'. dpkg-genchanges
dpkg-genchanges: error: badly formed line in files list file, line 1
pailhead@ubuntu:~/packages/guifications/guifications-2.12$
```

Any ideas what might be causing this error?[/QUOTE]
 ^bump^

---

### Post by Tamir on 2005-08-07
New packages!
[list]
[*]Freenx + nx packages (made by Drain)
[*]newset Ruby packages
[*]Rubygems
[/list]
```

apt-get update

```

---

### Post by Tamir on 2005-08-07
New packages!
[list]
[*]Freenx + nx packages (made by Drain)
[*]newset Ruby packages
[*]Rubygems
[/list]
```

apt-get update

```

 :smile:

---

### Post by DancingSun on 2005-08-08
Awesome!  Wiki page updated.

I just installed FreeNX, but how do I use it?  Any manuals I can look at?

I'll be trying out the new Ruby packages soon. :D

---

### Post by Tamir on 2005-08-08
[QUOTE=DancingSun]Awesome!  Wiki page updated.

I just installed FreeNX, but how do I use it?  Any manuals I can look at?

I'll be trying out the new Ruby packages soon. :D[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=54417](http://ubuntuforums.org/showthread.php?t=54417)

But skip the part of installation packages ::)

---

### Post by Cyberman on 2005-08-08
Could someone give me information as to configuring a *Broadcom 802.11b/g wireless card* for the **m6811 emachine laptop** on _Kubuntu_?

---

### Post by etitor on 2005-08-08
Tamir,

The GRAMPS genealogy program in the repositories is a rather old 1.* version. So I went to the SF homepage and downloaded the source of version 2.*. It compiled OK on my AMD64 system.

I have to say version 2.* of Gramps is *much* better than version 1.*.

I just followed your instructions on how to build a deb package from this new version. This is my first attempt at that. It appears I managed to do it well.

If you think it can be of interest to our community I can send you the deb package I made (2.7 MB).

---

### Post by Tamir on 2005-08-08
[QUOTE=etitor]Tamir,

The GRAMPS genealogy program in the repositories is a rather old 1.* version. So I went to the SF homepage and downloaded the source of version 2.*. It compiled OK on my AMD64 system.

I have to say version 2.* of Gramps is *much* better than version 1.*.

I just followed your instructions on how to build a deb package from this new version. This is my first attempt at that. It appears I managed to do it well.

If you think it can be of interest to our community I can send you the deb package I made (2.7 MB).[/QUOTE]
 why isn't that in my mail inbox already? :)
just kidding, Don't forget to send me all the files.

---

### Post by etitor on 2005-08-08
[QUOTE=Tamir]why isn't that in my mail inbox already? :)
just kidding, Don't forget to send me all the files.[/QUOTE]
In a couple of minutes!

---

### Post by DancingSun on 2005-08-08
Ok, I installed and setted up the FreeNX server.  However, when trying to connect to the server via a Win2k machine with NXClient, all I get is a "!M" logo on a black screen.  Sometimes  I just get a black screen, and nothing else.  I also can't close the NXClient window, I have to force-quit by using the task manager.  And even then, I noticed that the "nxssh" process still runs in the background.

I have setup the NXClient session to use GNOME.

A brief search in the forums indicates this has happened with the newer backports release as well, and they have since rolled back to an older version that was working before.  Unfortunately, I could not find any solution to this problem...:(

Any ideas? Pointers?

---

### Post by Tamir on 2005-08-09
New packages:
- The whole enlightenment CVS - snapshot 2 (tests repository)
- module weather included in package "emodules".

---

### Post by Drain on 2005-08-09
[QUOTE=DancingSun]Ok, I installed and setted up the FreeNX server.  However, when trying to connect to the server via a Win2k machine with NXClient, all I get is a "!M" logo on a black screen.  Sometimes  I just get a black screen, and nothing else.  I also can't close the NXClient window, I have to force-quit by using the task manager.  And even then, I noticed that the "nxssh" process still runs in the background.

I have setup the NXClient session to use GNOME.

(...snip...)

Any ideas? Pointers?[/QUOTE]

Well, I've only had luck connecting to a FreeNX server that is running XFCE. I mentioned that in the Howto I wrote, found here: [http://ubuntuforums.org/showthread.php?t=54417](http://ubuntuforums.org/showthread.php?t=54417) 

I had the same problems with both Gnome and KDE, but it worked for me when I ran with XFCE.

---

### Post by DancingSun on 2005-08-09
[QUOTE=Drain]Well, I've only had luck connecting to a FreeNX server that is running XFCE. I mentioned that in the Howto I wrote, found here: [http://ubuntuforums.org/showthread.php?t=54417](http://ubuntuforums.org/showthread.php?t=54417) 

I had the same problems with both Gnome and KDE, but it worked for me when I ran with XFCE.[/QUOTE]
Bummer.

Well, I found this old [announcement](http://mail.kde.org/pipermail/freenx-knx/2005-July/001690.html) that states that the 0.4.2 release fixes the GNOME session black screen issue:
> * Fixed problems with GNOME sessions: Gnome didn't start at all -- 
  screen remained black. You should now be able to fully enjoy Gnome
  sessions with FreeNX 0.4.2. 
Did they break it again with 0.4.3?
Can you please build a version 0.4.2 package, Dain?   ;-)

---

### Post by Drain on 2005-08-09
[QUOTE=DancingSun]Bummer.

Well, I found this old [announcement](http://mail.kde.org/pipermail/freenx-knx/2005-July/001690.html) that states that the 0.4.2 release fixes the GNOME session black screen issue:

Did they break it again with 0.4.3?
Can you please build a version 0.4.2 package, Drain?   ;-)[/QUOTE]


I'm been planning to go out of town soon, so I don't know if I'll be able to get to it for a while yet. And even then, I have no idea about how complex the process of going back to create a 0.4.2 package will be. (I just did some copy/paste instructions to create the last one! ;-) )

But I hope to keep an eye out on the mailing list, and if I see a potential fix or update, I'll make a note of it in the other thread.  :grin:

---

### Post by Killy on 2005-08-09
Really nice work! Thanks to all involved persons!

What about a CHM Viewer? (I have the slight feeling that [xCHM does not work as it should](http://ubuntuforums.org/showthread.php?t=54935) because I have the x64 version of Ubuntu.)

And is there really no way to install Flash for Firefox yet? I mean, there is a libflash-mozplugin package in Synaptic that crashes my FF...

Keep it up
Marc

---

### Post by Tamir on 2005-08-09
[QUOTE=Drain]I'm been planning to go out of town soon, so I don't know if I'll be able to get to it for a while yet. And even then, I have no idea about how complex the process of going back to create a 0.4.2 package will be. (I just did some copy/paste instructions to create the last one! ;-) )

But I hope to keep an eye out on the mailing list, and if I see a potential fix or update, I'll make a note of it in the other thread.  :grin:[/QUOTE]
 Drain, I have time to do it instead of you, are you interested?

---

### Post by PKing1977 on 2005-08-09
I see that you have kernel 2.6.12 up. Is there anyway to get the SMP patch for this?

PKing

---

### Post by songochain on 2005-08-09
[QUOTE=Tamir]New packages:
- The whole enlightenment CVS - snapshot 2 (tests repository)
- module weather included in package "emodules".[/QUOTE]
Thanks :)

---

### Post by Tamir on 2005-08-10
[QUOTE=songochain]Thanks :)[/QUOTE]
 The module worked for you? not for me, but enlightenment yes.
about smp kernel, yes we are working on that :)

---

### Post by Tamir on 2005-08-10
[COLOR=Green]Important Messege![/COLOR]
[list]
[*]I did a little sync to my repository, I added the sections: universe, multiverse and restricted.
[*]New repository added - cvs snapshots packages (packages from cvs).
[/list]
Please update your /etc/apt/sources.list:
```

## amd64 users repository
deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) hoary main universe multiverse restricted

## CVS snapshots packages
deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) cvs main universe multiverse restricted

## amd64 packages testers repository
deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) tests main universe multiverse restricted 

```
do apt-get update. enjoy!

Soon I will add all sources of the packages to the server.

---

### Post by cakey on 2005-08-10
Very nice.  Thank you for all the hard work Tamir!

---

### Post by Tamir on 2005-08-10
New packages:
[list]
[*]inkscape
[*]libgc1c2 
[*]libgc-dev
[*]sensors-applet (made by Corbelius)
[*]freenx (0.4.2)
[*]freenx (0.4.4)
[/list]

Dancingsun, I forget what do you need and it's weird that you want 0.4.2 instead 0.4.3,
so I made 0.4.2 and 0.4.4, choose with synaptic what ever you want...

---

### Post by songochain on 2005-08-10
[QUOTE=Tamir]The module worked for you? not for me, but enlightenment yes.
about smp kernel, yes we are working on that :)[/QUOTE]
I cant do a dist-upgrade and i've changed my source.lst with your new repositories

```
songochain@ximian64:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libepeg0
The following packages will be upgraded:
  edb-tools edje0-bin elicit embryo0-bin engage enlightenment
  enlightenment-data entice entrance eutils examine libe libecore0 libedb1
  libedje0 libeet0 libembryo0 libemotion0 libengrave0 libepsilon0
  libepsilon0-dev libesmart0 libetox0 libevas0 libewl0 libimlib2 xpdf
  xpdf-common xpdf-reader xpdf-utils
30 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.1MB/37.1MB of archives.
After unpacking 602kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libedb1 edb-tools libeet0 libevas0 libecore0 libembryo0 libedje0 libimlib2
  edje0-bin libepeg0 libepsilon0-dev libepsilon0 libesmart0 elicit embryo0-bin
  enlightenment-data libe enlightenment libemotion0 libewl0 examine engage
  entice entrance libengrave0 eutils libetox0
Install these packages without verification [y/N]? y
Get:1 http://security.ubuntu.com hoary-security/main xpdf-utils 3.00-11ubuntu3.1  [1271kB]
Err http://tamir.nooms.de tests/main libedb1 1.0.5.004
  404 Not Found
Err http://tamir.nooms.de tests/main edb-tools 1.0.5.004
  404 Not Found
Err http://tamir.nooms.de tests/main libeet0 0.9.10.013-1
  404 Not Found
Err http://tamir.nooms.de tests/main libevas0 0.9.9.013-1
  404 Not Found
Err http://tamir.nooms.de tests/main libecore0 0.9.9.013-1
  404 Not Found
Err http://tamir.nooms.de tests/main libembryo0 0.9.1.013-1
  404 Not Found
Err http://tamir.nooms.de tests/main libedje0 0.5.0-0cvs20050808
  404 Not Found
Err http://tamir.nooms.de tests/main libimlib2 1.2.1.004-1
  404 Not Found
Err http://tamir.nooms.de tests/main edje0-bin 0.5.0-0cvs20050808
  404 Not Found
Err http://tamir.nooms.de tests/main libepeg0 0.9.0-0cvs20050808
  404 Not Found
Err http://tamir.nooms.de tests/main libepsilon0-dev 0.0.2-0cvs20050808
  404 Not Found
Err http://tamir.nooms.de tests/main libepsilon0 0.0.2-0cvs20050808
  404 Not Found
Err http://tamir.nooms.de tests/main libesmart0 0.9.0-0cvs20050808
  404 Not Found
Err http://tamir.nooms.de tests/main elicit 0.9.0-0cvs20050808
  404 Not Found
Err http://tamir.nooms.de tests/main embryo0-bin 0.9.1.013-1
  404 Not Found
Err http://tamir.nooms.de tests/main enlightenment-data 0.16.999.003-0cvs2005080 8

```

So i cant probe new emodules :roll:

---

### Post by Tamir on 2005-08-10
I had a problem with the script that makes the packages list (gendir.sh), it fixed now.

---

### Post by songochain on 2005-08-10
[QUOTE=Tamir]The module worked for you? not for me[/QUOTE]
For me it doesnt work too, i think the module isnt installed because i get a error that says "no module name ... could be found ..."

Edit: could you add to your repository modconf app??

---

### Post by Tamir on 2005-08-10
[QUOTE=songochain]For me it doesnt work too, i think the module isnt installed because i get a error that says "no module name ... could be found ..."

Edit: could you add to your repository modconf app??[/QUOTE]
 What is it?
and about the module, I have it and I can load the module, but when I load it I have an error, we should remember it CVS anyway.

---

### Post by songochain on 2005-08-10
May be in a few days it can be fixed (we hope). Also i cant run emblem, i get Segmentation fault, anyway i can change backgrounds with e17setroot...

And modconf [http://packages.debian.org/unstable/admin/modconf]("http://packages.debian.org/unstable/admin/modconf")

Thanks for support ;)

---

### Post by DancingSun on 2005-08-10
[QUOTE=Tamir]New packages:
Dancingsun, I forget what do you need and it's weird that you want 0.4.2 instead 0.4.3,
so I made 0.4.2 and 0.4.4, choose with synaptic what ever you want...[/QUOTE]
I'm only seeing FreeNX 0.4.4 on Synaptic.  Can't force version...

Anyway, the reason I requested for 0.4.2 was because 0.4.3 doesn't work with GNOME, I just get a black screen.  I didn't know there was a 0.4.4 since on the FreeNX website the latest release is only 0.4.2.  But in anycase, I just tried 0.4.4 and I still get that black screen...:(

---

### Post by patricia on 2005-08-10
[QUOTE=Kemotaha]Does the blackdown java package or the sun package have a working browser plugin in it?[/QUOTE]


Hi guys!

Fist of all, sorry for the mistakes that l'll probably do (if I have already did) with english.

Second: thanks for the project.

Third: I need Help!!! I've been tried to make the java plugin work with Mozilla-Firefox 1.06 but I can't!! I tried all packages that I found! The last one was the j2re1.4-blackdown

It created a link in /usr/lib64/mozilla-firefox/plugin called libjavaplugin_oji.so apoint to /usr/lib/j2re1.4-blackdown/plugin/amd64/mozilla/libjavaplugin_oji.so  but it still not working.

There are tree more links for the same file in these directories:
   * /usr/lib/mozilla/plugins
   * /usr/lib/mozilla-firefox/plugins
   * /usr/lib64/mozilla/plugins
  
All of them like this one:   

libjavaplugin_oji.so -> /usr/lib/j2re1.4-blackdown/plugin/amd64/mozilla/libjavaplugin_oji.so


But, whem I try do open a page that uses java, the firefox just froze (stop working). I'll I can do is kill the proccess.


What is wrong??


I'm usin:
   *kernel: 2.6.10-5-amd64-generic
   *firefox: 1.0.6

My PC is:
   Compaq Presario R3000
   AMD 64 bits 3200
   Video: GeForce4 440 Go
   ... 
   what more is necessary to you know?




Thanks a lot

Patrícia

---

### Post by patricia on 2005-08-10
Hi!

If I got it rigth, there is no "skype package" for amd_64, is it? I got the Dynamic binary tar.bz2 package in the skype site but it is not working!! Even to sent messages.... 

Is there a way do make it work? 


Thanks,
Patrícia

---

### Post by DancingSun on 2005-08-10
Tamir...I'm getting this when installing FreeNX 0.4.2 now (error is at the bottom):
```
bill@Apollo:~$ sudo apt-get install freenx
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nxdesktop nxviewer
The following NEW packages will be installed:
  freenx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/50.5kB of archives.
After unpacking 197kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  freenx
Install these packages without verification [y/N]? y

Preconfiguring packages ...
Selecting previously deselected package freenx.
(Reading database ... 73213 files and directories currently installed.)
Unpacking freenx (from .../freenx_0.4.2-0ubuntu1_all.deb) ...
Setting up freenx (0.4.2-0ubuntu1) ...
dpkg: error processing freenx (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 freenx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Also, I could not see any other versions of FreeNX.

---

### Post by DancingSun on 2005-08-10
[QUOTE=patricia]Hi!

If I got it rigth, there is no "skype package" for amd_64, is it? I got the Dynamic binary tar.bz2 package in the skype site but it is not working!! Even to sent messages.... 

Is there a way do make it work? 


Thanks,
Patrícia[/QUOTE]
You probably won't want to use the dynamic binary download, as a dynamically linked binary means that it will try to access libraries on Ubuntu64, which might cause problems since we most likely have the 64-bit versions of the libraries.  Try the static binary download.

I just saw that there's a .deb package for Ubuntu, you might want to try that instead.

---

### Post by Kuolio on 2005-08-11
Request:

Could someone of you nice 64bit compiling souls make a 64bit version of transcode so that I could apt-get dvd::rip and other ripping tools? Would be so much apreciated, the GTK frontend to dvdrip has already been converted to 64bit and I can find it in the repos, but not the ripper itself (says needs transcode to fill dependencies). This would bring amd64 media support up yet another level, atleast in my book. 

Hope it's possible, ty in advance <3

---

### Post by DancingSun on 2005-08-11
[Wiki](https://wiki.ubuntu.com/x86_64packages) updated.

---

### Post by Kemotaha on 2005-08-11
After looking at the wiki I noticed that it says Freeciv 2.03 is built but I don't have it in the main repository.  Is it in the CVS and/or the testers repository?

Kemo

---

### Post by DancingSun on 2005-08-11
[QUOTE=Kemotaha]After looking at the wiki I noticed that it says Freeciv 2.03 is built but I don't have it in the main repository.  Is it in the CVS and/or the testers repository?

Kemo[/QUOTE]
I can confirm this.  I only see the version of Freeciv that's in the backports.  I can see that Tamir's repo has Freeciv 2.0.3 when browsing it using the browser, but it does not show up on Synaptic.

---

### Post by patricia on 2005-08-11
[QUOTE=DancingSun]You probably won't want to use the dynamic binary download, as a dynamically linked binary means that it will try to access libraries on Ubuntu64, which might cause problems since we most likely have the 64-bit versions of the libraries.  Try the static binary download.

I just saw that there's a .deb package for Ubuntu, you might want to try that instead.[/QUOTE]


Hi! I tried both and anyone worked!


What more should I do!?


Thanks!!

---

### Post by DancingSun on 2005-08-11
[QUOTE=patricia]Hi! I tried both and anyone worked!


What more should I do!?


Thanks!![/QUOTE]
Did you get any error messages?

---

### Post by patricia on 2005-08-11
[QUOTE=DancingSun]Did you get any error messages?[/QUOTE]


No! It is strange but any I dind't get anyone error message! The menus works, I can change one by ony, but anyone works... 


Thanks

---

### Post by DancingSun on 2005-08-11
[QUOTE=patricia]No! It is strange but any I dind't get anyone error message! The menus works, I can change one by ony, but anyone works... 


Thanks[/QUOTE]
Did you meant "nothing" rather "anyone"?

Did you try executing Skype from the terminal?  Maybe that will give more information.

---

### Post by patricia on 2005-08-11
[QUOTE=DancingSun]Did you meant "nothing" rather "anyone"?

Did you try executing Skype from the terminal?  Maybe that will give more information.[/QUOTE]


Yeah... I gues 'nothing' was what I tried to say! Sorry!


About skype... I did run it from the terminal! And I did not get any error message.
Sometimes, I can connect on skype. As usually, all the menus work fine. But, when I try do do something, like a call, it stop... the menus still working, but nothing happens.


Patricia

---

### Post by songochain on 2005-08-12
[QUOTE=Tamir]What is it?
and about the module, I have it and I can load the module, but when I load it I have an error, we should remember it CVS anyway.[/QUOTE]
Did u see if your emblem runs? because mine not
I load weather module with enlightenment_remote -module-load weather (also i've tried to load it with eweather), but it isn't. How do u load the module?

**Patricia** may be you did this before but did u try to do a dpkg-reconfigure skype???

---

### Post by Corbelius on 2005-08-12
[QUOTE=Kuolio]Request:

Could someone of you nice 64bit compiling souls make a 64bit version of transcode so that I could apt-get dvd::rip and other ripping tools? Would be so much apreciated, the GTK frontend to dvdrip has already been converted to 64bit and I can find it in the repos, but not the ripper itself (says needs transcode to fill dependencies). This would bring amd64 media support up yet another level, atleast in my book. 

Hope it's possible, ty in advance <3[/QUOTE]

In order now it's not possible to create a package of transcode for Hoary, demands too many libraries up to date, between which the libc6, wait for the breezy stable.
However, add this to yours source.list and tries:

```
# Marillat AMD64
deb http://cyberspace.ucla.edu/marillat/ unstable main 
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

[QUOTE=Corbelius]*Request* (again  :razz: )

[Marlin - A GNOME Sample Editor](http://gnomefiles.org/app.php?soft_id=333)

Tha package dont exist in whichever repository, read the Gnomefiles comments first ;)[/QUOTE]

Same here, required new libnautilusburn version 2.11.1, wait for breezy stable :D

---

### Post by pailhead on 2005-08-12
I'm trying trying to build the 64bit package for Rhythmbox 0.9.0 and I'm running your script Tamir to check for deps. 

Here's what I get when I run it:

```
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
base-files (>= 3.1.0ubuntu3 ), coreutils (>= 5.2.1-2ubuntu0 ), grep (>= 2.5.1.ds1-4ubuntu1 ), libacl1 (>= 2.2.26-1 ), libattr1 (>= 2.4.18-1 ), libc6 (>= 2.3.2.ds1-20ubuntu14 ), libncurses5 (>= 5.4-4 ), perl-base (>= 5.8.4-6ubuntu1 ), 
```

Where can I get the XML::Parser?  And is this needed to compile?

---

### Post by Corbelius on 2005-08-13
[QUOTE=pailhead]I'm trying trying to build the 64bit package for Rhythmbox 0.9.0 and I'm running your script Tamir to check for deps. 

Here's what I get when I run it:

```
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
base-files (>= 3.1.0ubuntu3 ), coreutils (>= 5.2.1-2ubuntu0 ), grep (>= 2.5.1.ds1-4ubuntu1 ), libacl1 (>= 2.2.26-1 ), libattr1 (>= 2.4.18-1 ), libc6 (>= 2.3.2.ds1-20ubuntu14 ), libncurses5 (>= 5.4-4 ), perl-base (>= 5.8.4-6ubuntu1 ), 
```

Where can I get the XML::Parser?  And is this needed to compile?[/QUOTE]

```
apt-cache search xml-parser
libxml-parser-perl - Perl module for parsing XML files
libdbix-xml-rdb-perl - Perl module for creating XML from a DBI datasource
libxml-parser-ruby1.6 - Interface of expat for the scripting language Ruby 1.6
libxml-parser-ruby1.8 - Interface of expat for the scripting language Ruby 1.8
``` 

 :roll: 

```
libxml-parser-perl - Perl module for parsing XML files
```

---

### Post by pailhead on 2005-08-13
[QUOTE=Corbelius]```

 :roll: 

libxml-parser-perl - Perl module for parsing XML files
```[/QUOTE]

Thanks.. man. Sorry I didn't know about the apt-cache deal. My bad...

---

### Post by alb_gra on 2005-08-13
Hi folks!

I've sent a mail to tamir a¡bout my new beta testing in this project.

There's a package i'd love having, the wine amd64 package, because the only thing that keeps xp in my hd is gaming. 

Good luck Tamir!

PD: Sorry about my poor english

---

### Post by Kemotaha on 2005-08-13
[QUOTE=DancingSun]I can confirm this.  I only see the version of Freeciv that's in the backports.  I can see that Tamir's repo has Freeciv 2.0.3 when browsing it using the browser, but it does not show up on Synaptic.[/QUOTE]
 Tamir

Any word on this?

---

### Post by rplantz on 2005-08-14
[QUOTE=Snodgrass]Does LaTeX work in AMD64?[/QUOTE]

I just brought my 335 page book over from my Mac OSX to my amd64. Didn't do anything special. It works out of the box.

Since it's a textbook on assembly language programming under Linux, it makes more sense to have it here instead of the Mac.  :) 

Of course, all my example programs are 32-bit. I had to do a little looking around to figure out how to assemble/link them in 32-bit mode.

Bob

---

### Post by Tamir on 2005-08-14
Look, I saw your mails guys, but I can't do anything because I don't have any linux dist for a few days, I sent my 512mb x 2 ram to computers compan, and I can't start the another computer. I am on 32bit computer (666hz, 128ram) so I can't do nothing from here :(.

---

### Post by Kemotaha on 2005-08-14
[QUOTE=Tamir]Look, I saw your mails guys, but I can't do anything because I don't have any linux dist for a few days, I sent my 512mb x 2 ram to computers compan, and I can't start the another computer. I am on 32bit computer (666hz, 128ram) so I can't do nothing from here :(.[/QUOTE]
 no problem Tamir

I jsut was making sure that it wasn't lost in the other posts.  Thanks for your response and all the great things you do for us.

---

### Post by joshuapurcell on 2005-08-14
Thanks for starting up this nice repository... this will definitely help people with this 64-bit OS. Here are the top three applications I would like to see made into a 64-bit .deb:

1. **zsnes**: [http://www.zsnes.com/](http://www.zsnes.com/)
2. **splashy** (already mentioned)
3. **teamspeak** (already mentioned): [http://goteamspeak.com/](http://goteamspeak.com/)

---

### Post by DancingSun on 2005-08-15
[QUOTE=joshuapurcell]Thanks for starting up this nice repository... this will definitely help people with this 64-bit OS. Here are the top three applications I would like to see made into a 64-bit .deb:

1. **zsnes**: [http://www.zsnes.com/](http://www.zsnes.com/)
2. **splashy** (already mentioned)
3. **teamspeak** (already mentioned): [http://goteamspeak.com/](http://goteamspeak.com/)[/QUOTE]
I believe splashy is already in the repository.  Check the first post.  You may want to take a look at the wiki page as well to view the list of requested packages.

---

### Post by DancingSun on 2005-08-15
How about keeping up to date with the latest nVidia OpenGL drivers for Linux?

---

### Post by patricia on 2005-08-15
[QUOTE=songochain]Did u see if your emblem runs? because mine not
I load weather module with enlightenment_remote -module-load weather (also i've tried to load it with eweather), but it isn't. How do u load the module?

**Patricia** may be you did this before but did u try to do a dpkg-reconfigure skype???[/QUOTE]


Hi!

Yeah, I can see the emblem of skype runing. It apperas in the systray.

About the module, I am not doing anything do load it. I have these modules loaded:

snd_intel8x0           34368  3
snd_ac97_codec         76704  1 snd_intel8x0
snd_pcm_oss            53668  2
snd_mixer_oss          19072  1 snd_pcm_oss
snd_pcm                96012  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24968  1 snd_pcm
snd                    55400  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11168  4 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm


Did I missed some?



dpkg-reconfigure skype didn't work for me. It returns that skype is not intalled. I got the static binary file from www,skype.com



Thanks

---

### Post by DancingSun on 2005-08-16
Patricia, try [this sound how-to](http://ubuntuforums.org/showthread.php?t=32063).  There's a post in the thread that said it make skype work.  You'll need to install libesd-alsa0 from Tamir's repository.

---

### Post by patricia on 2005-08-16
[QUOTE=DancingSun]Patricia, try [this sound how-to](http://ubuntuforums.org/showthread.php?t=32063).  There's a post in the thread that said it make skype work.  You'll need to install libesd-alsa0 from Tamir's repository.[/QUOTE]
 DancingSun, the sound for all other aplication is working prety fine. Should I try this sound how-to yet?


Patrícia

---

### Post by DancingSun on 2005-08-16
Yes.  The sound how-to enables multiple sounds simultaneously.  At the end of the how-to thread, there was a post about skype hanging when the user tried to dial out, and that how-to fixed his problem.  It sounded "similar" to your problem, so I thought this might worth a try.

It's likely that his problem has to do with line-in (mic) streams and line-out (speaker) streams fighting for the same sound resource.

---

### Post by patricia on 2005-08-16
[QUOTE=DancingSun]Yes.  The sound how-to enables multiple sounds simultaneously.  At the end of the how-to thread, there was a post about skype hanging when the user tried to dial out, and that how-to fixed his problem.  It sounded "similar" to your problem, so I thought this might worth a try.

It's likely that his problem has to do with line-in (mic) streams and line-out (speaker) streams fighting for the same sound resource.[/QUOTE]


Ok! I tried do follow the how to but I've alread found a problem... What should I do to install virtual packges?!  Exemplo: libesd-alsa0 is a virtual package and I just can't install it doing: sudo apt-get install libesd-alsa0  What should I do?


Thanks a lot!!

---

### Post by cakey on 2005-08-16
[QUOTE=patricia]What should I do?[/QUOTE]

Start a new thread.

---

### Post by patricia on 2005-08-16
[QUOTE=DancingSun]Yes.  The sound how-to enables multiple sounds simultaneously.  At the end of the how-to thread, there was a post about skype hanging when the user tried to dial out, and that how-to fixed his problem.  It sounded "similar" to your problem, so I thought this might worth a try.

It's likely that his problem has to do with line-in (mic) streams and line-out (speaker) streams fighting for the same sound resource.[/QUOTE]


I did!! Now I can make and receive calls, but I don't listen the call ring. I listen when the other side is talking, and it listen to me too, but I cant't listen the ring.

I check the confinguration of skype and in the audio devices, `calls` are set to /dev/dsp but `ringing` is desabled.  Why??



Thanks.

---

### Post by DancingSun on 2005-08-17
[QUOTE=patricia]I did!! Now I can make and receive calls, but I don't listen the call ring. I listen when the other side is talking, and it listen to me too, but I cant't listen the ring.

I check the confinguration of skype and in the audio devices, `calls` are set to /dev/dsp but `ringing` is desabled.  Why??



Thanks.[/QUOTE]
I'm glad it works now....but I don't use skype so I have no idea why ringing is disabled...

---

### Post by Kuolio on 2005-08-17
Request:

amaroK 1.3

It just came out and i would love to just apt-get it :)

---

### Post by negatory on 2005-08-17
I've compiled it and made a deb,you can install it using dpkg if you like
[taglib1.4](http://pwp.netcabo.pt/0245939201/linux/taglib_1.4-1_amd64.deb) 
[amarok1.3](http://pwp.netcabo.pt/0245939201/linux/amarok_1.3-1_amd64.deb) 
Hope that helps.
Pedro Carrico

---

### Post by Kuolio on 2005-08-17
Thanks negatory, that was fast  \\:D/

---

### Post by bagatonovic on 2005-08-17
I would love to see more emulators.  My favorites are the following:

Zsnes
Gens

As a side note, your efforts to make more AMD64 packages are greatly appreciated.

---

### Post by songochain on 2005-08-17
[QUOTE=patricia]Ok! I tried do follow the how to but I've alread found a problem... What should I do to install virtual packges?!  Exemplo: libesd-alsa0 is a virtual package and I just can't install it doing: sudo apt-get install libesd-alsa0  What should I do?


Thanks a lot!![/QUOTE]
May be you should install polyaudio ?
And about skype, check [this](http://ubuntuforums.org/showthread.php?t=16143&page=1) :)

---

### Post by DancingSun on 2005-08-17
Requesting [Pitfdll](http://sourceforge.net/projects/pitfdll/).
From the project homepage:
> Pitfdll is a GStreamer plugin that allows the use of binary files, such as Quicktime QTX or Directshow/DMO DLL files, for use as a playback codec in GStreamer-based media applications, such as Totem. With this plugin, people can playback proprietary file formats for which no free software implementation exists yet.
If we can get this to work in AMD64...we just might be able to solve the win32codecs problem!?

---

### Post by DancingSun on 2005-08-17
[GNOME Clipboard Daemon](http://members.chello.nl/~h.lai/gnome-clipboard-daemon/index.html)

Note: The "autopackage" project on that site also looks very nice.  I don't know if there are other initiatives like that in Linux, but Linux definitely needs a standardized decentralized package manager that can manage dependencies.  Centralized repositories introduces synchronization problems when the developer already released the software, but the repository manager has not made it available.  Which is one of the reasons why we have this thread/project.

---

### Post by Tamir on 2005-08-18
DancingSun, keep wiki updated, so I can see what to make packages of.
I am going to get my RAM soon, I know that first thing I make deb of it is lasted Nvidia Drivers

I move this project on step forward, we will have a website, a wiki etc.
Corbelius accepted my request to be a modurator beside me, so he can handle things too.

At time I am not here, you can try to think about a name for the project.
I know this whole messege is suck (my english), so I am sorry, try to understand me.

I am available on email (tamir@nooms.de), so feel free to ask whatever you want.

thank you all.

---

### Post by DancingSun on 2005-08-18
No problem, Tamir.  BTW, the wiki is already updated.  Oh, and don't forget about the freenx [problem](http://ubuntuforums.org/showpost.php?p=296119&postcount=267) I'm having. Basically an error occured while dpkg is trying to configure the package.  I've never used freenx before, so I'm really eager to find out if it is up to what it claims to be.

---

### Post by nwillis on 2005-08-18
Hey Howdy all.  I just tried making a deb of Gnomeradio, the only FM tuner app that *actually* works.

I have already sent it to Tamir.  Just thought I'd mention it for the record.

Assuming everything checks out, the next on my list to try and package is Cinepaint....

---

### Post by Tamir on 2005-08-18
[QUOTE=DancingSun]No problem, Tamir.  BTW, the wiki is already updated.  Oh, and don't forget about the freenx [problem](http://ubuntuforums.org/showpost.php?p=296119&postcount=267) I'm having. Basically an error occured while dpkg is trying to configure the package.  I've never used freenx before, so I'm really eager to find out if it is up to what it claims to be.[/QUOTE]
 about freenx I know what the problem is, until I will fix it - I will upload the working version.

nwills: thanks for the package, I will check it when I'll get my computer home (actually only ram, I build my computer myselfy). I belive it is something like sanday-monday.

---

### Post by hod139 on 2005-08-18
I would like to add a request for boost 1.33.  Maybe we can get an AMD64 version before an x86  :-)

---

### Post by kjus on 2005-08-18
I would like to have 
libmusepack
gstreamer0.8-musepack
on ubuntu 64 bits to get amarok playing mpc files.
Thank you very much for your work.

---

### Post by DancingSun on 2005-08-19
[QUOTE=Killy]Really nice work! Thanks to all involved persons!

What about a CHM Viewer? (I have the slight feeling that [xCHM does not work as it should](http://ubuntuforums.org/showthread.php?t=54935) because I have the x64 version of Ubuntu.)
(..)
[/QUOTE]
You know, I just installed xCHM....and it could not open the CHM file that I wanted to view.  No error messages.  Just "connecting..." and after that, nothing happened.  

Does anybody know of a good, robust CHM viewer that we can add to the repository?

I found these while doing a search in the forums:
[INDENT][http://freshmeat.net/projects/gnochm/](http://freshmeat.net/projects/gnochm/)
[http://freshmeat.net/projects/kchmviewer/](http://freshmeat.net/projects/kchmviewer/)
[http://freshmeat.net/projects/kama_helpexplorer/](http://freshmeat.net/projects/kama_helpexplorer/)[/INDENT]
Has anybody tried these?

Edit:
Ok, after checking out the above projects, I've crossed-out "kama" since that is a shareware.  So only "kchmviewer" and "gnochm".  Out of those two, I vote for "**gnochm**" since it is a GNOME application, therefore, fits in with whatever GNOME theme you have on.

---

### Post by DancingSun on 2005-08-19
[PostgreSQL](http://www.postgresql.org/ftp/source/v8.0.3/) 8.0.3 database.

---

### Post by nwillis on 2005-08-20
Request: gstreamer-faad

I can't understand why this isn't in the standard packages.  anybody know anything?

N

---

### Post by DancingSun on 2005-08-20
[QUOTE=nwillis]Request: gstreamer-faad

I can't understand why this isn't in the standard packages.  anybody know anything?

N[/QUOTE]
Do you have a link where we can get the sources?

Updated request list on wiki.

---

### Post by nwillis on 2005-08-21
Um, not a special one.  It's in 32 bit ubuntu, though -- backports, maybe?  I'm not sure.  Shouldn't we use the same source that they do, for compatibility?

---

### Post by mandos on 2005-08-21
could you add amule compiled for gtk 2, instead of gtk1?

---

### Post by Corbelius on 2005-08-21
[QUOTE=nwillis]Request: gstreamer-faad

I can't understand why this isn't in the standard packages.  anybody know anything?

N[/QUOTE]

It does not respect politics of ubuntu.

[QUOTE=DancingSun]Do you have a link where we can get the sources?

Updated request list on wiki.[/QUOTE]

Find the faad plugin source (and others) in the source package of gst-plugins [http://gstreamer.freedesktop.org/src/](http://gstreamer.freedesktop.org/src/)

[QUOTE=mandos]could you add amule compiled for gtk 2, instead of gtk1?[/QUOTE]

I can try.

---

### Post by Tamir on 2005-08-21
[QUOTE=Corbelius]It does not respect politics of ubuntu.



Find the faad plugin source (and others) in the source package of gst-plugins [http://gstreamer.freedesktop.org/src/](http://gstreamer.freedesktop.org/src/)



I can try.[/QUOTE]
 I tried a long time ago. It didn't work - but try!

---

### Post by nwillis on 2005-08-21
[QUOTE=Corbelius]It does not respect politics of ubuntu.
[/QUOTE]

Huh?  What do you mean, exactly?

[QUOTE=Corbelius]
Find the faad plugin source (and others) in the source package of gst-plugins [http://gstreamer.freedesktop.org/src/](http://gstreamer.freedesktop.org/src/)
I can try.[/QUOTE]

Well, like I siad in my previous post, this *is* in 32bit Ubuntu.  Therefore, shouldn't we try to use the same src package that they use?  Tell me how to track it down and I will do it myself.  

Nate

---

### Post by Corbelius on 2005-08-22
[QUOTE=nwillis]Huh?  What do you mean, exactly?[/QUOTE]

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28faad%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28faad%29)

---

### Post by Tamir on 2005-08-22
**[COLOR=Grey]OK. We have a wiki (also our website)![/COLOR]**

I have not done everything, but take a look anyway!
Just register and edit this wiki, and make it better, if someone can - fix my spelling problems.

Remember - We don't have a name to this project yet!
[http://tamir.nooms.de/wiki/](http://tamir.nooms.de/wiki/)

enjoy.  ;-)

---

### Post by hack_benjamin on 2005-08-22
[Request]
If you could get ruby rails then that would be great =D (i cant seem to get gem install rails to work)
Otherwise a BIG thankyou for the rest of the ruby stuff.

---

### Post by Tamir on 2005-08-22
[QUOTE=hack_benjamin][Request]
If you could get ruby rails then that would be great =D (i cant seem to get gem install rails to work)
Otherwise a BIG thankyou for the rest of the ruby stuff.[/QUOTE]
No problem, I will add it, know that you can just add this package to new wiki :)

---

### Post by DancingSun on 2005-08-22
[QUOTE=hack_benjamin][Request]
If you could get ruby rails then that would be great =D (i cant seem to get gem install rails to work)
Otherwise a BIG thankyou for the rest of the ruby stuff.[/QUOTE]
I installed Ruby on Rails using RubyGems.  Although I did it before we have the newest Ruby packages ported here.  Ruby on Rails has a lot of dependencies, you need to install all the packages mentioned in this wik pagei:
[http://www.rubyonrails.com:2750/rails/print/RailsOnUbuntuDebianTestingAndUnstable](http://www.rubyonrails.com:2750/rails/print/RailsOnUbuntuDebianTestingAndUnstable)

---

### Post by Tamir on 2005-08-22
[QUOTE=DancingSun]I installed Ruby on Rails using RubyGems.  Although I did it before we have the newest Ruby packages ported here.  Ruby on Rails has a lot of dependencies, you need to install all the packages mentioned in this wik pagei:
[http://www.rubyonrails.com:2750/rails/print/RailsOnUbuntuDebianTestingAndUnstable](http://www.rubyonrails.com:2750/rails/print/RailsOnUbuntuDebianTestingAndUnstable)[/QUOTE]
 Dancingsun, can you please update the new website with packages? you just don't answer me on email/private I don't know why :|.

---

### Post by DancingSun on 2005-08-22
[QUOTE=Tamir]Dancingsun, can you please update the new website with packages? you just don't answer me on email/private I don't know why :|.[/QUOTE]
Oops, sorry, didn't notice I have a PM message  :-P

---

### Post by DancingSun on 2005-08-22
[QUOTE=Tamir]No problem, I will add it, know that you can just add this package to new wiki :)[/QUOTE]
BTW, I think Ruby on Rails is one item that is better left to RubyGems to handle.  For one, Ruby on Rails is already released as a Gem directly by the developers, it just seems repetitive to make a deb package.  Secondly, RubyGems can take care of the package upgrades easily.  Plus, you can have different version of Ruby on Rails installed via Gems (for development purposes, you might need an older version of Ruby on Rails if you are maintaining or developing an existing website).

This brings up another topic, I believe the packages that Ruby on Rails depended on were all part of the "standard libraries" collection.  These were included in the Ruby install for Windows, I don't know why for Linux it has to be installed separately, but it would be nice to include the "standard libraries" as dependencies or suggested dependencies.

Edit:  You can all slap me now...I forgot I was the one requested for Ruby WITH standard libraries....I think in Tamir's repo, libruby contains the standard library.  I'm not sure if it has everything, but it sure looks like it has them all.

---

### Post by nwillis on 2005-08-22
[QUOTE=Corbelius][https://wiki.ubuntu.com/RestrictedFormats?highlight=%28faad%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28faad%29)[/QUOTE]

Again, this package is already currently in 32bit via backports.  I feel like I say this every time I post.  Furthermore, it shouldn't need pointing out that there are other non-free codecs -- such as MP3, to state the most obvious example -- which are supplied in 64bit backports.

To be clearer:
If FAAD is okay in 32bit, then it is okay in 64bit.  If MP3 is okay in 64bit, then FAAD is okay in 64bit.  There is absolutely no difference.

I would be happy to compile it myself if no one else is willing to do so, but there is no source deb for the 32bit package that I could find, and we should try to stay in sync with 32bit for identical packages.  If someone has a solution to this conundrum, please let me know and I personally will get right on it.  I, for one, fear no petty format.

N

---

### Post by Tamir on 2005-08-22
Ok just decied.

NOW is the time to decide about a name of the project. Please remeber it doesn't have to a decription of the project. Better a cool word. ;-)

---

### Post by nwillis on 2005-08-22
[QUOTE=Tamir]Ok just decied.

NOW is the time to decide about a name of the project. Please remeber it doesn't have to a decription of the project. Better a cool word. ;-)[/QUOTE]

How about: LXIV
?

Or perhaps Lexiv, to make it look more like a word?

N

---

### Post by Tamir on 2005-08-22
[QUOTE=nwillis]How about: LXIV
?

Or perhaps Lexiv, to make it look more like a word?

N[/QUOTE]
 Ok that's a start, any ideas?

---

### Post by DancingSun on 2005-08-22
TAMD64
"Tamir's AMD64" :)

---

### Post by DancingSun on 2005-08-22
[QUOTE=nwillis]Again, this package is already currently in 32bit via backports.  I feel like I say this every time I post.  Furthermore, it shouldn't need pointing out that there are other non-free codecs -- such as MP3, to state the most obvious example -- which are supplied in 64bit backports.

To be clearer:
If FAAD is okay in 32bit, then it is okay in 64bit.  If MP3 is okay in 64bit, then FAAD is okay in 64bit.  There is absolutely no difference.

I would be happy to compile it myself if no one else is willing to do so, but there is no source deb for the 32bit package that I could find, and we should try to stay in sync with 32bit for identical packages.  If someone has a solution to this conundrum, please let me know and I personally will get right on it.  I, for one, fear no petty format.

N[/QUOTE]
It should be noted that the 64-bit backports only started very recently (after the backports project became official).  That being said, I am already seeing some packages from the 32-bit backports repository being ported over to the 64-bit repository.  It's reasonable to expect that everything in the 32-bit backports that can be ported to the 64-bit platform will *eventually *be ported over.

---

### Post by hardw1re on 2005-08-22
I made a post about this on the hardware support forum, but is there a chance of the Logitech Quickcam Messenger (USB) webcam can be ported into a 64bit package?
the drivers for it are here: [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/) but i cant seem to get it to work / detect my camera.

---

### Post by DancingSun on 2005-08-22
Hmm...I don't see the "rubygems" package...I swear I saw it in the repository before...

---

### Post by DancingSun on 2005-08-22
[QUOTE=DancingSun]BTW, I think Ruby on Rails is one item that is better left to RubyGems to handle.  For one, Ruby on Rails is already released as a Gem directly by the developers, it just seems repetitive to make a deb package.  Secondly, RubyGems can take care of the package upgrades easily.  Plus, you can have different version of Ruby on Rails installed via Gems (for development purposes, you might need an older version of Ruby on Rails if you are maintaining or developing an existing website).

This brings up another topic, I believe the packages that Ruby on Rails depended on were all part of the "standard libraries" collection.  These were included in the Ruby install for Windows, I don't know why for Linux it has to be installed separately, but it would be nice to include the "standard libraries" as dependencies or suggested dependencies.

Edit:  You can all slap me now...I forgot I was the one requested for Ruby WITH standard libraries....I think in Tamir's repo, libruby contains the standard library.  I'm not sure if it has everything, but it sure looks like it has them all.[/QUOTE]

Ok, apparently, the libruby contains the "core" library only, and not the "standard" library.  The list of standard libraries can be found here:
[http://www.ruby-doc.org/stdlib/](http://www.ruby-doc.org/stdlib/)

I think most of these are already in the Ubuntu repositories, but they are available separately.  Creating a dependency to these would be nice.  Without these libraries you really can't do much in Ruby.

---

### Post by matsur on 2005-08-22
Hi all,

My gaim 1.5.0 package can be found here: [http://www.columbia.edu/~rxl2101/gaim_1.5.0-1_amd64.deb](http://www.columbia.edu/~rxl2101/gaim_1.5.0-1_amd64.deb)

HTH someone.

Cheers,
matsur

---

### Post by Kemotaha on 2005-08-23
Name issue:

I still like Pure64 but maybe something like:

64updated?  
DoubleBits?
Global64?
All about 64?

Just some ideas.

---

### Post by Tamir on 2005-08-23
[QUOTE=matsur]Hi all,

My gaim 1.5.0 package can be found here: [http://www.columbia.edu/~rxl2101/gaim_1.5.0-1_amd64.deb](http://www.columbia.edu/~rxl2101/gaim_1.5.0-1_amd64.deb)

HTH someone.

Cheers,
matsur[/QUOTE]
 I need the other files either (.diff, .dsc, orig.gz), please send me them on email.

I like Pure64!

---

### Post by Corbelius on 2005-08-23
[QUOTE=matsur]Hi all,

My gaim 1.5.0 package can be found here: [http://www.columbia.edu/~rxl2101/gaim_1.5.0-1_amd64.deb](http://www.columbia.edu/~rxl2101/gaim_1.5.0-1_amd64.deb)

HTH someone.

Cheers,
matsur[/QUOTE]

It's no good, you have created it with checkinstall, it wants also the gaim-data package :)

[QUOTE=Tamir]

I like Pure64![/QUOTE]

[http://debian-amd64.alioth.debian.org/](http://debian-amd64.alioth.debian.org/)

better ubuntu pure64 :D

---

### Post by Tamir on 2005-08-23
[QUOTE=Corbelius]It's no good, you have created it with checkinstall, it wants also the gaim-data package :)



[http://debian-amd64.alioth.debian.org/](http://debian-amd64.alioth.debian.org/)

better ubuntu pure64 :D[/QUOTE]
 corbelius, don't build it yourself ok? I just want to check something, then make it.

---

### Post by medication on 2005-08-23
Hey everyone... sorry that I disappeared for a little while.  I'm back and I'm willing to start testing (after work hours that is).  I'll be switching my repository over to the "tests" tonight.

---

### Post by Tamir on 2005-08-23
[QUOTE=medication]Hey everyone... sorry that I disappeared for a little while.  I'm back and I'm willing to start testing (after work hours that is).  I'll be switching my repository over to the "tests" tonight.[/QUOTE]
 Great, I already added you to testers list:
[http://tamir.nooms.de/wiki/doku.php?id=testers](http://tamir.nooms.de/wiki/doku.php?id=testers)

---

### Post by medication on 2005-08-23
Awesome... is there anything particular that you wanted me to work on / test?  

Also, I was wondering if we could put nvtv on the list of wanted packages? [http://sourceforge.net/projects/nv-tv-out/](http://sourceforge.net/projects/nv-tv-out/)

---

### Post by Tamir on 2005-08-23
[QUOTE=medication]Awesome... is there anything particular that you wanted me to work on / test?  

Also, I was wondering if we could put nvtv on the list of wanted packages? [http://sourceforge.net/projects/nv-tv-out/](http://sourceforge.net/projects/nv-tv-out/)[/QUOTE]
 Currently there are not packages to test, 'cause I can upload anything, I don't have linux right now. My computer is waiting for ram.

---

### Post by nwillis on 2005-08-23
'Nother request: quick-lounge-applet.
I found amd64 deb from Debian here:
[http://mirror.hamakor.org.il/pub/mirrors/debian-amd64/pool/main/q/quick-lounge-applet/](http://mirror.hamakor.org.il/pub/mirrors/debian-amd64/pool/main/q/quick-lounge-applet/) 

But it doesn't install as-is, claiming some suspicious dependencies -- version numbers specific to build num, etc.

---

### Post by Tamir on 2005-08-23
[QUOTE=nwillis]'Nother request: quick-lounge-applet.
I found amd64 deb from Debian here:
[http://mirror.hamakor.org.il/pub/mirrors/debian-amd64/pool/main/q/quick-lounge-applet/](http://mirror.hamakor.org.il/pub/mirrors/debian-amd64/pool/main/q/quick-lounge-applet/) 

But it doesn't install as-is, claiming some suspicious dependencies -- version numbers specific to build num, etc.[/QUOTE]
 Sorry I can't handle requests, I just don't have my amd64 right now.

---

### Post by DancingSun on 2005-08-23
[QUOTE=Corbelius][http://debian-amd64.alioth.debian.org/](http://debian-amd64.alioth.debian.org/)

better ubuntu pure64 :D[/QUOTE]
How about a substitute for "pure".  Like "Genuine64" or Genuinely64". Or maybe "Authentic64", "AuthenticMD64" <-- a play on AMD64.  "Absolute64", "Absolutely64"....

---

### Post by nwillis on 2005-08-23
We should be carful not to sound too similar to Tru64, the commercial Unix from DEC/Compaq/HP/Whoever's next.

Sure, nobody uses Tru64, but it's still a preexisting mark.

N

---

### Post by Tamir on 2005-08-24
[QUOTE=nwillis]We should be carful not to sound too similar to Tru64, the commercial Unix from DEC/Compaq/HP/Whoever's next.

Sure, nobody uses Tru64, but it's still a preexisting mark.

N[/QUOTE]
 But why "64" at all? what about a cool word? like "azuarus", "nirvana" you know...

---

### Post by nwillis on 2005-08-24
Hey, I agree 100%.  That's why I suggested my own cool word, lexiv ....

Nate

---

### Post by jamesrw on 2005-08-24
[QUOTE=DancingSun]How about a substitute for "pure".  Like "Genuine64" or Genuinely64". Or maybe "Authentic64", "AuthenticMD64" <-- a play on AMD64.  "Absolute64", "Absolutely64"....[/QUOTE]

```

james@[COLOR=Red]tux64[/COLOR]:
```

---

### Post by appleman77 on 2005-08-24
Is there a working version of FreeNX for AMD64 in the repository?

I get the following error from the current version:

subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
freenx

I read that it would be fixed - wasn't sure if it was or if something was wrong with my installation.

Thanks for everything!

---

### Post by Corbelius on 2005-08-24
[QUOTE=Tamir]But why "64" at all? what about a cool word? like "azuarus", "nirvana" you know...[/QUOTE]

I like a name with "64" in, simply why our packages is only for 64bit users :D

---

### Post by DancingSun on 2005-08-24
[QUOTE=nwillis]Hey, I agree 100%.  That's why I suggested my own cool word, lexiv ....

Nate[/QUOTE]
Hmm....If you don't mind me playing around with your idea...what about "LuXIV"?
The "u" is for Ubuntu, and of course, I emphasized LXIV for 64.

---

### Post by Tamir on 2005-08-24
[QUOTE=appleman77]Is there a working version of FreeNX for AMD64 in the repository?

I get the following error from the current version:

subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
freenx

I read that it would be fixed - wasn't sure if it was or if something was wrong with my installation.

Thanks for everything![/QUOTE]
 Currently no, I can't do anything right now 'cause I don't have my computer right now. If corbelius will create this package I will upload it.

everybody that knows how to make debs, please take freenx source from here:
[http://download.berlios.de/freenx/freenx-0.4.2.tar.gz](http://download.berlios.de/freenx/freenx-0.4.2.tar.gz)

and take the debian/ dir from here:
[http://debian.tu-bs.de/project/kanotix/unstable/f/freenx/](http://debian.tu-bs.de/project/kanotix/unstable/f/freenx/)

---

### Post by nwillis on 2005-08-25
[QUOTE=DancingSun]Hmm....If you don't mind me playing around with your idea...what about "LuXIV"?
The "u" is for Ubuntu, and of course, I emphasized LXIV for 64.[/QUOTE]

Aha....  very nice.

So in that sense, we could say that it means Ubuntu *in* 64 bits....

---

### Post by Tamir on 2005-08-25
[QUOTE=nwillis]Aha....  very nice.

So in that sense, we could say that it means Ubuntu *in* 64 bits....[/QUOTE]
 I know that's stupid but my friend told me it rings nice "uPackages". u = ubuntu. "packages for humans begins" - :) lol

---

### Post by Tamir on 2005-08-25
[QUOTE=Tamir]I know that's stupid but my friend told me it rings nice "uPackages". u = ubuntu. "packages for humans begins" - :) lol[/QUOTE]
 _Testers_: you ask why there are no packages to test, and there are. I sent a mail to all testers:

[http://tamir.nooms.de/wiki/doku.php?id=testers](http://tamir.nooms.de/wiki/doku.php?id=testers)

I guess you didn't check your emails, becuase you usually don't do it.
Please check your emails! thanks ;-)

---

### Post by DancingSun on 2005-08-25
I like "uPackages" and "LuXIV".  Of course, I'm leaning towards "LuXIV"  ;-) .

Any other ideas?  I think we should collect some generally accepted names and do a poll on them to decide which name we're going to use :).

Tamir, I'm not getting any emails from you/the project!  Could you give me the e-mail address that you are sending the e-mails from?  I want to add it in my address book to make sure Yahoo! doesn't sort it as bulk mail.  What's the title of the e-mail?

Edit:
E-mail notifications from the Ubuntu Forums work fine, however.  So, somehow I'm just not receiving mails from you...or the domain that your mails come from.

---

### Post by sx460 on 2005-08-25
I'd like to get in on this band wagon but not too sure how. Do I just need to install Ubuntu64 and then use synaptic? Is there a URL to paste into synaptic? Also, do these packages run noticably faster in 64?

---

### Post by Tamir on 2005-08-25
> I like "uPackages" and "LuXIV". Of course, I'm leaning towards "LuXIV"  .

Any other ideas? I think we should collect some generally accepted names and do a poll on them to decide which name we're going to use .

Tamir, I'm not getting any emails from you/the project! Could you give me the e-mail address that you are sending the e-mails from? I want to add it in my address book to make sure Yahoo! doesn't sort it as bulk mail. What's the title of the e-mail?

Edit:
E-mail notifications from the Ubuntu Forums work fine, however. So, somehow I'm just not receiving mails from you...or the domain that your mails come from.


It could explain why you didn't get the mail from wiki! look, maybe yahoo/mail client thinks my messages are junk, and removing them. However, i will send you with another email.

> I'd like to get in on this band wagon but not too sure how. Do I just need to install Ubuntu64 and then use synaptic? Is there a URL to paste into synaptic? Also, do these packages run noticably faster in 64?

Just install ubuntu64, and add our repositories to the file /etc/apt/sources.list, and you will see the packages on synaptic. if you need some help, post a topic, send me a message privately.

---

### Post by DancingSun on 2005-08-25
[QUOTE=sx460]I'd like to get in on this band wagon but not too sure how. Do I just need to install Ubuntu64 and then use synaptic? Is there a URL to paste into synaptic? Also, do these packages run noticably faster in 64?[/QUOTE]
Consult amd64.ubuntuguide.org on how to add additional repositories to apt/Synaptic.  To add this project's repository, just paste the repository's URL on the first post into the "/etc/apt/sources.list" file.

The AMD64 packages DOES NOT run noticably faster than their 32-bit counterparts, at least not yet.

---

### Post by Tamir on 2005-08-26
[QUOTE=DancingSun]Consult amd64.ubuntuguide.org on how to add additional repositories to apt/Synaptic.  To add this project's repository, just paste the repository's URL on the first post into the "/etc/apt/sources.list" file.

The AMD64 packages DOES NOT run noticably faster than their 32-bit counterparts, at least not yet.[/QUOTE]
 Another name: Ubuntu 64 Packages, elegant.
 And another : Ubuntu 64 Backports.

"u64p", "u64b".

---

### Post by Kuolio on 2005-08-26
Why not set up a poll about the name, with the names suggested here..?

---

### Post by ianikeev on 2005-08-26
[QUOTE=Tamir]hi,

As amd64 user, I know there is not good support of many packages.
So I want to improve it. just tell me which packages you need, I will try to deb it.

all of the debs I will make will be hosted here (thanks to [smoon](http://ubuntuforums.org/member.php?userid=15862) that hosted me):
```

## amd64 users repository
deb http://tamir.nooms.de/ubuntu/ hoary main universe multiverse restricted

## CVS snapshots packages
deb http://tamir.nooms.de/ubuntu/ cvs main universe multiverse restricted

## amd64 packages testers repository
deb http://tamir.nooms.de/ubuntu/ tests main universe multiverse restricted

```
Website (wiki): [http://tamir.nooms.de/wiki/](http://tamir.nooms.de/wiki/)

The following packages already built:
[list]
[*]the whole [ Enlightement 0.17](http://ubuntuforums.org/showthread.php?t=48616) from CVS  (+evidence)
[*]sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
[*]sun-j2sdk1.5 - Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)
[*]blackdown-j2sdk1.4 - Java(TM) 2 SDK, Standard Edition, Blackdown
[*]blackdown-j2re1.4 - Java(TM) 2 RE, Standard Edition, Blackdown
[*]gnomebaker 0.4
[*]freeciv 2.0.3 (thanks to filterban that made it) 
[*]gdesklets 0.35.2
[*]splashy (on tests)
[*]smeg 0.7.5
[*]python-xdg 0.14
[*]gaim 1.4.0 (made by [mo42](http://ubuntuforums.org/member.php?u=22260))
[*]gkrellm
[*]gkrellm-common
[*]gkrellmd
[*]rubygems
[*]inkscape
[*]libgc1c2 
[*]libgc-dev
[*]sensors-applet (made by Corbelius)
[/list]
NX (made by Drain):
[list]
[*]freeNX
[*]libnxcomp0
[*]libnxcomptext0
[*]nxagent
[*]nxdesktop
[*]nxlibs
[*]nxproxy
[*]nxviewer
[/list]
Ruby (1.8.2-9):
[list]
[*]irb1.8
[*]libdbm-ruby1.8
[*]libgdbm-ruby1.8
[*]libopenssl-ruby1.8
[*]libreadline-ruby1.8
[*]libruby1.8-dbg
[*]libruby1.8
[*]libtcltk-ruby1.8
[*]rdoc1.8
[*]ri1.8
[*]ruby1.8-dev
[*]ruby1.8-elisp
[*]ruby1.8-examples
[*]ruby1.8
[/list]
Linux Kernel with ubuntu patches (on tests repository):
[list]
[*]kernel-image-2.6.12-amd64-k8 (2.6.12-4.4)
[*]kernel-headers-2.6.12-amd64-k8 (2.6.12-4.4)
[/list]
Esound Packages:
[list]
[*]esound
[*]esound-clients
[*]esound-common
[*]libesd0
[*]libesd0-dev
[*]libesd-alsa0
[/list]
Firefox:
[list]
[*]firefox 1.0.5 
[*]firefox-dev 1.0.5
[*]firefox-dom-inspector 1.0.5
[*]firefox-gnome-support 1.0.5
[*]mozilla-firefox-dev 1.0.5
[/list]
Firefox deer park (Unstable!!! Backup your data. not ready to use):
[list]
[*]mozilla-firefox (1.0.99+deerpark-alpha2-1) 
[*]mozilla-firefox-dom-inspector (1.0.99+deerpark-alpha2-1) 
[*]mozilla-firefox-gnome-support (1.0.99+deerpark-alpha2-1) 
[/list]
KDE 3.4.1:
[list]
[*]arts (arts, libartsc0, libarts1-dev, libartsc0-dev, libarts1)
[*]kdeaccessibility (kdeaccessibility, kmag, kmousetool, kmouth)
[/list]
Todo List:
[list]
[*]acroread
[*]xmame/xmess 0.97
[*]koffice
[*](currently not updated, I have too packages to build)
[/list]
**Denied Packages:**
[list]
[*]_wine_ - Currently there is not way to build it on amd64
[*]_skype (I will try to)_ - Currently there is not way to build it
[*]_openoffice 2 Beta_ - Currently there is not way to build it on amd64
[/list]
_**Testers:**_
[list]
[*]DancingSun
[*]eolo999
[*]jensyt
[*]jon_gunnar
[/list]
Need testers!

_**How to send me your packages?**_
a. [Make a .deb](http://ubuntuforums.org/showthread.php?t=51003) of the package you want
b. Send to [EMAIL=tamir@nooms.de]my Email[/EMAIL] the files (.dsc, .diff, .orig.tar.gz, .deb)
c. I will contact you on email

**Please send me only [Debian standards](http://www.debian.org/doc/maint-guide/)  packages**  

Please report about bugs, problems, corrections on my Email:
**tamir@nooms.de** 

thanks.[/QUOTE]
 Oh well, it would be nice to have a fully functional and up-to-date Mono....

--
Igor

---

### Post by Tamir on 2005-08-26
[QUOTE=Kuolio]Why not set up a poll about the name, with the names suggested here..?[/QUOTE]
 because, We don't have enought names yet :)

---

### Post by Corbelius on 2005-08-26
I like Ubuntu Pure64 or uPure64 :D 2 options for the poll :D

---

### Post by DancingSun on 2005-08-26
So, we have the following suggested names for our project:
[list]
[*]Lexiv
[*]LuXIV
[*]Pure64
[*]u64p
[*]u64b
[*]uPackages
[*]uPure64
[/list] 
I'm adding "uPac64", for "Ubuntu Packages 64".

---

### Post by Tamir on 2005-08-26
[QUOTE=DancingSun]So, we have the following suggested names for our project:
[list]
[*]Lexiv
[*]LuXIV
[*]Pure64
[*]u64p
[*]u64b
[*]uPackages
[*]uPure64
[/list] 
I'm adding "uPac64", for "Ubuntu Packages 64".[/QUOTE]
 no u64b, call it Ubuntu 64 Backports.

---

### Post by DancingSun on 2005-08-26
Ok, updated list:
[list]
[*]Lexiv
[*]LuXIV
[*]Pure64
[*]u64p
[*]Ubuntu 64 Backports
[*]uPac64
[*]uPackages
[*]uPure64
[/list]

---

### Post by liquidfire on 2005-08-26
Could somebody compile libdvd2 for the AMD64 users?

---

### Post by DancingSun on 2005-08-26
[QUOTE=liquidfire]Could somebody compile libdvd2 for the AMD64 users?[/QUOTE]
Did you mean libdvdcss2 instead?

---

### Post by ROUBOS on 2005-08-26
Anyone got libdvdcss2 ??? 
I can't install it. I've been told it's not available in AMD64 and to request here....

Also, I've installed enlightenment and don't know how to make it available.
I did "sudo apt-get install enlightenment"
now what?

---

### Post by Tamir on 2005-08-26
[QUOTE=ROUBOS]Anyone got libdvdcss2 ??? 
I can't install it. I've been told it's not available in AMD64 and to request here....

Also, I've installed enlightenment and don't know how to make it available.
I did "sudo apt-get install enlightenment"
now what?[/QUOTE]
 Now i know why you didn't have the session, you didn't install many libs!
work with my guide: [http://ubuntuforums.org/showthread.php?t=48616](http://ubuntuforums.org/showthread.php?t=48616)
and install edb1 by:

```
apt-get install libedb1 libedb1-dev
```

:)

---

### Post by ROUBOS on 2005-08-26
create the file??? 
gedit /etc/apt/preferences

no extension on the file???

and just copy the code into it?

---

### Post by Tamir on 2005-08-26
[QUOTE=ROUBOS]create the file??? 
gedit /etc/apt/preferences

no extension on the file???

and just copy the code into it?[/QUOTE]
 Yes. but try to not ask questions here, ask them on the guide.

---

### Post by nwillis on 2005-08-26
[QUOTE=DancingSun]Ok, updated list:
[list]
[*]Lexiv
[*]LuXIV
[*]Pure64
[*]u64p
[*]Ubuntu 64 Backports
[*]uPac64
[*]uPackages
[*]uPure64
[/list][/QUOTE]

As the guy who suggested ubercoolword lexiv, I view luxiv as a refinement of it, so I say it takes its place, and lexiv should be cut from the ballot.

Also I intentionally spelled both in all lowercase in that last paragraph, just to see how they looked.  My personal pref is aversion to funky capitalization -- it always looks contrived and goofy, plus if the name or acronym *really* catches on, people will eventually stop adhering to it -- case in point Dixv, ipod, even ubuntu.

nAtE

---

### Post by Corbelius on 2005-08-26
[QUOTE=DancingSun]Did you mean libdvdcss2 instead?[/QUOTE]

Add this to ur sources.list and install libdvdcss: 

```
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

---

### Post by liquidfire on 2005-08-26
Thanks, :)


Are the amd64 servers down? I'm getting alot of 404 errors.

---

### Post by Tamir on 2005-08-27
[QUOTE=liquidfire]Thanks, :)


Are the amd64 servers down? I'm getting alot of 404 errors.[/QUOTE]
 That suck, I can't manage my repository on this windows system. ok, I should get my computer tommorow, we'll see.

---

### Post by DancingSun on 2005-08-27
[QUOTE=Tamir]That suck, I can't manage my repository on this windows system. ok, I should get my computer tommorow, we'll see.[/QUOTE]
It's probably the Marillat repository, Tamir.  I don't don't have any problems refreshing the repositories.

---

### Post by liquidfire on 2005-08-27
[QUOTE=][/QUOTE]
 Could VLC be made available?
I can't install it trough normal methods :/

> 
  vlc: Depends: dbus-1 (>= 0.23.4) but it is not installable
       Depends: libflac6 but it is not installable
       Depends: libhal0 (>= 0.4.0) but it is not installable
       Depends: libmodplug0 (>= 1:0.7-1) but it is not installable
       Depends: wxvlc but it is not going to be installed


---

### Post by DancingSun on 2005-08-27
[QUOTE=liquidfire]Could VLC be made available?
I can't install it trough normal methods :/[/QUOTE]
That's odd, I installed VLC via Synaptic just fine...

Just for reference, the following is my sources.list file.  I took out Tamir's testing repository as you probably don't need that.  If you have Marillat's repository entered, take it out, as that might cause some dependency problems by upgrading some important system package and thus breaking all the existing Ubuntu packages, for example: libc6.
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Tamir's AMD64 repo
deb http://tamir.nooms.de/ubuntu/ hoary main universe multiverse restricted
```

---

### Post by Tamir on 2005-08-28
I have got my computer back!! yoohooo.

---

### Post by Tamir on 2005-08-28
[QUOTE=Tamir]I have got my computer back!! yoohooo.[/QUOTE]
 New packages:
[list]
[*]gaim 1.5.0
[*]quick-lounge-applet
[*]gnomeradio
[*]goobox
[*]netspeed
[*]libdvdcss2
[/list]

---

### Post by DancingSun on 2005-08-28
[QUOTE=Tamir]I have got my computer back!! yoohooo.[/QUOTE]
Finally!!!  :grin:

---

### Post by appleman77 on 2005-08-29
Is anyone having issues running Kompose on AMD64?  I keep getting a SIGSEGV error 
```

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)...
[Thread debugging using libthread_db enabled]
[New Thread 182952065456 (LWP 8707)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#3  0x0000002a956afecb in __imlib_amd64_copy_rgb_to_rgba ()
   from /usr/lib/libImlib2.so.1
#4  0x0000002a9568529f in __imlib_BlendRGBAToData ()
   from /usr/lib/libImlib2.so.1
#5  0x0000002a95685c11 in __imlib_BlendImageToImage ()
   from /usr/lib/libImlib2.so.1
#6  0x0000002a9567bfac in imlib_create_cropped_scaled_image ()
   from /usr/lib/libImlib2.so.1
#7  0x000000000041f311 in QMemArray<char>::detach ()
#8  0x000000000041f1f4 in QMemArray<char>::detach ()
#9  0x0000000000412dd2 in QWidget::setWFlags ()
#10 0x0000000000412cbd in QWidget::setWFlags ()
#11 0x0000000000412b6e in QWidget::setWFlags ()
#12 0x0000002a96dfbc5e in QWidget::event () from /usr/lib/libqt-mt.so.3
#13 0x0000002a96d7d392 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#14 0x0000002a96d7cc4c in QApplication::notify () from /usr/lib/libqt-mt.so.3
#15 0x0000002a960069e5 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#16 0x0000002a96d4fb97 in QWidget::internalSetGeometry ()
   from /usr/lib/libqt-mt.so.3
#17 0x0000002a96dfa7d0 in QWidget::setGeometry () from /usr/lib/libqt-mt.so.3
#18 0x000000000041355f in QWidget::setWFlags ()
#19 0x0000000000415a88 in QWidget::setWFlags ()
#20 0x0000000000415660 in QWidget::setWFlags ()
#21 0x0000002a96dfbc5e in QWidget::event () from /usr/lib/libqt-mt.so.3
#22 0x0000002a96d7d392 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#23 0x0000002a96d7cc4c in QApplication::notify () from /usr/lib/libqt-mt.so.3
#24 0x0000002a960069e5 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#25 0x0000002a96d4fb97 in QWidget::internalSetGeometry ()
   from /usr/lib/libqt-mt.so.3
#26 0x0000002a96dfa7d0 in QWidget::setGeometry () from /usr/lib/libqt-mt.so.3
#27 0x0000000000412563 in QWidget::setGeometry ()
#28 0x0000000000415a88 in QWidget::setWFlags ()
#29 0x00000000004157d7 in QWidget::setWFlags ()
#30 0x0000002a96dfbc5e in QWidget::event () from /usr/lib/libqt-mt.so.3
#31 0x0000002a96d7d392 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#32 0x0000002a96d7cc4c in QApplication::notify () from /usr/lib/libqt-mt.so.3
#33 0x0000002a960069e5 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#34 0x0000002a96d2312a in QETWidget::translateConfigEvent ()
   from /usr/lib/libqt-mt.so.3
#35 0x0000002a96d1ed43 in QApplication::x11ProcessEvent ()
   from /usr/lib/libqt-mt.so.3
#36 0x0000002a96d32585 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#37 0x0000002a96d8cae4 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#38 0x0000002a96d8c9b2 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#39 0x0000002a96d7d535 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#40 0x000000000040fa41 in ?? ()
#41 0x0000002a981973c1 in __libc_start_main () from /lib/libc.so.6
#42 0x000000000040f86a in ?? ()
#43 0x0000007fbffffa28 in ?? ()
#44 0x0000000000000000 in ?? ()
#45 0x0000000000000001 in ?? ()
#46 0x0000007fbffffc36 in ?? ()
#47 0x0000000000000000 in ?? ()
#48 0x0000007fbffffc3e in ?? ()
#49 0x0000007fbffffc51 in ?? ()
#50 0x0000007fbffffc6c in ?? ()
#51 0x0000007fbffffc9e in ?? ()
#52 0x0000007fbffffcae in ?? ()
#53 0x0000007fbffffcfa in ?? ()
#54 0x0000007fbffffd17 in ?? ()
#55 0x0000007fbffffd2d in ?? ()
#56 0x0000007fbffffd3b in ?? ()
#57 0x0000007fbffffd68 in ?? ()
#58 0x0000007fbffffdc2 in ?? ()
#59 0x0000007fbffffdd6 in ?? ()
#60 0x0000007fbffffde9 in ?? ()
#61 0x0000007fbffffdfa in ?? ()
#62 0x0000007fbffffe0e in ?? ()
#63 0x0000007fbffffe16 in ?? ()
#64 0x0000007fbffffe22 in ?? ()
#65 0x0000007fbffffe33 in ?? ()
#66 0x0000007fbffffe6f in ?? ()
#67 0x0000007fbffffe7c in ?? ()
#68 0x0000007fbffffe8f in ?? ()
#69 0x0000007fbffffea3 in ?? ()
#70 0x0000007fbffffeb9 in ?? ()
#71 0x0000007fbfffff12 in ?? ()
#72 0x0000007fbfffff74 in ?? ()
#73 0x0000000000000000 in ?? ()
#74 0x0000000000000000 in ?? ()
#75 0x0000000000000010 in ?? ()
#76 0x00000000078bfbff in ?? ()
#77 0x0000000000000006 in ?? ()
#78 0x0000000000001000 in ?? ()
#79 0x0000000000000011 in ?? ()
#80 0x0000000000000064 in ?? ()
#81 0x0000000000000003 in ?? ()
#82 0x0000000000400040 in ?? ()
#83 0x0000000000000004 in ?? ()
#84 0x0000000000000038 in ?? ()
#85 0x0000000000000005 in ?? ()
#86 0x0000000000000008 in ?? ()
#87 0x0000000000000007 in ?? ()
#88 0x0000002a95556000 in ?? ()
#89 0x0000000000000008 in ?? ()
#90 0x0000000000000000 in ?? ()
#91 0x0000000000000009 in ?? ()
#92 0x000000000040f840 in ?? ()
#93 0x000000000000000b in ?? ()
#94 0x00000000000003e8 in ?? ()
#95 0x000000000000000c in ?? ()
#96 0x00000000000003e8 in ?? ()
#97 0x000000000000000d in ?? ()
#98 0x00000000000003e8 in ?? ()
#99 0x000000000000000e in ?? ()
#100 0x00000000000003e8 in ?? ()
#101 0x0000000000000017 in ?? ()
#102 0x0000000000000000 in ?? ()
#103 0x000000000000000f in ?? ()
#104 0x0000007fbffffc2f in ?? ()
#105 0x0000000000000000 in ?? ()
#106 0x0000000000000000 in ?? ()
#107 0x0000000000000000 in ?? ()
#108 0x7800000000000000 in ?? ()
#109 0x6f6b0034365f3638 in ?? ()
#110 0x53530065736f706d in ?? ()
#111 0x5f544e4547415f48 in ?? ()
#112 0x323739373d444950 in ?? ()
#113 0x544e4f435f4d4400 in ?? ()
#114 0x7261762f3d4c4f52 in ?? ()
#115 0x6d64782f6e75722f in ?? ()
#116 0x5f475047006c7463 in ?? ()
#117 0x4e495f544e454741 in ?? ()
#118 0x2f706d742f3d4f46 in ?? ()
#119 0x544b67522d677067 in ?? ()
#120 0x6770672e532f7675 in ?? ()
#121 0x373a746e6567612d in ?? ()
#122 0x485300313a393639 in ?? ()
#123 0x6e69622f3d4c4c45 in ?? ()
#124 0x445800687361622f in ?? ()
#125 0x4547414e414d5f4d in ?? ()
#126 0x722f7261762f3d44 in ?? ()
#127 0x74636d64782f6e75 in ?? ()
#128 0x6c74636d64782f6c in ?? ()
#129 0x7379616d2c303a2d in ?? ()
#130 0x2c6e6679616d2c64 in ?? ()
#131 0x73722c6465686373 in ?? ()
#132 0x6f6874656d2c6476 in ?? ()
#133 0x697373616c633d64 in ?? ()
#134 0x42494c5f53470063 in ?? ()
#135 0x682f656d6f682f3d in ?? ()
#136 0x2f6f62676e617768 in ?? ()
#137 0x4b0073746e6f662e in ?? ()
#138 0x5f4c4c55465f4544 in ?? ()
#139 0x3d4e4f4953534553 in ?? ()
#140 0x4553550065757274 in ?? ()
#141 0x676e617768683d52 in ?? ()
#142 0x415f485353006f62 in ?? ()
#143 0x4b434f535f485455 in ?? ()
#144 0x73732f706d742f3d in ?? ()
#145 0x4f5251677a662d68 in ?? ()
#146 0x6567612f39313937 in ?? ()
#147 0x00393139372e746e in ?? ()
#148 0x73752f3d48544150 in ?? ()
#149 0x2f6c61636f6c2f72 in ?? ()
#150 0x73752f3a6e696273 in ?? ()
#151 0x2f6c61636f6c2f72 in ?? ()
#152 0x7273752f3a6e6962 in ?? ()
#153 0x752f3a6e6962732f in ?? ()
#154 0x2f3a6e69622f7273 in ?? ()
#155 0x69622f3a6e696273 in ?? ()
#156 0x622f7273752f3a6e in ?? ()
#157 0x2f3a3131582f6e69 in ?? ()
#158 0x656d61672f727375 in ?? ()
#159 0x4f544b5345440073 in ?? ()
#160 0x4f49535345535f50 in ?? ()
#161 0x57500065646b3d4e in ?? ()
#162 0x2f656d6f682f3d44 in ?? ()
#163 0x6f62676e61776868 in ?? ()
#164 0x6e653d474e414c00 in ?? ()
#165 0x2d4654552e53555f in ?? ()
#166 0x2f3d454d4f480038 in ?? ()
#167 0x7768682f656d6f68 in ?? ()
#168 0x4853006f62676e61 in ?? ()
#169 0x414c00313d4c564c in ?? ()
#170 0x653d45474155474e in ?? ()
#171 0x4d414e474f4c006e in ?? ()
#172 0x676e617768683d45 in ?? ()
#173 0x5f53554244006f62 in ?? ()
#174 0x5f4e4f4953534553 in ?? ()
#175 0x524444415f535542 in ?? ()
#176 0x78696e753d535345 in ?? ()
#177 0x636172747362613a in ?? ()
#178 0x642f706d742f3d74 in ?? ()
#179 0x555176432d737562 in ?? ()
#180 0x440055484a364c53 in ?? ()
#181 0x3a3d59414c505349 in ?? ()
#182 0x752f3d5f00302e30 in ?? ()
#183 0x6b2f6e69622f7273 in ?? ()
#184 0x4b0074696e696564 in ?? ()
#185 0x49544c554d5f4544 in ?? ()
#186 0x6c61663d44414548 in ?? ()
#187 0x5352554358006573 in ?? ()
#188 0x454d4548545f524f in ?? ()
#189 0x746c75616665643d in ?? ()
#190 0x5f43525f4b544700 in ?? ()
#191 0x652f3d53454c4946 in ?? ()
#192 0x672f6b74672f6374 in ?? ()
#193 0x6f682f3a63726b74 in ?? ()
#194 0x6e617768682f656d in ?? ()
#195 0x6b74672e2f6f6267 in ?? ()
#196 0x656d6f682f3a6372 in ?? ()
#197 0x62676e617768682f in ?? ()
#198 0x732f65646b2e2f6f in ?? ()
#199 0x6e6f632f65726168 in ?? ()
#200 0x726b74672f676966 in ?? ()
#201 0x525f324b54470063 in ?? ()
#202 0x3d53454c49465f43 in ?? ()
#203 0x6b74672f6374652f in ?? ()
#204 0x6b74672f302e322d in ?? ()
#205 0x656d6f682f3a6372 in ?? ()
#206 0x62676e617768682f in ?? ()
#207 0x63726b74672e2f6f in ?? ()
#208 0x6f682f3a302e322d in ?? ()
#209 0x6e617768682f656d in ?? ()
#210 0x65646b2e2f6f6267 in ?? ()
#211 0x632f65726168732f in ?? ()
#212 0x74672f6769666e6f in ?? ()
#213 0x535345530063726b in ?? ()
#214 0x414e414d5f4e4f49 in ?? ()
#215 0x61636f6c3d524547 in ?? ()
#216 0x4248434e554c2f6c in ?? ()
#217 0x2f706d742f3a584f in ?? ()
#218 0x696e752d4543492e in ?? ()
#219 0x4400343230382f78 in ?? ()
#220 0x535f504f544b5345 in ?? ()
#221 0x495f505554524154 in ?? ()
#222 0x4248434e554c3d44 in ?? ()
#223 0x32353231313b584f in ?? ()
#224 0x37363b3330383239 in ?? ()
#225 0x3230383b30393437 in ?? ()
#226 0x3831454d49545f39 in ?? ()
#227 0x2f00343536393730 in ?? ()
#228 0x2f6e69622f727375 in ?? ()
#229 0x0065736f706d6f6b in ?? ()
#230 0x0000000000000000 in ?? ()

```

It's ugly!

---

### Post by DancingSun on 2005-08-29
[QUOTE=appleman77]Is anyone having issues running Kompose on AMD64?  I keep getting a SIGSEGV error[/QUOTE]
Please start a new thread for this.  And use the CODE tags (the "#" button) for the error output, that way it will not make the post so long.

---

### Post by Tamir on 2005-08-29
[QUOTE=DancingSun]Please start a new thread for this.  And use the CODE tags (the "#" button) for the error output, that way it will not make the post so long.[/QUOTE]
 and edit the message here, so we don't have to see it :)

---

### Post by ROUBOS on 2005-08-29
How about NVU??? To do some web development.
Has anyone asked for it already?

---

### Post by Corbelius on 2005-08-29
[QUOTE=ROUBOS]How about NVU??? To do some web development.
Has anyone asked for it already?[/QUOTE]

I made Bluefish 1.0.2, I task am better than NVU ;)

---

### Post by DancingSun on 2005-08-29
Bluefish and Nvu are on the official repositories (Ubuntu, and backports respectively) for AMD64.  Might not be the latest versions (I didn't check) but it's there.

---

### Post by ROUBOS on 2005-08-29
You are right. Bluefish is very nice.
I installed version 1.0 from Synaptic. But could not find NVU.

---

### Post by DancingSun on 2005-08-29
[QUOTE=ROUBOS]You are right. Bluefish is very nice.
I installed version 1.0 from Synaptic. But could not find NVU.[/QUOTE]
You probably don't have the official backports repository in your sources.list:
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

---

### Post by ROUBOS on 2005-08-30
you're right. getting it now thanks :)

EDIT>>> I installed it. Refreshed the GnomePanel, I even loged out and in again, and when I select NVU from the gnome panel, it does not start. Why?

---

### Post by Corbelius on 2005-08-30
[QUOTE=ROUBOS]you're right. getting it now thanks :)

EDIT>>> I installed it. Refreshed the GnomePanel, I even loged out and in again, and when I select NVU from the gnome panel, it does not start. Why?[/QUOTE]

Also for me, segmentation fault, i think NVU is not good for amd64 system :/

---

### Post by ROUBOS on 2005-08-30
Battle for Wesnoth is not working since it updated.
I click on it and nothing happens. Just like NVU

 :neutral:

---

### Post by DancingSun on 2005-08-30
[QUOTE=Corbelius]Also for me, segmentation fault, i think NVU is not good for amd64 system :/[/QUOTE]
Heh, apparently Wesnoth and Nvu are both from the "Official Backports" repository, and it sounds like they didn't test it...I guess unlike us, they don't have AMD64 testers :)

The segmentation fault is related to mozilla, it seems.

In anycase, if you find AMD64 packages from the Official Backports that are not working please report it to the backports forums.

---

### Post by DancingSun on 2005-08-30
Reminder to packagers: please fix the FreeNX package, I really want to try it on GNOME! I've been itching see it in action since the package was ported...

---

### Post by ROUBOS on 2005-08-30
Battle for Wesnoth was working for me before. On my AMD64 system.
Since an upgrade it has stoped working
 :-|

---

### Post by DancingSun on 2005-08-30
[QUOTE=ROUBOS]Battle for Wesnoth was working for me before. On my AMD64 system.
Since an upgrade it has stoped working
 :-|[/QUOTE]
Yes, the new version is only up on the backports repository.  You can check this by viewing the property of the package in Synaptic.  There should be a tab titled "Versions" or something to that effect.  You'll see that the older version is part of the "hoary" repository, which is a core repository that "should" be tested by the Ubuntu Team.

---

### Post by ROUBOS on 2005-08-31
OK, so how do I go about uninstalling NVU and Wesnoth, then installing the tested version?

---

### Post by stoeptegel on 2005-08-31
a package for rtorrent is that requestable?  :)

---

### Post by DancingSun on 2005-08-31
[QUOTE=ROUBOS]OK, so how do I go about uninstalling NVU and Wesnoth, then installing the tested version?[/QUOTE]
In Synaptic:

To install a different version, click and select the package.  Go to the menu Package --> Force Version, and choose the lower version.

To uninstall, right-click on a package and, well, choose remove.

---

### Post by Angel666 on 2005-09-01
If someone could package emelfm2, I would be most appreciative.
[http://emelfm2.org/](http://emelfm2.org/)

---

### Post by DancingSun on 2005-09-01
Wiki is updated with the new requests.

---

### Post by Tamir on 2005-09-01
[QUOTE=DancingSun]Wiki is updated with the new requests.[/QUOTE]
 OK, I think i solved the problem with freenx 0.4.2. I uploaded it, do a reinstall (don't forget to apt-get update)

---

### Post by DancingSun on 2005-09-01
[QUOTE=Tamir]OK, I think i solved the problem with freenx 0.4.2. I uploaded it, do a reinstall (don't forget to apt-get update)[/QUOTE]
Good news, and bad news.

The good, the installation works now.

The bad, I still can't see the gnome desktop.  Same problem as with using 0.4.3.  Get a big "M", then black screen.
A sample if my error log from the .nx directory on Windows2K:
```
Loop: WARNING! Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.

```

---

### Post by Tamir on 2005-09-02
[QUOTE=DancingSun]Good news, and bad news.

The good, the installation works now.

The bad, I still can't see the gnome desktop.  Same problem as with using 0.4.3.  Get a big "M", then black screen.
A sample if my error log from the .nx directory on Windows2K:
```
Loop: WARNING! Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.
handleUnpack: PANIC! Unsupported source coordinates in unpack request.
handleImage: PANIC! Sending X_NoOperation for FD#11 to recover from failed unpack.

```[/QUOTE]
 I guess I don't know what version it needs. check it, then tell what package to create.

---

### Post by smoon on 2005-09-02
Hey guys!

I just checked the wiki out of boredom and saw that you created a package of libdvdcss2. I'm not exactly sure if it is legal to host packages of this library in germany  where the server is located. I can't remember exactly but there was something about libdvdcss being prohibited to use and/or distribute in germany. Maybe there's a difference between libdvdcss and libdvdcss2?

Please, could you check this out and remove the package if necessary? I'm the owner of the server that is hosting tamir.nooms.de and would like to avoid any trouble.

Thanks in advance,
smoon

---

### Post by xodeus on 2005-09-02
[QUOTE=Angel666]If someone could package emelfm2, I would be most appreciative.
[http://emelfm2.org/](http://emelfm2.org/)[/QUOTE]

I've built the package now and it seems to be working.
Send me an PM with your email and I will mail it to you.

---

### Post by Tamir on 2005-09-02
[list]
[*]emelfm2
[/list]
uploaded :).

---

### Post by smoon on 2005-09-02
[QUOTE=smoon]Hey guys!

I just checked the wiki out of boredom and saw that you created a package of libdvdcss2. I'm not exactly sure if it is legal to host packages of this library in germany  where the server is located. I can't remember exactly but there was something about libdvdcss being prohibited to use and/or distribute in germany. Maybe there's a difference between libdvdcss and libdvdcss2?

Please, could you check this out and remove the package if necessary? I'm the owner of the server that is hosting tamir.nooms.de and would like to avoid any trouble.

Thanks in advance,
smoon[/QUOTE]

Ok, if nobody will take care of this within the next three hours I'll remove the package from the repository. Sorry, guys, but I don't want to get sued...

---

### Post by hod139 on 2005-09-02
[QUOTE=smoon]Ok, if nobody will take care of this within the next three hours I'll remove the package from the repository. Sorry, guys, but I don't want to get sued...[/QUOTE]

All I know is that PackMan.de (which used to provide an rpm) had this to say about libdvdcss:
> Now, the new copyright in germany is coming into force, it's no longer allowed to provide tools to breake technical protections.

Therefore we can no longer provide libdvdcss, sorry.

---

### Post by DancingSun on 2005-09-02
[QUOTE=hod139]All I know is that PackMan.de (which used to provide an rpm) had this to say about libdvdcss:[/QUOTE]
Yes, looks like it's safer to remove the libdvdcss2 package. :(  :mad:

---

### Post by DancingSun on 2005-09-02
Hmm....however, libdvdcss2 is in the backports though (although not for AMD64):
[https://wiki.ubuntu.com/RestrictedFormats#head-2bb84d8aa273e8fa93be00ad25ec3c8b7fb83dbd](https://wiki.ubuntu.com/RestrictedFormats#head-2bb84d8aa273e8fa93be00ad25ec3c8b7fb83dbd)

And as some have pointed out, there's a installer script installed in Ubuntu anyway...is it possible to setup a package in the repository that executes that script?

---

### Post by smoon on 2005-09-02
Ok, thanks for the research. I'll remove the package now. I'm really sorry about that, but I think you can understand that I don't want to get into any trouble.

---

### Post by DancingSun on 2005-09-03
[QUOTE=Tamir]I guess I don't know what version it needs. check it, then tell what package to create.[/QUOTE]
Is there a version 1.5 for nxproxy?  I found a warning message in on of the logs that says I'm using nxproxy 1.4 with nxclient 1.5...and since nomachines only offer 1.5 for download I can't do anything about the client part...

---

### Post by DancingSun on 2005-09-03
Hmm....I noticed that we have a bunch of other nx packages...but those are not part of freenx's dependencies.  Am I suppose to install those as well?

Edit: nxproxy was one of the packages that was not part of freenx depencies...and I didn't install it...which makes the warning message that I got about nxproxy 1.4 really weird...

---

### Post by xodeus on 2005-09-03
[QUOTE=smoon]Ok, thanks for the research. I'll remove the package now. I'm really sorry about that, but I think you can understand that I don't want to get into any trouble.[/QUOTE]
 I can mayeb host it for you for free, just the deb for download if you wish. :D

---

### Post by theICEBear.dk on 2005-09-03
Hey all, I am new to Ubuntu AMD64, but I want to first thank Tamir and the rest of you for providing additional packages great work. 

Secondly I would ask if anyone is interested in doing a compile of Valgrind 3.0.1 for AMD64, according to their website [http://www.valgrind.org](http://www.valgrind.org) the latest version is meant to work for us as well and I would very much like to analyze my code with it.

Regards all,
Mikael

---

### Post by xodeus on 2005-09-03
[QUOTE=theICEBear.dk]Hey all, I am new to Ubuntu AMD64, but I want to first thank Tamir and the rest of you for providing additional packages great work. 

Secondly I would ask if anyone is interested in doing a compile of Valgrind 3.0.1 for AMD64, according to their website [http://www.valgrind.org](http://www.valgrind.org) the latest version is meant to work for us as well and I would very much like to analyze my code with it.

Regards all,
Mikael[/QUOTE]
 I've now built the package.
I'll email tamir with it, and I hope he'll put it into tests. Then users and you can test it.
I have not tested it so I don't know if it works. So please test....

Håber at det vil virke.

---

### Post by tseliot on 2005-09-03
Excuse me I can't see java in Synaptic (and in the repos I presume).

Can you help me, please?

---

### Post by Angel666 on 2005-09-03
[QUOTE=xodeus]I've built the package now and it seems to be working.
Send me an PM with your email and I will mail it to you.[/QUOTE]

Looks like its already in the repo installed fine and looks great.  Thanks!

---

### Post by DancingSun on 2005-09-03
[QUOTE=tseliot]Excuse me I can't see java in Synaptic (and in the repos I presume).

Can you help me, please?[/QUOTE]
It's called j2sdk.

---

### Post by Corbelius on 2005-09-04
[QUOTE=tseliot]Excuse me I can't see java in Synaptic (and in the repos I presume).

Can you help me, please?[/QUOTE]

j2re for the plugin and machine, j2sdk for developement.

---

### Post by sander marechal on 2005-09-04
Can it be that the repository is not available? Or are the links on page 1 of this thread perhaps out-of-date? I just tried adding it to my sources.list but I get errors. I bought a brand-new PC yesterday and I'd really like to put a proper K8 kernel in, instead of the generic i386 kernel that Ubuntu installs by default.

---

### Post by xodeus on 2005-09-04
[QUOTE=Corbelius]j2re for the plugin and machine, j2sdk for developement.[/QUOTE]
 You have to mention that j2re for plugin for browsing must be blackdowns.
For further instructions please read this guide:
[http://tamir.nooms.de/wiki/doku.php?id=guides:java_on_hoary_amd64](http://tamir.nooms.de/wiki/doku.php?id=guides:java_on_hoary_amd64)

---

### Post by DancingSun on 2005-09-04
[QUOTE=Corbelius]j2re for the plugin and machine, j2sdk for developement.[/QUOTE]
Also, j2sdk can be used for regular java apps as well.  I'm using j2sdk right now.

It used to be that the SDK can only be used for software development, and the regular java apps are associated with the JRE.  But Sun changed this for 1.5.

---

### Post by DancingSun on 2005-09-04
[QUOTE=sander marechal]Can it be that the repository is not available? Or are the links on page 1 of this thread perhaps out-of-date? I just tried adding it to my sources.list but I get errors. I bought a brand-new PC yesterday and I'd really like to put a proper K8 kernel in, instead of the generic i386 kernel that Ubuntu installs by default.[/QUOTE]
It would be helpful if you include the description of the errors in a post.  The repository URI's should be fine, since most of us on this thread are using it without any errors.

---

### Post by rah on 2005-09-04
Why was libdvdcss2 removed?

---

### Post by DancingSun on 2005-09-04
[QUOTE=rah]Why was libdvdcss2 removed?[/QUOTE]
 Legal concerns.

---

### Post by rah on 2005-09-05
*sigh*

Okay, thanks.

---

### Post by sander marechal on 2005-09-05
[QUOTE=DancingSun]It would be helpful if you include the description of the errors in a post.  The repository URI's should be fine, since most of us on this thread are using it without any errors.[/QUOTE]

Yes, ofcourse. Here they are:

```

http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/hoary/universe/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/cvs/main/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/cvs/universe/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/cvs/multiverse/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/cvs/restricted/binary-i386/Packages.gz: 404 Not Found


```

---

### Post by Corbelius on 2005-09-05
> **rah]*sigh*

Okay, thanks.[/QUOTE]

Contact me on email and i'll send u  said:**
> Yes, ofcourse. Here they are:

```

http://tamir.nooms.de/ubuntu/dists/hoary/main/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/hoary/universe/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/cvs/main/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/cvs/universe/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/cvs/multiverse/binary-i386/Packages.gz: 404 Not Found
http://tamir.nooms.de/ubuntu/dists/cvs/restricted/binary-i386/Packages.gz: 404 Not Found


```

The Tamir repository is only for amd64 architecture.

---

### Post by sander marechal on 2005-09-05
[QUOTE=Corbelius]The Tamir repository is only for amd64 architecture.[/QUOTE]

I know :) I got a brand new AMD64 3500+ waiting for a proper kernel here. It's just that synaptic seems to 404 when trying to load those repositories.

EDIT: Ah, I see the problem now. I got this in my sources.list:

```

## AMD64 ports

deb http://tamir.nooms.de/ubuntu/ hoary main universe multiverse restricted

## CVS snapshots packages
deb http://tamir.nooms.de/ubuntu/ cvs main universe multiverse restricted

```

and synaptic seems to want to load i386 packages. So, how do I tell APT/Synaptic to look for AMD64 packages in that repository?

Small second question: Do I need the CVS repository as well? Or just the user repository?

Thanks!

---

### Post by DancingSun on 2005-09-05
[QUOTE=sander marechal]I know :) I got a brand new AMD64 3500+ waiting for a proper kernel here. It's just that synaptic seems to 404 when trying to load those repositories.

EDIT: Ah, I see the problem now. I got this in my sources.list:

```

## AMD64 ports

deb http://tamir.nooms.de/ubuntu/ hoary main universe multiverse restricted

## CVS snapshots packages
deb http://tamir.nooms.de/ubuntu/ cvs main universe multiverse restricted

```

and synaptic seems to want to load i386 packages. So, how do I tell APT/Synaptic to look for AMD64 packages in that repository?

Small second question: Do I need the CVS repository as well? Or just the user repository?

Thanks![/QUOTE]
You probably have the 32-but Ubuntu installed, instead of the 64-bit one...

---

### Post by sander marechal on 2005-09-05
[QUOTE=DancingSun]You probably have the 32-but Ubuntu installed, instead of the 64-bit one...[/QUOTE]

Yes. I just used the install CD that I used everywhere else. I didn't know you needed a different install CD for Ubuntu64. Oh, well. Downloading it now!

---

### Post by sander marechal on 2005-09-05
It's working now. Thanks!

---

### Post by tseliot on 2005-09-05
[QUOTE=Corbelius]j2re for the plugin and machine, j2sdk for developement.[/QUOTE]
Thanks

---

### Post by Kemotaha on 2005-09-06
I would like to request an updated version of freeciv.  2.0.5 is out. [http://www.freeciv.org/index.php/Freeciv](http://www.freeciv.org/index.php/Freeciv)

Thanks

---

### Post by markuman on 2005-09-07
hi

i'm now on 64bit and want to install inkscape.
but following message came:

```
inkscape: Hängt ab: libgc1c2 soll aber nicht installiert werde

```
inkscape needs libgc1c2, but that should not install.

but if i install it, it delete ubuntu-base package :-(

so any ideas?

---

### Post by Kuolio on 2005-09-07
Request:

Seems I'm always longing for multimediasupport-things.. and here we go again: gplflash or gplflash2! It would be cool to have even some-sort-of flashsupport, untill macromedia releases official 64bit flash.

---

### Post by xodeus on 2005-09-07
[QUOTE=Kuolio]Request:

Seems I'm always longing for multimediasupport-things.. and here we go again: gplflash or gplflash2! It would be cool to have even some-sort-of flashsupport, untill macromedia releases official 64bit flash.[/QUOTE]
 Try

```

sudo apt-get install libflash0 libflash-mozplugin

```
for gplflash

---

### Post by mlomker on 2005-09-08
[QUOTE=DancingSun]Legal concerns.[/QUOTE]

Could someone update the repository info files so that Synaptic doesn't keep trying to upgrade it when the file was deleted?  Thanks.

The files is elsewhere on the `net.  Try:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

---

### Post by cakey on 2005-09-08
Another vote for Transcode and nvidia 7676 here.  
 
Thanks alot!   :)

---

### Post by mlomker on 2005-09-08
I made the mistake of updating arts, libarts1, and libartsc0 from tamir's repository and now I'm in a pickle.  I can't install kdebase-dev because it wants exactly the older older versions of those files and I can't downgrade without removing pretty much all of KDE due to dependencies.

Were those files intended just for KDE 3.4.1?  What precipitated all of this is that I started getting sound-related errors on startup and trying to compile the latest Koffice resulted in some arts-related errors which I assumed were version issues.  I removed the DEV package and now I can't put it back on.

Any ideas?

---

### Post by DancingSun on 2005-09-08
[QUOTE=mlomker]I made the mistake of updating arts, libarts1, and libartsc0 from tamir's repository and now I'm in a pickle.  I can't install kdebase-dev because it wants exactly the older older versions of those files and I can't downgrade without removing pretty much all of KDE due to dependencies.

Were those files intended just for KDE 3.4.1?  What precipitated all of this is that I started getting sound-related errors on startup and trying to compile the latest Koffice resulted in some arts-related errors which I assumed were version issues.  I removed the DEV package and now I can't put it back on.

Any ideas?[/QUOTE]
Have you tried forcing to an older version (you can select this option in Synaptic under the "Package" menu)?  Or does it still want to uninstall stuff?

---

### Post by mlomker on 2005-09-08
[QUOTE=DancingSun]Have you tried forcing to an older version (you can select this option in Synaptic under the "Package" menu)?  Or does it still want to uninstall stuff?[/QUOTE]

Yeah, it wanted to remove pretty much all of KDE.  After spending a few hours researching things I realize that I could have tried **dpkg --force-downgrade** but I didn't find that command until after I'd whacked things.

On the plus side, I did find KDE 3.4.1 so I'm choosing to look at it as an "upgrade opportunity."   \\:D/

---

### Post by DancingSun on 2005-09-08
[QUOTE=markuman]hi

i'm now on 64bit and want to install inkscape.
but following message came:

```
inkscape: Hängt ab: libgc1c2 soll aber nicht installiert werde

```
inkscape needs libgc1c2, but that should not install.

but if i install it, it delete ubuntu-base package :-(

so any ideas?[/QUOTE]
Is it the Ubuntu-Desktop package?  If it's just uninstalling a dummy package then it should be okay.

---

### Post by xodeus on 2005-09-09
REQ:
As seen in this topic:
[http://ubuntuforums.org/showthread.php?t=63839](http://ubuntuforums.org/showthread.php?t=63839)
there is a new flash for amd64.
So It would be nice if anyone could compile it with mozilla plugin.
I don't have time untill next weekend so, it can't be me.

gplaflash2 is available through cvs, if anyone would compile for tests i will be glad too.
[http://gplflash.sourceforge.net/](http://gplflash.sourceforge.net/)

I know that this is much to ask for but why not try it. 
Many people miss flash when surfing, mee too.
I would like but as mentioned work work work and my girly always asks me, what is this, this doesn't work as windows and so on. then i have to explain that this is not windows. LOL.

---

### Post by thundertoad on 2005-09-11
Hi,

Was wondering if you could port p7zip to AMD64 or plain old 7zip... in fact anything that can compress and decompress files that are *.7z extensions.

Thanks
Th'undertoad

---

### Post by songochain on 2005-09-11
I'll install breezy and i want to know if it's possible to use this repository to install E17 (only) without any dependency problem.
Thanks

---

### Post by zarathustra on 2005-09-12
Is it possible to have the Gaim-dev package and/or the latest guifications? I've noticed that the dev package for Gaim is still the old one in the repositories.

---

### Post by Corbelius on 2005-09-12
[QUOTE=thundertoad]Hi,

Was wondering if you could port p7zip to AMD64 or plain old 7zip... in fact anything that can compress and decompress files that are *.7z extensions.

Thanks
Th'undertoad[/QUOTE]

Add it ;)

---

### Post by thundertoad on 2005-09-12
[QUOTE=Corbelius]Add it ;)[/QUOTE]
 Bonjourno
Um.. do you mean added? or are you telling someone to add it to the list of this yet to be ported? Corbelius... um sorry man I am not sure what you meant!

any help with porting p7zip or plain old 7zip would be much appreciated.
gratci

ciao
Th'undertoad

---

### Post by kumpf on 2005-09-12
Here are a couple packages I would like... :)

 - Adobe Acroread (restricted, i know.. but it would be nice)
 - OpenOffice2 (I see some open office 2 packages.. but needs openoffice.org2-core (>1.9.79.2) )

The 64-bit repository is awesome.. keep up the good work!

---

### Post by Corbelius on 2005-09-13
[QUOTE=thundertoad]Bonjourno
Um.. do you mean added? or are you telling someone to add it to the list of this yet to be ported? Corbelius... um sorry man I am not sure what you meant!

any help with porting p7zip or plain old 7zip would be much appreciated.
gratci

ciao
Th'undertoad[/QUOTE]

I'm the moderator of this project ;) [http://tamir.nooms.de/wiki/doku.php?id=about](http://tamir.nooms.de/wiki/doku.php?id=about)
Add your request in wishlist and i try to compile it ;) [http://tamir.nooms.de/wiki/doku.php?id=packages](http://tamir.nooms.de/wiki/doku.php?id=packages)

---

### Post by thundertoad on 2005-09-13
Ah, ok. I went to add P7zip but found someone had already added it... so I guess now I just have to wait till you guys get to it.

thanks for the links... and thanks for the great work you are doing.
Now I know where to go to ask for stuff.

ciao
Th'undertoad

---

### Post by Laerte Andrade on 2005-09-13
Hello, I'm in need of the **libc5** package compiled for AMD64. Unfortunately it is necessary for the data reduction software I'm using (IRAF).

Could someone help me? Thanks in advance.

---

### Post by jensyt on 2005-09-16
I have a small question about someone's request for a TeamSpeak 2 deb...

Are there any legal issues involved in repackaging TeamSpeak 2 that we should know about? I'm not sure if their license allows you to make a deb and redistribute their software.

Not only that, but they have a really easy-to-use installer on their website, so it shouldn't be too hard to just install it. I had no problems with it at all.

With all that said and done, I did make a deb for it if anyone wants it. I just would like to know if there are any legal issues with redistribution before submitting it to the repository or giving it to anyone.

I suppose I could look it up myself, but if nobody objects, I don't really care.

---

### Post by Corbelius on 2005-09-17
> **Laerte Andrade]Hello, I'm in need of the **libc5** package compiled for AMD64. Unfortunately it is necessary for the data reduction software I'm using (IRAF).

Could someone help me? Thanks in advance.[/QUOTE]

It's no possible, sorry  said:**
> I have a small question about someone's request for a TeamSpeak 2 deb...

Are there any legal issues involved in repackaging TeamSpeak 2 that we should know about? I'm not sure if their license allows you to make a deb and redistribute their software.

Not only that, but they have a really easy-to-use installer on their website, so it shouldn't be too hard to just install it. I had no problems with it at all.

With all that said and done, I did make a deb for it if anyone wants it. I just would like to know if there are any legal issues with redistribution before submitting it to the repository or giving it to anyone.

I suppose I could look it up myself, but if nobody objects, I don't really care.

It's true, teamspek has an installer very easy, and to create a .deb package is much difficult.

---

### Post by jensyt on 2005-09-17
Well, I have a deb finished. All I did was run the installer, dump all the files that were added by the installer into a false directory, add a symlink for /usr/bin/teamspeak2, and then manually create the deb.

It might not be the right way, but it works just as good as the installer, if not better. It makes you a symlink so you can simply run the "teamspeak2" command without having to go to /usr/share/teamspeak2/TeamSpeak. It also lets you easily uninstall the whole thing... (there is also an uninstall script from TeamSpeak in the directory with the binary.)

Like I said, it might not be standardized for debian, but then again, the installer isn't either. :)

EDIT: I just noticed that teamspeak is no longer on the list of requests, so I guess that means it isn't needed for the repo...

---

### Post by etitor on 2005-09-17
Tamir:

I think Gedit is a less than useful text editor (regexp missing).

I tried to compile winefish on my AMD64, and configure, make and make install went OK. Nevertheless, when trying to run winefish a segment violation is all I get, sometimes accompanied by the splash image.

Do you think you could add winefish?

---

### Post by Parkotron on 2005-09-17
Hello,

I'd like to see a .deb for Azureus. I realise that it's rather simple to install manually, but I love the convenience of apt-getable packages.

Thanks for all the work.

---

### Post by Laerte Andrade on 2005-09-17
[QUOTE=Corbelius]It's no possible, sorry ;)[/QUOTE]

Sorry to bother you, but could be a little bit more specific why not? As far as I know, the [libc5 package](http://packages.ubuntu.com/breezy/oldlibs/libc5) (link provided)  does not contain the whole libc, but just some specific files to insure compatibility with old systems. That's exactly what I need. 

Thanks in advance.

---

### Post by dlai on 2005-09-17
Cube and the upcoming Sauerbraten are really good games. I would like to see them ported to amd64. Glest is already fairly easy to compile for amd64, but it could be really cool with a .deb...

---

### Post by Corbelius on 2005-09-18
[QUOTE=Laerte Andrade]Sorry to bother you, but could be a little bit more specific why not? As far as I know, the [libc5 package](http://packages.ubuntu.com/breezy/oldlibs/libc5) (link provided)  does not contain the whole libc, but just some specific files to insure compatibility with old systems. That's exactly what I need. 

Thanks in advance.[/QUOTE]

It demands of uninstall the libc6...

---

### Post by songochain on 2005-09-18
Request: Kiax 
Info: [http://kiax.sourceforge.net/](http://kiax.sourceforge.net/)

Thanks in advance

---

### Post by acariquara on 2005-09-18
If that's not too much, I request Azureus - 2.3.0.4 is out for AMD64 already, should be a matter of simple packaging.

---

### Post by Kuolio on 2005-09-20
Hey does the switch to breezy affect this repo? Any major changes coming, or broken packages, something?

---

### Post by Corbelius on 2005-09-20
[QUOTE=Kuolio]Hey does the switch to breezy affect this repo? Any major changes coming, or broken packages, something?[/QUOTE]

You can use them without no problem ;)

---

### Post by kumpf on 2005-09-22
I program PIC microntrollers frequently and really like the interface of MPLAB's IDE.  But, it runs in Windows and I'm tired of starting up a virtual machine to run it.

So I looked around a bit and "gpsim" is getting to be pretty full-featured with a nice interface and great functionality for programming PIC microcontrollers.  

I found a version of "gpsim" in the repository (0.20.14-7.1), but it is not the latest (0.21.4) and operates in a very clumsy manner.  Anyone want to make the .deb package for amd64 and put it in the repository?  I started to do it, but realized it needed some other packages I wasn't sure how to include. (needs a later version of gtk+ >= 1.3.13 , and a gtk+extras package gtk+extra-1.1.0)

You can get the source here.
[http://www.dattalo.com/gnupic/gpsim.html#src](http://www.dattalo.com/gnupic/gpsim.html#src)

Thanks so much for the help!   :grin:

---

### Post by Corbelius on 2005-09-22
[QUOTE=kumpf]I program PIC microntrollers frequently and really like the interface of MPLAB's IDE.  But, it runs in Windows and I'm tired of starting up a virtual machine to run it.

So I looked around a bit and "gpsim" is getting to be pretty full-featured with a nice interface and great functionality for programming PIC microcontrollers.  

I found a version of "gpsim" in the repository (0.20.14-7.1), but it is not the latest (0.21.4) and operates in a very clumsy manner.  Anyone want to make the .deb package for amd64 and put it in the repository?  I started to do it, but realized it needed some other packages I wasn't sure how to include. (needs a later version of gtk+ >= 1.3.13 , and a gtk+extras package gtk+extra-1.1.0)

You can get the source here.
[http://www.dattalo.com/gnupic/gpsim.html#src](http://www.dattalo.com/gnupic/gpsim.html#src)

Thanks so much for the help!   :grin:[/QUOTE]

Add it, stay tuned ;)

---

### Post by cristyde on 2005-09-23
Hi, I need the[COLOR=DarkOrange] gcc-2.95[/COLOR] packages (for installing Oracle), any chance to have them?

Thanks for the great work!

---

### Post by cristyde on 2005-09-23
Sorry, gcc-2.95 and [COLOR=DarkOrange]libstdc++-2.10-glibc2.2[/COLOR]
Thanks again

---

### Post by Corbelius on 2005-09-23
[QUOTE=cristyde]Sorry, gcc-2.95 and [COLOR=DarkOrange]libstdc++-2.10-glibc2.2[/COLOR]
Thanks again[/QUOTE]

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libstdc&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libstdc&searchon=names&subword=1&version=all&release=all)

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gcc&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gcc&searchon=names&subword=1&version=all&release=all)

---

### Post by cristyde on 2005-09-23
[QUOTE=Corbelius][http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libstdc&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libstdc&searchon=names&subword=1&version=all&release=all)

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gcc&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gcc&searchon=names&subword=1&version=all&release=all)[/QUOTE]

Yes, I see them there, but they're i386 and I need amd64.
Thanks.

---

### Post by kumpf on 2005-09-25
still waiting on the addition of "gpsim 0.21.4" to the repository... 

[http://www.dattalo.com/gnupic/gpsim.html#src](http://www.dattalo.com/gnupic/gpsim.html#src)

I've been trying to make a .deb of it for a while, but somehow keep getting lost in the intricacies of the how-to..   Any help?  

Shouldn't there be an easy script that takes a .tar.gz file and builds a deb package completely assuming defaults?  I know it wouldn't be as personal, but it would probably allow for .deb package creation with just a line or two instead of 10 pages of how-to.

I think the how-to is awesome \\:D/ , but I must be missing something important along the way.  ](*,) 


thanks.

---

### Post by Vladtux on 2005-09-25
Hey Guys... great Job !!! congratulations :D


Well I need install kernel-source-2.6.12-amd64-k8.deb ...then you can put this package in the repository?  :roll: 


Thxns!!! Again

Esop  :razz:

---

### Post by Vladtux on 2005-09-25
[QUOTE=Vladtux]Hey Guys... great Job !!! congratulations :D


Well I need install kernel-source-2.6.12-amd64-k8.deb ...then you can put this package in the repository?  :roll: 


Thxns!!! Again

Esop  :razz:[/QUOTE]


Sorry but I found it :D

[http://tamir.nooms.de/ubuntu/dists/cvs/universe/binary-amd64/kernel-image-2.6.12-amd64-k8_2.6.12-4.4_amd64.deb](http://tamir.nooms.de/ubuntu/dists/cvs/universe/binary-amd64/kernel-image-2.6.12-amd64-k8_2.6.12-4.4_amd64.deb)


XD

---

### Post by arlie on 2005-09-27
How about Gambase BASIC? I'm new to Linux and I originally installed Ubuntu 64-bit on my Athlon64 1800 but I could not use a lot of apps because there were no 64-bit version so I switched to the 32-bit Ubuntu.

I'm now trying to learn Gambas and there's no 64-bit version of it. I just bought an Athlon64 3200 and I want to try Breezy Badger 64-bit on it.

---

### Post by greenfrog on 2005-09-27
I tried to install jre1.5 and use with OpenOffice Base.

However, I can not find the jre1.5 after installing it with apt-get.

What am I doing wrong?
Thanks

---

### Post by DancingSun on 2005-09-27
[QUOTE=greenfrog]I tried to install jre1.5 and use with OpenOffice Base.

However, I can not find the jre1.5 after installing it with apt-get.

What am I doing wrong?
Thanks[/QUOTE]
You should be able to see the installed package in Synaptic if you installed it correctly.

---

### Post by dlai on 2005-09-30
Hey guys
A few weeks ago, I tried suggesting making a .deb for both Cube/Sauerbraten and Glest, is this possible. It could be really nice, but are you not porting games?

---

### Post by Win2Kuser on 2005-10-01
Hey Guys,
struggling with this a little bit :)

I did the sanaptic -->add-->custom etc and added the deb info etc and it took it ok.

Question is, how exactly would I install Sun-java?

I did the apt-get update

But now what do I type?

I tried apt-get install j2re1.5, sun-j2re1.5, blackdownj2re1.5 and lots of other combinations, but I get the same file not found error :(

Anyone got an idea of how to install it?

TIA :D

---

### Post by Win2Kuser on 2005-10-01
oops - Never mind :)

I had missed the universe multiverse restricted off the end of the deb entry :roll:

J2re installing now, hopefully I can get Net Dimes installed and running now :D

---

### Post by DancingSun on 2005-10-04
[QUOTE=Win2Kuser]oops - Never mind :)

I had missed the universe multiverse restricted off the end of the deb entry :roll:

J2re installing now, hopefully I can get Net Dimes installed and running now :D[/QUOTE]
What's Net Dimes?

---

### Post by Tamir on 2005-10-06
Hello everybody :)
As you can see, i was not here a long time - that's because i study and I don't have time for anything.
But please if you have questions/anything mail me, i am available on email [email]Tamir@nooms.de[/email].

See you ;)

---

### Post by DancingSun on 2005-10-06
[QUOTE=Tamir]Hello everybody :)
As you can see, i was not here a long time - that's because i study and I don't have time for anything.
But please if you have questions/anything mail me, i am available on email [email]Tamir@nooms.de[/email].

See you ;)[/QUOTE]
HE'S ALIIIIVE!:D

---

### Post by DancingSun on 2005-10-06
Bit of a discouraging new, but I heard Sun's Java package has been taken off of the official repositories due to "legal reasons", so should we take ours off as well?

---

### Post by Tamir on 2005-10-07
Well i don't know, can someone check it for us?

---

### Post by DancingSun on 2005-10-07
[QUOTE=Tamir]Well i don't know, can someone check it for us?[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=67198&highlight=java](http://ubuntuforums.org/showthread.php?t=67198&highlight=java)

---

### Post by Tamir on 2005-10-07
I afraid it means we can not host java packages anymore :???: 
I am not sure i understood right, but we can host it only after paying money - I am not sure.

---

### Post by medication on 2005-10-07
It definitely appears that we are unable to host the packages.  According to jdong ([profile]("http://ubuntuforums.org/member.php?u=780")): "In addition to licensing, J2RE can't be distributed with any other Java distributions, including GCC 4.0's Java compiler, and the GCC4 suite is necessary for Firefox backports."

Meaning that even if we were to pay for the license we would still be unable to distribute the RE due to the GCC/Firefox conflict.

Hope everyone that needed got a chance to install it before it got yanked.

For those who didn't, you should look at this thread to find instructions about building Java for your system: [Java Instructions]("http://ubuntuforums.org/showthread.php?t=68718")

---

### Post by Stereotypical Rage on 2005-10-07
Is the new FireFox 1.5 Beta 2 in the repos, yet?

I can't find the Source for FF1.5B2. I must be dumb or not looking in the right places.

---

### Post by jvictor on 2005-11-04
Can u build the 64 bit version of via UNICHROME display drivers? U can find the source at 
[http://www.viaarena.com/Driver/linux-fbdev-kernel-src_20050726.tgz](http://www.viaarena.com/Driver/linux-fbdev-kernel-src_20050726.tgz)
[edit]
I find that lots of people need it .. and it will b great if u can get it done
[/edit]

---

### Post by skylark on 2005-11-04
there are amd64 packages for celestia and poker3d. But when I try and run them I always get multiple errors. I'm wondering if there are bugs in the code to these projects that make them unstable on amd64 or if it is something to do with the packaging. One day I'll get around to compiling these from source myself to see. But has anyone tried already?

---

### Post by Tamir on 2005-11-04
Ok, hi guys :D
I want to ask, is the a reason to build another packages for hoary? or to move breezy?
I think i will back soon.

---

### Post by songochain on 2005-11-05
breezy

---

### Post by mihaic on 2005-11-18
Hi Tamir,

  This is indeed a nice initaitive. Do you by any chance have some amd64 packages for FireFox 1.0.7 or for 1.5 RC2? If not, maybe I can try making those packages for you. The only problem is that I am a newbie in Linux environment and I never did this before. Do you have some pointers from where to start documenting myself?

Thanks.

---

### Post by DancingSun on 2005-11-18
[QUOTE=Tamir]Ok, hi guys :D
I want to ask, is the a reason to build another packages for hoary? or to move breezy?
I think i will back soon.[/QUOTE]
Move to breezy.

---

### Post by DancingSun on 2005-11-18
[QUOTE=mihaic]Hi Tamir,

  This is indeed a nice initaitive. Do you by any chance have some amd64 packages for FireFox 1.0.7 or for 1.5 RC2? If not, maybe I can try making those packages for you. The only problem is that I am a newbie in Linux environment and I never did this before. Do you have some pointers from where to start documenting myself?

Thanks.[/QUOTE]
Click on the "Ubuntu 64 Backports" link in Tamir's signature.  It'll take you to the project's wiki page, you'll find a section on "Guides" which will have a tutorial written by Tamir about making packages.

---

### Post by mihaic on 2005-11-18
I intend to move to Breezy just as soon as my freshly oredred cd's get here (I'm to lazy to download it). 
  I also see no reason to why not make those packages, maybe there are peaople who still use Hoary an they will find them useful.

P.S. I can hardly wait for the disks to get here :)

---

### Post by mihaic on 2005-11-18
Thanks DancingSun, I'll have a look there and try to put things in practice :)

---

### Post by freedom on 2005-12-02
Will BREEZY repos soon be available?
:confused: 
That would truly be great. :KS

---

### Post by Zuggi on 2006-01-15
Hi Tamir -

just wanted to thank you for your packages! Java was on top of my wish list :p 

As I am some kind of new to Linux, some wishes wil larise soon ;-) - then I'll let you know!

Thanks,
Zuggi

---

### Post by BluBoy on 2006-01-31
Does anyone have a copy of all the files provided by the OP?
The Reps no longer work, the HTML and wiki pages are no longer available either.

OR - Are there anyother how-to's around for FreeNX on a AMD64 machine?

Thanks!

---

### Post by majik279 on 2006-02-19
What happened to everything? Will someone fill me in?

---

### Post by smoon on 2006-02-24
Ahoi guys!

I'm the one who hosted tamir's stuff. Since he did not log in for a few months and didn't respond to any email I send him I put his stuff offline for security reasons (you know, there may be bugs in the wiki code and I'm not interested in doing updates for tamir). All the data's still there, so if anyone is interested in it I can provide you with a tarball, just contact me on jabber: [email]smoon@jabber.ccc.de[/email] or via email public%nooms,de

---

### Post by Josef K. on 2006-02-27
@smoon

if nobody is going to support tamir archive anymore, since plf doesn't provide support for amd64 architecture (none of them got an amd64 :P) maybe you should contact them
would be a pity loose all that packages

---

### Post by workbench on 2006-02-28
Hi,
What I do wrong because I get this error message when trying to build firefox
on Ubuntu 5.10 (cpu is AMD Turion):

/usr/bin/ld: jsapi.o: relocation R_X86_64_PC32 against `memset@@GLIBC_2.2.5' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: final link failed: Bad value
collect2: ld returned 1 exit status
make[4]: *** [libmozjs.so] Error 1

Do I need new compile tools or what is the case?

---

### Post by Sandman71 on 2006-04-10
Any plans on working on an AMD64 version of Pine? Try as I might, I can't seem to be able to compile it for this architecture.

---

### Post by ravpaul on 2006-09-30
I have recently installed Java(TM) Plug-in Blackdown-1.4.2-rc1 but when I visit any site that requires java my browser (firefox) freezes.

I ran the browser from terminal and got the following error when it froze:

```
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

```

I have googled this message but have not found any solutions please help

---

