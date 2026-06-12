---
title: "dll problem with ReFxNexus"
date: 2015-02-18
forum: Wine
---

### Post by devdlp on 2015-02-18
I just ended another thread on how to unlock the application ReFxNexus on ubuntu, my problem was solved in the end. Then i ran into another problem afterwards, when i double-click on the the Setup.exe file and run with Wine it shows this message: Runtime Error (at -1:0):
Cannot Import dll:C:\users\deven\Temp\ia-FDTQU.tmp\isskin.dll.Im not sure what to do at this point or if im just unable to use the application at all i would like to know if its something i can do to fix this through Wine Tricks or something else i can do to fix this error at all i really need this to work for me thanks in advance>

---

### Post by oldos2er on 2015-02-18
Moved to Wine.

---

### Post by devdlp on 2015-02-18
Sorry i shouldve posted it in wine to begin with

i still have a problem with this could someone help solve this please

---

### Post by Fincer on 2015-02-25
Run

```
winetricks vcrun6sp6
```

as suggested [here]("https://forum.winehq.org/viewtopic.php?t=8896").

If it doesn't help, there is also alternative winetricks suggestion given:

```
winetricks mfc42
```

Regards,
Fincer

---

### Post by devdlp on 2015-02-27
Trying it now after ubuntu updates

Omg it worked. Thank you

---

### Post by Fincer on 2015-02-27
Glad to hear that. :)

Regards,
Fincer

---

