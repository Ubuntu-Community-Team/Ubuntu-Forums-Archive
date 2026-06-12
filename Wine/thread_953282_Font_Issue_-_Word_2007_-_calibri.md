---
title: "Font Issue - Word 2007 - calibri"
date: 2008-10-20
forum: Wine
---

### Post by brandoncolorado on 2008-10-20
Hi,

I installed Word 2007 in Ubuntu.  I also use it with Windows.  Most of my documents use the Calibri font.  The Ubuntu installation lets me select this font, and I believe that crossover installed that font.  However, the Ubuntu version of the text looks really crappy.  

I am attaching a screenshot (Windows on right/Ubuntu on left).

What can I do to fix this?

---

### Post by brandoncolorado on 2008-10-20
I also copied/pasted the same text into OpenOffice.  The font chose is still shown as calibri, but the font looks great again!

See screenshot

---

### Post by ooobuntooo on 2008-10-20
I have the same problem, but I personally use FreeSans.

---

### Post by brandoncolorado on 2008-10-27
Do you know how to update the font that the actual Word 2007 program is using for menus and other parts of the program?

---

### Post by Duranxl on 2009-03-24
I have this problem.
However, if i use calibri in OpenOffice, it's **also** ugly.. any help?
I had the Vista fonts installed for open office before i used word 2007..then calibri didnt work either

edit: a reason why i wanted to use word 2007 because open office would render fonts differently from word.. causing pages to shift down and ruin the layout.
But now in Word 2007 the fonts are the same? Even verdana looks different (ugly) while in OpenOffice it looks nice

---

### Post by NightMKoder on 2009-03-24
What you're calling "ugly" is called anti-aliasing, and for some reason wine doesn't do anti-aliasing in the word document. Strangely enough, it DOES do anti-aliasing on shapes. 

I have no idea what's wrong - maybe you can fix it by getting native gdiplus, but I've never tried and wouldn't recommend it. My other guess is its a freetype issue that doesn't work with subpixel rendering well, or its an issue with the font itself. I never investigated very much into it - it's an eyesore at most and I'm more of a function over aesthetics person.

---

### Post by amadeus266 on 2009-03-24
Does your document print the way it looks on the screen? I use OO while other people at work use office2007 and sometimes (infrequently) the document created in word will look strange on my screen but prints just fine.

---

### Post by Duranxl on 2009-03-30
> **NightMKoder said:**
> What you're calling "ugly" is called anti-aliasing, and for some reason wine doesn't do anti-aliasing in the word document. Strangely enough, it DOES do anti-aliasing on shapes. 


The thing is, whenever I make the font larger, it does look nice..and it does look anti-aliased.. but if i used fontsize 10+bolt it looks like i'm back in 1998..

Don't know about printing..havent tried

---

### Post by illmatic on 2009-04-02
Have you tried to install ms Powerpoint viewer via Wine, because Calibri comes with the ms poweropint viewer 07 ;)

---

### Post by hasinasi on 2009-05-24
I've seen this problem for a while, and it annoys the crap out of me. The problem is that for calibri (and for some other fonts) anti-aliasing strangely does not work for some font sizes. 

In my case, this is irrespective of being done through WINE (which supports font-AA since version 1.1.16), or in native Linux apps, such as OOo. So, this would be similar to what Duranxl is describing, above. 

