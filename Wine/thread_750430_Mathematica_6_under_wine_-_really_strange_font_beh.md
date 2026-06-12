---
title: "Mathematica 6 under wine - really strange font behavior"
date: 2008-04-09
forum: Wine
---

### Post by noahsark1126 on 2008-04-09
There seems to be an issue with the display of certain fonts in Mathematica 6.  The best examples are 

1. The horizontal line to indicate a over b, which is printed as an absurdly thick black bar with the numerator and denominator way too far above and below it

2. The == sign, which is used often for equation solving and such.  This doesn't even display a character, it's just a box.

See the screenshot for what I'm talking about.  The result of the first integral is supposed to be x^3/3, and the cosine of that angle is 1/sqrt2.  You can also see the missing == in the equation.

Can someone help?  This isn't a big deal for small things like this...I can still figure out what it says.  But for more complicated results, it becomes impossible to see what's going on.

I'm running Hardy beta with an ATI card and compiz.  The reason I'm using wine is because the linux version of mathematica had even worse fonts than this - in fact, they weren't even visible, they were just little unreadable black dots.  Perhaps this indicates a problem with my system overall?

---

### Post by happyhamster on 2008-04-09
- Try installing the windows truetype fonts:

sudo apt-get install msttcorefonts

- If that didn't help, take a look at:
[http://support.wolfram.com/mathematica/systems/windows/general/latestfonts.html](http://support.wolfram.com/mathematica/systems/windows/general/latestfonts.html)

Good luck.

---

### Post by jjk7288 on 2008-04-09
Why don't you just use the native Linux version? If you have a license already you should be able to just download the Linux copy of it.

---

### Post by noahsark1126 on 2008-04-09
msttcorefonts is already installed...I also downloaded the latest fonts from wolfram, with no improvement.

Also, @ jjk, I have tried the Linux version as I said in the first post.  Because of some problem with compiz or motif, the fonts were even less readable than under wine.

Any other ideas?

---

### Post by noahsark1126 on 2008-04-09
More possibly useful info:

I have the exact same program installed on my actual Windows XP partition.  It runs perfectly under native windows.  So I tried to run that version under wine, instead of the version in ~/.wine/drive_c.  The exact same thing happened.  This seems to indicate that the problem is not a missing font, but rather a problem with the rendering of a font.  I think...

---

### Post by jjk7288 on 2008-04-09
> **noahsark1126 said:**
> msttcorefonts is already installed...I also downloaded the latest fonts from wolfram, with no improvement.

Also, @ jjk, I have tried the Linux version as I said in the first post.  Because of some problem with compiz or motif, the fonts were even less readable than under wine.

Any other ideas?

And you think that by running Mathematica under Wine, this would somehow fix a problem with Compiz?

Both Wine and Compiz are beta (read: not bug free) and you shouldn't go around looking to fix Mathematica when the problem probably derives from the use of one of these programs (or possibly Motif, but I don't know much about that).

What's to keep you from disabling Compiz at least while using Mathematica? If that fixes the problem, then you know that it's Compiz (and that there's probably not much more you can do than submit a bug report)

---

### Post by noahsark1126 on 2008-04-10
> **jjk7288 said:**
> And you think that by running Mathematica under Wine, this would somehow fix a problem with Compiz?

Both Wine and Compiz are beta (read: not bug free) and you shouldn't go around looking to fix Mathematica when the problem probably derives from the use of one of these programs (or possibly Motif, but I don't know much about that).

