---
title: "Is there a beryl for 64bit? (Solved)"
date: 2006-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2006-10-12
Yesterday I got my dapper to boot on xgl (howtos missed one package, necessary for 64bit). However, I have included the repositories as explained and used the add key stuff - however, when I give apt-get install beryl-core, Ubuntu gehaves as if it's never heard of it?

So is the beryl-core etc. packages available in repositories for 64bit dapper or what can I do? Can I still install compiz?

---

### Post by Sirkent on 2006-10-12
Try here:
[http://forum.beryl-project.org/topic-3396-1.html](http://forum.beryl-project.org/topic-3396-1.html)

---

### Post by John.Michael.Kane on 2006-10-12
This one has a list of guides that may help.

[**One thread to rule them all v2: Beryl & Official Compiz**]("http://ubuntuforums.org/showthread.php?t=272104")

Then theres this one should you make the move to edgy:

[**HOWTO: Beryl with latest nvidia drivers and Edgy's built in AIGLX (no XGL)**]("http://ubuntuforums.org/showthread.php?t=263851")

For the most part all you should need is the 64bit beryl repo's.

---

### Post by Saubazi on 2006-10-12
I have been adding repositories like no tomorrow but still apt-get won't recognize beryl????

---

### Post by killkoy on 2006-10-12
I built it from source.
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev
sudo update-alternatives --config automake
sudo apt-get build-dep compiz
svn co http://svn.beryl-project.org/trunk/

cd trunk/beryl-core
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-core*.deb beryl-dev*.deb

cd beryl-plugins
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-plugins-data*.deb beryl-plugins*.deb

cd emerald
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald*.deb

cd emerald-themes
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald-themes*.deb

cd beryl-settings
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-settings*.deb

cd beryl-manager
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-manager*.deb beryl*.deb
```

---

### Post by justaguynpc on 2006-10-12
> **SD-Plissken said:**
> This one has a list of guides that may help.

[**One thread to rule them all v2: Beryl & Official Compiz**]("http://ubuntuforums.org/showthread.php?t=272104")

Then theres this one should you make the move to edgy:

[**HOWTO: Beryl with latest nvidia drivers and Edgy's built in AIGLX (no XGL)**]("http://ubuntuforums.org/showthread.php?t=263851")

For the most part all you should need is the 64bit beryl repo's.

I have done nothing (productive) lately to my Kubuntu 6.10 Beta while pouring over all the (conflicting?) info in the forums with regard to Beryl.  I see a lot, read a lot, but am still not convinced I am capable of "pulling-it-off" without hosing my install.  Installing in Gnome is commonplace, but the lack of Kubuntu 64 bit documentation has me concerned.

Is anyone aware of any reputable sources of documentation for a Beryl install on Kubuntu Edgy ?

Cheers!

Am certain my hardware is "up-to-speed"  8)

---

### Post by John.Michael.Kane on 2006-10-12
All howto's bring with them some form of problems nothing's perfect all the time. as to the guides in my post they where writen by reputable sources.

If you need kde beryl howto's look at the site below
[http://forum.beryl-project.org/forum-5-howto](http://forum.beryl-project.org/forum-5-howto)

You can also ask for help on irc channels #beryl and/or #xgl or even #ubuntu-xgl

---

### Post by JAwuku on 2006-10-12
Thanks to your script, Kilkoy, I have successfully compiled beryl for my AMD 64 running Kubuntu Edgy.

I wasn't able to access **svn://metascape.afraid.org/svnroot/beryl**
so I had to use the main Beryl subversion sources:
```
svn checkout svn://svn.beryl-project.org/beryl
```
Also I had to install the package **librsvg2-dev** to satisfy dependencies on building beryl-plugins (the autogen.sh actually tells you which package to install :-D )
```
sudo apt-get install librsvg2-dev
```
So, here is what I did based on your script:
```
sudo aptitude update
sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev
sudo update-alternatives --config automake
sudo apt-get build-dep compiz
svn checkout svn://svn.beryl-project.org/beryl

cd beryl/trunk/beryl-core
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-core*.deb beryl-dev*.deb

cd beryl-plugins
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-plugins-data*.deb beryl-plugins*.deb

cd emerald
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald*.deb

cd emerald-themes
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald-themes*.deb

cd beryl-settings
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-settings*.deb

cd beryl-manager
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-manager*.deb beryl*.deb
```

Again, thank you for posting the script! \\:D/

Now, I just have to find out how to start it up

---

### Post by John.Michael.Kane on 2006-10-12
JAwuku you should be able to add the startup to your session's list

System->Preferences->Sessions

---

### Post by justaguynpc on 2006-10-12
> **SD-Plissken said:**
> All howto's bring with them some form of problems nothing's perfect all the time. as to the guides in my post they where writen by reputable sources.

If you need kde beryl howto's look at the site below
[http://forum.beryl-project.org/forum-5-howto](http://forum.beryl-project.org/forum-5-howto)

You can also ask for help on irc channels #beryl and/or #xgl or even #ubuntu-xgl

No offense intended by the use of "reputable".  Possibly a poor choice of words?  I only meant to infer that frequently when a popular package comes along that is less that point and click to configure, many posts claim to have "the best" way of going about a particular method of install.

Cheers

Will check out the link you provided ...............

---

### Post by John.Michael.Kane on 2006-10-12
No offence taken. just letting you know that the howto's where writen very well,and there are many places for support questions including these very forums.

---

### Post by killkoy on 2006-10-13
the only problem with those howtos is that none of them contain repos with packages for 64bit dapper and niether do any other repos that i have been able to find.

---

### Post by Saubazi on 2006-10-13
Thx for the tips - so it seems there are no packages, eh?
I can't access neither of the svns - connection refused 
what can I do?

---

### Post by killkoy on 2006-10-13
updated previous post with
```
svn co http://svn.beryl-project.org/trunk/
```

---

### Post by killkoy on 2006-10-13
also this is developement software so be sure to report bugs
[http://bugs.beryl-project.org/](http://bugs.beryl-project.org/)

---

### Post by Saubazi on 2006-10-14
Thx bunches I got the svn but got stuck here:

checking for BERYL... configure: error: Package requirements (libpng xcomposite >= 0.3                xfixes                  xdamage xrandr                   ice                     sm                  xinerama libstartup-notification-1.0 >= 0.7) were not met:

Requested 'xcomposite >= 0.3' but version of Xcomposite is 0.2.2.2


I don't understand the first bit since I have libpng and don't know where to get xcomposite - hasty seacrh in packages did not provide the answer...

EDIT seems to be libxcomposite1 the relevan package but I don't have a glue how to get a higher version!?! It says it is already latest...

---

### Post by killkoy on 2006-10-14
add the following line to your sources list by
```
sudo gedit /etc/apt/sources.list
```
The repo:
```
deb http://www.beerorkid.com/compiz dapper main main-amd64
```
If you have this repo already add main-amd64 to the end of the line.

Then type
```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by Saubazi on 2006-10-14
Ok - I admit, I am impressed :)
Needed to install intltool x11proto-gl-dev cause build-pkg was complaining
also at the end I got:
dpkg-deb: building package `beryl-dev' in `../beryl-dev_0.1.0-1_amd64.deb'.
 signfile beryl-core_0.1.0-1.dsc
gpg: skipped "Quinn Storm <livinglatexkali@gmail.com>": secret key not availablegpg: [stdin]: clearsign failed: secret key not available


I suppose this isn't anything serious ...

---

### Post by killkoy on 2006-10-14
> **Saubazi said:**
> gpg: skipped "Quinn Storm <livinglatexkali@gmail.com>": secret key not availablegpg: [stdin]: clearsign failed: secret key not available


Yes i also got that i assume it is because Quinn Storm has set it to sign his secret key to the package:confused:
I assume by your previous post that your build was successful?

---

### Post by PriceChild on 2006-10-14
Yeah all you need to add is a main-amd64 to whatever repos you are using.

e.g.```
deb http://www.beerorkid.com/compiz dapper main main-amd64
```

---

### Post by Saubazi on 2006-10-14
Yeah, I suppose build was succesful at least some .debs resulted from it. Going to test it as soon as I can. 

Pricechild, you don't mean that the beryl package would have been available straight on with apt-get, do you? 

Anyway, thx again killkoy!

---

### Post by killkoy on 2006-10-14
> **Saubazi said:**
> Pricechild, you don't mean that the beryl package would have been available straight on with apt-get, do you? 

No if you go to [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz)
you can see that the only beryl pakages for amd64 dapper (in main or main-amd64 sections) are beryl-plubins-data and emerald-themes

---

### Post by Saubazi on 2006-10-14
Okey, nevermind it runs and compared to my short compiz detour much 
much better.

There are few issues, though - I wonder whether you'd know about them, per change or is there a better forum to ask about beryl stuff?
1) Windows miss the handles (or the title bar) - is there a way to get them?
2) Opening beryl settings always throws me to compiz
3) gmplayer or something crashes me to login screen.

