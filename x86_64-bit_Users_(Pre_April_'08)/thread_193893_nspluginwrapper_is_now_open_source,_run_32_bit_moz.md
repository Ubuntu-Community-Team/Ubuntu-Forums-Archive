---
title: "nspluginwrapper is now open source, run 32 bit mozilla plugins on 64 bit firefox!"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmb on 2006-06-10
I mentioned this on the other threads, but before nspluginwrapper was not open source and didn't work as well. Well, now, the author has opensourced it and put it under gpl license. This allows you to run 32-bit plugins with 64-bit firefox.   I'd just thought i'd tell everyone. Anyone have any good experiences with it? Is it good enough to include in ubuntu?

---

### Post by RaZoR1394 on 2006-06-10
I tried it on Gentoo (binary) and it was horrible. It kept locking up the browser all the time just to name one of the problems.

---

### Post by dmb on 2006-06-10
Well, now that its open sourced (and there has been a large update appearently) the possibilities are unlimited.  I currently do not have access to a 64bit proc to test it, but appearently its supposed to be better now.

---

### Post by jairo.serrano on 2006-06-12
[QUOTE=dmb]I mentioned this on the other threads, but before nspluginwrapper was not open source and didn't work as well. Well, now, the author has opensourced it and put it under gpl license. This allows you to run 32-bit plugins with 64-bit firefox.   I'd just thought i'd tell everyone. Anyone have any good experiences with it? Is it good enough to include in ubuntu?[/QUOTE]


works very well ... :)

---

### Post by JoWilly on 2006-06-12
Version 0.9.90.1 does not work.

I have tried to build this from source and I have also tried converting the rpms to debs.

The docs talk of an  nspluginwrapper command which does not exit; it seems to be replaced by the npconfig command.

The plugin is now loaded in my firefox, but when I start npconfig to install the flash plugin it seems to do so, but in reality it does not (the flash plugin is in the scanned dirs). I'm losing a lot of time on this crap. If anyone has any hints please post.

---

### Post by nwillis on 2006-06-14
Managing the installation/removal of plugins manually from a bash terminal is inconvenient for a web browser feature -- someone needs to write a Firefox extension around this so you can do it in-browser.

---

### Post by superm1 on 2006-06-15
[quote=JoWilly]Version 0.9.90.1 does not work.

I have tried to build this from source and I have also tried converting the rpms to debs.

The docs talk of an  nspluginwrapper command which does not exit; it seems to be replaced by the npconfig command.

The plugin is now loaded in my firefox, but when I start npconfig to install the flash plugin it seems to do so, but in reality it does not (the flash plugin is in the scanned dirs). I'm losing a lot of time on this crap. If anyone has any hints please post.[/quote]

I've got the exact same problem.  In looking at the gentoo ebuild, I saw that /usr/bin/nspluginwrapper is supposed to be a symlink to npconfig, so I made that hoping it would do it.  Still nothing.

---

### Post by superm1 on 2006-06-15
Quick followup-

```
sudo apt-get install linux32
```


And now your nspluginwrapper should work correctly.

---

### Post by John Jason Jordan on 2006-06-15
[QUOTE=superm1]Quick followup-
```
sudo apt-get install linux32
```
And now your nspluginwrapper should work correctly.[/QUOTE]
What does that code do?

---

### Post by superm1 on 2006-06-15
Installs linux32.

linux32 is a binary that nspluginwrapper depends on.  If you look at the source code, you can see there are some direct calls to it.

---

### Post by JoWilly on 2006-06-15
[quote=superm1]Quick followup-

```
sudo apt-get install linux32
``` 

And now your nspluginwrapper should work correctly.[/quote]

I have linux32 installed.

But it does not work. The ns plugin shows up in the firefox plugin list, but it neither detects flash nor installs the flash plugin from the command line.

What did you do to get it to work ?

---

### Post by superm1 on 2006-06-15
Is the wrapped plugin installed in your home directory?

```
/usr/lib/nspluginwrapper/x86_64/npconfig -v -a -i
```

Will automatically generate wrapped versions of each plugin available to you.

---

### Post by Corbelius on 2006-06-17
It work good with flash player now :)

---

### Post by HellSpawn on 2006-06-19
It's there a HOW-TO for this??

---

### Post by superm1 on 2006-06-19
Maybe good idea for original thread author to change his post to make this thread a howto :)

---

