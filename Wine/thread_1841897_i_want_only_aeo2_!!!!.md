---
title: "i want only aeo2 !!!!"
date: 2011-09-10
forum: Wine
---

### Post by shubham1 on 2011-09-10
i have tried many many ubuntu software games but now i want only age of empires i installed it using wine tricks but it is not working please help i dont want to install it again its big in size i want aeo2 only!!!!!!!!!
i have freedom figthers and linux that cam from windows can  run them i dont installed from wine or play on linuxi

---

### Post by howefield on 2011-09-10
Thread moved to the "*Wine*" forum.

---

### Post by shubham1 on 2011-09-10
> **howefield said:**
> Thread moved to the "*Wine*" forum.
its right the problem i want is i want to instakll aeo2 its gaming in wine nobody might see it

---

### Post by Dlambert on 2011-09-10
> **Workaround for sound, graphics, and**
 by  Charles Wise on Thursday July 7th 2011, 8:23
 After a lot of troubleshooting and testing, I finally got Age of Empires  II to run pretty successfully on my Samsung laptop with Ubuntu 11.04  using Wine 1.2.2. I encountered and solved the following issues: 

1) No game CD detected. 
2) No sound in game. 
3) Choppy scrolling 


1) No game CD detected 
Despite carefully installing AOE2 through PlayOnLinux from the CD,  this error kept coming up, even after configuring Wine to look in the  CD-ROM drive to run the game. Eventually I ditched PlayOnLinux and just  installed the game directly through Wine using the command-line, which  overcomes the "executable-bit" problem of Wine trying to run a read-only  executable on a disk. 

a) With the AOE2 CD inserted, open Terminal and navigate to the  CD-ROM drive (the directory is called AOE2 and is located in  /media/AOE2). Run the installer by typing "wine aoesetup.exe." The  installer will start in the Wine Program Loader. 

b) Click through all the steps to install the game (it's not a bad  idea to make a desktop icon either so that you don't have to launch the  game through the command-line each time). When the install is finished,  do not start playing immediately but exit the game installer. 

c) Open Configure Wine by typing "winecfg" at the command-line.  First, add the program "empires2.exe" by clicking "Add Application" and  browsing to the program location (Program Files -> Microsoft Games  -> Age of Empires II -> empires2.exe).  

d) Set the Windows version to Windows XP, then click on the "Drives"  tab. Click "Autodetect" to see if your CD-ROM drive will automatically  be detected. If not, then click "Add" and specify the path as  /media/AOE2, which is where the CD is inserted. Click "Apply" and then  click "OK." 

e) Test the CD-ROM recognition by opening Age of Empires, creating a  new user, and then click on "Single Player." The game should allow you  to choose from the single-player game options now. 


2) No sound in the game 
Another problem that affects Age of Empires in Ubuntu is that Wine  doesn't do a very good job of utilizing PulseAudio, the default sound  server for Ubuntu. Before opening the game, go to the command-line and  type in "killall pulseaudio" before starting. Make sure you stop running  any audio programs as well before opening the game. 

a) Once in the game (meaning playing on the map), there may still be  no sound. No to worry. Just open the command-line again and type in the  "killall pulseaudio" command to get your in-game sound. The sound will  reboot and start playing from the beginning. 


3) Choppy scrolling and annoying desktop intrusions 
You may have noticed that the in-game performance is a bit weak.  This can be fixed by resizing the graphics inside the game itself and by  disabling "Desktop Effects" in the CompizConfig Settings Manager under  System Settings. If you do not have this manager installed, it is highly  recommended you do so, so that you can make edits to the Compiz  settings.  

a) Open the manager, select effects, and get rid of all effects  except for "Window Decoration." This should help eliminate flickering in  the game. 

b) In the game, select the Options button, and resize the screen to  the standard 800x600 output, even if your screen is not this size. The  performance will improve dramatically using this resolution, especially  the scrolling. Though it may not be the best graphics display ever, the  benefits outweigh the costs in my opinion. 

