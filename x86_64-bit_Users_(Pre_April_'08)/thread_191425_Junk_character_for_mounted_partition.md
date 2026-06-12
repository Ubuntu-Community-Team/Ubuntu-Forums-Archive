---
title: "Junk character for mounted partition"
date: 2006-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sanketmedhi on 2006-06-07
This is a very tiny lil problem. I just upgraded to Dapper. I have 3 vfat partitions on my system which I have added to /etc/fstab. They are /media/C , /media/D , /media/E. Now, these mounted partitions appear on the Desktop as they should. C and D appear quite fine. However, E appears with some junk character :???: . You can have a look at it here :

[IMG]http://img407.imageshack.us/img407/8046/why9rq.png[/IMG]

I have tried remounting, restarting, changing the partition name and then remounting. I feel I have done all I could think of. Please suggest some solution to this. Thanks.

---

### Post by Patsoe on 2006-06-07
Very weird? The thing it is showing is just the unicode number for the character I think, but it should do that only when the character set was not installed. How could it be that just the E is missing from your set??

---

### Post by MiD-AwE on 2006-06-08
I am seeing the same thing on my system.

---

### Post by rhipwell on 2006-06-16
Same deal here, only mine is with DVD filesystems.

---

### Post by rhipwell on 2006-06-16
I got mine resolved. ( thread [http://ubuntuforums.org/showthread.php?p=1147049#post1147049](http://ubuntuforums.org/showthread.php?p=1147049#post1147049) ) 

try mounting the filesystem with:  -o utf8

hope this helps!

---

### Post by sanketmedhi on 2006-06-17
Sorry, did not work for me! :(

---

### Post by MiD-AwE on 2006-09-30
Hi all. I got mine back; unfortunitly required a re-install. In the set up app you have the opportunity to mount and name all drives an partitions.

***Take the opportunity and name all of the mounted drives and partitions.***

I did and it worked. Not a big deal to do but worth it.

---

