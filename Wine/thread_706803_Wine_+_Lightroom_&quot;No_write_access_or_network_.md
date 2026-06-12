---
title: "Wine + Lightroom: &quot;No write access or network folder&quot; issue"
date: 2008-02-24
forum: Wine
---

### Post by sunside on 2008-02-24
Hi folks.

I just installed Lightroom using wine 0.9.55 and that worked well. When I start Lightroom it asks me to open a catalog. When I select my catalog, Lightroom says that it can't open the catalog because it is either read-only or on a network share (which Lightroom doesn't seem to support right now).

The catalog is on a ntfs-3g mounted drive, which is owned by root and has full read+write permissions for everyone (at least I thought that, I have another thread  open with a similar problam). I tried mount the catalog folder directy as a drive and also created a link to it in my "My Photos" folder (or whatever it is called in English), but without success.

Any idea how to work around that, without using Lightrooms import/export options. (I'd like to keep the catalog where it is)


Markus

---

### Post by HonourableTyr on 2008-08-02
I've just had exactly the same problem installing Lightroom on Ubuntu 8.04. It would probably work if I could get the catalogue to load. I've only just started using Linux so have no idea what to try next.

---

### Post by aoanla on 2008-08-02
This *may* be an issue with the catalogue being on an ntfs partition. I know that ntfs-3g doesn't enable all of the features that Wine expects a filesystem to have - this causes issues with running Steam from an ntfs partition, for example - and so it's worth, if you can, testing to see if the problem persists from a different file system.

---

### Post by HonourableTyr on 2008-08-02
Well, I tried loading the catalogue from the 'virtual' C drive, the primary ext2 partition, an actual XP ntfs partition and all failed.

It is a little like tripping on a flat surface and breaking your ankle just before the finishing line.

So close yet so far.

Seeing as it gets far enough to want to load a catalogue if we could get past this hurdle it would probably load.

Whether it would be usable is a different issue though, may end up being really slow. Just wish Adobe would release a Linux version. Then again, there is Lightzone but it is spending yet again. The other annoying thing is the lack of support for calibration and profiling for monitors.

---

### Post by Jerzabek39 on 2008-08-16
Any news here..? :(

---

### Post by qwertymn on 2008-08-16
Hi, i downloaded the trial from Adobe site.
This seems to be related to unimplemented function GetVolumePathNameW. I made a quick hack like below, and than the trial starts for me. I dunno how far it's usable, seemed a bit sluggish , and already had 2 crashes while pushing some buttons in the GUI. guess that needs more testing

diff --git a/dlls/kernel32/volume.c b/dlls/kernel32/volume.c
index 74397a9..545eca0 100644
--- a/dlls/kernel32/volume.c
+++ b/dlls/kernel32/volume.c
@@ -1400,10 +1400,16 @@ BOOL WINAPI GetVolumePathNameA(LPCSTR filename, LPSTR volumepathname, DWORD bufl
 BOOL WINAPI GetVolumePathNameW(LPCWSTR filename, LPWSTR volumepathname, DWORD buflen)
 {
     FIXME("(%s, %p, %d), stub!\n", debugstr_w(filename), volumepathname, buflen);
-    SetLastError(ERROR_CALL_NOT_IMPLEMENTED);
-    return FALSE;
+
+    WCHAR l[] = {'c',':','\\',0};
+
+    lstrcpyW(volumepathname,l);
+    return 1;
 }
 
+
+
+
 /***********************************************************************
  *           FindFirstVolumeA   (KERNEL32.@)
  */

---

### Post by Jerzabek39 on 2008-08-17
> **qwertymn said:**
> 
diff --git a/dlls/kernel32/volume.c b/dlls/kernel32/volume.c
index 74397a9..545eca0 100644
--- a/dlls/kernel32/volume.c
+++ b/dlls/kernel32/volume.c
@@ -1400,10 +1400,16 @@ BOOL WINAPI GetVolumePathNameA(LPCSTR filename, LPSTR volumepathname, DWORD bufl
 BOOL WINAPI GetVolumePathNameW(LPCWSTR filename, LPWSTR volumepathname, DWORD buflen)
 {
     FIXME("(%s, %p, %d), stub!\n", debugstr_w(filename), volumepathname, buflen);
-    SetLastError(ERROR_CALL_NOT_IMPLEMENTED);
-    return FALSE;
+
+    WCHAR l[] = {'c',':','\\',0};
+
+    lstrcpyW(volumepathname,l);
+    return 1;
 }
 
+
+
+
 /***********************************************************************
  *           FindFirstVolumeA   (KERNEL32.@)
  */
What should I do with the code..?

---

### Post by qwertymn on 2008-08-19
>What should I do with the code..? 

You'd have to get the wine-source, patch it with the patch, and compile wine yourself. I've sent a (different) patch to wine-patches, not sure if it'll get accepted

---

### Post by epud on 2009-03-29
So, did anybody find a solution to this? I am also at the catalogue step. Very close I feel.

---

### Post by takashisenko on 2009-05-26
Just go to [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and add APT Repository for your distro. See the page for more specific. And now you can upgrade to the latest beta. Lightroom error already solved.

cheers.
:popcorn:

---

### Post by blur xc on 2009-07-08
> **takashisenko said:**
> Just go to [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and add APT Repository for your distro. See the page for more specific. And now you can upgrade to the latest beta. Lightroom error already solved.

cheers.
:popcorn:

Yeah...  I read this post, did all that, and BAM!  Lightroom loadedup and appeared to be running!!!!  YAY!!!  Untull I tried importing a picture....  FAIL...  

Doesn't work- real buggy.  Crashed- etc...  I tried doing a bunch of killall's to get rid of the orphaned processes, but had to reboot to get them to go away.

I have hope at least- Mabye I'll give bible a go- but I already have thousands of pics in lightroom, many raw files with actions applied to them, and I'm not willing to throw all that work away by switching to a new raw processor.

BM

---

### Post by tienhn on 2009-08-03
Close, but no cigar!!!

Installed LightRoom 2.4 OK.
Create Album OK.
Import pictures OK.
However, no icon or images displayed.

So, stick with [www.virtualbox.org](www.virtualbox.org) for now!!!

By far LightRoom is the best tool for photo management and processing that I have found. I have tried F-Spot, digiKam, etc, noe f them even come close.

Cheers,

---

### Post by giampaolo44 on 2010-03-12
anybody knows  if there's news on this topic?

cheers

---

### Post by winjeel on 2010-07-18
> **tienhn said:**
> ...

By far LightRoom is the best tool for photo management and processing that I have found. I have tried F-Spot, digiKam, etc, noe f them even come close.

Cheers,

Bibble 5 is pretty darn awesome, but I still feel that LR is an n-th of a degree better. Hopefully, because of the squabbling between Steve Jobs and Adobe, we'll eventually see a Linux version of LR.

---

### Post by handy on 2010-08-20
Has anyone managed to get Lightroom 3, to work in Wine yet?

It is such an awesome tool & I'd love to be able to use it one way or another on Linux, instead of having to boot into OS X, where many of the fonts are so small it causes eye strain using it (OS X, that is).

---

