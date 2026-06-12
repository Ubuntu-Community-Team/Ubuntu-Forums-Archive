---
title: "tabula rasa"
date: 2007-11-10
forum: Wine
---

### Post by element8 on 2007-11-10
anyone had any luck with this mmo? looks like it's all dx9 but i was curious if anyone has had luck running it before i try it out

---

### Post by slightlypaul on 2007-11-11
I just bought it, but I'm waiting for my new computer to come(Intel Duo 3ghz, geforce 6600) and try using VirtualBox or WINE.  I'd be glad to post the information!

---

### Post by Wiebelhaus on 2007-11-11
I had no luck.

---

### Post by carlosjuero on 2007-11-11
Tabula Rasa uses the NCSoft updater to launch/play - the NCSoft updater is very unfriendly to Linux (no one has managed to get it run yet). (Edit: it is the .NET routines the updater uses that makes it not work properly under any 'emulated' environment like WINE, Cedega, or Crossover).

For now Tabula Rasa has to be run Windows side only (same with any other game that uses that launcher - such as Dungeon Runners). Hopefully we can get some better .NET support in WINE, or maybe VM's will be able to handle the 3D graphics calls in the near future - not so much now though.

---

### Post by slightlypaul on 2007-11-12
The .NET framework makes me sad.  I really didn't want to have to dual-boot.  Maybe I'll just play WoW...

---

### Post by Wiebelhaus on 2007-12-14
> **slightlypaul said:**
> The .NET framework makes me sad.  I really didn't want to have to dual-boot.  Maybe I'll just play WoW...

lol , I feel the same way , I don't want to use windows so much that i'll sit out on these games that don't support it.

---

### Post by SBFC on 2008-02-15
Thought I'd share this despite the thread being a few months old. Whenever a new version of Wine comes out I check WineHQ AppDB to see the status on games I am forced to dual boot to play.

Since TR came out there hasn't been much listed...until now. Was browsing AppDB at work today and someone actually got it to run. Didn't know you could bypass the launcher...

You still can't update the game via Wine...only play it after it's been updated with Windows.

[AppDB ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9841")
[URL="http://www.planettr.com/forums/showthread.php?t=3889"]
And his writeup[/URL]

Thanks Jan!

---

### Post by ajackson on 2008-03-24
**TRLinux-0.1**

First (and hopefully last) version of a Mono based launcher that allows you to patch and run Tabula Rasa directly under linux, further instructions are contained within the tarball.

If you have any problems post here and I'll do my best to help.

[TRLinux Home Page]("http://www.lotrolinux.com/TR")

---

### Post by Emmental on 2008-03-27
Hi Alan.

The TR servers are down at the moment as it looks like they're applying 1.6 (hopefully). However, when launching TRLinux it's crashing when trying to connect to tabularasa.patcher.ncsoft.com. The message given when run from the shell is:

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Net.WebException: **The remote server returned an error: (503) Service Unavailable.**
  at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] 

   at GLib.ExceptionManager.RaiseUnhandledException ()
   at GLib.Idle+IdleProxy.Handler ()
   at GLib.Idle+IdleProxy.Handler ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.Run ()
   at TRLinux.GladeApp..ctor ()
   at TRLinux.GladeApp.Main ()

---

### Post by ajackson on 2008-03-27
Oops, I knew there was a bit of error catching that I missed. I'll fix it and put version 0.2 up on my site later today (and announce it here and over at TRPlanet).

Thanks for letting me know.

---

