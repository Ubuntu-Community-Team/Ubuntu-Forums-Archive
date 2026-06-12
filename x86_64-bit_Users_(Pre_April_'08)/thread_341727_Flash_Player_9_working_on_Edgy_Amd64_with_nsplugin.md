---
title: "Flash Player 9 working on Edgy Amd64 with nspluginwrapper"
date: 2007-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by pinguin on 2007-01-19
[COLOR=Black]**[SIZE=3]Please, if you are running Gutsy (K/Ubuntu 7.10) stop and read this section. With any flavor of Gutsy you should be able to install "flashplugin-nonfree"[/SIZE]**[/COLOR][COLOR=Black]**[SIZE=3] with apt-get or synaptic/adept and nspluginwrapper should also install and automatically configure the plugin wrapper. You shouldnt need a script or howto to install it.[/SIZE]**[/COLOR]

After several tests in order to make Flash Player working on Amd64 with nspluginwrapper based on the reading of varies how-to and in occasion of the definitive version of Flash Player 9 I have thought to write this guide, taking cue from the several one how-to that I have read; I synthetize the things that I have made in order to make it to work. 
First of all we must install one series of libraries for compatibility with 32 bit 
Indispensable is to install ia32-libs ia32-libs-gtk linux32 lib32asound2 
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2 
```**Installation of the nspluginwrapper **

_# Alternative n.1: using repository kindly offered by Janvitus: _
add the respository and update the sources list: [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)
installation:
```
sudo apt-get install nspluginwrapper gsfonts-x11
```# end of Alternative 1 

_# Alternative n. 2:downloading the last version of .rpm files the Plugin and Viewer from his site and debianizing with alien _
Download:
[http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.2-1.x86_64.rpm](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.2-1.x86_64.rpm) 
[http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm) 
install alien 
```
sudo apt-get install alien 
```Let&#8217;s go into the folder with the downloaded .rpm files (in my case /home/maurizio) 
And convert the packages 
```
sudo alien nspluginwrapper-0.9.91.2-1.x86_64.rpm 
sudo alien nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm 
```And install the packages 
```
sudo dpkg -i nspluginwrapper-0.9.91.2-1.x86_64.deb 
sudo dpkg -i nspluginwrapper-i386-0.9.91.2-1.x86_64.deb 
```#end of Alternative n. 2 

**Download flash player 9 from Adobe site **[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) 

WARNING: At this point, make sure to close every open browser. 

Let&#8217;s go into the folder with the downloaded file and untar it
the &#8220;install_flash_player_9_linux&#8221; folder has been created  
move the 2 files &#8220;libflashplayer.so&#8221; and &#8220;flashplayer.xpt&#8221; from that folder into the /usr/lib/mozilla/plugins folder 
at last give the command 
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
```if it is all right, it would have to return to the prompt without no messages

in the folder .mozilla/plugins/ in our /home we can see the file &#8220;npwrapper.libflashplayer.so&#8221;, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works] 
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]

