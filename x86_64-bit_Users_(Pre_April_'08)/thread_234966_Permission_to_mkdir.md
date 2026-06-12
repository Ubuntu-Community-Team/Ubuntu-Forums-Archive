---
title: "Permission to mkdir???"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikeescott on 2006-08-12
I tried to mkdir so I could access my Windoze ntsf drives and I got an error message saying I did not have permission to mkdir and to ask admin for assistance. Why do I I not have permission to mkdir on my own computer?

---

### Post by hopstah on 2006-08-12
because you're trying to do it in a location that normal users don't have access to.  do ```
sudo mkdir
``` instead.

---

### Post by Kilz on 2006-08-12
In linux some areas are owned by root, not by the user. Try
```
sudo mkdir
```

---

### Post by mikeescott on 2006-08-12
> **Kilz said:**
> In linux some areas are owned by root, not by the user. Try
```
sudo mkdir
```

I am running into a lot of things that I do not have permission to do. Is there a way around this?

sudo allowed the mkdir, but could not find the ntsfmount command afterwards.

Where do I find libfuse2, ntsfprogs, and fuseutils and how do I install them?

---

### Post by mikeescott on 2006-08-12
> **hopstah said:**
> because you're trying to do it in a location that normal users don't have access to.  do ```
sudo mkdir
``` instead.
 
Is there a way to let the computer know I would like to be more than a normal user?

---

### Post by Greycloak on 2006-08-12
> **mikeescott said:**
> I am running into a lot of things that I do not have permission to do. Is there a way around this?

This is exactly the reason that Linux is more secure than Windows.  It is a minor inconvenience, and worth it for security.

---

### Post by mikeescott on 2006-08-13
> **Greycloak said:**
> This is exactly the reason that Linux is more secure than Windows.  It is a minor inconvenience, and worth it for security.


So if I do not have permission from my computer to type commands, how do I access files on my Windoze drives and install my modem drivers?

---

### Post by Greycloak on 2006-08-13
Like Kilz said above...you can precede the commands with 'sudo' and you will have the appropriate permission. As far as accessing NTFS volumes, you should be able to read from them without any problems. My windows drives/partitions show up on my desktop as hda1/hda5/hdb1.  I understand it is possible to write to NTFS volumes, but not exactly recommended as it is not 100% guaranteed to work.

That being said, have a look here:

[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)

Hope this helps.

---

### Post by Kilz on 2006-08-13
> **Greycloak said:**
> I understand it is possible to write to NTFS volumes, but not exactly recommended as it is not 100% guaranteed to work.

That being said, have a look here:

[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)

Hope this helps.

Writing to ntfs drives can corrupt the entire drive, you stand the chance of losing everything on it. Its experimental. Like " I just made some brake pads from cotton candy. Who wants to go for a drive with me?" experimental.
The first line from the howto you linked to should be a warning to everyone.
[COLOR="Red"]Warning : ntfs-3g is still in beta. You should not use it on production machines[/COLOR]

---

### Post by mikeescott on 2006-08-13
I am not wanting to write. I just want to access videos, music, pictures, documents, and other files that I use regularly. I am somehow able to go into the filesystem/media and access sda1 and hdb1 but not sdc, sdd, sdd, hdb5 or 6. and none of these are on my desktop. I am more worried about getting on the net for now though. Then I need to get audio working.

---

### Post by hecato on 2006-08-13
Then why not try

```

sudo nautilus
or
sudo konqueror

```
For launch the browser... in case the partition is mounted, you will be able to access it...

---

### Post by mikeescott on 2006-08-13
> **hecato said:**
> Then why not try

```

sudo nautilus
or
sudo konqueror

```
For launch the browser... in case the partition is mounted, you will be able to access it...


This is what I got when trying both of those:

```

** (nautilus:6091): CRITICAL **: nautilus_launch_show_file: assertion `!nautilus_file_needs_slow_mime_type (file)' failed

mike@mike-desktop:~$ sudo konqueror
sudo: konqueror: command not found
```

---

