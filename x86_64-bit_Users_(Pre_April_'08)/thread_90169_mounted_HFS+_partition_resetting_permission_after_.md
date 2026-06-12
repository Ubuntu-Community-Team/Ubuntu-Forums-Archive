---
title: "mounted HFS+ partition resetting permission after reboot"
date: 2005-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomislavmedak on 2005-11-14
whenever i reboot into my ubuntu, the mounted HFS+ partition resets the access permissions to read only. to enable the write permission i have to reboot into OS X first and apply the existing read and write permissions for user, group and others to all items on the volume. upon rebooting into linux i can then write on this partition.

the fstab entry for this volume is following:

```
/dev/hda5       /media/ko3moc   hfsplus rw,umask=0      0       0

```

did anyone had same problems and how to resolve them?

---

### Post by ssam on 2005-11-14
have a look through the mount man page, run
```
man mount
```
and find the section about options. there are also a few hfs specific options.

perhaps if you set the
```
uid=n, gid=n
```
values to your user. i think this just mounts with those ownerships rather than change them on disk

the command
```
id
```
will give you the **n** numbers.

i think somepeople change thier uid to match between max os x and linux.

---

### Post by slux on 2005-11-14
[QUOTE=ssam]have a look through the mount man page, run
```
man mount
```
and find the section about options. there are also a few hfs specific options.
.[/QUOTE]

Plain HFS is completely different from HFS+ which is what we are talking about with OS X. While HFS is a single-user filesystem similarly to FAT and has the uid and gid mount options for that reason, I don't think hfsplus has them at all.

---

### Post by ssam on 2005-11-14
i think you can apply those options on most file systems to override the real values, but i may be worng. i think i have used them to override ownership on a cdrom burned from mac os x. I think that uses rockridge an extention to iso9660 that allows ownership.

maybe setting the uid to match between linux and mac os xis the way to go

---

### Post by tomislavmedak on 2005-11-15
i solved the problem by placing the uid number of my linux account into my fstab. now the respective fstab line is:

```
/dev/hda5       /media/ko3moc   hfsplus uid=1000        0       0
```

thanks guys

---

### Post by slux on 2005-11-15
That's interesting. On a multi-user FS all users get mapped to that one? I was positive that it doesn't work with hfs+... Oh well, I'm still pretty sure it doesn't work on some filesystems since I have a very strong memory that I've tried this. :)

uid=xxx is bad in one respect though. It'll let you control everything with no effort, even the files apple has deemed best for only the root user to touch and you might do serious damage on the fs with an accidental command unlike if you make your OS X UID and Ubuntu UID match.

---

### Post by tomislavmedak on 2005-11-16
the volume i'm mounting is not the OS X system partition - it's a partition that i use to store my data and that i want to be able to access from both systems. as the drivers to access ext3 from Tiger are not available yet, i had to use the hfs+ file system. OS X system partition i do not mount. but now that i don't have to boot into OS X to reset my permissions, i won't have much use for the OS X anyhow.

this said, how do you change the UID on ubuntu?

---

### Post by pindar on 2005-11-16
[QUOTE=tomislavmedak]this said, how do you change the UID on ubuntu?[/QUOTE]

sudo usermod -u <new UID> <login>

Do this from a shell and remember to sudo chown all files in your home directory to this new UID. I remember that after changing my UID, Gnome wouldn't start properly because it couldn't read the config files.

---

### Post by slux on 2005-11-16
[QUOTE=pindar]sudo usermod -u <new UID> <login>

Do this from a shell and remember to sudo chown all files in your home directory to this new UID. I remember that after changing my UID, Gnome wouldn't start properly because it couldn't read the config files.[/QUOTE]

From the usermod manpage:
```

      -u uid The  numerical  value  of  the  user’s  ID.   This value must be
              unique, unless the -o option is used.  The value  must  be  non-
              negative.   Values  between  0 and 99 are typically reserved for
              system accounts.  Any files which the user owns  and  which  are
              located  in  the directory tree rooted at the user’s home direc&#8208;
              tory will have the file user ID  changed  automatically.   Files
              outside of the user’s home directory must be altered manually.

```

So this should not be an issue unless usermod is functioning incorrectly for some reason.

---

