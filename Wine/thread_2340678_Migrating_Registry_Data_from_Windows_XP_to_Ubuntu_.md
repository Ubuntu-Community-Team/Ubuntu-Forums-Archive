---
title: "Migrating Registry Data from Windows XP to Ubuntu Wine"
date: 2016-10-20
forum: Wine
---

### Post by artist-wavenet on 2016-10-20
I am migrating from an old computer that is irreparably broke, but the disk drives are intact. The older computer won't boot. The new computer's OS is Ubuntu. The old computer's OS is Windows XP.

There is a Windows XP program I had on the old computer that I have installed in the new one using Wine. I want to migrate that program's configuration from the old computer instead of entering it all again manually. The program's configuration is stored in the Windows XP registry. I have transferred the entire C:\WINDOWS directory from the old computer to the new computer just to make sure I won't lose something I will need later. Now I need a registry editor I can use to export the program's configuration in the C:\WINDOWS directory that was transferred from the old computer to files that can be imported by Wine's registry editor. When I invoked Wine's registry editor at: /home/<user>/.wine/drive_c/windows/regedit.exe I could not find a way to change the directory of the registry it edits. What registry editor can allow me to change the registry directory to the one I transferred from the old computer?

---

### Post by colmax on 2016-10-20
Welcome!
Not sure if you have to be in wine directory to make changes
You can always try gedit & drill down to the file you want to change
Either way i think it is gonna be a little difficult
Cheers

---

### Post by artist-wavenet on 2016-10-20
MS Windows registry files are binary files. They cannot be edited by a text editor.
[https://en.wikipedia.org/wiki/Windows_Registry](https://en.wikipedia.org/wiki/Windows_Registry)

---

### Post by colmax on 2016-10-21
ascii editor?
8 bits to 1 byte with parity
May need to establish permissions to write and save
Cheers

---

### Post by howefield on 2016-10-21
Thread moved to the "*Wine*" form.

---

### Post by artist-wavenet on 2016-10-21
It is not practical, and it is dangerous, to edit a registry with anything other than an editor that was made for the purpose. And even with such a made for the purpose editor there is still an element of danger, most especially for those that do not know what they are doing.

---

