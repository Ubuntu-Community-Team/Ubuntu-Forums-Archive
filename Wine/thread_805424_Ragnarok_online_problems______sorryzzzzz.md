---
title: "Ragnarok online problems      sorryzzzzz"
date: 2008-05-23
forum: Wine
---

### Post by caelcynndarr on 2008-05-23
hay uhm i am trying to get a private rag server to work on wine 

when i run the program  wine starts up and then it allluvasudden DIES  
plz help   
i will provide any info you need just ask 


thank you for your time

---

### Post by caelcynndarr on 2008-05-24
i have not been able to make any progress yet......  to google away

---

### Post by caelcynndarr on 2008-05-24
bump   uhm it ends up the patch will not start any ideas thanks

---

### Post by caelcynndarr on 2008-05-25
bump

---

### Post by cogadh on 2008-05-25
Are you trying to run a private server or a private server *client*? If you are trying to run a server, Wine isn't needed, it has a Linux native version:
[http://eathena.deltaanime.net/wiki/index.php/Main_Page](http://eathena.deltaanime.net/wiki/index.php/Main_Page)

If you are trying to run the client, it might help if your provided Wine's error output from the terminal.

---

### Post by caelcynndarr on 2008-05-25
i am trying to run a private server patcher

and i would post an error log if there were one    
terminal didn't even peep while the wine browser popped up and then disappeared

---

### Post by Exershio on 2008-05-25
> **caelcynndarr said:**
> i am trying to run a private server patcher

and i would post an error log if there were one    
terminal didn't even peep while the wine browser popped up and then disappeared

**Copied straight from [http://appdb.winehq.org/appview.php?iVersionId=928](http://appdb.winehq.org/appview.php?iVersionId=928)**

This requires a native version of the mfc42.dll library, and can be obtained at [http://www.gn0me.org/mfc42.dll](http://www.gn0me.org/mfc42.dll). Please do not download this file unless you own a valid copy of Microsoft Windows, as it will most likely cause problems. This file must be copied to your ~/.wine/drive_c/windows/system32/ directory.

A native version of msvcp60.dll is also needed, and can be obtained at [http://www.gn0me.org/msvcp60.dll](http://www.gn0me.org/msvcp60.dll). Please do not download this file unless you own a valid copy of Microsoft Windows, as it will most likely cause problems. This file must be copied to your ~/.wine/drive_c/windows/system32/ directory.

---

### Post by caelcynndarr on 2008-05-25
> **Exershio said:**
> **Copied straight from [http://appdb.winehq.org/appview.php?iVersionId=928](http://appdb.winehq.org/appview.php?iVersionId=928)**

This requires a native version of the mfc42.dll library, and can be obtained at [http://www.gn0me.org/mfc42.dll](http://www.gn0me.org/mfc42.dll). Please do not download this file unless you own a valid copy of Microsoft Windows, as it will most likely cause problems. This file must be copied to your ~/.wine/drive_c/windows/system32/ directory.

A native version of msvcp60.dll is also needed, and can be obtained at [http://www.gn0me.org/msvcp60.dll](http://www.gn0me.org/msvcp60.dll). Please do not download this file unless you own a valid copy of Microsoft Windows, as it will most likely cause problems. This file must be copied to your ~/.wine/drive_c/windows/system32/ directory.



hi i have already done this and it fails horribly   but thanks you for the help

---

### Post by Exershio on 2008-05-25
Then it appears you are having the same problem I am having. heh, sorry I couldn't be of any help. Have you tried running the game exe without the patcher? you can usually run it like "wine ragexe.exe -1rag1"

Replacing ragexe.exe with whatever exe the private server you're on uses

---

### Post by caelcynndarr on 2008-05-25
> **Exershio said:**
> Then it appears you are having the same problem I am having. heh, sorry I couldn't be of any help. Have you tried running the game exe without the patcher? you can usually run it like "wine ragexe.exe -1rag1"

Replacing ragexe.exe with whatever exe the private server you're on uses

yeah that works but then one will be out of the data loop when it comes to important patches    hmmm i will have to fight it then 

thank you though

---

### Post by Exershio on 2008-05-26
that is right, however, it's a nice temporary solution until we find a fix for the patcher. :)

---

### Post by caelcynndarr on 2008-05-26
hey hey the patcher came up alluvasudden   but but but   i says "Attempting to connect to patchserver; please wait"    and it says that FOREVER

---

### Post by caelcynndarr on 2008-05-26
> **caelcynndarr said:**
> hey hey the patcher came up alluvasudden   but but but   i says "Attempting to connect to patchserver; please wait"    and it says that FOREVER

and ever   i tried iptables and everything grrrrr

---

### Post by caelcynndarr on 2008-05-26
bump

---

### Post by caelcynndarr on 2008-05-26
bump

---

### Post by caelcynndarr on 2008-05-27
bump

---