### Post by HellSpawn on 2006-06-20
I found one here: 

 [http://ubuntuforums.org/showthread.php?t=160318](http://ubuntuforums.org/showthread.php?t=160318)

> 
Instructions to install:

1) Download the Plugin and the Viewer from [http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper](http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper)
2) Install Alien, if not already installed.
3) Convert the downloaded rpm's to deb's (sudo alien -d *.deb)
4) Install the newly created debs (Install in this order: sudo dpkg -i nspluginwrapper-i386_0.9.90-2_amd64.deb, sudo dpkg -i nspluginwrapper_0.9.90-2_amd64.deb) -- If I got the order wrong, you'll know because it won't install.
5) Download the plugin you want to install, and extract the .so file. For example, to install flash, grab the tar.gz file from Macromedia's website, and extract libflashplayer.so.
6) Move the plugin (example, libflashplayer.so) to /usr/lib/mozilla/plugins. This is where nspluginwrapper stores the main plugin, so it's probably a nice folder to keep them.
7) Now we need nsplugwrapper to make the new plugin, so call: /usr/lib/nspluginwrapper/x86_64/npconfig -i /usr/lib/mozilla/plugins/libflashplayer.so (if wanting the flash plugin, of course). Depending on whether or not you run that command with sudo, it will either end up in /usr/lib/mozilla/plugins, or ~/.mozilla/plugins. If you ran it as sudo, you'll need to link it to either your profile's plugins or the main plugins (/usr/lib/mozilla-firefox/plugins). Or copy, doesn't matter. The old plugin must not move, as it's path seems to become hard coded in the new plugin created (which has "npwrapper-" prepended to the old name).


I think the "alien -d *.deb" should be "alien -d *.rpm" (It worked for me), and the filename and versions of the nsplugginwrapper RPM had changed since the thread was open...

It works just fine for me :D

---

