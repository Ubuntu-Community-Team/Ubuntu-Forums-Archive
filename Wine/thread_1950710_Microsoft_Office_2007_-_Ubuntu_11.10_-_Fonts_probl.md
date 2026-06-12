---
title: "Microsoft Office 2007 - Ubuntu 11.10 - Fonts problem"
date: 2012-04-01
forum: Wine
---

### Post by alves93 on 2012-04-01
Hi everyone!
I've installed MS Office through Wine, everything went well, the only problem is that the words are a little weird, does anyone have this problem too?

Thanks!

---

### Post by pratikk on 2012-04-01
Experienced something similar, though with another package, not Office. It was resolved by installing fonts from the Win machine where that package used to run.

---

### Post by Elfy on 2012-04-01
*Thread moved to **Wine**.*

---

### Post by alves93 on 2012-04-01
How do I do that exactly?
Thanks! :)

---

### Post by pratikk on 2012-04-01
Copy the fonts you use to the Ubuntu machine. Double-click on each. The font will be displayed and you will see an install button. 

Command line method: Copy the fonts to /usr/share/fonts. Or make a new directory in this folder and copy into that, to keep the win fonts separate. That's neater, and helpful if you have to replicate this process on another machine.

Then run sudo fc-cache -f -v to refresh the font cache. You will be prompted for your password. You may have to close and restart Office for the fonts to be available and show up in the font options box.

Hope that helps

Pratik

---

### Post by forrestcupp on 2012-04-02
The easy way is to go to your user's /home folder and create a folder named **.fonts**. Then on your Windows partition, go to **C:\Windows\Fonts** and copy all of the fonts in that folder with the **.ttf** extension. Then paste them all into the .fonts folder you created in your /home folder. After you do that, you'll be able to use those fonts in anything in Ubuntu. You can even change your system fonts to be something like SegoeUI, like Windows uses.

If you do this, sometimes it helps to delete all of your Wine installed fonts to force Wine to use the fonts you just copied over. You can find these in your Wine folder in your user's /home folder: ~/.wine/drive_c/windows/Fonts. You can delete any fonts in this folder as long as you have copied the fonts to your .fonts folder, like I described earlier.

---

### Post by pratikk on 2012-04-02
Absolutely true, Forrest, but:
1. Fonts installed in /usr/share/fonts are accessible to all users, while an installation in the home folder is accessible to only one user. 
2. As a publisher in print and on the web, I've found that 9 out of 10 fonts in the win\fonts folder are never used. They just clog the system, and any system they're installed to. So it may be a good idea to transfer the ones you actually use, rather than all. 

Your suggestion to delete old Wine fonts is a good idea. That foxed me for a while using QuarkXpress. Some fonts looked funny because the old ones were being used. At the time, I uninstalled and reinstalled all my routine fonts and it was solved.

---

### Post by alves93 on 2012-04-02
Thanks for the help, but the fonts are weird still. It's funny because if I choose a bigger font (font size: 36 e.g) it is most likely the fonts in windows. The bigger they are, the most they look like the original fonts in windows...

---

### Post by pratikk on 2012-04-02
I could be wrong, but I think you have a font smoothing problem and better eyes than mine. Or maybe I no longer care about fonts under 72 pts. The solution is at [http://ubuntuforums.org/showthread.php?p=16896](http://ubuntuforums.org/showthread.php?p=16896). Take a gander, maybe it's what you miss.

---