Now, (if I remembered to write back all steps) it would work,
try going on [http://www.youtube.com/](http://www.youtube.com/) and watch a video. 

In my system it works, for stability we will see.

Automatically translated text: [http://www.google.com/intl/en/help/faq_translation.html](http://www.google.com/intl/en/help/faq_translation.html)
from: [http://forum.ubuntu-it.org/index.php/topic,56771.0.html](http://forum.ubuntu-it.org/index.php/topic,56771.0.html)

---

### Post by NotPhil on 2007-01-20
I picked up NSPluginWrapper from its home page and converted it to a Debian package with Alien. (Alien told me it skipped converting the scripts.) I installed it with dpkg, and npconfig and npwrapper.so showed up in /usr/lib/nspluginwrapper/x86_64/linux.

I got the Flash plug-in from its site and pulled out libflashplayer.so and flashplayer.xpt. I ran sudo nspluginwrapper -i on libflashplayer.so and was told ...

> *** NSPlugin Viewer *** preloader not found
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: libflashplayer.so is not a valid NPAPI plugin

... after installing ia32-libs, ia32-libs-gtk, lib32asound2, and linux32 and logging out, I ran sudo nspluginwrapper -i on libflashplayer.so again and was told ...

> *** NSPlugin Viewer  *** ERROR: libflashplayer.so: cannot open shared object file: No such file or directory
*** NSPlugin Viewer  *** ERROR: libflashplayer.so: cannot open shared object file: No such file or directory
nspluginwrapper: libflashplayer.so is not a valid NPAPI plugin

Anyone know what's wrong?

---

### Post by je1117 on 2007-01-21
hmmm...all I did was install firefox32 (1.5), used the upgrade install to get firefox32 (2.0). I then downloaded the newest flashinstall.tar.gz, and extracted flashplayer.xpt and libflashplayer.so to /usr/lib32/firefox32/plugins.

Java and flash work fine for me. :p

---

### Post by NotPhil on 2007-01-21
> **je1117 said:**
> hmmm...all I did was install firefox32 [and install the plug-ins.]

So, all I need to do is install the 32-bit version of Firefox? Are you sure it will run on a 64-bit machine?

I only ask because this is my third Linux distribution, and I've had problems with either my video card (which has an NVIDIA instruction set) or my processor (a 64-bit AMD, with a really slow data bus, but I couldn't find anything else at the electronics stores). 

I really don't want to go back to a Mac or a Wintel Box, but I'd like to be able to use Flash and Java. I'm sure if I were really patient, Adobe and Sun would come out with 64-bit versions of both of those plug-ins, but I'd rather get them working before the next development cycle comes around.

---

### Post by pinguin on 2007-01-21
> **NotPhil said:**
> 
......
Anyone know what's wrong?

Sure you followed step by step my guide?

---

### Post by pinguin on 2007-01-21
> **NotPhil said:**
> So, all I need to do is install the 32-bit version of Firefox? Are you sure it will run on a 64-bit machine?
....

Yes, you can!
You also can install a complete 32bit version of Ubuntu in your 64bit PC.
Or, first of all you can try my guide to install flash plugin in your 64bit PC with Firefox
If it works fine for you.....
bye

---

### Post by janfsd on 2007-01-21
Maybe for stability you should consider installing the flasblock addon, I am using it and so far no crashes because of flash.

---

### Post by clueless on 2007-01-21
This worked like a charm. Finally, flash on my 64bit firefox! Thank you!

---

### Post by Lowfront on 2007-01-21
lowfront@lowfront-x60:~$ sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

---

### Post by Kilz on 2007-01-21
> **NotPhil said:**
> So, all I need to do is install the 32-bit version of Firefox? Are you sure it will run on a 64-bit machine?



Yes, you can install 32bit firefox on a Ubuntu amd64 install. There are howto's that you can follow, as long as you can read then cut and paste its simple. There are also install scripts that can do it for you.

---

### Post by NotPhil on 2007-01-21
> **pinguin said:**
> Or, first of all you can try my guide to install flash plugin in your 64bit PC with Firefox

It looks like nspluginwrapper needs a couple [more libraries]("http://ubuntuforums.org/showpost.php?p=2011260&postcount=26") than the ones you mentioned to work. It also looks like nspluginwrapper is [kinda flakey]("http://ubuntuforums.org/showthread.php?t=269170"). I think I'll try installing the 32-bit version of Firefox from the Mozilla site.

---

### Post by Lowfront on 2007-01-21
anyone have any idea's here


lowfront@lowfront-x60:~$ sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs

---

### Post by NotPhil on 2007-01-21
> **Lowfront said:**
> E: Couldn't find package ia32-libs

It shows up when I use the Synaptic Package Manager. Try the GUI and see if you can install it that way. The package says it's maintained by the Ubuntu Core Developers, so I wouldn't think you'd need to add any repositories to find it.

---

### Post by pinguin on 2007-01-21
> **clueless said:**
> This worked like a charm. Finally, flash on my 64bit firefox! Thank you!

I'm happy my work helped you =D> 
bye

---

### Post by Lowfront on 2007-01-21
> **NotPhil said:**
> It shows up when I use the Synaptic Package Manager. Try the GUI and see if you can install it that way. The package says it's maintained by the Ubuntu Core Developers, so I wouldn't think you'd need to add any repositories to find it.

I'm sorry but what do you mean by try to GUI?

---

### Post by pinguin on 2007-01-21
> **Lowfront said:**
> I'm sorry but what do you mean by try to GUI?
I think he means Synaptic Package Manager
Are you sure you have main repository enabled?

---

### Post by Lowfront on 2007-01-21
I assume...How do I know for sure?

could it not work because I don't have the amd version but the other 64bit version?

---

### Post by pinguin on 2007-01-21
> **Lowfront said:**
> I assume...How do I know for sure?
Open /etc/apt/sources.list with gedit
if you have a row like this (without # at the beginnig)
```
deb http://archive.ubuntu.com/ubuntu/ edgy-updates [COLOR="Red"]main[/COLOR] restricted universe multiverse

```
It is enabled
look if there are universe multiverse, too

---

### Post by Lowfront on 2007-01-21
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by Lowfront on 2007-01-21
?

---

### Post by HotFoot on 2007-01-22
Your instructions worked for me.  This is the first time I've seen the 64-bit firefox play flash.  It's nice to see progress being made.

---

### Post by pinguin on 2007-01-22
> **Lowfront said:**
> deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
.........


take a look at [COLOR="Red"]Release i386[/COLOR] in your output
It seems you installed a i386(=32bit) system
this section is for x86_64 users and my guide is for 64bit version of firefox!
On 32bit system flash player works without this workaround
take a look at some wiki page
bye

---

### Post by pinguin on 2007-01-22
> **HotFoot said:**
> Your instructions worked for me.  This is the first time I've seen the 64-bit firefox play flash.  It's nice to see progress being made.

I am happy hearing this

---

### Post by John Jason Jordan on 2007-01-22
I am on Edgy amd-64. I decided to give pinguin's method a try (from the instructions in post 1 of this thread). I got as far as adding Janvitus' repository, but [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) gives me a 404 error (page not found). In the past I have tried to use alien and it has never worked, so I am leery of trying the second alternative. Is there any place I can get the .deb file?

---

### Post by pinguin on 2007-01-22
> **John Jason Jordan said:**
> I am on Edgy amd-64. I decided to give pinguin's method a try (from the instructions in post 1 of this thread). I got as far as adding Janvitus' repository, but [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) gives me a 404 error (page not found). In the past I have tried to use alien and it has never worked, so I am leery of trying the second alternative. Is there any place I can get the .deb file?

first, try again the method with alien, it is enough safe

the link [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) works from my PC
howerver these are the instructions:
> To navigate into repository: [http://janvitus.cabspace.com/ubuntu/](http://janvitus.cabspace.com/ubuntu/)

This repository is for the Ubuntu Linux 64bit distribution, at this moment Edgy Eft AMD64.
To add my GPG-key to your keyrings from console:

    gpg &#8211;keyserver hkp://wwwkeys.eu.pgp.net &#8211;recv-keys 2C4C84CC && gpg &#8211;export &#8211;armor 2C4C84CC | sudo apt-key add -

Insert root password.
To add my repository in your APT system, insert this string in your sources.list.



For Edgy Eft:

    deb [http://janvitus.cabspace.com/ubuntu/](http://janvitus.cabspace.com/ubuntu/) edgy-janvitus main-amd64

From console: sudo apt-get update

---

### Post by Corbelius on 2007-01-22
> **John Jason Jordan said:**
> . I got as far as adding Janvitus' repository, but [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) gives me a 404 error (page not found)

Sorry, hosting problems :)

---

### Post by Lowfront on 2007-01-22
> **pinguin said:**
> take a look at [COLOR="Red"]Release i386[/COLOR] in your output
It seems you installed a i386(=32bit) system
this section is for x86_64 users and my guide is for 64bit version of firefox!
On 32bit system flash player works without this workaround
take a look at some wiki page
bye

Hmm.. Thats not right.  I had the 32bit version for awhile then decided to install the 64bit version.  I'm positive that I downloaded the 64bit version for this install.  

wtf....

---

### Post by John Jason Jordan on 2007-01-22
> **pinguin said:**
> first, try again the method with alien, it is enough safe
the link [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) works from my PC
howerver these are the instructions:
First, the janvitus site is now working, as Corbelius noted, evidently there was a temporary hosting problem.

I added the repository to /etc/sources.list easily enough, but adding the key does not work:

jjj@Devil5:~$ gpg –keyserver hkp://wwwkeys.eu.pgp.net –recv-keys 2C4C84CC && gpg –export –armor 2C4C84CC | sudo apt-key add -
usage: gpg [options] [filename]

I also sudo-ed the command, but got the same results. Then I decided I'd just use Synaptic to add the key. But Synaptic for Edgy has changed. When I click on Settings > Repositories I now get a tabbed window. The Repositories tab shows the new repository, but you can't add a key from that tab. Instead there is an Authentication tab where the keys are displayed. However, there is no Add button on that tab. The only option is Import Key File. If you click on it you get a file browser window where you are supposed to select a key file to import, and I have no idea where that is. I looked in /etc/apt thinking that perhaps now there is a file like the sources.list file. There are a number of files there, but nothing that looked like a list of keys.

So then I clicked on the Help button on the tabbed window in Synaptic and it said the syntax for the command line should be:

jjj@Devil5:~$ gpg -recv-keys --keyserver hkp://wwwkeys.eu.pgp.net 2C4C84CC && gpg –export –armor 2C4C84CC | sudo apt-key add -

But that got me:

gpg: can't open `2C4C84CC'

So at least I got the options in the command line correct, but something is still wrong. Perhaps the keyserver is down?

---

### Post by janfsd on 2007-01-22
> **John Jason Jordan said:**
> First, the janvitus site is now working, as Corbelius noted, evidently there was a temporary hosting problem.

I added the repository to /etc/sources.list easily enough, but adding the key does not work:

jjj@Devil5:~$ gpg –keyserver hkp://wwwkeys.eu.pgp.net –recv-keys 2C4C84CC && gpg –export –armor 2C4C84CC | sudo apt-key add -
usage: gpg [options] [filename]

I also sudo-ed the command, but got the same results. Then I decided I'd just use Synaptic to add the key. But Synaptic for Edgy has changed. When I click on Settings > Repositories I now get a tabbed window. The Repositories tab shows the new repository, but you can't add a key from that tab. Instead there is an Authentication tab where the keys are displayed. However, there is no Add button on that tab. The only option is Import Key File. If you click on it you get a file browser window where you are supposed to select a key file to import, and I have no idea where that is. I looked in /etc/apt thinking that perhaps now there is a file like the sources.list file. There are a number of files there, but nothing that looked like a list of keys.

So then I clicked on the Help button on the tabbed window in Synaptic and it said the syntax for the command line should be:

jjj@Devil5:~$ gpg -recv-keys --keyserver hkp://wwwkeys.eu.pgp.net 2C4C84CC && gpg –export –armor 2C4C84CC | sudo apt-key add -

But that got me:

gpg: can't open `2C4C84CC'

So at least I got the options in the command line correct, but something is still wrong. Perhaps the keyserver is down?

This should work:
```
wget http://janvitus.cabspace.com/ubuntu/2C4C84CC.gpg -O- | sudo apt-key add -
```

---

### Post by John Jason Jordan on 2007-01-22
> **janfsd said:**
> This should work:
```
wget http://janvitus.cabspace.com/ubuntu/2C4C84CC.gpg -O- | sudo apt-key add -
```
Thanks!

It did work. I got it installed. Then I fired up Firefox and went to youtube.com. Sure enough, the videos played! Great! I also tried Opera, and even though I did nothing to enable flash in Opera (I don't even know how it handles plugins), youtube worked fine in Opera as well!

For further testing I have a bookmark to a site for testing plugins: [http://kb.mozillazine.org/Testing_plugins](http://kb.mozillazine.org/Testing_plugins)
I went there and tried some of the pages. None of them would work. Worse, suddenly Firefox was not responding. I have a utility to kill non-responding apps, so I used it. Then I tried to relaunch Firefox, but I got a popup that said "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

Note: This experience is with Firefox 2.0 on Ubuntu Edgy amd64.

So then I tried top, but it didn't list Firefox as running. Finally I logged out and back in again. After logging back in again finally Firefox would restart. In fact, it asked if I wanted to resume, and I said yes. 

When it came back up I went back to youtube.com, but now nothing works. :(

However, I just launched Opera again and youtube is still working in Opera.

---

### Post by pinguin on 2007-01-23
Have you done all these steps?

> move the 2 files “libflashplayer.so” and “flashplayer.xpt” from that folder into the /usr/lib/mozilla/plugins folder
at last give the command
Code:

nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

if it is all right, it would have to return to the prompt without no messages

in the folder .mozilla/plugins/ in our /home we can see the file “npwrapper.libflashplayer.so”, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works]
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]

try they again

---

### Post by Corbelius on 2007-01-23
> **John Jason Jordan said:**
> First, the janvitus site is now working, as Corbelius noted, evidently there was a temporary hosting problem.

I added the repository to /etc/sources.list easily enough, but adding the key does not work:

jjj@Devil5:~$ gpg –keyserver hkp://wwwkeys.eu.pgp.net –recv-keys 2C4C84CC && gpg –export –armor 2C4C84CC | sudo apt-key add -
usage: gpg [options] [filename]

I also sudo-ed the command, but got the same results. Then I decided I'd just use Synaptic to add the key. But Synaptic for Edgy has changed. When I click on Settings > Repositories I now get a tabbed window. The Repositories tab shows the new repository, but you can't add a key from that tab. Instead there is an Authentication tab where the keys are displayed. However, there is no Add button on that tab. The only option is Import Key File. If you click on it you get a file browser window where you are supposed to select a key file to import, and I have no idea where that is. I looked in /etc/apt thinking that perhaps now there is a file like the sources.list file. There are a number of files there, but nothing that looked like a list of keys.

So then I clicked on the Help button on the tabbed window in Synaptic and it said the syntax for the command line should be:

jjj@Devil5:~$ gpg -recv-keys --keyserver hkp://wwwkeys.eu.pgp.net 2C4C84CC && gpg –export –armor 2C4C84CC | sudo apt-key add -

But that got me:

gpg: can't open `2C4C84CC'

So at least I got the options in the command line correct, but something is still wrong. Perhaps the keyserver is down?

Syntax errors, see here: [http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

---

### Post by John Jason Jordan on 2007-01-23
> **pinguin said:**
> Have you done all these steps?
try they again
Yes, I did all of them and they all worked properly. And the files are in the correct folders. When I go to about:plugins it lists Flash 9 as installed. But when I go to youtube.com it says I either have Java turned off (it is turned on) or that I have an old version of Flash.

Note that it did work at first right after installing it. It broke only after Firefox hung on another site and I had to kill it. After that it no longer works. Repeating the instructions now will not get it back.

However, this exercise has accomplished one thing for me: I also have Opera installed and flash never worked there either. But now it does. I can go to youtube.com with Opera and view videos just fine now. 

I suspect the difference is that Opera was installed from the static i386 .deb with --force-architecture, where Firefox is the 64-bit version 2.0 under Edgy. Still, it's odd that it worked at first and now I can't fix it.

---

### Post by mister mick on 2007-01-23
I got everything done to the bottom of the list, but there is no /plugins directory in .mozilla, just a /firefox directory.  I didn't get any error from the nswrapper, it just returned me to the command prompt.

---

### Post by Eddie Mac on 2007-01-26
> **pinguin said:**
> 
Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works] 
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]


I had to copy it to **/usr/lib32/firefox32/plugins** for it to work (FYI to anyone who might be having the same problem I was having getting this to work).

---

### Post by saris on 2007-01-27
This worked out great for me as well! Thank you very much for the post.

---

### Post by Doug11 on 2007-01-27
> **John Jason Jordan said:**
> I am on Edgy amd-64. I decided to give pinguin's method a try (from the instructions in post 1 of this thread). I got as far as adding Janvitus' repository, but [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) gives me a 404 error (page not found). In the past I have tried to use alien and it has never worked, so I am leery of trying the second alternative. Is there any place I can get the .deb file?

I had problems with the first alternative as well. I tried the second one and it worked first try.

---

### Post by Footer on 2007-01-28
Thanks for the post.  2nd alternative worked flawlessly for me.

:)

---

### Post by Guardia Republicano on 2007-01-29
It works! Thanks. :lolflag: 

I use Mozilla Firefox 2.0 for 64 bits.

I could not install nspluginwrapper-i386 from repository but it works anyway.

Regards,
Pablo from Argentina.

---

### Post by Footer on 2007-01-29
I spoke too soon.  After restarting the machine, it no longer works.  I seem to have the same problem as John Jason Jordan.  Anyone else?  And if so, did you come up with a fix?

Thanks.

---

### Post by John Jason Jordan on 2007-01-29
> **Footer said:**
> I spoke too soon.  After restarting the machine, it no longer works.  I seem to have the same problem as John Jason Jordan.  Anyone else?  And if so, did you come up with a fix?
I never found a fix. After I discovered that it did make Flash work in Opera that I also have installed, I decided that was good enough. If a site requires Flash, I'll just use Opera. I installed Opera with the 32-bit static deb, so that may be why it works. But having said that, the other day I used Opera to view a Flash demonstration of Beryl. Afterwards I left it running. Later that day I decided to close Opera, and when I clicked to close it the entire computer froze up -- mouse and keyboard dead. So now I'm leery of the whole thing.

It's weird that Flash worked fine on Firefox 2.0 when I first installed it, but after shutting down and restarting it never worked again.

---

### Post by pinguin on 2007-01-29
> **Footer said:**
> I spoke too soon.  After restarting the machine, it no longer works.  I seem to have the same problem as John Jason Jordan.  Anyone else?  And if so, did you come up with a fix?

Thanks.
Try this:
move the 2 files “libflashplayer.so” and “flashplayer.xpt” from /usr/lib/mozilla/plugins folder to /usr/lib/firefox/plugins folder
then in terminal run:
nspluginwrapper -v -a -i

let me know

---

### Post by Strangerdave on 2007-01-29
So I wanted to try this out and got the section where I had to install nspluginwrapper, but keep on getting this message after I  add the repository..

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  nspluginwrapper
E: Package nspluginwrapper-i386 has no installation candidate

```

What does this mean?  And how can I go about fixing it?

-SD-

---

### Post by pinguin on 2007-01-29
> **Strangerdave said:**
> So I wanted to try this out and got the section where I had to install nspluginwrapper, but keep on getting this message after I  add the repository..

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  nspluginwrapper
E: Package nspluginwrapper-i386 has no installation candidate

```

What does this mean?  And how can I go about fixing it?

-SD-

Janvitus changed the repository
now simply run:
```
sudo apt-get install nspluginwrapper gsfonts-x11
```

I'll go change first post!

---

### Post by heinkel_111 on 2007-01-29
Hi I just wanted to notify that I followed method 2 yesterday, but had problems locating the repositories, I got a 302 found error whatever that means. I browsed to the repos using my trusty konqueror instead, downloaded the deb.. and used  mc to make a manual install. 

The pluginwrapping works for firefox, but I cannot get it to work in Konqueror. And I would like to get it to work in Konqueror. Can someone report if they have used these methods to get flash on 64 bit konqueror in kubuntu edgy 6.10? (KDE 3.5.5/Konqueroror 3.5.5)

I read in the nspluginwrapper release notes that this may require a special konqueror with fixed npapi headers, but .... what is your experience?

---

### Post by John Jason Jordan on 2007-01-29
> **pinguin said:**
> Try this:
move the 2 files “libflashplayer.so” and “flashplayer.xpt” from /usr/lib/mozilla/plugins folder to /usr/lib/firefox/plugins folder
then in terminal run:
nspluginwrapper -v -a -i
let me know
That worked! After doing the above I could watch videos on youtube.com again!

But then I shut down and restarted Firefox, and it was broken again. :(

So (acting on a hunch) without restarting Firefox, I ran again just the last command, "nspluginwrapper -v -a -i," and it started working again. :)

Not sure what that means.

---

### Post by Strangerdave on 2007-01-29
Thanks for fixing the syntax, but I have another question.  I do apologize I am a n00b at this and am muddling through it all...

When I install the deb packages this is a message I get:

```
dpkg: error processing nspluginwrapper_0.9.91.2-1.x86_64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 nspluginwrapper_0.9.91.2-1.x86_64.deb

```

Any an all help is greatly appreciated during this time of learning curve :( 

-SD-

---

### Post by pseudonym on 2007-01-29
> **Strangerdave said:**
> Any an all help is greatly appreciated during this time of learning curve :( 
My advice is to dump nspluginwrapper and use flash/java etc. with 32-bit Firefox running with ia32-libs. Why? Because the wrapper is buggy and inevitably breaks, and when you go the 32-bit Firefox route web browsing on Ubuntu 64 becomes a non-problem.

For further info see posts 7 & 9 in [this thread]("http://www.ubuntuforums.org/showthread.php?p=1823857&highlight=tall-male#post1823857"). I recommend the first of those methods because you can use the most up-to-date Firefox as it gets released.

---

### Post by Footer on 2007-01-31
> **pinguin said:**
> Try this:
move the 2 files “libflashplayer.so” and “flashplayer.xpt” from /usr/lib/mozilla/plugins folder to /usr/lib/firefox/plugins folder
then in terminal run:
nspluginwrapper -v -a -i

let me know

That fixes it.  For how long, I don't know.  But it's not too much trouble to run that command so I'll go with it for now!

Thanks!

---

### Post by jariy on 2007-02-01
I don't know is it me or the plugin but flash and acroread stops working after a while and the only way to get it working again is to restart the browser (ff 2.0).

For instance I can watch a tens of youtube videos and later that day all I see is a white box where the flash should be.

I have the latest pluginwrapper (0.9.91.2) and Flash 9.0 r31

---

### Post by Corbelius on 2007-02-01
> **jariy said:**
> 

For instance I can watch a tens of youtube videos and later that day all I see is a white box where the flash should be.



It's a bug, refresh the page.

---

### Post by Scarlett on 2007-02-01
> if it is all right, it would have to return to the prompt without no messages

in the folder .mozilla/plugins/ in our /home we can see the file “npwrapper.libflashplayer.so”, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works]
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]

Weird.  I returned to the prompt with no messages.... so far, so good.  But I couldn't find any folders in /home, never say an "nwrapper.libflashplayer.so" and therefore couldn't copy it anywhere.  Frustrating.  I've been at this for quite a few hours now and I'm becoming increasingly upset with Adobe for not just working with us to make a plug-in that just works.  

Anyway... because I'm a masochist and I wanted to see the little message from youtube, taunting me to install their damn plug-in, (I'm trying, I'm trying) I went to the site and LO AND BEHOLD.... IT WORKED!  Hot damn, I've finally got a 64 bit version of FF that works!

Many, many thanks for posting this, pinguin.  Oh geez, I've got a weeks worth of Daily Show to catch up on...

---

### Post by Scarlett on 2007-02-01
I spoke too soon.  Youtube works but Comedy Central doesn't.  Guess I really do need to copy this non-existent file somewhere.  :(

---

### Post by jariy on 2007-02-02
> **Corbelius said:**
> It's a bug, refresh the page.

I think I found the "bug" it was the Flashblock addon and btw refreshing the page didn't help. I still have some font (or encoding) issues with acroread. I attached two screenshots which speak from themselves. Acroread is 7.0.9, I also tried 7.0.1 and 7.0.0 IIRC.

---

### Post by John Jason Jordan on 2007-02-02
> **Footer said:**
> That fixes it.  For how long, I don't know.  But it's not too much trouble to run that command so I'll go with it for now! Thanks!
I now have a workaround that enables me to have flash working always in 64-bit Firefox 2.0, even after shutting it down and restarting it. First, I did the following per pinguin's instructions:
```
move the 2 files “libflashplayer.so” and “flashplayer.xpt” from /usr/lib/mozilla/plugins folder to /usr/lib/firefox/plugins folder
then in terminal run:
nspluginwrapper -v -a -i
```
After doing that it worked great, but the minute I shut down Firefox and restarted it, flash no longer worked. Eventually I learned all I needed to do is run the last line as a command in a terminal. Even if Firefox was already launched, that was enough to get it to work again.

So I made myself a bash script that runs the above command and then launches Firefox. To emulate what I did, open Gedit (or whatever you use for a text editor) and paste in the following lines:
```
#!/bin/bash
nspluginwrapper -v -a -i
firefox
```
Save the file as firefox_launch_script in your home folder. Open Nautilus, right click on the file and select Properties. In the Properties window check on the box to make it an executable file.
Now change the launch command in your launch menu item or icon on the panel that you use to launch Firefox. Where it says "firefox %u" change it to read "/home/<your_user_name>/firefox_launch_script."
From now on when you click to launch Firefox it will run the command first, then launch Firefox.
It's kind of a clunky workaround, but it does work and Flash is always working now in 64-bit Firefox.

---

### Post by datr on 2007-02-03
That works great John, thanks.

---

### Post by mjskia1 on 2007-02-03
> **mister mick said:**
> I got everything done to the bottom of the list, but there is no /plugins directory in .mozilla, just a /firefox directory.  I didn't get any error from the nswrapper, it just returned me to the command prompt.

I've got the same problem -- anyone know where to find it?

---

### Post by one_stinky_bum on 2007-02-07
Works like magic - Edgy + AMD X2 64 + 64bit FF (from automatix) + flash plugin from adobe site. Thanks.

One day, one day we'll get the same ease of use as the 32 bit guys, and they'll be stuck with their 4 Gigs of ram! Well, not that you'll need more than that with firefox.

---

### Post by Cat in a tree on 2007-02-09
> **NotPhil said:**
> I picked up NSPluginWrapper from its home page and converted it to a Debian package with Alien. (Alien told me it skipped converting the scripts.) I installed it with dpkg, and npconfig and npwrapper.so showed up in /usr/lib/nspluginwrapper/x86_64/linux.

I got the Flash plug-in from its site and pulled out libflashplayer.so and flashplayer.xpt. I ran sudo nspluginwrapper -i on libflashplayer.so and was told ...


... after installing ia32-libs, ia32-libs-gtk, lib32asound2, and linux32 and logging out, I ran sudo nspluginwrapper -i on libflashplayer.so again and was told ...


Anyone know what's wrong?
I had the same thing happen  with NSPlugin Viewer *** preloader not found and that libflashplayer.so was not a valid NPAPI plugin.
I saw the same error about scripts with Alien, I redid it with Alien -c and i didn't get the warning about scripts however, after following the rest of the steps I got the same errorl
would sure like help on what to do next........

---

### Post by fastawdtsi on 2007-02-09
Worked perfect for me. Ubuntu Edgy 6.10 x86_64.

Thank you so much for the guide!

---

### Post by andrian.ivanov on 2007-02-10
:)

---

### Post by mc^2 on 2007-02-11
I've got the same problem as John Jason Jordan. When I close firefox or ephy and open it again I need to run ```
nspluginwrapper -a -i
``` (-v is just verbose) to see flash content again (instead of white boxes). 
Does anyone know how to make nspluginwrapper remember its settings (making a shell script to launch firefox works but somehow it doesn't seem to be THE way).
Anyway, thanks for a great guide, I don't have to switch to MSWXP to watch youtube vids:popcorn:.

---

### Post by fussel78 on 2007-02-11
Ciao! 

Quote:
*** NSPlugin Viewer *** preloader not found
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: libflashplayer.so is not a valid NPAPI plugin


You need to 
$sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

then (again)
$sudo dpkg -i nspluginwrapper-i386-0.9.91.2-1.x86_64.deb

and 
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

This time it should work!

Missed out a package in the howto...

Greets from Switzerland,
Fussel

---

### Post by Tom Mann on 2007-02-12
Sun have released JRE for linux X64!! :D

---

### Post by Amurko on 2007-02-13
Great, I can watch youtube on my new Core 2 system for the first time!

On a side note, if anyone affiliated with them is reading this...  is there any chance Automatix can be updated to follow these instructions in installing Flash?

---

### Post by jackrobinson on 2007-02-13
if anyone has installed the package from Janvitus's repository, can he/she post the result of the following command:
```
dpkg -s nspluginwrapper | grep "Depends"
```

---

### Post by John Jason Jordan on 2007-02-13
> **jackrobinson said:**
> if anyone has installed the package from Janvitus's repository, can he/she post the result of the following command:
```
dpkg -s nspluginwrapper | grep "Depends"
```
I installed it with the Janvitus repository. Here is what I got:

jjj@Devil5:~$ dpkg -s nspluginwrapper | grep "Depends"
Depends: lib32gcc1 (>= 1:4.1.1-12), libc6 (>= 2.4-1), libc6-i386 (>= 2.4-1), libglib2.0-0 (>= 2.12.0), libx11-6, libxt6, ia32-libs, ia32-libs-gtk, linux32, lib32asound2, gsfonts-x11

It's working fine, although I had to make a bash script so that it would be reinitiated every time Firefox is launched.

---

### Post by Michelpt on 2007-02-18
Yeap! :)  After trying the huge quantity of tutorials finally I can see youtube.com and [www.thefwa.com](www.thefwa.com) on edgy amd_64!! Thanks a lot! :) ... 

here is that **dpkg -s nspluginwrapper | grep "Depends"**  outputs:
Depends: lib32gcc1 (>= 1:4.1.1-12), libc6 (>= 2.4-1), libc6-i386 (>= 2.4-1), libglib2.0-0 (>= 2.12.0), libx11-6, libxt6, ia32-libs, ia32-libs-gtk, linux32, lib32asound2, gsfonts-x11

---

### Post by r_rehashed on 2007-02-18
both Flash and Java work fine for me. but, firefox sudddenly hangs at times while playing flash videos like those from youtube or google video!

---

### Post by Luk0r on 2007-02-23
Sorry for bumping this thread, but it worked like a charm.  Thanks a lot!

---

### Post by coacharnold on 2007-02-26
YOU RULE!!!!!!!!!!!!!!!!  Worked like a charm ....... THANK YOU THANK YOU SO MUCH!!!!!!!:) :) :) :) :) :)

---

### Post by javaguru on 2007-02-28
Great tutorial, thanks ! works as a charm.. by the way, I run Debian unstable amd64.

---

### Post by djrobthaman on 2007-02-28
Hi,

I was using this guide and my noobness reared its ugly head.  I'm trying to transfer the two files to the mozilla plugin folder but it says I do not have the permissions.  I tried to log out and then log in from startup as "root", but when I do this it gives me a message like "you cannot log in as the administrator from this screen."

How can I get to transfer the files?

Thanks,
Douglas

---

### Post by John Jason Jordan on 2007-03-01
> **djrobthaman said:**
> Hi,

I was using this guide and my noobness reared its ugly head.  I'm trying to transfer the two files to the mozilla plugin folder but it says I do not have the permissions.  I tried to log out and then log in from startup as "root", but when I do this it gives me a message like "you cannot log in as the administrator from this screen."
How can I get to transfer the files?
Because it is built from the ground up as a secure OS the only files a user is allowed to mess with are those in the user's home folder. However, any user who has the password for root can become root, and root can do anything.

There usual way to become root is to type su at a command line, which will prompt you for the root password. In Ubuntu the root account is sort of not there (the explanation is very long), but you can do things as root by using sudo in front of the command. This will prompt you for the root password the same as su.

A simple way around your problem is to launch Nautilus as root. To do so, open a command line (Applications > Accessories > Terminal) and type "sudo nautilus." This will launch an instance of Nautilus with root privileges. Now you can drag and drop files anywhere. BUT BE CAREFUL. Do this only with a piece of paper in front of you and a pen in hand so you can document exactly what files you moved/deleted and how. The folders you are trying to access require root privileges for a reason. Mucking them up can render the system unbootable or create security problems. Having said that, if just want to move the mozilla files the worst that will happen is that Firefox will fail to launch or the plugin won't work. Still, whenever assuming the cloak of root, be careful.

---

### Post by rembert on 2007-03-01
Managed to get flash running now but not with the repository as posted in the first post. Just browsing tot he page [www.janvitus.netsons.org/repository/](www.janvitus.netsons.org/repository/) did the trick:

Instead of adding the repository (to /etc/apt/sources.list)

```
deb http://www.janvitus.netsons.org/repository/ ./
```

I added

```
deb http://janvitus.interfree.it/ubuntu/ edgy-janvitus main-amd64
```

This followed by the 

```
sudo apt-get update
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
sudo apt-get install nspluginwrapper gsfonts-x11
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

And voila, it seems to work perfectly.

NB If your have enabled the root account and are doing this as root, be sure to run nspluginwrapper as the non-root user.

---

### Post by Her Ghost on 2007-03-01
hi, I'm having problems with this.  Has anyone got any ideas?

```
leigh@leigh-desktop:~$ sudo apt-get install nspluginwrapper gsfonts-x11Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package nspluginwrapper**
```

Thanks for any help

---

### Post by c0nv1ct on 2007-03-01
Has anyone been able to apply this technique to getting flash to work in Swiftfox amd64?

I tried following the same steps, but putting the files in /opt/swiftfox/plugins, but it doesn't work :(  Works like a charm in regular firefox though.

---

### Post by Kilz on 2007-03-01
> **c0nv1ct said:**
> Has anyone been able to apply this technique to getting flash to work in Swiftfox amd64?

I tried following the same steps, but putting the files in /opt/swiftfox/plugins, but it doesn't work :(  Works like a charm in regular firefox though.

Swiftfox is non-free. Why would anyone work to make it better?

---

### Post by hodad on 2007-03-02
I get all the way to the last step and get:

 sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflshplayer.so
nspluginwrapper: /usr/lib/mozilla/plugins/libflshplayer.so is not a valid NPAPI plugin


Any suggestions on what I should do? Everything seemed to work OK up to the last step.

Thanks

---

### Post by c0nv1ct on 2007-03-02
> **hodad said:**
> I get all the way to the last step and get:

 sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflshplayer.so
nspluginwrapper: /usr/lib/mozilla/plugins/libflshplayer.so is not a valid NPAPI plugin


Any suggestions on what I should do? Everything seemed to work OK up to the last step.

Thanks

is that a direct copy from your console? if so, you misspelled "libfl**a**shplayer.so"

> **Kilz said:**
> Swiftfox is non-free. Why would anyone work to make it better?

I didn't realize it was non-free.  It didn't seem any faster anyway, i guess i'll ditch it.

---

### Post by Corbelius on 2007-03-02
> **Her Ghost said:**
> hi, I'm having problems with this.  Has anyone got any ideas?

```
leigh@leigh-desktop:~$ sudo apt-get install nspluginwrapper gsfonts-x11Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package nspluginwrapper**
```

Thanks for any help

I have changed repository address, have u update? 

[http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

---

### Post by hodad on 2007-03-02
oooops! Thanks for catching that!.  Still have the same problem, however. Here's what I get:

xxxx@xxxx-desktop:~/Flash_Install/install_flash_player_9_linux$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin
xxxx@xxxx-desktop:~/Flash_Install/install_flash_player_9_linux$

libflashplayer.so is in the subdir where I ran the command.   I guess I'm missing the "preloader", whatever that is.

Any ideas?  Thanks

---

### Post by DuckMan on 2007-03-04
works perfect in my box

AMD64 with feisty fawn

:) thx

---

### Post by Her Ghost on 2007-03-04
> **Corbelius said:**
> I have changed repository address, have u update? 

[http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

Done it!

Thanks - it works beautifully.

One thing I struggled with (after updating the repositories as above) was that the file created did not have permissions that were needed for a standard user to run the plugin, so I had to run

```
sudo chmod 666 npwrapper.libflashplayer.so
```

in the mozilla-firefox/plugins folder, to make sure that it worked (probably pretty obvious, but I'm still learning!).  After this it worked perfectly.

Thanks again

---

### Post by NeilBlanchard on 2007-03-05
Greetings,

> **pinguin said:**
> 
_# Alternative n.1: using repository kindly offered by Janvitus: _
add the respository and update the sources list: [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

I'm a noob -- where is this sources list?

---

### Post by ecs_pf5 on 2007-03-05
It's in /etc/apt/

```

neil@ubuntu:~$ cd /
neil@ubuntu:/$ cd etc
neil@ubuntu:/etc$ cd apt
neil@ubuntu:/etc/apt$ dir
apt.conf    secring.gpg   sources.list~   sources.list.save  trusted.gpg
apt.conf.d  sources.list  sources.list.d  trustdb.gpg        trusted.gpg~
neil@ubuntu:/etc/apt$ sudo vi sources.list
Password:
neil@ubuntu:/etc/apt$

```

BTW - take the URL's and the key stuff direct from the author's site, as close in terms of clicks to his actual 'browse' links as possible ;)

Did you install Dapper or Edgy? I discovered the nspluginwrapper package is only in the Edgy repo & it doesn't seem to play nice with Dapper right now.

---

### Post by Corbelius on 2007-03-06
The new version of nspluginwrapper (0.9.91.3) is in the repository, if upgrade, re-launch "nspluginwrapper -v -a -i" from console.

---

### Post by NeilBlanchard on 2007-03-06
Greetings,

> **ecs_pf5 said:**
> It's in /etc/apt/

```

neil@ubuntu:~$ cd /
neil@ubuntu:/$ cd etc
neil@ubuntu:/etc$ cd apt
neil@ubuntu:/etc/apt$ dir
apt.conf    secring.gpg   sources.list~   sources.list.save  trusted.gpg
apt.conf.d  sources.list  sources.list.d  trustdb.gpg        trusted.gpg~
neil@ubuntu:/etc/apt$ sudo vi sources.list
Password:
neil@ubuntu:/etc/apt$

```

BTW - take the URL's and the key stuff direct from the author's site, as close in terms of clicks to his actual 'browse' links as possible ;)

Did you install Dapper or Edgy? I discovered the nspluginwrapper package is only in the Edgy repo & it doesn't seem to play nice with Dapper right now.

Okay, I'm fine up to sudo vi sources.list -- that seems to open that file, but I can't figure out where/how to paste in the URL, and then how to save it?

I hope I didn't mess it up trying...

BTW, I'm using Edgy (see header).

---

### Post by ecs_pf5 on 2007-03-06
[http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

You need to toggle between command and insert mode to use vi properly (easy once you get used to it but it's a bit strange at first)

---

### Post by RichOlson on 2007-03-06
Option 1 as described by pinguin rendered firefox inoperable for me.  It would not accept input from the keyboard. Removing nspluginwrapper and gsfonts=x11 and restarting firefox restored functionality.

---

### Post by pinguin on 2007-03-07
> **NeilBlanchard said:**
> Greetings,



Okay, I'm fine up to sudo vi sources.list -- that seems to open that file, but I can't figure out where/how to paste in the URL, and then how to save it?

I hope I didn't mess it up trying...

BTW, I'm using Edgy (see header).

You can use gedit, it is friendly
sudo gedit /etc/apt/sources.list

---

### Post by HeinBehrens on 2007-03-10
Works well for me. With Feisty Fawn.

Thanks

---

### Post by vitalik on 2007-03-10
Wow, thank you so much. I have been using Ubuntu 64 without flash for couple of month now. This guide worked great for me with alternative method # 2. The only problem I have run in was when I tried to install deb packages generated with **alien**

sudo dpkg -i nspluginwrapper-0.9.91.2-1.x86_64.deb 
sudo dpkg -i nspluginwrapper-i386-0.9.91.2-1.x86_64.deb

It gave me some errors, ca not remember which, sorry. But what I did is installed them in graphical interface. Just doubled click on them and grphical packege installer did the rest. So if any of you had the same problem, try to locate where you deb files where generated and install them form graphical interface and then continue to the rest of the guide.

Thanks again, awesome guide.

---

### Post by RacerII on 2007-03-11
The latest version of nspluginwrapper doesnt work for me on edgy
Heres the error:

(npviewer.bin:17012): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** NSPlugin Viewer  *** ERROR: NPP_Destroy() get args: Message argument mismatch
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Message type invalid
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Message type invalid

---

### Post by elchudi on 2007-03-13
it work for my also (alternative 2), running a kubuntu x86_64 edgy on a amd 64 x2 3800+
tnx mate

---

### Post by jzimmerman on 2007-03-18
I only read the first few pages of this thread while troubleshooting my installation issues, but I figured out what the problem was for me.  Ignore this if this issue has already been discussed.

I am running Feisty AMD64 w/ Firefox 2.0.  

I followed installation alternative 1 described at the start of this thread.  I could not get the libraries to load so that flash would work.  All steps executed without error and I executed every command with sudo (I didn't want it to go in my profile).

My problem was that the files I copied into /usr/lib/mozilla/plugins were owned by root and had permissions 700.  I chmod'd them to 755 and everything loaded properly.

So "check your permissions" might be a helpful tip to add to the list.  Probably just for those not following the directions _exactly_ though.

Thanks for all the information in this thread.

---

### Post by Memocjro on 2007-03-18
Thank you. It worked like a charm.

I have used the second alternative, but i downloaded the last packages from

[http://gwenole.beauchesne.info/](http://gwenole.beauchesne.info/)

It's great

---

### Post by jonnylinuxnerd on 2007-03-20
This guide rules! I just wanted to say thanks for the great instructions. I've been trying to get flash working for ages when I stumbled across this. :)

---

### Post by chrism66 on 2007-03-20
Thanks also worked fine here!

---

### Post by DREMA on 2007-03-21
Followed the instructions and works perfect for me!

---

### Post by eatmo on 2007-03-21
This worked nicely for me, but I'd just like to add that if you happen to have **libswfdecmozilla.so** in your plugin directory you will need to delete it for flash to work. It was probably there after I initially tried to just install flash without all the tricks.

This had me a little confused for a good 15 minutes.

---

### Post by nategreat on 2007-03-22
I've found an easy way of viewing  flash videos (FLV) such as youtube & google videos on an 64 bit Linux operating system, but theres no sound. I'm using Ubuntu.

1 Install gxine using the add/remove programs in the application menu. 
2 Install VideoDownload extension in Firefox or any other video downloader extension.
3 Go to the page with the embedded flash video you want to play. Click on the VideoDownload symbol.
4 This will give you a link to the file. Right  click on it and select "copy link location".
5 Open gxine from the application > sound and video menu and paste the url (web address) into the FILE > OPEN MRL box
6 Voila! It will load the video in gxine

If anyone  knows how to get sound and automate this please let me know.

---

### Post by mfrnka on 2007-04-04
Great info.  Worked well for me today installing the latest nspluginwrapper, "option 2".

I'll be 100% Windows free very shortly.  :)

---

### Post by CadetD on 2007-04-04
He he, U D Man!

Works perfectly.  Thanks. 

D. 

-------------------------
Dual AMD64 Opteron 270 (quad core), 8GB RAM, ATI X1950 Pro
Ubuntu 6.10

---

### Post by Corbelius on 2007-04-05
New version 0.9.91.4 is up to repository for edgy :)

---

### Post by fabertawe on 2007-04-05
Corbelius, just wanted to say thanks for this, working great here :) 

Paul

---

### Post by bcrowell on 2007-04-05
Hi Pinguin -- Thanks for posting this!

This worked for me on my amd64 machine, running edgy.

Here are a few notes, corrections, and explanations:

On Janvitus's page, there is information in English down below the Italian part. In the commands he lists there for setting up the gpg key, the -- (double dashes) have been typeset as m-hyphens, so it won't work if you just cut and paste from his page into a terminal window. The correct command is this:

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -

The following is incorrect, I think:

in the folder .mozilla/plugins/ in our /home we can see the file “npwrapper.libflashplayer.so”, created from the previous command.

Actually this file is already in the directory /usr/lib/mozilla/plugins. Therefore, it's not necessary to copy it to that directory. All that should be necessary is to copy it into the mozilla-firefox/plugins directory (or create a link).

-Ben

---

### Post by sebastian__ on 2007-04-05
Thanks man it's working for me

---

### Post by yelserpdog on 2007-04-05
I just keep getting

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lib32asound2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lib32asound2 has no installation candidate

What's happening?

Dog

---

### Post by Christobevii3 on 2007-04-08
I think the problem people are having is that the ia32-libs-gtk isn't installing.

```
Package ia32-libs-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ia32-libs
E: Package ia32-libs-gtk has no installation candidate

```

This is what it causes later  

```
christobevii3@laptop:~/Desktop$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin

```

---

### Post by Corbelius on 2007-04-08
> **yelserpdog said:**
> I just keep getting

What's happening?

Dog

> **Christobevii3 said:**
> I think the problem people are having is that the ia32-libs-gtk isn't installing.



Enabled multiverse and universe ubuntu repositories.

---

### Post by yelserpdog on 2007-04-08
> **Corbelius said:**
> Enabled multiverse and universe ubuntu repositories.

And hey presto, it works!!! Many thanks Corbelius and Kilz 

you rock :guitar: 

Cheers

---

### Post by Spr0k3t on 2007-04-09
Many thanks.  Alternate method #2 works with Feisty with the following changes.

When you go to move the files, move them to /usr/lib/firefox/plugins/* and perform the nspluginwrapper command on that file specifically.  The folder /usr/lib/mozilla/ did not exist on my system.  Using a clean install of Ubuntu Feisty beta.

Thanks again!

---

### Post by Spr0k3t on 2007-04-09
After closing and loading the browser flash no longer works.  I have to rerun the following:

```
nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so
```

before flash plays properly.

---

### Post by saru411 on 2007-04-10
thanks for the howto. i learned how to copy files with terminal also from trying to do this howto.

---

### Post by dellUsional on 2007-04-11
> **Corbelius said:**
> New version 0.9.91.4 is up to repository for edgy :)
Does this version fix the restart/reboot problem? Also, how can I tell which version of nspluginwrapper I've installed? I used method 1 (repository) to install. I still have to use the [COLOR="Red"]nspluginwrapper -v -a -i[/COLOR] command.

---

### Post by Corbelius on 2007-04-13
> **dellUsional said:**
> Does this version fix the restart/reboot problem? 

It's not a bug, never had this problem, try to eliminate all files you have installed and created before and reinstall nspluginwrapper.

> Also, how can I tell which version of nspluginwrapper I've installed? 

From terminal:

```
nspluginwrapper --help
```

---

### Post by saru411 on 2007-04-13
i also have the issue of having to type nspluginwrapper -v -a -i command after restarting fire fox. i was wondering if i should delete the copy of the .so file in this screen shot. you can also see the wrapped one to the far right.

---

### Post by ender on 2007-04-13
Beautiful. :grin: 
I really hated having to install 32bit Firefox to get flash working.

---

### Post by alecut on 2007-04-14
I followed penguins instructions and managed to install flash 9 on my firefox on a 64-bit system with ubuntu feisty beta version 7.04 (alternative #2 worked for me)

Only one addition at the end since i kept on getting the following error : 
> LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/
npwrapper.libflashplayer.so [/usr/lib/firefox/plugins/npwrapper.libflashplayer.so: npwrapper.libflashplayer.sonpwrapper.libflashplayer.sonpwrapper.libflashplayer.so:
cannot open shared object file: Permission denied]


I ran the following to fix it:

> sudo chmod 555 /usr/lib/firefox/plugins/npwrapper.libflashplayer.so 
sudo chmod 755 /usr/lib/firefox/plugins/

it glitched a bit at the beginning but after a reboot all seems well.

Hope this will be helpful and thanks penguin.

---
Alexandra Alecu

---

### Post by rogeriovinhal on 2007-04-14
And for java plugin? What do you do to make it work in 64-bit firefox?
nspluginwrapper also works?

Becasu blackdown Java closes firefox for me everytime I use a java application.

---

### Post by Spr0k3t on 2007-04-14
> **alecut said:**
> I followed penguins instructions and managed to install flash 9 on my firefox on a 64-bit system with ubuntu feisty beta version 7.04 (alternative #2 worked for me)

I ran the following to fix it:
```
sudo chmod 555 /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo chmod 755 /usr/lib/firefox/plugins/
```

Thanks alecut!  Performing the chmod fixed the issue on my system as well.  Now we just need to get the updated information about the chmod and the /firefox/ instead of /mozilla/ back into the first post so people don't have to dig for the solution.

---

### Post by dellUsional on 2007-04-18
> **Corbelius said:**
> It's not a bug, never had this problem, try to eliminate all files you have installed and created before and reinstall nspluginwrapper.
Hey, it's working. I rm'd all files, reinstalled, and then ran the chmod commands. I quit FF. Restarted FF. Still get Flash. Haven't rebooted yet but I'm totally optimistic. :popcorn:

---

### Post by vitalik on 2007-04-18
Yes this is a great guide and everything is working. Awesome, and thank you.
Too bad Java does not work yet, I know it will work with 32bit Firefox, but I don't want to run 32 bit apps on on my Ubuntu 64. What is a purpose of running 64bit OS and then installing 32bit apps, of course if there is no 64bit app available then maybe I will consider, but for now I will not use Java. And besides there are not to many sites that use it, but Flash on the other hand is very handy.

Thank You.

---

### Post by DaylanDarby on 2007-04-19
Thank you, pinguin, your instructions worked for me.

---

### Post by CarlosinFL on 2007-04-20
Anyone know if this will now work with 7.04? I tried this on my 6.10 and it worked great but since 4/19 I have upgraded to 7.04. Not sure if I should try this on my new system (fresh install).

---

### Post by CarlosinFL on 2007-04-20
OK - I would like to report back that this works perfectly on 7.04 as well!

---

### Post by zham61 on 2007-04-21
Hey I'm new to Ubuntu.  This is actually my first post on the forums!! I was doing this install and I got stuck at one part.  I don't understand how to find the folder location stated here:

"in the folder .mozilla/plugins/ in our /home we can see the file “npwrapper.libflashplayer.so”, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works]
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]"

Can you explain where I find this .mozilla/plugins/ in our /home ? 

Thanks!

---

### Post by Dhana on 2007-04-21
Works a treat mate! Thanks so much!

---

### Post by pinguin on 2007-04-21
to zham61
open Resources > Home
then click on View in your nautilus menu bar
then check Show Hidden files
(I think these are english menus, my menus are in italian languages)
and you can see .mozilla in your home
files beginning with "." are hidden files

---

### Post by CarlosinFL on 2007-04-21
> **zham61 said:**
> Hey I'm new to Ubuntu.  This is actually my first post on the forums!! I was doing this install and I got stuck at one part.  I don't understand how to find the folder location stated here:

"in the folder .mozilla/plugins/ in our /home we can see the file &#8220;npwrapper.libflashplayer.so&#8221;, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works]
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]"

Can you explain where I find this .mozilla/plugins/ in our /home ? 

Thanks!

Yes,

open a "Terminal" window and type this:

```
sudo cd ~/.mozilla/plugins
```

The "~/" tells Linux to put you in your current users /home directory and anything with a "." in front of it is a hidden directory.

So you're telling linux to move you (cd) to my home dir. (~/) and once in my home dir, put me in .mozilla/plugins.

You can "pwd" once you're there and see for yourself.

- Carlos

---

### Post by felin on 2007-04-22
Hi I used option 2 - I must be missin something basic here? wheen I get to the last command i get
> bash: nspluginwrapper: command not found


---

### Post by FiggyG on 2007-04-22
Thanks for the guide Pinguin, got it working and wow... flawless on my system so far! I was about to install the 32-bit firefox but did this instead :D

Athlon 64 3000+, SB Audigy SE, X1600XT, 2GB RAM, Kubuntu Feisty
:popcorn:

---

### Post by radiobuzzer on 2007-04-23
just followed the HOWTO and had it perfectly working in Ubuntu Feisty. I haven't restarted yet. Let's see.

---

### Post by LHoT on 2007-04-23
> **Spr0k3t said:**
> Many thanks.  Alternate method #2 works with Feisty with the following changes.

When you go to move the files, move them to /usr/lib/firefox/plugins/* and perform the nspluginwrapper command on that file specifically.  The folder /usr/lib/mozilla/ did not exist on my system.  Using a clean install of Ubuntu Feisty beta.

Thanks again!

Same here. But its saying I don't have permission to move the file to there. How do I move it. (I've tried dragging and dropping.

EDIT::: I got it

Edit part two::: Halp!
```
lhot@lhot-laptop:~$ nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: /usr/lib/firefox/plugins/libflashplayer.so is not a valid NPAPI plugin

```

---

### Post by Kilz on 2007-04-23
> **FiggyG said:**
> Thanks for the guide Pinguin, got it working and wow... flawless on my system so far! I was about to install the 32-bit firefox but did this instead :D

Athlon 64 3000+, SB Audigy SE, X1600XT, 2GB RAM, Kubuntu Feisty
:popcorn:

Its nice that you got it working.[ Can you play the game at this website]("http://www.wildsnake.com/webgame/sso/") with 64bit firefox?

---

### Post by dsegarra on 2007-04-23
For some reason Xubuntu is missing something that lets you play flash. Any ideas??  I know flash is installed with nspluginwrapper but lets say youtube wont display the interface where the play,stop buttons are. Any ideas???

---

### Post by AscendedDaniel on 2007-04-23
I got this working on Feisty Fawn Amd64 by following the instructions and choosing using alien to get nspluginwrapper.

---

### Post by Focus Fate on 2007-04-24
I'm brand new to Linux, only have had Ubuntu Feisty Fawn 64bit  a few days and a complete noob. But this guide (main post) using method 2 worked beautifully. No problems. Flash worked but youtube would still say java wasn't enabled. I merely restarted firefox and there it was working :) Restarted the system and it still works! Thanks for a 'noob' friendly guide!!!

---

### Post by fastpakr on 2007-04-24
> **felin said:**
> Hi I used option 2 - I must be missin something basic here? wheen I get to the last command i get

Same here... I feel sure I missed an obvious step - can somebody explain the error in our ways?

---

### Post by B-&gt;J-&gt;Eagle on 2007-04-24
Thank you so much friend. This so totally helped me. And i did on Feisty Fawn 7.04. Thanks. i love you man.

---

### Post by chamithal on 2007-04-24
ThnX pinguin! This works! Nice work! Keep it up!

But these bold parts shd be changed according to whats on your PC!
sudo dpkg -i nspluginwrapper**-0.9.91.2-1.x86_64**.deb 
sudo dpkg -i nspluginwrapper**-i386-0.9.91.2-1.x86_64**.deb

---

### Post by FiggyG on 2007-04-24
> **Kilz said:**
> Its nice that you got it working.[ Can you play the game at this website]("http://www.wildsnake.com/webgame/sso/") with 64bit firefox?
Unfortunately, the browser closes when I click on the game to play. :(

---

### Post by boogachamp on 2007-04-24
Hi,

I added:
deb [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-janvitus main-amd64
deb-src [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-janvitus main-amd64

to my sources.list and get this when I do an update:
W: GPG error: [http://janvitus.interfree.it](http://janvitus.interfree.it) feisty-janvitus Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5CEBE24C2C4C84CC
W: You may want to run apt-get update to correct these problems


Am I doing something wrong?

---

### Post by marcio.mutti on 2007-04-24
Thanks man. Alternative #2 worked flawlessly on my feisty 64 core2duo.
Many thanks.

---

### Post by boogachamp on 2007-04-25
Even with the warnings everything worked flawlessly.  Thank You for this!!!!

---

### Post by Wolfraem on 2007-04-25
It actually works! I used Alternative 2. 

I did encounter error messages, and the final file showed as simply "npwrapper.so" rather than "npwrapper.libflashplayer.so"

I'm not sure if this will cause issues for me in the future, but for now shockwave applets seem to work, so I'm satisfied.

---

### Post by trailrunner13 on 2007-04-25
First, pinguin, thanks. It's posts like yours that make the Ubuntu forums much more useful than many others. Plus everyone is so polite here. Very newbie friendly.
 
I was also successful in getting flash working, but had to do a few gyrations on _# Alternative n. 2_ to get there. I'm not a power user (I know enough to NOT rm *.* while root or any other time ;-) ), so I did a lot of your steps via GNOME GUI vs CLI. The only reason I'm putting my version of the process forward is to help out some other clueless newbies like me bumble their way through the install. Here goes:
[LIST]
[*]I didn't have the alien package installed, but it's part of the Ubuntu Desktop "main" components group, so I was able to add it via Synaptic Package Manager. Super easy.
[*]I also didn&#8217;t have the dpkg package installed, but it too is part of the "main" components group. However, since I'm a divot, I didn't think to install it. I didn't really know what dpkg was / does and thought it was a regular Linux / Unix command. When I tried from Terminal and Root Terminal and got errors, I figured there was something wrong with the .deb files. But I stumbled into the GDebi Package Installer in GNOME and tried that out. It did the deed on the .deb files, so I moved on. In retrospect, I now know why dpkg didn't work. Duh.
[*]File Browser doesn't let you access certain folders if their permissions aren't just right. Since I didn't want to muck around doing chmod's all over the place and potentially harm something, I just used Root Terminal to cp "libflashplayer.so&#8221; and &#8220;flashplayer.xpt&#8221; over to /usr/lib/mozilla/plugins. This same "challenge" was addressed in [http://ubuntuforums.org/showthread.php?t=341727&page=8&highlight=flash+feisty+firefox](http://ubuntuforums.org/showthread.php?t=341727&page=8&highlight=flash+feisty+firefox).
[*]But since Terminal and Root Terminal can't get into any of the /. directories in my /home area (maybe someone can explain that to me), I was at a loss. I ended up using File Browser to copy &#8220;npwrapper.libflashplayer.so&#8221; into a non-/. directory, then used Root Terminal to cp it over to /usr/lib/mozilla/plugins/ and /usr/lib/mozilla-firefox/plugins/. Yes, yes, all have a chuckle at my expense. I don't mind.[/LIST]That's about it. The process took me a couple tries to get it right. The first time I failed to follow the very first step of installing the various *32* libraries. Later, I think because I was failing in different places and retrying different steps, I just plain messed things up. I ended up rm all the files I'd created, rebooted and started over from the beginning. It worked. I think the process is solid IF you execute the steps properly, which I didn't.
 
BTW... The names of the .rpm files I pulled down from [http://gwenole.beauchesne.info]("http://gwenole.beauchesne.info/") were named the same as in your steps:
```

nspluginwrapper-0.9.91.2-1.x86_64.rpm
nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm

```
 
But the .deb files generated by Alien were named differently:
```

nspluginwrapper_0.9.91.2-2_amd64.deb
nspluginwrapper-i386_0.9.91.2-2_amd64.deb

```
 
No matter, it still worked.

---

### Post by Judo on 2007-04-25
The first method worked fine for me.  Not even one error message.  There seem to be some bugs, but they're annoying at worst.

Thank you very much.

---

### Post by CarlosinFL on 2007-04-25
> **Kilz said:**
> Its nice that you got it working.[ Can you play the game at this website]("http://www.wildsnake.com/webgame/sso/") with 64bit firefox?

No - that is wanting the Java-Plugin for Firefox which I dont think is available for AMD64. Atleast I am looking for a way to make it work...

---

### Post by dogson on 2007-04-25
Thank you, this works altho abit slow at times and controls in youtube videos are a abit flakey. i really hope adobe get its act together and releases a 64bit version of flash9

---

### Post by damvcoool on 2007-04-25
I followed the guied and it worked flawlessly. it takes a little bit of time to load youtube and metacafe but it works :D even with audio :D

---

### Post by lifelover on 2007-04-25
Everything went smooth until I wanted to move libflashplayer.so and flashplayer.xpt into the mozilla plugins folder. It did not let me to copy and paste the files. It says that I'm not the owner, so bye-bye. Any suggestions?

---

### Post by Judo on 2007-04-25
> **lifelover said:**
> Everything went smooth until I wanted to move libflashplayer.so and flashplayer.xpt into the mozilla plugins folder. It did not let me to copy and paste the files. It says that I'm not the owner, so bye-bye. Any suggestions?

Open up the terminal and type this and type in your password:
```
sudo nautilus
```
This will give Nautlius permission to copy and paste the files.

---

### Post by Toupee on 2007-04-25
Maybe someone can help me out here.

I've followed all the steps up to nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so , and I get this error message:

```
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libgobject-2.0.so.0: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

I am running as root.  I don't know if that has anything to do with it.  (Don't ask.)

---

### Post by David Jenkins on 2007-04-26
Well, I followed option 2 yesterday, and it worked perfectly.

Today I tried to look at a YouTube video - and just got a blank.

The only thing that's happened in-between was that I had loaded RealPlayer 10 - could this be interfering with this Flash installation?

David

UPDATE: I re-read the thread! :D Entering **nspluginwrapper -v -a -i** fixed it, as described elsewhere.  As always, RTFM...

---

### Post by damvcoool on 2007-04-26
I got nothing now!! :'( the only thing i did was that i turned my pc off. i did not installed anything or unistal anything.

---

### Post by LHoT on 2007-04-26
> **LHoT said:**
> Same here. But its saying I don't have permission to move the file to there. How do I move it. (I've tried dragging and dropping.

EDIT::: I got it

Edit part two::: Halp!
```
lhot@lhot-laptop:~$ nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: /usr/lib/firefox/plugins/libflashplayer.so is not a valid NPAPI plugin

```

Please help. I'm not sure what I did wrong.

---

### Post by damvcoool on 2007-04-27
> **damvcoool said:**
> I got nothing now!! :'( the only thing i did was that i turned my pc off. i did not installed anything or unistal anything.

i found my problem i have to fix the permission of the file that is on /usr/lib/firefox/plugins to make it 777 as the others.

---

### Post by kdkirsch on 2007-04-27
Worked on first run without any problems. Thank you pinguin and Janvitus.

---

### Post by kdkirsch on 2007-04-27
The best approach (instead of changing folder/file permissions) is to open Nautilus with sudo. 
Issue the following command in the terminal:
sudo nautilus

you can even open nautilus to a specific directory, such as /usr/lib/mozilla, by issuing the following command:
sudo nautilus /usr/lib/mozilla

Hope this helps.

---

### Post by kdkirsch on 2007-04-27
> **LHoT said:**
> Please help. I'm not sure what I did wrong.

Regular users do not have the necessary privileges necessary to manipulate many key folders and files, e.g., /usr/.

The best way to make changes to these folder and files is to run Nautilus with sudo.

Issue the following command in the terminal:

[INDENT][FONT="Courier New"]sudo nautilus[/FONT][/INDENT]

You can also open Nautilus to a specific directory as follows:

[INDENT][FONT="Courier New"]sudo nautilus /usr/lib/mozilla[/FONT][/INDENT]

Hope this helps.

---

### Post by rgovind on 2007-05-04
FLASH PLAYER 9 WORKING on AMD64 Feisty Fawn.
===========================================
Hey this worked like a charm on AMD64 Feisty Fawn. One small change though. 

The wrapper landed here :

/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

[B]and not 
[/B]
 "
 in the folder .mozilla/plugins/ in our /home we can see the file &#8220;npwrapper.libflashplayer.so&#8221;, created from the previous command in the folder .mozilla/plugins/ in our /home we can see the file &#8220;npwrapper.libflashplayer.so&#8221;, created from the previous command.
"
Note : This is On **Kubuntu** 

All that we 
**/usr/lib/mozilla-firefox/plugins$** sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so npwrapper.libflashplayer.so

So a mentioned all that was required was 



Humble request: Team Ubuuntu Not that this took long but it would be great make it easier to do stuff like this via a UI such as adept ( its so much more porductive for a non-techie).

---

### Post by forbitel on 2007-05-04
works FINE in Feisty AMD64, with Firefox64... NICE.. thanks...

---

### Post by coolcalt on 2007-05-05
this worked for me with the alternative 1 approach.

I'm running Feisty 64.

---

### Post by chevrier on 2007-05-07
Amazing guide.  Worked like a charm (ubuntu feisty on dell xps, core2duo).  Thanks!

---

### Post by zmigliozzi on 2007-05-08
Sweet this works on Feisty x86_64 no problems. Thanks for the help!

---

### Post by prestonrittenhouse on 2007-05-10
Thank you, thank you, thank you. This was the *very* *last* *thing* I got fixed, after reinstalling eleventy-zillion development packages and praying it would all work.  Even got slave MS XP up under vmware!

Preston, dual-core Ath64 3600, Nvidia GeForce 7300 LE, 1G, Feisty, baby!

---

### Post by penvzila on 2007-05-10
This works for me, but if I close the browser and open it again, I have no Flash, and I have to to the whole process again.

---

### Post by Snargledorf on 2007-05-11
Thanks for this this is the only tutorial for nspluginwrapper that made sense to me im in school now so I'll have to wait till i get home to try this. I currently have 32bit Firefox and it works fine but I miss the Ubuntu integration (right click to set background etc.) Hopefully this will work for me but even if it doesn't its still a good tut.

---

### Post by queency on 2007-05-11
what about feisty ? ? ? amd64 machine

---

### Post by je1117 on 2007-05-11
WOW. Finally. Flash works with Feisty AMD64.

Now, does anyone know how to get Java working?

---

### Post by Guardia Republicano on 2007-05-11
I think you should add this to the first post to complete the guide:

[http://ubuntuforums.org/showpost.php?p=2095280&postcount=55](http://ubuntuforums.org/showpost.php?p=2095280&postcount=55)

It runs for Festy AMD64. :lolflag: 

Regards,
Pablo from Argentina.

---

### Post by Kilz on 2007-05-11
> **je1117 said:**
> WOW. Finally. Flash works with Feisty AMD64.

Now, does anyone know how to get Java working?

Nspluginwrapper does not work with the java plugin. You can try the blackdown 64bit plugin, but it causes the browser to crash for most people on every java applet. The other way is to install the 32bit browser with the link in my signature.

---

### Post by stealth17 on 2007-05-12
Worked perfectly on Feisty 7.04 per the instructions in the first post and the repository alternative.

Greatly appreciated, thanks!!

---

### Post by Corbelius on 2007-05-12
> **je1117 said:**
> WOW. Finally. Flash works with Feisty AMD64.

Now, does anyone know how to get Java working?

Install gcjwebplugin-4.1.

---

### Post by iam1e5 on 2007-05-17
help~!
im going crazy trying to install flash on ubuntu amd64 architechture~

for alternative 1:
iam1e5@iam1e5-desktop:~$ sudo apt-get install nspluginwrapper gsfonts-x11
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package nspluginwrapper**
iam1e5@iam1e5-desktop:~$

for alternative 2:
iam1e5@iam1e5-desktop:~$ sudo dpkg -i nspluginwrapper-0.9.91.2-1.x86_64.deb 
Password:
[B]dpkg: error processing nspluginwrapper-0.9.91.2-1.x86_64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 nspluginwrapper-0.9.91.2-1.x86_64.deb[/B]
iam1e5@iam1e5-desktop:~$ 

for alternative 3:
there is an error saying i dun have the permission to copy the files to the plugin folder

help help

---

### Post by rada on 2007-05-18
**[COLOR="DarkRed"]Awesome!! [/COLOR]**Thank you. So good to have smooth video on my main workstation again.

> **Guardia Republicano said:**
> I think you should add this to the first post to complete the guide:

[COLOR="Blue"][http://ubuntuforums.org/showpost.php?p=2095280&postcount=55](http://ubuntuforums.org/showpost.php?p=2095280&postcount=55)[/COLOR]


Yes, as described in that link, I also have to use a launcher script running the following command before launching firefox.

```
nspluginwrapper -v -a -i
```

I did ***not*** have to move or copy files from /usr/lib/mozilla/plugins to /usr/lib/firefox/plugins.

---

### Post by sidrit on 2007-05-18
pinguin, great job !
worked perfectly for me on first try.

thank you :)

---

### Post by iam1e5 on 2007-05-19
> **iam1e5 said:**
> help~!
im going crazy trying to install flash on ubuntu amd64 architechture~

for alternative 1:
iam1e5@iam1e5-desktop:~$ sudo apt-get install nspluginwrapper gsfonts-x11
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package nspluginwrapper**
iam1e5@iam1e5-desktop:~$

for alternative 2:
iam1e5@iam1e5-desktop:~$ sudo dpkg -i nspluginwrapper-0.9.91.2-1.x86_64.deb 
Password:
[B]dpkg: error processing nspluginwrapper-0.9.91.2-1.x86_64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 nspluginwrapper-0.9.91.2-1.x86_64.deb[/B]
iam1e5@iam1e5-desktop:~$ 

for alternative 3:
there is an error saying i dun have the permission to copy the files to the plugin folder

help help

help help~
any1 can help me~?

---

### Post by hiruzzolo on 2007-05-20
Hi I have a little problem with this.. Everything install smoothly and flash works in my firefox.. The little problem is that the click event in flash doesn't work perfectly.. I can click once (for example in a YouTube video) and than the click event doesn't work anymore for 20-30 seconds at least.. Is there anyone who can also experience this?

---

### Post by Corbelius on 2007-05-20
> **iam1e5 said:**
> help~!
im going crazy trying to install flash on ubuntu amd64 architechture~

for alternative 1:
iam1e5@iam1e5-desktop:~$ sudo apt-get install nspluginwrapper gsfonts-x11
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package nspluginwrapper**
iam1e5@iam1e5-desktop:~$



Have you dapper? my nspluginwrapper packages are only for edgy and feisty =)

---

### Post by gomera on 2007-05-20
It works !!!!  :D

Thanks a lot for the help. I was getting frustrated about not having flash on my x86_64 machine. I used to have firefox running as 32 bits but I don't think this was the correct solution. This workaround seems better and less intrusive.

Again, thanks a lot !

---

### Post by hoarder on 2007-05-23
I setup PulseAudio and everything works great, and the install of this Flash player works great, however, I cannot hear any audio, and I've tried setting firefoxrc to use both ALSA and Pulse. I have audio everywhere else, including embedded audio objects in Firefox, anyone have any clues?

---

### Post by hemebond on 2007-06-01
> **hiruzzolo said:**
> Hi I have a little problem with this.. Everything install smoothly and flash works in my firefox.. The little problem is that the click event in flash doesn't work perfectly.. I can click once (for example in a YouTube video) and than the click event doesn't work anymore for 20-30 seconds at least.. Is there anyone who can also experience this?I also have this problem, though it's not a time delay for me. I click a button, but then have to click outside the Flash component before it'll accept another click. It looks like it's registering the click, but something isn't being triggered.

---

### Post by Midahed on 2007-06-02
Many, many, many thanks to Pinquin and some of the other contributors to this thread.  Thanks to their efforts, I now have Shockwave Flash 9.0 r31 working fine on my AMD64 PC using Ubuntu 7.04 Feisty with the 64-bit version of Firefox 2.0.0.4.

Once I'd figured out where I was making mistakes and got over a couple of path differences, it all went very smoothly.  And, as someone who's completely new to Linux, I've learnt a heck of a lot over the last few hours!

Without the help of this thread I might have given-up and gone back to Windows ;)

Thanks!

Mike

---

### Post by D!mon on 2007-06-02
yeah, though it still seems to be cause of terrible memory leaks sometimes:((

---

### Post by berthanas on 2007-06-03
thanks a lot for the help... it works perfectly with 64bit feisty for me...

---

### Post by jscheel on 2007-06-04
> **hiruzzolo said:**
> Hi I have a little problem with this.. Everything install smoothly and flash works in my firefox.. The little problem is that the click event in flash doesn't work perfectly.. I can click once (for example in a YouTube video) and than the click event doesn't work anymore for 20-30 seconds at least.. Is there anyone who can also experience this?

I'm having the same problem. This is really frustrating... I think flash is teasing me! Nspluginwrapper is a wonderful utility though.

---

### Post by D!mon on 2007-06-04
Can you watch youtube videos with this installation?

---

### Post by fabertawe on 2007-06-06
> **hiruzzolo said:**
> Hi I have a little problem with this.. Everything install smoothly and flash works in my firefox.. The little problem is that the click event in flash doesn't work perfectly.. I can click once (for example in a YouTube video) and than the click event doesn't work anymore for 20-30 seconds at least.. Is there anyone who can also experience this?

I have this too, it seems to be affected by Beryl. Anyone else find it better with Metacity?

Paul

---

### Post by hiruzzolo on 2007-06-08
Hi! does it happen to you too that sometimes after sometime (like 1 hour) you use the flash plugin, like in youtube,the box of the flash application become grey and you have to restart firefox to get it work again?

---

### Post by OldDog11 on 2007-06-08
Can someone please tell me how to do the following instruction.

Let’s go into the folder with the downloaded .rpm files (in my case /home/maurizio)
And convert the packages
Code:

sudo alien nspluginwrapper-0.9.91.2-1.x86_64.rpm 
sudo alien nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm

I'm a newbie and when I enter the code it say that the nspluginwrapper is not found.

How do I "go into the folder with the downloaded .rpm files" and the use the code?

Thanks

---

### Post by mlabenda on 2007-06-08
Worked for my like a champ !!!
Great HowTo

---

### Post by sra136 on 2007-06-08
Hooray for Pinguin.  Much Props, seriously.

At first I didn't under why Alternatives 1,2 were not working.  I realized, much to my stupidity, I didn't download the npluginswrapper .deb package.  You have:

1. click on the link [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) 

2. click on the appropriate link for your Ubuntu version (mine was fiesty fawn amd64, and I chose the link with the deb, either link takes you to the page below).

3. click on the link [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/)

4. click on "feisty-upure64"

5. click on "browse contents" next to main-amd64

6. scroll down to npluginwrapper and download the .deb package (nspluginwrapper_0.9.91.4-0ubuntu2~janvitus_amd64.deb)

7. double click on the nspluginwrapper_0.9.91.4-0ubuntu2~janvitus_amd64.deb and install it.

8. follow pinguin's instructions for "Down flash player 9 from Adobe..."

** make sure you are doing everything from your "root" account.   Works like a charm!

---

### Post by dn* on 2007-06-12
There is a (tedious) work around for the issue people are having with being able to interact with their flash videos (e.g. pausing and resuming YouTube videos) and that is to right click and change the quality settings e.g. from High to Medium and then back to High. You need to do it each time you want to click something though which makes it a pain.

Anyone know of any solutions to this problem? Or solutions to the Flash/AMD64 problem that isn't this guide or the Firefox32 solution?

---

### Post by Kilz on 2007-06-13
> **sra136 said:**
> 
** make sure you are doing everything from your "root" account.   Works like a charm!

New users should think twice, and maybe a third time before activating the root account. It makes Ubuntu a little less secure. Besides , why do all that when you could just run the script in my signature?

---

### Post by Corbelius on 2007-06-13
> **sra136 said:**
> 
** make sure you are doing everything from your "root" account.   Works like a charm!

Use "sudo" only to move libflashplayer.so, other commands not required it :)

> **Kilz said:**
> Besides , why do all that when you could just run the script in my signature?

A .deb native package is much better of a package converted from a .rpm with alien :)

---

### Post by Kilz on 2007-06-13
> **Corbelius said:**
> Use "sudo" only to move libflashplayer.so, other commands not required it :)


A .deb native package is much better of a package converted from a .rpm with alien :)

Maybe, its possible. But the package alien converts is from the developer of nspluginwrapper. I have fewer security concerns that way.

---

### Post by Alex&amp;Linux on 2007-06-13
Hey Lowfront, you werent able to find the package using apt-get install?
Check out "software souces" in "administration" 
Make sure all repositories are enabled!

---

### Post by simplypatrick on 2007-06-14
Awesome, This works great thanks! :popcorn:

---

### Post by Scott64 on 2007-06-18
Thanks very much! Not being able to use flash was getting on my nerves! :)

---

### Post by CarlosinFL on 2007-06-21
Guys - I know this is a long thread however I am attempting to follow the steps on page one and I can't follow the 1st step as I can't find the following:

```
cwilliams@tunafish:~$ sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ia32-libs-gtk
E: Package ia32-libs has no installation candidate

```

Any suggestions?

---

### Post by pinguin on 2007-06-22
check yours repository list
and
sudo apt-get update
then try again

---

### Post by CarlosinFL on 2007-06-22
When I go to "System" > Administration > Restricted Drivers, I get an error that tell me my system does not require restricted drivers. I really don't understand as I could use the nVidia drivers in Debian but Ubuntu does not like the 8600GTS or something like that.

Here is my xorg.conf

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by fabertawe on 2007-06-22
> **Carlwill said:**
> When I go to "System" > Administration > Restricted Drivers, I get an error that tell me my system does not require restricted drivers. I really don't understand as I could use the nVidia drivers in Debian but Ubuntu does not like the 8600GTS or something like that.

You need driver 100.* from the Nvidia site for 8600 support. I'd recommend the latest driver at the time of writing (**[100.14.11]("http://www.nvidia.com/object/linux_display_amd64_100.14.11.html")**) as this has fixed some annoying bugs. It still doesn't play nice with Beryl on my system but I'll just have to bide my time on that one. I think Envy unstable supports an early 100.* release but I couldn't get it to install on my machine.

Take a look at **[these instructions]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#METHOD_2")** for installing the **[Nvidia website driver]("http://www.nvidia.com/object/linux_display_amd64_100.14.11.html")**.

In brief... save your work and go to a tty terminal (Ctrl Alt F1) and log in. Shut down the X server...
```
sudo /etc/init.d/gdm stop
```
Backup your Xorg config...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Install the necessary development libraries to compile the driver module...
```
sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config
```
Everything 'nvidia-*' (driver) **apart from 'nvidia-kernel-common'** needs to be completely removed...
```
sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-glx-legacy
```
Blacklist the 'nv' driver...
```
sudo nano -w /etc/default/linux-restricted-modules-common
```
by adding it like this...
```
# This file is sourced from the linux-restricted-modules-common init
    # script and is used to disable the link-on-boot feature, one module
    # at a time.  This can be useful if you want to use hand-compiled
    # versions of one or more modules, but keep linux-restricted-modules
    # installed on your system, or just to disable modules you don't use
    # and speed up your boot process by a second or two.
    #
    # Use a space-separated list of modules you wish to not have linked
    # on boot.  The following example shows a (condensed) list of all
    # modules shipped in the linux-restricted-modules packages:
    #
    # DISABLED_MODULES="ath_hal fc fglrx ltm nv"
    #
    # Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
    # ltmodem and ltserial, and "nv" disables both the nvidia drivers.
    # You can also name each module individually, if you prefer a subset.

    DISABLED_MODULES="nv"
```
Ctrl-O to save, Ctrl-X to exit. Now navigate to your downloaded Nvidia driver, i.e. if you saved it to your desktop type
```
cd ~/Desktop
```
Then run the Nvidia driver installer...
```
sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run
```
Follow the instructions (accept the licence, install 32 bit compatibility layer etc.) and it will compile and install everything. You then need to restart X...
```
sudo /etc/init.d/gdm start
```
**Troubleshooting:**
If you still get an 'API mismatch' error then there is still an 'nvidia*' driver lurking somewhere! Personally I had to delete the file '/lib/modules/`uname -r`/volatile/nvidia_new.ko'. If you do get this error then...
```
cd /lib/modules/`uname -r`
```
and have a nose around. If you find one you can remove it with
```
sudo rm nvidia_new.ko
```
**Be CAREFUL removing files as sudo**! If in doubt ask on the forums first. Hopefully you won't have that problem. If you are stuck with a dead X server you can always do this...
```
sudo nano /etc/X11/xorg.conf
```
and make sure you have **nv** as 'Driver' like this...
```
Section "Device"
    Identifier     "nVidia Corporation [MSI GeForce 8600GT OC]"
    Driver         "**nv**"
EndSection

```
Whatever you have for 'Identifier' (above) **must match exactly** in the 'Screen' section...
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "**nVidia Corporation [MSI GeForce 8600GT OC]**"
```
Also remember to
```
sudo nano -w /etc/default/linux-restricted-modules-common
```
and remove 'nv' from the disabled list! Then a...
```
sudo /etc/init.d/gdm start
```
will get you back to the desktop but without 3D acceleration. Good luck and do post back ;)

Paul

---

### Post by glok_twen on 2007-06-23
this seemed to work well for me in firefox.

anyone get it to work in konqueror? for each youtube video for example, i get just a black box where the video should be and the message "Klash: Stop Playing"

---

### Post by madubuntuer on 2007-06-27
Hi i'm running edgy with oss4 but I cant get any sound with the flash plugin. With abit of googling I relised that the sound library I've installed is for alsa. Which library do I use for OSS

---

### Post by devanity on 2007-06-28
Thank you, worked perfectly.

---

### Post by Do0odz on 2007-07-06
> **pinguin said:**
> After several tests in order to make Flash Player working on Amd64 with nspluginwrapper based on the reading of varies how-to and in occasion of the definitive version of Flash Player 9 I have thought to write this guide, taking cue from the several one how-to that I have read; I synthetize the things that I have made in order to make it to work. 
First of all we must install one series of libraries for compatibility with 32 bit 
Indispensable is to install ia32-libs ia32-libs-gtk linux32 lib32asound2 
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2 
```


During the installation I got the following error 
 Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

when I run the update I get this :  Some index files failed to download, they have been ignored, or old ones used instead.

how to solve plz ?

---

### Post by tyk on 2007-07-06
brilliant man :) thanks