---

### Post by killkoy on 2006-10-14
> **Saubazi said:**
> Okey, nevermind it runs and compared to my short compiz detour much 
much better.

There are few issues, though - I wonder whether you'd know about them, per change or is there a better forum to ask about beryl stuff?
1) Windows miss the handles (or the title bar) - is there a way to get them?
2) Opening beryl settings always throws me to compiz
3) gmplayer or something crashes me to login screen.

1) do you mean that there arn't any title bars? If so did you install beryl-plugins and emerald? are there any errors when you start beryl by typing beryl manager in the console?
Edit - do the effects work (eg cube rotation; ctrl alt sidewaysarrow)

2)can you elaborate? you should have removed cgwd, and csm before installing beryl. Do you get errors when you type beryl-settings

3)What do you mean by or something? Otherwise i cant think what might be causing this problem.

---

### Post by Saubazi on 2006-10-14
> **killkoy said:**
> 1) do you mean that there arn't any title bars? If so did you install beryl-plugins and emerald? are there any errors when you start beryl by typing beryl manager in the console?

2)can you elaborate? you should have removed cgwd, and csm before installing beryl. Do you get errors when you type beryl-settings

3)What do you mean by or something? Otherwise i cant think what might be causing this problem.

1) The windows (terminal or whatever application) looses the window handle - so I can't grab and pull them around from borders. There is output something like this:
$ beryl-manager
$ Couldn't load settings.  Reverting to defaults.
Engine settings loaded
XGL Present
beryl-xgl: Plugin 'settings' already active
beryl-xgl: No GLXFBConfig for depth 32
beryl-xgl: No GLXFBConfig for depth 32
beryl-xgl: No GLXFBConfig for depth 32

