---
title: "notepad-plus-plus fails to open after updating to 8.6.5"
date: 2024-03-31
forum: Wine
---

### Post by 7-mike-x on 2024-03-31
If using the CLI, error msg 'wine: failed to open "/home/myhome/snap/notepad-plus-plus/400/notepad-plus-plus/notepad-plus-plus.exe": c0000135' appears.
The path to np++ is '/snap/bin/notepad-plus-plus'.
Have tried removing and re-installing. Have also tried opening np++ after aa-teardown.
np++ was working befire the auto-update.
How can this be fixed?

---

### Post by kostkon on 2024-03-31
Try using the path
```
/home/myhome/snap/notepad-plus-plus/current/notepad-plus-plus/notepad-plus-plus.exe
```

Also, update any desktop files of np++ accordingly, if needed be.

---

### Post by 7-mike-x on 2024-03-31
There are no notepad-plus-plus.exe files anywhere under my $HOME/snap directory. That is the state immediately after a snap (re) install.

---

### Post by kostkon on 2024-03-31
Looks like a widespread issue afterall 
[https://github.com/mmtrt/notepad-plus-plus/issues/39]("https://github.com/mmtrt/notepad-plus-plus/issues/39")

---

### Post by nectarinebandit on 2024-05-10
This is one of those IN CASE OF EMERGENCY, BREAK GLASS moments, so I break out the dowgrade commands. After I downgraded today, Notepad++ works for me again.

Do one of the following

```
snap refresh --beta notepad-plus-plus --devmode

```


OR

```
snap list notepad-plus-plus --all
    Name               Version  Rev  Tracking     Publisher  Notes
    notepad-plus-plus  8.3.2    363  latest/beta  mmtrt      disabled,devmode
    notepad-plus-plus  8.1.9.3  334  latest/beta  mmtrt      devmode

    
sudo snap revert notepad-plus-plus --revision 334
```


Change 334 to match your available revisions.

Source: [https://ubuntuforums.org/showthread.php?t=2474848](https://ubuntuforums.org/showthread.php?t=2474848)

---