### Post by ajackson on 2008-03-27
**TRLinux-0.2**
Fixed the problem, go to [http://www.lotrolinux.com/TR]("http://www.lotrolinux.com/TR"), the download link now points to version 0.2

---

### Post by Emmental on 2008-03-27
Hi again. I've run into another couple of problems with the patcher.

**1.** The patching process stalls at the stage "Extracting patch to /tmp". A /tmp/TRLinux directory is created but then the application seems to get stuck in an infinite loop. It spits out this error if run from a shell (but does not crash):

Unhandled Exception: System.IO.DirectoryNotFoundException: Could not find a part of the path "/tmp/tabula_rasa_intl_1.5.4.3To1.6.5.0/PatchManifest.xml".
  at System.IO.FileStream..ctor (System.String name, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] 
  at System.IO.FileStream..ctor (System.String name, FileMode mode, FileAccess access, FileShare share) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.Xml.XmlUrlResolver.GetEntity (System.Uri absoluteUri, System.String role, System.Type ofObjectToReturn) [0x00000] 
  at Mono.Xml2.XmlTextReader.GetStreamFromUrl (System.String url, System.String& absoluteUriString) [0x00000] 
  at Mono.Xml2.XmlTextReader..ctor (System.String url, System.Xml.XmlNameTable nt) [0x00000] 
  at System.Xml.XmlTextReader..ctor (System.String url, System.Xml.XmlNameTable nt) [0x00000] 
  at System.Xml.XmlDocument.Load (System.String filename) [0x00000] 
  at TRLinux.PatchWindow.ProcessPatch () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

**2.** The patch file downloads at a much slower speed than the Windows patcher. TRLinux downloaded at around 16-20k/sec and the Windows patcher downloaded at around 65-95k/sec.

Probably not a major issue since the file does download, just slower.

**3.** If the application is closed while downloading the patch (by first closing the download window then attempting to close the main window or use the Quit button) it hangs and must be killed. Also, the patch download starts from the beginning again when restarted and does not resume.

Again, probably not a major issue, just let it finish.

I've kept an unpatched copy of TR 1.5 so let me know if you need me to test anything again.

---

### Post by ajackson on 2008-03-27
> **Emmental said:**
> **1.** The patching process stalls at the stage "Extracting patch to /tmp". A /tmp/TRLinux directory is created but then the application seems to get stuck in an infinite loop. It spits out this error if run from a shell (but does not crash):
Do you have unar installed (and xdelta) as it uses those, I'll have to see about changing the configure to check for them.

> **2.** The patch file downloads at a much slower speed than the Windows patcher. TRLinux downloaded at around 16-20k/sec and the Windows patcher downloaded at around 65-95k/sec.

Probably not a major issue since the file does download, just slower.
I'm just using a cheap and cheerful download method that is part of mono (and I think .NETs) base libraries. NCSoft have probably got a better version or there might be other download servers (I just used the one wireshark told me I was downloading from under windows).

> **3.** If the application is closed while downloading the patch (by first closing the download window then attempting to close the main window or use the Quit button) it hangs and must be killed. Also, the patch download starts from the beginning again when restarted and does not resume.
The no resume is again because of the cheap & cheerful method, the failing to abort I'll look into.

But for now ensure that you have unrar and xdelta installed, that should atleast allow you to patch the game.

---

### Post by ajackson on 2008-03-27
**TRLinux-0.3**
The ./configure stage now checks for unrar and xdelta being installed (it needs them for patching).

Note: Aborting the download is not guaranteed to work, I've tightened up the abort code but it is far from perfect. It is an area I will look at but for now if you abort it may or may not hang as it is using threads rather than a better less hacky method (I normally program billing engines, threads aren't my speciality :)).

---

### Post by Emmental on 2008-03-28
Ah yes, I was missing xdelta. I've now been able to patch the game and login just fine.

Thanks for the quick replies and thanks for this very useful launcher. :)

---

### Post by SangreNegra on 2008-03-28
Hi Alan,

first I have to say kudos on your nice little piece of software, pretty useful!!

Just wanted to give you a quick bug report on V0.3.

If the game folder path contains whitespaces the download will work but unfortunately not extracting the archive/patch.

The bug must be located somewhere in method ExtractPatch() of the PatchWindow class. I would guess it should help to quote the game folder path and everything should perform well.

Again, thanks for your effort on the launcher!

Kind regards Johannes

---

### Post by ajackson on 2008-03-28
The quick fix for that is to edit PatchWindow.cs and find the line
```
private const string keyUnRarParams = "x -inul -o+ {0} /tmp";
```
It's up the top of the file, change it to
```
private const string keyUnRarParams = "x -inul -o+ \"{0}\" /tmp";
```
That should solve the problem.

I'm half-way through rewriting the patch and repair functions so that they will download faster and be less prone to crashing if you stop them. Also after emmental's comments I'm implementing a change so that it resumes the download from where it left off if you stop it.