What's to keep you from disabling Compiz at least while using Mathematica? If that fixes the problem, then you know that it's Compiz (and that there's probably not much more you can do than submit a bug report)

I am quite aware that Wine and Compiz are beta versions and by no means perfect.  But this doesn't mean by any stretch that I am simply going to give up on an issue and say "oh well, it's not even version 1.0, it's bound to mess up sometimes."  If I did, I would still be using Windows.  So yes, I disagree - I think I absolutely should go around trying to fix Mathematica.

I decided to try Mathematica under Wine because the native motif version did not work in the slightest, and I have read that it works well with Wine.  Indeed, it does come much closer to doing the job, so I figured I would stick with the Wine version and try to fix those issues.

I will certainly try running Mathematica with metacity as opposed to compiz, but it would also be much more ideal to not have to do that, since temporarily running metacity has the unfortunate side effect of placing every single window on workspace 1.

---

### Post by noahsark1126 on 2008-04-10
Update:  Definitely not a Compiz problem.  Tried running with metacity and got the exact same effect.

---

### Post by schtufbox on 2008-04-10
Which fonts does it use anyway? could be one not included in the msttcorefonts package, like tahoma or something.

---

### Post by noahsark1126 on 2008-04-10
> **schtufbox said:**
> Which fonts does it use anyway? could be one not included in the msttcorefonts package, like tahoma or something.

It uses Courier New, which is in msttcorefonts.

---

### Post by schtufbox on 2008-04-11
> **noahsark1126 said:**
> It uses Courier New, which is in msttcorefonts.

Just a thought, have you tried also copying the Courier New ttf to the windows folder in wine as well? can't hurt to try :)

---

### Post by noahsark1126 on 2008-04-11
Yes I did try that actually.  Regular characters seem to be rendered normally...the problem is some special characters like the "over" sign or the "==" sign.

---

### Post by Quicksilver_Johny on 2008-09-26
I've been having the exact same problem running mathematica under wine, everything works fine except for the division bar, the == character, and maybe 1 or two other very special characters.
Mainly it's just an annoyance, but I'd like to know if anyone finds a solution.

---

### Post by Tanis Shadow on 2008-12-22
Hi there,

I don't know if anyone is still interested but still here is my solution to the problem.
1. start Mathematica 6 in Linux
2. go to Edit -> Preferences -> Advanced
3. use the button Open Option Inspector (a new window should open)
4. on the left side go to Formatting Options -> Font Options -> Font Properties
5. set "FontMonospaced" to "False" (should be on "Automatic" by default)

That should solve it, at least it worked for me

Good Luck

---

### Post by ghaspias on 2009-01-05
I am using Mathematica 5 under XCM (Linux Caixa Mágica - a Mandriva-based portuguese distro), running via wine. Have lots of problems with fonts - no readable text in the notebook and some dialogs (preferences). The tip above helped, but also
```
PrivateFontOptions->{"WindowsUseTrueTypeNames"->False}
```
(check ~/.wine/drive_c/windows/profiles/%username%/Application Data/Mathematica/FrontEnd/init.m).
Still, not usable, altough some text in notebook is readable.
I will try on Ubuntu 8.10 (Intrepid) soon.

---

### Post by skintythe1andonly on 2009-01-06
I had this problem with the fonts in mathematica 6 for linux, i found a solution at 

[http://www.walkingrandomly.com/?p=112]("http://www.walkingrandomly.com/?p=112")

They say this is fixed for version 6.03.

I have just installed mathematica 7, and there seems to be some issues with the fonts again, but nothing near the problems i had with 6

---

### Post by DavidNoahG on 2009-10-05
> **happyhamster said:**
> - Try installing the windows truetype fonts:

sudo apt-get install msttcorefonts

- If that didn't help, take a look at:
[http://support.wolfram.com/mathematica/systems/windows/general/latestfonts.html](http://support.wolfram.com/mathematica/systems/windows/general/latestfonts.html)

Good luck.


Thank you sooooo much Happy Hamster!  I had the same problem (fonts not rendering in Mathematica via Wine) and "sudo apt-get install msttcorefonts" fixed the problem.

As far as the "why," I'm sure a lot of people asked Newton and many other luminaries and artists that same question, and it did not stop them.  The benefits to a multitude of inquiries seem obvious to us now, but these things may not have exhibited use or value until time long passed after experimentation and conception.

---

### Post by DavidNoahG on 2009-10-06
I spoke too soon.  After installation, all I got was garbage.  After installing mttscorefont package, I was able to make sense of what I was seeing, which is when I made my first post here.  But then I noticed a few boxes here and there, in place of things such as the diving symbol.

Did some research, and it turns out to be a little more complicated.  But I learned a lot.  I now have Mathematica fonts in Open Office!  lol  Perhaps one day they will be of use.

I'm still working on it, though.  Here are the pieces that I'm working with:  First, you will find that there is a fonts directory in the Mathematica installation folder:

~/.wine/drive_c/Program Files/Wolfram Research/Mathematica/6.0/SystemFiles/Fonts

Then you will need to learn about FontConfig:

[http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html](http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html)
[http://www.openfontlibrary.org/wiki/FontConfig](http://www.openfontlibrary.org/wiki/FontConfig)

Let me know what you find out.

---

### Post by noravanq on 2010-02-24
Thanks a lot. This worked for me. I had incomprehensible text, but after doing this everything looks fine.

> **Tanis Shadow said:**
> Hi there,

I don't know if anyone is still interested but still here is my solution to the problem.
1. start Mathematica 6 in Linux
2. go to Edit -> Preferences -> Advanced
3. use the button Open Option Inspector (a new window should open)
4. on the left side go to Formatting Options -> Font Options -> Font Properties
5. set "FontMonospaced" to "False" (should be on "Automatic" by default)

That should solve it, at least it worked for me

Good Luck

---