** (process:10555): WARNING **: bailing, couldn't find a val for command in
[decoration]->a_command or
[decoration]->d_a_command

** (process:10555): WARNING **: bailing, couldn't find a val for drop_shadows in
[decoration]->a_drop_shadows or
[decoration]->d_a_drop_shadows

2) I have the diamong there for beryl-manager - if I choose the first option beryl-setting manager, do something and select quit, the next time I look the "select window manager" is compiz. I gave now sudo apt-get remove csm and it wants to remove csm and compiz-plugins - I'll see what happens with that...

3) gmplayer or totemplayer and actually just few secs ago glxgears crashed the desktop back to login screen. (The totemplayer did that too during the short detour I made with compiz).

Thanks again! I realize this is still very beta but it looks damn good!

---

### Post by killkoy on 2006-10-14
I think that the fact that you have csm installed is interfering with beryl.

can you list the debs that you installed for beryl?
Did you install all the ones in my first post and did you do the installing and building in the order stated in the post (building beryl-plugins depends on having beryl-dev installed.)?

---

### Post by Saubazi on 2006-10-14
Yes - however, like I wrote I already tried compiz so there might have been bits and pieces still around. I now removed csm - I don't know whether I should now re-install your packages :confused: 

One thing, is though that I had this missing borders problem also with compiz and some googleing shows that I am not the only one having this issue - so far I haven't come across a solution but I keep my thumbs crossed...

---

### Post by thoffland on 2006-10-19
I've managed to get some of it installed, but I'm getting an error and cannot seem to get it to work. 

Here's what happens when I run beryl-manager in a terminal: 

