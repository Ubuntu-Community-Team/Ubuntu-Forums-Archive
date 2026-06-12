---
title: "How do I setup ePSXe under x86-64 ? Older forum posts not helpful anymore"
date: 2009-10-04
forum: x86 64-bit Users
---

### Post by Dthdealer on 2009-10-04
**[SOLVED]**
Non 32-bit users (such as myself) have problems getting ePSXe to work, as it outputs this error message when run.
```
 error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```
After a google I came across _[this page]("http://ubuntuforums.org/showthread.php?t=229457")_ which links me to two other pages. The first was dead (not on waybackmachine either) and was supposed to outline how to copy over the libraries to the lib32 folder but [_the second_]("http://ubuntuforums.org/showpost.php?p=1339711&postcount=25") is a post from Ubuntu forums.

Unfortunately all but the first link is dead.

So I went for a search on the forums themselves and I came to _[this topic]("http://ubuntuforums.org/showthread.php?t=928546&highlight=ePSXe")_.
The deb (link removed from original post, but it is quoted later) on the page is *only* for i386 architectures. Someone posts the same problem I have but to no avail.

Has anyone using an x86 64-bit system got ePSXe or any other PlayStation 1 emulators to work? The Windoze version under Wine does not work either.

---

### Post by ShadowTek on 2009-10-04
> Has anyone using an x86 64-bit system got ePSXe or any other PlayStation 1 emulators to work? The Windoze version under Wine does not work either.

I got pSX to work, but I have to run it with sudo, and I have to do "sudo killall pulseaudio" before I run it.

---

### Post by Dthdealer on 2009-10-05
> **ShadowTek said:**
> I got pSX to work, but I have to run it with sudo, and I have to do "sudo killall pulseaudio" before I run it.

I've read about the audio-server problem, but doing either or both didn't fix the library problem.

---

### Post by ShadowTek on 2009-10-05
I might have needed to copy one of those libs manually before getting pSX to work, but I can't recall clearly.

Basically, you want to find the 32-bit version of whatever package contains the file that you need, and copy that particular file to whatever 32-bit directory your application is looking in.

I've never managed to get any other playstation emus to work, so I can't comment on them.

---

### Post by Dthdealer on 2009-10-06
I found this page
[http://ubuntuforums.org/showpost.php?p=2849759&postcount=1]("http://ubuntuforums.org/showpost.php?p=2849759&postcount=1")
which told me how to obtain libgtk1.2 (sudo getlib -l libgtk-1.2.so.0) and so that problem has been fixed. ePSXe then also asked for libglib and libgmodules libraries of version 1.2 (of which I have 2.0 in the /usr/lib32 folder). I just copied them over to the 1.2 names.

Now I'm presented with a new error.

```
 * Running ePSXe emulator version 1.6.0. 
./epsxe: symbol lookup error: /usr/lib32/libgdk-1.2.so.0: undefined symbol: g_source_add
```

Googling comes to two results, both the same topic in the two Ubuntu forum page-styles. As far as I could see the author comes to no conclusion.

---

### Post by Dthdealer on 2009-10-09
[SOLVED]

nullDC works perfect under WINE after copying some dlls over to my wine ystem32 directory.  No need for ePSXe anymore.

However it suffers from two problems, one being it hates the fglrx module I use and the other audio stutters a bit, but that is fine.

---

### Post by Yellow Pasque on 2009-10-09
> ePSXe then also asked for libglib and libgmodules libraries of version 1.2 (of which I have 2.0 in the /usr/lib32 folder). I just copied them over to the 1.2 names.


That's what caused your error. Make sure you change those filenames back in case other 32-bit programs need them. In case you want to try epsxe again:
```
sudo getlibs -p libglib1.2ldbl libgtk-1.2
```

---

### Post by quequotion on 2009-10-09
> **Dthdealer said:**
> [SOLVED]

nullDC works perfect under WINE after copying some dlls over to my wine ystem32 directory.  No need for ePSXe anymore.

However it suffers from two problems, one being it hates the fglrx module I use and the other audio stutters a bit, but that is fine.

....isn't nullDC a dreamcast emulator? how does that remove the need for a playstation emulator?

---

