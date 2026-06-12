---
title: "Installed Office 2007, but i have some problems"
date: 2008-03-28
forum: Wine
---

### Post by tarekeldeeb on 2008-03-28
Hello all ..

I had successfully installed office 2007 on my ubuntu 7.10 amd 64.
This was done following [these]("http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html") steps .. thanks goes to him.

I have some problems:
1- Although word and excel work fine, power point fails to start .. a splash .. then close .. did any1 manage to fix it ?
2- I want to add Calibri and other office 2007 fonts .. how is this done ?
3- the word does not type right-to-left text correctly .. can this be fixed ? I type arabic text in native ubuntu aplications normally with no problems.

Thanks in advance,
Tarek

---

### Post by erginemr on 2008-03-28
May I ask why you are not using OpenOffice (which is as good as it gets as long as open source software goes)? Incompatibility problems?

---

### Post by tarekeldeeb on 2008-03-28
> **erginemr said:**
> May I ask why you are not using OpenOffice (which is as good as it gets as long as open source software goes)? Incompatibility problems?

Although there's a .docx converter .. the interoperability between OpenOffice and Microsoft is too poor.

I have to read/edit docx files.

Not all of my work mates use ubuntu :)

---

### Post by Game_boy on 2008-03-28
> **tarekeldeeb said:**
> Although there's a .docx converter .. the interoperability between OpenOffice and Microsoft is too poor.

I have to read/edit docx files.

Not all of my work mates use ubuntu :)

OpenOffice 3.0 is coming in September with Word, Excel and Powerpoint 2007 file compatibility built in, and I better than the converter.

Can you not get your colleagues to save in the old formats, at least in some cases?

---

### Post by erginemr on 2008-03-28
> ...
2- I want to add Calibri and other office 2007 fonts .. how is this done ?
...

For your second question, I am not sure if it will work, but you may try to put the fonts in question into your virtual Windows drive under "C:\Windows\Fonts" which really is under:
```
~/.wine/drive_c/windows/fonts
```

---

### Post by jjk7288 on 2008-03-28
tarekeldeeb,

In addition to copying the fonts to the "C:\Windows\Fonts" folder under Wine's virtual drive, you might try adding it the fonts to Ubuntu's font folder, located at /usr/share/fonts/truetype for truetype fonts. The easiest way to copy them would be in Nautilus obviously, so just run
```
sudo nautilus
```
(since it's only root-writable) at the console, navigate to the font files and toss them in /usr/share/fonts/truetype. That should work.

---

### Post by mikedep333 on 2008-03-29
You might want to try wine-doors. Go through the initial steps and it will install fonts for you.

[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

---

### Post by tarekeldeeb on 2008-03-30
thank u ..

I love this community :lolflag:

---

### Post by Kinst on 2008-03-30
Everyone's having trouble with Powerpoint 2007 still. I installed Office 2007 this morning and still can't figure it out.

Of course, Powerpoint 2003 still runs great if you want to try it.

---

### Post by Jonathan Moerman on 2011-06-14
for PowerPoint: set riched20 to native

for the font issue:
[FONT="Arial"]This is very easy to fix: 
1. install FontForge
2. navigate to the fonts directory.
3. open the font you want (Calibri) and _do NOT import the bitmaps  fonts_
4. file -> generate fonts : save as TrueType and with the option _"No Bitmap Fonts"_ (and I recommend to disable the validate before saving option)
5. rename and replace the font
6. repeat this with the Italic and bold variants[/FONT]

Have a nice day!:)

---

### Post by christoph411 on 2011-06-14
You may be interested in this page here --  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

(scroll down to howto, and it will tell you how to get powerpoint up and running) I have personally used the howto and got powerpont working!

---

### Post by SoFl W on 2011-06-14
This thread is three years old, haven't those problems been addressed?

---

### Post by christoph411 on 2011-06-14
> **SoFl W said:**
> This thread is three years old, haven't those problems been addressed?

Whoops! Didn't notice... :oops::oops::oops:

---

### Post by Jonathan Moerman on 2011-06-16
> **SoFl W said:**
> This thread is three years old, haven't those problems been addressed?

The font (calibri & cambria) problem was still an unsolved problem in wine.

---

