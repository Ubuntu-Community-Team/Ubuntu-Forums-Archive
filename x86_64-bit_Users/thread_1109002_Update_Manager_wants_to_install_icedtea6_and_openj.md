---
title: "Update Manager wants to install icedtea6 and openjdk6."
date: 2009-03-28
forum: x86 64-bit Users
---

### Post by trekguy on 2009-03-28
Why is this happening?  I have the 64bit Sun Java (jre 1.6.0_12) installed, and working great.

Would there be any reason to have the icedtea6 and openjdk6?
 
If not, is there a way to clear the icedtea and openjdk from Update Manager??

---

### Post by Arup on 2009-03-28
Unless you have iced tea installed, it shouldn't be updating it. Open JDK is needed by Open Office to make Java work so I would keep that but make sure Sun Java is the default by checking it in Java options in OO. Also its a good idea to give the alternatives update command to make Sun Java default. I have Open JDK and Sun Java 14 installed.

---

### Post by inphektion on 2009-03-28
I don't recall installing iced tea myself but maybe was a dependency and got installed.  so I can remove it then install the one from sun and use update alternatives to make it the default... sound right?

---

### Post by Arup on 2009-03-28
Don't remove Open JDK as its needed by Open Office Java Common.

---

### Post by trekguy on 2009-03-28
> **Arup said:**
> Unless you have iced tea installed, it shouldn't be updating it. Open JDK is needed by Open Office to make Java work so I would keep that but make sure Sun Java is the default by checking it in Java options in OO. Also its a good idea to give the alternatives update command to make Sun Java default. I have Open JDK and Sun Java 14 installed.

I guess I do have openjdk installed... I checked, and the Sun Java is selected as default.

I installed the updates...

Thanks for the replies.... still learning...  :)

---