---

### Post by Bubs on 2007-07-11
I get this error on your last step
```
/usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin

```
any ideas?

---

### Post by Bubs on 2007-07-11
nevermind I didn't copy the files first.  but it didn't work for me anyway...  I'll just search for the 32bit script

---

### Post by EnemyUnknown on 2007-07-11
It Works
thank you

---

### Post by absurdity on 2007-07-12
Alright guys I'm completely new to Linux so bare with me.
When I add the line:
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
```
A couple of things download and then it tells me to say Y/N to continue.
When I type Y and hit enter, this pops up and I have no idea what to do next:
[IMG]http://i168.photobucket.com/albums/u200/oogna/Screenshot3.png[/IMG]
Any responses are greatly appreciated.

---

### Post by pinguin on 2007-07-13
that is for java installation 
are you installing java? if yes check ok to accept license
but it has nothing to do with
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

---

### Post by Sh!fty on 2007-07-17
> **pinguin said:**
> in the folder .mozilla/plugins/ in our /home we can see the file “npwrapper.libflashplayer.so”, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works] 
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]


Everything OK until this. There was no plugins/ in my .mozilla/ directory but the file was already in /usr/lib/mozilla/plugins/ and not in /usr/lib/mozilla-firefox/plugins/ (despite I ran your how-to for both of them. All I did was copy the plugin in /usr/lib/mozilla/plugins/ into /usr/lib/mozilla-firefox/plugins/ and it worked.

I wanted to point this out just in case anyone else runs into it. I guess is just a different setup since this was written or something like that.

Thanks Pinguin!

---

### Post by PCWizKid on 2007-07-18
Worked great for me, only one step didnt work properly and that was installing the Debs command line.  I instead used the GUI Deb installer to install the 2 deb files created.

Also I'm using Fiesty 7.04 fully updated and this worked, just an FYI.


Youtube here I come!

Cheers
PCWiZkid

---

### Post by mhenriday on 2007-07-19
Thanks a lot, **pinguin** - the modified **alternative 1** on the first page of this thread worked perfectly for me, with a few further minor modifications and updates. Great to have **flash** installed on **64-bit Firefox** without having to install the **32-bit** little brother or forcing the architecture ! Now I can _watch_ videos in **Feisty** - I write «watch» advisedly, as I am unable to _hear_ them - after two years the good people at **Creative Technologies** have not yet gotten 'round to releasing a **Linux** driver (no matter whether **32** or **64-bit**) for their **Sound Blaster X-Fi** audio card. But perhaps by the end of Q3 this year ? And maybe some day, when _everybody_'s gone over to **64-bit** computing, **Adobe** will consider releasing versions of their software with native support for that format. Don't hold your breath !...

Henri

---

### Post by joe4psu on 2007-07-21
pinguin, thank you, thank you, thank you.  I followed your directions and while the directories were slightly different, flash is working!  Thanks for taking the time to post.

---

### Post by MorayJ on 2007-07-23
Excellent. Worked like a charm using the first alternative (which I have now disabled as that repository has all sorts of updated compiz etc that I may or may not need).

Just to mention that npwrapper.libflashplayer.so didn't get into my home directory - it went straight to /usr/lib/mozilla/plugins and I copied it from there to  /usr/lib/mozilla-firefox/plugins/

Thanks again

MorayJ

---

### Post by upthelum on 2007-08-04
How can i find out if i have 32 bit or 64 bit firefox or is it installed by default with Feisty?

---

### Post by Gutter on 2007-08-05
Just to chime here, this method worked perfectly on an Intel 64 bit system (Q6600 on a EVGA board)

The only catch is that Alien (using nspluginwrapper) was insisting of calling the converted package "AMD_64" instead of x86_64. But it still worked.

Thanks!

---

### Post by upthelum on 2007-08-06
> **pinguin said:**
> After several tests in order to make Flash Player working on Amd64 with nspluginwrapper based on the reading of varies how-to and in occasion of the definitive version of Flash Player 9 I have thought to write this guide, taking cue from the several one how-to that I have read; I synthetize the things that I have made in order to make it to work. 
First of all we must install one series of libraries for compatibility with 32 bit 
Indispensable is to install ia32-libs ia32-libs-gtk linux32 lib32asound2 
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2 
```
**Installation of the nspluginwrapper **

