---
title: "Can't even wine steam.exe"
date: 2007-08-22
forum: Wine
---

### Post by Aesir09 on 2007-08-22
i just got a counter strike account back and i cant even play :(!

as soon as i wine steam.exe i get this message

[IMG]http://i71.photobucket.com/albums/i141/Bodomshadow/Screenshot-ERROR.png[/IMG]

---

### Post by hikaricore on 2007-08-22
I think you're going to have to provide a little more detail if you need help.

Did it work before?
Have you upgraded wine?
Have you upgraded steam?
Searched wineapp database to see if this is a known issue?
Searched Ubuntu Forums to see if this is a known issue (it sounds familiar)?
Have you changed any hardware or upgraded Ubuntu lately?
Do you have any weapons of mass destruction in your basement?

Ya know you gotta give some info.  ^_^

---

### Post by cogadh on 2007-08-22
Don't forget - 
Did you follow one of the many Steam install/use tutorials?

---

### Post by quadomatic on 2007-08-22
[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

Follow the guide. Also, instead of using the .msi installer, use the exe. For whatever reason, that one doesn't have a problem.

BTW: Are you running this off of an NTFS partition? I hear that works, but you have to mount it with NTFS-3G, because i think you need write support.

---

### Post by splintercellguy on 2007-08-23
Running Steam off NTFS even with NTFS-3G won't work because of a shortcoming in the NTFS-3G driver, but this may have changed.

---

### Post by Brynster on 2007-08-23
thats a fairly common failure in steam for the .blob files to become corrupted.

All you need to do is goto where the steam fold is on you harddrive typically

/home/.wine/c_drve/steam

delete the 2 .blob files and re start steam it should reload new .blob files and then you *should* be good to go.

---

### Post by Aesir09 on 2007-08-23
ok everyone, im trying to run this from my windows hard drive, so i have run it fine before on winblows, so now i want to wine it

i also yes have used the .exe before in linux and my fake c drive that wine had made was not big enough! so i installed it to my home directory, steam would work fine

but when i tried to download css, it went really slow, so i stopped it, reinstalled in winblows and i still get this when i try to wine it.


thanks please please please help i just got counter strike again and it was one of the game i looked forward to most top playing in Linux.:confused:

---

### Post by Aesir09 on 2007-08-23
**it is also trying to run off a ntfs windows partition**

---

### Post by Aesir09 on 2007-08-23
thanks brynster i will try that 

:guitar:

---

### Post by Aesir09 on 2007-08-23
deleting the blob files did not work i get the same message...

i installed this in windows if that helps at all

---

### Post by Falcorian on 2008-05-27
Since you screenshoted the error, it didn't come up in my searches.

The error is:

> Steam.exe (main exception): Cannot open blob archive file: CMultiFieldBlob(mem-mapped file): Failed to MapViewOfFile

The cause is trying to run steam from an ntfs partition with ntfs-3g. This can not currently be done. :(

---

### Post by cogadh on 2008-05-27
Dude, this thread is almost a year old. I'm pretty sure this is no longer an issue for the OP.

---

