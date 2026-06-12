---
title: "Problem with Foxit Reader on Wine"
date: 2011-11-17
forum: Wine
---

### Post by soin on 2011-11-17
Hi all,

I use ubuntu for quite a long time, but I haven't had many experience in wine, just didn't need it, I think. 

Now I've found that unfortunately ubuntu doesn't provide any good pdf reader, that would also work with annotations. I have lectures at the university in pdf and it would be quite handy to change them on the fly as the lecturer speaks.

That is what Foxit Reader for Windows offers.

I downloaded .exe from the site and installed it using wine. I am able to run it, but not able to open any file, I think that's because the difference in file naming for win and linux.

Also I would like to find a way of making it a default reader.

I've found [this]("http://sodeve.net/2007/12/foxit-reader-on-ubuntu-linux-through-wine/") link for doing it and it is perfectly clean. but there is a problem. 
I run ubuntu 11.10 and there seems to be no option of adding a custom script as a default action.
There are some threads about .desktop files, but I didn't get a point of how to do it... 

Would be very grateful if someone would spend a little time and help we with this. :)

---

### Post by soin on 2011-11-19
bump... please, anyone?

---

### Post by ergo-proxy on 2011-11-20
Look for xournal otherwise check winehq.

---

### Post by karenyyng on 2011-12-30
No luck with Foxit Reader as well with wine. 
But if you are looking for pdf reader with annotation functionality, you can try installing pdfXChange viewer with wine.
[http://www.tracker-software.com/product/pdf-xchange-viewer]("http://www.tracker-software.com/product/pdf-xchange-viewer")

It has most of Foxit Reader (window version) 's functionality.
PdfXchange pdf viewer works perfectly after tweaking some rendering settings.

---

### Post by Dlambert on 2011-12-30
What do you mean by "no good pdf reader" I personally find Ubuntu's default is great.

---

### Post by ilkos on 2012-01-08
Hi everyone,

I use Foxit Reader because it supports annotations (PDF X-Change too).
Everything is OK, but there is a problem:
when open second pdf file from file manager (message "Setup.exe Could not open file. File not found."). 

I use Ubuntu for about seven days. I used Win7 before. Ubuntu is +++:)
Thanks in advance!

---

### Post by Advice Pro on 2012-01-11
I just found out about this: [Foxit Reader for desktop Linux]("http://www.foxitsoftware.com/pdf/desklinux/").

---

### Post by ilkos on 2012-01-13
I hope Foxit for Linux will support annotations soon. :)

---

### Post by bluexrider on 2012-01-13
I fail to understand why you would want to use WINE and a .pdf reader over the default Ubuntu one. Look to the software center to find an appropriate application.

---

### Post by ilkos on 2012-01-13
I would like to find but, I need better annotation support then native Linux applications offer at the moment.

I tried some native applications which support annotations:
 1. Okular - supports annotation, but I'm not satisfied how it works. Can't use saved file in Windows (not .pdf extension) and I think it has some specific annotation format.
 2. Adobe Acrobat 9 - works OK, but need explicit owner rights to allow others make annotations. Many files were locked for Acrobat.

Because of that I use Wine (slower, some bugs, but annotation works perfect with Foxit Reader version 4.3.0.1110).

I tried with ten or more different native applications but didn't find better solution.

---

### Post by Simian Man on 2012-01-13
> **ilkos said:**
>  1. Okular - supports annotation, but I'm not satisfied how it works. Can't use saved file in Windows (not .pdf extension) and I think it has some specific annotation format.

I just tried this and it saves the annotations with the file in regular PDF format.  I can't test whether they can be opened on Windows though.  You could install Okular on Windows to get around that though.

---

### Post by ilkos on 2012-01-13
Sorry I mixed Okular with Xournal. Okular saves to .pdf format but doesn't work OK with annotations.
When I try to highlight one column of text (article is written in two columns) both columns were highlighted. After file reopening annotations disappeared.

---

### Post by Dennis N on 2012-01-13
FYI:

Last year I emailed FoxIt to see if a 64 bit version would ever be available. They replied that FoxIt Reader's version for Linux isn't under development any longer, so the April '09 release is the last. No 64 bit version. It is a nice basic reader, but the Linux version doesn't have a lot of the features the Windows version has. Probably comparable to Evince. The .deb file is still available on their downloads page.

---

### Post by ilkos on 2012-01-13
I visited official Foxit site, but didn't notice release date for Linux version :(.

---

### Post by agestrada on 2012-03-16
Thanks a lot ilkos!! I tried with the Foxit 4.3.1 in [http://www.oldapps.com/foxit_reader.php](http://www.oldapps.com/foxit_reader.php) under Wine and it works in Natty. I can finally save annotations and bookmarks in the PDFs. Big time. 
PS. Latest Foxit (5...) does not work BTW.

---

### Post by r_avital on 2012-07-31
> **bluexrider said:**
> I fail to understand why you would want to use WINE and a .pdf reader over the default Ubuntu one. Look to the software center to find an appropriate application.

You fail to understand because you don't read.

It has been mentioned several times, that the WINDOWS version of the software FOXIT, allows the user to ANNOTATE.

Does ANY PDF reader available for linux do that?  

Now do you understand?

---

