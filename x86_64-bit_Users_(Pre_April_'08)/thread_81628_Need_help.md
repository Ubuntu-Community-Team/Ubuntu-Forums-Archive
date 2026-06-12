---
title: "Need help"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sophotect on 2005-10-24
hello, i am completely new to this. i downloaded the ubuntu5.10 for amd64 but i dont know how and what to burn on cd. i am running windows x64

any help is appreciated!!!

---

### Post by Leigh on 2005-10-24
You need to get some software that can burn an ISO image to a CD. If you have a CD writer in your computer you probably have already got the software necessary, it's usually Nero. Failing that you can download a free versions of CD burning software from the Internet. One I have used very successfully is available [here]("http://www.cdburnerxp.se/index.php") assuming your current operating system is Windows XP.

Install the software, then from the menu choose **File, Write disc from ISO file..**. Navigate you way to where you have the Ubuntu ISO file. Ensure you check the "Finalize Disc" option or the CD won't boot. Now click "Write Disc"

Hopefully you'll have a bootable Ubuntu CD.

---

### Post by cstudent on 2005-10-24
You're going to need a program like Nero ([www.nero.com](www.nero.com)) or equivalent to burn the .iso file to a CD. Which you will then use to install ubuntu by booting up the computer you plan to install to from the CD. You could google for a free .iso burner for Windows. I found this link, but I don't know if it will work with 64.

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)


Bill

---

### Post by Sophotect on 2005-10-24
thanks guys but i have one more question. when i downloaded ubuntu-5.10-install-amd64.iso, i got many files and folders instead of one iso image. do i just burn all those files and folders or am i supposed to download something else?

---

### Post by DancingSun on 2005-10-25
[QUOTE=Sophotect]thanks guys but i have one more question. when i downloaded ubuntu-5.10-install-amd64.iso, i got many files and folders instead of one iso image. do i just burn all those files and folders or am i supposed to download something else?[/QUOTE]
That's odd, I downloaded my ISO from bittorrent and I got only 1 file.  I just tried clicking on the dowload link from the Ubuntu website, and I only got 1 file as well...

In anycase, you should only need the ISO file.  The file you should be looking for to burn to the CD is the file that you mentioned: "ubuntu-5.10-install-amd64.iso".

---

### Post by Leigh on 2005-10-25
The numerous files and folders should be **inside** the .ISO image, so you should have ONLY one file, the .ISO file.

---

### Post by Sophotect on 2005-10-25
i downloaded several iso images from different mirrors but all i get is a winrar archive. it does not make sense. the file is .iso but my burning software does not see it. does this have anything to do with the fact that i am running windows xp x64? i am just lost. is there a way to install ubuntu without burning the iso image?

---

### Post by Leigh on 2005-10-25
ISO files appear as WinRAR archives because WinRAR can see inside the ISO, so you willl see several files and folders. Don't extract any of the files or folders, leave them intact inside the ISO. It sounds like you have the correct file, though, judging by what you've written so far.

What CD burning software are you using? Also, are you sure you are navigating to where you downloaded the ISO when you use the burning software? When I downloaded the ISO I stored it on my "Desktop". That way it was easy to find when I burnt it to CD.

---

### Post by zekolas on 2005-10-25
Ok, you really just have one ISO file, what is kind of like a zip file. Winrar can "see" into the iso file at all the individual files, just like winrar can browse a zip file, even though it is only one file.

If you open up windows explorer and go to tools>>folder options their should be two options, one that says "hide file extentions for known file types" and one that says "show file extentions" put the dot into show file extentions and you will see the .iso file extention.

check this link out
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
follow the directions, it will have you download iso recorder and show you how to burn the cd imaga.

---

### Post by Sophotect on 2005-10-25
Yes! I got ubuntu working. Thank you guys for your awesome help.

---

