---
title: "I need to use MS Excell as a helper application"
date: 2015-08-06
forum: Wine
---

### Post by quasitor on 2015-08-06
I am starting on a course to learn to use Excell and the first exercise needs me to open a file in excell. At the moment the helper application is Libre office. What I nedto know is where the copy of excel i have on my machine would be stored. 

Ubuntu 14.04 LTS
Easy note TS

---

### Post by SeijiSensei on 2015-08-06
Ubuntu doesn't come with any copies of Excel by default because it's a Windows program from Microsoft and isn't free.  You can use the open alternatives to MS Office products like LibreOffice or OpenOffice or gnumeric for spreadsheets.  If those don't work for you, you could look into subscribing to [Office 365]("http://www.microsoftstore.com/store/msusa/en_US/pdp/Office-365-Home/productID.286395000").

Frankly, if this is your first time out with spreadsheets, I'd try using LibreOffice Calc.  For anything basic, it's pretty much identical to Excel.  To the extent that they differ, consider figuring out how to do the equivalent tasks in Calc that your instruction presents for Excel a valuable learning experience in the long-run.

---

### Post by QIII on 2015-08-06
Is this training for a job, part of a school curriculum?

If so, I'd recommend actually using Excel on Windows.  The environments are different and even if you save a Calc file as an Excel spreadsheet, formatting may be different.  Furthermore, the built-in Excel functions won't probably be available in LibreOffice.

Learn Excel with Excel if that's the intent.  Use LibreOffice if you choose to for things other than your training.

---

### Post by monkeybrain20122 on 2015-08-06
> **quasitor said:**
> I am starting on a course to learn to use Excell and the first exercise needs me to open a file in excell. At the moment the helper application is Libre office. What I nedto know is where the copy of excel i have on my machine would be stored. 

Ubuntu 14.04 LTS
Easy note TS

Is that what they call education now?? :)

---

### Post by QIII on 2015-08-06
The reality is that the money in the workplace is in using Microsoft products.

I could be idealistic and develop software for Linux.  But I like the big house, the swimming pool, all the cool computers I have, the woodworking tools...

---

### Post by monkeybrain20122 on 2015-08-06
> **QIII said:**
> The reality is that the money in the workplace is in using Microsoft products.

I could be idealistic and develop software for Linux.  But I like the big house, the swimming pool, all the cool computers I have, the woodworking tools...

Well perhaps. But to my mind learning to do something you can read from a manual is not education (first exercise is to open a spreadsheet in EXCEL??!!), and knowing only how to use a product by one company is not knowledge, whether it is EXCEL or MATLAB(but of course you will need to know a lot  more in math to use MATLAB, I mean using MATLAB itself) I don't know, I just find that there is something deeply unsatisfying to know that all you know revolves around a product which you cannot modify or peek inside, and is subjected to some licensing terms and payment scheme. But then this is philosophical my background is pure mathematics. :)

---

### Post by QIII on 2015-08-06
As a Mathematician, I know that there may be two or more equally valid solutions to some arbitrary function.

I use Microsoft products and develop for Windows to earn my pay.  Clearly, that has not precluded me from also being well-versed in Linux tools.

We speak so often about "choice" in the Linux community, but so often disparage the choices of others.  Let's not call the OP to task or demean their pursuit.

If someone is studying Excel, they should use Excel.

One man's opinion and still my recommendation.  For whatever it's worth.

---

### Post by Irihapeti on 2015-08-06
I think that we need to answer the question that is asked, and not the one that we think ought to be asked.

Personally, I loathe the fairly frequent "why would you want to do that???" response.

---

### Post by quasitor on 2015-08-07
Thank you for your responses. However I have a copy of office 97 on my machine which opens and works in Wine. However there are exercises that need to be completed using Excell. I am reasonably familiar with running spreadsheets but I need to have office qualifications to improve my chances of a new job; the course will provide certification.

---

### Post by Irihapeti on 2015-08-07
Programs running under Wine can be found in /home/username/.wine/drive_c/Program Files/  At least, I have copies of the free Word and Excel readers, and they are installed there in a folder called Microsoft Office.

---

### Post by Simon_Tomoko on 2015-08-13
Years ago, when I was attending college, we received "Student Versions of MS Excel" *Note: it is one "L" not two. I had only one class on this subject but as stated above Open Office and Libre Office have  the pretty much the same setup. In fact, when Frank and I opened our clinic, we took some free PCs donated to the clinic, and Frank installed Debian Gnome on them. Our office runs Linux. Maybe not my "favorite flavor" but it is Linux. And the personnel in our office trained on Windows and Excel and Word, had no issue learning the new software. Most just picked it up straight away thinking it was the same software.

If you still must use Excel '97 on a Linux machine, then you may need to tweak you WINE. Since WINE runs as Windows XP default you might need to use winecfg or access it through the start menu. Go to the Applications TAB and select Windows 98 from the Windows Version box at the bottom.

---

