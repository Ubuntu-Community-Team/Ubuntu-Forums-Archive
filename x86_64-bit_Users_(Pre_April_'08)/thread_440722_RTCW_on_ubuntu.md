---
title: "RTCW on ubuntu"
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by nzadLithium on 2007-05-11
Hey I'm trying to get rtcw to go on ubuntu x86_64. The game is supposed to be similar installation as quake3. The game is** return to castle wolfenstein not wolfenstein: enemy-territory.** I ran the installer and got

[COLOR="RoyalBlue"]./setup.sh: 20: source: not found
This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
Fatal error, no tech support email configured in this setup
The setup program seems to have failed on x86_64/glibc-2.0

Fatal error, no tech support email configured in this setup
The program returned an error code (1)[/COLOR]

so i took looked it up in google and pretty much everywhere said that i should do 
[COLOR="DarkRed"]linux32 sh wolf-linux-1.33.x86.run[/COLOR] (i know this is an out of date version but its the version i like playing)

then i get a similar error just slightly shorter

i went onto id softwares website in linux area and they say if that doesnt work then i should do --force
so i did  [COLOR="DarkRed"]sudo sh wolf-linux-1.33.x86.run --force [/COLOR]

this gave exactly the same output but when i look i now have a folder called wolf-setup
in this folder are all the game files in these directories:

```
bin
       x86
               wolf.x86
               wolfded.x86
               wolfsp.x86
               wolfmp
               wolfsp
docs
        (etc...)
        (cant be bothered writin it all out coz its only documentations)
main
        scripts
                    translation.cfg
       cgame.mp.i386.so
       cgamei386.so
       mp_bin.pk3
       mp_pak3.pk3
       mp_pak4.pk3
       qagame.mp.i386.so
       qagamei386.do
       rotate.cfg
       sp_pak3.pk3
       ui.mp.i386.so
       uii386.so
pb
         htm
                  (bunch of htm files)
        pbag.so
        pbcl.so
        pb_eula.txt
        pbsv.so
setup.data
        bin
               Linux
                         x86
                                 glibc-2.1
                                 plugins
                                 setup
               (bunch of other os)
      locale
              (folders containing dif language settings)
       config.sh
       postinstall.sh
       setup.glade
       setup.xml
       splash.xpm
changes
install
openurl.sh
quickstart
setup.sh
wolfmp.xpm
wolfsp.xpm
```

i tried running wolf.x86 and it appeared to do nothing so i ran it in the terminal using ./wolf.x86
then i get this output:

[COLOR="Sienna"]Wolf 1.33-MP linux-i386 Jun 11 2002
----- FS_Startup -----
Current search path:
/root/.wolf/main
/home/cmaster/setups/wolf/wolf-setup/bin/x86/main

----------------------
0 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg - I am missing essential files - verify your installation?[/COLOR]

im pretty sure this is because the directory structure isn't right bt i have no clue where all the files go. 

I am hoping someone here can tell me where all the files should be. Or better yet tell me how to get the installer to work properly.

thx

Lithium

(sry for the post bein so long)

---

### Post by nzadLithium on 2007-05-11
well i guy on wolfenstein called bad command gave me a directory tree of his wolf.

For anybody who cares to install return to castle wolfenstein on 64bit all you have to do is download the file from [ftp://ftp.idsoftware.com/idstuff/wolf/linux/old](ftp://ftp.idsoftware.com/idstuff/wolf/linux/old) for older versions
if you want the latest version then [ftp://ftp.idsoftware.com/idstuff/wolf/linux](ftp://ftp.idsoftware.com/idstuff/wolf/linux)
then you open up terminal and type sh wolf-linux-(version).x86.run --force

login as root (if you know another way to do this without login as root go for it but im a noob so i dont have any idea)
then you copy the wolf-setup directory that is created to /usr/local/games
then go into the wolf directory and copy the files from wolf-setup/bin/x86 into wolf-setup.


to run it type cd /usr/local/games/wolf-setup
then to run multiplayer type ./wolf.x86
to run singleplayer ./wolfsp.x86

I'm really laggy at the moment though so i have to find out why that is. (takes me like 10 mins to load the menu)
and i also have the same problem i have with wolfet of when im running the game the screen goes mini i think this might have something to do with the fact i gots dual screens.

once i find how to fix this other stuff ill post it on here also

lithium

---

### Post by nzadLithium on 2007-05-12
ok so to fix the problem of this game or any number of other games going mini.
goto system preferences screenresolution have a look at the resolution. If you think your game can handle that resolution then leave it. If you dont think it can then turn it down.

Then go into your game settings and change the resolution in game to the same resolution as the one you have for ubuntu. Now the game will be fullscreen instead of mini. This also fixes the same problem that occurs with enemy-territory.

My lag was caused because i was using beryl themes manager. when i removed it and went back to the default that came with ubuntu the game went so fast it was insane! 1337 ubuntu! usually on windows on this same pc takes like 5 seconds for game to close. I clicked close on linux and boom it was gone. It was instantaneous. 

Also you will probably need to fix the sound thing:
[http://ubuntuforums.org/showthread.php?t=5246](http://ubuntuforums.org/showthread.php?t=5246)
that thread tells you how to fix under troubleshooting.
just make sure u change et.x86 to wolf.x86 or if its single player your trying to run change it to wolfsp.x86

---

