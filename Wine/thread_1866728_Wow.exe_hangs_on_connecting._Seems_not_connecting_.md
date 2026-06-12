---
title: "Wow.exe hangs on connecting. Seems not connecting to the internet."
date: 2011-10-21
forum: Wine
---

### Post by cumpaste on 2011-10-21
Im new on ubuntu i understand the terminal a bit. I think Ubuntu is the best os. ok now to the point.

MY world of Warcraft hangs on connecting while logging in.
the launcher works and downloads normmally, but wow.exe seems not connecting to the internet.

Its a clean instal, ubuntu wine and wow. 

Wow is installed on another partition a NTFS drive.

Maby there is a dll missing with wine or? something els. cause The launcher downloads normally.

I Hope you can help me guys.. And i looking forward to meet everyone of the Ubuntu cummunity.:D

---

### Post by cwwilson721 on 2011-10-21
2 things:
[LIST]
[*]DO NOT run WoW from an NTFS partition. Copy to your ~/.wine folder. Running from an NTFS partition can run into SEVERE playability and file issues.
[*]Launcher.exe has issues, and most times, will not run normally. After Launcher.exe 'exits', it is supposed to run Wow.exe, but it hangs, and Wow.exe is never run. This is not just an issue with wine, it does it in some Windows installs, also.The fix is to run Wow.exe instead. I only run Launcher.exe when I want to check to see if there is a patch.
[/LIST]

---

### Post by cumpaste on 2011-10-22
Reply: cwwilson721

hey thanks man i got wow.exe working by using wowrepair.exe 

I will be moving the files from my partition and format it to a different kind.  maby fat32? or ext4? 

il just do what you said, and see if it runs better.

Btw wow does not support shadows and stuff in ubuntu?

---

### Post by cumpaste on 2011-10-22
> **cwwilson721 said:**
> 2 things:
[LIST]
[*]DO NOT run WoW from an NTFS partition. Copy to your ~/.wine folder. Running from an NTFS partition can run into SEVERE playability and file issues.
[*]Launcher.exe has issues, and most times, will not run normally. After Launcher.exe 'exits', it is supposed to run Wow.exe, but it hangs, and Wow.exe is never run. This is not just an issue with wine, it does it in some Windows installs, also.The fix is to run Wow.exe instead. I only run Launcher.exe when I want to check to see if there is a patch.
[/LIST]

BTw i got a new problem the wow files say. error the file cannot be found.

---

### Post by cumpaste on 2011-10-22
nvm Im doing clean install of wow agian and i formatted the nfts drive to ext4

---

### Post by cumpaste on 2011-10-22
> **cwwilson721 said:**
> 2 things:
[LIST]
[*]DO NOT run WoW from an NTFS partition. Copy to your ~/.wine folder. Running from an NTFS partition can run into SEVERE playability and file issues.
[*]Launcher.exe has issues, and most times, will not run normally. After Launcher.exe 'exits', it is supposed to run Wow.exe, but it hangs, and Wow.exe is never run. This is not just an issue with wine, it does it in some Windows installs, also.The fix is to run Wow.exe instead. I only run Launcher.exe when I want to check to see if there is a patch.
[/LIST]

Thanks man it finnaly works for me now.

im running it in gl most set gpx "Opengl"

Only the shadows dont work. well ok i can run directx but is lags more.

thanks agian

(solved)

---