_# Alternative n.1: using repository kindly offered by Janvitus: _
add the respository and update the sources list: [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)
installation:
```
sudo apt-get install nspluginwrapper gsfonts-x11
```
# end of Alternative 1 

_# Alternative n. 2:downloading the last version of .rpm files the Plugin and Viewer from his site and debianizing with alien _
Download:
[http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.2-1.x86_64.rpm](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.2-1.x86_64.rpm) 
[http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm) 
install alien 
```
sudo apt-get install alien 
```
Let’s go into the folder with the downloaded .rpm files (in my case /home/maurizio) 
And convert the packages 
```
sudo alien nspluginwrapper-0.9.91.2-1.x86_64.rpm 
sudo alien nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm 
```
And install the packages 
```
sudo dpkg -i nspluginwrapper-0.9.91.2-1.x86_64.deb 
sudo dpkg -i nspluginwrapper-i386-0.9.91.2-1.x86_64.deb 
```
#end of Alternative n. 2 

**Download flash player 9 from Adobe site **[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) 

WARNING: At this point, make sure to close every open browser. 

Let’s go into the folder with the downloaded file and untar it
the “install_flash_player_9_linux” folder has been created  
move the 2 files “libflashplayer.so” and “flashplayer.xpt” from that folder into the /usr/lib/mozilla/plugins folder 
at last give the command 
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
```
if it is all right, it would have to return to the prompt without no messages

in the folder .mozilla/plugins/ in our /home we can see the file “npwrapper.libflashplayer.so”, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works] 
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]

Now, (if I remembered to write back all steps) it would work,
try going on [http://www.youtube.com/](http://www.youtube.com/) and watch a video. 

In my system it works, for stability we will see.

Automatically translated text: [http://www.google.com/intl/en/help/faq_translation.html](http://www.google.com/intl/en/help/faq_translation.html)
from: [http://forum.ubuntu-it.org/index.php/topic,56771.0.html](http://forum.ubuntu-it.org/index.php/topic,56771.0.html)

Hey i've tried various methods to install flash and none work so far and when i run "sudo alien nspluginwrapper-0.9.91.2-1.x86_64.rpm", i get the output on the screendump attached. 

Can you help please? Many thanks.

---

### Post by djn48 on 2007-08-06
hi, my problem is that after i install the nspluginwrapper and get flash working in my 64 bit firefox, i only get video but no sound, and after a while of having firefox open, i dont get the flash to load at all.. i tried several things i found on this forum but none has worked.
i am running oss v4 for my sound. i read someone made a question regarding the possibility of different libraries needed for oss, but i found no answer to that post.
for more information i tried getting flash with the script found on this forum but that got my firefox to crash every time i tried to load flash.

how can i get the sound to work?

thanks,

djn48

---

### Post by Corbelius on 2007-08-08
> **djn48 said:**
> hi, my problem is that after i install the nspluginwrapper and get flash working in my 64 bit firefox, i only get video but no sound, and after a while of having firefox open, i dont get the flash to load at all.. i tried several things i found on this forum but none has worked.
i am running oss v4 for my sound. i read someone made a question regarding the possibility of different libraries needed for oss, but i found no answer to that post.
for more information i tried getting flash with the script found on this forum but that got my firefox to crash every time i tried to load flash.

how can i get the sound to work?

thanks,

djn48

You have installed .deb or .rpm?

---

### Post by Kilz on 2007-08-08
> **upthelum said:**
> Hey i've tried various methods to install flash and none work so far and when i run "sudo alien nspluginwrapper-0.9.91.2-1.x86_64.rpm", i get the output on the screendump attached. 

Can you help please? Many thanks.

Do you have the universe and multiverse repositories enabled?

---

### Post by djn48 on 2007-08-08
> **Corbelius said:**
> You have installed .deb or .rpm?

I installed flash using the rpm files in this guide, which i later converted into .deb with alien for the installation.

thanks, 
djn48

---

### Post by Corbelius on 2007-08-09
> **djn48 said:**
> I installed flash using the rpm files in this guide, which i later converted into .deb with alien for the installation.

thanks, 
djn48

Remove all files you have installed, include symlynks in your "home", now reinstall.

If you have edgy or feisty is better to use the deb native package that you find in my upure64 repository, .debs converted with alien can create problems when upgrade to gutsy.

---

### Post by djn48 on 2007-08-09
> **Corbelius said:**
> Remove all files you have installed, include symlynks in your "home", now reinstall.

If you have edgy or feisty is better to use the deb native package that you find in my upure64 repository, .debs converted with alien can create problems when upgrade to gutsy.

what do you mean exactly by "include symlynks in your "home""?
i am using feisty, could you point me to a guide on how to make the installation from your repository?

thanks a lot,

djn48

---

### Post by Mochino on 2007-08-09
i'm also having the weird click bug, it's a pain since i use the netacad at cisco a lot :/ i used alternative 1, but i'm starting to wonder if i should try number 2, also using beryl.

---

### Post by mojportal on 2007-08-09
I see this

robi@phoenix:/usr/lib/mozilla/plugins$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by Corbelius on 2007-08-10
> **djn48 said:**
> what do you mean exactly by "include symlynks in your "home""?
i am using feisty, could you point me to a guide on how to make the installation from your repository?



1) 

```
@ubuntubox:~$ ls '/home/gianvito/.mozilla/plugins' 
npwrapper.libflashplayer.so

