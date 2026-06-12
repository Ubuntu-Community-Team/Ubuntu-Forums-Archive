---
title: "Cant install build-essential"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by aziz07 on 2008-05-20
Hi,

Just installed Ubuntu and I was trying to install my wireless WPN111. I read that I need ndiswrapper which I successfully installed and it shows up in wireless net config but I cant scan networks and wifiradar doesnt show anything  and I need to install Build-essential which when I try, it tells me it needs the g++ package. Then I tried to  install it and here what it gives:

ThnX in advance.

EDIT: I have Ubuntu 8.04 LTS  64bit amd64

---

### Post by istblacken on 2008-05-20
```
sudo apt-get install build-essentials
```

write this command in terminal then it will ask ubuntu cd put it thats all.

---

### Post by Sef on 2008-05-20
> 
Code:

sudo apt-get install build-essentials



That is not quite correct.

Applications > Accessories > Terminal

then just copy and paste this command in the terminal:

```
sudo apt-get update && sudo apt-get install build-essential
```

No 's' on essential.

---

### Post by Yellow Pasque on 2008-05-20
It is most likely a problem with your software sources. Go to System -> Administration -> Software Sources and make sure all of the boxes on the first tab are checked. Then:
```
sudo apt-get install libstdc++6-4.2-dev build-essential
```

---

