---
title: "Acer C710-2055 with Wine and Excel"
date: 2014-04-03
forum: Wine
---

### Post by angel8 on 2014-04-03
Hello community :)

I am planning to buy a new laptop: Acer C710-2055 Chromebook

CPU: 1.1 GHz Dual-core Intel Celeron Processor 847
RAM: 2GB
HDD: 320GB (5400 rpm)
(Taken from : [http://www.laptopmag.com/reviews/notebooks/acer-c710-chromebook.aspx](http://www.laptopmag.com/reviews/notebooks/acer-c710-chromebook.aspx))

I want to install ubuntu in that Chromebook (I readed and it seems possible: [http://liliputing.com/2012/11/how-to-install-ubuntu-12-04-on-the-199-acer-c7-chromebook.html](http://liliputing.com/2012/11/how-to-install-ubuntu-12-04-on-the-199-acer-c7-chromebook.html))

My real need is to use Microsoft Excel, I use it a lot, thousands of rows because is part of my job and it has to be Excel. I have installed wine before (to use Word) without problems.

Do you think this laptop could run good ubuntu + wine + excel (with thousands of rows) ? or do you think it will get too stressed to do anything?
Does the use of Excel with Wine have a strong impact in perfomance?

Excel 2010 requirements in Windows platforms :
CPU = 500 MHz
RAM = 256
HDD= 2GB
(official page: [http://technet.microsoft.com/en-us/library/ee624351%28v=office.14%29.aspx#section7](http://technet.microsoft.com/en-us/library/ee624351%28v=office.14%29.aspx#section7))

Thank you very much in advance, and sorry if this is not the section; there are too many! and this seemed to be okay.

---

### Post by Mark Phelps on 2014-04-03
You should read through the Wine page on Excel 2010 and see what limitations are listed:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22304]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22304")

You should also note that all of the ratings are Silver or Bronze -- which is not good.  These ratings mean that major functionality is missing, otherwise, it would have rated higer (Gold or Platinum).

Also, lots of folks have reported Macros and VB NOT working in the Wine implementations of Excel.

Quite frankly, MS Office products do not work particularly well in Wine, and then when you factor in the newer XML file formats (i.e., .xlsx, .docx), you get even worse results.

---

### Post by angel8 on 2014-04-03
Thank you very much for your answer and your opinion, Mark.
I appreciate it.

I see, I didn't know about the rating system.

When you see the "show all bugs" there a lot of them in "FIXED" status. I think I will try to set up an ubuntu virtual and test it, to see if at least is acceptable.

One doubt though, do you think with the laptop specs I posted is viable to use excel? The dual core cpu scares me a little.

---

### Post by oldrocker99 on 2014-04-08
I have an Acer C7 with the same processor, 6GB RAM running Chrubuntu (which is Canonical's GNU running on the ChromeOS's Linux kernel). (Are you absolutely certain that LibreOffice Calc cannot fit the bill?)

I am able to play some fairly demanding games on this little slab, but the CPU, certainly no heavyweight, is pretty beefy. I can open a 15MB .xls spreadsheet in LibreOffice Calc, and the machine chugs a bit, but it opens. Note that I added 4GB.

---

### Post by david2310 on 2015-03-24
hi folks,
i just received a used acer-c710 as gift.  working very fine, but i want to use it for my son's studies.  he is a student and needs office, thunderbird, and oracle express 11.  So am planning to install ubuntu and then a virtual machine for windows+oracle.
One of my friends told me upgrade RAM to 16gb, i am ready to cover the costs.  but i want to check here, and want to know if this machine can work like this?

precisely
1. i will put libre office and thunderbird on linux
2. oracle 11g (express)on virtual machine

is it worth to have 8gb or 16gb on this machine?  if we upgrade will it deliver what we want?

thanks in advance for your time and any assistance

---