```

2) 

[http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)
[http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/](http://www.janvitus.netsons.org/2007/01/15/nspluginwrapper-adobe-flash-player/)
[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093)

> **Mochino said:**
> i'm also having the weird click bug, it's a pain since i use the netacad at cisco a lot :/ i used alternative 1, but i'm starting to wonder if i should try number 2, also using beryl.

It's a bug with compiz/beryl, no one fix at this moment.

> **mojportal said:**
> I see this

robi@phoenix:/usr/lib/mozilla/plugins$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

Have you downloaded and installed the flash player?

```
ls /usr/lib/firefox/plugins
```

---

### Post by shanek on 2007-08-11
Wow, this worked just perfectly for me. 

Thank you!

---

### Post by hphan on 2007-08-11
Thank you, Pinguin.
I followed your instructions and have made Flash work on HP Laptop AMD64 with Ubuntu 7.04

---

### Post by greybit on 2007-08-13
Thanks!  This worked for me!

---

### Post by vettepurr on 2007-08-13
> **pinguin said:**
> Try this:
move the 2 files &#8220;libflashplayer.so&#8221; and &#8220;flashplayer.xpt&#8221; from /usr/lib/mozilla/plugins folder to /usr/lib/firefox/plugins folder
then in terminal run:
nspluginwrapper -v -a -i

let me know

Along with the original instructions at the beginning of this thread and the above quote, I am now running flash Stable.  Even after several reboots.  I had to to run this last command under each profile of course. THANK YOU!!  Now my google talk gmodule works on igoogle too.  SCHWEEEET!

---

### Post by froginator on 2007-08-16
Sorry about my rookiness in linux... Ive followed instructions but when I come to the point where I write:
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

it says: "bash: nspluginwrapper: command not found"

I also tried to install nspluginwrapper by the second alternative.. but got same message..

I looked through whole thread and found 2 people having the same problem but they never got any answers...

Thanks in advance.

---

### Post by darthyorik on 2007-08-16
Try typing a **./** immediately before the command.

the **./** tells the shell to look for the command you are trying to run in the current directory, if you are not in the same directory as the command then you will have to supply the full path name to the command.

Commands that do not need this have their paths defined in your path in your user profile.

Hope that is clear enough, and helps.

---

### Post by JobeJahova on 2007-08-19
I just used ndiswrapper for flashplayer 9 on my 64 bit Dual core system and it works great. 

I am actually using it on Fedora 7 but I am an ubuntu user too (for my iBook). I hope it works on PPC's too.

---

### Post by saikat on 2007-08-20
[SIZE=4][COLOR=DarkOrange]It works like magic!
Thanks a Billion, [/COLOR][/SIZE][SIZE=5][COLOR=SeaGreen]Pinguin[/COLOR][/SIZE][SIZE=4][COLOR=DarkOrange] !!!![/COLOR][/SIZE]

---

### Post by arbulus on 2007-08-20
> **JobeJahova said:**
> I just used ndiswrapper for flashplayer 9 on my 64 bit Dual core system and it works great. 

I am actually using it on Fedora 7 but I am an ubuntu user too (for my iBook). I hope it works on PPC's too.

There are no Flash versions that work on PPC.

---

### Post by froginator on 2007-08-20
hihi, donno what was the problem but it worked in the end..

it seems like I failed to install those files I got from alien from terminal.. when I installed them just by clicking on the icon, that nsbutplugger worked. 

Im off to youtube to listen to some yngwie!

Thanks for your time

---

### Post by arbulus on 2007-08-20
> **froginator said:**
> hihi, donno what was the problem but it worked in the end..

it seems like I failed to install those files I got from alien from terminal.. when I installed them just by clicking on the icon, that nsbutplugger worked. 

Im off to youtube to listen to some yngwie!

Thanks for your time


Can a mod please block this troll?

---

### Post by bdoe on 2007-08-23
Hi!

I want to thank you for this tutorial; without wonderful people like you, I don't think many of us would get anywhere, since it seems so clear the major software developers have absolutely no interest in supporting the 64-bit community.

Anyways, I'm posting because I'm having some serious problems and am hoping someone can help me through this.

The first stumbling block I hit is when I try to do this:
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
```
I get this:
```
briandoe@Paige:~/Desktop$ sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 but it is not going to be installed
  lib32asound2: Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not going to be installed
E: Broken packages
briandoe@Paige:~/Desktop$
```
This may be the cause of my other problems.

