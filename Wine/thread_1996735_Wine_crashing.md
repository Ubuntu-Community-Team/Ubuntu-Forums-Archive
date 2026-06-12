---
title: "Wine crashing"
date: 2012-06-04
forum: Wine
---

### Post by Code9 on 2012-06-04
I am trying to run ASA Prepware 2012 via Wine. I installed Mono and .Net Framework, but I am getting an error upon trying to start the application. 

```


[POL_Wine] Message: Running wine- Prepware 2012.exe
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\Program Files (x86)\\ASA\\Prepware 2012\\Prepware 2012.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files (x86)\\ASA\\Prepware 2012\\Prepware 2012.exe" failed, status c0000135
[POL_Wine] Message: Wine return: 53

```

Any help with getting the program to run is appreciated.

---

### Post by editheraven on 2012-06-04
Try download it from the link below and copy it to the mentioned path after you unzip it.

[http://www.dll-files.com/dllindex/dll-files.shtml?mscoree](http://www.dll-files.com/dllindex/dll-files.shtml?mscoree)

le : if it's not working this way add the dll at the libraries tab in winecfg and set it to "bulletin then native" or disabled.

---

### Post by Code9 on 2012-06-04
I did that, and now it's giving me a new error. 

[IMG]http://i.imgur.com/d6Xj3.png[/IMG]

as well as some new stuff from the terminal 

```

wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"

```

[IMG]http://i.imgur.com/ogIyQ.png[/IMG]

---

### Post by oldos2er on 2012-06-04
Moved to Wine.

---

### Post by editheraven on 2012-06-05
Do you have MS Visual c++ installed with winetricks?

---

