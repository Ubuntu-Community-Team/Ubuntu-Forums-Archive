---
title: "Photoshop CS2 Wine 1.4 (Ubuntu 12.04)"
date: 2012-05-10
forum: Wine
---

### Post by cbanakis on 2012-05-10
So, I have been using Wine for quite some time, and it has been good to me.

I had MS Office 2007, and Photoshop CS2 working flawlessly running Ubuntu 11.10 with Wine 1.3.

I recently did a clean install of Ubuntu 12.04, and Wine 1.4 (Also Tried 1.5)

Originally, I did not need to do anything special.
Office and Photoshop just installed, and ran the same as it would on windows.

But now when I install Photoshop, everything works the same, until I try to open it.

Installation works, but launching the program results in
"an error has been detected with a required application library and the product cannot continue. Please reinstall the application"

I have tried everything I can think of, and I spent a while on google.

Apparently, this was a big issue a long time ago, because I found plenty of very old threads referring to the same problem, but none of the solutions are working for me.

Any thoughts?  Ideas?  Solutions?

Thanks for any help

---

### Post by cbanakis on 2012-05-10
I did install Office 2010 without any issues.

So if anyone was wondering, it seems to work perfect.

However, it looks like whatever was done to make office 2010 work, made photoshop cs2, NOT work.

Hopefully, I or someone else will soon find a fix for this.

---

### Post by cbanakis on 2012-05-10
Figured out a solution.

It seems to work fine when I launch in terminal via
```
wine '/home/chris/.wine/drive_c/Program Files/Adobe/Adobe Photoshop CS2/Photoshop.exe' 
```

So for a permanent fix, I just created a custom launcher, using that as the command.

Thanks for listening.

---

### Post by pablo180 on 2012-06-13
Thanks this helped me a lot. I had the same problem with the same pieces of software (Adobe Photoshop CS2, Wine 1.4 and Ubuntu 12.04). 

I wasn't getting the same error message but other odd (and old ones) such as:

“Could not complete request because of a program error” 

“Could not complete request as there is not enough RAM available”

“Adobe Photoshop CS2 has encountered a problem...”

The latter one resulting in the program exiting at the most inopportune times. I remember having these errors years ago when I first installed, but have been running CS2 flawlessly ever since. 

I hadn't installed any new Wine programs, I hadn't tinkered with any settings or anything and it was working OK up until a couple of weeks ago, so I am not sure what caused the above problems but they only started recently. 

I took your advice and tried from the terminal; Photoshop CS2 ran without any problems so I just created a launcher and all seems to be well again!

Thanks again.

---