When I try to do this:
```
sudo alien nspluginwrapper-0.9.91.2-1.x86_64.rpm 
sudo alien nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm
```
I get this:
```
briandoe@Paige:~/Desktop$ sudo alien nspluginwrapper-0.9.91.2-1.x86_64.rpm
Warning: Skipping conversion of scripts in package nspluginwrapper: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
hostname: Unknown host
hostname: Unknown host
nspluginwrapper_0.9.91.2-2_amd64.deb generated
briandoe@Paige:~/Desktop$ sudo alien nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm
hostname: Unknown host
hostname: Unknown host
nspluginwrapper-i386_0.9.91.2-2_amd64.deb generated
briandoe@Paige:~/Desktop$
```

Lastly, when I try this:
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
I get this:
```
briandoe@Paige:~/Desktop$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin
briandoe@Paige:~/Desktop$ 
```

Can anyone tell me what I'm doing wrong?

Oh yeah - I'm running Ubuntu Feisty 7.04.

---

### Post by mhenriday on 2007-08-25
Ciao **Pinguin**,

this is a wonderful initiative, and by following your instructions on page 1, I was able to get it working on my previous **Feisty** setup, and it continued to work after upgrading to a test version of **Gutsy**. But after a crash in connexion with an attempt to upgrade the kernel from **2.6.22-9** to **2.6.22-10** (hubris is always punished by the gods) and a re-installation of **Feisty** from the live CD, I find I can no longer get it to work - at least not consistently ; yesterday I was able to see this hilarious [take-off]("http://www.youtube.com/watch?v=05hDiLTDkFo") on the *Ring*  after running «**nspluginwrapper -v -a -i**», but today, nothing....

My guess is that these difficulties have to do with the fact that I have no «**.mozilla/plugins/**» under **/home** ; my **mozilla**, **firefox**, and **mozilla-firefox** folders are all found under **/usr/lib** (they all now contain the «**libflashplayer.so**» and «**flashplayer.xpt**» files under **/plugins**). What I do, however, find under **/home/mhenriday** is the **nspluginwrapper**  (**/nspluginwrapper_0.9.91.4-0ubuntu3~upure64_amd64.deb**) package, which, upon my clicking the «Included files» tab is found to contain the following : 

[INDENT]./
usr/
usr/share/
usr/share/doc/
usr/share/doc/nspluginwrapper/
usr/share/doc/nspluginwrapper/README
usr/share/doc/nspluginwrapper/copyright
usr/share/doc/nspluginwrapper/TODO
usr/share/doc/nspluginwrapper/changelog.Debian.gz
usr/share/doc/nspluginwrapper/changelog.gz
usr/share/doc/nspluginwrapper/NEWS.gz
usr/share/man/
usr/share/man/man1/
usr/share/man/man1/nspluginwrapper.1.gz
usr/lib/
usr/lib/firefox/
usr/lib/firefox/plugins/
usr/lib/mozilla/
usr/lib/mozilla/plugins/
usr/lib/iceweasel/
usr/lib/iceweasel/plugins/
usr/lib/nspluginwrapper/
usr/lib/nspluginwrapper/noarch/
usr/lib/nspluginwrapper/noarch/npviewer
usr/lib/nspluginwrapper/noarch/mkruntime
usr/lib/nspluginwrapper/plugins/
usr/lib/nspluginwrapper/i386/
usr/lib/nspluginwrapper/i386/linux/
usr/lib/nspluginwrapper/i386/linux/libxpcom.so
usr/lib/nspluginwrapper/i386/linux/npviewer
usr/lib/nspluginwrapper/i386/linux/npviewer.bin
usr/lib/nspluginwrapper/x86_64/
usr/lib/nspluginwrapper/x86_64/linux/
usr/lib/nspluginwrapper/x86_64/linux/npconfig
usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so
usr/bin/
usr/sbin/
usr/bin/nspluginwrapper[/INDENT]

