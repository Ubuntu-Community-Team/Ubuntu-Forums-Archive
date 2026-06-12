---
title: "Google Sketchup, Wine, 3D Warehouse"
date: 2011-09-17
forum: Wine
---

### Post by craig_parker on 2011-09-17
Anyone ever get this working?  Is there a tutorial somewhere?  I'm currently running:
Lucid
wine-1.3.26
 (via the commands: 
    add-apt-repository ppa:ubuntu-wine/ppa
    apt-get update
    apt-get install wine1.3
 )
Sketchup 8

When I click on the 3D Warehouse button, my default browser goes to the main warehouse page, and a blank 3D Warehouse window also opens up.  
I hear that getting this blank window to actually function takes "days of tweaking" but cannot for the life of me figure out what the tweaking consists of.
Google isn't helpful so far; I've not found anything to get me over the hump yet.

---

### Post by craig_parker on 2011-09-19
Is this in the wrong forum?

---

### Post by scania_gti on 2011-10-06
3D warehouse show only blank page :)
 Firefox say "Firefox doesn't know how to open this address, because the protocol (skp) isn't associated with any program."
An chromium not work too... :D Google sketchup not work with google chromium :)
When in Sketchup open 3D warehouse - it open warehouse sign page in firefox, but i can't sign!

---

### Post by jjk75 on 2012-04-08
Since this thread was the first on my search list, I figured I will add this after I found a work-around. I had to install IE6 into Wine, namely by typing
winetricks ie6

Worked when using Sketchup 8 and Wine 1.4.

---

### Post by Dlambert on 2012-04-08
I will try later!

---

### Post by JKSully on 2012-04-22
Im not new to linux but how do i run winetricks ie6?

---

### Post by Abe41 on 2012-12-13
64 Bit Ubuntu Sketchup launches Firefox successfully at the point you grab the satellite image Firefox gives an error  "Firefox doesn't know how to open this address, because the protocol (skp) isn't associated with any program." so between grabbing the PNG file and importing into sketchup through wine has anyone got this figured out and how to do it through command line yet? I am still unable to install 64 bit sketchup with IE 6 which is not supported in 64bit platforms anyone got a fix for this yet?

---

### Post by jparnell883 on 2012-12-25
or, simply go to the model you want in your favorite web browser (I'm using Chrome and this is the only one I can confirm this works for), right click the image it shows and click "Open Link in New Tab" and a new tab will open and it will download the SKP of the model. Then, in SketchUp, File->Import and search for your downloaded SKP.

Hope this helps :D

---

### Post by shimniok on 2013-03-13
Click the link, then after it fails, remove **[FONT=courier new]skp:getSkp@[/FONT]** from the address bar, press return, and it downloads a-ok.

> **jparnell883 said:**
> or, simply go to the model you want in your favorite web browser (I'm using Chrome and this is the only one I can confirm this works for), right click the image it shows and click "Open Link in New Tab" and a new tab will open and it will download the SKP of the model. Then, in SketchUp, File->Import and search for your downloaded SKP.

Hope this helps :D

---

### Post by dasankir on 2013-03-13
> **shimniok said:**
> Click the link, then after it fails, remove **[FONT=courier new]skp:getSkp@[/FONT]** from the address bar, press return, and it downloads a-ok.

Thanks! At last could download a model :b

---

### Post by majedaly on 2013-07-02
I used playonlinux to install google sketchup. It was easy and straight forward.
First Install play on linux
sudo apt-get install playonlinux. It will install wine, the prerequisites
Then from play on linux choose to install google sketchup, and follow the screen.
Works great on Ubuntu 13.04 Have been using for some time, didn't notice any glitch.

---

