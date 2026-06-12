---
title: "Printing from acrobat reader inside chroot: is it possible?"
date: 2007-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by hardhu on 2007-03-08
Hello everybody,
to have flash and java working with firefox in my feisty 64bit, I have followed the way of building a 32 bit feisty chroot and installing Firefox inside it. Now, when I am browsing the web, sometimes I find some pdf documents that are automatically opened in acrobat reader through its plugin (that I have installed in the 32 bit chroot too). But when I try to print them directly from print menu of the plugin, the printer is shown in it and the print job seems to start, but nothing seems to be sent to the printer.
I have cups installed only in the 64 bit environment, and I can print pdf documents from kpdf, but again not using acrobat reader, and in this case I don't see the printer listed in print menu window of acrobat reader.

So what I am asking is: is it possible to print pdf documents directly from acrobat reader 32 bit plugin inside firefox, or have I to save them before and then print them from kpdf (that is, is this the only way)?

---

### Post by John Jason Jordan on 2007-03-08
> **hardhu said:**
> So what I am asking is: is it possible to print pdf documents directly from acrobat reader 32 bit plugin inside firefox, or have I to save them before and then print them from kpdf (that is, is this the only way)?
There are three ways to install Adobe Reader 7.0.x under 64-bit Ubuntu. Putting it in a 32-bit chroot is one, as you have discovered. I used to run it that way under Hoary and Breezy. It is also possible to install it in your regular 64-bit world with --force-architecture. There are lots of threads here explaining how to do it. I switched to this way with Dapper and continue now with Edgy. A third option is to install the Windows version in Wine or Crossover Office. I managed to get Adobe Reader 7.0.5 for Windows installed in Crossover Office Pro 5.03, but after upgrading to Crossover Office Pro 6.0 I was unable to reinstall it. 

The problem with printing will be the same regardless of how you install it. In each of the three installation methods I used the print dialog box was the same -- even the Windows version installed in Crossover Office. That is, it does not show printers installed in CUPS. The reason is that Adobe proggers apparently have never heard of CUPS, therefore Adobe Reader for Linux is not CUPS-enabled. The only way to print from it is t use command line syntax in the little box in the print dialog box. However, the rest of the print dialog box does work, that is, options like scaling, number of pages per sheet, page orientation, etc. It's just that you have to tell Adobe Reader the destination by the command line.

The syntax for the command line is fairly straightforward. You use either the lp or the lpr command (see man lp or man lpr for more details). In the command you type the name of the printer exactly as it is known in CUPS. I have several laser printers. Here is the command for my HP Laserjet 8000DN, first for lp and then for lpr:

lp -d HP-Laserjet-8000-Postscript
lpr -P HP-Laserjet-8000-Postscript

In the man pages for lp and lpr you will find some other print options that you can append at the end. However, for most printing the options that you might want to put at the end are easier to set by using the options in the print dialog box (duplexing, scaling, etc.). You could also just send the file to the printer directly from the command line, using lp or lpr options, without even launching Adobe Reader, but then you really need to get familiar with lp and lpr.

Personally, printing PDF files is a major pain for me. I can print anything to my Laserjet 8000DN, but lp and lpr do not have syntax to access some of the features of the printer. Therefore, sometimes I cannot use Adobe Reader for the print job. I can access almost all the features of the printer with Kpdf, but Kpdf uses some rendering engine (Ghostscript, I think), so that it takes forever for the printer to image the pages. 

That was a bit lengthy. I hope it helps you resolve your problem.

---

