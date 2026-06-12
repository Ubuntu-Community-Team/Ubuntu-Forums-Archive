---
title: "Dual boot 32 and 64-bit Ubuntu"
date: 2009-03-09
forum: x86 64-bit Users
---

### Post by becho on 2009-03-09
This may seem like a really dumb question to some but since i have been having numerous issues trying to run Wine i will give it a shot. I have been using 8.10 64-bit for about 2 weeks now and i love it. I am still dual-booting to a second HDD to run XP 32-bit since i can't get certain games that are supposed to work with Wine to work with 64-bit 8.10.

I was wondering since my 1st. HDD is a 250GB drive, is it possible to run 8.10 64-bit on half the drive and have 32-bit 8.10 on the other half. Will Grub take care of it automatically or what must i do to have the Grub menu list both 32 and 64-bit Ubuntu. I will still keep my 2nd HDD with XP 32-bit untouched. I know the obvious answer is to just run 32-bit Ubuntu but i have all the hardware to run 64-bit including 8GB of ram. My ultimate goal is just to rid myself of windows and run Linux but i can't because of the stoopid games.

The games i speak of are native 32-bit with no 64-bit versions, CSS,DODS,Quake 4.

---

### Post by oldos2er on 2009-03-09
Quake4 runs just fine under 64-bit Ubuntu, no Wine needed. You just need [ftp://ftp.idsoftware.com/idstuff/quake4/linux/quake4-linux-1.4.2.x86.run](ftp://ftp.idsoftware.com/idstuff/quake4/linux/quake4-linux-1.4.2.x86.run). Don't know about the other games.

---

### Post by 3Miro on 2009-03-10
I run Civilization and Oblivion and both are 32-bit game on 64-bit Linux. What I have noticed is that if wine handles the game in 32-bit ti would do it in 64-bit, make little to no difference.

I was dual-booting 32-64 kubuntu using the 32 for games and regular work, but I don't see the point anymore.

If your game doesn't work under wine, you might have to keep XP around.

---

### Post by gdbutcher on 2009-03-11
Becho, I just wanted to elaborate on oldos2er reply. I've run Quake 4 on 64 bit myself before. Try these instructions for installation of quake 4:

1. Download the Quake 4 Installer here: [http://zerowing.idsoftware.com:6969/torrents/e5959385dac81ab9ae74062e061c6fe7bbffb2a0.torrent]("http://zerowing.idsoftware.com:6969/torrents/e5959385dac81ab9ae74062e061c6fe7bbffb2a0.torrent")Save it to your Desktop.

2. Put your Quake 4 DVD into the drive, open a terminal, input the following lines changing "fred" for your own username:

```
mkdir /home/fred/quake4
mkdir /home/fred/quake4/q4base
cp /cdrom/Setup/Data/q4base/*.pk4 /home/fred/quake4/q4base 
```

3.Once the file: quake4-linux-1.4.2.x86.run has finished downloading copy and paste this into the terminal:

```
cd ~/Desktop
sudo chmod +x quake4-linux-1.4.2.x86.run
```

Then this, to start the installer:

```
sudo ./quake4-linux-1.4.2.x86.run
```

4. Follow the instructions and after being asked several questions you will be asked for your installation path. Enter your installation path as **/home/fred/quake4** but again, as before, replace 'Fred' with your own username. Don't change the binary path, keep the default: /usr/local/bin. 

Once installation is complete follow these final steps before playing:

5. To change default language from spanish to english. Copy and paste this into the terminal:

```
 sudo gedit ~/.quake4/q4base/Quake4Config.cfg 
```

Press 'ctrl' and 'f' together, and type in the word 'spanish' in the search for box. it should find the line: seta sys_lang "spanish" change "spanish" to "english" then save the file and close it down

6. and finally...  Go back into the terminal and type the following ( again replace 'fred' with your own username):-

```
sudo chown -hR fred: /home/fred/quake4
```

and your done. you should be ready to play. Hope this works out for you!!

---

### Post by Yellow Pasque on 2009-03-12
As others have mentioned, there would be no point in using 32-bit Ubuntu just for WINE. 32-bit programs like WINE run fine in 64-bit Linux.

WINE has two branches - stable and development. If you haven't already, I'd recommend using WINE's repository to get the development version if you're using WINE for gaming. (The Ubuntu repo only offers the stable branch version).
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by stchman on 2009-03-12
I recommend for games who play Windows games to dual boot.  The openGL games run very well under WINE as the video card drivers have a full openGL ICD.  I find the DirecX stuff to be too hit or miss.

DirecX is a Microsoft proprietary API and WINE does the best job they can to emulate it.

---

