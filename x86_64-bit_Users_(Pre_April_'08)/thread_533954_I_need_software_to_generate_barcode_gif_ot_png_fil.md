---
title: "I need software to generate barcode gif ot png files on Ubuntu 7.04"
date: 2007-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Licicin on 2007-08-24
Hi

I need software to generate barcode gif ot png files on Ubuntu 7.04

Thanks.

---

### Post by A$h X on 2007-08-24
I can't actually understand what you are saying. You want to "generate" barcodes in gif and png formats?

---

### Post by Licicin on 2007-08-24
i need to make a barcode gif file from say 12345678 string.

---

### Post by John Jason Jordan on 2007-08-24
> **Licicin said:**
> i need to make a barcode gif file from say 12345678 string.
The problem with your request is that there are many, many different kinds of barcode formats. You need to say what kind of barcode you want to generate. If you don't know what format you need, at least say what the barcode is for. Is it for a book? A product to be sold in a store? A mailing label to be processed by automatic post office reader devices? An internal company inventory control system?

---

### Post by Licicin on 2007-08-24
I need at least Code 128 UCC, Code 128 mode A-C
It will be good to print Data Matrix barcode symbols, with the ECC
200 data quality format or MaxiCode barcode.

---

### Post by John Jason Jordan on 2007-08-25
> **Licicin said:**
> I need at least Code 128 UCC, Code 128 mode A-C
It will be good to print Data Matrix barcode symbols, with the ECC
200 data quality format or MaxiCode barcode.
I believe Scribus will do this. You can find version 1.2.4 and 1.3.4 in Synaptic. However, I do not believe barcodes were added as early as 1.2.4, and I also do not recommend 1.3.4. Version 1.3.4 is a development version and is quite buggy. I use 1.3.3.8 and it is very stable, although also a development version. I think you can install 1.3.3.8 if you go to Package > Force Version in Synaptic. If not, just install 1.3.4 and cross your fingers that it works.

Once you have it created in Scribus, you can export to other formats. 

There may be other packages that can create barcodes, but I am not familiar with any except Scribus. You can search in Synaptic on "barcode" and it will tell list all packages that have "barcode" in the name or the description.

---

### Post by jfinkels on 2007-08-25
[http://www.barcodesinc.com/generator/index.php](http://www.barcodesinc.com/generator/index.php)

[http://www.terryburton.co.uk/barcodewriter/generator/](http://www.terryburton.co.uk/barcodewriter/generator/)

[http://www.barcoding.com/upc/](http://www.barcoding.com/upc/)

[http://www.google.com/search?hl=en&q=barcode+generator&btnG=Google+Search](http://www.google.com/search?hl=en&q=barcode+generator&btnG=Google+Search)

---

### Post by eentonig on 2007-08-25
Here you go. Try them out at your liking.

>  user@host: ~$ apt-cache search barcode
alexandria - a GNOME application for managing book collections
**barcode - Creates barcodes in .ps format**
emilda-print - Client-side print application for Emilda
**iec16022 - Generates 2d ISO/IEC 16022 barcodes (data matrix/semacode)**
**kbarcode - barcode and label printing application for KDE**
libgd-barcode-perl - Library to create barcode images (GD::Barcode)
**libpostscriptbarcode - A barcode generator written entirely in PostScript**
mednafen - multi-platform emulator, including NES, GB/A, Lynx, PC Engine
texlive-fonts-extra - TeX Live: Extra fonts
texlive-pstricks - TeX Live: PSTricks packages


---

