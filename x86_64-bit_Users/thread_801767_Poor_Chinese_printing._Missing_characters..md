---
title: "Poor Chinese printing. Missing characters."
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by lancest on 2008-05-20
Ubuntu 64-Hardy
HP 1029, HP 5608 printers 
[FONT="Arial Black"]20 to 40% of Chinese characters don't print out from Calc and Writer to my printers. [/FONT]
Chinese language fully installed & complex characters-can input.
 Scim works. OO 2.4 is set is for Chinese characters.
Anybody help?

---

### Post by solkis on 2008-06-09
When I experienced this same issue in OpenOffice Calc I found a work around. Export the document to a PDF using the File > Export as PDF... option. Using this route I was able to generate a pdf which included *all* of the Chinese characters which were previously displaying and previewing correctly but printing as little boxes. First I tried just printing to the PDF printer using File > Print but this just created a pdf with the missing characters (but this is a good way to test the normal printing support without wasting paper.)

Hope this helps others in this situation...

-solkis

---

### Post by lancest on 2008-06-09
Yes I found this solution early on. I think 7.10 had better Chinese print support.

---

### Post by ericy on 2008-06-10
This may work. Change the font to your preferred Chinese font. By default, the font used to display Chinese characters is DejaVu Sans, and apparently there's a conversion (or font swapping) problem when you print.

---

### Post by solkis on 2008-06-11
This does work. I switched the font for the Chinese columns in Calc to use the AR PL UKai CN font and they now look and print beautifully. Thanks.

---

### Post by lancest on 2008-06-17
Late Reply sorry. Unfortunately I cannot get perfect Chinese printing- by changing the fonts as you say you did. Still some Chinese fonts do not print in Calc. Here is a screenshot from my Calc Tools/Options/Fonts. (English is the default language) Any difference from yours? Did you do anything additional to this?

update: able to print Chinese perfectly using the DejaVu Sans swap with AR PL UKai CN font
New problem though. Changing those that has altered my whole Open Office interface fonts to quite small and blurry (DejaVu Sans?).
(If this doesn't get solved i think i will just create a user account for strictly Chinese)

---

### Post by Tharangalion on 2008-12-04
I changed the font to AR PL UMing CN. It worked a treat.
I did not however, set up any replacement fonts in Open Office Calc. Changed the font directly in the worksheet. 
The DejaVu font family will not print every character.

---

### Post by daqron on 2009-02-02
> **Tharangalion said:**
> I changed the font to AR PL UMing CN. It worked a treat.

Yes, this worked for me as well. It's a much nicer font than the default one anyway. Thanks guys!

---

### Post by daqron on 2009-02-09
After using this for a few days I've noticed that despite a 99.9% improvement using the method described in this thread, I'm still having sporadic issues using the AR PL UMing CN font. 

Specifically, the character &#20570; ('zuo4') still refuses to print. As always, printing to PDF first addresses this problem but I'm curious if anybody else is having this problem. I will update this post again if I run into any more stubborn characters.

---

### Post by lancest on 2009-02-10
Sorry no idea. Still printing in PDF or using Google documents. The font change in Open Office was undesirable as it changed the interface font also.

---

### Post by zhangweiwu on 2009-02-16
Hi. I found I can workaround this problem by setting font-replacement table for Simplified Chinese fonts I found on Windows Simplified Chinese version.

See the attached screenshot how I did it. I didn't replace all fonts that available on Windows Simplified Chinese version but only the ones I came across. You can do the similar.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=103520&stc=1&d=1234766477[/IMG]

Interestingly, although font replacement seems to work for printing, it doesn't work on the screen, even if the checkbox is checked for "screen".

---

### Post by Claire Zerbinette on 2009-03-15
**Lancest said : **> update: able to print Chinese perfectly using the DejaVu Sans swap with AR PL UKai CN font
New problem though. Changing those that has altered my whole Open Office interface fonts to quite small and blurry (DejaVu Sans?).
(If this doesn't get solved i think i will just create a user account for strictly Chinese) 


hello! 
I also wanted to change the automatic font in order to use the AR PL UKai CN font instead of DejaVu Sans. I first followed your way, then I discovered that there is another way that doesn't change the whole interface. 

Instead of doing modifications in "OpenOffice.org -> Fonts" with the replacement table, I went to "OpenOffice.org Writer -> standard fonts (oriental). There I choosed the fonts. (maybe the names are not exactly the same because I use the french interface for OpenOffice). 

You have to desactivate the replacement table and to restart OpenOffice. 
Then you'll have the standard design and write with your favourish chinese font. 

**But... I still don't manage to write the "zuo"-words like &#20316; or &#20570; with chewing (traditional characters)** 
I always have to swich to the simplified font "&#26234;&#33021;&#25340;&#38899;"... but... this short-term solution has limits...
How do the taiwanese or Hong-Kong-chinese linux users do ? oh... they might use another system without pinyin...

---

### Post by zhangweiwu on 2009-06-17
did you also try printing?

In my case with OOO 2.4, if you do not specify font replacement table, you cannot print it right. It will display correct ideograph but prints square blocks, unless if you generate PDF and print that PDF instead of using OOO's print dialog. I consider it a bug and as far as I remember it was reported before.

Please use the attached renewed screenshot to configure your font replacement, this screenshot contain all the Chinese fonts installed by default on Windows 2000 Simplified Chinese. I haven't find time to complete it with other Windows versions yet.

Note that to get the chinese san-serif font you need to install ttf-wqy-zenhei

---

