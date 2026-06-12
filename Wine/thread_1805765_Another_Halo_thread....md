---
title: "Another Halo thread..."
date: 2011-07-16
forum: Wine
---

### Post by J3WD4Z on 2011-07-16
Okay I looked through a couple of the old Halo threads but I couldn't find the problem I was having.  Every time I try to set the properties to executable on the setup.exe I get a prompt that says cannot be changed is a read only file... I'm REALLY SORRY I've read a few of the halo threads and they aren't popular here >.<

---

### Post by hobbit1983 on 2011-07-16
Hello

The file that you are trying to make executable; was that on a CDROM or DVD?

Are you trying to run the file within wine? or crossovergames?

If you can give a little more information I might be able to point you in the right direction.

---

### Post by J3WD4Z on 2011-07-16
> **hobbit1983 said:**
> Hello

The file that you are trying to make executable; was that on a CDROM or DVD?

Are you trying to run the file within wine? or crossovergames?

If you can give a little more information I might be able to point you in the right direction.
It is a CD-Rom i believe and I'm trying to use wine but because the disc wont let me add the executable properties to it I can't actually open it with wine...
Edit: it's a DVD-rom >.> it's too large to be a cd-rom
Edit: it doesn't actually say on the thing im jsut assuming it's a DVD given how large the game is...

---

### Post by Elfy on 2011-07-16
Thread moved to Wine.

---

### Post by hobbit1983 on 2011-07-16
Hello

The reason you can't add executable permissions to the file is because you cannot alter the disc.  However this isn't a problem.

Bring up a terminal and cd to the folder that contains the executable you want to run under wine.  It is usually mounted under /media.

once you are in the correct directory then issue the command:
wine <<executable file>>

this will run wine passing it the name of the executable which wine will then start to run.

I hope this helps

---

### Post by J3WD4Z on 2011-07-16
Okay so i added the MFC42.dll to the folder reccomended in this thread [http://ubuntuforums.org/showthread.php?t=655352](http://ubuntuforums.org/showthread.php?t=655352) but it still say cannot load pidgen.dll into the ~/.wine/drive_c/windows/system32 i got the dll from my windows 98 SE disc that i had lying around in my stuff and nothing happened...

---

