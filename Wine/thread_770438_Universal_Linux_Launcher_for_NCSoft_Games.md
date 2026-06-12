---
title: "Universal Linux Launcher for NCSoft Games"
date: 2008-04-27
forum: Wine
---

### Post by ajackson on 2008-04-27
Since NCSoft seem to be heading for a universal launcher for all their games which unfortunately relies on .NET 2.0, I have combined my TRLinux and DRLinux launches to for ULL (Universal Linux Launcher for NCSoft Games), naff name I know :)

At present it can handle the following games from NCSoft:
Auto Assault
Dungeon Runners (incl PTS)
Tabula Rasa
Lineage 1 & 2 (incl Test)
Guild Wars
City of Heroes (incl EU & Test)
Exteel

Apart from Dungeon Runners, Tabula Rasa and Exteel all of the others self-patch, these three however require the launcher to patch the game files.

ULL can be downloaded from [www.lotrolinux.com/ULL/ULL-0.1.tar.bz2]("www.lotrolinux.com/ULL/ULL-0.1.tar.bz2") (I'm working, slowly, on the web page). It requires mono to build and run (see README and INSTALL).

The only oddities I've notice so far is that Dungeon Runners installs some of it's files a read only (so update can fail), City of Heroes EU needs the program CohUpdater.exe renamed CohUpdater.eu.exe.

I've not tested any of Lineages, Exteel or Auto Assault. Guild Wars starts fine, Tabula Rasa patches and starts fine.

---

### Post by schtufbox on 2008-04-27
Nice work as ever! Tabula Rasa runs fine as well as just starts :P
I created a .deb file of this with checkinstall too, if you want to use it anywhere.

---

### Post by ajackson on 2008-04-27
> **schtufbox said:**
> Nice work as ever! Tabula Rasa runs fine as well as just starts :P
I created a .deb file of this with checkinstall too, if you want to use it anywhere.
I just fixed a bug on it, altering options changed the wrong game (but left at at 0.1 by mistake), once I get time I'll sort out the debs like I've done for LotROLinux and give it a proper web page.

---

### Post by schtufbox on 2008-04-27
Righto, I only made a  .deb so it'd be easier to remove etc if needed at a later date.

---

### Post by ajackson on 2008-04-28
Home page for ULL can be found at [http://www.lotrolinux.com/ULL]("http://www.lotrolinux.com/ULL")

---

### Post by Laibcoms on 2008-04-28
Finally!

A thousand chocolates to you!

---

### Post by ajackson on 2008-05-01
**ULL 0.3**
New version available, corrects a potential problem caused by windows being case insensitive but linux isn't.

Also repository now available (Hardy only for now).
```
deb http://ppa.launchpad.net/ajackson-bcs/ubuntu hardy main
```

Any problems (ie I've missed a dependancy) let me know.

---

### Post by copperpot on 2008-05-03
Hello. I just downloaded and installed ULL 0.3 to use it with Tabula Rasa. I also copied the NCSoft directory from the windows partition to the wine drive_c folder and pointed ULL to use it for TR. When I started it, it says that TR has to be updated, I click on update and one patch is downloaded and extracted to /tmp directory. And then ULL closes not doing anything else.
This is the output I get running sudo ULL from the terminal:
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ComponentModel.Win32Exception: ApplicationName='xdelta', CommandLine='patch "/tmp/tabula_rasa_intl_1.5.4.3To1.6.5.0/ProductFiles/data/maps/adv_foreas_concordia_palisades_treebackcamp/audioemitters.xml.X-D-E-L-T-A" "/home/sirlogan/.wine/drive_c/Archivos de programa/NCSoft/Tabula Rasa/data/maps/adv_foreas_concordia_palisades_treebackcamp/audioemitters.xml" "/tmp/ULL/data/maps/adv_foreas_concordia_palisades_treebackcamp/audioemitters.xml"', CurrentDirectory='', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin'
  at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
  at ULL.PatchWindow.PatchFile (System.String dirName, System.String fileName, System.String preHash, System.String postHash) [0x00000] 
  at ULL.PatchWindow.ProcessPatch () [0x00000] 
  at ULL.PatchWindow.ExtractPatch () [0x00000] 
  at ULL.PatchWindow.UpdateGame () [0x00000] 
  at ULL.PatchWindow.Run () [0x00000] 
  at ULL.MainWindow.OnBtnOKClicked (System.Object sender, System.EventArgs e) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at ULL.GladeApp..ctor(System.String[] args)
   at ULL.GladeApp.Main(System.String[] args)

I have no clue if I am doing something wrong or not. Please help me here if possible.
Thank you!!

Francisco

---

### Post by ajackson on 2008-05-04
> **copperpot said:**
> This is the output I get running sudo ULL from the terminal:
Don't run it as root, there is no need to.

> GLib.ExceptionManager.UnhandledException to handle the exception.
System.ComponentModel.Win32Exception: ApplicationName='xdelta', CommandLine='patch "/tmp/tabula_rasa_intl_1.5.4.3To1.6.5.0/ProductFiles/data/maps
Have you got xdelta installed? If not it should have kicked up a fuss (unless I broke something, oops). Did you get ULL via source and build or via the deb?

Edit: It is because you are running ULL as root, root doesn't have write permission on the files to be patched so it is aborting.

---

### Post by copperpot on 2008-05-04
Cool! Thanks! I did not have xdelta installed. I installed the packages through Synaptic and everything is running as it should.
Now I just have to cieck how to fix an issue with DX9.

Thanks!

Francisco

---

### Post by ajackson on 2008-05-05
**ULL 0.4**
Fixed a problem with the configure script not aborting if unrar or xdelta is missing (no I don't know how I broke it in the first place).
Tabula Rasa PTS added
Some details changed in GameList.xml to reflect the changes in the files NCLauncher uses, looks like they are slowly gearing up to switch all the games to being patched via the launcher.

New DEB should be in place, new source tar ball at SourceForge (follow link in my signature).

---

### Post by ajackson on 2008-05-07
**ULL 0.5**
The big change is that the launcher now works with Crossover Games (and hopefully Crossover Office but I haven't tested that).

In the options window you can select Wine or one of the Crossovers, when a Crossover is selected the WINEPREFIX gets replaced with Bottle Name, just enter the name of the bottle you installed the game into (remember case sensitive).

If your version of Crossover Games is installed somewhere other than /opt/cxgames or /home/username/cxgames give the full path to the wine program, otherwise it might try to use the wine version or just not find it. Same with Crossover Office but replace cxgames with cxoffice.

DEB versions are in the process of being built.

---

### Post by ajackson on 2008-05-26
**ULL-0.6**
I've added game parameters to the options window in case you need to pass any parameters to the game (Guild Wars for example).

Should now work via CrossOver on Macs (open shell from within CrossOver Games and run using mono ULL).

---

### Post by ajackson on 2008-05-26
**ULL-0.6.1**
There was an error in the GameList.xml preventing Dungeon Runners from updating.

Also I've found that you can use the repair function to install the game for you. Just create a directory, set the game dir to there (ignore the error message), click repair and go have a cup of coffee or 7.

---

### Post by simus on 2008-06-03
I installed the Universal launcher, but when i try to run exteel i get this error

simus@simus-laptop:~$ ULL
preloader: Warning: failed to reserve range 00000000-60000000
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
simus@simus-laptop:~$ wine EXTEEL
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\EXTEEL.exe": Module not found
simus@simus-laptop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

Can someone please help me?
THANX

---

### Post by ajackson on 2008-06-04
> **simus said:**
> I installed the Universal launcher, but when i try to run exteel i get this error

simus@simus-laptop:~$ ULL
preloader: Warning: failed to reserve range 00000000-60000000
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

Looks like a bug in my launcher, Exteel is a bit odd because the executable resides in a sub-directory rather than the game directory.

I'll fix the problem and post a new version when I have time.

---

### Post by ajackson on 2008-06-04
> **ajackson said:**
> Looks like a bug in my launcher, Exteel is a bit odd because the executable resides in a sub-directory rather than the game directory.

I'll fix the problem and post a new version when I have time.
**ULL 0.7** should fix this problem.

---

### Post by simus on 2008-06-04
I downloaded the new version but the game still not works. When I press start the initial image appears but then it says 
"There is an error with GameMon. PLease try to reboot the system or close the programs that cause collisions"

I rebootted nd closed everything but i still get the message. In the terminal that's what happens:

simus@simus-laptop:~$ ULL
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
simus@simus-laptop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: Unhandled page fault on write access to 0x00000000 at address 0x7f4aa254 (thread 0025), starting debugger...

HELP!!!

---

### Post by ajackson on 2008-06-04
> **simus said:**
> I downloaded the new version but the game still not works. When I press start the initial image appears but then it says 
"There is an error with GameMon. PLease try to reboot the system or close the programs that cause collisions"
Uh GameMon, that game won't work as wine can't handle security protection things like GameMon, wonder why they put that on Exteel but none of the other games.

---

### Post by simus on 2008-06-04
SO i guess i have to give up tring to get it to work. Thanx anyways.

---

### Post by ajackson on 2008-08-14
**ULL 0.8**
Fixed bug causing patcher to crash if it tried to delete a file that didn't exist.

---

### Post by benmoran on 2009-01-20
Sorry for the necropost, but I just had to say thank you for this app!

---

### Post by chuanyu on 2009-01-22
i downloaded the launcher and i think i installed it.
how do i work it?
i a noob

---

### Post by h4mx0r on 2009-01-22
Nice work on the launcher. I heard NCSoft is going to be releasing a title called "Aion" which uses a very intricate graphics system using the same engine as crysis which runs alright on wine already. Hoping it runs well with your launcher.

---

### Post by ravdragon on 2009-04-05
What do I search for Synaptic to find this package? "ULL" or "NCSoft" etc doesn't seem to work. I have added the third party repository to my source manager:

deb [http://ppa.launchpad.net/ajackson-bcs/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ubuntu) hardy main

Also tried

deb [http://ppa.launchpad.net/ajackson-bcs/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ubuntu) intrepid main

Since I installed 8.10

Thanks

---

### Post by ajackson on 2009-04-05
> **ravdragon said:**
> deb [http://ppa.launchpad.net/ajackson-bcs/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ubuntu) hardy main

Should that one, you may have to make synaptics reload it's package list before you see it. Hopefully then searching for ULL should show the launcher.

---

### Post by ravdragon on 2009-04-05
Found it. Thanks!

---

### Post by sejml on 2009-04-26
> **h4mx0r said:**
> Nice work on the launcher. I heard NCSoft is going to be releasing a title called "Aion" which uses a very intricate graphics system using the same engine as crysis which runs alright on wine already. Hoping it runs well with your launcher.

its not the crysis engine its the far cry engine and the game sooks awsome atm! :D
Far cry and aion= Cryengine
Crysis and far cry 2=Cryengine 2

---

### Post by blitzenslayn on 2009-05-07
New to Ubuntu, well linux actually, so please bear with me.

I'm trying to add the third party repository to the source manager, but I keep getting this error.
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D210E847676F63E7Not really sure what I should do here. I'll keep on google searching for ideas, since it was google that pointed me to this nifty app in the first place via: [http://www.lotrolinux.com/ULL/](http://www.lotrolinux.com/ULL/)

Ultimately, I want to be able to play Dungeon Runners again. Bling Gnome ftw!

---

### Post by Carlos A. on 2009-05-08
> **ajackson said:**
> **ULL 0.8**
Fixed bug causing patcher to crash if it tried to delete a file that didn't exist.

Hi man, i'll try to speak your language but im learning english, so have patient with me ^_^.

mi problem is this:
mrukairo@rukairo-laptop:~/Escritorio/Launcher$ make install
make[1]: se ingresa al directorio `/home/rukairo/Escritorio/Launcher'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'ULL' '/usr/local/bin/ULL'
/usr/bin/install: no se puede crear el fichero regular «/usr/local/bin/ULL»: Permiso denegado
make[1]: *** [install-binSCRIPTS] Error 1
make[1]: se sale del directorio `/home/rukairo/Escritorio/Launcher'
make: *** [install-am] Error 2

I know work in my OS, enought to didn't give up using ubuntu. But with that problem i don't know what to do.

Well... the first question maybe is: Is Exteel working with your launcher?. I mean, 2 weeks ago i read that exteel didn't run in wine and bla bla bla.

if exteel runs, how i could fix my problem?. thx for all, and for try understand me. ^-^ .. bb gl.

pd: oh if you need the complete text, here you are:

rukairo@rukairo-laptop:~/Escritorio/Launcher$ ./configure
checking build system type... x86_64-unknown-linux-gnu   
checking host system type... x86_64-unknown-linux-gnu    
checking target system type... x86_64-unknown-linux-gnu  
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes           
checking for a thread-safe mkdir -p... /bin/mkdir -p        
checking for gawk... no                                     
checking for mawk... mawk                                   
checking whether make sets $(MAKE)... yes                   
checking for gmcs... /usr/bin/gmcs                          
checking for mono... /usr/bin/mono                          
checking for Mono 2.0 GAC for System.dll... found           
checking for Mono 2.0 GAC for System.Xml.dll... found       
checking for Mono 2.0 GAC for System.Web.dll... found       
checking for unrar... /usr/bin/unrar                        
checking for xdelta... /usr/bin/xdelta                      
checking for pkg-config... /usr/bin/pkg-config              
checking pkg-config is at least version 0.9.0... yes        
checking for gtk-sharp-2.0... found                         
checking for glade-sharp-2.0... found                       
configure: creating ./config.status                         
config.status: creating Main.cs                             
config.status: creating Makefile                            
config.status: creating ULL                                 
config.status: creating ULL.desktop                         
rukairo@rukairo-laptop:~/Escritorio/Launcher$ make
/usr/bin/gmcs Main.cs MainWindow.cs Config.cs Patch.cs Game.cs PatchWindow.cs RepairWindow.cs Settings.cs SettingsWindow.cs GameSelectWindow.cs StartGame.cs DetermineOS.cs -noconfig -codepage:utf8 -warn:3 -out:ULL.run -target:exe -resource:ULL.ico -resource:TabulaRasa.png -resource:TabulaRasaPTS.png -resource:DungeonRunners.png -resource:DungeonRunnersPTS.png -resource:Lineage1.png -resource:Lineage2.png -resource:Lineage2Test.png -resource:GuildWars.png -resource:Exteel.png -resource:AutoAssault.png -resource:CityOfHeroes.png -resource:CityOfHeroesEU.png -resource:CityOfHeroesTest.png -resource:NCLauncher.png -resource:MainWindow.glade -resource:PatchWindow.glade -resource:RepairWindow.glade -resource:SettingsWindow.glade -resource:GameSelectWindow.glade -r:System -r:System.Xml -r:System.Web -pkg:gtk-sharp-2.0 -pkg:glade-sharp-2.0
mrukairo@rukairo-laptop:~/Escritorio/Launcher$ make install
make[1]: se ingresa al directorio `/home/rukairo/Escritorio/Launcher'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'ULL' '/usr/local/bin/ULL'
/usr/bin/install: no se puede crear el fichero regular «/usr/local/bin/ULL»: Permiso denegado
make[1]: *** [install-binSCRIPTS] Error 1
make[1]: se sale del directorio `/home/rukairo/Escritorio/Launcher'
make: *** [install-am] Error 2
rukairo@rukairo-laptop:~/Escritorio/Launcher$
rukairo@rukairo-laptop:~/Escritorio/Launcher$
rukairo@rukairo-laptop:~/Escritorio/Launcher$ io `/home/rukairo/Escritorio/Launcher'
> make: *** [install-am] Error 2

---

### Post by whaevr on 2009-05-19
Im getting 404 errors when going to [http://www.lotrolinux.com/ULL/](http://www.lotrolinux.com/ULL/)

Help?

Edit:
Well I found the sourceforge page and downloaded version .8 but now when it trys to patch the game it says

"Can not find the game version file

Please check game directory under options."

and in the terminal I see this
```

wine: cannot find '/usr/lib/ULL//dumpexe.exe'

```

I configured it with --prefix=/usr
Am I doing something wrong?

Edit2:
Edited Config.cs and made a patch for it added it as an attachment, but now it displays in terminal

```

wine: cannot find '/usr/lib/ULL/dumpexe.exe'

```

The path is correct now...I don't see why it can't find it now, if that is even the problem..because I still get the message above.

---

### Post by whaevr on 2009-05-21
Actually even if try and run wine /usr/lib/ULL/dumpexe.exe from terminal I get that wine can't find it...

Its there I know it is..

Edit:
Figured it out. I didn't have /usr/lib/ set as a drive path.

Apparently if that isn't set wine can't "see" any of those files.

So I made a D: /usr/lib in winecfg and it worked fine.

Although when I click launch it fails to run the program, I don't know if thats necessarily ULL's fault though.

---

### Post by ajackson on 2009-05-23
From [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")

> **Section I - General Policy:**
16 Private Messaging users for support is strongly discouraged. It is also unlikely that users will respond to these requests.

I no longer maintain ULL, I have no intention of maintaining ULL and I certainly don't do support via PMs.

---

### Post by morghanphoenix on 2009-05-28
Sad to see it go. Worked great for me when I played Tabula Rasa, was hoping it would help with Aion but this thread was the best match when I googled it.

---

### Post by MadJerry on 2009-06-21
I also got to this post hoping to find something in regard to running Aion on Ubuntu.  Too bad its not still being supported.

---

### Post by OlympicSoftworks on 2009-12-15
That's a loss for the community then.  Can I ask you why you chose to stop work on the NCSoft ULL?  Your LoTRO launcher seems to be a success, so you obviously know what you're doing.

---

### Post by whaevr on 2009-12-15
Well you could go and [vote for the NCSoft launcher](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10172) at winehq's appdb and submit/vote for bug reports for that.

Maybe if it gets enough votes it'll receive some attention!

---

### Post by ajackson on 2009-12-15
> **OlympicSoftworks said:**
> That's a loss for the community then.  Can I ask you why you chose to stop work on the NCSoft ULL?  Your LoTRO launcher seems to be a success, so you obviously know what you're doing.
The main problem I had was people PMing me or emailing me more or less demanding support and some getting quite abusive when I said no since I no longer play any of the games that ULL supports.

I'm assuming at the moment it uses NCSofts launcher, that conatins all the information needed in a file called GameList.xml or Game.xml (or something with a similar name), if someone with the EU and NA versions can post copies of that file I'll have a look to see if it is just a simple mod needed to get it working with ULL. From what I can gather from NCSofts approach it should be a simple change for ULL but I don't want to get into another cycle of people demanding support.

I can't make any promises but I'll certainly look if the info I need is posted.

---

### Post by OlympicSoftworks on 2009-12-23
I know someone that has a US account, I can get those XML files for you for that version...can't say the same for the EU one though.

btw, great choice on your avatar pic.  That series was way ahead of it's time.

---

### Post by Nicodemus144 on 2011-08-08
hi there.

i know this project isn't maintained anymore, but if there's anyone out there who can help i'd really appreciate it.

City of Heroes has moved to the NC Soft launcher, so we're trying to use this program to help us continue playing the game.

when i try to update the CoH client, the ULL crashes with this output:

Marshaling clicked signal
Exception in Gtk# callback delegate
Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.ArgumentOutOfRangeException: Argument is out of range.
Parameter name: index
at System.Collections.Generic.List`1[ULL.Patch].get_Item (Int32 index) [0x00000] in <filename unknown>:0
at ULL.PatchWindow.UpdateGame () [0x00000] in <filename unknown>:0
at ULL.PatchWindow.Run () [0x00000] in <filename unknown>:0
at ULL.MainWindow.OnBtnOKClicked (System.Object sender, System.EventArgs e) [0x00000] in <filename unknown>:0
at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0
--- End of inner exception stack trace ---
at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0
at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] in <filename unknown>:0
at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0
at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0
at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] in <filename unknown>:0
at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0
at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0
at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] in <filename unknown>:0
at GLib.ExceptionManager.RaiseUnhandledException(Syst em.Exception e, Boolean is_terminal)
at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
at Gtk.Application.gtk_main()
at Gtk.Application.Run()
at ULL.GladeApp..ctor(Boolean args)
at ULL.GladeApp.Main(System.String[] args)


i can't really make any sense of that.  i'd appreciate any insights anyone may have.

thanks!

---

### Post by p3hndrx on 2011-08-23
@blitz

try this:
[http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/]("http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/")

---

