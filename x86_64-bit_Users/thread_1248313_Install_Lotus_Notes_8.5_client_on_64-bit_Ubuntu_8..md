---
title: "Install Lotus Notes 8.5 client on 64-bit Ubuntu 8.04 LTS"
date: 2009-08-24
forum: x86 64-bit Users
---

### Post by akkornel on 2009-08-24
[CENTER]**[SIZE="5"]Attention![/SIZE]**

**Ubuntu 9.10 (Karmic) breaks Lotus Notes 8.5 client.  If you want to use Lotus Notes 8.5 client on 64-bit Ubuntu, use Hardy or Jaunty.**[/CENTER]

Hello all!

A month or so ago, I managed to get the Lotus Notes 8.5 client installed on my Hardy Heron (Ubuntu 8.04 LTS) desktop, running on AMD Opteron (64-bit) processors.  I used the documentataion from [http://www.rayd.co.uk/blogs/rayblog.nsf/d6plinks/Ubuntu64](http://www.rayd.co.uk/blogs/rayblog.nsf/d6plinks/Ubuntu64), but the web page appears to be gone.

I did not want the information to disappear entirely, so while Google was still caching the original page, I decided to move the instructions here!  I also use some documentataion from [http://www.glump.net/howto/notes_8_on_ubuntu](http://www.glump.net/howto/notes_8_on_ubuntu), along with my own investigations and the notes posted by people in this thread.

I particularly liked this HOWTO, and think it's worth keeping around, because it's the only one I've found that keeps everything in packages.  There's no installation of files from .tar archives, or running setup.sh commands, or things like that (well, unless you're running on Karmic).  Even the required 32-bit libraries are installed as packages, thanks to *getlibs*.

It is worth noting that not everything works perfectly.  The Open button on attachments does not always work (**this is now fixed!**); and in some cases opening address book items, or the feature in meeting entries that shows everyone's schedule, causes the screen to freeze or slow (I'm thinking something to do with my graphics card/driver/settings); and one of my applications sends me an automated HTML email that renders pretty badly on screen (**this is now fixed!**).  If anyone else sees these problems, **and** has solutions, let me know!

However, there are many things that do work properly.  In particular, address book and Journal sync to BlackBerry work, as does the various in-house applications my workplace uses.  The built-in SameTime client also works.

***Karmic users, alert!!***  Lotus Notes 8.5 client is **broken** in Karmic.  Karmic does not provide some of the required software packages, and something in the display system has changed enough to break Lotus Notes.  Although we can help you find the missing packages, I don't yet have any info on how to fix the display problems.  This post will be updated as new information emerges!

**Part I: Install core 32-bit libraries, fonts, and getlibs**

First, install the 32-bit libraries that apt-get will allow you to easily install, along with some non-free fonts which Lotus Notes likes to use, and the curl command to download other stuff later on.

```
sudo apt-get update
sudo apt-get install ia32-libs ttf-xfree86-nonfree curl

```

The ia32-libs package is part of the Ubuntu universe package repository; the ttf-xfree86-nonfree package is part of the Ubuntu multiverse repository.  If you get an error like *E: Couldn't find package ia32-libs*, then your Ubuntu installation is not configured to get packages from these repositories.  Please see [Adding Repositories in Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu") for instructions on how to enable the universe and multiverse repositories, and then try the *apt-get* command again.

**Part II: Download and install the required 32-bit library packages**

Lotus Notes relies on lots of different libraries, which are available as Ubuntu packages.  Hardy and Jaunty have all of the packages needed.  Karmic, unfortunately, dropped some of the packages needed by Losut Notes, so the Jaunty versions need to be downloaded and installed.  Older versions of Ubuntu are not covered here.

Follow one of the two procedures below, depending on which Ubuntu version you are using:

***For Hardy & Jaunty***

Download the [getlibs-all package]("http://ubuntuforums.org/showthread.php?t=474790") from [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb), and install it.  Then have the *getlibs* command download and install the 32-bit versions of all the necessary libraries.

```
cd /tmp
curl -O http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs -p libavahi-client3 libavahi-common3 libavahi-glib1 libbonoboui2-0 libcroco3 libdbus-1-3 libdbus-glib-1-2 libeel2-2 libgnome2-0 libgnomecanvas2-0 libgnome-keyring0 libgnome-menu2 libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0 libgsf-1-114 libgsf-1-dev librsvg2-2 librsvg2-common libselinux1 libsepol1 libstartup-notification0 libxkbfile1 gtk2-engines-ubuntulooks gtk2-engines-murrine
```

***For Karmic only***

Download the [getlibs-all package]("http://ubuntuforums.org/showthread.php?t=474790") from [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb), and install it.  Then have the *getlibs* command download and install most the 32-bit versions of all the necessary libraries.  Two required libraries (libeel2 and libstdc++5) are not provided by Karmic, so you will have to download the versions available from Jaunty.

```
cd /tmp
curl -O http://frozenfox.freehostia.com/cappy/getlibs-all.deb -O http://mirrors.kernel.org/ubuntu/pool/main/e/eel2/libeel2-2_2.26.0-0ubuntu2_amd64.deb -O http://mirrors.kernel.org/ubuntu/pool/main/e/eel2/libeel2-data_2.26.0-0ubuntu2_all.deb -O http://mirrors.kernel.org/ubuntu/pool/main/e/eel2/libeel2-2_2.26.0-0ubuntu2_i386.deb -O http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb
sudo dpkg -i getlibs-all.deb libeel2-data*.deb libeel2-*_amd64.deb
sudo dpkg -i --force-architecture libeel2-*_i386.deb libstdc++5*.deb
sudo getlibs -p libavahi-client3 libavahi-common3 libavahi-glib1 libbonoboui2-0 libcroco3 libdbus-1-3 libdbus-glib-1-2 libgnome2-0 libgnomecanvas2-0 libgnome-keyring0 libgnome-menu2 libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0 libgsf-1-114 libgsf-1-dev librsvg2-2 librsvg2-common libselinux1 libsepol1 libstartup-notification0 libxkbfile1 gtk2-engines-ubuntulooks gtk2-engines-murrine
```

**Part III: Install Lotus Notes 8.5 Client**

Obtain the Lotus Notes 8.5 Linux client .deb files from your Lotus Notes administrator.  He/she should look for and download the "C1W0TEN.tar" file from IBM.  Let's assume the file has been copied to the */tmp* directory.

*Side Note 1:* I originally tried installing just the notes package, but the client would not run, so I just gave up and installed the others.  It appears then that each package has bits that are used by the other Notes packages, but this information was not included in the dependency information when the packages were made.

*Side Note 2:* Well, it seems like what I said in Side Note 1 was wrong!  I'm now running Notes on my 64-bit Hardy workstation with only the Notes and SameTime packages installed.  Given that, the best advise I can give is to install only the Lotus packages that you need, and install everything else only if you seem to be having problems!

Each Lotus Notes package contains a different piece of functionality:

[LIST]
[*]**ibm-lotus-notes**: Lotus Notes client
[*]**ibm-lotus-sametime**: Lotus Notes SameTime client (*requires SameTime server*)
[*]**ibm-lotus-activities**: Lotus Notes Connections Activities client (*requires Activities server*)
[*]**ibm-lotus-cae-8.5**: Lotus Notes Composite Application Editor (*not totally sure what this is*)
[*]**ibm-lotus-symphony**: Lotus Symphony
[/LIST]

```
tar -xf C1W0TEN.tar
sudo dpkg -i --force-architecture ibm_lotus_notes-8.5.i586.deb
# If you have an Activities server...
sudo dpkg -i --force-architecture ibm_lotus_activities-8.5.i586.deb
# If you want the Composite Application Editor...
sudo dpkg -i --force-architecture ibm_lotus_cae-8.5.i586.deb
# If you have a SameTime server...
sudo dpkg -i --force-architecture ibm_lotus_sametime-8.5.i586.deb
# If you want Lotus Symphony
sudo dpkg -i --force-architecture ibm_lotus_symphony-8.5.i586.deb
# Or, if you want everything, then install everything in one command:
sudo dpkg -i --force-architecture ibm_lotus_notes-8.5.i586.deb ibm_lotus_activities-8.5.i586.deb ibm_lotus_cae-8.5.i586.deb ibm_lotus_sametime-8.5.i586.deb ibm_lotus_symphony-8.5.i586.deb
```

Before we go on, we have to replace a Notes executable.  The *openwith* executable shipped by Notes doesn't seem to function properly (even with all 32-bit libraries installed), so we replace it with a link to GNOME's equivalent command:

```
cd /opt/ibm/lotus/notes
sudo mv openwith openwith.old
sudo ln -s /usr/bin/gnome-open openwith
```

At this point, you should see the Lotus Notes entries in the Applications menu, Office sub-menu.  If you can't see them, or you'd like to run Lotus Notes from the command-line, use the following command:

```
cd /opt/ibm/lotus/notes/framework/ ; ../notes
```

On first launch, you should be prompted to agree to the license agreement, and then you'll be run through the new user setup process.  Your Lotus Notes administrator can help you with the necessary information.

Your data directory is located at path *~/lotus/notes/data*.  You do not need to copy your ID file, because on first-time setup Notes will give you the option of placing a copy in your data directory.  However, other files, particularly .nsf files that contain your data (such as *journal.nsf*) should be copied/moved into the data directory.  Notes still might ask you to locate the file the first time it's needed, but not after that.

**A note on fonts:** By default, Lotus Notes uses the Luxi font.  Depending on your system, with some emails, the font may look extremely jaggy and unpleasent.  If this happens to you, here is how to fix the problem:  Run the command `sudo dpkg-reconfigure fontconfig-config`.  Enter your password when prompted.  When you are asked to select a "Font tuning method for screen", select 'Autohinter'.  The other options you can leave alone, or set to taste, but as long as you select 'Autohinter', the Luxi font will look good.

**That's it!**  I hope the tutorial that was written, and disappeared, but is now back, and updated, is helpful for you!  By all means, though, if you use 64-bit Ubuntu, do not assume that this is _the_ solution to the original problem:  Talk to your IT department, IT manager, or other person in your organization who works/communicates with IBM; and have them make IBM aware of that fact that you are using Lotus Notes 8.5 client on a 64-bit Ubuntu installation, and that they should release packages that are "out of the box" compatible!  NetBackup, Lotus Notes, and other enterprise applications may have compatible versions now (either out of the box or with workarounds), but they won't remain like that, or get better, if you don't send feedback saying "I use this!" and "I want this!"

Later!

---

### Post by akkornel on 2009-08-28
I've added a few new lines of code to the Notes installation step.  When attempting to open an attachment, Notes would not do anything.  This was because of Notes' *openwith* command, which would not work even when all of the 32-bit libraries were present.  The solution is to replace it with a symlink to GNOME's *gnome-open* command (I'm not sure what the equivalent would be for KDE).

This information came from [http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllThreadedWeb/68f2e44b9808deeb852576190026ffd9?OpenDocument](http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllThreadedWeb/68f2e44b9808deeb852576190026ffd9?OpenDocument).

---

### Post by Strelock on 2009-08-31
Great guide!!! I hope a day would come when IBM would make an installation howto )

