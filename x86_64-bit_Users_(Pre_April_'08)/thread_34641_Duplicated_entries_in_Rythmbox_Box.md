---
title: "Duplicated entries in Rythmbox Box"
date: 2005-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by idn on 2005-05-15
Hi, some of the songs listed in rhythm box have been duplicated (same song listed twice) this is a bit annoying when playing albums etc, is there a way to remove songs or delete the file that stores the playlist, I had a look round but couldnt see anything

---

### Post by Sam on 2005-05-15
[QUOTE=idn]Hi, some of the songs listed in rhythm box have been duplicated (same song listed twice) this is a bit annoying when playing albums etc, is there a way to remove songs or delete the file that stores the playlist, I had a look round but couldnt see anything[/QUOTE]
Remove files list:
```
$ rm ~/.gnome2/rhythmbox/rhythmdb.xml
```
Remove playlists:
```
$ rm ~/.gnome2/rhythmbox/playlists.xml
```

---

### Post by idn on 2005-05-16
brilliant, thanks alot

---

### Post by Package on 2005-06-01
The other way is to delete duplicates from your Hard disk with any program which can do that. For ex. with  [Dupe Checker PRO](http://www.atory.com/download/dupe_checker_pro.exe). And then you should refresh your music library...

Peace!

---

### Post by dannystaple on 2006-06-19
[QUOTE=Package]The other way is to delete duplicates from your Hard disk with any program which can do that. For ex. with  [Dupe Checker PRO](http://www.atory.com/download/dupe_checker_pro.exe). And then you should refresh your music library...

Peace![/QUOTE]

Hardly appropriate since this is a Linux forum. Dupe checker may run under Wine, but what a complicated way to do things.

May I heartily recommend fslint. It is a gtk based tool for routing out lint (or fluff) on your harddrive. I reviewed it some time ago [Danny Staple Blog - Tip For Dealing With Duplicate Files]("http://orionrobots.co.uk/tiki-view_blog_post.php?blogId=1&postId=72")

Cheers,
Danny

---

