---
title: "Help accessing files copied from external HDD"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by greengecko on 2008-06-08
[SIZE="3"]I recently decided to reformat my maxtor external HDD (usb2.0).  To backup the content to my HDD I used the command:

sudo cp -R * /home/vault/maxtor_backup

Some of the copied files can be see here:
drwxr-xr-x 8 root root    4096 2008-06-07 19:45 backup
p--Sr-x--- 1 root root       0 2008-06-07 20:08 MiniDisk music
drwxr-xr-x 4 root root    4096 2008-06-07 19:37 movies
cr--r-Sr-x 1 root root 42, 228 2008-06-07 20:16 photo_library
dr-x-----x 2 root root    4096 2008-06-07 20:08 pictures

On the maxtor external HDD the photo_libary was a folder full of jpg's but it now seems to be a type of file called a 'character special device' ???. I am at a loss to explain why the cp command has changed it in this way??

I found some information about using a cpio to extract it but have been unable to make that work.  Some examples of commands I have used are:

cpio -ivd -I /dev/sda1/photo_library  or
cpio -ivd -I /dev/sda1/home/vault/maxtor_backup/ext-share/photo_library

but these have both returned withe the message
cpio: Cannot open /dev/sda1/home/vault/maxtor_backup/ext-share/photo_library: Not a directory

As I have already formatted the exteranl HDD and this is the only copy I have of these files any help to get them into a useable format would be very appreciated [SIZE="3"][/SIZE]??
[/SIZE]

---

### Post by greengecko on 2008-06-10
Has anyone got anyideas on this one?  Any help or hints would be very appreciated, I am well and truly stuck :confused:

---

### Post by ASULutzy on 2008-06-10
Not 100% sure, but when you do backups I'd use cp -ax instead of jsut cp -R

---

### Post by greengecko on 2008-06-10
Thanks for the reply, I will use that in the future.

---

### Post by cubeist on 2008-06-11
What happens when you cd into the photo library? Do you see individual photo files? or does it not let you because it thinks it is a character file?

---

### Post by greengecko on 2008-06-11
I am unable to cd into it.

---

