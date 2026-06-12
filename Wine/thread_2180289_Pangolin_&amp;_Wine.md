---
title: "Pangolin &amp; Wine"
date: 2013-10-12
forum: Wine
---

### Post by czgirb on 2013-10-12
Now, I'm using **12.04** and **Wine 1.4** (showed in **Wine configuration**) and my questions is:

1. **Application > Wine > Programs** ... it showed there is **Sketchup 8** and **Sketchup 2013** installed.
--- When I browse **C:** drive, both **Program Files** and **usr** (**czgirb** and **Public**), I found no **Sketchup 8**. Where is it?

2. When I go to **Uninstall Wine Software**, in the list I see there are **TWO** items called **Wine Gecko (32-bit) 1.4** and **Wine Gecko (32-bit) 1.6**
--- Why?

3. I ever installed **Format Factory**, and it was uninstalled (and it do not showed in **Programs** and **Uninstall Wine Software** anymore)
--- But today, when I browse **C:** drive, I still saw the folder ... so, I manually delete the folder.
--- I wondering WHY the folder still shown in my **C:** drive? Any suggestion?

---

### Post by andreazzz on 2013-10-14
Sketchup is located in the Google-folder in Program Files;
Gecko is the GUI-shell for Wine (I thought it was) and it will be updates from time to time. Version 1.6 is the most recent version. I think Wine uses files both from 1.4 as well as from 1.6.
If you remove an application in Windows, the folder would not been deleted either.

Have fun with Sketchup!
offtopic: you might have more fun with Blender, which is native Linux. It is a lot harder to understand, but you can create many many more things. I switched myself 3 weeks ago.

---

### Post by czgirb on 2013-10-16
> **andreazzz said:**
> Sketchup is located in the Google-folder in Program Files
Sorry! In my Program Files contains **Foobar, Internet Explorer, Medieval, Rovio,** and **Sketchup 2013** only

> **andreazzz said:**
> 
Gecko is the GUI-shell for Wine (I thought it was) and it will be updates from time to time. Version 1.6 is the most recent version. I think Wine uses files both from 1.4 as well as from 1.6.
If you remove an application in Windows, the folder would not been deleted either.
Thank you for the explanation

---

### Post by andreazzz on 2013-10-16
Don't you have a Program Files x86 folder? Maybe it's located in there. But if you are able to start Sketchup 8, what's the problem? And why Sk8 and Sk2013?

---

### Post by czgirb on 2013-10-16
> **andreazzz said:**
> Don't you have a Program Files x86 folder? Maybe it's located in there.
What is "**Program Files x86**" folder?
I go to **Program Files** by using Wine's **browse C: drive** option.

 > **andreazzz said:**
> But if you are able to start Sketchup 8, what's the problem? And why Sk8 and Sk2013?
I uninstalled **Sketchup 8** before I installed **Sketchup 2013** ... it's about a month ago.
But now I found there is a **Sketchup 8's trace** left here ... and I want to clean it.

Please guide me ... thank you

---

### Post by andreazzz on 2013-10-17
Well, in 64-bit versions of Windows there is a X86 folder for program's that do not work with 64 bit, I thought it might be possible that such a folder exists in Wine too.

Well, it seems the "trace" you are talking about is only the shortcut in the Wine-Menu. Have you already deleted Sketchup through Wine Remove Programs (in Wine entry in Start-Menu)? 

You can find how right [here](http://askubuntu.com/questions/37320/how-do-i-remove-wine-program-entries-from-the-menu).

---

### Post by czgirb on 2013-10-18
> **andreazzz said:**
> Well, in 64-bit versions of Windows there is a X86 folder for program's that do not work with 64 bit, I thought it might be possible that such a folder exists in Wine too.

Well, it seems the "trace" you are talking about is only the shortcut in the Wine-Menu. Have you already deleted Sketchup through Wine Remove Programs (in Wine entry in Start-Menu)? 

You can find how right [here]("http://askubuntu.com/questions/37320/how-do-i-remove-wine-program-entries-from-the-menu").

Thank you for the guidance
Since I'm in Classic DE, **Edit Menu** > browse to **WINE** > and select **Sketchup 8**, and **DELETE** it ... and it disappeared.
Thank you for the guidance.
So, the thread is **SOLVED**.

---

