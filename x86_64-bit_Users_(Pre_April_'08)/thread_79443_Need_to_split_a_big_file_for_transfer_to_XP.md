---
title: "Need to split a big file for transfer to XP"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jon_gunnar on 2005-10-20
I got a rather big file, around 4.2Gb that gives me problems when I tries to burn it to a dvd.
Is there a way I can split the file in smaller chunks, and reassemple / extract it without problems under WinXP?

---

### Post by zekolas on 2005-10-20
Well their is a split command that will split files into defined chucks, I believe the command is

```
split -b n m 100  wholefile splitfile
```

will start splitting "wholefile" into 100mb chucks named splitfileaa, aplitfileab and so on. You can change the 100 to 2000 if you like so it will split it into bigger chunks. However I am not sure of a windows utility that would re-combine them.

you could also try to compress the file with gzip to try and shrink it. the command is just

```
gzip filename
```

will create a filename.gz that is compressed. However the largest individual file a DVD can hold is 2gigs so I doubt it will be able to be compressed that much.

I would just try to send it over a network if that is an option.

---

### Post by zekolas on 2005-10-20
I should also add that in linux you use the cat command to combine the files. the command is

```
cat file1 file2 file3 >>combinfile
```

will combine file1, file2, file3 into a new file named combinfile. Their might be a cat utility for windows that works the same way.

---

### Post by jon_gunnar on 2005-10-20
[QUOTE=zekolas]I should also add that in linux you use the cat command to combine the files. the command is

```
cat file1 file2 file3 >>combinfile
```

will combine file1, file2, file3 into a new file named combinfile. Their might be a cat utility for windows that works the same way.[/QUOTE]

Yes, I'm aware of split and cat. But since it will end up on a xp machine with no network connection I'm still lost. But I may try to find a cat substitute for xp.
Thank's anyway.

---

### Post by az on 2005-10-20
Cygwin is a unix environment for windows.  You can install that and use your favorite unix commands...


I beleive there is a way to do this in windows, but I am completely unfamiliar with Windows.

---

### Post by jon_gunnar on 2005-10-20
[QUOTE=azz]Cygwin is a unix environment for windows.  You can install that and use your favorite unix commands...


I beleive there is a way to do this in windows, but I am completely unfamiliar with Windows.[/QUOTE]

Thanks for the tip. Had a look at the homepage and it looks like cat is in the cygwin package. Found some post about problems with it, but if I don't find a better way, I will give it a try.

--Edit--
Solved the problem by bringing with me the disk and using Explore2fs from xp on the host machine.
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

### Post by queenorych on 2005-10-21
Doesn't zip still support breaking up files?  I used pkzip back in the old dos days to break files to fit on a floppy.

---

### Post by cychem1 on 2005-10-22
It sounds like you are using a FAT32 file system, in Windows XP if so it cannot handle a file bigger than 4.0 GB. If you are running NTFS it should work and burn correctly.

---

### Post by zekolas on 2005-10-22
I believe the 2 gig file limit is an limitation of the dvd-r not of the local file system. I however believe it is possible to get around the 2 gig file limit by burning the dvd in a differnt file format,  however I don't have much experance working with dvd-r drives

---

### Post by jon_gunnar on 2005-10-22
[QUOTE=cychem1]It sounds like you are using a FAT32 file system, in Windows XP if so it cannot handle a file bigger than 4.0 GB. If you are running NTFS it should work and burn correctly.[/QUOTE]

Is has nothing with the local system to do. The problem were the limitation on the file size on the dvd disc.

---

### Post by MaX on 2005-10-23
Overburn it...
Or just split it with rar/file-roller etc.

---

### Post by wmcbrine on 2005-10-24
```
copy /b filename1+filename2 filename3
```
is approximately the Windows/DOS equivalent of

```
cat filename1 filename2 >filename3
```
IIRC. YMMV. IANAL.

---

### Post by ranf on 2005-10-24
```
split --help
```

---