---

### Post by Valkrist! on 2009-10-14
Hi, 

Great guide. It has been a while and I have downloaded the trial. 

However I came a cross some issues:

[LIST=1]
[*]I could not install library ia32-libs
root@vindicator:~# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs
[*]I had to install the packages in two phases
dpkg -i --force-architecture ibm_lotus_notes-8.5.i586.deb
dpkg -i --force-architecture ibm_lotus_activities-8.5.i586.deb ibm_lotus_cae-8.5.i586.deb ibm_lotus_sametime-8.5.i586.deb ibm_lotus_symphony-8.5.i586.deb
[/LIST]

---

### Post by akkornel on 2009-10-14
Hello!

> **Valkrist! said:**
> Hi, 

Great guide. It has been a while and I have downloaded the trial. 

However I came a cross some issues:

[LIST=1]
[*]I could not install library ia32-libs
root@vindicator:~# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs
[/LIST]

I'm sorry, I guess I should have said that the ia32-libs package is in the universe repository.  In my case, I've got the following lines enabled in */etc/apt/sources.list*:

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
```

(you might be using a different server than us.archive.ubuntu.com)

Running *apt-cache policy ia32-libs* on my machine says that the latest hardy version of ia32-libs (2.2ubuntu11.2) is available in hardy-updates/universe and hardy-security/universe, so if you enable the hardy-updates universe, or the hardy-security lines, in your apt sources.list, and then do an *apt-get update*, you should be able to get the ia32-libs package.

> **Valkrist! said:**
> 
[LIST=2][*]I had to install the packages in two phases
dpkg -i --force-architecture ibm_lotus_notes-8.5.i586.deb
dpkg -i --force-architecture ibm_lotus_activities-8.5.i586.deb ibm_lotus_cae-8.5.i586.deb ibm_lotus_sametime-8.5.i586.deb ibm_lotus_symphony-8.5.i586.deb
[/LIST]

Could you please tell me why?  Did you get an error of some sort when you tried to install all of the Lotus packages in one go?

---

### Post by Valkrist! on 2009-10-17
Hi,
When I tried to install all notes packages in one command I received an error message with regard to dependancies.
The packages I installed with the second command depend on Lotus Notes.

---

### Post by Valkrist! on 2009-10-17
Ps. I am using Ubuntu distro of 9.04

---

### Post by Valkrist! on 2009-10-17
Well I had to reinstall lotus notes ... because I managed to get my laptop (Dell inspiron 1720) killed. (This because I used the Dell media button that starts a restricted os with only multi media center like options. That worked, only it totally f*c*ed up my MBR, Grub and partition table. Though the last might be because of my trying to get grub reinstalled. Don't press the dell button when you have a dual boot system (with all dell sh*t installed)

But this gave me the opportunity to install notes again:

Here are the errors:
root@vindicator:/media/Data/software/software-ibm/Lotus-Notes-85b-debian-C1WR1EN# dpkg -i --force-architecture ibm_lotus_notes-8.5.i586.deb ibm_lotus_activities-8.5.i586.deb ibm_lotus_cae-8.5.i586.deb ibm_lotus_sametime-8.5.i586.deb ibm_lotus_symphony-8.5.i586.deb
Selecting previously deselected package ibm-lotus-notes.
(Reading database ... 121675 files and directories currently installed.)
Unpacking ibm-lotus-notes (from ibm_lotus_notes-8.5.i586.deb) ...
Selecting previously deselected package ibm-lotus-activities.
dpkg: regarding ibm_lotus_activities-8.5.i586.deb containing ibm-lotus-activities, pre-dependency problem:
 ibm-lotus-activities pre-depends on ibm-lotus-notes (= 8.5-20090107.1537)
  ibm-lotus-notes is unpacked, but has never been configured.
dpkg: error processing ibm_lotus_activities-8.5.i586.deb (--install):
 pre-dependency problem - not installing ibm-lotus-activities
Selecting previously deselected package ibm-lotus-cae.
dpkg: regarding ibm_lotus_cae-8.5.i586.deb containing ibm-lotus-cae, pre-dependency problem:
 ibm-lotus-cae pre-depends on ibm-lotus-notes (= 8.5-20090107.1537)
  ibm-lotus-notes is unpacked, but has never been configured.
dpkg: error processing ibm_lotus_cae-8.5.i586.deb (--install):
 pre-dependency problem - not installing ibm-lotus-cae
Selecting previously deselected package ibm-lotus-sametime.
dpkg: regarding ibm_lotus_sametime-8.5.i586.deb containing ibm-lotus-sametime, pre-dependency problem:
 ibm-lotus-sametime pre-depends on ibm-lotus-notes (= 8.5-20090107.1537)
  ibm-lotus-notes is unpacked, but has never been configured.
dpkg: error processing ibm_lotus_sametime-8.5.i586.deb (--install):
 pre-dependency problem - not installing ibm-lotus-sametime
Selecting previously deselected package ibm-lotus-symphony.
dpkg: regarding ibm_lotus_symphony-8.5.i586.deb containing ibm-lotus-symphony, pre-dependency problem:
 ibm-lotus-symphony pre-depends on ibm-lotus-notes (= 8.5-20090107.1537)
  ibm-lotus-notes is unpacked, but has never been configured.
dpkg: error processing ibm_lotus_symphony-8.5.i586.deb (--install):
 pre-dependency problem - not installing ibm-lotus-symphony
Setting up ibm-lotus-notes (8.5-20090107.1537) ...

Errors were encountered while processing:
 ibm_lotus_activities-8.5.i586.deb
 ibm_lotus_cae-8.5.i586.deb
 ibm_lotus_sametime-8.5.i586.deb
 ibm_lotus_symphony-8.5.i586.deb

---

### Post by Valkrist! on 2009-10-17
I did a bit of searching. I do not have a 64 bit os installed. ... 

ia32-libs is needed on 64 bit machines in order to use 32 bit software

---

### Post by akkornel on 2009-10-17
> **Valkrist! said:**
> I did a bit of searching. I do not have a 64 bit os installed. ... 

ia32-libs is needed on 64 bit machines in order to use 32 bit software

That is correct.  That is why I called this thread "Install Lotus Notes 8.5 client on **64-bit** Ubuntu 8.04 LTS"!

If you are running 32-bit, then you can (and should) be using the [official installation instructions]("http://www.elink.ibmlink.ibm.com/publications/servlet/pbi.wss?CTY=US&FNC=SRX&PBL=GC27240400") that are provided by IBM.  If you decide to read it online, go to Notes Client Installation and Upgrade -> Installing Notes in a multi-user environment -> Installing and upgrading Notes on Linux.

If, once you follow those instructions, you continue to have problems getting Lotus Notes installed, you should work with your Lotus Notes administrator to get IBM support involved.  Good luck!

---

### Post by Ellery McKenzie on 2009-11-02
So close yet so far ....

getlibs -p libeel2-2 gets me nowhere.  The other 32-bit packages came down fine.

Linux is a new thing for me so I'm feeling my way through.  I've managed to establish that I probably don't have the right repository configured but in my ignorance I'm damned if I can work out how to find the correct repository.

On a hunch I pushed on with the install anyway.  Notes almost works!  There was a grizzle about some eclipse problem but I didn't think to note it down straight away.  Grrr.  I'll come back to this later.

So for now I've come back to this libeel2-2.  That brick wall is beginning to hurt my head.

So.... how do I find where to get libeel2-2 from?

I'd be fine with just being told where it is but being told how to do it myself seems a better approach (give a man a fish, teach him to fish, etc).

PS: I'm on Karmic

---

### Post by Ellery McKenzie on 2009-11-03
Well, I've now found and installed libeel2-2. :D

For those who are as confused as I was, do the following:

1. add the following to /etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu/ jaunty main
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main
```

