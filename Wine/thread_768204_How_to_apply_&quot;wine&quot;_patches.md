---
title: "How to apply &quot;wine&quot; patches?"
date: 2008-04-26
forum: Wine
---

### Post by Kosimo on 2008-04-26
In this winehq post, says: apply this patch. (Witch is a txt file)

[http://www.winehq.org/pipermail/wine-devel/2008-April/064425.html](http://www.winehq.org/pipermail/wine-devel/2008-April/064425.html)

Could you please tell me how can I apply this .txt file?
I'm trying to follow instructions in order to install iTunes.

Thank you in advance

---

### Post by ajmorris on 2008-04-26
hi there,
to apply a patch, you do:
patch <original file> <patch file>


AJ

---

### Post by Kosimo on 2008-04-26
> **ajmorris said:**
> hi there,
to apply a patch, you do:
patch <original file> <patch file>


AJ

Thanks for your answer-..  But I don't understand it :(


I've got a txt file,   then I do:  

```
laptop:~$ patch ipod_big.txt


```

And doesn't do anything



Instructions from winehq webpage are:

Instructions:
- Apply attached patch
- Get a clean wineprefix
- Set wine version to vista
- Download the installer from itunes.com, and install.
- wine net start ipod\ service
- run itunes
- Hopefully the ipod is detected now. Dapper might have a bug in hald
which case it won't detect any usb hard drive that's plugged in. sudo
killall hald; sudo hald; wineserver -k; wine net start ipod\ service
seems to work as workaround.


So, where do I have to apply this patch? I need to write a destination file?

Thank you again.

---

### Post by ajmorris on 2008-04-26
im not completely certain on the process of patching wine apps. However, i believe you need to apply that patch to your wine source code directly, and then compile wine yourself.

Unfortunately, i dont know how to/what to patch for that wine patch.
Standard convention is:
```
patch -p0 < ../patch_to_apply.diff

```Which uses a .diff patch file to patch the file in teh wine source for the same file name of the .diff patch. (-p0 tells it to do this) so in the above example, it would patch patch_to_apply in the source directory. It will probably be the same for the .txt file, but for that specific patch, i am unsure what file to patch.

if the .txt file contains information on what to patch, then doing ```
patch -p1 < /path/to/.txtfile
```

---

### Post by Kosimo on 2008-04-26
> **ajmorris said:**
> im not completely certain on the process of patching wine apps. However, i believe you need to apply that patch to your wine source code directly, and then compile wine yourself.

Unfortunately, i dont know how to/what to patch for that wine patch.
Standard convention is:
```
patch -p0 < ../patch_to_apply.diff

```Which uses a .diff patch file to patch the file in teh wine source for the same file name of the .diff patch. (-p0 tells it to do this) so in the above example, it would patch patch_to_apply in the source directory. It will probably be the same for the .txt file, but for that specific patch, i am unsure what file to patch.

if the .txt file contains information on what to patch, then doing ```
patch -p1 < /path/to/.txtfile
```

Hey, I guess that how you said this needs to be apply directly to the source code. I've installed wine from Hardy's repositories, so... I guess that I give up, I really don't know how to manage this.
Thank you anyway for your time and answers :)

---

