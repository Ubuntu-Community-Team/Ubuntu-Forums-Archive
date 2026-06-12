---
title: "Wine won't load native DLLs"
date: 2008-06-17
forum: Wine
---

### Post by TonyPursell on 2008-06-17
I am trying to get an app working (Tax Calc). There seems to be a problem with the builtin version of shdocvw.dll so I want to try it using the native version.  However I get 

err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"shdocvw.dll"

I assume this means Wine cannot find the dll even though I have it in both the system32 folder and the program's own folder. 

I am using Ubuntu 8.04 and Wine 1.0.  Any suggestions why Wine won't load this DLL?

Tony

---

### Post by cogadh on 2008-06-17
Did you apply a native library override for the DLL in winecfg?

---

### Post by TonyPursell on 2008-06-17
Yes, native only

---

### Post by cogadh on 2008-06-17
Based on past test results at Wine's Application Database, TaxCalc doesn't work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1398](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1398)

---

### Post by TonyPursell on 2008-06-17
That was my test results done a long time ago using just builtin libraries. (I'm also the appdb maintainer for taxcalc!).  I'm trying to tackle the issues with taxcalc now the new 2008 version is available. Once I know which DLLs don't work with builtin, I will start reporting the bugs they throw up.

---