TBH, i've no idea if the second line is necessary and I didn't try without it.  Maybe someone knowledgeable can elaborate on that.

2. run

```
sudo apt-get update
sudo getlibs -p libeel2-2
```3. remove additions to /etc/apt/sources.list


Essentailly what I've found is that llibeel2-2 isn't present in the Karmic repositories but is present in the Jaunty repositories.

Still got some issues with Notes itself - no replicator, can't create emails ...

Working on them.  Will post an update at some point.


//just a little bit less of a noob today ;-)

---

### Post by anjali.thampi on 2009-11-11
Hi,
  When i try to force install the .deb packages , i get the following error.Please help!

```
~/Installables/lotus$ sudo dpkg -i --force-architecture ibm_lotus_notes-8.5.i586.deb ibm_lotus_activities-8.5.i586.deb ibm_lotus_cae-8.5.i586.deb ibm_lotus_sametime-8.5.i586.deb ibm_lotus_symphony-8.5.i586.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 185796 files and directories currently installed.)
Preparing to replace ibm-lotus-notes 8.5-20080822.1349 (using ibm_lotus_notes-8.5.i586.deb) ...
cat: /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties: No such file or directory
Unpacking replacement ibm-lotus-notes ...

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace ibm-lotus-activities 8.5-20080822.1349 (using ibm_lotus_activities-8.5.i586.deb) ...
cat: /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties: No such file or directory
Unpacking replacement ibm-lotus-activities ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace ibm-lotus-cae 8.5-20080822.1349 (using ibm_lotus_cae-8.5.i586.deb) ...
cat: /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties: No such file or directory
Unpacking replacement ibm-lotus-cae ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace ibm-lotus-sametime 8.5-20080822.1349 (using ibm_lotus_sametime-8.5.i586.deb) ...
cat: /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties: No such file or directory
Unpacking replacement ibm-lotus-sametime ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace ibm-lotus-symphony 8.5-20080822.1349 (using ibm_lotus_symphony-8.5.i586.deb) ...
cat: /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties: No such file or directory
Unpacking replacement ibm-lotus-symphony ...
Setting up ibm-lotus-notes (8.5-20080822.1349) ...

Setting up ibm-lotus-activities (8.5-20080822.1349) ...
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/deploy/install.xml.orig': No such file or directory

Setting up ibm-lotus-cae (8.5-20080822.1349) ...
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/deploy/install.xml.orig': No such file or directory

Setting up ibm-lotus-sametime (8.5-20080822.1349) ...
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/deploy/install.xml.orig': No such file or directory

Setting up ibm-lotus-symphony (8.5-20080822.1349) ...
mv: cannot stat `/opt/ibm/lotus/notes/framework/rcp/deploy/install.xml.orig': No such file or directory
```When i checked in my /opt/ibm/lotus/notes/framework/rcp directory, only the following were found:

```
/opt/ibm/lotus/notes/framework/rcp$ ls -lrt
total 232
-rwxr-xr-x 1 root root 217090 2008-08-24 03:41 rcplauncher
drwxr-xr-x 5 root root   4096 2009-11-11 10:39 eclipse
-rw-r--r-- 1 root root    222 2009-11-11 10:40 plugin_customization.ini
drwxr-xr-x 2 root root   4096 2009-11-11 10:40 deploy

