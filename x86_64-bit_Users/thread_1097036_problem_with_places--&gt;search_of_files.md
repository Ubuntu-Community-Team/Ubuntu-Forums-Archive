---
title: "problem with places--&gt;search of files"
date: 2009-03-15
forum: x86 64-bit Users
---

### Post by aimonas on 2009-03-15
Hello, I have installed ubuntu 8.10-64bit and I 've noticed a strange behaviour of the search of files utility. In specific, while in 8.04 I could immediately find the location of folders and files simply writing the keyword, in this case it just doesn't show the desired locations for system files. 

For example, I searched to find the folders related to texlive by adding it as keyword and the search in the file system didn't return anything.
 
Does anyone have a clue about the problem?

---

### Post by aimonas on 2009-03-18
well, it seems that this option is somehow related to the indexer--although I remember reading somewhere that their functions are independent (quite vague, but this is what I understood). anyway after the indexer has done some job in the filesystem the place-->search of files option work fine.  

anyway for whomever encounters the problem after the installation of this version and doesn't know what to do, as were I. greets and viva ubuntu!

---

### Post by philinux on 2009-03-18
> **aimonas said:**
> Hello, I have installed ubuntu 8.10-64bit and I 've noticed a strange behaviour of the search of files utility. In specific, while in 8.04 I could immediately find the location of folders and files simply writing the keyword, in this case it just doesn't show the desired locations for system files. 

For example, I searched to find the folders related to texlive by adding it as keyword and the search in the file system didn't return anything.
 
Does anyone have a clue about the problem?

One thing to remember here. It will not search for folders, only files. i made that mistake a long time ago. Also nautilus search does not use tracker it use updatedb. You may need to run this from a terminal if you recently installed something as it runs as a cron job I think

```
sudo updatedb
```

It runs but returns no text and can take a few mins.
Then either use the gui or
```
locate filename
```

---

### Post by aimonas on 2009-03-18
thanks for the notice! it's nice to know what are the dependencies exactly. But it isn't explained why the problem has been resolved without running it. It might be the case though, that now that I run a query for the same word (texlive), it returned more results

oh, and it does return folders. why you say that it doesn't?

greets and thanks again

---

### Post by philinux on 2009-03-18
> **aimonas said:**
> thanks for the notice! it's nice to know what are the dependencies exactly. But it isn't explained why the problem has been resolved without running it. It might be the case though, that now that I run a query for the same word (texlive), it returned more results

oh, and it does return folders. why you say that it doesn't?

greets and thanks again

Meant to say it will not show hidden folders. Updatedb is run periodically by the system. So depends when it was run and when you do a search.

---

### Post by aimonas on 2009-03-18
> **philinux said:**
> Meant to say it will not show hidden folders. Updatedb is run periodically by the system. So depends when it was run and when you do a search.

thanks! everything is clear now!

---

