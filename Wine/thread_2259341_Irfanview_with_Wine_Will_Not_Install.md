---
title: "Irfanview with Wine Will Not Install"
date: 2015-01-03
forum: Wine
---

### Post by leegold on 2015-01-03
Hi,

Using Ubuntu Studio 14.04.1 32 bit. I download the Irfanview exe and right click to install with Wine. Nothing happens. No install window opens - nothing, hard drive seems to crank a while then stops.

Any help appreciated.

Thanks

Edit: Well I used the zip files for Irfanview (instead of trying to install via exe files) and Irfanview and the plugins seem to work with Wine when you do it that way...

---

### Post by yancek on 2015-01-03
Never heard of that software but googling it took me to the site below with 5 steps to get it going.  Do you have a windows installation to get the file referred to in step 2?

[http://www.boekhoff.info/?pid=linux&tip=install-irfan-view-on-linux](http://www.boekhoff.info/?pid=linux&tip=install-irfan-view-on-linux)

---

### Post by yoshii on 2015-02-26
I had a similar problem several months ago and I had to email the software author to get the appropriate DLL files to allow the EXE's to work, and then everything installed OK.

---

### Post by ar22 on 2015-06-11
I managed to start it up when I did the following:

1. I installed wine on my Ubuntu
2. I copied mfc42.dll from my windows/system32/ folder on other computer into my Ubuntu Deskotp folder
3. I used "winetricks mfc42" command in a folder where mfc42.dll file was stored
4. I copied IrfanView installation folder (with all files in it) from my windows based computer to my Ubuntu laptop into the following folder path:

/home/artur/.wine/drive_c/Program Files/

5. I right clicked the IrfanView.exe and started it with Wine and it worked out.

I tried installing it on Ubuntu from installation archive but I was getting errors related to *.dll files.

good luck

---

### Post by Bucky Ball on 2015-06-11
*Thread moved to **Wine**.*

---

