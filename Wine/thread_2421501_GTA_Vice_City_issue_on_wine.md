---
title: "GTA Vice City issue on wine"
date: 2019-06-22
forum: Wine
---

### Post by sam-mo on 2019-06-22
Hi everyone, few months ago I installed gta on my Ubuntu using wine and it worked fine, but later my pc was damaged and I needed to reinstall Ubuntu again, I reinstalled gta but it didn't work on wine anymore, BUT I noticed something, when I ran gta the first time and worked well, I haven't had insatled any dll components using winetricks, anyway now I try to run it using wine after I insatlled components using winetricks (which are necessary for other apps) these are the components and dlls I have installed (click on images to see them) plus these ones : directplay + dsound + quartz + vcrun 2005

[ATTACH=CONFIG]283478[/ATTACH]


[ATTACH=CONFIG]283479[/ATTACH]

should I install others to make it work ? or can I exclude them from affecting gta specifically ?

please note the Wine and Ubuntu versions are the same now as they were before, Ubuntu is 18.04 LTS

---

### Post by mastablasta on 2019-06-24
have you run these in winecfg:

> *[SIZE=3]Configuring Wine for GTA:VC [/SIZE]*
[LIST=1]
[*][SIZE=2]Run wine configuration (or type winecfg in terminal[/SIZE])
[*][SIZE=2]Add an application and select your "GTA VC exe"[/SIZE]
[*][SIZE=2]In graphical options enable all first 4 options (from Directx .... to Enable virtual desktop) and set Virtual desktop to 800x600.[/SIZE]
[*][SIZE=2]Now you can start GTA VC (be sure "Vice City Play" is mounted or inserted, My crack tries to find CD, but will accept both the original or the image). [/SIZE]
[/LIST]


more info: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=3050](https://appdb.winehq.org/objectManager.php?sClass=version&iId=3050)

---

### Post by sam-mo on 2019-06-28
yes I did but it didn't work either :(

---