### Post by JoWilly on 2006-06-20
[quote=HellSpawn]I found one here: 

 [http://ubuntuforums.org/showthread.php?t=160318]("http://ubuntuforums.org/showthread.php?t=160318")
[/quote]

Thanks a lot ! It is working now :D

I tried everything previously, but missed the fact that npconfig created a new npwrapper.libflashplayer.so in /usr/lib/mozilla/plugins that need to be linked to /usr/lib/firefox/plugins.

---

### Post by ssmaxss on 2006-06-21
As it is opensource, can it be added to universe?

---

### Post by darkshadow on 2006-06-21
I just installed this and loved it until I noticed my firefox browser has started freezing all the time. Has anyone else noticed this problem?

---

### Post by JoWilly on 2006-06-21
[quote=darkshadow]I just installed this and loved it until I noticed my firefox browser has started freezing all the time. Has anyone else noticed this problem?[/quote]

Nope... works fine here.

---

### Post by superm1 on 2006-06-21
[QUOTE=darkshadow]I just installed this and loved it until I noticed my firefox browser has started freezing all the time. Has anyone else noticed this problem?[/QUOTE]

Its not consistent, but happens for me a bit.

---

### Post by incubus on 2006-06-24
I'm probably missing something, the question is what. I followed the suggestions in here, but still no flash in firefox. 

I have linux32, I tried to copy or make a soft link for the files:
```

npwrapper.libflashplayer.so
npwrapper.so
libflashplayer.so

```

in /usr/lib/firefox/plugins/.

I also tried to copy them to ~/.mozilla/plugins/ and I gave "npconfig -v -a -i" a try as well.

Just to check, ```
about:plugins
``` in firefox gives me:

```

    File name: npwrapper.so
    nspluginwrapper 0.9.90.1 adds support for i386 compiled Netscape 4 plugins.
    This is beta software available under the terms of the GNU General Public License.

MIME Type                 Description      Suffixes     Enabled
unknown/mime-type     Do not open    none         Yes

```

So, does anybody see what I'm doing wrong?
Java applets are working.

Thank you!
incubus

---

### Post by superm1 on 2006-06-24
Incubus, I Think that  nspluginwrapper is highly dependent on where the files npconfig generates are placed.  I Think that they're hardcoded to the path of the plugin rather then a relavent path.  So if you run npconfig with the 32 bit flash plugin in your home directory, it will generate wrapped plugins that point to that flash binary in your home directory.

---

### Post by incubus on 2006-06-24
Thanks superm1,

I started again from scratch, now also following your notes in the other thread. I deleted the things from /usr/lib/mozilla/plugins and ran again with libflash in ~/.mozilla/plugins.

Still nothing. 
One question: what do you have in about : plugins? I only have npwrapper, but I wonder if I should see npwrapper.libflash as well.

I had an idea. I'm gonna try another plugin.

incubus

---

### Post by JoWilly on 2006-06-24
[quote=incubus]I'm probably missing something, the question is what. I followed the suggestions in here, but still no flash in firefox. 

I have linux32, I tried to copy or make a soft link for the files:
```

npwrapper.libflashplayer.so
npwrapper.so
libflashplayer.so

``` 
in /usr/lib/firefox/plugins/.

I also tried to copy them to ~/.mozilla/plugins/ and I gave "npconfig -v -a -i" a try as well.

Just to check, ```
about:plugins
``` in firefox gives me:

```

    File name: npwrapper.so
    nspluginwrapper 0.9.90.1 adds support for i386 compiled Netscape 4 plugins.
    This is beta software available under the terms of the GNU General Public License.

MIME Type                 Description      Suffixes     Enabled
unknown/mime-type     Do not open    none         Yes

``` 
So, does anybody see what I'm doing wrong?
Java applets are working.

Thank you!
incubus[/quote] 
I had EXACTLY the same problem, until I realised that npconfig created a new npwrapper.libflashplayer.so in /usr/lib/mozilla/plugins that need to be linked to /usr/lib/firefox/plugins.

Do not mess with your home dir. I was issuing exactly the same commands you do, and it was not working. _Follow the howto precisely_ (also give the full paths in the commands) on the previous page and it should work.

---

### Post by incubus on 2006-06-24
Thanks JoWilly,

Still doesn't work. This time I literally copied/pasted. I must be doing something wrong, of course. 

Can we do this the silly way? Can you confirm which files I should have?

In /usr/lib/mozilla/plugins/ I have (using ls -aslh):
```

   0 drwxr-xr-x 2 root root  133 2006-06-24 15:28 .
   0 drwxr-xr-x 3 root root   20 2006-06-24 11:33 ..
2.1M -rwxr-xr-x 1 root root 2.1M 2006-06-24 15:27 libflashplayer.so
   0 lrwxrwxrwx 1 root root   38 2006-06-24 11:33 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
 24K -rw-r--r-- 1 root root  24K 2006-06-24 11:51 libnullplugin.so
 40K -rwxr-xr-x 1 root root  39K 2006-06-24 15:27 npwrapper.libflashplayer.so
 40K -rwxr-xr-x 1 root root  39K 2006-06-24 15:28 npwrapper.so

```

In /usr/lib/firefox/plugins/
```

   0 drwxr-xr-x 2 root root  109 2006-06-24 15:29 .
4.0K drwxr-xr-x 5 root root 4.0K 2006-06-24 11:21 ..
   0 lrwxrwxrwx 1 root root   45 2006-06-24 14:08 libjavaplugin_oji.so -> /usr/lib/mozilla/plugins/libjavaplugin_oji.so
 24K -rw-r--r-- 1 root root  24K 2006-06-24 14:10 libnullplugin.so
   0 lrwxrwxrwx 1 root root   52 2006-06-24 15:29 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
   0 lrwxrwxrwx 1 root root   37 2006-06-24 15:29 npwrapper.so -> /usr/lib/mozilla/plugins/npwrapper.so

```

And should I see only nspluginwrapper in about : plugins, or anything else?

incubus

PS: Before doing this I deleted ~/mozilla/plugins/, to avoid confusion. I've already tried the other way around.

PS2: I also don't have any firefox or npviewer processes, by the way. And I even rebooted.

---

### Post by JoWilly on 2006-06-24
[quote=incubus]Thanks JoWilly,

Still doesn't work. This time I literally copied/pasted. I must be doing something wrong, of course. 

Can we do this the silly way? Can you confirm which files I should have?

In /usr/lib/mozilla/plugins/ I have (using ls -aslh):
```

   0 drwxr-xr-x 2 root root  133 2006-06-24 15:28 .
   0 drwxr-xr-x 3 root root   20 2006-06-24 11:33 ..
2.1M -rwxr-xr-x 1 root root 2.1M 2006-06-24 15:27 libflashplayer.so
   0 lrwxrwxrwx 1 root root   38 2006-06-24 11:33 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
 24K -rw-r--r-- 1 root root  24K 2006-06-24 11:51 libnullplugin.so
 40K -rwxr-xr-x 1 root root  39K 2006-06-24 15:27 npwrapper.libflashplayer.so
 40K -rwxr-xr-x 1 root root  39K 2006-06-24 15:28 npwrapper.so

``` 
In /usr/lib/firefox/plugins/
```

   0 drwxr-xr-x 2 root root  109 2006-06-24 15:29 .
4.0K drwxr-xr-x 5 root root 4.0K 2006-06-24 11:21 ..
   0 lrwxrwxrwx 1 root root   45 2006-06-24 14:08 libjavaplugin_oji.so -> /usr/lib/mozilla/plugins/libjavaplugin_oji.so
 24K -rw-r--r-- 1 root root  24K 2006-06-24 14:10 libnullplugin.so
   0 lrwxrwxrwx 1 root root   52 2006-06-24 15:29 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
   0 lrwxrwxrwx 1 root root   37 2006-06-24 15:29 npwrapper.so -> /usr/lib/mozilla/plugins/npwrapper.so

``` 
And should I see only nspluginwrapper in about : plugins, or anything else?

incubus

PS: Before doing this I deleted ~/mozilla/plugins/, to avoid confusion. I've already tried the other way around.

PS2: I also don't have any firefox or npviewer processes, by the way. And I even rebooted.[/quote] 
I have now just installed it again on a fresh dapper install.

This is what about:plugins shows:
```

Shockwave Flash
npwrapper.libflashplayer.so
Shockwave Flash 7.0 r63
Type MIME Description Suffixes application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  

``` 
In /usr/lib/mozilla/plugins/ I have :
```

$ ls /usr/lib/mozilla/plugins/
libflashplayer.so  npwrapper.libflashplayer.so  npwrapper.so

``` 
In  /usr/lib/firefox/plugins/
```

$ ls /usr/lib/firefox/plugins/
libtotem_mozilla.so   libunixprintplugin.so
libtotem_mozilla.xpt  npwrapper.libflashplayer.so

``` 
(java is not installed yet on this machine, but its working fine with java in the folder on the other machine).

This is what I did:

```

1. download the 2 nspluginwrapper rpms
2. sudo alien -d *.rpm
3. sudo dpkg -i *.deb
4. download flash from macromedia and extract libflashplayer.so to a tmp folder
5. sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
6. sudo /usr/lib/nspluginwrapper/x86_64/npconfig -i /usr/lib/mozilla/plugins/libflashplayer.so
7. sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/

``` 
This worked on the first try just 2 minutes ago.

Good luck.

---

### Post by incubus on 2006-06-24
Aah, finally got it. I knew the problem was here (read: me).

JoWilly, the key was you telling me what should be in "about : plugins". I didn't have the correct plugin. So I decided to run firefox in the terminal to see what was going on and bingo, I got this message when opening "about : plugins" (just starting firefox didn't give me anything):

