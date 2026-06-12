---
title: "Install wine on Ubuntu 16.0"
date: 2017-03-18
forum: Wine
---

### Post by nhatnduy on 2017-03-18
I'm using Ubuntu 16.10 , I tried  Wine window program loader  via websites  and forums but was failed .
Pls help me to install wine with correct command

---

### Post by Bucky Ball on 2017-03-19
Welcome. Strongly advised you check the official repositories before installing stuff from third-party sites. That is the Win way. Wine is in the repositories. Just open a package manager and install it.

---

### Post by howefield on 2017-03-19
You should be able to install the Wine from the Ubuntu repositories with the terminal command..

```
sudo apt install wine-stable
```

which should give you Wine 1.8.5-x 

or if you needed the latest version..
```
sudo add-apt-repository ppa:wine/wine-builds
```
```
sudo apt-get update
```

and then, depending on whether you want the staging version or the devel version..
```
sudo apt-get install --install-recommends winehq-staging
```
```
sudo apt-get install --install-recommends winehq-devel
```

I would suggest the first method unless you do a little research as to exactly what wine staging/devel gives you over and above the version included in the Ubuntu repository.

---

