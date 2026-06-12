---
title: "[SOLVED] Firefox / Fonts / system / Hard on the eyes"
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-06-24
Has anyone else noticed that the default fonts and page views aren't exactly easy on the eyes?

Take the google home page for instance.  Using IE, it has a nice crisp look.  The search box has an even thin line around it and everything looks in place and easy to read.

In Firefox the sides of the box and the top of the box carry a thick bold line while the bottom has no line at all.  It's the same on on web combo box's as well.

The pages in IE have sharp clear text of adequate size for reading on my 19" monitor at 1024x768.  In fire fox, the fonts seem much smaller and very think.  System fonts seem to mostly follow the same pattern.

How can I get my pages and system to be a little more friendly on my eyes?  I do go into the  Firefox View menu and change the text size (or use the ctrl +) so that it's more readable, but this is a band aide.

Any ideas how to change this?

TIA

---

### Post by david_2001 on 2007-06-24
Installing the msttcorefonts package will help - it'll give you the standard Microsoft web fonts.  Even then, I have to admit that the Google search page looks prettier in IE7 than Firefox.  Also have a play with System | Preferences | Font.

---

### Post by jamesford on 2007-06-24
[[img]http://bildr.no/thumb/80007.jpeg[/img]](http://bildr.no/view/80007)

these font settings suit me

---

### Post by crjackson on 2007-06-24
Where do I find that settings menu and I'll give yours a shot...

---

### Post by crjackson on 2007-06-24
Okay, I found it and made the changes.  We'll see how this works out...  Thanks.

---

### Post by Cappy on 2007-06-24
Don't forget to change your preferences in (System-->Preferences-->Font) too. If you're using a LCD you should use "Subpixel smoothing (LCDs)" and on the "Details .." button, pick whatever looks best (I use Smoothing: Subpixel LCDs and Hinting: Full).

---

### Post by crjackson on 2007-06-24
> **Cappy said:**
> Don't forget to change your preferences in (System-->Preferences-->Font) too. If you're using a LCD you should use "Subpixel smoothing (LCDs)" and on the "Details .." button, pick whatever looks best (I use Smoothing: Subpixel LCDs and Hinting: Full).

I changed everything and rebooted.  The settings held, but they didn't seem to take effect.  Nothing seems to have changed.

---

### Post by Cappy on 2007-06-24
They take effect as soon as you click on one of the boxes. You don't even need to click "apply" or anything so that you can test each one. This dramatically improved the fonts for me =(

---

### Post by michaelzap on 2007-06-24
You also may want to change the default font in Firefox (Edit -> Preferences -> Content -> Fonts & Colors). I think that Google just uses your browser's default font instead of specifying one. I found that making my default Firefox font Sans-Serif and 16 points made a number of pages more readable (more like they are on IE in Windows).

---

### Post by Kilz on 2007-06-24
> **crjackson said:**
> Has anyone else noticed that the default fonts and page views aren't exactly easy on the eyes?

Take the google home page for instance.  Using IE, it has a nice crisp look.  The search box has an even thin line around it and everything looks in place and easy to read.

In Firefox the sides of the box and the top of the box carry a thick bold line while the bottom has no line at all.  It's the same on on web combo box's as well.

The pages in IE have sharp clear text of adequate size for reading on my 19" monitor at 1024x768.  In fire fox, the fonts seem much smaller and very think.  System fonts seem to mostly follow the same pattern.

How can I get my pages and system to be a little more friendly on my eyes?  I do go into the  Firefox View menu and change the text size (or use the ctrl +) so that it's more readable, but this is a band aide.

Any ideas how to change this?

TIA

Select fonts in the Preferences > Content tab > Fonts section > Click Advanced button. This will set the default fonts to your preferences.

---

### Post by crjackson on 2007-06-24
> **Kilz said:**
> Select fonts in the Preferences > Content tab > Fonts section > Click Advanced button. This will set the default fonts to your preferences.

I got things to change but damn it seems the fonts just aren't doing it for me, they just aren't crisp and clear...  Thanks for the help... I give up...

---

### Post by oldlucky on 2007-06-25
I have had trouble with fonts in Linux in the past "mostly blurry fonts" , i have played around with them for many months until i stumbled across the settings i use now.

Here is my little recipe i use .

First i install msttcorefonts , gsfonts , gsfonts-other and gsfonts-x11.

Then i setup my fonts as follows

[http://img181.imageshack.us/my.php?image=screenshot1fontpreferenpo2.png](http://img181.imageshack.us/my.php?image=screenshot1fontpreferenpo2.png)

and

[http://img131.imageshack.us/my.php?image=screenshotfont2renderinhi4.png](http://img131.imageshack.us/my.php?image=screenshotfont2renderinhi4.png)


then in Firefox i set them up like this

[http://img405.imageshack.us/my.php?image=screenshot3firefoxprefezi0.png](http://img405.imageshack.us/my.php?image=screenshot3firefoxprefezi0.png)

and this

[http://img131.imageshack.us/my.php?image=screenshot4fontsna4.png](http://img131.imageshack.us/my.php?image=screenshot4fontsna4.png)

This fixed my font problem as well as my sore eye's , as you can see from the screen shots the fonts are crystal clear and easy on the eye's.



edit: I posted this over at the debian forums some months ago and i still use these settings , it makes the fonts look crisp and clean on my computers using lcd monitors.



Hope it helps.

---

### Post by crjackson on 2007-06-25
> **oldlucky said:**
> I have had trouble with fonts in Linux in the past "mostly blurry fonts" , i have played around with them for many months until i stumbled across the settings i use now.

Here is my little recipe i use .

First i install msttcorefonts , gsfonts , gsfonts-other and gsfonts-x11.

Then i setup my fonts as follows

[http://img181.imageshack.us/my.php?image=screenshot1fontpreferenpo2.png](http://img181.imageshack.us/my.php?image=screenshot1fontpreferenpo2.png)

and

[http://img131.imageshack.us/my.php?image=screenshotfont2renderinhi4.png](http://img131.imageshack.us/my.php?image=screenshotfont2renderinhi4.png)


then in Firefox i set them up like this

[http://img405.imageshack.us/my.php?image=screenshot3firefoxprefezi0.png](http://img405.imageshack.us/my.php?image=screenshot3firefoxprefezi0.png)

and this

[http://img131.imageshack.us/my.php?image=screenshot4fontsna4.png](http://img131.imageshack.us/my.php?image=screenshot4fontsna4.png)

This fixed my font problem as well as my sore eye's , as you can see from the screen shots the fonts are crystal clear and easy on the eye's.



edit: I posted this over at the debian forums some months ago and i still use these settings , it makes the fonts look crisp and clean on my computers using lcd monitors.



Hope it helps.

I'm at work right now so I haven't had a chance to try your solution.  I'm confident it will help and I'll post back after I've applied the changes.

Thank you for your assistance.

---

### Post by crjackson on 2007-06-25
> **oldlucky said:**
> Here is my little recipe i use .

First i install msttcorefonts , gsfonts , gsfonts-other and gsfonts-x11.


Do I install these using synaptic or some other method?

---

### Post by oldlucky on 2007-06-25
> **crjackson said:**
> Do I install these using synaptic or some other method?

Yes you can install these by synaptic or just open up a terminal and run

sudo apt-get install msttcorefonts gsfonts gsfonts-other gsfonts- x11

cheers

---

### Post by crjackson on 2007-06-25
> **oldlucky said:**
> Yes you can install these by synaptic or just open up a terminal and run

sudo apt-get install msttcorefonts gsfonts gsfonts-other gsfonts- x11

cheers

Thank you.  If this works out it shoud be a sticky.

---

### Post by crjackson on 2007-06-26
It's much better. I did have to exit firefox and re launch it before the changes took place on the web pages.  I know it was supposed to happen like instantly, but it didn't.  Restarting the browser after the settings change made a big difference.

I did have to use the CTRL+ to make it larger though, but I can live with that...

Thanks...

---

### Post by oldlucky on 2007-06-26
Yes i forgot to mention that x should be restarted after making the changes...it makes a big difference and you should see an improvement again.

cheers

edit : you may have to play around with the sizes to get it right for your desktop i use a 1280x1024 resolution and the font sizes work well with my setup.

---

### Post by crjackson on 2007-06-26
> **oldlucky said:**
> Yes i forgot to mention that x should be restarted after making the changes...it makes a big difference and you should see an improvement again.

cheers

edit : you may have to play around with the sizes to get it right for your desktop i use a 1280x1024 resolution and the font sizes work well with my setup.

Actually, I'm pretty happy now.  Things are feeling more in place.

---

### Post by Buendia on 2007-06-27
I have a question:

If this font is not comfortable for your eyes, are they okay for the developers or anyone else who choose this setting for this linux distro?

Whenever I install a new linux, I have to spend a stupid time to fine-tune it, and at the end of the day I usually delete the whole thing and go back to the god-damn-windows again. Then wait a few months or a year and do the same thing and find out that linux is still the same bla-bla and delete it and go back to the god-damn-windows again.

I know that this is open source and does not have billy the gates to support it and this and that. but, all of these are not even close to good excuses to embed eye-soring fonts in the official release. I really want to know what is the font of the developers.

(1) They use the same eye-soring fonts, which doesn't make sense. I mean, apart from being uncomfortable, they are ugly too!

(2) Their system is different to the official release, that is, they fine tune it for themselves, which doesn't make sense too.

There is billy there with his nice-looking-outside crap-being-inside thing he calls it windows which is more than good enough for loads of people to use. Even if they don't want to pay, they can always download it from somewhere. You cannot expect people to come to your amateurish-looking system when there is this ergonomic windows out there.

Most of people do not care that linux has such and such history and such and such stability and such and such virus-free-env and that windows is crap in such and such ways. Most of people just want to browse the internet and play streaming media and create a word document.

---

### Post by FrancoNero on 2007-06-28
and not get eye cancer in firefox and openoffice :-)
yeah that fonts issue is really a bummer.... time to have that fixed once and for all in Gutsy, and checkboxes and such in firefox as well

---

### Post by voided3 on 2007-06-29
Very nice! I use a 19" widescreen LCD and I feel like i've been playing with fonts for ages. This worked out quite well. Thanks!

---

### Post by taisao on 2007-07-06
> **oldlucky said:**
> I have had trouble with fonts in Linux in the past "mostly blurry fonts" , i have played around with them for many months until i stumbled across the settings i use now.

Here is my little recipe i use .

First i install msttcorefonts , gsfonts , gsfonts-other and gsfonts-x11.

Then i setup my fonts as follows

[http://img181.imageshack.us/my.php?image=screenshot1fontpreferenpo2.png](http://img181.imageshack.us/my.php?image=screenshot1fontpreferenpo2.png)

and

[http://img131.imageshack.us/my.php?image=screenshotfont2renderinhi4.png](http://img131.imageshack.us/my.php?image=screenshotfont2renderinhi4.png)


then in Firefox i set them up like this

[http://img405.imageshack.us/my.php?image=screenshot3firefoxprefezi0.png](http://img405.imageshack.us/my.php?image=screenshot3firefoxprefezi0.png)

and this

[http://img131.imageshack.us/my.php?image=screenshot4fontsna4.png](http://img131.imageshack.us/my.php?image=screenshot4fontsna4.png)

This fixed my font problem as well as my sore eye's , as you can see from the screen shots the fonts are crystal clear and easy on the eye's.



edit: I posted this over at the debian forums some months ago and i still use these settings , it makes the fonts look crisp and clean on my computers using lcd monitors.



Hope it helps.

thank you,

Using Subpixel smoothing (setup in image 1)
and subpixel (lcds) smoothing and full hinting (setup in image 2) looks nicer for me. I, who like cleartype from ms winxp.

and for more eyecandy setup for firefox: [http://ubuntuforums.org/showthread.php?t=369596](http://ubuntuforums.org/showthread.php?t=369596) ( Firefox Widgets) ;)

---

### Post by oldlucky on 2007-07-06
Great :D I am glad someone has had some benefit from the settings...you may have to play around a little to get it to your liking but overall they work good for me and hopefully they will help others achieve a crisper clearer looking desktop.

oldlucky

---

### Post by crjackson on 2007-07-06
> **oldlucky said:**
> Great :D I am glad someone has had some benefit from the settings...you may have to play around a little to get it to your liking but overall they work good for me and hopefully they will help others achieve a crisper clearer looking desktop.

oldlucky

@oldlucky,

They worked ou t good for me too.  Thanks.

---

### Post by ScottC2105 on 2007-07-24
> **oldlucky said:**
> I have had trouble with fonts in Linux in the past "mostly blurry fonts" , i have played around with them for many months until i stumbled across the settings i use now.

Here is my little recipe i use .

First i install msttcorefonts , gsfonts , gsfonts-other and gsfonts-x11.

Then i setup my fonts as follows

[http://img181.imageshack.us/my.php?image=screenshot1fontpreferenpo2.png](http://img181.imageshack.us/my.php?image=screenshot1fontpreferenpo2.png)

and

[http://img131.imageshack.us/my.php?image=screenshotfont2renderinhi4.png](http://img131.imageshack.us/my.php?image=screenshotfont2renderinhi4.png)


then in Firefox i set them up like this

[http://img405.imageshack.us/my.php?image=screenshot3firefoxprefezi0.png](http://img405.imageshack.us/my.php?image=screenshot3firefoxprefezi0.png)

and this

[http://img131.imageshack.us/my.php?image=screenshot4fontsna4.png](http://img131.imageshack.us/my.php?image=screenshot4fontsna4.png)

This fixed my font problem as well as my sore eye's , as you can see from the screen shots the fonts are crystal clear and easy on the eye's.



edit: I posted this over at the debian forums some months ago and i still use these settings , it makes the fonts look crisp and clean on my computers using lcd monitors.



Hope it helps.

Thank you very much, Ubuntu is now easy on the eyes on my LCD :).

---

### Post by Musky Melon on 2007-11-12
The problem extends beyond the fonts which still don't look nearly as good as Microsoft's with ClearType. I need to be able to increase sharpness and slightly scale the the font weight. I can't do that Ubuntu at the moment. I can make the fonts sharp but not slightly bolder. This makes a huge difference when you are on a 24" monitor. Everything is a bit blurrier in Ubuntu including the fine lines around boxes and whatnot. I find Windows to be less strenuous on my eyes. Any suggestions?

---

### Post by soho324 on 2008-06-25
Beautiful fix. Thanks!!!!!

---