But I can't open the package further, and despite many attempts to apply «**nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so**» and «**nspluginwrapper -v -a -i**», I'm never able to find the file «**npwrapper.libflashplayer.so**»  under **/usr/lib/mozilla/plugins** or **/usr/lib/mozilla-firefox/plugins/**. Where do I go from here ?...

Henri

---

### Post by Corbelius on 2007-08-27
> **mhenriday said:**
> Ciao **Pinguin**,

But I can't open the package further, and despite many attempts to apply «**nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so**» and «**nspluginwrapper -v -a -i**», I'm never able to find the file «**npwrapper.libflashplayer.so**»  under **/usr/lib/mozilla/plugins** or **/usr/lib/mozilla-firefox/plugins/**. Where do I go from here ?...

Henri

Found it to "/home/user/.mozilla/plugins".

New **NSPluginWrapper 0.9.91.5** is available in my repository ;)

**@ Tip for a easy installation of the Flash Player:**
Download the flash player, extract and move the files into "/usr/lib/nspluginwrapper/plugins" (root privilege required), now give the command:

```
nspluginwrapper -i /usr/lib/nspluginwrapper/plugins/libflashplayer.so
```

---

### Post by conchur on 2007-09-05
Thanks, this worked brilliantly.

Only point to add is that I had to add the --scripts option to the first rpm conversion, and the output package names had changed suffix  to  amd64 rather than x86_64.

I downloaded the 32 bit flash package and extracted it to my home directory (~/install_flash_player_9_linux).

The commands I used from then on are copied below:
```

sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
sudo apt-get install alien
sudo alien --scripts nspluginwrapper-0.9.91.2-1.x86_64.rpm
sudo alien nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm
sudo dpkg -i nspluginwrapper_0.9.91.2-2_amd64.deb
sudo dpkg -i nspluginwrapper-i386_0.9.91.2-2_amd64.deb

cd ~/install_flash_player_9_linux
sudo mv flashplayer.xpt /usr/lib/mozilla/plugins
sudo mv libflashplayer.so /usr/lib/mozilla/plugins
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo cp  ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/npwrapper.libflashplayer.so

```

Hope that saves someone a few seconds!

---

### Post by zo3adams on 2007-09-16
I also encountered the 'works at first, then a white box' bug, this was because the permissions on on file were restricted so I went to /usr/lib/firefox/plugins/ and ran:

sudo chmod 777 npwrapper.libflashplayer.so 

which solved it. (though i am confused why it was able to run once?)

One thing I still don't have working is the full screen option in youtube, does everyone else? I don't' see it mentioned. The resolution is usually so poor to do that anyway, but still... 

BIG THANKS to everyone in this thread, i worked on this for like a week and got no where but aside form minor details the how to in post 1 worked great!

---

### Post by davefromnz on 2007-09-17
Hi All, first post to the forums as a week-old Linux/Ubuntu user, and it's to say thanks to the threadstarter for this fix - worked a charm :cool:

---

### Post by anatak23 on 2007-09-18
> **zo3adams said:**
> I also encountered the 'works at first, then a white box' bug, this was because the permissions on on file were restricted so I went to /usr/lib/firefox/plugins/ and ran:

sudo chmod 777 npwrapper.libflashplayer.so 

which solved it. (though i am confused why it was able to run once?)

One thing I still don't have working is the full screen option in youtube, does everyone else? I don't' see it mentioned. The resolution is usually so poor to do that anyway, but still... 

BIG THANKS to everyone in this thread, i worked on this for like a week and got no where but aside form minor details the how to in post 1 worked great!

Same as poster quoted above... thanks for the tip!

---

### Post by chemisus on 2007-09-30
in case anyone else had the same problem as i did with there not being the npwrapper.libflashplayer.so in the ~/.mozilla/plugins directory, it is probably in the /usr/lib/mozilla dir.

i just did:

cd /
sudo find -name npwrapper.libflashplayer.so

should give you a path. just copy that file into the .mozilla/plugins, and it worked fine for me.

---

### Post by Kilz on 2007-09-30
> **zo3adams said:**
> I also encountered the 'works at first, then a white box' bug, this was because the permissions on on file were restricted so I went to /usr/lib/firefox/plugins/ and ran:

sudo chmod 777 npwrapper.libflashplayer.so 

which solved it. (though i am confused why it was able to run once?)

One thing I still don't have working is the full screen option in youtube, does everyone else? I don't' see it mentioned. The resolution is usually so poor to do that anyway, but still... 

BIG THANKS to everyone in this thread, i worked on this for like a week and got no where but aside form minor details the how to in post 1 worked great!

Full screen functionality is not working in the present version of flash. It is a problem Adobe is working on. They have it working in the new beta of flash, but it isnt quite right , and the beta has other issues so I wouldnt recommend it.

---

### Post by deoray on 2007-10-02
Thanks a lot pinguin. Its just perfect. Got it working in single attempt. thanks for detailed instructions.

Ravindra

---

### Post by ytene on 2007-10-07
Apologies if this is a silly or repeat question.

I've just upgraded FireFox on my Edgy/AMD64 build to version 2.0.0.7 and noticed that the flash player has stopped working. I had previously used the wrapper hack kindly provided by Janvitus and this has worked perfectly through a series of FireFox upgrades. 

I'm not aware that I did anything new or unusual this time around...

Can anyone offer a relative newbie any pointers on things to check in order to see if I can restore this please?

Thanks in Advance...

---

### Post by photonx on 2007-10-08
Yeah!! Works 100%! I have my Firefox 64 bits alive!
Thanks!
:popcorn:

---

### Post by magikx21 on 2007-10-08
Everytime I run GetFlash adept manager notifies me there is an update for nspluginwrapper but if I update then the browser locks when I open a page with flash, if I tell it to purge update flash becomes invisible on pages.

---

### Post by karanspage on 2007-10-12
it works.Thanks alot ;)

---

### Post by gtdaqua on 2007-10-22
upgraded from 7.04 64bit to Gutsy 64 bit. Flash was working in Firefox (Feisty) but wont work in Gutsy.
Just had to type the following to have flash installed on Firefox:

```

 nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

```

---

### Post by gtdaqua on 2007-10-22
upgraded from 7.04 64bit to Gutsy 64 bit. Flash was working in Firefox (Feisty) but wont work in Gutsy.
Just had to type the following to have flash installed on Firefox:

```

 nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

```

---

### Post by vange on 2007-10-30
When I use option 1 on Kubuntu 7.10 I get the following message. Should I ignore that util-linux is an essential package, and is removed?

sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
[sudo] password for rva:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting ia32-libs instead of ia32-libs-gtk
The following packages were automatically installed and are no longer required:
  jsvc libcommons-pool-java libbcel-java libecj-java liboro-java eclipse-jdt libcommons-modeler-java eclipse-pde
  libcommons-fileupload-java zenity eclipse-rcp libservlet2.4-java libcommons-beanutils-java junit libswscale1d
  libcommons-launcher-java libnotify1 libcommons-logging-java libcommons-collections-java libtomcat5.5-java ant libjsch-java
  ecj ant-optional libmx4j-java libscrollkeeper0 libcommons-dbcp-java liblucene-java libswt3.2-gtk-java libcommons-el-java
  libservlet2.3-java eclipse-source libcommons-daemon-java libregexp-java gnash libstruts1.2-java
  libcommons-collections3-java libgutenprintui2-1 eclipse-platform scrollkeeper libcommons-validator-java
  libcommons-digester-java liblog4j1.2-java libswt3.2-gtk-jni libsoup2.2-8 liblucene-java-doc
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386
Suggested packages:
  libasound2-plugins
The following packages will be REMOVED:
  ubuntu-minimal util-linux util-linux-locales
The following NEW packages will be installed:
  ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386 linux32
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  util-linux
0 upgraded, 8 newly installed, 3 to remove and 0 not upgraded.
Need to get 34,4MB of archives.
After unpacking 85,8MB of additional disk space will be used.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]

---

### Post by Footer on 2007-10-30
I did this and typed in the phrase 'Yes, do as I say!' and ended up reinstalling my system!  Thankfully, I have /home on it's own partition so it was really no big deal.  I'd been apt-get update/dist-upgrading my system for about 18 months though so I was actually glad to do a fresh install of 7.10.

You've been warned!!!

:)

---

### Post by vange on 2007-10-31
I will live without Flash for a while, then :-) I actually think of installing Kubuntu 32-bit just for enabling Flash and w32codecs.

---

### Post by vange on 2007-11-05
As of today the nonfree 32-bit Flash player from Adobe can be installed with no problems (on my laptop). I just installed "flashplugin-nonfree" from Adept Manager, and after restarting Firefox, it just worked. Together with the nonfree flashplugin all the linux32-stuff was automatically installed with no warnings or errors about broken dependencies.

I am quite sure that the flashplugin-nonfree wasn't available when I installed the OS a couple a weeks ago. So I started investigating when the package was added to the repositories, but I cannot find the date of a package at [http://packages.ubuntu.com](http://packages.ubuntu.com) - can you?

I am running 64-bit Kubuntu 7.10 on Dual Core 2.

---

### Post by pinguin on 2007-11-11
First post edited about Gutsy, K/Ubuntu 7.10.
Gutsy users look at the beginning of the first post, please.

---

### Post by pinguin on 2007-11-11
> **vange said:**
> I will live without Flash for a while, then :-) I actually think of installing Kubuntu 32-bit just for enabling Flash and w32codecs.
With Gutsy 64-bit you should be able to install flash with apt-get or synaptic/adept and nspluginwrapper should also install and automatically configure the plugin wrapper.
About w64codecs take a look at Medibuntu repos: [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by gerrievj on 2007-11-11
This worked ok for me on feisty fawn! thx for post

---

### Post by God_Bless on 2007-11-23
I have an AMD 64 Laptop. I just gave up on trying to write patches for every 64/32 bit problem. I just reinstalled ubuntu with the standard 32 version. It is much easier and truly I haven't noticed much of a difference with my hardware. Every patch that I used from all the seasoned ubuntu and linux users never seemed to work. Maybe when things are fixed with the 64 bit version I will go back to it. For now the best thing to do (in my opinion) is just go with the 32 bit version.

---

### Post by OisinT on 2007-11-24
I need some serious help.. I have no flash... I followed the instructions ([https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64FlashJava#nspluginwrapper](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64FlashJava#nspluginwrapper)) to no avail for 64bit.  I filed a bug report weeks ago with no fix, and I'm starting to go a little crazy.  The weird thing is when I go to pages with flash it doesnt say it's not installed, the items just don't show up.  Any help is appreciated!!

---

### Post by Yellow Pasque on 2007-11-24
OisinT,
type about:plugins in the url bar (and hit Enter)
Does that show any shockwave plugin installed?

---

### Post by OisinT on 2007-11-24
```
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```



```
oisint@OisinT1:~$ ls -al /usr/lib/mozilla/plugins/
total 208
drwxr-xr-x 2 root   root    4096 2007-11-17 15:30 .
drwxr-xr-x 3 root   root    4096 2007-04-15 12:58 ..
lrwxrwxrwx 1 root   root      38 2007-11-17 15:30 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
-rw-r--r-- 1 root   root   65692 2007-08-30 23:50 libswfdecmozilla.a
-rw-r--r-- 1 root   root    1308 2007-08-30 23:50 libswfdecmozilla.la
-rw-r--r-- 1 root   root   45320 2007-08-30 23:50 libswfdecmozilla.so
lrwxrwxrwx 1 root   root      36 2007-11-13 21:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root   root      37 2007-11-13 21:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root   root      34 2007-11-13 21:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root   root      35 2007-11-13 21:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root   root      36 2007-11-13 21:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root   root      37 2007-11-13 21:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root   root      42 2007-11-13 21:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root   root      43 2007-11-13 21:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 oisint oisint 70120 2007-09-13 17:01 npwrapper.libflashplayer.so

```

---

### Post by golebara on 2007-12-04
Thanks for the tute, Pinguin. Worked like a charm.

---

### Post by Yellow Pasque on 2007-12-05
> -rwx------ 1 oisint oisint 70120 2007-09-13 17:01 npwrapper.libflashplayer.so

Sorry for the delayed response. Try:
```
cd /usr/lib/mozilla/plugins
sudo mv npwrapper.libflashplayer.so libflashplayer.so
sudo chmod 755 libflashplayer.so
```

---

### Post by OisinT on 2007-12-05
> **Temüjin said:**
> Sorry for the delayed response. Try:
```
cd /usr/lib/mozilla/plugins
sudo mv npwrapper.libflashplayer.so libflashplayer.so
sudo chmod 755 libflashplayer.so
```

it's saying "mv: cannot stat `npwrapper.libflashplayer.so': No such file or directory"


```
oisint@OisinT1:~$ ls -al /usr/lib/mozilla/plugins/
total 132
drwxr-xr-x 2 root root  4096 2007-11-26 19:37 .
drwxr-xr-x 3 root root  4096 2007-04-15 12:58 ..
lrwxrwxrwx 1 root root    38 2007-11-17 15:30 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
-rw-r--r-- 1 root root 65692 2007-08-30 23:50 libswfdecmozilla.a
-rw-r--r-- 1 root root  1308 2007-08-30 23:50 libswfdecmozilla.la
-rw-r--r-- 1 root root 45320 2007-08-30 23:50 libswfdecmozilla.so
lrwxrwxrwx 1 root root    36 2007-11-13 21:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-11-13 21:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-11-13 21:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-11-13 21:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-11-13 21:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-11-13 21:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-11-13 21:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-11-13 21:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
oisint@OisinT1:~$ 


```

---

### Post by Yellow Pasque on 2007-12-05
> it's saying "mv: cannot stat `npwrapper.libflashplayer.so': No such file or directory"
LOL, where did your file go? :confused:

---

### Post by Kilz on 2007-12-05
> **OisinT said:**
> ```
oisint@OisinT1:~$ ls -al /usr/lib/mozilla/plugins/
total 208
drwxr-xr-x 2 root   root    4096 2007-11-17 15:30 .
drwxr-xr-x 3 root   root    4096 2007-04-15 12:58 ..
lrwxrwxrwx 1 root   root      38 2007-11-17 15:30 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
[B]-rw-r--r-- 1 root   root   65692 2007-08-30 23:50 libswfdecmozilla.a
-rw-r--r-- 1 root   root    1308 2007-08-30 23:50 libswfdecmozilla.la
-rw-r--r-- 1 root   root   45320 2007-08-30 23:50 libswfdecmozilla.so[/B]
lrwxrwxrwx 1 root   root      36 2007-11-13 21:36 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root   root      37 2007-11-13 21:36 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root   root      34 2007-11-13 21:36 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root   root      35 2007-11-13 21:36 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root   root      36 2007-11-13 21:36 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root   root      37 2007-11-13 21:36 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root   root      42 2007-11-13 21:36 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root   root      43 2007-11-13 21:36 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rwx------ 1 oisint oisint 70120 2007-09-13 17:01 npwrapper.libflashplayer.so

```

It is best to remove **[COLOR="Red"]all [/COLOR]**flash plugins before installing flashplugin-nonfree.  You still have [swfdec]("http://swfdec.freedesktop.org/wiki/") installed. I seem to remember telling you in the past to remove all conflicting flash plugins.

---

### Post by OisinT on 2007-12-08
> **Kilz said:**
> It is best to remove **[COLOR="Red"]all [/COLOR]**flash plugins before installing flashplugin-nonfree.  You still have [swfdec]("http://swfdec.freedesktop.org/wiki/") installed. I seem to remember telling you in the past to remove all conflicting flash plugins.

I did, and i'm not sure if they're being automatically re-installed or what, but after I delete them - the flash works for a while, but if I ever restart the machine it stops working again and these files are back.

---

### Post by daradib on 2007-12-08
BTW

There is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This caused Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10 and later 6.10 and 6.06.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

For Ubuntu 6.06 and 6.10, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by Jabb3r on 2007-12-09
Thanks for the guide. It really helped me to get flash working on Gutsy

Few differences though. Theres no .xpt file after extraction but just doing the copy of libflashplayer.so works ok and the firefox path on my amd64 machine is

/usr/lib/firefox/plugins which is where yu need to link or copy the npwrapper.libflashplayer.so file to.

Hope this helps. All went very smooth for me. Thanks again.

---

### Post by daradib on 2007-12-09
> **Jabb3r said:**
> Thanks for the guide. It really helped me to get flash working on Gutsy

Few differences though. Theres no .xpt file after extraction but just doing the copy of libflashplayer.so works ok and the firefox path on my amd64 machine is

/usr/lib/firefox/plugins which is where yu need to link or copy the npwrapper.libflashplayer.so file to.

Hope this helps. All went very smooth for me. Thanks again.

Although everyone is focusing on Hardy and Gutsy 7.10, updates for Dapper, Edgy, and Feisty will eventually be needed. See my (Cyrus Jones) nomination (where the status of the bug is displayed) for those releases on the [Launchpad bug]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890").

---

### Post by daradib on 2007-12-09
In Feisty and Gutsy, nspluginwrapper is taken care of when installing the flashplugin-nonfree package in Ubuntu 64-bit.

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by rambn on 2007-12-12
Ok, I hate to add to this well-covered topic, but here goes...

First of all I'm a noob.  Secondly, I've followed these instructions once already and had success.  Too bad that I re-installed the OS.

I have an AMD64 system with Dapper 6.10 (I can't seem to get any other version of Ubuntu running on my machine due to the Broadcom wireless and Radeon video).  I don't know if I need to post any further specs than that for this issue.  

I get an error during the installation process of the repository update 

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) dapper-upure64 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5CEBE24C2C4C84CC
W: You may want to run apt-get update to correct these problems

I think the link may be bad.  This seems like it should be an easy process.  I have done quite a bit of research through these forums to find an answer to my problem and will continue to do so, but I REALLY could use some help.  ](*,)

---

### Post by daradib on 2007-12-12
> **rambn said:**
> Ok, I hate to add to this well-covered topic, but here goes...

First of all I'm a noob.  Secondly, I've followed these instructions once already and had success.  Too bad that I re-installed the OS.

I have an AMD64 system with Dapper 6.10 (I can't seem to get any other version of Ubuntu running on my machine due to the Broadcom wireless and Radeon video).  I don't know if I need to post any further specs than that for this issue.  

I get an error during the installation process of the repository update 

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) dapper-upure64 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5CEBE24C2C4C84CC
W: You may want to run apt-get update to correct these problems

I think the link may be bad.  This seems like it should be an easy process.  I have done quite a bit of research through these forums to find an answer to my problem and will continue to do so, but I REALLY could use some help.  ](*,)

Try this in Terminal (Applications -> Accessories -> Terminal):

```
gpg --keyserver hkp://keyserver.ubuntu.com:11371 --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
```

---

### Post by rambn on 2007-12-12
> **daradib said:**
> Try this in Terminal (Applications -> Accessories -> Terminal):

```
gpg --keyserver hkp://keyserver.ubuntu.com:11371 --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
```

First of all, thanks for the reply.  I ran the command are here is the error:

chris@chris-laptop:~$ gpg --keyserver hkp://keyserver.ubuntu.com:11371 --recv-keys 2C4C84CC && gpg --export --armor 2C4C84CC | sudo apt-key add -
gpg: directory `/home/chris/.gnupg' created
gpg: new configuration file `/home/chris/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/chris/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/chris/.gnupg/secring.gpg' created
gpg: keyring `/home/chris/.gnupg/pubring.gpg' created
gpg: requesting key 2C4C84CC from hkp server keyserver.ubuntu.com
gpg: no valid OpenPGP data found.
gpg: /home/chris/.gnupg/trustdb.gpg: trustdb created
gpg: key 2C4C84CC: public key "Gianvito Cavasoli <gianvito@nectarine.it>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


by the way, what does this command do?  And by the way, my internet is fine right now.

if it helps, here's the error I get on youtube

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

---

### Post by rambn on 2007-12-13
And another thing... I don't have flashplayer.xpt anywhere.  Could that have something to do with it?  I'm also still have problems with the repositories.

please help.

---

### Post by kylethesir on 2007-12-13
same i open the folder and the only files there are:
flashplayer-installer
libflashplayer.so

and if i try to run the installer in the terminal i get the following error:
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

also I do not have the permissions to move libflashplayer.so into the mozilla/plugins folder

---

### Post by Kilz on 2007-12-13
> **kylethesir said:**
> same i open the folder and the only files there are:
flashplayer-installer
libflashplayer.so

and if i try to run the installer in the terminal i get the following error:
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

also I do not have the permissions to move libflashplayer.so into the mozilla/plugins folder

[Go Here, download script, run script.]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by rambn on 2007-12-14
Kilz - YOU ROCK.  It worked on the first try.  I would, however, like to know how it works.  At least as much as my noobness can allow.  Maybe if I simply review the threads on this topic enough, I'll eventually get it, but if there's anything that could be easily explained I'm all ears.  

I imagine that it wouldn't be too hard to get it working with Flock as well.  I'm guessing just change some of the paths?

Anyway, I'm just grateful I've got my plugin back.

thanks again.

---

### Post by Kilz on 2007-12-14
> **rambn said:**
> Kilz - YOU ROCK.  It worked on the first try.  I would, however, like to know how it works.  At least as much as my noobness can allow.  Maybe if I simply review the threads on this topic enough, I'll eventually get it, but if there's anything that could be easily explained I'm all ears.  

I imagine that it wouldn't be too hard to get it working with Flock as well.  I'm guessing just change some of the paths?

Anyway, I'm just grateful I've got my plugin back.

thanks again.

How it works is it is a shell script. For the most part a shell script is just a series of commands that you can enter into the terminal. The commands are the ones in the howto here. They differ slightly depending on what version of Ubuntu you use. I have found that even though people give great info in howto's , we are all human. Little mistakes happen, the script removes the possibility of those. If you want to see how it works, the script is commented. Lines starting with # tell you what the next little section does.
Flash should also be working with flock, if not it would be easy to symlink the wraped flash plugin to the flock plugin folder. If you need help just tell me where the flock folder is. Odds are its in /usr/lib/flock.

---

### Post by Scarlett on 2007-12-14
Once again, I'm beating my head against the desk over flash.  

I just installed Gutsy and was very happy to see that flashplugin-nonfree and nspluginwrapper were included in the repository.  Youtube works fine.  Yay!!!!  

Comedy Central does not.  ](*,)  It won't even load and I get a pop-up message saying I need the latest flash 9 and it directs me to a page where I can download it.  So now I have flashplayer-installer and libflashplayer.so but the installer won't install. It doesn't do anything.  I tried starting out with the first instruction of this thread and got a message that what I was about to do was potentially hazardous and I should only continue if I knew what I was doing... which I clearly don't.  I have made this work in the past on Feisty and Edgy but I have no idea how I did it.  Help??

---

### Post by maxomai on 2007-12-15
Ugh.

So here's where I'm at:

- 7.10 AMD64 version: check
- flash-nonfree installed: check
- nspluginwrapper installed: check
- flash working: no

I install gnash and I at least get some flash functionality, but not enough to play YouTube videos. 

Does this happen to anyone else? Am I missing some really obvious step? Could it be my laptop?

---

### Post by slowcoach on 2007-12-15
Add the Video DownloadHelper add-on to Firefox and you can save the YouTube videos as .avi files, plus, you don't get all the Flash Adverts (SPAM) when cruising the NET.

---

### Post by Kilz on 2007-12-15
> **maxomai said:**
> Ugh.

So here's where I'm at:

- 7.10 AMD64 version: check
- flash-nonfree installed: check
- nspluginwrapper installed: check
- flash working: no

I install gnash and I at least get some flash functionality, but not enough to play YouTube videos. 

Does this happen to anyone else? Am I missing some really obvious step? Could it be my laptop?

Since you have told us you have gnash installed. Make sure it and all other failed attempts at installing flash or flash alternatives have been removed.

---

### Post by mastergunner on 2007-12-23
OK so how can I install flashplayer to run 64bit Firefox on a amd64 machine?

---

### Post by Kilz on 2007-12-23
> **mastergunner said:**
> OK so how can I install flashplayer to run 64bit Firefox on a amd64 machine?

Yes!

---

### Post by mastergunner on 2007-12-24
How do I do it then? I am a noob and would like a step by step way to do it so I will not screw it up.

---

### Post by agaran on 2007-12-24
The current install_flash_player_9_linux.tar.gz does NOT include the .xpt fiile anymore:

$ tar tvzf *.tar.gz
drwxr-xr-x buildmeister/users 0 2007-11-20 18:24 install_flash_player_9_linux/
-r-xr-xr-x buildmeister/users 21700 2007-11-20 18:24 install_flash_player_9_linux/flashplayer-installer
-rwxr-xr-x buildmeister/users 8119784 2007-11-20 18:24 install_flash_player_9_linux/libflashplayer.so

Any idea why Adobe appears to no longer include this in their distribution?

Any idea of a workaround to make this work in the absence of the xpt file?

---

### Post by Kilz on 2007-12-24
> **mastergunner said:**
> How do I do it then? I am a noob and would like a step by step way to do it so I will not screw it up.

Read the first post in this topic for those instructions. [I also have a install script ]("http://ubuntuforums.org/showthread.php?t=476924")that does it automatically.

---

### Post by mastergunner on 2007-12-24
I do not get the ability to run in terminal when I double click on the installer. Any ideas?

---

### Post by mastergunner on 2007-12-24
Ok got it to install but it does not work. I went to youtube and still get the same message that either I do not have flashplayer or I have on older version. Now what?

---

### Post by Kilz on 2007-12-24
> **mastergunner said:**
> Ok got it to install but it does not work. I went to youtube and still get the same message that either I do not have flashplayer or I have on older version. Now what?

How many different methods have you tried to get flash working?

---

### Post by mastergunner on 2007-12-24
A few. Any ideas?

---

### Post by Kilz on 2007-12-25
> **mastergunner said:**
> A few. Any ideas?

Please give me the results of ```
ls -al /usr/lib/mozilla/plugins
``` and ```
ls -al /usr/lib/firefox/plugins
```

---

### Post by mastergunner on 2007-12-25
Here they are:
brad@Coop:~$ ls -al /usr/lib/mozilla/plugins
total 7956
drwxr-xr-x 2 brad users    4096 2007-12-24 14:52 .
drwxr-xr-x 3 root root     4096 2007-12-24 14:51 ..
-rwxr-xr-x 1 brad users 8119784 2007-11-20 16:24 libflashplayer.so
lrwxrwxrwx 1 brad users      60 2007-12-24 14:52 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


and:
brad@Coop:~$ ls -al /usr/lib/firefox/plugins
total 24
drwxr-xr-x 2 root root  4096 2007-12-24 14:52 .
drwxr-xr-x 5 root root  4096 2007-12-21 11:26 ..
-rw-r--r-- 1 root root 11456 2007-12-04 04:04 libunixprintplugin.so
lrwxrwxrwx 1 root root    60 2007-12-24 14:52 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

Thanks and Merry Christmas.

---

### Post by Kilz on 2007-12-25
It should work there are no conflicting plugins.

---

### Post by mastergunner on 2007-12-25
It is not working. So what should I do now?

---

### Post by rambn on 2008-01-09
my flock directory is in on my desktop. it's been a while since I've looked at this stuff. seems like it should be easy enough.  I'm not sure which file I need to create a symbolic link for.

---

### Post by Kilz on 2008-01-09
> **rambn said:**
> my flock directory is in on my desktop. it's been a while since I've looked at this stuff. seems like it should be easy enough.  I'm not sure which file I need to create a symbolic link for.

The 32bit flash plugin is /usr/lib/mozilla/plugins/libflashplayer.so copy it to the flock/plugins directory and restart frock. You should not need a wrapper since flock is 32bit, just like the plugin file.

---

### Post by rambn on 2008-01-09
thanks, again!  so simple. it's people like you that make ubuntu viable for people like me.:guitar:

---

### Post by narcisgarcia on 2008-01-14
With a 64bit UbuntuStudio 7.10 (Gutsy) I've installed the "ubuntu-restricted-extras" and appears to be installed the "flashplugin-nonfree" package.

But M.Firefox still asks for Flash plugin with Flash web-pages.

---

### Post by edantes on 2008-01-14
> **narcisgarcia said:**
> With a 64bit UbuntuStudio 7.10 (Gutsy) I've installed the "ubuntu-restricted-extras" and appears to be installed the "flashplugin-nonfree" package.

But M.Firefox still asks for Flash plugin with Flash web-pages.

Same here.  Is the plugin supposed to work with the 64-bit Firefox?

---

### Post by vange on 2008-01-15
Yes, the non-free flash plugin is supposed to work. I am running Kubuntu 64 bit, installed the plugin using apt-get, and it works fine for me.

---

### Post by narcisgarcia on 2008-01-15
It may not work when installing via "ubuntu-restricted-extras" ?

---

### Post by vange on 2008-01-17
I am using "kubuntu-restricted-extras", but I suppose the packages are the same as "ubuntu-restricted-extras" regarding the flash plugin.

---

### Post by Kilz on 2008-01-17
There has been a problem with the flashnonfree -plugin in Gutsy for about a month now. It happened after Adobe released a new version of flash. To get flash to work you can follow the manual howto in the first post here, or [run my script.]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by braks on 2008-02-04
Got flash working in firefox 64bit following all but this last step in first post:

> in the folder .mozilla/plugins/ in our /home we can see the file “npwrapper.libflashplayer.so”, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/ [Epiphany works]
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/ [now Firefox works, too]

I don't know if i need to do this but hey its working now so YEAH and THANKS!

---

### Post by Dragonfi on 2008-03-22
It's seems quite like magic for me at the moment ,but it worsks, thanks for the guide :)

---

### Post by MarshyTheKid on 2008-04-03
So I'm not sure what happened. I was on Facebook playing an app(Scrabulous) and it was working fine. I shut down, went to my next class and fired it up again, but it said that I need to have the latest version of Adobe Flash Player, so I thought maybe something was updated and messed with my flash.

I ran
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
sudo apt-get install flashplayer-nonfree
```
And it installed everything. I went back to test it out and it still says I don't have the latest version.
I'm running Gutsy 64-bit with 32bit FireFox 2.0.0.13




```
$ ls -l /usr/lib/mozilla/plugins
total 7984
lrwxrwxrwx 1 root    root       37 2008-04-03 11:52 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwxr-xr-x 1 USERNAME users 8119784 2007-11-20 15:24 libflashplayer.so
lrwxrwxrwx 1 USERNAME users      38 2007-11-27 15:23 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 USERNAME users      39 2007-11-26 13:20 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 USERNAME users      36 2007-11-23 08:23 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 USERNAME users      37 2007-11-23 08:23 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 USERNAME users      34 2007-11-23 08:23 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 USERNAME users      35 2007-11-23 08:23 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 USERNAME users      36 2007-11-23 08:23 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 USERNAME users      37 2007-11-23 08:23 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 USERNAME users      42 2007-11-23 08:23 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 USERNAME users      43 2007-11-23 08:23 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 USERNAME users   27856 2007-05-06 08:48 mozplugger.so
lrwxrwxrwx 1 USERNAME users      60 2008-03-08 15:45 nphelix.so -> /home/USERNAME/Desktop/Programs/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 USERNAME users      61 2008-03-08 15:45 nphelix.xpt -> /home/USERNAME/Desktop/Programs/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 USERNAME users      60 2008-04-03 11:32 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
$ ls -l /usr/lib/firefox/plugins
total 24
lrwxrwxrwx 1 root    root     37 2008-04-03 11:52 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 USERNAME users    39 2007-11-26 13:20 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 USERNAME users    36 2007-11-23 08:23 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 USERNAME users    37 2007-11-23 08:23 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 USERNAME users    34 2007-11-23 08:23 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 USERNAME users    35 2007-11-23 08:23 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 USERNAME users    36 2007-11-23 08:23 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 USERNAME users    37 2007-11-23 08:23 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 USERNAME users    42 2007-11-23 08:23 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 USERNAME users    43 2007-11-23 08:23 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 USERNAME users 11456 2008-03-25 08:19 libunixprintplugin.so
lrwxrwxrwx 1 USERNAME users    35 2008-04-01 08:52 mozplugger.so -> ../../mozilla/plugins/mozplugger.so
lrwxrwxrwx 1 USERNAME users    60 2008-03-08 15:45 nphelix.so -> /home/USERNAME/Desktop/Programs/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 USERNAME users    61 2008-03-08 15:45 nphelix.xpt -> /home/USERNAME/Desktop/Programs/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 USERNAME users    60 2008-04-03 11:32 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

---

### Post by dchurch on 2008-04-08
Hi, I did exactly what you said to do, and hey! it worked.

One problem though, the flash player won't take any input from the mouse after the first time I click it.

I mean, it's like I'm allowed one mouse click.  If I click off of the flash player and onto, say an HTML part of a website, then I can click back inside the flash player again.

Is anyone else getting this problem?

I had this on 7.04 and after a complete fresh install of 7.10.

---

### Post by Mega__ on 2008-05-08
I didn't bother reading the past 30 pages, but I ran into a problem with this script. I was running it on Hardy Heron. Everything went smoothly, but flash would not work. I solved this by running the following command:

```
cp /usr/lib/firefox/plugins/* /usr/lib/firefox-3.0b5/plugins/
```

Now it works perfectly :D

Thanks for the information guys!

---

### Post by Majestic Jim on 2008-07-01
Hi, just wanted to say thanks. Got this to work without any problems, or need to adjust any commands. Good work.

eta: Should've mentioned that I've installed on Hardy, not Edgy.

---