```How and where do i get rcplauncher.properties file?

I am using 64-bit Ubuntu 8.10

**UPDATE: **Thanks to akkornel's solution for my above problem, I was able to successfully install Lotus notes on my Intrepid.Thank you.

---

### Post by akkornel on 2009-11-13
> **Ellery McKenzie said:**
> Well, I've now found and installed libeel2-2. :D

Congratulations!  Using your notes as a starting point, I've gone back and updated my original post.  Instead of having users add and then remove the jaunty repository, I just have them manually download & install the jaunty package.  It also turns out that one of Note's shared libraries requires an older version of libstdc++ that Karmic doesn't include, so that needs to be downloaded as well.

If, as things go on, we need to download more and more packages from an older repository, then I'll be changing my guide to do exactly what you did.

Anyway, I'm now running a Karmic installation in a virtual machine, and I'm seeing tons of display problems.  I can't view my mailbox, or my inbox, or write emails.  SameTime works, but that's essentially it.  I don't think these problems are a result of the libraries (since I've found the ones that Karmic doesn't have), I think it's something that was changed from Jaunty to Karmic.  I'm not sure really what to do about that.

There is one other thing that I noticed:  If you run Notes manually, it reports a couple of interesting errors:

> /usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

There are 32-bit versions of these libraries installed, but those versions are in the */usr/lib32/gio/modules* directory; Notes is looking at the 64-bit versions instead.  Problem is, I'm not sure how to get Notes to look in the right place.  I've tried manually running Notes with the LD_LIBRARY_PATH set to "/usr/lib32:/usr/lib32/gio/modules", and I've tried adding "/usr/lib32" and "/usr/lib32/gio/modules" to the /etc/ld.so.conf file (and then running *ldconfig* before running Notes), but neither method helps.

So if anyone can help me with that problem, I'd really appreciate it!

---

### Post by akkornel on 2009-11-13
> **anjali.thampi said:**
> Hi,
  When i try to force install the .deb packages , i get the following error.Please help!

```
~/Installables/lotus$ sudo dpkg -i --force-architecture ibm_lotus_notes-8.5.i586.deb ibm_lotus_activities-8.5.i586.deb ibm_lotus_cae-8.5.i586.deb ibm_lotus_sametime-8.5.i586.deb ibm_lotus_symphony-8.5.i586.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 185796 files and directories currently installed.)
Preparing to replace ibm-lotus-notes 8.5-20080822.1349 (using ibm_lotus_notes-8.5.i586.deb) ...
cat: /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties: No such file or directory
Unpacking replacement ibm-lotus-notes ...
<<<snip>>>
```

Hello!  I notice dpkg says it is doing an upgrade (because you already have an older version installed), and it is upgrading from 8.5-20080822.1349.  The version being installed is 8.5-20081211.1925.  I think that Notes packages either don't support upgrades, or they don't support upgrading from 8.5-20080822.1349.

My suggestion is to remove the Notes packages you have installed now, and then install the latest version.  To remove the packages, run the command "sudo dpkg -r ibm-lotus-notes ibm-lotus-cae ibm-lotus-activities ibm-lotus-sametime ibm-lotus-symphony".  After that, follow the steps in Part III of my post.

If you want to be extra-safe, make an archive of your ~/notes directory.  That contains your Notes ID file, you address book, and other stuff.

Good luck!

---

### Post by Strelock on 2009-11-16
Guys, do I understand correctly that the solution for Karmic is not there yet? I have some strange behavior still...

---

### Post by akkornel on 2009-11-16
Correct, Karmic breaks Lotus Notes client.  If you want to use Lotus Notes client on Karmic, you will have to downgrade to either Hardy or Jaunty, or wait until IBM releases a Karmic-compatible version of Lotus Notes (which probably won't be for some time; I have no idea how long).

---

### Post by swacongne on 2009-11-16
Seams that some people made it work...
[http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllFlatWeb/69b50f2db7bb7b0b85257659005ab79e?OpenDocument](http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllFlatWeb/69b50f2db7bb7b0b85257659005ab79e?OpenDocument)

Also consider installing libgnomeprint2.2-0 
libgnomeprintui2.2-0 and libeel2-2 (for the last one, search in Jaunty... [http://packages.ubuntu.com/jaunty/libeel2-2](http://packages.ubuntu.com/jaunty/libeel2-2))

---

### Post by akkornel on 2009-11-16
> **swacongne said:**
> Seams that some people made it work...
[http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllFlatWeb/69b50f2db7bb7b0b85257659005ab79e?OpenDocument](http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllFlatWeb/69b50f2db7bb7b0b85257659005ab79e?OpenDocument)


Thanks for the link!  :mrgreen:  I notice that most of the steps match this post, and that it was actually posted a month after this thread was started!

That said, though, the link in Step 8 was helpful, and matches the instructions I found this morning (and am investigating) in [Launchpad bug #427949](https://bugs.launchpad.net/ubuntu/+bug/427949).  Essentially, for those out there who are wondering, the possible solution (I still have to verify on my side) is to take older versions of some GTK libraries (used by Notes to draw things on screen) and put them in the same directory as the other Notes libraries.  This causes Notes to use the older versions (the versions that don't break Notes).

I'll update the post once I've checked it out!

> **swacongne said:**
> Also consider installing libgnomeprint2.2-0 
libgnomeprintui2.2-0 and libeel2-2 (for the last one, search in Jaunty... [http://packages.ubuntu.com/jaunty/libeel2-2](http://packages.ubuntu.com/jaunty/libeel2-2))

Yup, the current steps already tell you to install those three packages, along with many more!

---

### Post by Strelock on 2009-11-17
> **swacongne said:**
> Seams that some people made it work...
[http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllFlatWeb/69b50f2db7bb7b0b85257659005ab79e?OpenDocument](http://www-10.lotus.com/ldd/nd85forum.nsf/DateAllFlatWeb/69b50f2db7bb7b0b85257659005ab79e?OpenDocument)


Step 7 of the manual above did the trick for me! thanks )

---

