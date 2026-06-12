---
title: "Is there a way to get Windows-like contextual menus on a Windows-like desktop?"
date: 2016-01-14
forum: Wine
---

### Post by yoshii on 2016-01-14
Hello, I am currently running Ubuntu Studio v14.04.3 with Wine v1.9 and it's running smoothly.  
I am just wondering if there is a way to get a desktop like on Windows where there's a contextual menu when I right-click on an icon.  

I of course have the Linux desktop (Xfce) and it's running fine and it has it's own contextual menus.  
But is there a way to get to the contextual menus that are installed in Windows?  

For example, both 7-zip and Bandizip (Windows freewares) have options to install contexual menus into the Windows desktop.  
But they don't show up in Ubuntu's interface even with Wine running.  Do you know how to get to those contextual menus?  
Or do they just not translate?  It's nothing crucial, but it would be nice to know how to get those features if possible.

---

### Post by yoshii on 2016-01-21
Does anybody have any answers for this?

---

### Post by yoshii on 2016-01-25
Thanks for trying to help ozo2.  
I already have Linux contextual menus.  That is not my issue.  
All of my Linux contextual menus are just fine.  
I'm just wanting to have contextual menus added (Windows shell commands) for Windows programs that install them via registry or whatnot to the "explorer".  

I really don't want to install a completely different distro.  I'm happy with Xubuntu and Ubuntu Studio.  I tried Mint and I didn't like it.  

Anybody else?

---

### Post by dacha on 2016-03-09
> **yoshi2 said:**
> Thanks for trying to help ozo2.  
I'm just wanting to have contextual menus added (Windows shell commands) for Windows programs that install them via registry or whatnot to the "explorer".  


In other words, when you install 7-Zip and right-click on an archive in Nautilus / Konqueror / Thunar / PCManFM / etc., you want a "7-Zip -> Extract files..." context menu just like in Windows Explorer?

If so, you're out of luck: the Linux desktop fundamentally does not support that. There is no way to customize the right-click menu of a file manager in general - no Freedesktop specification for it exists. Maybe we could patch Wine's Explorer to support this, but then you'd have to do all file browsing with Wine's Explorer, which I don't imagine anybody does by choice :). Adding this feature to Linux file managers is both a large technical and a large political project, as not only does a specification have to be written, but patches for all the file managers have to be written and their upstream developers have to be convinced to accept them, and finally Wine would have to be patched to convert those menus into the Linux form.

What can be done, and what Wine already does, is support opening files with Windows applications installed under Wine, so that double-clicking on a file in a Linux file manager will open it with the Windows application installed under Wine that registered itself for that file extension (or at least list that Windows application among those offered, if multiple applications can open that file).

---

### Post by sudodus on 2016-03-09
There is a native version of 7-zip in linux: ***7z***. If I understand correctly, it's tools integrate with the ***file-roller*** GUI.

```
sudo apt-get install p7zip-full
```

```
7z(1)                                             General Commands Manual                                             7z(1)

NAME
       7z - A file archiver with highest compression ratio

SYNOPSIS
       7z [adeltux] [-] [SWITCH] <ARCHIVE_NAME> <ARGUMENTS>...

DESCRIPTION
       7-Zip  is a file archiver with the highest compression ratio. The program supports 7z (that implements LZMA compres&#8208;
       sion algorithm), LZMA2, XZ, ZIP, Zip64, CAB, RAR (if the non-free p7zip-rar package is installed), ARJ, GZIP, BZIP2,
       TAR, CPIO, RPM, ISO, most filesystem images and DEB formats. Compression ratio in the new 7z format is 30-50% better
       than ratio in ZIP format.

       7z uses plugins to handle archives.

FUNCTION LETTERS
       a      Add

       d      Delete

       e      Extract

       l      List

       t      Test

       u      Update

       x      eXtract with full paths

...

```

---

### Post by yoshii on 2016-03-09
Thanks Dacha, you answered my questions.  
And yes, Sudodus, I'm aware of the Native Linux 7-zip stuff.  That's not what I was asking about.  But thanks anyways.

---

### Post by 6975 on 2016-03-17
You need kde desktop or kubuntu distro to do that for example:

[IMG]http://tomtomtom.org/p7zip-gui/images/Kontextmen%C3%BC.png[/IMG]

[IMG]http://2.bp.blogspot.com/-KeSogIJJuNo/VJ72DN0BJxI/AAAAAAAAD2E/siZgWQNRgmA/s1600/peazip.png[/IMG]

But that's it that's the price to pay for heaviness.
If me I don't need to I prefer XFCE desktop.

---

