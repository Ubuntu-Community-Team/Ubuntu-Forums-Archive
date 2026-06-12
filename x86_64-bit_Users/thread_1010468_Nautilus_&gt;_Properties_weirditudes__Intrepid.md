---
title: "Nautilus &gt; Properties weirditudes / Intrepid"
date: 2008-12-13
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2008-12-13
I have a desktop and a laptop, both with Ubuntu Intrepid x86_64. The laptop is the main computer and the desktop is used for backups, downloading ISOs, and playing vids. On both computers I am user jjj.

I just finished a backup of the laptop to the desktop using Flyback, a front end for rsync. Looking at Properties in Nautilus for the /home/jjj folder on the desktop (while on the desktop computer) it reports the folder size at 7.3 GB. Looking at the Properties for the same folder from the laptop (with the desktop mounted on the laptop, of course) it shows the total as 13.8 GB. The latter is the correct size of the /home/jjj folder.

I found a Nautilus bug report where Nautilus does not report the size correctly if you have the view options set to not display hidden files. Indeed, the hidden files may account for all of the difference. However, Show Hidden Files is selected on both computers.

I could swear that this never happened when both computers were running Hardy. Has anyone run into this?

---

### Post by cariboo on 2008-12-14
What are the results if you run in a terminal:

```
du -h
```

on both computers?

Jim

---

### Post by John Jason Jordan on 2008-12-14
> **cariboo907 said:**
> What are the results if you run in a terminal:

```
du -h
```

on both computers?

It just runs a list of all files on the computers. It doesn't even sum the total file sizes. Using the man page for du I see that I can add the -c option to sum them. The sums are the same.

But that doesn't help much in figuring out why Nautilus reports the wrong totals, other than to see that du reports the (apparently) correct totals.

---

