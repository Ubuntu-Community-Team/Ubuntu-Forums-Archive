---
title: "&quot;WINE is not owned by you&quot;"
date: 2015-03-14
forum: Wine
---

### Post by mdavis1231 on 2015-03-14
I have a program called "Visual Link Spanish" which requires me to install it in WINE as "sudo", otherwise it won't let me click on the buttons that I need to in order to install the program.  I used to be able to do this until WINE updated to the latest version.  Now, when I try and install "Visual Link Spanish" under "sudo", I get the error message "WINE is not owned by you".  Is there any way for me to take ownership of WINE so that I can install this program as "sudo", or has WINE simply made this impossible now?  If they have, then I can't install my "Visual Link Spanish" on my Ubuntu 14.04 LTS Trusty Tahr. ](*,)

Please let me clarify up front that I do not completely run WINE as "sudo", I only HAVE to install this one program as "sudo".  Like I said before, otherwise for some reason it won't let me click on the buttons needed to install the program to WINE.

---

### Post by mdavis1231 on 2015-03-14
I actually FOUND the answer  after almost 2 complete days of searching.  Instead of making the setup.exe file executable by using chmod a+x, you have to use chmod +rwxrwxrwx /path/to/file.extension.  Then it allows you to take COMPLETE control of the setup.exe file, and you can install it without having to install as "root".  It will then allow you to click on the buttons and install the application.  WOO HOO!!!

---

### Post by Bucky Ball on 2015-03-14
Great news. Please mark the thread as solved as your efforts might save someone else two days of searching (see second link in my sig for how). ;)

---

