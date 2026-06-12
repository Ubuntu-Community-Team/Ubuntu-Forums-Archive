---
title: "Warcraft 3 start menu not found?"
date: 2013-12-29
forum: Wine
---

### Post by StevenHodges92 on 2013-12-29
I've heard for Warcraft 3 to work with wine you have to do a registry edit, here are the directions I found:

> 1) Go to Start > Run > type regedit 
2) Navigate to "HKEY_CURRENT_USER\Software\Microsoft\Windows\Current 
Version\Explorer\Shell Folders" 
 
if there is no string in there called "Programs" put that in with the 
value: 
 
C:\\Users\\%USERNAME%\\AppData\\Roaming\\Microsoft\\Windows\\Start 
Menu\\Programs

So I edited the Programs string and put that in but am still getting "No Program Start Menu Found" when trying to run the installer.

---

### Post by manudo on 2013-12-31
Dota or Warcraft player?
Yes, it works. But I have a Warcraft version that I can run it by executing the war3.exe, doesn't have to run any registry keys, a friend got that version but I don't know where.
Try to download a portable version or I don't know.

---