```
beryl-manager doesn't autostart window-manager/decorator
any more. Please consult: man beryl-manager

/home/thoffland/.themes/Crystal dlb/gtk-2.0/gtkrc:9: Unable to find include file: "panel.rc"
/home/thoffland/.themes/Crystal dlb/gtk-2.0/gtkrc:10: Unable to find include file: "toolbar.rc"
/home/thoffland/.themes/Crystal dlb/gtk-2.0/gtkrc:481: Unable to locate image file in pixmap_path: "gfx/menuline.png"
/home/thoffland/.themes/Crystal dlb/gtk-2.0/gtkrc:484: Background image options specified without filename
/home/thoffland/.themes/Crystal dlb/gtk-2.0/gtkrc:910: Unable to locate image file in pixmap_path: "gfx/scrollbar_horizontal_insens.png"
/home/thoffland/.themes/Crystal dlb/gtk-2.0/gtkrc:914: Background image options specified without filename
/home/thoffland/.themes/Crystal dlb/gtk-2.0/gtkrc:939: Unable to locate image file in pixmap_path: "gfx/scrollbar_vertical_insens.png"
/home/thoffland/.themes/Crystal dlb/gtk-2.0/gtkrc:943: Background image options specified without filename

```

Here's my sources.list - I just keep adding more as I find them.

```

# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe


#### My list ####

####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
 deb http://archive.ubuntu.com/ubuntu dapper main
 deb-src http://archive.ubuntu.com/ubuntu dapper main

 deb http://www.beerorkid.com/automatix/apt dapper main

 deb http://archive.ubuntu.com/ubuntu dapper restricted
 deb-src http://archive.ubuntu.com/ubuntu dapper restricted

 deb http://archive.ubuntu.com/ubuntu dapper universe
 deb-src http://archive.ubuntu.com/ubuntu dapper universe

 deb http://archive.ubuntu.com/ubuntu dapper multiverse
 deb-src http://archive.ubuntu.com/ubuntu dapper multiverse


# Dapper Security Updates
 deb http://archive.ubuntu.com/ubuntu dapper-security main
 deb-src http://archive.ubuntu.com/ubuntu dapper-security main

 deb http://archive.ubuntu.com/ubuntu dapper-security restricted
 deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

 deb http://archive.ubuntu.com/ubuntu dapper-security universe
 deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

 deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
 deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
 deb http://archive.ubuntu.com/ubuntu dapper-updates main
 deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

 deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
 deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

 deb http://archive.ubuntu.com/ubuntu dapper-updates universe
 deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

 deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
 deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
 deb http://archive.ubuntu.com/ubuntu dapper-backports main
 deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

 deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
 deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

 deb http://archive.ubuntu.com/ubuntu dapper-backports universe
 deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

 deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
 deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse


deb http://raof.dyndns.org/falcon/ dapper eyecandy main-amd64
deb-src http://raof.dyndns.org/falcon/ dapper eyecandy main-amd64

deb http://www.beerorkid.com/compiz dapper main aiglx main-amd64
deb http://media.blutkind.org/xgl/ dapper main aiglx main-amd64

deb http://www.beerorkid.com/compiz dapper main main-amd64
deb http://ubuntu.compiz.net/ dapper main main-amd64

# Treviño's Beryl-SVN Ubuntu Repository
# GPG key: 81836EBF
deb http://3v1n0.tuxfamily.org dapper beryl-svn main-amd64


deb http://www.beerorkid.com/compiz dapper main main-amd64

```

I would really like to get it running, I've seen some screenshots, but would like to see it in person!!!

---

### Post by killkoy on 2006-10-19
how did you install it, from source like in my previous post?

Your sources list contains what are effectivly duplicate repos, although that shouldnt effect the running of beryl

---

### Post by thoffland on 2006-10-19
> **killkoy said:**
> how did you install it, from source like in my previous post?

Your sources list contains what are effectivly duplicate repos, although that shouldnt effect the running of beryl

Yes, actually your way was the only way I could get it installed this far. One problem I think is that when I tried to install emerald, it says something like "dependancy emerald >0.1 is required" and that it referred to another package that could not be installed or referred to from another source. 