---

### Post by schtufbox on 2008-03-28
I'm havign some problems with your launcher. As fas as I know I have everything I need to run it, unrar, xdelta. I had no problems compiling it, and it runs just fine, until it gets to the patching stage, where I get the following error:

```
xdelta: usage: xdelta patch patchfile [fromfile [tofile]]

Unhandled Exception: System.IO.FileNotFoundException: Could not find file "/tmp/TRLinux/data/maps/adv_foreas_concordia_wilderness_cavesofdonn02/adv_foreas_concordia_wilderness_cavesofdonn02.map"
File name: '/tmp/TRLinux/data/maps/adv_foreas_concordia_wilderness_cavesofdonn02/adv_foreas_concordia_wilderness_cavesofdonn02.map'
  at System.IO.FileStream..ctor (System.String name, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] 
  at System.IO.FileStream..ctor (System.String name, FileMode mode) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode)
  at TRLinux.PatchWindow.GetMD5HashFromFile (System.String filename) [0x00000] 
  at TRLinux.PatchWindow.PatchFile (System.String dirName, System.String fileName, System.String preHash, System.String postHash) [0x00000] 
  at TRLinux.PatchWindow.ProcessPatch () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

```

Any ideas?  Maybe I just missed something but I just can't see it

---

### Post by ajackson on 2008-03-29
Similar problem to the post above, edit PatchWindow.cs find the line
```
private const string keyXDeltaParams = "patch {0} {1} {2}";
```

Change it to
```
private const string keyXDeltaParams = "patch \"{0}\" \"{1}\" \"{2}\"";
```

---

