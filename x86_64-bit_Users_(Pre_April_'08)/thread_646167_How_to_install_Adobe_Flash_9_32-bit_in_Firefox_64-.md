---
title: "How to install Adobe Flash 9 32-bit in Firefox 64-bit on Kubuntu 7.04 Feisty 64-bit"
date: 2007-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by antonr on 2007-12-20
6-Dec-2007

How I installed Adobe Flash 9 32-bit Netscape plugin in 64-bit Firefox running on Kubuntu 7.04 64-bit, using nspluginwrapper.

(The reason for this is that, to my knowledge, there is no 64bit version of Flash plugin yet.)

First see what plugins are installed already
Type in the location bar
[INDENT]about:plugins[/INDENT]

--------------------------------------------------------------

Disable any existing Flash plugin.
To get it out the way and make sure it didn't interfere, I moved the old Flash 4 compatible plugin to the parent directory and renamed it. (You can restart Firefox and check about:plugins to see it disappear.):
[INDENT]mv /usr/lib/mozilla/plugins/libflash-mozplugin.so /usr/lib/mozilla/DISABLEDlibflash-mozplugin.so[/INDENT]

--------------------------------------------------------------

From the about:plugins page I followed a couple of links to this website:
[INDENT]http://plugindoc.mozdev.org/linux-amd64.html[/INDENT]

and started following the instructions.

--------------------------------------------------------------

Download nspluginwrapper.
	[INDENT](Note: I probably didn't need to do this, because Adept has packages for nspluginwrapper, so I could probably just have installed nspluginwrapper via Adept.)[/INDENT]

It comes in two parts, plugin and viewer.
I went to the nspluginwrapper home page:
	[INDENT]http://gwenole.beauchesne.info/en/projects/nspluginwrapper[/INDENT]

and downloaded the latest versions of plugin and viewer, which at this time are:
	[INDENT]http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.5-1.x86_64.rpm[/INDENT]
	[INDENT]http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.5-1.x86_64.rpm[/INDENT]

Notice that the two files are .rpm (RedHat packages).

------------------------------------------------------------

Now, back to the plugindoc, which says that on DEB based distributions (as Kubuntu is) we need to use
alien to convert RPMs to DEBs, then we can install the DEBs.

------------------------------------------------------------

Install alien.
	[INDENT]sudo apt-get install alien[/INDENT]
	
Change directory to where I downloaded the above RPMs.
	[INDENT]cd temp[/INDENT]

Use alien to convert the RPMs to DEBs.
	[INDENT]sudo alien -d nspluginwrapper-0.9.91.5-1.x86_64.rpm[/INDENT]
		[INDENT][INDENT]Warning: Skipping conversion of scripts in package nspluginwrapper: postinst prerm
		Warning: Use the --scripts parameter to include the scripts.
		nspluginwrapper_0.9.91.5-2_amd64.deb generated[/INDENT][/INDENT]
	[INDENT]sudo alien -d nspluginwrapper-i386-0.9.91.5-1.x86_64.rpm[/INDENT]

(Those warnings did not seem to do any harm.)
Install the newly created DEBs.
	[INDENT]sudo dpkg -i nspluginwrapper*.deb[/INDENT]

Create a symbolic link nspluginwrapper.

Let's see what I had there already.
	[INDENT]ls -al /usr/bin/nspluginwrapper[/INDENT]
	[INDENT]/usr/bin/nspluginwrapper -> ../../usr/lib/nspluginwrapper/x86_64/linux/npconfig[/INDENT]

Mmm.. not quite the same as the path in the instructions (which misses "linux/").
What is working for me at the end is this:
	[INDENT]/usr/bin/nspluginwrapper -> /usr/lib/nspluginwrapper/x86_64/linux/npconfig[/INDENT]

So make that link:
	[INDENT]sudo ln -s /usr/lib/nspluginwrapper/x86_64/linux/npconfig /usr/bin/nspluginwrapper[/INDENT]

(I think the parent directory markers (../../) used to get to root should actually be used...)

--------------------------------------------------------------

"nspluginwrapper requires linux32."
	[INDENT]sudo apt-get install linux32[/INDENT]

--------------------------------------------------------------

Download Adobe's Flash Player for linux x86 (32-bit):
Go to www.adobe.com and click on "Get ADOBE Flash Player"
Download the .tar.gz file. I got it here:
	[INDENT]http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz[/INDENT]

Extract the contents somewhere.
(The extraction directory should continue to exist after the install, so extracting onto a folder
on your desktop is not recommended. Here I created the directory in the user's home directory.
Maybe not the best place, but for a single-user system, it works.)

The contents should include three files:
	[INDENT]flashplayer-installer
	flashplayer.xpt
	libflashplayer.so[/INDENT]
(Ignore flashplayer-installer, because it says "your architecture, 'x86_64', is not supported".)

-----------------------------------------------------------------------

Use nspluginwrapper to install the shared object library plugin file.
(Change to the directory where you extracted it.)
My first attempt failed because I originally had the above symbolic link incorrect:
	[INDENT]nspluginwrapper -i libflashplayer.so[/INDENT]
		[INDENT][INDENT]*** NSPlugin Viewer *** preloader not found
		nspluginwrapper: no appropriate viewer found for libflashplayer.so[/INDENT]
I restored the symbolic link:
	[INDENT]sudo ln -s -f /usr/lib/nspluginwrapper/x86_64/linux/npconfig /usr/bin/nspluginwrapper[/INDENT]

My second attempt to install the plugin failed as well:
	[INDENT]nspluginwrapper -i libflashplayer.so[/INDENT]
	[INDENT]/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
	nspluginwrapper: no appropriate viewer found for libflashplayer.so[/INDENT]

I checked my system and found libgtk-x11-2.0.so.0 was definitely installed (in /usr/lib/).
I googled for the above error and found a French forum poster who claimed he got it
working after installing ia32-libs-gtk.
	[INDENT]sudo apt-get install ia32-libs-gtk[/INDENT]

My third attempt, using an absolute path, seemed to work, giving no errors, no output at all:
	[INDENT]nspluginwrapper -i ~/install_flash_player_9_linux/libflashplayer.so[/INDENT]

Note well: it seems that after using the above command to install, the directory
you specified must continue to exist, therefore it's a good idea to put it somewhere
good.
Note, it looks like if you issue the above command more than once, you get multiple entries. Get nspluginwrapper to list the plugins.
	[INDENT]nspluginwrapper -l[/INDENT]

I had a whole bunch of entries of libflashplayer.so in different directories.
Probably an accumulation of previous attempts to install Flash !
I used rm to delete all the listed files and installed using nspluginwrapper as above.

--------------------------------------------------------------

It looks like firefox/plugins/ contains some links to actual .so files in mozilla/plugins/
	[INDENT]cd /usr/lib/firefox/plugins/[/INDENT]

So, in the same manner, I:
Create a new link in firefox/plugins to the mozilla/plugins directory:
	[INDENT]sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so npwrapper.libflashplayer.so[/INDENT]


Restart Firefox and the Flash plugin works !!


--------------------------------------------------------------

[SOLVED: This section was before I deleted all the plugins listed by nspluginwrapper.]

Ahh.. but strangely, it only works the first time Firefox is loaded after issuing the above nspluginwrapper command.
I suspect Firefox is trying to repair something it considers a bit broken.

Starting firefox from a Konsole shows this error:
	[INDENT]*** NSPlugin Viewer  *** ERROR: /home/marisa/install_flash_player_9_linux/libflashplayer.so: cannot open shared object file: No such file or directory[/INDENT]

Aha, so it tries to access the file from the unpacked download directory.
(I had deleted that directory thinking it wasn't needed any more.)

-------------------------------------------------------------

Clean up.

Delete the temp directory where I downloaded the nspluginwrapper RPMs.

(Leave the install_flash_player_9_linux directory where it is.)

Delete the symbolic link in /usr/lib/firefox/plugins that we broke by moving libflash-mozplugin.so  ?

Check permissions on all the new files.

-------------------------------------------------------------

List of interesting Directories:

	/usr/lib/firefox/plugins/
	/usr/lib/mozilla/plugins/
	~/install_flash_player_9_linux/

and Files:

	/usr/lib/nspluginwrapper/x86_64/linux/npconfig 
	/usr/bin/nspluginwrapper
	/usr/lib/libgtk-x11-2.0.so.0

These are the plugin files listed by nspluginwrapper which I deleted:

	/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
	/usr/lib64/mozilla/plugins/npwrapper.libflashplayer.so
	/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
	/usr/lib64/firefox/plugins/npwrapper.libflashplayer.so
	/home/marisa/.mozilla/plugins/npwrapper.libflashplayer.so

This is where they originally came from:	

	/home/marisa/install_flash_player_9_linux/libflashplayer.so
	/home/marisa/install_flash_player_9_linux/libflashplayer.so
	/home/marisa/install_flash_player_9_linux/libflashplayer.so
	/home/marisa/install_flash_player_9_linux/libflashplayer.so

-------------------------------------------------------------

References:

	about:pluginsnow

	http://plugindoc.mozdev.org/linux-amd64.html	
	http://gwenole.beauchesne.info/en/projects/nspluginwrapper
	http://www.adobe.com/

The French forum:
	http://forum.ubuntu-fr.org/viewtopic.php?id=118110

-------------------------------

See also:

	Flash 9 install script for AMD64 (nspluginwrapper)  http://ubuntuforums.org/showthread.php?t=476924

---

