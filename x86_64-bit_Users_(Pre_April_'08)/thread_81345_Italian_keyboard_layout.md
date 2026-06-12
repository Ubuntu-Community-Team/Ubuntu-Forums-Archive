---
title: "Italian keyboard layout"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Leonida on 2005-10-24
How can I set up Italian Kayboard layout.
I set up layout: Italian and Keyboard Model: Generic 104, but all symbols are messed up.
It work fine with 5.04.
I did the same as [here]("http://ubuntuforums.org/showpost.php?p=76697&postcount=5"), but now don-t work.

Edit: I-ve also try different options, generic 105 and 101, but same problem.

---

### Post by Rxke on 2005-10-24
in System ->Preference->Keyboard, go to the layout where you choose language, and select keyboardmodel as: 
 "Macintosh" (and if not working, try "Macintosh old") instead of generic 104,5 etc etc...

---

### Post by Leonida on 2005-10-24
[QUOTE=Rxke]in System ->Preference->Keyboard, go to the layout where you choose language, and select keyboardmodel as: 
 "Macintosh" (and if not working, try "Macintosh old") instead of generic 104,5 etc etc...[/QUOTE]
Thanks, I've tryed before also Mac and Mac old, but problem still remain.

Have I to restart gnome to see changes?

---

### Post by Rxke on 2005-10-24
weird.

you could try to restart Gnome, but i doubt it will change anything.

---

### Post by Leonida on 2005-10-27
Today I had to reinstall all. I start installing 5.04 and I set Italian keyboard with no problem:
Desktop->Preferences->Keyboard, on Layouts tab I selected:
* Keyboard model: Generic 101-key PC
 * Selected layouts: Italian

All caracters on keyboard layout are typed correctly.

Then I **apt-get dist-upgrade** to 5.10, and my keyboard layout is now wrong!!!! :cry: :cry:

Is it a bug?

---

### Post by Leonida on 2005-10-29
[QUOTE=Leonida]Is it a bug?[/QUOTE]
I solved, but in a strange way. From a clean install of 5.10 I can set my Italian keyboard _only_ when I also add "PC-98xx Series"!!!.
When I select my correct layout window themes strangely blink from brown ubuntu to blu traditional!!!
Watch to believe, I did a [little screenmovie]("http://www.freesmug.org/usex/index.php?/archives/18-Italian-keyboard.html") to show what happen to me:

P.S. [OT] Please support [Istambul]("http://live.gnome.org/Istanbul") developer to[ improve]("http://www.freesmug.org/usex/index.php?/archives/17-Instanbul-test.html") his screenrecord application.

---

