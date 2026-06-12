---
title: "Installing a patch in Wine"
date: 2008-07-22
forum: Wine
---

### Post by Vakman on 2008-07-22
I was told to patch Wine with this. But that would mean I have to install it from source I guess. Could anyone show me how to get Wine with this in it I guess? I have no idea how to really. Also this is the page the patch is on [http://bugs.winehq.org/show_bug.cgi?id=12929](http://bugs.winehq.org/show_bug.cgi?id=12929) help please.

```
diff --git a/loader/preloader.c b/loader/preloader.c
index 109ad3f..84dc8c4 100644
--- a/loader/preloader.c
+++ b/loader/preloader.c
@@ -108,9 +108,7 @@
 
 static struct wine_preload_info preload_info[] =
 {
-    { (void *)0x00000000, 0x00010000 },  /* low 64k */
-    { (void *)0x00010000, 0x00100000 },  /* DOS area */
-    { (void *)0x00110000, 0x5fef0000 },  /* low memory area */
+    { (void *)0x00000000, 0x60000000 },  /* low memory area */
     { (void *)0x7f000000, 0x02000000 },  /* top-down allocations + shared heap */
     { 0, 0 },                            /* PE exe range set with WINEPRELOADRESERVE */
     { 0, 0 }                             /* end of list */
@@ -921,7 +919,7 @@ static void preload_reserve( const char *str )
     const char *p;
     unsigned long result = 0;
     void *start = NULL, *end = NULL;
-    int i, first = 1;
+    int first = 1;
 
     for (p = str; *p; p++)
     {
@@ -950,22 +948,15 @@ static void preload_reserve( const char *str )
         start = end = NULL;
     }
 
-    /* check for overlap with low memory areas */
-    for (i = 0; preload_info[i].size; i++)
-    {
-        if ((char *)preload_info[i].addr > (char *)0x00110000) break;
-        if ((char *)end <= (char *)preload_info[i].addr + preload_info[i].size)
-        {
-            start = end = NULL;
-            break;
-        }
-        if ((char *)start < (char *)preload_info[i].addr + preload_info[i].size)
-            start = (char *)preload_info[i].addr + preload_info[i].size;
-    }
+    /* check for overlap with low memory area */
+    if ((char *)end <= (char *)preload_info[0].addr + preload_info[0].size)
+        start = end = NULL;
+    else if ((char *)start < (char *)preload_info[0].addr + preload_info[0].size)
+        start = (char *)preload_info[0].addr + preload_info[0].size;
 
-    while (preload_info[i].size) i++;
-    preload_info[i].addr = start;
-    preload_info[i].size = (char *)end - (char *)start;
+    /* entry 2 is for the PE exe */
+    preload_info[2].addr = start;
+    preload_info[2].size = (char *)end - (char *)start;
     return;
 
 error:
```

---

### Post by LinuxRocks713 on 2008-08-03
First, download the Wine sources. Extract to ~/Desktop/wine. 

Next, type "sudo ln -s /wine ~/winebuild" and then "mkdir ~/winebuild".

Change into ~/Desktop/wine in a terminal and type "./configure --prefix=/wine".

Then, patch any required files. Then build with "make" followed with "make install".

And in the end, build a debian package for easier management. Here's a guide: [http://www.compdigitec.com/labs/2008/07/28/building-deb-packages-on-ubuntudebian/](http://www.compdigitec.com/labs/2008/07/28/building-deb-packages-on-ubuntudebian/)

Just copy the contents of /wine into the virtual /usr folder mentioned in the guide. Don't forget to do "ln -s wine usr" inside the virtual root.

---

