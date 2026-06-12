---
title: "All-In-One Printers and x64?"
date: 2007-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_spiff on 2007-08-25
I plan to buy a Epson CX6600 tomorrow. Although, I have Windows, I would like to know if it'll run on my Ubuntu Feisty Fawn x64 installation? Are there drivers available or some substitutes? 
If not, can you suggest an all in one printer which will run with Ubuntu? I chose CX6600 as it has gained the highest ratings in CNet reviews.

Thanks.

---

### Post by John.Michael.Kane on 2007-08-25
> **s_spiff said:**
> I plan to buy a Epson CX6600 tomorrow. Although, I have Windows, I would like to know if it'll run on my Ubuntu Feisty Fawn x64 installation? Are there drivers available or some substitutes? 
If not, can you suggest an all in one printer which will run with Ubuntu? I chose CX6600 as it has gained the highest ratings in CNet reviews.

Thanks.

According to this [Epson Stylus CX6600]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX6600") the printer "works Mostly" not fully compatible.

You can use the same site [OpenPrinting database - Printer Listings]("http://openprinting.org/printer_list.cgi") to help you find one that is "fully" linux compatible.

Heres one example of fully supported all in one.
[HP OfficeJet 5610]("http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_5610")

---

### Post by Tanker Bob on 2007-08-25
> **s_spiff said:**
> I plan to buy a Epson CX6600 tomorrow. Although, I have Windows, I would like to know if it'll run on my Ubuntu Feisty Fawn x64 installation? Are there drivers available or some substitutes? 
If not, can you suggest an all in one printer which will run with Ubuntu? I chose CX6600 as it has gained the highest ratings in CNet reviews.

Thanks.
It should work fine. I'm running a CX7800 with no issues. You need to do two things. First, you need to install it manually in the CUPS server. For some reason, the printer wizard in the GUI doesn't list the Epson Stylus printers, but the CUPS server has the necessary files. You can access the server at [http://localhost:631/](http://localhost:631/).

In order to get the scanner to work, you'll need to install both sane, its support libraries, and libsane-extras. The latter has the support for the 3-in-1 series.

Enjoy your new printer/scanner!

---

### Post by s_spiff on 2007-08-26
> **Tanker Bob said:**
> It should work fine. I'm running a CX7800 with no issues. You need to do two things. First, you need to install it manually in the CUPS server. For some reason, the printer wizard in the GUI doesn't list the Epson Stylus printers, but the CUPS server has the necessary files. You can access the server at [http://localhost:631/](http://localhost:631/).

In order to get the scanner to work, you'll need to install both sane, its support libraries, and libsane-extras. The latter has the support for the 3-in-1 series.

Enjoy your new printer/scanner!
Thanks..will be picking up the printer tomorrow hopefully. and will try this out. thanks for the info. :guitar:

---

