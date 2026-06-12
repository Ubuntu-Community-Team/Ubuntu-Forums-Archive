---
title: "Unable to install libsvga1_1.4.3-24_amd64.deb"
date: 2008-10-28
forum: x86 64-bit Users
---

### Post by Christian Knudsen on 2008-10-28
I'm trying to install libsvga1_1.4.3-24_amd64.deb with package manager on Ubuntu 64-bit but get a "failed to install package" message, but nothing displayed in the terminal window. What's wrong?

---

### Post by cariboo on 2008-10-28
Have you tried in a terminal:

```
sudo apt-get install libsvga1
```

or if you have already downloaded the file just double click on it and gdebi should open and install it for you.

Jim

---

### Post by Christian Knudsen on 2008-10-28
I can't use apt-get as I'm not connected to the net on my Ubuntu box. I've downloaded the package and double-clicked on it as you said. I then select "Install package" and that's when I get the "failed to install package" message.

---

### Post by Yellow Pasque on 2008-10-29
To get a more succinct error message, try installing the package through the CLI.
```
cd <path where the file is located>
sudo dpkg -i libsvga1_1.4.3-24_amd64.deb
```

---

### Post by Christian Knudsen on 2008-10-29
It was conflicting with svgalib, so I've removed that and reinstalled all the other packages. Works fine now! Thanks! :)

---

