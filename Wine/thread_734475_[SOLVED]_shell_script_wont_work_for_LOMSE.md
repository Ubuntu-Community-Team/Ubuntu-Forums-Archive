---
title: "[SOLVED] shell script wont work for LOMSE"
date: 2008-03-24
forum: Wine
---

### Post by Tyke91 on 2008-03-24
when I run these two commands, the game lords of magic special edition will run better than it even does in windows vista (vista has a speed problem)

```
cd ~/.wine/drive_c/SIERRA/LOMSE/
```
```
wine lomse.EXE
```


if I run this code, the game will run with serious gameplay flaws

```
wine ~/.wine/drive_c/SIERRA/LOMSE/lomse.EXE
```

if I write this shell script, the game will not run at all
```
#!/bin/sh
wine ~/.wine/drive_c/SIERRA/LOMSE/lomse.EXE

```

neither will this code 

```
#!/bin/sh
cd ~/.wine/drive_c/SIERRA/LOMSE
wine lomse.EXE 
```


does anyone know why this would happen?

---

### Post by Tyke91 on 2008-03-24
I solved the problem. Wine runs into a myriad of problems when first running LOMSE, and uses the terminal to autocorrect everything. so I piped the command through a terminal emulator, in this case, xterm. everything works better now :)

```
 #!/bin/sh

cd /home/mykola/.wine/drive_c/SIERRA/LOMSE/

wine lomse.EXE | xterm

```

---

