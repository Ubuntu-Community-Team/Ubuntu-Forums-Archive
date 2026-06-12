---
title: "Error opening oledb database after upgrade to wine 5.0"
date: 2020-10-06
forum: Wine
---

### Post by dulx on 2020-10-06
Hi,

after upgrading Ubuntu (and wine) my video recorder management app is not working anymore. Some details:

old Ubuntu release: 18.04
new Ubuntu release: 20.04
old wine release: 1.x (don't know the exact release anymore)
new wine release: 5.03 (came with the upgrade, don't know why it is such a big jump)

The prefix was created with "WINEARCH=win32". Additions installed via winetricks, which are necessary to get the app running:

mdac27
wsh57
jet40
mdac28
mfc42
msvcirt
vcrun6
vcrun6sp6

In the old release I had wsh56sp6 installed additionally, but this can't be installed with current winetricks any more (I'm getting forwarding to wsh57 again).
I can start the app and configure my network connection to the VCR successfully. But when trying to open the video stream, it fails with the following message:


open db
open :Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\iVSS\config\SysDB.mdb;user id=admin;jet oledb:database password=*<some password here>* err:317--Des:-ErrMsg: Unknown error 0x80004001--:

(I replaced the password string, which is hardcoded in the app). 

When searching around, I found that some MS Office users have similar problems with current office releases when opening password protected databases, so this might be related. On a machine running Ubuntu 16.04 and wine 1.1.6.2 the app is still working.

Would be bad, if I had to downgrade Ubuntu again because of this... Any ideas are much appreciated.

Thanks.
Regards,
Dulx

---

### Post by mastablasta on 2020-10-06
on play on linux it i easy to select the wine version you want your application to use. the versions on offer go back quite far. in this case you would just select the wine version when the app was working and continue like nothing happened.

---

### Post by dulx on 2020-10-09
Hi Mastablasta,
thanks for the reply. Indeed an interesting tool and I used it to install wine 1.6. I installed the app there and when I tried to start, it created 2 little bars, which were windows, as I could see in the taskbar. But I couldn't enlarge them in any way, so I checked the process list and executed the commands in a console window. That showed me some missing library, which I installed and the next try showed me another one. So I finally gave up after some tries, because I already had such situations and they never led me to a good end.

I switched the distribution meanwhile and everything is running smooth with wine 4.0 now.
Thanks again.
Regards,
Dulx

---