```

Failed to open device
/usr/lib/nspluginwrapper/i386/npviewer.bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```

Seaching the forums for that library, I came across somebody mentioning "ia32-libs-gtk". Just had to install the sucker and voila (I had only installed linux32). Perhaps adding these requirements to the "HOWTO" would help other people.

Thank you guys! :)

incubus

---

### Post by JoWilly on 2006-06-24
FYI I just installed realplayer 10.0.0.7, the plugin works  ! (installs in the same way, but I deleted nphelix.* from /usr/lib/firefox/plugins before setting it up with nspluginwrapper).

Edit: get the realplayer deb here and install with "dpkg -i --force-architecture"
[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb")

---

### Post by Dragonstar on 2006-06-25
[QUOTE=darkshadow]I just installed this and loved it until I noticed my firefox browser has started freezing all the time. Has anyone else noticed this problem?[/QUOTE]

I got the same problem. On many pages where there's a flash animation my firefox just freezes. I run firefox in the terminal and when it then freezed i killed it and terminal looked like this:

```
*** NSPlugin Viewer  *** ERROR: failed to receive reply from NPN_GetURLNotify
*** NSPlugin Viewer  *** ERROR: failed to receive reply from NPN_GetURLNotify
Killed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 541 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

What's the deal here?

---

### Post by JoWilly on 2006-06-25
[quote=Dragonstar]I got the same problem. On many pages where there's a flash animation my firefox just freezes. I run firefox in the terminal and when it then freezed i killed it and terminal looked like this:

```
*** NSPlugin Viewer  *** ERROR: failed to receive reply from NPN_GetURLNotify
*** NSPlugin Viewer  *** ERROR: failed to receive reply from NPN_GetURLNotify
Killed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 541 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
``` 
What's the deal here?[/quote] 
It's working fine here. 

Have you tried reporting the bug to the author of nsplugin wrapper ?

I think the only contact info for feedback on his site is this email : 
[email]gb.public@free.fr[/email]

[http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper]("http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper")

---

### Post by JoWilly on 2006-06-25
Furthermore, **_regarding firefox freezes_** :

Firefox64 freezed on my system if 32bit plugins were in the plugins directory when accessing pages that need these plugins.

So make sure, that** if you are running firefox64 all 32bit plugins (flash, realplayer,...) are removed from the plugins directories** (/usr/lib/firefox/plugins, the home dir, etc...).

Only the nspluginwrapper plugins (and all 64bit plugins) should remain in the firefox64 plugin dirs (the 32bit flash, realplayer plugins will be in /usr/lib/mozilla/plugins where firefox64 is not looking for them).

---

### Post by superm1 on 2006-06-25
[quote=JoWilly]Furthermore, **_regarding firefox freezes_** :

Firefox64 freezed on my system if 32bit plugins were in the plugins directory when accessing pages that need these plugins.

So make sure, that** if you are running firefox64 all 32bit plugins (flash, realplayer,...) are removed from the plugins directories** (/usr/lib/firefox/plugins, the home dir, etc...).

Only the nspluginwrapper plugins (and all 64bit plugins) should remain in the firefox64 plugin dirs (the 32bit flash, realplayer plugins will be in /usr/lib/mozilla/plugins where firefox64 is not looking for them).[/quote]
Does doing this completely resolve all freezes?

---

### Post by JoWilly on 2006-06-25
[quote=superm1]Does doing this completely resolve all freezes?[/quote] 
As I said, 32bit plugins do not work on firefox64, they make the browser freeze.

Yes, it has never crashed here since firefox is not trying to use the 32bit plugins. And it works very well with flash and realplayer using nspluginwrapper.

---

### Post by incubus on 2006-06-25
That makes a lot of sense. It never crashed for me either. 

In my 1 day of experience anyway.

incubus

---

### Post by superm1 on 2006-06-25
[quote=JoWilly]As I said, 32bit plugins do not work on firefox64, they make the browser freeze.

Yes, it has never crashed here since firefox is not trying to use the 32bit plugins. And it works very well with flash and realplayer using nspluginwrapper.[/quote]

I don't think that is the solution for the random freezes.  I moved all my plugins around as you indicated, but I am still getting freezes every so often on flash sites.
```
supermario@supermario:~$ cd /usr/lib/mozilla/plugins/
supermario@supermario:/usr/lib/mozilla/plugins$ ls
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.so   nppdf.so
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt  npwrapper.libflashplayer.so
libnullplugin.so        mplayerplug-in-rm.so   mplayerplug-in.xpt      npwrapper.nphelix.so
mplayerplug-in-gmp.so   mplayerplug-in-rm.xpt  nphelix.so              npwrapper.nppdf.so
mplayerplug-in-gmp.xpt  mplayerplug-in.so      nphelix.xpt             npwrapper.so
supermario@supermario:/usr/lib/mozilla/plugins$ cd /usr/lib/firefox/plugins/
supermario@supermario:/usr/lib/firefox/plugins$ ls
libunixprintplugin.so   mplayerplug-in-qt.so   mplayerplug-in-rm.xpt  mplayerplug-in-wmp.xpt
mplayerplug-in-gmp.so   mplayerplug-in-qt.xpt  mplayerplug-in.so      mplayerplug-in.xpt
mplayerplug-in-gmp.xpt  mplayerplug-in-rm.so   mplayerplug-in-wmp.so
supermario@supermario:/usr/lib/firefox/plugins$ cd /home/supermario/.mozilla/plugins/
supermario@supermario:~/.mozilla/plugins$ ls
npwrapper.libflashplayer.so  npwrapper.nphelix.so  npwrapper.nppdf.so
```

---

### Post by Dragonstar on 2006-06-25
Well, my firefox started freezing after i installed flash with nspluginwrapper.

---

### Post by JoWilly on 2006-06-25
[quote=superm1]I don't think that is the solution for the random freezes.  I moved all my plugins around as you indicated, but I am still getting freezes every so often on flash sites.
```
supermario@supermario:~$ cd /usr/lib/mozilla/plugins/
supermario@supermario:/usr/lib/mozilla/plugins$ ls
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.so   nppdf.so
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt  npwrapper.libflashplayer.so
libnullplugin.so        mplayerplug-in-rm.so   mplayerplug-in.xpt      npwrapper.nphelix.so
mplayerplug-in-gmp.so   mplayerplug-in-rm.xpt  nphelix.so              npwrapper.nppdf.so
mplayerplug-in-gmp.xpt  mplayerplug-in.so      nphelix.xpt             npwrapper.so
supermario@supermario:/usr/lib/mozilla/plugins$ cd /usr/lib/firefox/plugins/
supermario@supermario:/usr/lib/firefox/plugins$ ls
libunixprintplugin.so   mplayerplug-in-qt.so   mplayerplug-in-rm.xpt  mplayerplug-in-wmp.xpt
mplayerplug-in-gmp.so   mplayerplug-in-qt.xpt  mplayerplug-in.so      mplayerplug-in.xpt
mplayerplug-in-gmp.xpt  mplayerplug-in-rm.so   mplayerplug-in-wmp.so
supermario@supermario:/usr/lib/firefox/plugins$ cd /home/supermario/.mozilla/plugins/
supermario@supermario:~/.mozilla/plugins$ ls
npwrapper.libflashplayer.so  npwrapper.nphelix.so  npwrapper.nppdf.so
```[/quote] 
Well... works fine here.

The only differences I have is that I do not have the plugins in my home dir (should not change anything, but you never know... here the plugins run with root/system privileges, you run them as user.. maybe this could make a difference with nspluginwrapper (?)), I have installed nspluginwrapper with sudo and made links to /usr/lib/firefox/plugins , as in the easy install steps I have posted on page 3 of this thread.

I also have not installed the pdf plugin, as I see no need for it (I just open pdfs in adobe reader when I click on then).

---

### Post by superm1 on 2006-06-25
Also a FIY.  /usr/lib/mozilla/plugins/ is in the search path for plugins for FF.  So even if 32 bit plugins were just there, it wouldn't matter.  FF will spit an error back to a terminal but still work.

```
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: cannot open shared object file: No such file or directory]
```

---

### Post by JoWilly on 2006-06-25
[quote=superm1]Also a FIY.  /usr/lib/mozilla/plugins/ is in the search path for plugins for FF.  So even if 32 bit plugins were just there, it wouldn't matter.  FF will spit an error back to a terminal but still work.

```
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: cannot open shared object file: No such file or directory]
```[/quote] 
Are you sure ? Because here it freezes if the 32bit plugins are in /usr/lib/firefox, but does not if they are in /usr/lib/mozilla.

Well... if your firefox is looking in /usr/lib/mozilla and it sees the flash plugin there I can now understand why it crashes...

Edit: I also don't have these errors on my system

---

### Post by superm1 on 2006-06-25
If you open up about:config, there is an option plugin.expose_full_path.
If you set this to true, then about:plugins will tell you exactly where its getting its plugins from.

For me, its pulling all my mplayer plugins from /usr/lib/mozilla/plugins (even though they are also in /usr/lib/firefox/plugins) and my npwrapped plugins from my home directory plugins directory.

---

### Post by JoWilly on 2006-06-25
[quote=superm1]If you open up about:config, there is an option plugin.expose_full_path.
If you set this to true, then about:plugins will tell you exactly where its getting its plugins from.

For me, its pulling all my mplayer plugins from /usr/lib/mozilla/plugins (even though they are also in /usr/lib/firefox/plugins) and my npwrapped plugins from my home directory plugins directory.[/quote] 
Ahhaa !

Yes you are right :)

These are all the paths of all my installed plugins, as now shown by about : plugins (in order of appearance):

/usr/lib/mozilla/plugins/npwrapper.nphelix.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/libtotem_mozilla.so
/usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so

Edit: so this would most probably mean that the install steps can be simplified as there should be no need for the links in /usr/lib/firefox ... good :)

---

### Post by memas on 2006-06-29
I followed the instructions but firefox freezes when I try to visit a page that requires flash. The message I get is:

LoadPlugin: failed to initialize shared library /home/memas/.mozilla/plugins/libflashplayer.so [/home/memas/.mozilla/plugins/libflashplayer.so: cannot open shared object file: No such file or directory]

I run /usr/lib/nspluginwrapper/x86_64/npconfig -v -a -i
as a user not root.

Can anyone help me?

---

### Post by JoWilly on 2006-06-29
[quote=memas]I followed the instructions but firefox freezes when I try to visit a page that requires flash. The message I get is:

LoadPlugin: failed to initialize shared library /home/memas/.mozilla/plugins/libflashplayer.so [/home/memas/.mozilla/plugins/libflashplayer.so: cannot open shared object file: No such file or directory]

I run /usr/lib/nspluginwrapper/x86_64/npconfig -v -a -i
as a user not root.

Can anyone help me?[/quote] 
Everything you need to do is explained in this thread (look starting from mid-page 3). When something does not work, don't try to invent the wheel yourself. Do what works.

---

### Post by bicchi on 2006-07-14
The plugin only seems to work for some types of flash animations. So here is a tip that might help if your browser freezes. I ended up installing [Flashblock,]("https://addons.mozilla.org/firefox/433/") a firefox extension that blocks all the flash stuff from the page. Flashblock puts an icon on top of the flash window and when you click it, the flash animation activates. This might not fix your problem but at least prevents any unwanted animation that is causing the problem from showing up and freezing the browser. It also blocks all those pesky ads. 

You can find information about the development of flash on linux by going [here.]("http://blogs.adobe.com/penguin.swf/") 

[ATTACH]12744[/ATTACH]

---

### Post by tkrisz on 2006-07-21
I have the flashplayer, thx for the hints.
As an extra step I had to copy npwrapper.libflashplayer.so from /usr/lib/mozilla/plugins to /usr/lib/firefox/plugins.
Note, that i don't see nspluginwrapper among the plugins at about:plugins (seems like it's no problem, but somebody wrote that there it is.)
I tested at youtube and it was working quite well for a while, but then freezed.
So what is the suspected reason of the freezing?

---

### Post by tkrisz on 2006-07-24
Got this in the term, when my firefox freezed (i think i've strated it from term this time...)

The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 6450 error_code 3 request_code 61 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by tkrisz on 2006-07-29
I don't understand, if npwrapper.libflashplayer.so is in /usr/lib/firefox/plugins or /home/username/mozilla/plugins it freezes, but if not firefox does not find the plugin.

---

### Post by iGold on 2006-07-29
> **superm1 said:**
> If you open up about:config, there is an option plugin.expose_full_path.
If you set this to true, then about:plugins will tell you exactly where its getting its plugins from.
Yes, but also it dereferences symlinks, so if you have in /usr/lib/firefox/plugins/ some npwrapper.*.so *symlink* points to /usr/lib/mozilla/plugins/ you will see in about:plugins full path to /usr/lib/mozilla/plugins/npwrapper.*.so But really it was loaded from /usr/lib/firefox/plugins/ directory.

> **JoWilly said:**
> Ahhaa !

Yes you are right :)

These are all the paths of all my installed plugins, as now shown by about : plugins (in order of appearance):

/usr/lib/mozilla/plugins/npwrapper.nphelix.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox/plugins/libtotem_mozilla.so
/usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so

Edit: so this would most probably mean that the install steps can be simplified as there should be no need for the links in /usr/lib/firefox ... good :)
How can firefox load plugin from /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/ ??? Is it has so strange plugin search path? ;-)
It's just dereferenced symlink from firefox plugin directory. And so - no, install steps can't be simplified.

> **JoWilly said:**
> So make sure, that** if you are running firefox64 all 32bit plugins (flash, realplayer,...) are removed from the plugins directories** (/usr/lib/firefox/plugins, the home dir, etc...).
You are right here or you will get errors as below:

> **superm1 said:**
> Also a FIY.  /usr/lib/mozilla/plugins/ is in the search path for plugins for FF.  So even if 32 bit plugins were just there, it wouldn't matter.  FF will spit an error back to a terminal but still work.

```
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: cannot open shared object file: No such file or directory]
```

But my firefox from ubuntu doesn't search in /usr/lib/mozilla/plugins/ because I did not get such messages (I have 32-bit flash plugin in this dir). But when plugin was in /usr/lib/firefox/plugins/ the messages were.
Also you have full path here so I think you have *symlinks* to this plugins somewhere in FF plugin search path.

---

### Post by tkrisz on 2006-08-06
Seriously, what's wrong at me?
Still freezes.

krisz@notata:/usr/lib/mozilla/plugins$ ls -al
összesen 2160
drwxr-xr-x 2 root root    4096 2006-07-21 14:30 .
drwxr-xr-x 3 root root    4096 2006-07-21 13:53 ..
-rwxr-xr-x 1 root root 2154768 2006-07-21 13:57 libflashplayer.so
-rwxr-xr-x 1 root root   39840 2006-07-21 14:35 npwrapper.libflashplayer.so
lrwxrwxrwx 1 root root      55 2006-07-21 14:30 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/npwrapper.so

krisz@notata:/usr/lib/firefox/plugins$ ls -al
összesen 20
drwxr-xr-x 2 root root  4096 2006-08-06 19:50 .
drwxr-xr-x 5 root root  4096 2006-08-06 14:36 ..
-rw-r--r-- 1 root root 11600 2006-07-31 17:59 libunixprintplugin.so
lrwxrwxrwx 1 root root    52 2006-08-06 19:50 npwrapper.libflashplayer.so -> /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

[email]krisz@notata:~/.mozi[/email]lla/plugins$ ls -al
összesen 8
drwxr-xr-x 2 krisz krisz 4096 2006-07-29 14:22 .
drwx------ 4 krisz krisz 4096 2006-07-08 20:22 ..
lrwxrwxrwx 1 krisz krisz   49 2006-07-08 20:22 nphelix.so -> /home/krisz/Desktop/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 krisz krisz   50 2006-07-08 20:22 nphelix.xpt -> /home/krisz/Desktop/RealPlayer/mozilla/nphelix.xpt

about:plugins

Shockwave Flash

    Fájlnév: /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
    Shockwave Flash 7.0 r63

MIME-típus 	Leírás 	Kiterjesztés 	Engedélyezve
application/x-shockwave-flash 	Shockwave Flash 	swf 	Igen
application/futuresplash 	FutureSplash Player 	spl 	Igen

---

### Post by superm1 on 2006-08-06
I still run into freezes myself.  I don't personally think this a good solution yet.  My solution is to flashblock everything until I come to a site NEEDING flash, and then only use it briefly.

---

### Post by jmono75 on 2006-09-06
> **superm1 said:**
> I still run into freezes myself.  I don't personally think this a good solution yet.  My solution is to flashblock everything until I come to a site NEEDING flash, and then only use it briefly.
Hello, superm1.
Try this.

LANG="C" firefox

My $LANG was "ja_JP.EUC-JP" .
It ran into freeze.
I evaded from freeze by this.

---

### Post by superm1 on 2006-09-06
> **jmono75 said:**
> Hello, superm1.
Try this.

LANG="C" firefox

My $LANG was "ja_JP.EUC-JP" .
It ran into freeze.
I evaded from freeze by this.

No difference.  Froze after I opened up my second google video.

---

### Post by Dragonstar on 2006-09-23
I have used that flashblock, watching only needed flashes, and it has worked good enough. But now when I updated Firefox to 1.5.0.7 flashes stopped working. If i try to view the flash behind the flashblock my browser freezes and I have to kill it. Any advices?

---

### Post by Kilz on 2006-09-23
> **Dragonstar said:**
> I have used that flashblock, watching only needed flashes, and it has worked good enough. But now when I updated Firefox to 1.5.0.7 flashes stopped working. If i try to view the flash behind the flashblock my browser freezes and I have to kill it. Any advices?

Yes install my 32bit firefox script/howto and flash will work without freezing anything.

---

### Post by Dragonstar on 2006-09-23
> **Kilz said:**
> Yes install my 32bit firefox script/howto and flash will work without freezing anything.

After some troubles this seems to work great. Thanks! One question though. It looks like some font settings are different than in 64-ver, text seems a little bit different. Although the settings are the same for both browsers when I looked. You know why is that?

---

### Post by Kilz on 2006-09-23
> **Dragonstar said:**
> After some troubles this seems to work great. Thanks! One question though. It looks like some font settings are different than in 64-ver, text seems a little bit different. Although the settings are the same for both browsers when I looked. You know why is that?

It may be that Ubuntu does some setinng up of fonts, the 32bit version is exactly as downloaded from mozilla, just placed in a deb. It has to be this way under the mpl for me to distribute it without a lot of paperwork.

---

### Post by __j__ on 2006-10-13
> **Dragonstar said:**
> I got the same problem. On many pages where there's a flash animation my firefox just freezes. I run firefox in the terminal and when it then freezed i killed it and terminal looked like this:

```
*** NSPlugin Viewer  *** ERROR: failed to receive reply from NPN_GetURLNotify
*** NSPlugin Viewer  *** ERROR: failed to receive reply from NPN_GetURLNotify
Killed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 541 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

