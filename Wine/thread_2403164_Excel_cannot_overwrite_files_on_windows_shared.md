---
title: "Excel cannot overwrite files on windows shared"
date: 2018-10-08
forum: Wine
---

### Post by jojit on 2018-10-08
Hi all.

Hope someone can advise me what went wrong. I am using crossover trial together with MS office 2016. I am on Ubuntu 16.04 LTS. My Ubuntu is joined to an AD domain and I've mapped some Windows shared folders. There are a variety of files such as xlxs, docx, txt, etc in those Windows shares. I have no problem accessing any of those files.

When I made changes to xlxs and docx files, opening them in Excel and Word respectively, I was unable to save and overwrite the file I was working on. I can do a "save as" in the same directory, I can delete original file as well, so I have RW access. I can work on the txt files and overwrite the originals. Can anyone advise why MS office files can't be overwritten in these Windows shares but txt can? MS office files in local directories have no problem.

JJ

---

### Post by Claus7 on 2018-10-09
Hello,

since you are able to do save as: can you overwrite the files in question in such a way? If this is the case I would advice you to choose different versions of your programs.

EDIT: I would also advice you to open your programs via command line and check if any message is posted while you are pressing the save button: that way maybe you will be able to track down the problem.

EDIT2: Also check this: [https://ubuntuforums.org/showthread.php?t=951424](https://ubuntuforums.org/showthread.php?t=951424) (even though is pp related)
ah! And welcome to the forums!

Regards!

---

### Post by jojit on 2018-10-19
Hi @claus7

Yes, I can do a save as into the same directory but with a different filename. It doesn't allow overwriting the original file. How do I open a commandline in Ubuntu to startup MS excel for example?

JJ

> **Claus7 said:**
> Hello,

since you are able to do save as: can you overwrite the files in question in such a way? If this is the case I would advice you to choose different versions of your programs.

EDIT: I would also advice you to open your programs via command line and check if any message is posted while you are pressing the save button: that way maybe you will be able to track down the problem.

EDIT2: Also check this: [https://ubuntuforums.org/showthread.php?t=951424](https://ubuntuforums.org/showthread.php?t=951424) (even though is pp related)
ah! And welcome to the forums!

Regards!

---

### Post by Claus7 on 2018-10-19
Hello,

you could check this out, since it seems to face the same problem as you do: [https://www.codeweavers.com/support/forums/general/?t=26;forumcurPos=450;msg=163396](https://www.codeweavers.com/support/forums/general/?t=26;forumcurPos=450;msg=163396)

as it is mentioned it has to do with permission issues. The command proposed might work. You can check it out. Also, if you write click on an application, don't you have the option to run it under terminal?

Regards!

---

### Post by jojit on 2018-10-19
If I change permissions, will that change affect other users who need to access them through Windows OS?

I have an AD environment here and most of the users access a Windows fileserver using Windows OS.

** then again.. I think it doesn't work. I tried saving new files from Ubuntu to the Windows shared folder but couldn't overwrite changes to them as well.

JJ

> **Claus7 said:**
> Hello,

you could check this out, since it seems to face the same problem as you do: [https://www.codeweavers.com/support/forums/general/?t=26;forumcurPos=450;msg=163396](https://www.codeweavers.com/support/forums/general/?t=26;forumcurPos=450;msg=163396)

as it is mentioned it has to do with permission issues. The command proposed might work. You can check it out. Also, if you write click on an application, don't you have the option to run it under terminal?

Regards!

---

### Post by Claus7 on 2018-10-19
Hello,

so the solution does not work in new files: does it work in old files at least? In other words: can you create a new file, change permissions, and then try to overwrite it? Not a solution that you seek, yet it might be a workaround.

For the permission's change you could check also here:
[https://en.wikipedia.org/wiki/Chmod](https://en.wikipedia.org/wiki/Chmod)

Regards!

---

