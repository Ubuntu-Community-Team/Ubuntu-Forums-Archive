---
title: "wine: apexdc++ v1.1.0 stays minimized"
date: 2008-06-17
forum: Wine
---

### Post by -random on 2008-06-17
Apex worked until I minimized it, moved to another workspace and tried to maximize it there.

Now I can launch apexdc, and it still connects to the hub and ppl download from it ( my buddy next door can download from me when I connect )

 BUT >_<

I can't see (or use) the user interface, that is, it stays minimized and when I doubleclick/rightclick > show/hide, It remains minimized :(

any help?

  - - - ok .. So I didn't solve the underlying problem, but I found a fix - - -
>First delete the .wine directory, then in terminal run ```
winecfg
```(to re-create it and other stuff)
>Then re-install Apex, do your settings and file hashing thing..
>Then copy the working folder to a temp directory (sommer ApexDC++_restore)
> and use the following script whenever Apex gives the same prob to recover it:
```

cd /home/your_name_here/.wine/drive_c/Program\ Files/
rm -r ApexDC++
mkdir ApexDC++
cp -r ApexDC++_restore/* ApexDC++

``` (code super redundant for super clarency :P )

Does anyone know which files apex uses to store the currrent download cue list? That would be great!..

---