What's the deal here?

It's an issue with flash on xorg with the composite extension enabled, not specific to 64-bit firefox or nspluginwrapper. I ran into this too. There's a bug logged at 
[mozilla.org]("https://bugzilla.mozilla.org/show_bug.cgi?id=304370").

To prevent the error, edit your /etc/X11/xorg.conf file and make certain your color depth is set to 24. This should prevent the X error.

If you still see NSPlugin Wrapper errors on the console when firefox loads a flash object, start firefox with the following environment variable:

```
XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/firefox
```

If this solves the issue, an easy persistent fix is to create the script /usr/local/bin/firefox using the line above. As long as /usr/local/bin comes before /usr/bin in your PATH, you should be good to go.

---

### Post by russianpirate on 2006-10-13
So you don't recommend using nspluginwrapper at all?
Anyone uses it and has no problems?

PS: I'm not planning to use firefox 32, because i had glitches with firefox 2.0rc2 32-bit like black flashes, crashes, and lag

---

### Post by hecato on 2006-10-15
I have tryied to install it, but in the console, when I do "about:plugins" I get the following...

> 
firefox
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: cannot open shared object file: No existe el fichero ó directorio]


---

### Post by __j__ on 2006-10-17
That looks like you're trying to load the 32-bit plugin. Unless you've named the symlink differently than the 64-bit plugin wrapper, the file you want in your plugins path is the one named "npwrapper.libflashplayer.so".