Sorry I dont have the exact error message, but I figured you'll probably know what I'm saying. 

Thanks for any help!

---

### Post by killkoy on 2006-10-19
Am I right in saying that you dont have emerald installed then? 

can you give me a list of the beryl packages that are installed?

Could you build emerald or did it fail at the installing the deb stage?

Try running ```
sudo aptitude update && sudo aptitude dist-upgrade
```
Then building emmerald again (and record any dependancy errors you get)

---

### Post by thoffland on 2006-10-19
> **killkoy said:**
> Am I right in saying that you dont have emerald installed then? 

can you give me a list of the beryl packages that are installed?

Could you build emerald or did it fail at the installing the deb stage?

Try running ```
sudo aptitude update && sudo aptitude dist-upgrade
```
Then building emmerald again (and record any dependancy errors you get)

OK, here it is. 

I tried "sudo apt-get install emerald" and got this: 

```
sudo apt-get install emerald
Reading package lists... Done
Building dependency tree... Done
Package emerald is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald has no installation candidate

```

So I figured I'd try starting you're method from the beginning and got this error: 

```
 sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

```

And I've tried [this other howto]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit") and tried this command ```
sudo apt-get install xserver-xgl compiz-gnome emerald emerald-themes beryl
``` which gives me the same errors. 

How to I get a list of what Beryl packages are installed? 

If I click "System" then preferences I see: 

Beryl Settings Manager - clicking it does nothing but I can open beryl-manager through the terminal.
Compiz Settings Manager - opens the configuration screen
Emerald Theme Manager - clicking it does nothing

But that doesn't give the full list I'm sure.

---

### Post by killkoy on 2006-10-19
do you have synaptic open when you run those comands?
you wont be able to run sudo apt-get install emerald as there are no repos with emerald in them.

to get a list open synaptic > System > Admin > Synaptic
Then click on search and type beryl, list the beryl packages installed, then search compiz and list those packages and then type emerald and list.

---

### Post by thoffland on 2006-10-19
> **killkoy said:**
> do you have synaptic open when you run those comands?
you wont be able to run sudo apt-get install emerald as there are no repos with emerald in them.

to get a list open synaptic > System > Admin > Synaptic
Then click on search and type beryl, list the beryl packages installed, then search compiz and list those packages and then type emerald and list.

Synaptic isn't open when I'm trying to install it. 

In synaptic, here's what it says: 
Under beryl: 
beryl-plugins-data

Under Compiz: 
compiz
compiz-core
compiz-plugins
csm

Under Emerald:
Nothing is installed, and when I try to install "emerald-themes" I get this error:  Depends: emerald (>=0.1) but it is not installable

#-o

---

### Post by killkoy on 2006-10-20
**Ok First tidy up your sources list**

This is a sources list that I think contains all the sources in your previous post with the duplicates removed. 
If you want to use this replace your previous sources.list completely with the one bellow. Don't just add to it.
```
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted

# gpg --keyserver subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages)
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted

# Ubuntu supported packages (sources)
#deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
#deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages)
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources)
#deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
#deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu Dapper Backports
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Ubuntu Dapper Backports (sources)
#deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

#wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -
deb http://ubuntu.moshen.de/ dapper eyecandy
deb-src http://ubuntu.moshen.de/ dapper eyecandy

#wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
deb http://www.beerorkid.com/compiz dapper main aiglx main-amd64
deb-src http://www.beerorkid.com/compiz dapper main aiglx main-amd64
deb http://media.blutkind.org/xgl/ dapper main aiglx main-amd64
deb http://ubuntu.compiz.net/ dapper main main-amd64
```

I have removed this as i think it only contains i386 packages
```
# Treviño's Beryl-SVN Ubuntu Repository
# GPG key: 81836EBF
deb http://3v1n0.tuxfamily.org dapper beryl-svn main-amd64
```
**2) install graphics drivers**

**For nvidia**
run ```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install nvidia-glx
```

**3) edit xorg.conf**

first back it up
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then edit it
```
sudo gedit /etc/X11/xorg.conf
```
look for    Section "Module"   if this section contains  Load "dri"  or  Load "glcore"  comment them out like this ```
#	Load	"dri"
#	Load	"glcore"
```
Then ensure that this section contains ```
 	Load	"glx"
