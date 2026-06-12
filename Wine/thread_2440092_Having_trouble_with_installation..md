---
title: "Having trouble with installation."
date: 2020-04-05
forum: Wine
---

### Post by arditprenga on 2020-04-05
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libfaudio0 : Depends: libsdl2-2.0-0 (>= 2.0.8) but it is not going to be installed
 libfaudio0:i386 : Depends: libsdl2-2.0-0:i386 (>= 2.0.8) but it is not going to be installed
 winehq-stable : Depends: wine-stable (= 5.0.0~bionic)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Does anyone have any idea what to do

---

### Post by TheFu on 2020-04-05
What is the exact command being run?
Run it from the terminal, show the command and output.

---

### Post by DuckHook on 2020-04-05
[LIST=1]
[*]What version and flavour are you running?
[*]Before installing WINE, did you first do:```
sudo dpkg --add-architecture i386 && sudo apt update
```
[*]Are you installing the official Ubuntu version of WINE, the snap or the external WINE repo? Please be specific.
[/LIST]
Do **NOT** run:```
apt --fix-broken install
```…yet. Not until you've answered TheFu's and my questions.

---