---

### Post by Corbelius on 2006-10-18
It's more stable 0.9.90.3 version on Epiphany browser...

---

### Post by VFiend on 2006-10-18
The Flash 9 beta seems to work great using the 0.9.90.3 nspluginwrapper debs, too

---

### Post by zeroc on 2006-10-19
Hi folks,

I've tried to get it working. FF freezes as soon as I try to view a flash movie. I'm getting the following message (Flash Player 7.x):
---------------
*** NSPlugin Viewer  *** ERROR: failed to receive reply from NPN_GetURLNotify
Killed
---------------
I've also tried Flash Player 9.x beta:
---------------
*** NSPlugin Viewer  *** WARNING: unhandled variable 15 for NPN_GetValue
*** NSPlugin Viewer  *** WARNING: unhandled variable 15 for NPN_GetValue
*** NSPlugin Viewer  *** ERROR: failed to receive reply from NPN_GetURLNotify
*** NSPlugin Viewer  *** WARNING: unhandled variable 15 for NPN_GetValue
Killed
--------------

Any ideas?
(I've also tried XLIB_SKIP_ARGB_VISUALS=1 and LANG="C" suggestions, without any effect...)
Ubuntu 6.06 64-Bit with 64-Bit Java, Firefox 1.5.0.7

---

### Post by __j__ on 2006-11-08
When installing the Flash plugin, if you're missing a package dependency the errors/warnings displayed on the console aren't very helpful. I believe the following packages will do:

```
sudo apt-get install gsfonts gsfonts-x11 ia32-libs ia32-libs-gtk lib32asound2 linux32
```

With this you may still get occasional warnings on the console (*NPP_GetValue* and *NPN_GetValue* warnings aren't uncommon) but these don't appear harmful if infrequent.

---

### Post by xopher on 2006-11-23
For version **0.9.90.4** check out my post:

[http://ubuntuforums.org/showpost.php?p=1792581&postcount=27](http://ubuntuforums.org/showpost.php?p=1792581&postcount=27)

---

