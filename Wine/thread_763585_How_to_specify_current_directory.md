---
title: "How to specify current directory?"
date: 2008-04-23
forum: Wine
---

### Post by HyperHacker on 2008-04-23
I have this [stupid program](http://en.wikipedia.org/wiki/Nemu64) (whose website seems to have disappeared) that only looks for its files in the directory it's launched from and won't run if it doesn't find them. In Windows this meant only actually browsing to the .exe itself and running it would work; any attempt to run it via any shortcut, script, etc would fail because it wouldn't find those files. I'm seeing the same annoyance in Wine and I'd really like to know if there's a way to have a launcher on my panel that will start this program with the current directory set so it will run.
I'm not sure exactly what it's doing to be able to fail so badly, I've never seen any other program have this problem.

---

### Post by dje on 2008-04-23
If i understand you correctly just open a terminal and do:
```
cd /path/to/.exe
``` (directory with the other files and the exe)
and then do
```
wine name_of_.exe
```

hope that helps,
dje

---

### Post by HyperHacker on 2008-04-23
Right, but how would I have a shortcut on the panel do that automatically?

---

### Post by dje on 2008-04-23
Just make a bash script with this in it:
```
#!/bin/bash

cd /path/to/.exe
wine name_of_.exe &
exit
```
Then do:
```
sudo mv /path/to/script /usr/local/bin
```
and
```
sudo chmod 755 /usr/local/bin/script_name
```

Then just add a launcher/modify the existing launcher to point to the script

hope that helps,
dje

---

### Post by CarpKing on 2008-04-23
If you put the script in your home folder the middle step is unnecessary and the last step changes to:

```
chmod 755 script_name
```

I don't think sudo is necessary, but it will complain at you if it is.

---