### Post by ajackson on 2008-03-29
**TRLinux-0.4**
Improved the downloading process, it is now faster and resumes if you cancel it, cancelling the patch process no longer cause the launcher to hang (or I haven't had it happen yet). Fixed the problems with unrar and xdelta failing if one of the directory names contained spaces.

---

### Post by schtufbox on 2008-04-02
> **ajackson said:**
> **TRLinux-0.4**
Improved the downloading process, it is now faster and resumes if you cancel it, cancelling the patch process no longer cause the launcher to hang (or I haven't had it happen yet). Fixed the problems with unrar and xdelta failing if one of the directory names contained spaces.

Works a treat now, thanks. Only issue is some corrupted gfx, and the game screen occasionally flipping upside down, but that's an ATI driver issue I think (current card is a cheapo 2400 HD as my nvidia 8800 died :(  )
I'll know for sure once my new nvidia card arrives tomorrow :D

---

### Post by schtufbox on 2008-04-03
and yes, it was the ATI drivers, using an nvidia geforce 7300GT it performed almost as well in linux + wine as under windows with the same card, and no GFX corruption.
Excellent work on the launcher btw :D

---

### Post by SmilingJack on 2008-04-04
The unofficial launcher works fine for me, but ingame I have no mouse cursor. This makes the game a lot less fun.:(
Does anyone have a solution for this problem?
I'm running wine 0.9.58 on a 32 bit system. Graphic driver is Nvidia.

---

### Post by ajackson on 2008-04-07
Problem with wine 0.9.59

You may or may not be affected by this bug, if the game hangs before the movie sequence the apply the patch listed [here]("http://winehq.org/pipermail/wine-patches/2008-March/052489.html").

---

### Post by schtufbox on 2008-04-09
This is just a slight bump for this thread, so others can see the excellent work Alan has done with his launcher.  Haaving now switched my main PC from Vista to Hardy beta (stable enough for me!) I am using TRLinux again.
Nice one :):guitar:

---

### Post by schtufbox on 2008-04-09
Updated to the latest wine today (it's in the hardy updates today) TR no longer seems to work :(

---

### Post by ajackson on 2008-04-09
> **ajackson said:**
> Problem with wine 0.9.59

You may or may not be affected by this bug, if the game hangs before the movie sequence the apply the patch listed [here]("http://winehq.org/pipermail/wine-patches/2008-March/052489.html").
Seems that fix just missed 0.9.59, so either stick with 0.9.58 or compile your own with that patch.

---

### Post by schtufbox on 2008-04-10
Well as I already updated, hard to stay with .9.58 :D
Got around it though, I'm using the crossover games trial to play it, good for 7 days at least!

---

### Post by brento73 on 2008-04-11
My game seems to patch, with TRLinux, and launch just fine, but I have no textures at all. Just white and some blue-ish highlights, although the menus look mostly ok. Has anyone else had this issue, and how might I fix it?

---

### Post by schtufbox on 2008-04-11
> **brento73 said:**
> My game seems to patch, with TRLinux, and launch just fine, but I have no textures at all. Just white and some blue-ish highlights, although the menus look mostly ok. Has anyone else had this issue, and how might I fix it?
What graphics card are you using?

---

### Post by DarthMort on 2008-04-11
Hello,

I have installed linux launcher v0.4. My TR client is 1.2.2.0. When Im tryin to update game Im getting error message  Download error : Try again or use repair option, almost immediately on my screen. What am I doing wrong? :(

---

### Post by ajackson on 2008-04-11
Have a look in your TR directory (where the game is installed), see if there are any files ending ncpatch, if there are delete them (they might be corrupt).

You get that error if something stops the download working, this could include the patch server being down or your user id not having write permission on the game files/directories.

---

### Post by schtufbox on 2008-04-11
New TR patch today...Seems to broken in wine now.
Even in crossover games (where it worked before too)
Anyone else or just me? If just me, well I'll try reinstalling TR, cos the repair function doesn't seem to work in the TRLinux launcher (thought I'd try it) not that I think it needs a repair as the patch seemed to go flawlessly

---

### Post by ajackson on 2008-04-12
> **schtufbox said:**
> New TR patch today...Seems to broken in wine now.
If you get the game hanging after just before where it plays the intro movie stuff then that is a known bug in wine. I posted a patch earlier or if you look on the PlanetTR site there are ways around it.

> cos the repair function doesn't seem to work in the TRLinux launcher (thought I'd try it)
What problems are you getting, as I repaired my installation two patches ago (just to check that it worked), it takes a while because it is downloading several gigs from the patch server and quiting it mid-download will mean that the file it was fetching needs repairing as it does a straight overwirite when downloading.

---

### Post by schtufbox on 2008-04-12
[QUOTE=ajackson]If you get the game hanging after just before where it plays the intro movie stuff then that is a known bug in wine. I posted a patch earlier or if you look on the PlanetTR site there are ways around it..[/QUOTE]
No this is a different issue, it's crashing as soon as the splash screen comes up.  I already downgraded wine to .9.58 and was playing TR (also worked with crossover games btw) Now, after I patched TR, it won't play with either.



[QUOTE=ajackson]What problems are you getting, as I repaired my installation two patches ago (just to check that it worked), it takes a while because it is downloading several gigs from the patch server and quiting it mid-download will mean that the file it was fetching needs repairing as it does a straight overwirite when downloading.[/QUOTE]

It doesn't download anything, it get's about 12kb of the repair file then quits downloading saying something about the server being down.  If the server is really down, then NCSoft have a serious problem, as it's been down for about 18 hours :D

I'll try reinstalling TR and repatching when I get home from work later, might just be a problem with my install.

---

### Post by ajackson on 2008-04-12
> **schtufbox said:**
> No this is a different issue, it's crashing as soon as the splash screen comes up.  I already downgraded wine to .9.58 and was playing TR (also worked with crossover games btw) Now, after I patched TR, it won't play with either.
Just noticed the Hardy Heron tag by your name, I found that wine and kernel 2.6.24-16 don't seem to get on, but when I login under 2.6.24-15 I can start TR fine.

> It doesn't download anything, it get's about 12kb of the repair file then quits downloading saying something about the server being down.  If the server is really down, then NCSoft have a serious problem, as it's been down for about 18 hours :D
I'll have a look, it might be because they have released a new patch and the server hasn't caught up yet.

---

### Post by schtufbox on 2008-04-12
> **ajackson said:**
> Just noticed the Hardy Heron tag by your name, I found that wine and kernel 2.6.24-16 don't seem to get on, but when I login under 2.6.24-15 I can start TR fine.

That could be it, as I updated Hardy right before I updated TR!
I'll try it with 2.6.24-15 when I get home (well okay 2.6.24-15-rt as I use an rt kernel)

---

### Post by ajackson on 2008-04-12
> **schtufbox said:**
> It doesn't download anything, it get's about 12kb of the repair file then quits downloading saying something about the server being down.  If the server is really down, then NCSoft have a serious problem, as it's been down for about 18 hours :D
It seems the very first file listed in the repair file doesn't exist on the patch server (but it is a valid game file), that is why the repair is aborting, the next 5 are on the patch server, didn't try any more after those. So it looks like a problem NCSoft's end.

---

### Post by javafiend on 2008-04-12
How did you manage to downgrade your kernel?

---

### Post by ajackson on 2008-04-12
> **javafiend said:**
> How did you manage to downgrade your kernel?
Press [Esc] when it mentions grub while booting and select a different kernel from the list shown. That's if you have more than one installed, if not add one via synaptic, reboot and carry on from above.

Normally there is no reason to use the non-default kernel but Hardy is still in development and it looks like 2.6.24-16 has a few problems that need fixing.

---

### Post by javafiend on 2008-04-12
Thanks, I'll give it a shot!

Edit::
Hit a snag... I can't figure out how to add another kernel in synaptic

Edit to the edit::
Rebooted and hit Esc into grub and .15 was there.  Nothing needed installed.

---

### Post by schtufbox on 2008-04-12
> **ajackson said:**
> Press [Esc] when it mentions grub while booting and select a different kernel from the list shown. That's if you have more than one installed, if not add one via synaptic, reboot and carry on from above.

Normally there is no reason to use the non-default kernel but Hardy is still in development and it looks like 2.6.24-16 has a few problems that need fixing.

Yeah and like an idiot, thinking it was working okay, I uninstalled the other kernels..whoops! now how do I get the old ones back? :P

---

### Post by ajackson on 2008-04-12
> **schtufbox said:**
> Yeah and like an idiot, thinking it was working okay, I uninstalled the other kernels..whoops! now how do I get the old ones back? :P
Done that myself in the past, now I always leave the previous version in there.

Search for linux-image, that should pull in all the other ones you need (obviously linux-image-2.6.24-15 or some such name).

---

### Post by schtufbox on 2008-04-12
> **ajackson said:**
> Done that myself in the past, now I always leave the previous version in there.

Search for linux-image, that should pull in all the other ones you need (obviously linux-image-2.6.24-15 or some such name).
only the linux-image-2.6.24-15etc is there, there's no kernel headers or modules etc in the repositories anymore...

However, more than one way to skin a cat!...If you check the package lists on the site for hardy, you can also download from there, so I just downloaded the ubuntu modules, the restricted modules and the headers etc, then installed the image via apt-get install and it set it all up for me :D

TR is now working again, so i'll use 2.6.24-15  until wine plays nice with -16
I got the files from here:

[http://packages.ubuntu.com/hardy/all/allpackages]("http://packages.ubuntu.com/hardy/all/allpackages")

If you wish to do the same (if, like me, you removed the older kernels) then you do so at your own risk..there's a chance you might end up with an unbootable pc!!

---

### Post by tparker on 2008-04-15
I downloaded TRLinux from sourceforge and tried to set it up following the directions found here: [http://www.planettr.com/forums/showthread.php?t=3889](http://www.planettr.com/forums/showthread.php?t=3889)

Everything was fine until I got to 'make' at which point I get this error:

/usr/bin/gmcs Main.cs MainWindow.cs Config.cs Patch.cs PatchWindow.cs RepairWind ow.cs Settings.cs SettingsWindow.cs StartGame.cs -noconfig -codepage:utf8 -warn: 3 -out:TRLinux.run -target:exe -resource:TRLinux.ico -resource:TRLinux.png -reso urce:MainWindow.glade -resource:PatchWindow.glade -resource:RepairWindow.glade - resource:SettingsWindow.glade -r:System -r:System.Xml -r:System.Web -pkg:gtk-sha rp-2.0 -pkg:glade-sharp-2.0
Config.cs(53,13): error CS0117: `System.IO.StreamReader' does not contain a defi nition for `EndOfStream'
Compilation failed: 1 error(s), 0 warnings
make: *** [TRLinux.run] Error 1

I'm not sure what to do now to continue, I am in Dapper (no joy upgrading to Hardy yet, hopefully will work after release), wine 0.9.57. I have mono, gtk-sharp, unrar, and xdelta; all installed through Synaptic. 

Any ideas how to fix this or what to try would be greatly appreciated, thanks.

---

### Post by ajackson on 2008-04-16
> **tparker said:**
> I'm not sure what to do now to continue, I am in Dapper (no joy upgrading to Hardy yet, hopefully will work after release), wine 0.9.57. I have mono, gtk-sharp, unrar, and xdelta; all installed through Synaptic. 

Any ideas how to fix this or what to try would be greatly appreciated, thanks.
I know that the mono included with Dapper is dated, didn't realise it was missing that particular function.

A quick fix is to edit Config.cs, find the line
```
while (!fileVersion.EndOfStream)
```
Change it to
```
while (fileVersion.Peek() != -1)
```
It should work with that modification.

---

### Post by tparker on 2008-04-17
Looks like that did it, patching now. Thank you!

---

### Post by tparker on 2008-04-17
Okay, launcher started up fine, trying to run game gave me an error. I clicked tools>repair , that started up and did fix some files, but afterward when I clicked 'launch' I got the same error as before the repair. I thin it's a graphics error, but I don't know enough more than that about it to get further without help. 

The error is:
Error initializing Game Client. Contents of tabula_rasa.log:
ERROR: Unknown shader profile found
WARNING: Warning
ERROR: Failed to load Global Effect
ERROR: Init Device Failed to load default effect
ERROR: Failed to start device.
ERROR: PalantirApp::Initialize failed

just in case this info is useful:

/etc/X11/xorg.conf:
-----------------------------------------------
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"HP w1907"
	Option		"DPMS"
	HorizSync	24-83
	VertRefresh	50-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"HP w1907"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
--------------------------------------------------

glxinfo says that direct rendering is enabled

running Dapper, wine 0.9.57, Nvidia 7600GS 

graphics card otherwise has no problems, WoW and CoH both work on this same machine.

Sorry if that was too much info, not enough, or all the wrong kind.

---

### Post by ajackson on 2008-04-18
How did you install TR? Was it copied from a Windows setup?

The only thing I can think of is that there is something (or maybe more than one) in the client.cfg file (lives in the game directory) that is causing the crash, you could try renaming it to let it create it again see if that fixes the problem.

The xorg.conf looks fine, the graphics card is almost the same version as mine (I have the GT) so I don't think it is anything related to those (since other games work anyway).

---

### Post by tparker on 2008-04-18
> **ajackson said:**
> How did you install TR? Was it copied from a Windows setup?

Yes, I copied the program files across a network from a currently working and patched windows (XP pro) install of the game, but it was not on this same computer, different video card, mainboard, audio, pretty much everything.

>  client.cfg file (lives in the game directory) that is causing the crash, you could try renaming it to let it create it again see if that fixes the problem.

I just tried that, thanks. I still crashed at the same point with the same error message. I checked back in the game file and it did not create a new client.cfg, the one I renamed is still there but not a new one. I'm not sure if that means it is crashing before it gets that far or if something else is going on. I do have the disks here if deleting and trying an install from them is better than the copied files, I just copied to try and save patch download time.

Thanks again for the help and ideas to try.

---

### Post by ajackson on 2008-04-19
> **tparker said:**
> I just tried that, thanks. I still crashed at the same point with the same error message. I checked back in the game file and it did not create a new client.cfg, the one I renamed is still there but not a new one. I'm not sure if that means it is crashing before it gets that far or if something else is going on. I do have the disks here if deleting and trying an install from them is better than the copied files, I just copied to try and save patch download time.

Thanks again for the help and ideas to try.
One thing to try go to the directory where TR is installed and try
```
wine tabula_rasa.exe /NoPatch
```
That will atleast tell us if the problem is being caused somehow by my launcher.

Another thing to check is that you have read/write permission to all the files in the game directory (and sub directories) I know some games that like to update date stamps on data files.

---

### Post by ajackson on 2008-04-27
**ULL 0.1**
TRLinux is being replaced by ULL, ULL or Universal Linux Launcher for NCSoft Games (yes it's a naff name) aims to support all of NCSofts games as they switch over to the NCSoft launcher, at the moment only TR, Dungeon Runners and Exteel need to use the launcher.

Full details are [here]("http://ubuntuforums.org/showthread.php?t=770438"), from a TR point of view there is no real change except a box on the left showing configured games.

Although most of the games on the list do their own patching if you have the game see if it launches ok using ULL.

---

### Post by unc0nn3ct3d on 2008-05-29
Wow, after playing TR for a few weeks now and just assuming the piss poor performane I was getting(maxed out at 20fps staring at a wall, 7fps while fighting, I just assumed it was because my cpu was 2 years old(AMD 3200+).  And then I stumbled upon a little gem that told me to do this:

go into ~/.wine/ and edit user.reg

and add the following to: [Software\\Wine\\Direct3D]

"OffscreenRenderingMode"="backbuffer"
"PixelShaderMode"="enabled"
"UseGLSL"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="512"

The main one being the last.. Apparently without this Wine defaults to 64mb of Video memory.  Change he "VideoMemorySize"= to whatever size your vid card is.  If you have 256mb of ram on your vid card obviously it would look like this: "VideoMemorySize"="256"

My frame rates in battles went from 7fps with all setting to min, up to 35fps with all settings to max and viewing distance maxed out as well.

I can actually enjoy the game now.. Hip hip hoorah!

---

### Post by blaise69 on 2008-09-26
I'm having trouble with Tabula Rasa launching.

When I load it using ULL v0.8 at first nothing seems to happen, my terminal will even return to the prompt (If I ran ULL from the terminal), then eventually I will see Tabula Rasa displayed in the task bar, but nothing on my desktop.

I do get a message in my terminal though.
```
 'import site' failed; use -v for traceback
python.client initialized, gameclient = <extern_gameclient_gameclient.GameClient object at 0xBFF370A0>
wine: Call from 0x73bc15de to unimplemented function GDI32.dll.GdiEntry1, aborting
```
And that's what I'm left with, using ctrl-c in terminal will bring me back to prompt, but I can't remove Tabula Rasa from my task bar.

I've tried putting a downloaded GDi32.dll into my system32 folder but this doesn't make a difference.

Another issue I have propping up that might be related, is that sometimes I get the following error
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe" failed, status c0000142
```
Not sure if these are related, I have Mono installed in both Ubuntu and Wine.
Tabula Rasa was installed using the downloaded client from its website in Wine, and I located the directory in ULL.  ULL does successfully load Dungeon Runners.

Any ideas?  Can I give you any more information?

---

### Post by ajackson on 2008-09-26
> **blaise69 said:**
> I do get a message in my terminal though.
```
 'import site' failed; use -v for traceback
python.client initialized, gameclient = <extern_gameclient_gameclient.GameClient object at 0xBFF370A0>
wine: Call from 0x73bc15de to unimplemented function GDI32.dll.GdiEntry1, aborting
```
And that's what I'm left with, using ctrl-c in terminal will bring me back to prompt, but I can't remove Tabula Rasa from my task bar.

Another issue I have propping up that might be related, is that sometimes I get the following error
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe" failed, status c0000142
```
Not sure if these are related, I have Mono installed in both Ubuntu and Wine.
I must admit I haven't much of a clue, having mono installed under wine shouldn't cause ULL a problem as the script launches it via the linux mono.

It might be worth renaming your .wine directory, creating a new one and copy/move TR into that. That should give a clue as to if it is TR or something else installed in wine that is causing the problem.

---

### Post by Olfiar on 2008-10-25
*deleted by me*

---

### Post by Virtua-Touch on 2008-10-26
> **slightlypaul said:**
> I just bought it, but I'm waiting for my new computer to come(Intel Duo 3ghz, geforce 6600) and try using VirtualBox or WINE.  I'd be glad to post the information!

Dude, upgrade that card. The 6600 can't handle these higher games like COD4, FFOW, Crysis, and Far Cry 2. I have the 6600 and I can only run on low on these games. I suggest getting a 9000 Geforce or an ATI Radeon X1900 series.

---