```
**For nvidia**
Scroll down to Section "Device" and ensure that the driver is nvidia and there is the renderaccel option so that this section will look a bit like this
```
Section "Device"
	Identifier	"NVIDIA Corporation NV41.0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option "RenderAccel" "true"
EndSection
```
don't change the identifier or the BusID. The one above is only an example.

**4) Now install xgl**
```
sudo aptitude install xserver-xgl libgl1-mesa libglitz-glx1
```
There are two ways to run xgl (only do one)

**Method 1, run as part of regular session**
edit gdm.conf-custom
```
sudo gedit /etc/gdm/gdm.conf-custom
```
At the bottom (in the servers bit) add this
```
[servers]
0=Xgl 

[server-Xgl]
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```

**Method 2, run as a separate session** (from [http://www.ubuntuforums.org/showthread.php?t=260452](http://www.ubuntuforums.org/showthread.php?t=260452) )

create a script to start xgl
```
sudo gedit /usr/bin/startxgl.sh
```
and paste this in then save and exit
```
#!/bin/sh 
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session
```
make the script executable
```
sudo chmod +x /usr/bin/startxgl.sh
```
 Then add the script to sessions
```
sudo gedit /usr/share/xsessions/xgl.desktop
```
paste this in then save and exit
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```

**5) Installing beryl from source** not recommended for people that have repositories for beryl. Beryl is still in development and could cause kittens to die, nukes to go off and an economic collapse, you've been warned :p (as far as i know there are no repositories for amd64 dapper, if anybody knows of one please tell me).

First remove compiz
```
sudo aptitude remove compiz-core compiz-gnome cgwd csm
```

Run the following one line at a time so that you can identify any errors. 
Pay particular attention when you type ./autogen.sh --prefix=/usr as you may be informed of unmet dependencies. If you get informed of one install it (sudo aptitude install package) then go back to the last make clean line and carry on.
Please post the unmet dependency up here so that I can add it to this guide.

The following should be done in order.

```
sudo aptitude update
sudo aptitude dist-upgrade
sudo apt-get update
sudo apt-get build-dep compiz
sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev subversion libneon25-dev libapr0-dev libsvn0-dev
sudo update-alternatives --config automake
svn co http://svn.beryl-project.org/trunk/

cd trunk/beryl-core
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-core*.deb beryl-dev*.deb

cd beryl-plugins
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-plugins-data*.deb beryl-plugins*.deb

cd emerald
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald*.deb

cd emerald-themes
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald-themes*.deb

cd beryl-settings
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-settings*.deb

cd beryl-manager
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-manager*.deb beryl*.deb
```
Beryl should now be installed

**6)Add beryl to startup programs**
System > Preferences > Sessions > Startup Programs
Add beryl-manager

**7) restart x **

**Important, If x fails to start do step 8**

press <ctrl><alt><back>
login and enjoy beryl :D

**8. only do if x fails to start**
go to terminal
<ctrl><alt><f1>
login
type ```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo reboot
```

---

### Post by thoffland on 2006-10-20
First, let me thank you for the time it probably took you to lay this all out for me. I really appreciate it. 

I got down to the installation part and everything seemed to go well until this point: 
```

sudo apt-get build-dep compiz
```
**gave me this error:**
Reading package lists... Done
Building dependency tree... Done
E: You must put some 'source' URIs in your sources.list

Same thing happened with the next line:
```

sudo apt-get build-dep compizsudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev
```

**Error:**
Reading package lists... Done
Building dependency tree... Done
E: You must put some 'source' URIs in your sources.list

These are similar to the problems I was having before, but I cant seem to find the right repositories? 

Again, thanks for your time.

-------------------------------------------------------------
Edit: 

I added these repositories: 

deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb-src [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy

and tried again, this is what I got:

```
sudo apt-get build-dep compiz
``` 
**gave me:**

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 ```
sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev
```
**Gave me: **
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```
svn co http://svn.beryl-project.org/trunk/
```
**gave me:**
bash: svn: command not found

```
sudo update-alternatives --config automake 
```
**gave me: **
There is only 1 program which provides automake
(/usr/bin/automake-1.9). Nothing to configure.

---

### Post by killkoy on 2006-10-20
ok I've edited the sources list so you've got some deb-src(id commented them out before) my mistake:oops: 

As for the svn not found, run ```
sudo aptitude install subversion
``` before step 5. I'll add that to my previous post.

> 
Code:

sudo update-alternatives --config automake

gave me:
There is only 1 program which provides automake
(/usr/bin/automake-1.9). Nothing to configure.
Thats fine, its what i expected:p

---

### Post by thoffland on 2006-10-20
Kilkoy, thank you so much!! 

It's up and running and I cant wait to play with it. I just had time to install it and reboot and see that it was running. 

Just some notes: I needed to "sudo" some of those commands, and the "make clean" said it didn't have a target or something, so I just bypassed those and it worked. I'm sure every system has something different about it. 

Thanks again, I'm sure this is going to help alot of other people too. ;) :D

---

### Post by killkoy on 2006-10-21
> **thoffland said:**
> Kilkoy, thank you so much!! 

It's up and running and I cant wait to play with it. I just had time to install it and reboot and see that it was running. 

Just some notes: I needed to "sudo" some of those commands, and the "make clean" said it didn't have a target or something, so I just bypassed those and it worked. I'm sure every system has something different about it. 

Thanks again, I'm sure this is going to help alot of other people too. ;) :D

No problem:)
The make clean output is fine. That line was put in incase you had a previous failed attempt at compiling it.
what commands did you need to sudo? no worries if you cant remember;)

---

### Post by thoffland on 2006-10-21
I'm pretty sure I needed to sudo the ```
svn co http://svn.beryl-project.org/trunk/
```command and the two in the middle of each block:

```

cd trunk/beryl-core
make clean
**sudo ./autogen.sh --prefix=/usr**
**sudo fakeroot dpkg-buildpackage**
cd ..
sudo dpkg -i beryl-core*.deb beryl-dev*.deb
```

And just like you said, I had some library dependancies that needed to be installed but only for Emerald... otherwise I was good to go. 

I have another quick question, I noticed we used both "aptitude" and "apt-get". What is the difference between the two? 

And, do you have this howto on another page anywhere? I'd like to link to it.

---

### Post by killkoy on 2006-10-21
> **thoffland said:**
> I'm pretty sure I needed to sudo the ```
svn co http://svn.beryl-project.org/trunk/
```command and the two in the middle of each block:

```

cd trunk/beryl-core
make clean
**sudo ./autogen.sh --prefix=/usr**
**sudo fakeroot dpkg-buildpackage**
cd ..
sudo dpkg -i beryl-core*.deb beryl-dev*.deb
```
That strange, I didnt need to do this:-k
> I have another quick question, I noticed we used both "aptitude" and "apt-get". What is the difference between the two? 
See [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)
> And, do you have this howto on another page anywhere? I'd like to link to it.
I think that now that ive writen it i may adapt it then post it in the howtos section. I'll reply with the link.

---

### Post by killkoy on 2006-10-21
[http://www.ubuntuforums.org/showthread.php?t=281613](http://www.ubuntuforums.org/showthread.php?t=281613)

---

### Post by s_spiff on 2006-10-22
> **killkoy said:**
> [http://www.ubuntuforums.org/showthread.php?t=281613](http://www.ubuntuforums.org/showthread.php?t=281613)
hey, I tried that how to, but I have a onboard nvidia graphics card, a 6100 series on a gigabyte motherboard, so how will the howto differ from the one you've given? I've been trying to install beryl for a few days now, but its has been a futile mess! I'm on a amd64 DD archtype. I have a Gigabyte motherboard iDNA series, 6100 series GeForece Nviadia Onboard graphics card, and 512 ram. I took some help from the irc forums and tried building it from the svn, but the makeall command didnt work without using sudo. Any sorlutions?

---

### Post by alek66 on 2006-10-23
I am using Dapper...
What are the repositories to use, I saw a lotttttt but I cant make up my mind, on weather wich one is the most updated one.
I am using Nvidia.

---

