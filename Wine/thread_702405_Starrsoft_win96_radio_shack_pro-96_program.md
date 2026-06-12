---
title: "Starrsoft win96 radio shack pro-96 program"
date: 2008-02-20
forum: Wine
---

### Post by kg4tah on 2008-02-20
I have a Radio Shack pro-96 digital trunking hand held scanner that can be programmed via starrsoft win96.  When I attempt to run the program under wine I receive the following error message:

Cannot find import; DLL may be missing, corrupt, or wrong version File MFC42.dll

I downloaded the dll file and placed in the win96 program folder as well as the system32 folder.  By placing the file in each folder one at a time I received another error.

I need some help getting this program to work.  It is a free download for anyone wishing to give it a try and help me get it working.  Here is the url for the program [http://www.starrsoft.com/software/Win96/](http://www.starrsoft.com/software/Win96/)

---

### Post by kg4tah on 2008-02-22
I still have not been able to get the program to run...... does anyone know of a linux program that would allow the scanner to be programmed via PC?

---

### Post by AE6QE on 2008-03-23
I am having the same issues here.  I can even register the program, but then I have the error:

Error:  Access violation at 0x008F31F2 (tried to read from 0x00002074), program terminated.

If I change the wine settings from WinXP or Win2K to Win98, the program doesn't error, but never loads.

Rickey

---

### Post by kg4tah on 2008-04-22
I installed vmware-server and created a virtual win xp environment.  I can run the program fine now however it seems my com ports will not communicate under the xp environment. I can't read any data from the radio or send data to it. Anyone want to give this a try and see if you can help find us a solution??? :-)

---

### Post by N467RX on 2008-05-03
I'm getting the same error except that I'm running it (well, trying to run it) using Mac OSX 10.4 under CrossOver (I believe it's the Mac equivalent to Wine). Same error of the "cannot find import" with MFC42.dll. Before I was running the trial on a virtualized Windows environment, but that just consumes too many resources.

I'll give it a try checking where is the MFC42.dll in a normal Windows XP system and then I will copy the MFC42 from there, instead of a downloaded one.

---