I found a web page in another language which seems to address this problem. They also show a nice demo of the fonts shown in several sizes. 
[http://www.yukei.net/2008/03/fix-para-calibri-en-linux/]("http://www.yukei.net/2008/03/fix-para-calibri-en-linux/") 
Unfortunately, I don't speak that language, but I'll try to figure it out. I'll post it here if I make some progress.

---

### Post by hasinasi on 2009-05-24
Oh, the answer is also here: 
[http://ubuntuforums.org/archive/index.php/t-594618.html]("http://ubuntuforums.org/archive/index.php/t-594618.html")
This worked for me. I think at the end, you want to add a
```
sudo fc-cache -f -v
```
(Otherwise it might not be effective immediately.)
Good luck!

---

### Post by NightMKoder on 2009-05-25
How did you manage to download the file? the webpage is long gone. (beta 2 was a while ago)

---

### Post by There Was A Time on 2009-06-05
Is there anywhere to download Calibri 1.0, then? Or any way to get it?

---

### Post by hasinasi on 2009-06-08
> **NightMKoder said:**
> How did you manage to download the file? the webpage is long gone. (beta 2 was a while ago)

Sorry for replying so late. I had my busiest two weeks in a veeeery long time. (Our second child was born, several deadlines at work...)

Anyway, isn't it quite easy to download the M$ compatibility pack? I just looked here: 
[http://www.microsoft.com/downloadS/details.aspx?familyid=9A1822C5-49C6-47BD-8BEC-0D68693CA564&displaylang=en]("http://www.microsoft.com/downloadS/details.aspx?familyid=9A1822C5-49C6-47BD-8BEC-0D68693CA564&displaylang=en")
and it was there. Otherwise, google should help. Isn't that all that's needed?

This download is a bit big (>26MB) and thus too big for e-mail. However, the calibri font alone is much smaller. If you have further questions, you can send me a private message.

---

### Post by Chandrashekhar on 2009-06-26
> **hasinasi said:**
> I've seen this problem for a while, and it annoys the crap out of me. The problem is that for calibri (and for some other fonts) anti-aliasing strangely does not work for some font sizes. 

In my case, this is irrespective of being done through WINE (which supports font-AA since version 1.1.16), or in native Linux apps, such as OOo. So, this would be similar to what Duranxl is describing, above. 

I found a web page in another language which seems to address this problem. They also show a nice demo of the fonts shown in several sizes. 
[http://www.yukei.net/2008/03/fix-para-calibri-en-linux/]("http://www.yukei.net/2008/03/fix-para-calibri-en-linux/") 
Unfortunately, I don't speak that language, but I'll try to figure it out. I'll post it here if I make some progress.

Create a file in $home/.fonts.conf and add following code to it

<match target="font" >
        <edit name="embeddedbitmap" mode="assign">
            <bool>false</bool>
        </edit>
</match>

That will solve the problem of anti-aliasing the calibri font.

---

### Post by luzbelito92 on 2009-11-21
Hum, la verdad muchas gracias ese pequeño tip me solucionó el problema. Dado que no está más disponible para descargar la versión 1.0 de Calibri en ningún lado, creo que esa es y será la única solución.

---

### Post by timrichardson on 2010-07-19
You don't need an old version of Calibri. You need to turn off Truetype embedded bitmaps. 
This answer comes from another launchpad post.

edit .fonts.conf in your home directory, and add to the bottom:

```
 <match target="font">
  <edit mode="assign" name="embeddedbitmap">
   <bool>false</bool>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>
```

the change will take effect when you log out and log in again.
this works in Debian squeeze as well.

---

### Post by Brebs on 2010-07-20
> **timrichardson said:**
> the change will take effect
... when you [COLOR="Black"]restart[/COLOR] the app.

I've done this a [million times](http://forums.gentoo.org/viewtopic-p-6183606.html#6183606).

---

### Post by Jonathan Moerman on 2011-06-14
[FONT="Arial"]This is very easy to fix: 
1. install FontForge
2. navigate to the fonts directory.
3. open the font you want (Calibri) and _do NOT import the bitmaps  fonts_
4. file -> generate fonts : save as TrueType and with the option _"No Bitmap Fonts"_ (and I recommend to disable the validate before saving option)
5. rename and replace the font
6. repeat this with the Italic and bold variants[/FONT]

I hope this helps!!

A fix is better than a workaround.;)

---

### Post by Pytte on 2013-02-05
Jonathan's answer worked for me after I installed Office 2010 with crossroads..

---

### Post by codemaniac on 2013-02-05
Old thread is closed now.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

