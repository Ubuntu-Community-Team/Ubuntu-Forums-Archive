---
title: "New Warcraft III - Frozen Throne patch 1.22."
date: 2008-06-30
forum: Wine
---

### Post by RubberSoul on 2008-06-30
The game was working, patch 1.20 dont needs CD, but with the new patch, it stoped, and begin ask for cd... ?!?!?!? Something wrong? How i resolve this?

---

### Post by guine on 2008-06-30
I'm having the same problem with warcraft no longer being able to see the cd in either wine or cedega after the last patch.  I've had this happen with their patches before, unfortunately its been probably 2 or 3 years so I don't remember what I did to get it working again.

---

### Post by Chess13 on 2008-06-30
yeah same message here too!

---

### Post by handband2 on 2008-06-30
Try this [http://ubuntuforums.org/showthread.php?t=845750&highlight=warcraft](http://ubuntuforums.org/showthread.php?t=845750&highlight=warcraft)

It worked for me.

---

### Post by RubberSoul on 2008-07-01
Worked for me too.

---

### Post by DontThinkSo on 2008-07-01
Hmm, that doesn't quite fix it for me. After running winetricks, Frozen Throne crashes with:

Runtime Error!

Program: C:\Program Files\Warcraft III\war3.exe

R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.

Any ideas?

---

### Post by someone13 on 2008-07-01
For those using cedega, this is how I got around this problem.

Follow this:
[http://ubuntuforums.org/showthread.php?t=845750&highlight=warcraft](http://ubuntuforums.org/showthread.php?t=845750&highlight=warcraft)

Now, you must goto:
/home/<your username>/.wine/drive_c/windows/system32/

Copy these files:
msvcm80.dll
msvcp80.dll
msvcr80.dll

Paste these files in:
/home/<your username>/.cedega/<your warcraft game folder>/c_drive/windows/system32/

There you have it.

---

### Post by ARedSlimeGin on 2008-07-01
i downloaded the new patch last night and the same thing is happening to me it just says something different. i dont have linux, i have an HP pc so how should i go about getting to my game?

---

### Post by someone13 on 2008-07-01
It looks like they upgraded to Visual Studio 2005.

Anyway, if your on Windws (or using Wine), what you wanna do is download and install these files:

[http://www.microsoft.com/downloads/details.aspx?familyid=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displaylang=en)

[http://www.microsoft.com/downloads/details.aspx?FamilyID=200b2fd9-ae1a-4a14-984d-389c36f85647&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=200b2fd9-ae1a-4a14-984d-389c36f85647&displaylang=en)

---

### Post by tacoboye on 2008-12-29
If you are unable to get warcraft to work after installing vcrun2005sp1 and vcrun2005, delete the wine registry and run sh winetricks vcrun2005sp1 vcrun2005 again. Doing this fixed the error messages about incorrectly accessing a C++ library and what not. Hope this helps, it will me considering I've referenced this post around 8 times between all my installations of ubuntu.... :P


An aside:

The wine registry files have a .reg exstension and are located in /home/USER/.wine/

---

