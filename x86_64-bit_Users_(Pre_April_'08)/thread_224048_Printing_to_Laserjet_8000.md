---
title: "Printing to Laserjet 8000"
date: 2006-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-07-27
1) Where are the spool files kept?

2) The Laserjet 8000 is capable of "RIP once, print many" functionality. That means that if you send a print job for multiple copies collated your computer need send the job only once along with (in the print stream) a counter for how many copies. The Laserjet 8000 images the entire document and holds it in RAM. This makes it print right up to the rated speed for all copies after the first one. I can't get it to do this under Linux with Adobe Reader 7.0.8 or with Evince. 

It does print multiple copies collated from Linux. But programs do so by repeatedly sending the print job over and over into one large spool file. With Adobe Reader there is a display showing it doing so. With Evince it does not show what it is doing, but it is obvious that it is concatenating individual print jobs because it takes forever and you can see the hard disk light flashing as it writes each job to the spool file. This morning I was trying to print 100 copies collated of a 256 page book. You can imagine how long it would take to finish sppoling 100 individual print jobs and how massive the resulting spool file would be (several GB). Plus, it would normally take a couple days to finish printing that job; if it has to reimage the document for each copy it would slow the printer down and it would take an extra day to finish printing.

Adobe Reader does not use CUPS. (At least I don't think it is using CUPS.) You have to give it an lp print command. The only way I know to do it is to tell it "lp -d Laserjet-8000" or, for the other driver (see below), "lp -d Laserjet-8000-Series-Postscript-(recommended)."

I don't know what Evince is using, but my guess is CUPS.

I've looked through all the possible settings in CUPS for the Laserjet 8000 (both installed versions) and can't find anything that might be wrong. 

Using CUPS I have installed both the Laserjet-8000 and the Laserjet-8000-Series-PostScript-(recommended). Neither can access the "RIP once, print many" feature. Note that the Postscript-(recommended) one is using the HP8000_7.PPD file. This is the same PPD file that I use on my Windows desktop, which has no problem using the "RIP once, print many" feature.

Until I can resolve this problem I have to transfer all PDF files to my Windows printer and print from there, unless it is something that I need only one copy of. This is seriously sucking. Any suggestions are welcome.

---

### Post by dasyar613 on 2006-07-27
You have a couple of options, [www.linuxprinting.org](www.linuxprinting.org), or goto the HP web site, and see what the UNIX drivers have to offer. Since your printer has been "retired", you may have a problem at the HP site. I guess your best bet would be the linuxprinting.org site. If you got a CD with the printer, you may want to check that out, maybe their are some drivers on the CD.

I think that in most cases it is not the fault of Ubuntu, but the companies that are unwilling to provide the necessary drivers for their equipment.

---

### Post by John Jason Jordan on 2006-07-27
> **dasyar613 said:**
> You have a couple of options, [www.linuxprinting.org](www.linuxprinting.org), or goto the HP web site, and see what the UNIX drivers have to offer. Since your printer has been "retired", you may have a problem at the HP site. I guess your best bet would be the linuxprinting.org site. If you got a CD with the printer, you may want to check that out, maybe their are some drivers on the CD.

I think that in most cases it is not the fault of Ubuntu, but the companies that are unwilling to provide the necessary drivers for their equipment.
Thanks for the suggestions.

The fault is not specifically with Ubuntu. The problem is either in the inability of programs to use the options available in CUPS, or in CUPS, or both. The fact that an option is set in the CUPS driver (e.g., the 3000 sheet stacker is marked as "installed") does not mean that the print dialog box in a given application will display that option and allow the user to select/deselect it.

Since my original post I found that there was a third driver option in CUPS -- Laserjet-8000-PS. I installed it, but found no differences. 

I also searched through Synaptic for something better than Adobe Reader 7.08 and Evince. I tried epdfview (looks like Evince but with no print function at all), gpdf (same comment as for gpdfview, except it does have a print function, but without a number of copies option), and kpdf. Of all the choices kpdf is by far the best, although it still does not work right.

Note that each application displays different options in its print dialog box. If an option is available in the CUPS driver, then failing to show that option in the application print dialog box is the fault of the application programmers.

Kpdf comes the closest to what I need. It will print multiple copies collated, and without concatenating individual jobs to a massive spool file. However, it still does not use "RIP once, print many." It prints multiple copies collated by continuously reprinting the document. My Laserjet 8000 is connected via ethernet, and you can see the ethernet port light flickering continuously long after the first job is finished, continuously until the last copy prints. If you close kpdf before it finishes printing the last copy the print job aborts at that point. This makes it print slow, plus it means I cannot shut down kpdf for possibly several days. 

Kpdf cannot print multiple copies collated to the Laserjet-8000-Series-Postscript-(recommended) or to the Laserjet-8000-Series-PS printers because there is evidently a bug in setting print options. When you click on Properties for the printer you can tell kpdf what features are installed (e.g., stacker, 2000-sheet paper tray, duplexer, etc.) But when you try to tell it there is a duplexer (or any other option) the option turns red and, when you try to save the settings, it makes the sound of breaking glass and tells you that there is a conflict with a setting in the Advanced tab. You go into the Advanced tab and there are no settings relating to what you were trying to do in the Properties window.

As for HP, they have nothing that is not already available in CUPS. I'll go check out linuxprinting.org (again) and search for more stuff, but I didn't find anything when I went there a couple days ago.

Still searching for answers. :(

---

