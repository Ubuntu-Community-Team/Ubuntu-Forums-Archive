---
title: "Installing Steam on a different hard drive."
date: 2007-12-12
forum: Wine
---

### Post by darkline on 2007-12-12
HI,
I have tried to install steam on the hard drive on my comp called /media/sda1.

To be exact i did this::-
WINEPREFIXCREATE --prefix /media/sda1/.steam
and got ::-
/media/sda1/.steam updated successfully.

Then i did::-
 WINEPREFIX="/media/sda1/.steam" wine msiexec /i SteamInstall.msi
which also worked.
But when i tried to launch steam it came up with the error ::-
Steam.exe(main Exception): Cannot open blob archive file: Cmultifieldblob(mem-mapped file): failedtomapviewoffile

Steam works when i install it in the normal way (wine msiexec /i SteamInstall.msi) but i cant leavev it on that drive as there is not enough room (about 6gigs left).

Can anyone figure out what i can do to fix this? All the files installed seem to be the same for both installations but the one in media/sda1 doesnt work, i cant see any other differences.
I am using wine-0.9.46 and the latest steam installer and ubuntu 7.10

Thanks

---