After all this, you should have a decently-functioning version of Age of Empires in Wine on Ubuntu.

 [[post new]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=comment&sAction=add&sReturnTo=http%3A%2F%2Fappdb.winehq.org%2FobjectManager.php%3FsClass%3Dversion%26amp%3BiId%3D147&sTitle=Post+new+comment&iVersionId=147")]   [[reply to this]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=comment&sAction=add&sReturnTo=http%3A%2F%2Fappdb.winehq.org%2FobjectManager.php%3FsClass%3Dversion%26amp%3BiId%3D147&sTitle=Post+new+comment&iVersionId=147&iThread=70535")]                    [IMG]http://appdb.winehq.org/images/blank.gif[/IMG]   
   [IMG]http://appdb.winehq.org/images/blank.gif[/IMG]                   **DirectDraw problem and multiplayer problem**
 by  Defiance on Wednesday March 2nd 2011, 9:51
 Hello. I have tried run AOE2 wine (which I have installed with apt-get)  and I was receiving the message  that could I cannot connect (cannot  join) to the game in multiplayer. I have tried the tip of DLLs in the  page of game in wineappdb too. 

So, ok. I recompile the wine and after that the game not runs, and I  received the message  "Could not initialize Graphics System. Make sure  that your video card and driver are compatible with DirecDraw". 

I think my tip will also work in another distribution linux and  another version of wine (I was used the version 1.3.14). So, make this: 

For debian users, first make this: 

sudo apt-get install libfreetype6-dev 
sudo apt-get install fontforge 
sudo apt-get install ftgl-dev glutg3-dev freeglut3-dev ftgl-dev 
sudo apt-get install xorg-dev 
sudo apt-get install gcc flex bison libc6-i386 libc6-dev-i386  

So, I was make this steps for solve my problem: 

1- Uninstall the wine 

2- Execute the follow commands: 

cd /usr/lib32 
sudo ln -s libX11.so.6 libX11.so 
sudo ln -s libXext.so.6 libXext.so 
sudo ln -s libfreetype.so.6 libfreetype.so 
sudo ln -s libz.so.1 libz.so  

2- Download the source of the wine. 

3- Extract the source with: tar jxf wine-version.tar.bz2   

4- Enter in the source directory and execute the command: 
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32  -Wl,-rpath,/usr/lib32" ./configure --enable-opengl --disable-trace  --disable-debug --with-x 

5- Execute the command: 

make depend && make all && sudo make install 

6- Ok, now wine it's finished to be installed. So, place the DLLs of  winepage (the first tip of this page) in Wine's windows/system32  directory. Then, start winecfg and add dll overrides (native, builtin)  for the following DLLs: dplayx, dpnet, dpnhpast and dpwsockx. 

It's this ! After this steps my wine runs AoE2 in multiplayer :D 

(and sorry for my english too :)


Hope this helps

---

### Post by Dlambert on 2011-09-10
[Try PlayOnLinux, http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")

---

### Post by shubham1 on 2011-09-11
> **Dlambert said:**
> [Try PlayOnLinux, http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")
i have playonlinux i upgraded it then to it syas to upgrade and do nohting

---

### Post by shubham1 on 2011-09-11
error:
wine: cannot find L"C:\\windows\\system32\\aoesetup.exe"

---

### Post by shubham1 on 2011-09-12
what to do after

---

### Post by Dlambert on 2011-09-12
The aoe setup file is not in the system 32 folder. Change it to the path of the game

---

### Post by Dlambert on 2011-09-12
EXAMPLE : wine /home/dlambert/games/aoe.exe

---

### Post by Dlambert on 2011-09-12
> **shubham1 said:**
> i have playonlinux i upgraded it then to it sayss to upgrade and do nothing


```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_natty.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```

YOU HAVE TO ADD THE REPO, OR IT WONT UPDATE!!!

---

### Post by shubham1 on 2011-09-13
> **Dlambert said:**
> EXAMPLE : wine /home/dlambert/games/aoe.exe
it gives error loading file i have such file x y and z which is the right and they are .exe.bak

---

### Post by shubham1 on 2011-09-13
> **Dlambert said:**
> ```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_natty.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```

YOU HAVE TO ADD THE REPO, OR IT WONT UPDATE!!!
done it again says the same

---

### Post by Dlambert on 2011-09-15
Hm, why not just go to the file in nautilus and run it using wine?

---

### Post by shubham1 on 2011-09-16
> **Dlambert said:**
> Hm, why not just go to the file in nautilus and run it using wine?
i did it ealir it gives error and now after using  the terminal he files are missing the drive is only not there

---

### Post by Dlambert on 2011-09-16
Bad media? Direct from cd?

---

### Post by shubham1 on 2011-09-17
> **Dlambert said:**
> Bad media? Direct from cd?
i cant get what you are trying to say

---

### Post by Dlambert on 2011-09-17
Are you trying to install directly from the cd?

---

### Post by shubham1 on 2011-09-18
> **Dlambert said:**
> Are you trying to install directly from the cd?
i have no cd i installed from the web

---

