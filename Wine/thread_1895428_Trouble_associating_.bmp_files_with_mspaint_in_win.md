---
title: "Trouble associating .bmp files with mspaint in wine"
date: 2011-12-14
forum: Wine
---

### Post by officialhopsof on 2011-12-14
I am running Kubuntu 11.10 and it is fully updated as of this posting.

I installed wine and mspaint for wine, mspaint works great, and save I save and open bmp files. The trouble comes when I attempt to associate bmp files with mspaint. My command line for opening bmp files is the following:

```
wine mspaint %f
```

when I double click on hello.bmp (located at /home/brandon/Desktop) I get a pop up window that says:

```
Z:\home\brandon\Documents\hello.bmp was not found
```

so I tried the following in the terminal:

terminal:
```
wine mspaint /home/brandon/Desktop/hello.bmp
```

output:
```
Z:\home\brandon\hello.bmp was not found
```



terminal:
```
wine mspaint '""/home/brandon/Desktop/hello.bmp""'
```

output:
```
Z:\home\brandon\""\home\brandon\Desktop\hello.bmp" contians an invalid path
```


terminal:
```
wine mspaint \\home\\brandon\\Desktop\\hello.bmp
```

works fine.

Any ideas on what I am possibly doing wrong?

Thanks!
Brandon

---

### Post by officialhopsof on 2011-12-14
Figured it out! My open command is this:

```
env WINEPREFIX="/home/brandon/.wine" wine start /ProgIDOpen bitmap %f
```

and I had to add some registry keys which I found out how to do here:

[http://www.jrnguyen.com/2009/11/16/windows-file-associations-in-linux-wine/](http://www.jrnguyen.com/2009/11/16/windows-file-associations-in-linux-wine/)

Thanks anyway though!

Brandon

---

