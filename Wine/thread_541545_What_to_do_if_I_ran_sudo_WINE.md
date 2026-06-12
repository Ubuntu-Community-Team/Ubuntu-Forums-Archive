---
title: "What to do if I ran sudo WINE"
date: 2007-09-02
forum: Wine
---

### Post by quadomatic on 2007-09-02
I might have run an application with sudo WINE a while ago. I'm not sure, but what should I do just to be safe?

I already ran the following:

sudo rm -rf ~/.wine
rm -rf ~/.wine
deleted my .wine directory (which I believe had already been deleted after running those commands)
uninstalled WINE
uninstalled ies4linux

Anything else I should do?

---

### Post by cogadh on 2007-09-03
All you had to do was not use sudo to run it again, deleting and uninstalling everything was really unecessary. If wine created a new .wine directory in root's home folder, then you might want to delete that, but that's about it.

---

### Post by dasunst3r on 2007-09-03
You could have issued a command like *sudo chown -R {owner}:{group} .wine*.  This will change the files' ownership back to you.

---

### Post by Cappy on 2007-09-03
Just to put it in simpler terms all you need to do is
```

sudo chown -R $USER:$USER ~/.wine
```

Run that as-is (don't replace $USER with your username or anything) and that will do the trick.

---

### Post by chuckyp on 2007-09-03
If you ran sudo wine <whatever.exe>  It would jsut create a .wine folder in /root/.wine  deleting that folder would be suficient then just as your user run wine <whatever.exe> and it would create the .wine in your ~

---

### Post by karhulitos on 2010-10-15
My gosh, thank you thank you thank you! I post this to help if some other soul bangs his/her head like I did. Keywords:
- Sony Vaio VGN-FW41ZJ
- with Pioneer BDR-TD01 Blueray writer
- needs firmware update (1.03 from Sony support) to write CD-RW properly
- which only runs from Windows (DOS mode not supported)

```
sudo chown -R root:root .wine
```
```
sudo wine EP0000221604.exe
```
```
sudo chown -R $USER:$USER .wine
```

And now I can finally write CD-RW's with my Vaio!

Thank you thank you thank you.

---

