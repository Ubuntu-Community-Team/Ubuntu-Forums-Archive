---
title: "A small application does not work with mono"
date: 2011-07-06
forum: Wine
---

### Post by mpiter on 2011-07-06
I wanted to use a small Japanese application to extract pictures from game saved files.  I ran it from a terminal:

```
mono EgokoroExport.exe
```

It opened a small window.  I clicked on it to open a dialog box to select a file.  I selected the file.  With a real Windows 7 system, it correctly extracted the pictures and it stored them in an "export" directory.  With Ubuntu 11.04 using [COLOR="Blue"]mono[/COLOR], it did nothing with no error messages in the console.  I however found in [COLOR="Blue"]~/.xsession-errors[/COLOR] this message:

```
warning :  (/build/buildd/cairo-dock-2.3.0~1/src/icon-factory/cairo-dock-application-factory.c:cairo_dock_new_appli_icon:264)  
  this window doesn't belong to any class, skip it.
```

I used Wine 1.2.2 in Windows 7 mode with this distrib:

```
# uname -a
Linux lilas 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

I also tried with the same wine in Windows XP mode with the same result.  I had installed [COLOR="Blue"]mono-complete[/COLOR] and I ran Compiz with Emerald in Ubuntu classic mode.

Any idea of what I should do?  Thanks in advance for any hint.

---

### Post by mpiter on 2011-07-07
Shame on me.  The program worked well but I did not notice it because the resulting pictures were stored in a directory one level above the working directory.  I was working in a directory called [COLOR="Blue"]0_tmp[/COLOR].  The resulting files were saved in the directory one level above with the name [COLOR="Blue"]0_tmp\export\image_001.jpg[/COLOR].  Of course, this was a correct tree expansion under Windows, but just a file name with Linux.  It did not occur to me to check the directory one level above the working directory.  Thanks to those who took time to check my request.

---

### Post by directhex on 2011-07-09
PLEASE use System.IO.Path.Combine to build paths - it correctly deals with differing DirectorySeparatorChar values on different OSes

---

### Post by mpiter on 2011-07-11
> **directhex said:**
> PLEASE use System.IO.Path.Combine to build paths - it correctly deals with differing DirectorySeparatorChar values on different OSes

Thank you for this piece of information.  I did not develop the application myself and I do not own the source code.  Hence, I cannot use the class.  But thanks to your piece of advise I found out that
```
export MONO_IOMAP=all
```
does the tricks ([http://www.mono-project.com/IOMap]("http://www.mono-project.com/IOMap")). I put the [COLOR="Blue"]export[/COLOR] in my .bashrc file and the problem was fully solved.  Thanks again.

---

