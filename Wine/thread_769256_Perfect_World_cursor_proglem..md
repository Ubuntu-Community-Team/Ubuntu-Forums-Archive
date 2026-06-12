---
title: "Perfect World cursor proglem."
date: 2008-04-26
forum: Wine
---

### Post by crazymanjared on 2008-04-26
Hi i've gotten wine to work with a few things now and i want to play perfect world, but the cursor wont show up, i found a patch to make it show up, but i have absolutely no idea how to use the patch, heres a link to it.

[http://bugs.winehq.org/show_bug.cgi?id=10708](http://bugs.winehq.org/show_bug.cgi?id=10708)

Also, i can login and stuff without the mouse and get to the loading screen, but at the loading screen it takes about 3 or 4 minutes and then crashes.

---

### Post by happyhamster on 2008-04-26
You'll have to compile wine yourself, which can be quite a hassle.

- First make sure you have the wine repository loaded. Follow the instructions on this page (also, see the post below):
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
(add key, add repo, run "sudo apt-get update").

- Download the wine-source from here (wine-0.9.59.tar.bz2):
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)
- Double-click the file to extract it. It will create a folder named wine-0.9.59.

- Download the patch (from your link):
[http://bugs.winehq.org/attachment.cgi?id=12133](http://bugs.winehq.org/attachment.cgi?id=12133)
(Just save it as pw.patch and put it into the wine-0.9.59 folder.)

- Open a terminal and navigate to the wine-0.9.59 folder. Apply the patch:

patch -Np1 < pw.patch

- If all went well, it will say:

patching file dlls/user32/cursoricon.c
patching file dlls/wined3d/drawprim.c
patching file dlls/wined3d/glsl_shader.c
patching file dlls/wined3d/state.c
patching file dlls/wined3d/surface.c
patching file dlls/wined3d/wined3d_private.h
patching file dlls/winex11.drv/mouse.c
patching file include/wine/winuser16.h

- Get the packages you need to be able to compile wine (can be quite a lot of software):

sudo apt-get build-dep wine

- For me, that's usually enough, but I've accumulated a lot of packages on my system over time. Also try:

sudo apt-get install libxcomposite-dev gcc-4.2-multilib x-dev libqt3-compat-headers

- Hopefully, you're now ready to compile. From within the wine-0.9.59 folder, run:

./configure

- If it complains about something at the end, it probably means you still have to install some packages first. If there aren't any warnings, proceed with:

make depend && make

- This will take 30~40 minutes, so go get yourself some soup. Tea is good too, but soup is better. Or beer, depending on your age. Anyway, when that's done, make sure the previous version of wine is uninstalled:

sudo apt-get remove wine

- Then double-check to make sure:

wine --version

- If it complains that wine isn't installed, everything's fine. Now you can install the patched wine. First install checkinstall:

sudo apt-get install checkinstall

- Then run it to install wine and also create a .deb package you can use later. Still from within the wine-0.9.59 folder:

sudo checkinstall

- It will ask a few questions:
--- default package docs : no
--- description: patched wine-0.9.59. Use a blank line to end this part.
--- press enter.
(Note that you have to install/uninstall wine as root (by using sudo). Don't run anything else wine-related as root though.)

- It will take a minute or so to install. When all's done, there should be a .deb file in the wine-0.9.59 folder. You can use that file to quickly re-install this patched version of wine in the future, without having to compile again (so move it somewhere safe). Lastly, run:

wineprefixcreate

- That command will update wine to get the new version to work with the previously installed programs. Also, should you want to get rid of this patched wine version in the future, you can uninstall it using:

sudo dpkg -r wine



Good luck, and let us know should you run into trouble.

---

### Post by happyhamster on 2008-04-26
I just noticed the wine page I linked to: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

, only talks about Ubuntu Hardy Heron now. I would say: Gutsy users, unite! Let us smite the evil Herons and claim our rightful place as the pinnacle of Ubuntu-ness/dom/stuff.

Or just use "gutsy" instead of "hardy" in the line:

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

---

### Post by crazymanjared on 2008-04-27
Error at end of compile: 

ernel32 -lntdll  -lXext -lX11  ../../libs/port/libwine_port.a  
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/jared/Documents/wine-0.9.59/dlls'
make: *** [dlls] Error 2

---

### Post by happyhamster on 2008-04-27
- Hmm, likely still missing packages. Try the script on this page:

[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

- Download it, and run it like:

sudo sh gutsy.sh

- In case it installed additional packages (X related preferrably), re-compile:

./configure

make clean && make

---

### Post by crazymanjared on 2008-04-27
Compile went just fine, now when i do sudo checkinstall and press enter, it gives an error.


Installing with make install...

========================= Installation results ===========================
make[1]: Entering directory `/home/jared/Documents/wine-0.9.59/libs'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/libs/port'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/libs/wine'
(GIT_DIR=../../.git git describe HEAD 2>/dev/null || echo "wine-0.9.59") | sed -e 's/\(.*\)/const char wine_build[] = "\1";/' >version-stamp || (rm -f version-stamp && exit 1)
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/libs/wine'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/libs/wpp'
make[1]: Leaving directory `/home/jared/Documents/wine-0.9.59/libs'
make[1]: Entering directory `/home/jared/Documents/wine-0.9.59/tools'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/tools/widl'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/tools/winebuild'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/tools/winedump'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/tools/winegcc'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/tools/wmc'
make[2]: Entering directory `/home/jared/Documents/wine-0.9.59/tools/wrc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jared/Documents/wine-0.9.59/tools/wrc'
make[1]: Leaving directory `/home/jared/Documents/wine-0.9.59/tools'
make[1]: Entering directory `/home/jared/Documents/wine-0.9.59/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jared/Documents/wine-0.9.59/include'
make[1]: Entering directory `/home/jared/Documents/wine-0.9.59/include'
../tools/mkinstalldirs -m 755 /usr/local/include/wine/windows/ddk
mkdir /usr/local/include/wine
chmod 755 /usr/local/include/wine
chmod: changing permissions of `/usr/local/include/wine': No such file or directory
make[1]: *** [/usr/local/include/wine/windows/ddk] Error 1
make[1]: Leaving directory `/home/jared/Documents/wine-0.9.59/include'
make: *** [include/__install__] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by happyhamster on 2008-04-27
Ok, before trying to re-install/re-compile, try running it from the wine-0.9.59 folder. There should be a script called wine there. To run it use:

./wine /path/to/program.exe

(something close to ./wine "$HOME/.wine/drive_c/Program Files/program folder name/program.exe"

If that works, the compilation did indeed succeed. You should be able to install it with:

sudo make install

But if you don't mind sticking some more time in it, I would just get rid of the wine-0.9.59 folder and re-compile from scratch (extract the source, copy the patch file into that folder, apply patch, ./configure. make depend && make, sudo checkinstall).

BTW, if someone knows of a way to do this quicker, please share.

---

### Post by crazymanjared on 2008-04-27
I completely redid everything, compile went fine but i'm still getting the error when i do sudo makeinstall. I really didnt understand the first part of your last post...i'm a complete noob when it comes to linux if you haven't noticed. :p

---

### Post by happyhamster on 2008-04-27
What I meant was that you don't have to install wine, you can run it directly from the wine-0.9.59 folder. It's a good way to test if wine itself works.

- First navigate to the wine-0.9.59 folder, then run wine from there:

./wine 

- However, you also have to add the path to the program you want to run: those programs are (likely) installed in the .wine folder in your home dir. When using the nautilus file-manager (choose Places-->Home Folder in your main menu), press ctrl-h to be able to see hidden files. There should be a .wine folder (folders starting with a dot are hidden folders). Just search that .wine folder until you find the program you want to run (some .exe file). (The path is probably /home/your_username/.wine/drive_c/Program Files/some_folder_name/)

- To be able to run it from a terminal, you have to put that entire path between quotes, for example:

./wine "/home/your_username/.wine/drive_c/Program Files/some_folder_name/program.exe"

> i'm a complete noob when it comes to linux if you haven't noticed. Then keep in mind that compiling stuff can be one of the hardest things to do on a linux box. (I wish I knew more about it myself actually :) )

---

### Post by happyhamster on 2008-04-27
BTW, which ubuntu version are you using precisely? And is it a regular or a 64 bits version?

---

### Post by crazymanjared on 2008-04-27
I'm running 32 bit hardy.

---

### Post by crazymanjared on 2008-04-27
I'm using hardy, and when i do ./wine, it comes up with the thing its supposed to when wine is installed.

---

### Post by happyhamster on 2008-04-27
- What do you get after (from within the wine 0.9.59 folder):

sudo mkdir /usr/local/include/wine

sudo chmod 755 /usr/local/include/wine


- If it doesn't complain, try:

sudo checkinstall

---

### Post by crazymanjared on 2008-04-27
Those 2 commands didnt say anything, and i tried checkinstall and it gave me the same error again.

---

### Post by happyhamster on 2008-04-27
Ok, I just tried to compile wine on my hardy heron test-pc, and I get the same errors (it compiles fine under gutsy). It's some sort of permission problem I guess, because you can manually create the folders, and then installation will proceed ... and immediately abort for the next non-existent folder. And manually creating a few 100(?) folders without any guarantee that it'll work in the end is not an option.

What I'm trying now is (this appears to work on hardy, but it won't on gutsy at the moment):

- Get rid of the previous wine-0.9.59 folder (but make sure you still have a copy of the patch file around).

- To prepare, you need:

sudo apt-get install dpkg-dev fakeroot

- Get the wine source like this (don't use "sudo" on this one):

apt-get source wine

- You don't have to extract anything, because, among other things, it will create an updated wine-0.9.59 folder for you. Copy your patch file into it, and apply the patch:

patch -Np1 < pw.patch

- Run:

dpkg-buildpackage -rfakeroot

- this will take ~ 30 minutes again, but it will also continue with installation.

---

### Post by crazymanjared on 2008-04-27
When i do apt-get source wine it gives me this error "E: Unable to find a source package for wine"
And I've def. put the wine repositories or whatever they are in the file i was supposed to.

---

### Post by happyhamster on 2008-04-27
> **crazymanjared said:**
> When i do apt-get source wine it gives me this error "E: Unable to find a source package for wine"
And I've def. put the wine repositories or whatever they are in the file i was supposed to.
Go to System-->Administration-->Software Sources-->Third Party Software. 

There should be 2 entries for Hardy, both of them should be ticked. If not select both. If there are any other wine entries (for previous ubuntu versions, get rid of them) Then choose close and reload and try to run "apt-get source again". Also, the server is slow at the moment, so try running that command a few times in a row (let some time pass in between).

The above way worked for me (I think): it created a .deb file which installed fine. There were a lot of complaints and some warnings when the package was being built though.

And when I run wine I get the preloader: Warning: failed to reserve range 00000000-60000000 message (known issue in Hardy Heron).

---

### Post by crazymanjared on 2008-04-27
jared@jared-desktop:~/wine$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package wine
dpkg-buildpackage: source version 0.9.60~winehq0~ubuntu~8.04-1ubuntu1
dpkg-buildpackage: source changed by Scott Ritchie <scottritchie@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5.0.0) libgif-dev | libungif4-dev libjack0.100.0-dev docbook-utils docbook-xsl docbook-to-man prelink libhal-storage-dev
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)

---

### Post by happyhamster on 2008-04-27
- Try running:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get build-dep wine

- then 

dpkg-buildpackage -rfakeroot

---

### Post by crazymanjared on 2008-04-27
I give up...I really appreciate all your help and I'm sorry for wasting your time...this is just ridiculous.

---

### Post by happyhamster on 2008-04-27
Crap. What did you get this time?

---

### Post by crazymanjared on 2008-04-27
Just a bunch of errors...I think I'm gonna go back to xp...if i have to do this with every game, I'll go insane...and i play a lot of games, I REALLY REALLY do appreciate your help though.

---

### Post by happyhamster on 2008-04-27
Are you sure it didn't create the packages regardless of the errors? The .deb files will be in the parent folder of the one you were running from.

---

### Post by crazymanjared on 2008-04-27
OMG I think it might have actually worked.


IT WORKEEEEEEEEEEEEEEEEEEEEEEEEEED!

THanks so much.


ROFL, now it crashes while loading into the world.

Heres the error

err:seh:setup_exception_record stack overflow 1744 bytes in thread 0037 eip 006f3005 esp 7bdefc60 stack 0x7bdef000-0x7bdf0000-0x7bf00000
err:ntdll:RtlpWaitForCriticalSection section 0x2a52a1c "?" wait timed out in thread 0036, blocked by 0037, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e912d24 "d3d8_main.c: d3d8_cs" wait timed out in thread 0026, blocked by 0037, retrying (60 sec)
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

---

### Post by happyhamster on 2008-04-28
Try as follows: open a text editor and create an empty text file. Copy&paste:

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"RenderTargetLockMode"="textex"

- Save the file as "perfectworld.reg". Next, import that file into the wine registry, with the command:

wine regedit perfectworld.reg

(You'll have to run that command from the folder where you saved perfectworld.reg, of course).

Good luck.


Source: [http://bugs.winehq.org/show_bug.cgi?id=11492#c37](http://bugs.winehq.org/show_bug.cgi?id=11492#c37)

---

### Post by BlewoW on 2008-05-05
i too tryed to run Perfect World on ubuntu, i was successful tho i experienced same problems of crashing, for some reason, lowering the display settings too much or increasing it too much would crash it, i tryed clicking recommanded (from the display option in the patcher) and then disabling everything but "Shadow" and it worked, i could play it but the problem is i cant get that same graphics like from windows and the icons are screwed up, see for ur self, and for the cursor problem, i just turn on A,D turning option on from the option menu in-game and hit ALT key and the mouse will show up(as a normal cursor), or use Hardy compiz fusion effect that shows the mouse location, its called "Show Mouse", u can find it in the Compiz fusion setting manager.
its still unplayable on ubuntu....and wats worse is that the installation cannot be done in ubuntu using any kind of Wine(Wine, Cedega, Play on Linux)....none is able to start the installation... :/ its the only only thing keeping me of letting go of windows...more generally game but i only play this game in the mean while...and alot..


Intel 3.2GHz 
Hardy 32bit
Nvidia Geforce 7300GT 512Mb
1GB Ram

---

### Post by trojvirus on 2008-09-29
Are there new updates that can run Perfect World on ubuntu? This game is the only reason why I still have XP on my PC.

---

### Post by XShinigamiXHadrielX on 2008-10-25
Ok ive tried your how-to several times includen formatting and reinstalling ubuntu and im still haven trouble getting PW-International running, here are my system/software specs...Listing all even if it dont matter ^^

WhiteBox:
AMD Athlon x64 +3800 2.0Ghz x2 (Dual Core) Processor
ECS A780GM-A Motherboard
3Gb DDR2 533Mhz RAM (1Gb Shared with integrated Graphics)
80Gb 7200RPM SATA Hard Drive
DVD/CD Burner/Reader
Ultra 69 in 1 Media Card Reader
430W Power Supply
5200RPM CPU Fan
2500RPM System Fan
Integrated 7.1 Sound
Integrated Hybrid HD 3400 Graphics Unit
Avg Download Speed = 200Kb/s

Ubuntu 8.04 Hardy Heron

Wine 0.9.59 Shown on Desktop
Wine 1.1.7  Shown in Terminal

DirectX 9.0c
ATI Accelerated Graphics Driver (Enabled)
--------------------------------------------------------------------------
Now that you know that im going to show you what the terminal showed me when i ran PW-International and the steps i took to that point

S1. Opened Terminal
S2.CD ~/Desktop/PerfectWorldInternational/launcher
S3.wine Launcher.exe

Terminal opened up PW and when i clicked "Start" it went to load screen for about 1 sec just long enofe to see it actualy load on the bar at bottom of window and then at login screen it flickered but i was still able to log in and then select character and enter world.

The cursor did not show or my character in character select screen and no other monsters/npcs/players showed while in game.

I have installed the pw.patch but had to go through the other steps several times so the order of the steps was messed up by the time i ran PW for the first time.

I havent Checked Sound yet since speakers are on the other computer.

I took Perfect World International folder from my Windows XP computer and burnt it onto a DVD with ImgBurn and used that to copy/paste to my desktop on this computer.

My PW-International Settings are at min. with none of the bubbles filled except windowed mode and i have it set to 800x600 and my client version is 24.

And im not sure if this is right but when it asks those questions the #7 one shows i386 and that looks like it would be ment for an Intel setup so if that matters could i get some help with that?

Last but not least what was shown in the terminal window before i exited...

2) from glUseProgramObjectARB @ glsl_shader.c / 3454
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 445
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3454
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 445
fixme:d3d:state_fog Implement table fog for foggy vertex shader
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3454
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 445
fixme:dinput:DllCanUnloadNow (void): stub


So if i could get a step-by-step on how to get PW-International installed and running properly on this system it would be much appreciated.

Here is how to contact me.
1. Email: [email]Beck_Xlll@hotmail.com[/email] (those are L's)
2. Post on these forums the step-by-step (maybe others are in same position as me)
3. Myspace: [http://www.myspace.com/S_M_O_K_Y](http://www.myspace.com/S_M_O_K_Y)

Thank You for the current How-To it has helped me get this far and thats better than nothing. Good Luck to others!

---

### Post by SistemBug on 2009-02-22
[QUOTE=happyhamster;4805950]You'll have to compile wine yourself, which can be quite a hassle.

- Open a terminal and navigate to the wine-0.9.59 folder.

How DO I open the terminal?:(

---

### Post by Found on 2009-04-14
damn...i tried to install PW with Wine that comes from ubuntu intrepid main rep with no patches and stuff.
It installed fine, but when i'm lauching the launcher.exe it just freezes on first "Connecting to server" dialog, that's very strange

---

### Post by Spazmunki13 on 2009-11-11
The Launcher.exe seems to freeze up  at first, you just need to close and reopen a few times and let it sit for a minute or two once it works it'll work fast every other time.

My problem is the same as the OPs the game downloads perfectly but I have no cursor once I click on "Start" in the launcher. (It opens the game but nothing can be clicked because my cursor is non-existant)

I tried going through the process explained above but it didn't seem to work.

Can anyone help?

EDIT: While I was messing around I found out that if you blindly click on the buttons. (Easily down with a window placed above the game window. The mouse clicks ARE picked up. Once you get to the login screen click on the square within the login and voila you have a cursor... not sure how long this lasts so I'll have to check.

---

### Post by tomcat025 on 2009-11-12
> **Spazmunki13 said:**
> The Launcher.exe seems to freeze up  at first, you just need to close and reopen a few times and let it sit for a minute or two once it works it'll work fast every other time.

My problem is the same as the OPs the game downloads perfectly but I have no cursor once I click on "Start" in the launcher. (It opens the game but nothing can be clicked because my cursor is non-existant)

I tried going through the process explained above but it didn't seem to work.

Can anyone help?

EDIT: While I was messing around I found out that if you blindly click on the buttons. (Easily down with a window placed above the game window. The mouse clicks ARE picked up. Once you get to the login screen click on the square within the login and voila you have a cursor... not sure how long this lasts so I'll have to check.

I do have a freeze as well. This, however, is between the time I click the link to start up PWi within wine and it activates.

Cursor? Yes I am also lacking a cursor. Logging in is not an issue as that can be done via enter and the arrow keys. However, changing any game options or clicking anything within game can.

THen there is the wacky icons that look like a crayola box threw up.

I've searched the internet for anything related and have gotten nothing.

The icon issue I can live with. The cursor however is something I need in order to play.

This is all using, I thought, the latest build of wine. IT appears that I was wrong and that I am using ver. 1.0.1

Will post if compiling the newest version helps.

---

