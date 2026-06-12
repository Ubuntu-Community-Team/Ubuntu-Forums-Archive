---
title: "Morrowind on Ubuntu.."
date: 2007-02-13
forum: Wine
---

### Post by Aaron Whisman on 2007-02-13
Hey, I still love The Elder Scrolls III: Morrowind. And I want to play it on my system with Ubuntu. Can I install it and play using Wine? And I'm not very...experienced with using a Windows emulator..so..Help if you can?

:D Thanks,
Aaron.

---

### Post by Perfect Storm on 2007-02-13
Use this loki installer (wine related) to install Morrowind: [http://www.liflg.org/?catid=7&gameid=38](http://www.liflg.org/?catid=7&gameid=38)

---

### Post by Aaron Whisman on 2007-02-13
After this is finished downloading, what do I need to do?

---

### Post by Perfect Storm on 2007-02-13
chmod +x <file>
sh <file>

---

### Post by Aaron Whisman on 2007-02-13
Thanks much.

---

### Post by Aaron Whisman on 2007-02-13
Installing :D

Thank you very much!

---

### Post by LordFiodor on 2007-02-13
> **Artificial Intelligence said:**
> Use this loki installer (wine related) to install Morrowind: [http://www.liflg.org/?catid=7&gameid=38](http://www.liflg.org/?catid=7&gameid=38)

That installer installed totally crap when I tried it some weeks ago :(

---

### Post by Perfect Storm on 2007-02-13
Works for me. You have to be more specific if you ran into trouble.

---

### Post by Aaron Whisman on 2007-02-13
I'm having trouble now...I have Wine installed and everything and I installed using that Loki installer, but when I try to run Morrowind it gives me this in the terminal :

> wine: could not load L"c:\\windows\\system32\\morrowind.exe": Module not found


???

---

### Post by EvilMarshmallow on 2007-02-13
I too am having trouble with installation.  The installer says everything went fine but when I attempt to open the game,  I get this:

ben@ubuntu:/usr/local/games/morrowind$ sudo wine Morrowind.exe
err:module:import_dll Library binkw32.dll (which is needed by L"Z:\\usr\\local\\games\\morrowind\\Morrowind.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\usr\\local\\games\\morrowind\\Morrowind.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\usr\\local\\games\\morrowind\\Morrowind.exe" failed, status c0000135
ben@ubuntu:/usr/local/games/morrowind$ sudo wine morrowind
err:module:import_dll Library binkw32.dll (which is needed by L"Z:\\usr\\local\\games\\morrowind\\morrowind.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\usr\\local\\games\\morrowind\\morrowind.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\usr\\local\\games\\morrowind\\morrowind.exe" failed, status c0000135

---

### Post by Perfect Storm on 2007-02-14
You don't need wine when running loki (and diffently not sudo infront)

---

### Post by Aaron Whisman on 2007-02-14
How come when I run the Morrowind launcher absolutely nothing happens??

---

### Post by Perfect Storm on 2007-02-14
There's a morrowind launcher script in the morrowind folder, launch it.

---

### Post by EvilMarshmallow on 2007-02-14
The loki installer was in their "wine/cedega" section.  So was Call of Duty, which I also downloaded, and it's working with wine (albeit with sound issues).  Are you sure I can run the game without wine?

---

### Post by Perfect Storm on 2007-02-14
Aye. When the loki installer pop up I choose to install Morrowin on /home/<username>/morrowind
You'll find a script file there called Morrowind, launch it and it will running. Albeit the movie/intro sequences might lag the game game runs perfectly.

---

### Post by Mongoose on 2007-02-14
Morrowind runs perfectly for me aside from the shadow / paper doll / issues which are well known.  I installed GotY under wine w/o any problems last time I installed it.

---

### Post by Aaron Whisman on 2007-02-14
> aaron@aaron-desktop:~$ morrowind
Wine(X) not in your PATH

Wha? I tried running the script you told me to run and still, nothing is happening... So I tried just typing "morrowind" like it said in the terminal to run and I get that.

---

### Post by Perfect Storm on 2007-02-14
try change to the folder (cd <distination>) and run it from there.

---

### Post by Aaron Whisman on 2007-02-14
I'm sorry, what? ... I'm a really big noob when it comes to running things that weren't made for Linux..

---

### Post by Perfect Storm on 2007-02-14
```
cd ~/morrowind
./morrowind
```

---

### Post by Aaron Whisman on 2007-02-14
> root@aaron-desktop:/usr/local/games/morrowind# morrowind
Wine(X) not in your PATH


>_< Yeah, I'm doing something wrong..sorry.

---

### Post by EvilMarshmallow on 2007-02-14
ben@ubuntu:/usr/local/games/morrowind$ ./morrowind
Wine(X) not in your PATH
ben@ubuntu:/usr/local/games/morrowind$ wine ./morrowind
wine: could not load L"Z:\\usr\\local\\games\\morrowind\\morrowind.": Bad EXE format for 
ben@ubuntu:/usr/local/games/morrowind$ wineserver: could not save registry branch to /home/ben/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/ben/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/ben/.wine/user.reg : Permission denied
'
It hangs here (I let it sit for a while just to see) and I have to ctrl-C to clear it out.

---

### Post by Mongoose on 2007-02-14
It looks like you need to reset permissions in ~/.wine for one thing.  You need to ensure your ~/.wine is valid and you can read/write to it and install morrowind from wine to get the correct application registry flags.  

I suggest removing your ~/.wine and starting over with a normal wine install as a user -- no sudo or whatever you ended up doing.  Read the Oblivion Wine Howto here in the forums, and it's pretty much the same thing.   Just pop in your Morrowind disc instead of Oblivion at the install / run steps.  Also ignore the Oblivion.ini settings section of course, since you're installing Morrowind.  ;)   I play both games under wine with the exact same wine settings, etc.

---

### Post by Perfect Storm on 2007-02-15
Install morrowind without sudo in your home folder.

---

### Post by cor2y on 2007-02-28
Just a quick question i too used the loki installer.
Had the Wine (X) not in your path error.
Couldn't figure it out since wine is installed 
So from the installed directory i just type
> 
wine morrowind_launcher.exe
And it worked even running the script did
Ok so one thing out of the way another problem popped up.
Trying to run Morrowind either via the launcher or morrowind.exe brought up this error
> 
wine morrowind.exe
err:module:import_dll Library binkw32.dll (which is needed by L"H:\\morrowind\\morrowind.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\morrowind\\morrowind.exe" failed, status c0000135
Obviously i am missing some dll files how do i fix this?
Would it have been better to just try to install using wine instead of the loki installer?

---

### Post by tenshi-no-shi on 2007-03-02
What Artificial Intelligence is trying to say is that you don't run the actually .exe file but instead run the shell script that the Loki installer installed. just goto the folder which the installer installed it (the Default being /home/<user name>/morrowind) and run ./morrowind the ./ showing that it's a shell script.

But after installing I get the same error as you the Wine(X) not in path. I have the Game of the Year edition, maybe that is what is causing this.

Also when I browse through the install directory, specifically the /Data Files when I open the sub folders it is just plain weird, instead of what should be there there is something completely different.

---

### Post by Mongoose on 2007-03-02
I'll reiterate just installing off the discs using Wine worked just fine for me.  The last version I installed was GotY edition.  The main thing with Morrowind is your registry needs to be correct.

---

### Post by cor2y on 2007-03-02
OK i will do a wine only install.
Anything  else i need be aware of from the wine install?

Edit
Ok it installed via wine.
Morowind_Launcher works, when i go to play this error comes up however.

> 
Font 0 not found in Morrowind.ini
current Path H:\

So now its a fault with the ini any ideas what i am looking for?

---

### Post by cezdeville on 2007-03-03
you need to get to morrowind folder thru terminal:
cd your/path/to/morrowind/folder
and thet type:
wine 'Morowind Launcher.exe'

worked for me, however i've got another problem - game crashes when i want to pickup letter for capitan (submiting character creation).

anyone had similiar problem? any solution?

---

### Post by tenshi-no-shi on 2007-03-05
How where you able to install the expansion packs? I keep on getting an error asking for the disk containing data3 and there is none.

---

### Post by Mongoose on 2007-03-05
I installed Game of the Year edition for the expansions.  I just installed right off the disc.  I couldn't tell you about multiple disc installs, but I'd assume they'd work fine since others have done it.

---

### Post by tenshi-no-shi on 2007-03-05
Weird because mine is goty too and it did not work, oh well.

---

### Post by Mongoose on 2007-03-05
Oh I had a thought reading this again.  Did you install and patch the game in the correct order?  I can't remember if installing over an existing Morrowind install or starting a new install was better.  I do remember the install taking a long time.  Also remember Linux doesn't treat the CDROM device the same as Windows.  I make multiple mount points that are Wine CDROM devices to avoid some of the related problems of not being able to unmount some game discs during install.

---

### Post by Lystrodom on 2007-03-12
I had the same problem as cezdeville using the standard installation with wine. The loki installer's running now, I'll see if that helps any.

---

### Post by Lystrodom on 2007-03-12
Loki installer gave me the "Wine)x) not in your path!" error thing, just like everyone else.

As for the non-loki installer, for anyone who cares, the terminal spat this out as it closed:

```
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadTexture (0x5629790) Operation not supported for scratch textures
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> 0x502 from glCopyTexSubImage2D @ surface.c / 2248
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadTexture (0x5629790) Operation not supported for scratch textures
wine: Unhandled page fault on read access to 0x00000014 at address 0x7e887faa (thread 0038), starting debugger...
Unhandled exception: page fault on read access to 0x00000014 in 32-bit code (0x7e887faa).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e887faa ESP:0034f150 EBP:0034f208 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:7e8d6158 ECX:0034ec8c EDX:00c70bb0
 ESI:00b10020 EDI:00000000
Stack dump:
0x0034f150:  00000c01 0034f1ec 00000003 05a80000
0x0034f160:  00110000 05a80000 7e88e721 00100038
0x0034f170:  7a3e2318 7e84d01b 7e8d6158 05629790
0x0034f180:  00c70bb0 00b10020 7e88fbea 00000000
0x0034f190:  7e8d1934 0034f218 00000001 7d193000
0x0034f1a0:  0034f224 a001ffff 00000000 00001fff
Backtrace:
=>1 0x7e887faa in wined3d (+0x57faa) (0x0034f208)
  2 0x7e88be17 IWineD3DSurfaceImpl_BltFast+0xf7() in wined3d (0x0034f268)
  3 0x7e8ef89b in d3d8 (+0xf89b) (0x0034f2f8)
  4 0x0042f697 in morrowind (+0x2f697) (0x0020d428)
  5 0x001c1478 (0x00746928)
  6 0x00433320 in morrowind (+0x33320) (0x00433260)
  7 0x64007298 (0x5b68ff6a)
  8 0x00000000 (0x00000000)
0x7e887faa: cmpl        0x14(%eax),%edx
Modules:
Module  Address                 Debug info      Name (86 modules)
PE      400000-7e4000   Export          morrowind
PE      30000000-3006e000       Deferred        binkw32
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d229000-7d25b000       Deferred        uxtheme<elf>
  \-PE  7d230000-7d25b000       \               uxtheme
ELF     7d25b000-7d270000       Deferred        midimap<elf>
  \-PE  7d260000-7d270000       \               midimap
ELF     7d296000-7d2ae000       Deferred        msacm32<elf>
  \-PE  7d2a0000-7d2ae000       \               msacm32
ELF     7d2ae000-7d2ea000       Deferred        wineoss<elf>
  \-PE  7d2c0000-7d2ea000       \               wineoss
ELF     7d541000-7d546000       Deferred        libxfixes.so.3
ELF     7d546000-7d54f000       Deferred        libxcursor.so.1
ELF     7d54f000-7d56c000       Deferred        imm32<elf>
  \-PE  7d560000-7d56c000       \               imm32
ELF     7d56c000-7d58a000       Deferred        ximcp.so.2
ELF     7d58a000-7d58c000       Deferred        xlcutf8load.so.2
ELF     7d58c000-7d58f000       Deferred        libxrandr.so.2
ELF     7d58f000-7d597000       Deferred        libxrender.so.1
ELF     7d597000-7d59a000       Deferred        libxinerama.so.1
ELF     7dac0000-7db4d000       Deferred        winex11<elf>
  \-PE  7dad0000-7db4d000       \               winex11
ELF     7db4d000-7db6b000       Deferred        libexpat.so.1
ELF     7db6b000-7db9a000       Deferred        libfontconfig.so.1
ELF     7db9a000-7dbae000       Deferred        libz.so.1
ELF     7dbae000-7dc18000       Deferred        libfreetype.so.6
ELF     7dc18000-7dcd4000       Deferred        comctl32<elf>
  \-PE  7dc20000-7dcd4000       \               comctl32
ELF     7dcd4000-7dd39000       Deferred        msvcrt<elf>
  \-PE  7dce0000-7dd39000       \               msvcrt
ELF     7dd9c000-7e622000       Deferred        libglcore.so.1
ELF     7e622000-7e627000       Deferred        libxdmcp.so.6
ELF     7e627000-7e6a1000       Deferred        libglu.so.1
ELF     7e6a1000-7e72d000       Deferred        libgl.so.1
ELF     7e72d000-7e7f6000       Deferred        libx11.so.6
ELF     7e7f6000-7e803000       Deferred        libxext.so.6
ELF     7e803000-7e81b000       Deferred        libice.so.6
ELF     7e81b000-7e8d7000       Export          wined3d<elf>
  \-PE  7e830000-7e8d7000       \               wined3d
ELF     7e8d7000-7e8ff000       Export          d3d8<elf>
  \-PE  7e8e0000-7e8ff000       \               d3d8
ELF     7e8ff000-7e948000       Deferred        dsound<elf>
  \-PE  7e910000-7e948000       \               dsound
ELF     7e948000-7e97e000       Deferred        dinput<elf>
  \-PE  7e950000-7e97e000       \               dinput
ELF     7e97e000-7e997000       Deferred        dinput8<elf>
  \-PE  7e980000-7e997000       \               dinput8
ELF     7e997000-7e9ab000       Deferred        lz32<elf>
  \-PE  7e9a0000-7e9ab000       \               lz32
ELF     7e9ab000-7e9c4000       Deferred        version<elf>
  \-PE  7e9b0000-7e9c4000       \               version
ELF     7e9c4000-7ea52000       Deferred        winmm<elf>
  \-PE  7e9d0000-7ea52000       \               winmm
ELF     7ea52000-7ea65000       Deferred        libresolv.so.2
ELF     7ea65000-7ea83000       Deferred        iphlpapi<elf>
  \-PE  7ea70000-7ea83000       \               iphlpapi
ELF     7ea83000-7ead8000       Deferred        rpcrt4<elf>
  \-PE  7ea90000-7ead8000       \               rpcrt4
ELF     7ead8000-7eb71000       Deferred        ole32<elf>
  \-PE  7eaf0000-7eb71000       \               ole32
ELF     7eb71000-7ebb6000       Deferred        advapi32<elf>
  \-PE  7eb80000-7ebb6000       \               advapi32
ELF     7ebb6000-7ebc1000       Deferred        libgcc_s.so.1
ELF     7eca0000-7ed57000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed57000       \               gdi32
ELF     7ed57000-7ee91000       Deferred        user32<elf>
  \-PE  7ed70000-7ee91000       \               user32
ELF     7ee91000-7eea7000       Deferred        libnsl.so.1
ELF     7eea7000-7eeb0000       Deferred        libnss_compat.so.2
ELF     7eeb4000-7eeb7000       Deferred        libxau.so.6
ELF     7eeb7000-7eec0000       Deferred        libsm.so.6
ELF     7efca000-7eff0000       Deferred        libm.so.6
ELF     7eff0000-7eff5000       Deferred        libxxf86vm.so.1
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     b7ce0000-b7ce2000       Deferred        libnvidia-tls.so.1
ELF     b7ce2000-b7cec000       Deferred        libnss_nis.so.2
ELF     b7cee000-b7cf2000       Deferred        libdl.so.2
ELF     b7cf2000-b7e26000       Deferred        libc.so.6
ELF     b7e27000-b7e3a000       Deferred        libpthread.so.0
ELF     b7e4a000-b7f5b000       Deferred        libwine.so.1
ELF     b7f5d000-b7f78000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000035 (D) C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe
        00000042   15
        00000041   -1
        00000026   15
        00000033    0
        00000038    0 <==
0000003d 
        0000003f    0
        0000003b    0
0000000a 
        0000000c    0
        0000000b    0

```

---

### Post by SBFC on 2007-03-13
I get the same 'Deferred' errors as Lystrodom when using the Loki installed version. As well as the Wine(X) not in your path (cd'd to install directory and ran .exe launcher).

When I try and install off cd's half way through I get a dialog asking me for the location of 'data3.cab'. Browsing the cd reveals no such file. 

Thought I'd try and copy all contents of cd to my HD and install, but I can't even do that. While copying data2.cab it fails. Complains it can't copy the whole thing. :(

---

### Post by ZylGadis on 2007-03-13
I have a different problem. I've been trying to run Morrowind under GNU/Linux for ages, and it finally became possible with wine 0.9.30 (and above). There are minor glitches such as choppy sound at times. I have a huge problem though:
When I start a new game, I get to the customs officer (Socius) and create the parameters of my character. He then tells me to pick my documents from the table, I do that, and the game crashes.
When I try to load a game that was started in Windows, the game crashes immediately.
Wine's output does not produce any sensible error messages in either case, and I can't find anybody with a similar problem. Really weird. My GPU is Nvidia Geforce 5200FX, and I'm running the stock nvidia drivers from Dapper's repositories.
The only thing I can think of is tinker with the driver and perhaps recompile the kernel with nvidia's shingle instead of agpgart, but I've no time for that now, and anyway, I doubt it will help.
Anybody with a similar problem?

---

### Post by cor2y on 2007-03-13
SBFC try copying the files off the cd in a virtual version of windows or booting back into windows and doing it there if you have a dual boot setup.
I didn't have one so i made a very small virtual  windows install when i ran into this problem with neverwinter nights, the loki installer would not correctly extract the data from the cds and trying to move the files in linux resulted in errors for a moment i thought my discs were damaged in some way , perhaps they are but the virtual windows pc had no problem moving the files off the disc to a folder, then move that folder to home or a shared folder created with samba.

I never did get morrowind to run outside of the control panel where you can add remove plugins and set screen resolutions so i can't help ZylGadis. But at the time i was using 0.9.31 of wine.

Maybe roll back to 0.9.30 see what happens.

---

### Post by Lystrodom on 2007-03-14
Zyl: Yeah, that's the same problem I had above.

No idea how to help you, though. I eventually gave up and have been playing it on my XP install.

---

### Post by tenshi-no-shi on 2007-04-15
Has anyone gotten mods to work with Morrowind and how do you load them?

Edit: Ok so I was able to enable and disable mods by using TESTool. I also have been playing it quite a bit since then. It works all very well for a DirectX game running in linux. The only problems I have are the "Paper Doll" in the inventory does not render at all, just a white screen. The mini maps don't render in both the one while playing and the bigger map in the menu. but other than that it seams fine.

---

### Post by Jiawen on 2007-05-11
> **Mongoose said:**
> I'll reiterate just installing off the discs using Wine worked just fine for me.  The last version I installed was GotY edition.  The main thing with Morrowind is your registry needs to be correct.How do you make your registry correct? I'm having the same errors as everyone else -- "Wine(X) not in your path" -- and it seems like the registry is the problem, but I have no idea how to fix it.

---

### Post by Josey on 2007-06-27
```
Wine(X) not in your path
```

:(
Here is the launcher.  Can someone modify this to make it work?
```
#!/bin/sh

GAME_BINARY="Morrowind.exe"
SUBDIR="."
WINE_NAMES="cedega winex3 cvswinex winex wine"

#----------------------------------------
script=$0
count=0

while [ -L "$script" ]  
do
    script=`perl -e "print readlink(\"$script\"), \"\n\""`
    count=`expr $count + 1`

    if [ $count -gt 100 ]  
    then
       	echo "Too many symbolic links"
       	exit 1
    fi
done

GAME_DIR=`dirname $script`

if [ -z "$WINE_EXEC" ]
then
	WINE_EXEC=`type -p $WINE_NAMES | head -n 1`
fi


if [ -e "$WINE_EXEC" ]
then
	cd $GAME_DIR
	cd $SUBDIR
	$WINE_EXEC $GAME_BINARY $* &
	sleep 2 &&
	renice 5 -p `pgrep wineserver`
else 
	echo "Wine(X) not in your PATH"
	exit 1
fi

```

---

### Post by curiousnoob on 2007-09-22
Resurrecting the thread to see if anyone ever came up with an answer.  I would love to install this game on my machine.

---

### Post by NeoFax on 2007-12-01
For those that have WineX not in your path, do you have Wine installed at all? (including Cedega, WineCVS or such)  If not, then install wine using sudo apt-get install wine.  If so, change the line in the script WINE_NAMES to only have wine.  This should force the script to look only for wine and then use it to start the game.  The easiest solution would be to just open a terminal program and cd to your install directory and do: wine Morrowind\ Launcher.exe(remember Linux is case sensitive).  This will then launch Morrowind.  Enjoy!

---

### Post by PacShady on 2007-12-18
I have an odd problem trying to install the game. I get two different errors, that occur on alternating runs of Setup.exe. The first problem comes up straight after I run it, saying "The InstallSheild Engine (iKernel.exe) could not be launched. (0x80004002)", with this in the terminal:

```
err:ole:CoGetClassObject no class object {91814ec0-b5f0-11d2-80b9-00104b1f6cea} could be created for context 0x4
```

The second error occurs when the InstallShield loads first, and then crashes with "An error occurred while parsing command line arguments or reading Setup.ini. (0x80030070)", with this terminal output:

```
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ole:ServerRpcChannelBuffer_GetDestCtx (0x34f5b0,0x34f5b4), stub!
err:ole:CoMarshalInterface Failed to write OBJREF header to stream, 0x80030070
err:rpc:I_RpcReceive we got fault packet with status 0x80030070
fixme:ole:NdrClearOutParameters (0x33eedc,0x10004212,0x33f160): stub

```

Although sometimes it does the SAME error with THIS terminal output:

```
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80030070
fixme:ole:NdrClearOutParameters (0x33eedc,0x10004212,0x33f160): stub
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005
err:ole:deserialize_param Failed to read integer 4 byte
err:ole:TMStubImpl_Invoke Failed to deserialize param State, hres 80004005

```

...


That's be right, as soon as I'm about to send this message it decides to work spontaneously. But still, I just tested, and trying to run the setup file again causes the same problem. So it was just a fluke it worked that one time.

Can someone look at this and tell me that a computer ONLY does what it's told to, when such randomness like this happens? Oh, and also if someone knows why it's being screwy too, that'd be good too.

'Shady

---

### Post by PacShady on 2007-12-24
OK, got it installed finally (just kept running the setup file over and over and over again until it finally ran), got my widescreen set up all nicely and everything, now I have a problem with my controls. Seems the game likes to freeze when one tries to change the controls (appears to be a WINE issue). The only "fix" for it I could find involved installing it in Windows, changing the controls there, and then transferring the registry entries into WINE's registry. All good in theory, except for the matter of having to install Windows, which I have no space for. I DID try installing it into a VirtualBox, and then installing Morrowind there, but after firstly having problems with the game complaining about a debugger or something, and realising that for some reason the patch I have for Morrowind is incompatible with the version I have, I found that Morrowind just won't run if it can't find a valid 3D card and, thanks to the brilliance of VirtualBox not being able to emulate 3d graphics cards or translating them directly, I now have NO way of changing my controls, because Bethesda decided to use some weird number reference system where 17956864 means "W". Anyone know of ANOTHER way of changing the controls???

'Shady

---

### Post by DarkSim on 2007-12-28
I had the same problem with changing controls and someone was nice enough to figure out the controls on their Windows registry. Look through these and type 'em in your registry if thats what control you want.

New Key Codes
-----------------------
Up arrow
1c90000

Down Arrow
1d10000

Left Arrow
?Couldn't Find Reg Entry. Possibly: 1cc0000

Right Arrow
?Couldn't Find Reg Entry. Possibly: 1ce0000

Return:
11d0307

Backspace:
10f030a

/
1360305

RShift
12b0306
edit:
I think it is infact 1370000


Click Mouse Wheel:
Hex:
2030000
Dec:
33751040

R is:
Hex: 1140304
Dec: 18088708

.
1350303

,
1340304

As you can see I use a strange control setup but it works for me. I think it is the hex you use but its been a while so I have both for a couple of them.

---

### Post by brennydoogles on 2008-01-02
It looks like the Loki installer is gone... anyone know where to find one?

---

### Post by DarkSim on 2008-01-02
Did you try installing it with Wine? It worked like a charm for me.

---

### Post by ClanCC on 2008-01-03
Fail.. Using Wine 0.9.52. GoTY Version of Morrowind, Happens when i try to exit the prison ship onto Seyda Neen.
```

fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1c9850) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1c9850) : stub
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(1024,768)
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(1024,768)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:quartz:DSoundRender_create Cannot create Direct Sound object (88780078)
fixme:ole:CoCreateInstance no instance created for interface {56a86895-0ad4-11ce-b03a-0020af0ba770} of class {79376820-07d0-11cf-a24d-0020afd79767}, hres is 0x88780078
err:quartz:FilterGraph2_Render Unable to create filter (88780078), trying next one
err:ole:CoGetClassObject class {e30629d1-27e5-11ce-875d-00608cb78066} not registered
err:ole:CoGetClassObject no class object {e30629d1-27e5-11ce-875d-00608cb78066} could be created for context 0x1
err:quartz:FilterGraph2_Render Unable to create filter (80040154), trying next one
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:MediaPosition_put_CurrentPosition (0x3d693d0)->(0.000000) stub!
fixme:quartz:PullPin_Seek (0x3116518)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x3116518)->()
fixme:quartz:PullPin_EndFlush (0x3116518)->()
fixme:quartz:PullPin_Seek (0x3116518)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x3116518)->()
fixme:quartz:PullPin_EndFlush (0x3116518)->()
wine: Unhandled page fault on read access to 0x00000000 at address 0x402f6a (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00402f6a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00402f6a ESP:0033fbf0 EBP:0033fc18 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:02ab4258 ECX:0154c8e8 EDX:40000000
 ESI:0154c8e8 EDI:00000000
Stack dump:
0x0033fbf0:  02208ed8 00489856 40000000 0154c8e8
0x0033fc00:  034a1bf0 035834d8 02ab4258 c0c090fd
0x0033fc10:  0154c8e8 00562023 03583468 0045cffa
0x0033fc20:  0033fca8 035834d8 439fdf84 42b7f629
0x0033fc30:  42b38106 4310f644 0251ff50 0000000c
0x0033fc40:  0033fc70 7e8a2d2e 00110000 00000002
Backtrace:
=>1 0x00402f6a in morrowind (+0x2f6a) (0x0033fc18)
  2 0x0045cffa in morrowind (+0x5cffa) (0x03583468)
  3 0x52464552 (0x0074a140)
  4 0x004ee920 in morrowind (+0xee920) (0x004e45a0)
0x00402f6a: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (94 modules)
PE        400000-  7e4000       Export          morrowind
PE      30000000-3006e000       Deferred        binkw32
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7ba5f000-7bb00000       Deferred        oleaut32<elf>
  \-PE  7ba70000-7bb00000       \               oleaut32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf5c000-7bf7b000       Deferred        devenum<elf>
  \-PE  7bf60000-7bf7b000       \               devenum
ELF     7bf7b000-7bfa2000       Deferred        msvfw32<elf>
  \-PE  7bf80000-7bfa2000       \               msvfw32
ELF     7bfa2000-7c000000       Deferred        quartz<elf>
  \-PE  7bfb0000-7c000000       \               quartz
ELF     7c809000-7c83b000       Deferred        uxtheme<elf>
  \-PE  7c810000-7c83b000       \               uxtheme
ELF     7c85b000-7c870000       Deferred        midimap<elf>
  \-PE  7c860000-7c870000       \               midimap
ELF     7c870000-7c896000       Deferred        msacm32<elf>
  \-PE  7c880000-7c896000       \               msacm32
ELF     7c896000-7c8b3000       Deferred        imm32<elf>
  \-PE  7c8a0000-7c8b3000       \               imm32
ELF     7c8b3000-7c8bb000       Deferred        libxrender.so.1
ELF     7c8be000-7c8d6000       Deferred        msacm32<elf>
  \-PE  7c8c0000-7c8d6000       \               msacm32
ELF     7c970000-7c97b000       Deferred        libgcc_s.so.1
ELF     7c982000-7c996000       Deferred        avicap32<elf>
  \-PE  7c990000-7c996000       \               avicap32
ELF     7e1d6000-7e41f000       Deferred        i915_dri.so
ELF     7e41f000-7e429000       Deferred        libdrm.so.2
ELF     7e429000-7e42e000       Deferred        libxfixes.so.3
ELF     7e42e000-7e431000       Deferred        libxdamage.so.1
ELF     7e431000-7e492000       Deferred        libgl.so.1
ELF     7e492000-7e497000       Deferred        libxdmcp.so.6
ELF     7e497000-7e49a000       Deferred        libxau.so.6
ELF     7e49a000-7e58b000       Deferred        libx11.so.6
ELF     7e58b000-7e599000       Deferred        libxext.so.6
ELF     7e599000-7e59e000       Deferred        libxxf86vm.so.1
ELF     7e59e000-7e5b6000       Deferred        libice.so.6
ELF     7e5b6000-7e5be000       Deferred        libsm.so.6
ELF     7e5c5000-7e5ce000       Deferred        libxcursor.so.1
ELF     7e5ce000-7e5d1000       Deferred        libxcomposite.so.1
ELF     7e5d1000-7e5d7000       Deferred        libxrandr.so.2
ELF     7e5d9000-7e663000       Deferred        winex11<elf>
  \-PE  7e5f0000-7e663000       \               winex11
ELF     7e6cb000-7e6eb000       Deferred        libexpat.so.1
ELF     7e6eb000-7e716000       Deferred        libfontconfig.so.1
ELF     7e716000-7e72b000       Deferred        libz.so.1
ELF     7e72b000-7e79b000       Deferred        libfreetype.so.6
ELF     7e7b6000-7e875000       Deferred        comctl32<elf>
  \-PE  7e7c0000-7e875000       \               comctl32
ELF     7e875000-7e8d9000       Deferred        msvcrt<elf>
  \-PE  7e880000-7e8d9000       \               msvcrt
ELF     7e8d9000-7e9c8000       Deferred        wined3d<elf>
  \-PE  7e8f0000-7e9c8000       \               wined3d
ELF     7e9c8000-7e9f3000       Deferred        d3d8<elf>
  \-PE  7e9d0000-7e9f3000       \               d3d8
ELF     7e9f3000-7ea3d000       Deferred        dsound<elf>
  \-PE  7ea00000-7ea3d000       \               dsound
ELF     7ea3d000-7ea73000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea73000       \               dinput
ELF     7ea73000-7ea8c000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea8c000       \               dinput8
ELF     7ea8c000-7eaa0000       Deferred        lz32<elf>
  \-PE  7ea90000-7eaa0000       \               lz32
ELF     7eaa0000-7eb2c000       Deferred        winmm<elf>
  \-PE  7eab0000-7eb2c000       \               winmm
ELF     7eb2c000-7eb3f000       Deferred        libresolv.so.2
ELF     7eb41000-7eb5a000       Deferred        version<elf>
  \-PE  7eb50000-7eb5a000       \               version
ELF     7eb5a000-7eb79000       Deferred        iphlpapi<elf>
  \-PE  7eb60000-7eb79000       \               iphlpapi
ELF     7eb79000-7ebd6000       Deferred        rpcrt4<elf>
  \-PE  7eb90000-7ebd6000       \               rpcrt4
ELF     7ebd6000-7ec75000       Deferred        ole32<elf>
  \-PE  7ebe0000-7ec75000       \               ole32
ELF     7ec75000-7ecbe000       Deferred        advapi32<elf>
  \-PE  7ec80000-7ecbe000       \               advapi32
ELF     7ecbe000-7ed55000       Deferred        gdi32<elf>
  \-PE  7ecd0000-7ed55000       \               gdi32
ELF     7ed55000-7ee8c000       Deferred        user32<elf>
  \-PE  7ed70000-7ee8c000       \               user32
ELF     7efab000-7efb6000       Deferred        libnss_files.so.2
ELF     7efb6000-7efc0000       Deferred        libnss_nis.so.2
ELF     7efc0000-7efe5000       Deferred        libm.so.6
ELF     7efe8000-7f000000       Deferred        libnsl.so.1
ELF     b7cc1000-b7cca000       Deferred        libnss_compat.so.2
ELF     b7ccb000-b7ccf000       Deferred        libdl.so.2
ELF     b7ccf000-b7e19000       Deferred        libc.so.6
ELF     b7e1a000-b7e32000       Deferred        libpthread.so.0
ELF     b7e4d000-b7f61000       Deferred        libwine.so.1
ELF     b7f63000-b7f7f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe
        00000011    0
        0000000f   -1
        0000000d    0
        00000009    0 <==
Backtrace:
=>1 0x00402f6a in morrowind (+0x2f6a) (0x0033fc18)
  2 0x0045cffa in morrowind (+0x5cffa) (0x03583468)
  3 0x52464552 (0x0074a140)
  4 0x004ee920 in morrowind (+0xee920) (0x004e45a0)


```

---

### Post by MisterBear on 2008-01-04
If I remember correctly, you need to use:

wine ~/Morrowind.exe

---

### Post by brennydoogles on 2008-01-04
Anyone have a copy or link to the Loki Installer??

---

### Post by archyslave on 2008-01-21
I'm trying to install the old version (w/o expansions) and InstallShield hangs up about 20% of the way in.  Using the latest version of WINE.

I'll try again with a different disc when I get the chance.

---

### Post by Skully on 2008-01-30
The same thing happens to me, except I'm trying to install the GOTY edition.

---

### Post by happyhamster on 2008-01-30
Try installing with wine 0.9.52 or earlier. Quite a lot of games won't install when using 0.9.53 or 0.9.54. (This is a known regression, no need to file bug reports or such. (Like I did :lolflag:)

You can get older wine versions from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

First, remove the previous wine from your system:

sudo apt-get remove --purge wine

Download the apropriate .deb file and double-click it to start the installation.

Good luck.

---

### Post by brennydoogles on 2008-01-31
> **brennydoogles said:**
> Anyone have a copy or link to the Loki Installer??

Bump?

---

### Post by kenora_kid02 on 2008-03-15
Ooof... This whole Morrowind fiasco is getting on my nerves!

I've pretty much got the same problem as ClanCC... I get to the prison ship's hatch to Seyda Neen and the game stalls once the "Loading Exterior" bar fills up.

I'm running Wine 9.57, I've edited my registry, I've modified my morrowind.ini file, I've erased the music... everything just like the Wine page suggested.  

For a while, the game wouldn't even start for me... I was trying to run it in windowed mode at 800X600.  It was only once I changed it to Virtual Desktop / 800X600 / Fullscreen that I got any life out of the thing at all.

The funny thing is, I've been able to get the game working near flawlessly.  Just last week I used Automatix to get everything I needed and for some reason it worked.. I had to re-install Gutsy, and now I can't get Automatix at all.. site's down or something.

Anyone know of where I might find some answers to in-game crashes?

Good luck folks, it's a great game, let's get it working!

---

### Post by DarkSim on 2008-03-15
Maybe it a sound problem. Open up the terminal and type winecfg. Now click on the audio tab and try ALSA if it is set at OSS or OSS if its set at ALSA.I forget which way it has to go but thats what cleared up the problem for me.


I just wanted to add if you play the GOTY version there is a bug that causes one of the cells of Tribunal that makes that room unplayable due to fog.This mod will clear up the cell so do grab it so you don't pull your hair out over it.

[http://planetelderscrolls.gamespy.com/View.php?view=Mods.Detail&id=3188](http://planetelderscrolls.gamespy.com/View.php?view=Mods.Detail&id=3188)

---

### Post by kenora_kid02 on 2008-03-16
> **DarkSim said:**
> Maybe it a sound problem. Open up the terminal and type winecfg. Now click on the audio tab and try ALSA if it is set at OSS or OSS if its set at ALSA.I forget which way it has to go but thats what cleared up the problem for me.


No luck.  Thanks though, I never would have thought about Audio... and there definitely was some improvement in THAT.  Also, thanks for the Tribunal fog-patch link... 'twill come in quite useful!

---

### Post by kenora_kid02 on 2008-03-16
Okay, problem solved!

I figured out that my main choking point was "unhandled page fault on read access to...", so once I figured that out I went to the Wine AppDB for Bloodmoon.... even though I've just got GOTY.  A user had a similar problem.

Right... so here's what I had to do to get it working on Wine 0.9.57:

In my registry, under a user-created Direct3D key, I added the strings:

OffscreenRenderingMode : pbuffers
VideoMemorySize : 64

Notice the lack of UseGLS? That's because it's already built in!

In my winecfg, settings look like this:

Applications:
Windows Version : Windows 98

Audio
ALSA : Emulation : Driver Emulation

Graphics
Emulate a virtual desktop : 800X600
Vertex Shader Support : Hardware

In my Morrowind.ini file, I changed:

Max FPS to 60 (or 40... low is good)
SkipProgramFlows=1
DontThreadLoad=1
Interior Cell Buffer = 1
Exterior Cell Buffer = 9

And... that's pretty much it.  Hope someone else gets it working!

Good Luck!

---

### Post by pandayanyan on 2008-04-07
[QUOTE=ZylGadis;2291700
When I start a new game, I get to the customs officer (Socius) and create the parameters of my character. He then tells me to pick my documents from the table, I do that, and the game crashes....
Wine's output does not produce any sensible error messages in either case, and I can't find anybody with a similar problem. Really weird....
Anybody with a similar problem?[/QUOTE]

I am having the exact same problem. but my game doesnt really crash. I pick up the documents and i can barely see the text on it. What should be a paper texture is all rainbow lines and stuff. I can see or click on the take button to progress further. I am running an Nvidia 7300LE Graphics card. I dont think it is a problem with the card so much because it worked the first time I played but i took a break and went back and now i have this problem. 

Does anyone have any suggestions?:confused:

---

### Post by pandayanyan on 2008-04-15
bump

---

### Post by Jiawen on 2008-04-27
> **kenora_kid02 said:**
> And... that's pretty much it.  Hope someone else gets it working!Using the Loki installer, Kenora's suggestions, the UESP Wiki page and a lot of effort, I managed to get Morrowind running. I'm going to have to boot up Windows once or twice to see what mods I was running before so I can again get my game-winning character running, and the game runs pretty slowly, but other than that, everything seems to be working fine. Thanks to everyone who helped!

Other tips and observations:[list][*]When I try to run it from an icon I have set up as wine ~/Morrowind_Launcher.exe, it doesn't load the mods or .esm files. But when I run it from a directory, it works. So I created a shell script that moves to that directory and then does "wine Morrowind_Launcher.exe". It works, but I have no idea why.  
[*]Remember to install in the order Morrowind, Tribunal, Bloodmoon. Doing it in a different order will result in weird errors.
[*]Morrowind doesn't create a Saves directory, or at least the Loki installer doesn't. I started a new game and got it to the point where I could save; this created the save games directory (Saves) in the main Morrowind directory. I don't know if just creating a Saves folder directly will cause Morrowind to allow loading and saving.
[*]The Loki installer copies a lot of files strangely. For example, the Data Files folder (I think it was) ends up with a copy of the main directory and all its contents rather than the data files it's supposed to have. The meshes folder was also missing a bunch of things (among others, tx_CURSOR.tga, the main mouse cursor image), and the Music directory ended up with only a few of the files it was supposed to have (~12 folders' worth in Windows install, only one folder or so in the Loki install). I have no idea why all this happened, but I copied over all the appropriate files from my Windows install of Morrowind and that eventually worked fine. 
[/list]

---

### Post by OpposingForce on 2008-07-14
I have wine 1.1.1 and morrowind runs like crap.  As soon as I start a new game I get outside, and all of the water is completely black and there is a black box where my health and mana bar goes.  But when I talk to the customs officer the water is no longer black, but just completely dissapears when I am in dialouge with him.  Then when I exit the dialogue the water goes black and the black box reappears.  Also the game runs pretty choppy.

My specs;

Toshiba Satellite A215
Ati radeon X1200 
1 gb of ram (upgrading to 4gb in 2 days)

---

### Post by brennydoogles on 2008-07-15
> **OpposingForce said:**
> I have wine 1.1.1 and morrowind runs like crap.  As soon as I start a new game I get outside, and all of the water is completely black and there is a black box where my health and mana bar goes.  But when I talk to the customs officer the water is no longer black, but just completely dissapears when I am in dialouge with him.  Then when I exit the dialogue the water goes black and the black box reappears.  Also the game runs pretty choppy.

My specs;

Toshiba Satellite A215
Ati radeon X1200 
1 gb of ram (upgrading to 4gb in 2 days)

How is your ATI card running in general?? Maybe it's that I hate ATI, but my first assumption was to blame them and their complete lack of Linux support.

---

### Post by OpposingForce on 2008-07-16
> **brennydoogles said:**
> How is your ATI card running in general?? Maybe it's that I hate ATI, but my first assumption was to blame them and their complete lack of Linux support.

I have the ATI linux drivers installed and enabled and counter strike 1.6 runs well.  I haven't tried many other games on my laptop yet.  Also if I run Morrowind more than once per ubuntu login session it seems, then it will start flashing a white box in the upper left of the screen.  I've attached a screenshot of the game.

Also Morrowind resets my desktop resolution, but doesn't change it back when I exit the game.

And I have tried all the fixes on this page:

[http://www.uesp.net/wiki/Morrowind:Linux](http://www.uesp.net/wiki/Morrowind:Linux)

and it seems OffScreenRenderingMode being set to fbo fixed the flashing white box in the upper left of the screen, but the water and area around my health bar is still all completely black

---

### Post by OpposingForce on 2008-07-19
So I'm guessing no one can provide assistance?  I've changed to 64 bit ubuntu and replaced the 1gb ram with 4gb.

edit -  Guess not, I'm going back to XP.

---

### Post by Ascendaeus on 2009-01-25
That site Was Irrelevant! (NO MRNWND):( )))>>>--- Have EXE! Have Expnapsions! Have WINE! Have Hardy! and proper equipment Nvidia 9600 and Quad Core 4gig ramnm but _-_ Moe Noreohwyndde' ~!!!! pls help please respond (Error Success)! (Error Success)??? wtf pls hlp distress pls help  ()))((((())()(()))))()()(__++=-=---===++All Sough,, what of uhhmm,, Emm Gee Eee? Better boddies? creeper change, balmora candle shop,  Hough would  Aye Bee installing regular mods???? would it work the same obviously not, pls forgive my ignorant *** Raised on windows(which won't install)

---

### Post by Ascendaeus on 2009-01-25
ohh god!! i just realized this forum hasn't been spoken in in six months!! That sucks!!

---

### Post by Arazu on 2009-03-02
Exiting the Prison Ship is a known issue with Morrowind. It's not specific to Wine. There are many suggestions on their site.

I'm going to be trying this tomorrow. Wish me luck.

Edit: Considering the mods aren't installed programs or additions to existing programs shouldn't they work fine? They are just files added to a directory.

---

### Post by Ascendaeus on 2009-03-23
I too love Morrowind very much and the only obstacle is the fact that it needs a cd to play. Kiso is dependant on something that can't be installed and deamon tools is apparently irrelevant. WTF? Ubuntu is so god damned difficult. !Azureus! is now available in my add/remove programs but "it"(just like kiso) is dependant on something that i don't have and can't install! ? WTF?  All this menial technical gibberish and ********! Bill gates is ******* evil and the microsoft corporation is Strangling the entire industry, BUT, Windows is somuch ******* SIMPLER! Why is all this **** so *******  COMPLICATED?  i gotta download and install anew Libs.dll/dsl/ dot ******* complicated gibberish for every single little thing that i want to do Why isn't ubuntu more like windows"(u know in the way that every thing is easy simple and computer gibberish free?) Why do i need a new communist establishment(library) inside my hard drive to play some doom knockoff or a clone of old skool Command And Conquer? All my **** is INCOMPATIBLE!all my **** IS NOT A DIRECTORY  or, IT IS A DIRECTORY. This loki thing that you told me to get is not even doing anything and google doesn't answer these ******* questions so don't act like like  im a naive ignorant little kid I'm ******* dying over here man it's all ******* bad I BOUGHT AND BUILT A CUSTOM COMPUTER OUT OF ONLY THE BEST COMPONENTS SO THAT I COULD HACK AND SLASH THRU MY OWN LITTLE ******* WORLD ON MY FAVOURITE GAME OF ALL TIME MORROWIND! MOD IT! CES INFINITE POSSIBILITIES! WINDOWS WON'T INSTALL! UBUNTU IS APPARENTLY USER FRIENDLY! NO! IT'S NOT! if WINDOWS gets an 8 out of ten for user compatability then ubuntu get's like a 2! i'm so goddamned confused man why is there all this irrelevant gibberish in the terminal SUDO **** YOU!!!!!!!!!!!!!

---

### Post by Progressive on 2009-03-24
Morrowind has worked for me for a long time as long as I was using proprietary drivers.

If you actually had an official morrowind cd then it would be easy. Since you mention azureus, I am assuming you don't. If that is the case, and you have no blank cds, it can still work without downloading anything special. 

You need to do the following things

make a directory called /mnt/iso

```
sudo mkdir /mnt/iso
```

then you need to mount the iso. If your iso is called morrowind.iso and it is in your home directory, type this:

```
sudo mount -o loop ~/morrowind.iso /mnt/iso

```

otherwise, just change "~/morrowind.iso" to whatever directory and file it is. Every time your computer restarts, it will unmount and in order to play you will have to mount the iso again using this command. 

Lastly, go into the WINE configuration. If you can't find it in your applications menu, then type:

```
winecfg
```

Then click on the drives tab and make sure it detects /mnt/iso as E drive or whatever.

cheers

---

### Post by Progressive on 2009-03-24
To avoid having to mount the iso each time, you can make it permanently mounted by editing the configuration file /etc/fstab with your favorite editor. If you use KDE, you might like kate:

```
sudo kate /etc/fstab
```

add this line to the end 

> ~/morrowind.iso /mnt/iso  udf,iso9660,user,loop 0 0

EDIT: This fix doesn't work.... but I'm pretty sure it is something like this. Anyone know what I am forgetting?

---

### Post by cutterjohn on 2009-03-25
> **Ascendaeus said:**
> I too love Morrowind very much and the only obstacle is the fact that it needs a cd to playIf you look hard enough you CAN fix that problem.

Anyways, if you love morrowind so ----ing much, go google Morrwind Graphics Extender and get a Windows install going on your machine and use MGE.  (I say windows, as I don't believe that it will be able to run under linux easily.  The GUI is written in .NET 2.0 IIRC (maybe 3.0 now), although it MAY work if you configure it under a windows install then copy the whole thing over to the linux partition as the real parts of it just use some .dlls to hook into DirectX 3D calls, so AFAIK .net isn't actually needed once it's configured and running.

Oh yeah, MGE is on sourceforge now, but I don't have the link handy.

Also not at all sure if things that do memory patching like Morrowind Script Extender (MWSE) will work either under linux + wine.  (Personally, I just boot into Windows to play mods and things like this that do weird things.  Also for those recalcitrant games that just won't work under linux + wine and/or exhibit other annoyances when run with wine.)

---

### Post by Ascendaeus on 2009-03-31
Sorry for my indescretion, a am an a-hole. any way gmount does the trick perty good , but i tried to install mge and it said you got no dll files so i got those, installed them and then tried to install mge and BAM!  Failure in every manner of the term. morrowind  now froze on the title screen. Then, i upgraded to intrepid, and now i can't install my video drivers, i changed it all to 180 or whatnot and it didn't do anything (nvidia 9600) so now i can't even do zsnes or halo! or desktop anesthetics, damn i suck at this

---

### Post by Progressive on 2009-03-31
```
sudo apt-get remove nvidia* --purge
```

Then re-install your drivers.

I believe MGE requires .NET 2.0

```
wget http://kegel.com/wine/winetricks
sh winetricks corefonts dotnet20 
```

People seem to have problems with MGE though, so don't be surprised if it doesn't work. You already mentioned dlls, but double check that you have the proper directx dlls, since it requires directx 9 and WINE doesn't always perfectly execute dx9 code. I think the dll is d3dx9_30.dll

---

### Post by Ascendaeus on 2009-12-25
WE'RE fasing a MOUNTAIN!. I have been playin the *?@$&++% out of morrowind for a whouayull, (like  3,.. or 4 years on XBOX) on pc for almost a year or something, and had it almosat worikn on wine one time when i didn't have )^&!window!@$( eg. plural__ now ive bean on morowind for a while but now the new mge brakes the phukyynm' GAME! and all the old versions have for some reason stopped rednering distant                                                   land!!!!                                                                                                                 if the d3.d8.dll file is in morroWind+=+morrOwind doesn't work, if i pull it out everything works fine but MGE Does'nt work.                                                                                                                                          !any! (even diferent versions of MorrowindMGE 3.8.0) Different versions of MGE RUN FINE other  Than the NEWEST OnE {3.8dot duh dah svn. or SVN. nonsense} Will Run with morrowind .except for distand lant. even the other 3.8 that ALSo replaces the dll. dot 8 file with something that looks exactly the same but doesn't make morrowind not work....        {multiple long winded sighs} BUT NO OTHER VERSIonS Will any Longer ProducE DIstANT LaNd.                                                                                                                                                                                                                      it aitn all cake in windowland so,...                                                                                                                            know that.

---

### Post by Ascendaeus on 2009-12-25
hey man. ive got a windows install now but i had to pay hellaz for it and it took a long time had my pc for a very long time before i ever got windows workin' why the K()# do you think i don't know that you can dowload **** with google windows didn't like my motherbored.

---

### Post by Ascendaeus on 2009-12-25
uhhmmm i really do need help though for real like is that a problem for me to ask windows problems here i mean, i do need help with morrowind distant land in older mge versions and or  d3.d8.dll ,.... FiX .., . ,. ,.. i mean what i don't knonw ...... is it wrong for me to ask you guys about problem'sm ime having with tryin'n to run A COMMU?NITY MODDED AND ENHEANCED GAME in }}}   !!! devil windeauxz....,.,. ? idk you decide

---

### Post by VitalHowl on 2012-01-30
> **Progressive said:**
> Morrowind has worked for me for a long time as long as I was using proprietary drivers.

If you actually had an official morrowind cd then it would be easy. Since you mention azureus, I am assuming you don't. If that is the case, and you have no blank cds, it can still work without downloading anything special. 

You need to do the following things

make a directory called /mnt/iso

```
sudo mkdir /mnt/iso
```then you need to mount the iso. If your iso is called morrowind.iso and it is in your home directory, type this:

```
sudo mount -o loop ~/morrowind.iso /mnt/iso

```otherwise, just change &quot;~/morrowind.iso&quot; to whatever directory and file it is. Every time your computer restarts, it will unmount and in order to play you will have to mount the iso again using this command. 

Lastly, go into the WINE configuration. If you can't find it in your applications menu, then type:

```
winecfg
```Then click on the drives tab and make sure it detects /mnt/iso as E drive or whatever.

cheers

   Thank you very much, Progressive. I've been struggling trough hours and, as I found your post, in some minutes I could start playing. You sincerely know your facts.

---

