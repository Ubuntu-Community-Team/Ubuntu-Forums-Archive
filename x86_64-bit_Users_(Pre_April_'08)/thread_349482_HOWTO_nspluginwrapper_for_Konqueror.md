---
title: "HOWTO: nspluginwrapper for Konqueror"
date: 2007-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by kuja on 2007-01-30
Alrighty willing guinea pigs, I've pulled together a how-to to tell you how to get 32-bit plugins (such as Adobe Flash) going in 64-bit Konqueror in (K)Ubuntu, through the use of nspluginwrapper. It's really simple, and it works, though it does take a while.

[size=5]**Patching Konqueror**[/size]
The hard part, rebuilding kdebase with a patch, still not that hard, maybe a bit time consuming. The download is around 29MB, and building it took roughly 20-30 minutes on my hardware (I wasn't paying that much attention while it built ... played on IRC instead)

First, you need to turn on the source repositories for, at least, Ubuntu main. It will look like one of these:
> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main #for Edgy
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main #for Dapper

It is important that the line say "deb-src" and not just "deb" - having only the "deb" line simply will not do! If you don't have a line like this, add it to your "/etc/apt/sources.list" file, and then ```
sudo apt-get update
```

If you're unsure how to do this, see this document for help: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Note: If you're using a more recent kde from [http://kubuntu.org](http://kubuntu.org), you need a line like one of these too:
> 
deb-src [http://kubuntu.org/packages/kde-356](http://kubuntu.org/packages/kde-356) edgy main #for edgy
deb-src [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) dapper main #for dapper

The instructions from now on will assume you're using KDE 3.5.6 in Edgy, if you're not, modify the locations/versions to suit.

```
sudo aptitude install build-essential fakeroot debhelper debconf
sudo apt-get build-dep kdebase
sudo apt-get source kdebase

wget http://gwenole.beauchesne.info/projects/nspluginwrapper/files/kdebase-3.4.2-npapi-64bit-fixes.patch
patch kdebase-3.5.6/nsplugins/sdk/npapi.h kdebase-3.4.2-npapi-64bit-fixes.patch
cd kdebase-3.5.6
dpkg-buildpackage -rfakeroot -uc -b
cd ..
sudo dpkg -i *.deb
```

[size=5]**Installing and Configuring NSPluginWrapper**[/size]

First, you need to add the Janvitus repository to your "/etc/apt/sources.list" file if you don't already have it:
> deb [http://janvitus.cabspace.com/ubuntu/](http://janvitus.cabspace.com/ubuntu/) edgy-janvitus main-amd64

Next, add the Janvitus gpg key:
```
wget http://janvitus.cabspace.com/ubuntu/2C4C84CC.gpg -O- | sudo apt-key add -
```

Next, update and install nspluginwrapper
```
sudo aptitude update;
sudo aptitude install nspluginwrapper
```

Next, you'll need to have nspluginwrapper wrap the plugins so you can use them. I'll use Flash 9 as the example. You'll need to know where you have the plug-in installed at, for example, I have flash installed in /usr/lib/opera/plugins, so the command I would run would be this:

```
nspluginwrapper --install /usr/lib/opera/plugins/libflashplayer.so
```

All you have to do after doing this, is go to, in konqueror, *settings -> configure konqueror -> plugins* and click on scan for new plugins. It should pick it up, if not, add the directory ~/.mozilla/plugins to the list of plug-in directories Konqueror searches and try again.

Go to a place like [http://www.adobe.com](http://www.adobe.com) or [http://www.youtube.com](http://www.youtube.com) to test.

That concludes this little how-to, good luck and tell me if it works for you :guitar:

---

### Post by Corbelius on 2007-01-30
> **kuja said:**
> 

Next, update and install nspluginwrapper
```
sudo aptitude update;
sudo aptitude install linux32 nspluginwrapper
```


Linux32, and other dependencies, already are included:

> @ubuntubox:~$ apt-cache show nspluginwrapper
Package: nspluginwrapper
Priority: opzionale
Section: main\-amd64/net (universe)
Installed-Size: 296
Maintainer: Gianvito Cavasoli <gianvito77@aim.com>
Architecture: amd64
Version: 0.9.91.2-1ubuntu5~janvitus
Replaces: nspluginwrapper-i386
Depends: lib32gcc1 (>= 1:4.1.1-12), libc6 (>= 2.4-1), libc6-i386 (>= 2.4-1), libglib2.0-0 (>= 2.12.0), libx11-6, libxt6, **ia32-libs, ia32-libs-gtk, linux32, lib32asound2, gsfonts-x11**
Conflicts: nspluginwrapper-i386
Filename: pool/edgy-janvitus/main-amd64/nspluginwrapper_0.9.91.2-1ubuntu5~janvitus_amd64.deb
Size: 95520
MD5sum: 125a9bc5eb8c98939de5168953f56bf8
SHA1: 3327f19e960f864a5a927547585d731b7f3246a1
SHA256: 757afdcbb091c5c6f7fc6130026a1375f856d8d51dc496163fdaec04c91d7643
Description: A compatibility layer for Netscape 4 plugins
 nspluginwrapper makes it possible to use Netscape 4 compatible plugins
 compiled for i386 into Mozilla for another architecture, e.g. x86_64.
 .
 This package consists in:
   * npviewer: the plugin viewer
   * npwrapper.so: the browser-side plugin
   * nspluginwrapper: a tool to manage plugins installation and update


;)

---

### Post by kuja on 2007-01-30
I know, but it didn't hurt anything, and it never hurts to be specific anyway. Besides, there's a story behind my putting that there. There's always a story ;)

Oh, and while I'm at things, thanks for providing such a useful repository!

---

