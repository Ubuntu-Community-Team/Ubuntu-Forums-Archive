---
title: "How to Print from Dia - PS?"
date: 2009-02-28
forum: x86 64-bit Users
---

### Post by wmichaelb on 2009-02-28
Hi, I'm trying to print a Dia file. I researched it, and found on the Dia site that the best way is to export the file as a postscript file, and then print it from Nautilus. But when I try, I get only about a quarter of the diagram. What am I missing? :confused:

Thanks in advance for any help.

---

### Post by cybergalvez on 2009-02-28
> **wmichaelb said:**
> Hi, I'm trying to print a Dia file. I researched it, and found on the Dia site that the best way is to export the file as a postscript file, and then print it from Nautilus. But when I try, I get only about a quarter of the diagram. What am I missing? :confused:

Thanks in advance for any help.

I just tried this and printed drectly to lpr and it worked, although the image was to big for one sheet and printed on multiple sheets.  You could also export your image to something line an svg file and user some other program to print it like inkscape

---

### Post by wmichaelb on 2009-03-01
Cybergalvez: thanks for responding! I did try that: the svg file I exported to was scrambled in Inkscape, and the diagram was too fuzzy to read in Open Office when exported as a bitmap or png. In order to provide this as a handout to my students, I really need to fit it on one 8-1/2 X 11" sheet of paper. 

How does one print directly to lpr? When I just ran lpr without an address or argument, the printer driver (Laserjet 2200 DN) generated an error. When I tried inserting my printer (HP-Laserjet-2200) into this command, I got a different error message. I did some investigation on lpr, and got quickly lost. 

Thanks for any light you can shed, or better links to investigate.

---

### Post by cybergalvez on 2009-03-03
> **wmichaelb said:**
> Cybergalvez: thanks for responding! I did try that: the svg file I exported to was scrambled in Inkscape, and the diagram was too fuzzy to read in Open Office when exported as a bitmap or png. In order to provide this as a handout to my students, I really need to fit it on one 8-1/2 X 11" sheet of paper. 

How does one print directly to lpr? When I just ran lpr without an address or argument, the printer driver (Laserjet 2200 DN) generated an error. When I tried inserting my printer (HP-Laserjet-2200) into this command, I got a different error message. I did some investigation on lpr, and got quickly lost. 

Thanks for any light you can shed, or better links to investigate.

I just tried it and mine exported to svg just fine, so I'm not sure why your is scrambled.  When I printed lpr was the selected printer and it just worked with my HP inkjet printer.  How big is your diagram? I'm wondering if size has anything to do with it?

---

### Post by wmichaelb on 2009-03-03
Cybergalvez: thanks for your interest and time! 

I don't know how to describe the size, other than to say that I developed it on a single screen, and when I click on the Dia preview button, I can arrange the file to fit on a single screen. 

When I try to print from Dia, I get a dialog box with "printer" selected, and "lpr" in the entry bar. When I click "ok", I get no print and an error message, "Printing error: command 'lpr' caused sigpipe." When I close this out, I find a second message that says "Printing error: command 'lpr' returned 256".

If I open the exported svg file in Inkscape, I get what appears to be a good copy of the diagram, but all the text entries are so large as to jumble together and hide the diagram. 

If I export the file as an eps, I can easily open it in Evince. It looks sharp, and I can easily set it up to "fit to page". But no combination of rotation or landscape selections in either Evince or the HP Laserjet driver will print it in landscape mode, and the right side of the diagram runs off the page. It simply insists on printing in portrait mode, no matter what the print preview looks like. 

If I export the file as a bitmap or png file, and try to print it from Open Office, it looks fuzzy and and the text is unreadable. I can find no selection in Dia to export as a pdf, which would allow me to try this on my Apple G4, or to project it on the Windows machines at school. 

What really puzzles me is the lack of control in Evince. I can find some entries in Launchpad referring to difficulties in printing pdf's in Evince, but not eps files. And apparently, the software works for you. 

I'm running 8.10 64-bit, which I prefer because of it's speed. My next step is to try and print it from 8.0 32-bit (I have a multi-boot system) or perhaps Open Suse, which has KDE. 

Thanks again for any other suggestions I might try. If KDE works, I may consider moving to that environment.

---

### Post by wmichaelb on 2009-03-03
After some thought, I opened the file in Inkscape, selected "all", and revised the font size. That got the file back to approximately normal, but for some reason without the "&" character in the text. I resized the whole diagram slightly, and then successfully printed it in landscape mode. 

Ubuntu 8.04 32-bit has a mode in Evince to print to PDF, but 8.10 64-bit does not. (?????). I am now more motivated to try KDE to see if it gets around this problem. I really like Dia, and would use it a lot more for teaching material if I could print the output more easily, and get it into PDF form to use on our school machines. When I get a few minutes, I may also put in a bug report on Evince to Launchpad. But for the moment, I'm okay.

Thanks again for your help. The ability to dialog with someone helped a lot.

---

### Post by cybergalvez on 2009-03-06
you can print anything to pdf that uses the normal cups printing.  When you print you use print to file and you can select either ps or pdf

---

### Post by yther on 2009-03-06
Doesn't OpenOffice import SVG directly these days?  I thought for sure it could.  If so, you could bring it into Draw and orient it properly, then export the drawing directly to PDF from OO.

If that doesn't work, how about this?  Save drawing from Dia into PS.  Use **ps2pdf** (in a terminal) to get it into PDF, then manipulate as needed.

---

### Post by zman58 on 2009-08-25
When you print from Dia you will send the print job to the default printer on your system. If you only have one printer, then it should go do that one.

In the dia grid you can see the paper sheet size areas--the larger black rectangles. When printing directly from dia your diagram will require as many pages as you have placed diagram objects into.

You can set paper size and margins using the menu:
File - Page Setup
...here you can set paper size, margin, and portrait or landscape mode.

When you change the page setup you will see that the black rectangles in the grid will change to match what you have set. ...very easy to visualize.

So it is easy to create a diagram that prints to a single sheet of letter size paper be it portrait or landscape.

I have not been able to make dia see additional printers on my system. It only gives me a choice of "lpr". I tried creating a symlink to printcap at /etc/printcap like so:

 sudo ln -s /var/run/cups/printcap /etc/printcap

...but that did not work for dia. I still only see "lpr"

...this did allow me to see all of my printers when printing with another application called QCAD which was not showing any printer.

---

### Post by Statik on 2009-09-10
In Dia, the best thing you can do in order to get a single sheet drawing of the layout you want is:
1. File -> Page Setup : Select Fit To 1 x 1
2. Export as eps
3. run epstopdf to get a PDF
4. Then print that PDF using either document viewer (not as reliable) or adobe acrobat.

I do this all the time.

Statik

---

### Post by wmichaelb on 2009-09-10
Statik: Thanks for responding; that in fact is what I ended up doing. I just thought (and continue to think) that one should be able to print directly from a fundamentally graphic program.

---

